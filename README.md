# Offerpad (offerpad)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Offerpad Solutions Inc. (NYSE: OPAD), headquartered in Chandler, Arizona, is a United States iBuyer and licensed residential real estate brokerage that buys homes directly from sellers for cash, renovates them, and resells them, while also offering traditional listing services, a free local move, and a Renovate service. It sits in the middle of the US residential value chain as a principal-position buyer and MLS-participating brokerage in seventeen states, consuming licensed MLS listing data rather than publishing it. Offerpad's API posture is honestly minimal: there is no developer portal, no published API documentation, and no self-serve API access of any kind. Offerpad is **not** listed in the RESO certification directory, holds no RESO Web API or Data Dictionary certification, and serves no OData service document, `$metadata` document, or Universal Property Identifier. Its partner surfaces are human web portals gated behind an intake form and a Mutual Non-Disclosure Agreement. Offerpad does run a real versioned transaction API — `helix.offerpad.com`, behind the Offerpad Connect portal and mobile apps — but it is undocumented, schema-less in public, and closed to third parties; see the Helix entry below.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/offerpad/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/offerpad/refs/heads/main/apis.yml)

## Tags

- Real Estate
- United States
- iBuyer
- PropTech
- Property Listings
- Brokerage
- MLS
- Cash Offer
- Renovation
- Home Buying

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

### Offerpad WordPress REST API

The stock WordPress REST API served by Offerpad's WP Engine-hosted marketing site. Confirmed live and anonymously readable on 2026-07-26 (HTTP 200, `application/json`, 387,532 bytes); the root discovery document self-describes 411 routes across 20 namespaces and advertises WordPress application passwords as its authentication scheme. This is a content-management surface — it is **not** a real estate, listing, valuation, or transaction API, and Offerpad does not document or support it as a developer product. It is catalogued because it is the only publicly callable, machine-describable API found on any Offerpad host.

- **Human URL:** [https://developer.wordpress.org/rest-api/](https://developer.wordpress.org/rest-api/)
- **Base URL:** `https://www.offerpad.com/wp-json`

#### Tags

- CMS
- Content
- WordPress
- Marketing Site

#### Properties

- [OpenAPI](openapi/offerpad-wordpress-wp-v2-openapi.yml) — 128 paths / 227 operations, **derived by API Evangelist** from the live route discovery document; Offerpad publishes no OpenAPI
- [Discovery](openapi/offerpad-wp-json-discovery.json) — WordPress REST API root discovery document, saved verbatim
- [Overlay](overlays/offerpad-wordpress-wp-v2-overlay.yaml)
- [Examples](examples/_index.yml) — real captured responses
- [Data model](data-model/offerpad-data-model.yml)
- [Documentation](https://developer.wordpress.org/rest-api/)

### Offerpad Helix API (private customer backend)

**Offerpad's real transaction API, and it is closed.** Discovered on 2026-07-26 as the `API_URL` constant compiled into the Offerpad Connect single-page-app bundle, `https://helix.offerpad.com` serves the customer identity, cash-offer transaction, contract, document, form and device endpoints that Offerpad Connect and the Offerpad mobile apps call. It is entirely undocumented — no portal, no reference, no schema, no public client registration — and every path except `/.well-known/oauth-authorization-server` returns `{"statusCode":404,"message":"Resource not found"}` anonymously. That one live document is a conformant RFC 8414 authorization-server metadata document delegating to an Okta custom authorization server, which is why Offerpad's *identity* layer is machine-discoverable while none of its *business* capability is. Catalogued as evidence that the capability exists and is deliberately closed, not absent; the endpoint inventory is recorded verbatim from the first-party client with **no schemas inferred**.

- **Human URL:** [https://connect.offerpad.com/auth/login](https://connect.offerpad.com/auth/login)
- **Base URL:** `https://helix.offerpad.com`

#### Properties

- [Observed endpoints](helix/offerpad-helix-observed-endpoints.yml)
- [RFC 8414 authorization server metadata](well-known/offerpad-helix-oauth-authorization-server.json)
- [Authentication](authentication/offerpad-authentication.yml)

## Artifacts

| Artifact | What it records |
|---|---|
| [Authentication](authentication/offerpad-authentication.yml) | WordPress application passwords; Okta OAuth 2.0 authorization code + S256 PKCE; OIDC discovery |
| [OAuth scopes](scopes/offerpad-scopes.yml) | Scopes advertised by the helix and Okta authorization servers |
| [Well-known](well-known/offerpad-well-known.yml) | Every `/.well-known/` probe across every Offerpad host, with status |
| [Conventions](conventions/offerpad-conventions.yml) | Paging (`X-WP-Total` 471 / 236 pages), filtering, caching, error envelope, **no idempotency** |
| [Error catalogue](errors/offerpad-problem-types.yml) | Four live-probed error payloads; not RFC 9457 |
| [Lifecycle](lifecycle/offerpad-lifecycle.yml) | Versioning; no status page, no deprecation policy, no SLA |
| [Conformance](conformance/offerpad-conformance.yml) | RFC 8414/7636/7662/7009/9126/9449/8628/8288 yes; RESO, OData, RFC 9457, AsyncAPI, GraphQL no |
| [Packages](packages/offerpad-packages.yml) | Zero Offerpad packages in npm, PyPI, RubyGems, NuGet, Packagist, crates.io, pkg.go.dev |
| [Domain security](security/offerpad-domain-security.yml) | TLS 1.3, HSTS, DNSSEC, CAA, SPF, DMARC (p=reject) |
| [MCP](mcp/offerpad-mcp.yml) + [crosswalk](mcp/offerpad-tool-crosswalk.yml) | Candidate tool surface bound to real operations (no Offerpad MCP server exists) |
| [Agent skills](skills/_index.yml) | Read site content; search and enumerate markets; assess what access actually exists |
| [Agentic access](agentic-access/offerpad-agentic-access.yml) | Recommended `x-agentic-access` contract for all 227 operations |
| [llms.txt](llms/offerpad-llms.txt) / [API llms.txt](llms/offerpad-llms-api.txt) | Offerpad's own Yoast-generated file, plus an API-surface file |

## RESO Posture

**Not certified.** No RESO reference of any kind exists on Offerpad's public surfaces, and Offerpad does not appear in the RESO certification directory. The full [RESO certificates directory](https://www.reso.org/certificates/) was fetched on 2026-07-26 (HTTP 200, 416,233 bytes) and contains zero occurrences of "Offerpad". Offerpad serves no OData service document, no `$metadata` CSDL document, and makes no reference to the RESO Universal Property Identifier. Offerpad is a *consumer* of MLS data as a licensed MLS-participating brokerage, not a certified data *provider*, so the RESO mandate NAR imposes on Multiple Listing Services does not attach to it.

## Access Gate

**None published.** There is no path by which a developer obtains API access to Offerpad — no portal, no key request, no application form, no partner API tier. The adjacent *business* programs are:

- **Offerpad Direct+** (investor buyers) — create an account in the Direct+ portal, submit the member intake form, and sign a Mutual Non-Disclosure Agreement. The published portal link (`https://offerpad.direct/start/`) does not resolve.
- **Agent Partnership Program / Powered By Offerpad** — no membership or sign-up fee; the referring brokerage or agent is identified in the offer request. Pro and Max tiers get the PBO portal.
- **Homebuilder services** and the **vendor network** — contact forms only.

None of these grants, or mentions, data or API access. Open data: none.

## Common Properties

- [Website](https://www.offerpad.com)
- [About](https://www.offerpad.com/about/)
- [Sell to Offerpad](https://www.offerpad.com/sell/)
- [Offerpad Renovate](https://www.offerpad.com/renovate/)
- [Agent Partnership Program](https://www.offerpad.com/agents/)
- [Powered By Offerpad](https://www.offerpad.com/pbo/)
- [Direct+ Member Onboarding](https://www.offerpad.com/dplusonboarding/)
- [Homebuilder Services](https://www.offerpad.com/hba/)
- [Vendor Network](https://www.offerpad.com/vendors/)
- [Offerpad Connect Portal Login](https://connect.offerpad.com/auth/login)
- [Create an Offerpad Connect account](https://connect.offerpad.com/auth/register)
- [llms.txt](https://www.offerpad.com/llms.txt)
- [Sitemap Index](https://www.offerpad.com/sitemap_index.xml)
- [Articles](https://www.offerpad.com/articles/)
- [Press](https://www.offerpad.com/press/)
- [FAQ](https://www.offerpad.com/faq/)
- [Contact](https://www.offerpad.com/contact/)
- [Brokerage Licenses](https://www.offerpad.com/licenses/)
- [Investor Relations](https://investor.offerpad.com/)
- [Careers](https://www.offerpad.com/careers/)
- [Terms of Use](https://www.offerpad.com/terms-of-use/)
- [Privacy Policy](https://www.offerpad.com/privacy-policy/)
- [GitHub Organization](https://github.com/Offerpad)
- [LinkedIn](https://www.linkedin.com/company/offerpad)
- [Facebook](https://www.facebook.com/offerpad)
- [Instagram](https://instagram.com/offerpad)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
