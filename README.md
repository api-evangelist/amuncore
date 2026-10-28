# AmunCore

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

**Areas:** Database · API Management · Backend · No-Code · SQL · PostgreSQL · MySQL · Oracle · MCP · Agents · Data · SQL Server

## AmunCore on APIs.io

Everything profiled for AmunCore is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/amuncore/](https://apis.io/providers/amuncore/)** — or go straight to one of the APIs or properties below.

### APIs (1)

- [AmunCore Dynamic API](https://apis.io/apis/amuncore/amuncore-dynamic-api-api/) — Generated CRUD over a table or view exposed as an endpoint on a registered AmunCore application.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Amuncore Webhooks](https://apis.io/asyncapis/amuncore/amuncore-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [amuncore](https://apis.io/servers/amuncore/amuncore/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Amuncore Agentic Access](https://apis.io/agentic-access/amuncore/amuncore-agentic-access/)

#### Collections (1)

Postman and Open Collection request collections.

- [AmunCore API Engine: Dynamic API](https://apis.io/collections/amuncore/open-amuncore-dynamic-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Amuncore Dynamic Api Overlay](https://apis.io/overlays/amuncore/amuncore-dynamic-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Amuncore Authentication](https://apis.io/security/amuncore/amuncore-authentication/)
- [Amuncore Domain Security](https://apis.io/security/amuncore/amuncore-domain-security/)
- [Amuncore Trust Center](https://apis.io/security/amuncore/amuncore-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Amuncore Scopes](https://apis.io/scopes/amuncore/amuncore-scopes/)

#### Plans and pricing (2)

Published plans, tiers and prices.

- [Amuncore Plans](https://apis.io/plans/amuncore/amuncore-plans/)
- [Amuncore Plans Pricing](https://apis.io/plans/amuncore/amuncore-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Amuncore Rate Limits](https://apis.io/rate-limits/amuncore/amuncore-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://amuncore.com)
- [Documentation](https://amuncore.com/swagger)
- [Pricing](https://amuncore.com/#pricing)
- [Sign up](https://amuncore.com/Register)
- [Support](https://amuncore.com/#contact)
- [Terms of service](https://amuncore.com/terms.html)
- [Privacy policy](https://amuncore.com/privacy.html)

## API Evangelist rating

**Kin Score 54.9** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 66.7 |
| Contract quality | 56.6 |
| Contract governance | 18.2 |
| Operational transparency | 39.5 |
| Developer ergonomics | 35.1 |
| Access clarity | 84.2 |

**Agent readiness 56.5** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 39.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/amuncore/](https://apis.io/providers/amuncore/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for AmunCore: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/amuncore/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
