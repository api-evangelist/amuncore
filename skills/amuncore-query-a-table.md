---
generated: '2026-08-10'
method: generated
name: Query a table through an AmunCore endpoint
description: Read records from a generated AmunCore endpoint with paging, sorting and column filters.
api: openapi/amuncore-dynamic-api-openapi.yml
operations: [DynamicApi_GetList, DynamicApi_GetById]
source: >-
  operationIds verified verbatim in openapi/amuncore-dynamic-api-openapi.yml
  (harvested from https://amuncore.com/openapi.json); conventions and error
  handling from conventions/amuncore-conventions.yml and
  errors/amuncore-problem-types.yml.
---

# Query a table through an AmunCore endpoint

AmunCore endpoints are generated per tenant. You are not calling a fixed resource — you are calling
`{appId}/{endpointName}`, where both segments were chosen by whoever configured the endpoint.

## Before you start

You need three things, and none of them can be discovered from the spec:

- **`appId`** — the application slug (the provider's own examples use `myapp` and `shop`).
- **`endpointName`** — the configured endpoint (e.g. `customers`).
- **An API key** for that application, sent as `X-Api-Key`.

The columns an endpoint returns, and therefore the columns you may filter and sort on, are fixed at
configuration time and are **not** in the OpenAPI. Read one page first and look at what comes back,
or ask the account owner. See `data-model/amuncore-data-model.yml` for why.

## Auth

`X-Api-Key: <key>` on every request. See `authentication/amuncore-authentication.yml`.

## Steps

1. **List records** — `DynamicApi_GetList` (`GET /api/v1/{appId}/{endpointName}`).
   - Paging: `page` (1-based) and `pageSize` (max **500**).
   - Sorting: `orderBy` = a column name, `orderDir` = `ASC` or `DESC`.
   - Filtering: bare column-name query parameters — `?city=Dubai`. The spec's `fieldName`
     parameter is a placeholder; substitute the real column name.
   - Response: `{success, page, pageSize, total, data: []}`. Use `total` against `pageSize` to
     decide whether to fetch another page — there is no cursor and no `has_more`.
2. **Fetch one record** — `DynamicApi_GetById` (`GET /api/v1/{appId}/{endpointName}/{id}`) once you
   have an `id` from the list response.

Example, from the provider's own documentation:

```
GET https://amuncore.com/api/v1/myapp/customers?page=1&pageSize=50
X-Api-Key: <key>
```

## Pacing

Quota is a **plan allowance**, not a per-second throttle — 1,000 calls/day on Free, 100K/month on
Starter, 5M/month on Pro. Backing off does not recover an exhausted quota; you have to wait for the
period to roll or upgrade. Check `X-RateLimit-Remaining` when present, and prefer a large `pageSize`
over many small pages. See `rate-limits/amuncore-rate-limits.yml`.

## Errors

Errors return `{success: false, message, error?, requestId?, timestamp?}` — **not** RFC 9457
problem+json, and the machine `error` code is documented as conditional, so branch on the HTTP
status first and treat `error` as a bonus.

- `401 UNAUTHORIZED` — bad or missing key. The message is deliberately ambiguous between "no such
  application" and "wrong key"; do not infer that the appId is wrong.
- `404 NOT_FOUND` — unknown `appId`/`endpointName`, **or** the endpoint is disabled. These are
  indistinguishable.
- `429 RATE_LIMITED` — quota exhausted. Honour `Retry-After`; do not hot-retry.
- `400 BAD_REQUEST` — usually a column name that the endpoint does not expose, or a filter value the
  database rejected.

Full catalogue: `errors/amuncore-problem-types.yml`.
