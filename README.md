# AmunCore

Turn any database into a secure REST API — no code, no backend project. Connect a database, pick
tables, and endpoints go live with routing, authentication, validation, pagination, joins, errors,
logs and docs already handled.

- **Website:** https://amuncore.com
- **API reference:** https://amuncore.com/swagger — public Swagger UI, no sign-in
- **OpenAPI:** https://amuncore.com/openapi.json — OpenAPI 3.0.1, 5 operations
- **MCP:** https://amuncore.com/mcp — live, token-gated, OAuth-discoverable
- **Databases:** SQL Server, MySQL, MariaDB, PostgreSQL, Oracle, SQLite
- **Operator:** HYNOWorld, Alexandria, Egypt

Part of the [API Evangelist](https://apievangelist.com) network. First profiled 2026-08-03,
re-probed and enriched 2026-08-10; every surface was fetched — see `X-Discovery` and `X-Reprobe`
in `apis.yml`.

## What changed between the two passes

This is the interesting part of the profile. On 2026-08-03 the OpenAPI, `llms.txt` and both OAuth
discovery documents all returned 404. On 2026-08-10 all four return 200. **AmunCore went from a
marketing site with a real MCP endpoint to a fully contract-bearing provider in seven days** — and
published none of it, because there is no changelog and no status page to publish it in.

## Why it is interesting

**MCP-native by design, and the implementation is real.** `GET /mcp` returns 405; `POST` with
JSON-RPC returns a correct protocol error and now a proper auth challenge:

```
HTTP/2 401
www-authenticate: Bearer resource_metadata="https://amuncore.com/.well-known/oauth-protected-resource"

{"jsonrpc":"2.0","error":{"code":-32001,"message":"Unauthorized: missing MCP-Token header"}}
```

That is a working server with discoverable authorization — RFC 8414 and RFC 9728 metadata, PKCE
`S256`, RFC 7591 dynamic client registration — not a marketing route. Its control path
(`/zzz-control-nonsense`) correctly 404s, so probes against this host are trustworthy.

**The agent surface builds APIs; it does not only call them.** Eleven of the twelve published MCP
tools are control-plane — `create_application`, `create_endpoint`, `toggle_endpoint`,
`regenerate_api_key`, `get_audit_logs`. Only `call_api` maps onto the public REST contract. An
assistant here can manufacture a new HTTP API over a database table. See
`mcp/amuncore-tool-crosswalk.yml` for the full binding, and
`skills/amuncore-expose-a-table-over-mcp.md` for the consequence classes that implies.

It is also a neat inversion of the usual catalog entry: most providers publish an API, whereas this
one **manufactures** APIs, per tenant, from databases that previously had none. That is why
`components.schemas` in its OpenAPI is empty — the record shape is unknowable until a customer
configures it.

## Gaps worth naming

- **No changelog, no status page, no deprecation policy.** For a platform whose value proposition is
  "we maintain the API layer so you don't", there is no public change or incident record at all.
  `lifecycle/amuncore-lifecycle.yml`.
- **No idempotency.** No key header, no replay semantics. A retried `POST` inserts twice.
  `conventions/amuncore-conventions.yml`.
- **No test mode and no sandbox.** Writes go to the customer's live database; keys are `ak_live_`
  with no test counterpart. `sandbox/amuncore-sandbox.yml`.
- **No SDKs in any registry.** Eleven registry lookups, all 404 — the developer story is generated
  code snippets, not a versioned client. `packages/amuncore-packages.yml`.
- **No `security.txt` and no vulnerability-disclosure route.** The security page is good and
  unusually honest, but a researcher has nowhere to report.
  `security/amuncore-trust-center.yml`.
- **No A2A agent card**, at either the canonical or the legacy well-known path.
- **Help centre is customer-only** — `/Help` serves the sign-in page. `llms.txt` is the public
  documentation.

## Credit where due

The security page carries an explicitly labelled **"Honest roadmap"** stating that independent
penetration testing, ISO 27001 alignment, SSO and SIEM export are *not yet implemented*. Publishing
what you have not built is rarer than publishing what you have, and it is the reason this profile
claims no certifications on their behalf.
