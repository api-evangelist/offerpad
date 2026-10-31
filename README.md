# Offerpad

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

Offerpad Solutions Inc. (NYSE: OPAD), headquartered in Chandler, Arizona, is a United States iBuyer and licensed residential real estate brokerage that buys homes directly from sellers for cash, renovates them, and resells them, while also offering traditional listing services, a free local move, and a Renovate service. It sits in the middle of the US residential value chain as a principal-position buyer and MLS-participating brokerage in seventeen states, consuming licensed MLS listing data rather than publishing it. Offerpad's API posture is honestly minimal: there is no developer portal, no published API documentation, and no self-serve API access of any kind. The developer., developers., api. and docs. subdomains do not resolve, and /developers, /api, /docs, /openapi.json, /swagger.json and /api-docs all return 404. Offerpad is NOT listed in the RESO certification directory, holds no RESO Web API or Data Dictionary certification, and serves no OData service document, $metadata document, or Universal Property Identifier. Its partner surfaces — the Direct+ investor-buyer program, the Powered By Offerpad agent partner portal, the homebuilder program and the vendor network — are human web portals gated behind an intake form and a Mutual Non-Disclosure Agreement, with no programmatic interface described anywhere. The only publicly callable, self-describing API on the domain is the stock WordPress REST API of the marketing site. Offerpad does, however, run a real versioned transaction API privately: helix.offerpad.com serves the customer identity, cash-offer transaction, contract, document and form endpoints behind the Offerpad Connect portal and mobile apps, and it publishes a live RFC 8414 authorization-server metadata document delegating to Okta — so Offerpad's identity layer is machine discoverable while none of its business capability is documented, schema-backed or obtainable by a third party.

**Areas:** Real Estate · United States · iBuyer · PropTech · Property Listings · Brokerage · MLS · Cash Offer · Renovation · Home Buying

## Offerpad on APIs.io

Everything profiled for Offerpad is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/offerpad/](https://apis.io/providers/offerpad/)** — or go straight to one of the APIs or properties below.

### APIs (2)

- [Offerpad Helix API (private customer backend)](https://apis.io/apis/offerpad/offerpad-helix-api/) — Offerpad's real transaction API, and it is closed. Discovered on 2026-07-26 as the API_URL constant compiled into the Offerpad Connect single-page-app…
- [Offerpad Website (WordPress REST)](https://apis.io/apis/offerpad/offerpad-com-website-wordpress-rest/) — The public WordPress REST API (wp-json) of the Offerpad website at www.offerpad.com: the route index of the site's content management system, catalogued as…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [offerpad-wordpress](https://apis.io/servers/offerpad/offerpad-wordpress/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Offerpad Agentic Access](https://apis.io/agentic-access/offerpad/offerpad-agentic-access/)

#### Examples (1)

Example requests and responses.

- [Offerpad Wp V2 Types Response](https://apis.io/examples/offerpad/offerpad-wp-v2-types-response/)

#### Collections (2)

Postman and Open Collection request collections.

- [Moved to /providers/offerpad/](https://apis.io/collections/offerpad/open-offerpad-wordpress-wp-v2/)
- [API Collection](https://apis.io/collections/offerpad/open-offerpad-wp-json-discovery/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Offerpad Authentication](https://apis.io/security/offerpad/offerpad-authentication/)
- [Offerpad Domain Security](https://apis.io/security/offerpad/offerpad-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Offerpad Scopes](https://apis.io/scopes/offerpad/offerpad-scopes/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.offerpad.com)
- [Sign up](https://connect.offerpad.com/auth/register)
- [Support](https://www.offerpad.com/faq/)
- [Blog](https://www.offerpad.com/articles/)
- [Terms of service](https://www.offerpad.com/terms-of-use/)
- [Privacy policy](https://www.offerpad.com/privacy-policy/)
- [GitHub](https://github.com/Offerpad)

## API Evangelist rating

**Kin Score 26.0** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 64.3 |
| Contract quality | 0.0 |
| Contract governance | 18.2 |
| Operational transparency | 5.3 |
| Developer ergonomics | 39.9 |
| Access clarity | 34.2 |

**Agent readiness 16.4** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 38.0** — Securities & Market Data

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/offerpad/](https://apis.io/providers/offerpad/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Offerpad: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/offerpad/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
