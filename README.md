# AmunCore

Turn any database into a secure REST API — no code, no backend project. Connect a database, pick
tables, and endpoints go live with routing, authentication, validation, pagination, joins, errors,
logs and docs already handled.

- **Website:** https://amuncore.com
- **Databases:** SQL Server, MySQL, MariaDB, PostgreSQL, Oracle, SQLite
- **MCP:** https://amuncore.com/mcp — live, token-gated

Part of the [API Evangelist](https://apievangelist.com) network. Profiled 2026-08-03; every
surface was fetched — see `X-Discovery` in `apis.yml`.

## Why it is interesting

**MCP-native by design, and the implementation is real.** The endpoints a user builds over their
own database become tools an AI assistant can call, under the same keys, permissions and audit
trail. `GET /mcp` returns 405; `POST` with JSON-RPC returns a correct protocol error:

```json
{"jsonrpc":"2.0","error":{"code":-32001,"message":"Unauthorized: missing MCP-Token header"}}
```

That is a working server that simply wants a token — not a marketing route. Its control path
(`/zzz-control-nonsense`) correctly 404s, so probes against this host are trustworthy.

It is also a neat inversion of the usual catalog entry: most providers publish an API, whereas
this one **manufactures** APIs, per tenant, from databases that previously had none.

## Gaps

No platform-level OpenAPI and no `llms.txt`. Worth distinguishing: the product generates a spec
per tenant, which is a different artifact from a contract describing AmunCore's own control
surface.
