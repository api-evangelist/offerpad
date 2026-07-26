# Offerpad (offerpad)

Offerpad Solutions Inc. (NYSE: OPAD), headquartered in Chandler, Arizona, is a United States iBuyer and licensed residential real estate brokerage that buys homes directly from sellers for cash, renovates them, and resells them, while also offering traditional listing services, a free local move, and a Renovate service. It sits in the middle of the US residential value chain as a principal-position buyer and MLS-participating brokerage in seventeen states, consuming licensed MLS listing data rather than publishing it. Offerpad's API posture is honestly minimal: there is no developer portal, no published API documentation, and no self-serve API access of any kind. Offerpad is **not** listed in the RESO certification directory, holds no RESO Web API or Data Dictionary certification, and serves no OData service document, `$metadata` document, or Universal Property Identifier. Its partner surfaces are human web portals gated behind an intake form and a Mutual Non-Disclosure Agreement.

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

- [OpenAPI](openapi/offerpad-wp-json-discovery.json) — WordPress REST API root discovery document (not an OpenAPI document)
- [Documentation](https://developer.wordpress.org/rest-api/)

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
