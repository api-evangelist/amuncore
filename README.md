# AmunCore (amuncore)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

AmunCore turns a database into a secure REST API without writing a backend. You connect a database, pick tables, and endpoints go live with routing, authentication, validation, pagination, joins, errors, logs and docs already handled — the layer between a database and HTTP that would otherwise be a two-to-six-week project. It supports SQL Server, MySQL, MariaDB, PostgreSQL, Oracle and SQLite, with a visual builder that is the same regardless of the engine underneath. It is MCP-native by design: the endpoints you build become tools an AI assistant can call under the same keys, permissions and audit trail, and the MCP endpoint is live, token-gated and now fronted by RFC 8414/9728 OAuth discovery. A public OpenAPI 3.0.1 describes the five generated CRUD operations; REST auth is an X-Api-Key header. Built and operated by HYNOWorld, with a self-hosted option for regulated deployments. Full CRUD, a free plan forever, and paid tiers from $29/mo.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/amuncore/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/amuncore/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Producing
- **Access:** 3rd-Party

## Tags

- Database
- API Management
- Backend
- No Code
- SQL
- PostgreSQL
- MySQL
- Oracle
- MCP
- Agents
- Data
- SQL Server
- Webhooks
- OpenAPI
- Low Code
- Egypt

## Timestamps

- **Created:** 2026-08-03
- **Modified:** 2026-08-10

## APIs

### AmunCore API

Generated REST API over a connected database — full CRUD across chosen tables, with auth, pagination and docs handled by the platform.

- **Human URL:** [https://amuncore.com](https://amuncore.com)
- **Base URL:** `https://amuncore.com`

#### Tags

- Database
- REST
- No Code
- MCP

#### Properties

- [Website](https://amuncore.com)
- [Documentation](https://amuncore.com/swagger)
- [OpenAPI](openapi/amuncore-dynamic-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/amuncore-dynamic-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/amuncore-dynamic-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Examples](examples/amuncore-dynamic-api-examples.yml)
- [Overlay](overlays/amuncore-dynamic-api-overlay.yaml)
- [Authentication](authentication/amuncore-authentication.yml)
- [O Auth Scopes](scopes/amuncore-scopes.yml)
- [Conventions](conventions/amuncore-conventions.yml)
- [Error Catalog](errors/amuncore-problem-types.yml)
- [Rate Limits](rate-limits/amuncore-rate-limits.yml)
- [Data Model](data-model/amuncore-data-model.yml)
- [M C P Server](mcp/amuncore-mcp.yml)
- [Tool Crosswalk](mcp/amuncore-tool-crosswalk.yml)
- [Webhooks](asyncapi/amuncore-webhooks.yml)
- [Plans](plans/amuncore-plans-pricing.yml)

## Common Properties

- [Agentic Access](agentic-access/amuncore-agentic-access.yml)
- [Domain Security](security/amuncore-domain-security.yml)
- [Website](https://amuncore.com)
- [Documentation](https://amuncore.com/swagger)
- [L L Ms Txt](https://amuncore.com/llms.txt)
- [OpenAPI](openapi/amuncore-dynamic-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Examples](examples/amuncore-dynamic-api-examples.yml)
- [Overlay](overlays/amuncore-dynamic-api-overlay.yaml)
- [L L Ms Txt](llms/amuncore-llms.txt)
- [Well Known](well-known/amuncore-well-known.yml)
- [M C P Server](mcp/amuncore-mcp.yml)
- [Tool Crosswalk](mcp/amuncore-tool-crosswalk.yml)
- [Agent Skill](skills/_index.yml)
- [Authentication](authentication/amuncore-authentication.yml)
- [O Auth Scopes](scopes/amuncore-scopes.yml)
- [Conventions](conventions/amuncore-conventions.yml)
- [Error Catalog](errors/amuncore-problem-types.yml)
- [Rate Limits](rate-limits/amuncore-rate-limits.yml)
- [Lifecycle](lifecycle/amuncore-lifecycle.yml)
- [Data Model](data-model/amuncore-data-model.yml)
- [Conformance](conformance/amuncore-conformance.yml)
- [Trust Center](security/amuncore-trust-center.yml)
- [Sandbox](sandbox/amuncore-sandbox.yml)
- [Webhooks](asyncapi/amuncore-webhooks.yml)
- [Packages](packages/amuncore-packages.yml)
- [Plans](plans/amuncore-plans-pricing.yml)
- [Pricing](https://amuncore.com/#pricing)
- [Sign Up](https://amuncore.com/Register)
- [Login](https://amuncore.com/Auth/Login)
- [Terms of Service](https://amuncore.com/terms.html)
- [Privacy Policy](https://amuncore.com/privacy.html)
- [Support](https://amuncore.com/#contact)
- [About](https://amuncore.com/about.html)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
