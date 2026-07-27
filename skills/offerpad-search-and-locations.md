---
name: Search Offerpad content and enumerate its markets
description: Use the public WordPress search route and page hierarchy to find Offerpad content and to enumerate the cities Offerpad publishes a sell landing page for.
api: openapi/offerpad-wordpress-wp-v2-openapi.yml
base_url: https://www.offerpad.com/wp-json
operations: [listSearch, listPages, getPagesById, listPosts, listTypes]
method: generated
generated: '2026-07-26'
---

# Search Offerpad content and enumerate its markets

## What this gets you, and what it does not

Offerpad publishes no markets API. The only public, machine-readable way to see which cities
Offerpad talks about is the marketing site's own page tree: each market has a
`/sell/<city>-<state>/` landing page (for example `/sell/houston-tx/`, `/sell/columbia-sc/`,
`/sell/henderson-nv/`). This skill reads those pages. **A published landing page is a marketing
signal, not an authoritative statement that Offerpad is buying in that market today** — treat it
as a lead, and confirm against `https://www.offerpad.com/locations/`.

The private backend does expose `customer/v3/cash-offer-transactions/markets`, which is the real
answer, but it is undocumented and requires an Offerpad customer credential — see
`helix/offerpad-helix-observed-endpoints.yml`. Do not attempt it.

## Steps

1. **Full-text search.** Call `listSearch` — `GET /wp/v2/search?search=<terms>`. Narrow with
   `type` (`post`, `term`, `post-format`) and `subtype`. Results are lightweight stubs carrying
   `id`, `title`, `url`, `type` and `subtype`.
2. **Resolve a hit.** Use the stub's `subtype` to pick the right follow-up: `getPagesById` for a
   page, `getPostsById` for an article.
3. **Enumerate market landing pages.** Call `listPages` — `GET /wp/v2/pages` with
   `per_page=100`, paging until `X-WP-TotalPages` is exhausted, and keep entries whose `link`
   starts with `https://www.offerpad.com/sell/`. The `slug` is the `<city>-<state>` key.
4. **Confirm the hierarchy.** The `/sell/` hub page's `id` is the `parent` of the market pages;
   filter `listPages` by that `parent` to get the set directly instead of matching on URL.
5. **Check what else the site exposes.** Call `listTypes` — `GET /wp/v2/types` — to see every
   registered content type and its `rest_base` before assuming a content set is missing.

## Rules

- Page with `per_page` ≤ **100** and follow the `Link` `rel="next"` header; read `X-WP-Total` /
  `X-WP-TotalPages` first.
- Search is not fuzzy-ranked across everything — it is WordPress core search. Set
  `search_semantics=exact` on `listPosts` when you need an exact-phrase match.
- Never send `context=edit` and never call a write route: both return HTTP 401 `rest_forbidden`
  and no self-serve credential exists.
- Do not present marketing-page counts as Offerpad's operating footprint. The
  company's own published statement of coverage is `https://www.offerpad.com/locations/`.

## References

- Conventions and paging: `conventions/offerpad-conventions.yml`
- Errors: `errors/offerpad-problem-types.yml`
- Captured search response: `examples/offerpad-wp-v2-search-response.json`
