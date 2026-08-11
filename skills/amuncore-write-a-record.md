---
generated: '2026-08-10'
method: generated
name: Create, update and delete a record safely
description: Write through an AmunCore endpoint, with the retry and concurrency hazards spelled out.
api: openapi/amuncore-dynamic-api-openapi.yml
operations: [DynamicApi_Post, DynamicApi_Put, DynamicApi_Delete, DynamicApi_GetById]
source: >-
  operationIds verified verbatim in openapi/amuncore-dynamic-api-openapi.yml
  (harvested from https://amuncore.com/openapi.json); hazards derived from
  conventions/amuncore-conventions.yml (no idempotency, no ETag) and
  errors/amuncore-problem-types.yml.
---

# Create, update and delete a record safely

Writes go straight to the customer's live database. There is no test mode, no sandbox and no
fixture data — see `sandbox/amuncore-sandbox.yml`. Treat every write as production.

## Auth

`X-Api-Key: <key>`, and the key must be a **read-write** key. AmunCore issues read-only and
read-write keys per consumer; a read-only key will fail. Note the API publishes no distinct `403`,
so an authorization failure surfaces as `401` or `400`.

## The two hazards to hold in mind

1. **No idempotency key.** AmunCore supports no `Idempotency-Key` header and no request replay. If a
   `POST` times out, you cannot safely retry it — a retry either inserts a duplicate row or returns
   `409` because a unique constraint caught it, and a `409` on a retry may mean the *first* attempt
   succeeded.
2. **No concurrency control.** No ETag, no `If-Match`, no `Last-Modified`. A `PUT` is last-write-wins
   and will silently clobber a concurrent edit.

## Steps

1. **Create** — `DynamicApi_Post` (`POST /api/v1/{appId}/{endpointName}`).
   - Body is an open JSON object whose keys are the endpoint's exposed columns. The spec ships
     `{"FieldName": "value", "AnotherField": 0}` as a placeholder because the real shape is per
     tenant.
   - Success is `201` with `{success: true, data: {...}}` — capture the returned `id`.
   - **On a timeout, do not blind-retry.** Query first with `DynamicApi_GetList` filtered on a
     column that uniquely identifies the record you were creating, and only retry if it is absent.
2. **Update** — `DynamicApi_Put` (`PUT /api/v1/{appId}/{endpointName}/{id}`). Read the current row
   with `DynamicApi_GetById` immediately beforehand if another writer may be active; there is no
   optimistic-locking mechanism to protect you.
3. **Delete** — `DynamicApi_Delete` (`DELETE /api/v1/{appId}/{endpointName}/{id}`). Irreversible.
   There is no soft delete and no undo. Confirm the `id` with `DynamicApi_GetById` first.

Writes target a **single table**, and there are no bulk or transactional operations — a multi-row
change is N independent calls with no rollback.

## Errors specific to writes

- `409 CONFLICT` — a database constraint, typically a duplicate key.
- `422 VALIDATION_FAILED` — a field failed type or constraint validation before reaching the
  database. Fix the field; retrying unchanged will fail again.
- `400 BAD_REQUEST` — covers both a malformed body and an error raised by the database engine, so
  read `message` to tell them apart.

## Side effects

Every write can fire a webhook — signed with HMAC-SHA256, retried, and optionally carrying the
previous values of the row. Assume downstream consumers see your change. See
`asyncapi/amuncore-webhooks.yml`.

Every call is written to the audit trail with method, path, status, duration and source IP.
