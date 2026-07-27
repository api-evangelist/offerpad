---
name: Assess what Offerpad API access actually exists
description: Determine, from evidence rather than assumption, which Offerpad capabilities are programmatically reachable — and stop cleanly at the ones that are not.
api: openapi/offerpad-wordpress-wp-v2-openapi.yml
base_url: https://www.offerpad.com/wp-json
operations: [getNamespaceIndex, listTypes, listSettings]
method: generated
generated: '2026-07-26'
---

# Assess what Offerpad API access actually exists

An agent asked to "use the Offerpad API" to sell, buy, value or track a home will fail. This
skill is how to establish that quickly and truthfully, and what to do instead.

## The state of the estate (verified 2026-07-26)

| Surface | Reachable | Notes |
|---|---|---|
| WordPress REST API, `https://www.offerpad.com/wp-json` | **Yes, anonymous** | Marketing-site CMS. 411 routes / 20 namespaces. `getNamespaceIndex` returns the wp/v2 index. |
| Helix backend, `https://helix.offerpad.com` | **No** | Private customer backend. Every path 404s except `/.well-known/oauth-authorization-server`. No public client registration. |
| Okta identity, `https://offerpad.okta.com/oauth2/ausftur6n2aTu6Sur357` | Metadata only | Full OIDC discovery is anonymous; tokens require an Offerpad account and a client_id that is not issued publicly. |
| Developer portal / docs / API subdomains | **No** | `developer.`, `developers.`, `api.`, `docs.`, `status.` are all NXDOMAIN. |
| Partner programmes (Direct+, Powered By Offerpad, homebuilder, vendor) | **No** | Web intake forms behind an NDA; no programmatic interface described. |
| RESO Web API / OData listing feed | **No** | Offerpad is an MLS data consumer, not a certified RESO provider. Zero occurrences in the RESO certificates directory. |

## Steps

1. **Confirm the public surface is live.** Call `getNamespaceIndex` — `GET /wp/v2` — or fetch
   `https://www.offerpad.com/wp-json/` for the full route discovery document. A 200 with a
   `routes` object means the CMS API is up.
2. **Enumerate what content is exposed.** Call `listTypes` — `GET /wp/v2/types` — and read each
   type's `rest_base`. If a capability is not there, it is not exposed publicly.
3. **Prove the credential wall rather than guessing.** Call `listSettings` —
   `GET /wp/v2/settings`. Anonymous callers get HTTP 401
   `{"code":"rest_forbidden","message":"Sorry, you are not allowed to do that.","data":{"status":401}}`.
   That is the boundary: everything requiring the `edit` context or a write is staff-only.
4. **Stop.** Do not probe the helix backend, do not attempt Okta token endpoints, and do not
   submit partner intake forms on a user's behalf. There is no self-serve path behind them.
5. **Report the alternative.** Real estate transaction and listing data comes from the MLS
   ecosystem via RESO-certified providers, or from Offerpad through a signed partner agreement
   initiated at `https://www.offerpad.com/contact/`.

## Rules

- Never claim Offerpad "has an API" without qualifying which one. The public one is a CMS.
- Never fabricate an endpoint for a capability Offerpad has not published.
- A 401 from this estate means *no credential exists to obtain*, not *retry with a key*.

## References

- Auth surfaces: `authentication/offerpad-authentication.yml`
- Discovery documents: `well-known/offerpad-well-known.yml`
- Private backend inventory: `helix/offerpad-helix-observed-endpoints.yml`
- Standards posture: `conformance/offerpad-conformance.yml`
