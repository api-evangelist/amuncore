---
generated: '2026-08-10'
method: generated
name: Expose a database table as an API over MCP
description: >-
  Use the AmunCore MCP control-plane tools to create an application, publish an
  endpoint over a table, and hand out a key — the flow that makes AmunCore
  unusual, because the agent builds the API rather than only calling it.
api: mcp/amuncore-mcp.yml
operations: [create_application, create_endpoint, toggle_endpoint, list_endpoints, regenerate_api_key, call_api]
source: >-
  Tool names quoted verbatim from https://amuncore.com/llms.txt and recorded in
  mcp/amuncore-mcp.yml; the REST binding of call_api is mapped in
  mcp/amuncore-tool-crosswalk.yml.
---

# Expose a database table as an API over MCP

Most providers give an agent tools that *call* an API. AmunCore gives an agent tools that *create*
one. Eleven of its twelve MCP tools operate on the control plane, so an assistant can provision an
application, publish an endpoint over a table, and rotate the key that guards it.

That is genuinely useful and genuinely sharp-edged. Read the consequence notes below before wiring
this into anything autonomous.

## Connect

- Endpoint: `https://amuncore.com/mcp` (HTTP transport). A local **stdio** transport is also
  documented for desktop assistants.
- Auth: an `MCP-Token` header, **or** an OAuth 2.0 bearer token with the `mcp` scope. The endpoint
  answers an unauthenticated call with JSON-RPC `-32001` and
  `WWW-Authenticate: Bearer resource_metadata="https://amuncore.com/.well-known/oauth-protected-resource"`,
  so an agent can discover the authorization server without being told.
- The OAuth flow is authorization_code with PKCE `S256`, and dynamic client registration is
  available at `https://amuncore.com/oauth/register`. See `scopes/amuncore-scopes.yml`.
- One MCP configuration exists per company; everything you touch is scoped to that tenancy.

## Steps

1. **Enumerate first** — `list_applications`, then `list_endpoints` for the application you care
   about. Do not create anything before you have checked whether it already exists; there is no
   idempotency anywhere in this platform.
2. **Create the application** — `create_application`, if one does not already exist for the target
   database.
3. **Publish the endpoint** — `create_endpoint`. This is the consequential step: it selects the
   table and the columns that become reachable over HTTP. **Column selection is the data-minimisation
   control** — a column you include is a column any holder of that application's key can read. The
   provider's own homepage example makes the point by excluding `internal_notes` and `credit_card`
   from a `customers` endpoint.
4. **Verify before you enable** — read the endpoint back with `list_endpoints` and confirm the
   column list, then use `toggle_endpoint` to bring it live. `toggle_endpoint` is also the kill
   switch.
5. **Call the data** — `call_api`, which is the single tool bound to the published REST contract. It
   fans out to `DynamicApi_GetList`, `DynamicApi_GetById`, `DynamicApi_Post`, `DynamicApi_Put` and
   `DynamicApi_Delete`; those operations' parameters are its real input contract. See
   `mcp/amuncore-tool-crosswalk.yml`.

## Consequence classes — do not treat these tools as equivalent

| Tool | Consequence |
|---|---|
| `list_applications`, `get_application`, `list_endpoints`, `get_dashboard_stats`, `get_audit_logs`, `get_license_status`, `check_plan_limits` | read-only |
| `create_application`, `create_endpoint` | **exposes data over HTTP** — irreversible in effect once a key is out |
| `toggle_endpoint` | availability — can take a live API down |
| `regenerate_api_key` | **breaks every existing consumer of that application immediately** |
| `call_api` | reads *or writes* the customer's live database, including deletes |

`regenerate_api_key` and `create_endpoint` should require a human confirmation step in any agent
harness. AmunCore documents no confirmation, no dry-run and no undo for either, and no REST
equivalent exists that a reviewer could audit against.

## Budgeting

Before a burst of `call_api`, call `check_plan_limits`. It is the only way to read remaining quota
ahead of time — there is no REST equivalent — and the quota is a plan allowance, so exhausting it
returns `429` until the billing period rolls. See `rate-limits/amuncore-rate-limits.yml`.

## Audit

Every MCP tool call is written to the same audit trail as REST traffic, and `get_audit_logs` reads
it back. If you are running an agent against this platform, that log is your only after-the-fact
record of what it did.

## Known limits

- `tools/list` is auth-gated, so the per-tool `inputSchema` cannot be read anonymously. The tool
  names and descriptions above are the provider's own, from `llms.txt`; argument shapes require an
  authenticated introspection call.
- MCP access is a **paid feature** — the pricing table lists AI/MCP as included on Pro.
