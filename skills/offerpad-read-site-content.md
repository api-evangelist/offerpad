---
name: Read Offerpad site content
description: Page through Offerpad's published articles and marketing pages over the public WordPress REST API, correctly and without credentials.
api: openapi/offerpad-wordpress-wp-v2-openapi.yml
base_url: https://www.offerpad.com/wp-json
operations: [listPosts, getPostsById, listPages, getPagesById, listCategories, listTags]
method: generated
generated: '2026-07-26'
---

# Read Offerpad site content

## What this gets you, and what it does not

This skill reads the **content of Offerpad's marketing site**. It is the only publicly callable
Offerpad API. It cannot request a cash offer, value a home, read a listing, look at a contract or
touch a transaction — Offerpad publishes no API for any of that (see
`helix/offerpad-helix-observed-endpoints.yml` for the private backend that does).

Base URL: `https://www.offerpad.com/wp-json`. No credentials are required for these reads; the
anonymous `context` is `view`.

## Steps

1. **List articles.** Call `listPosts` — `GET /wp/v2/posts`. Always set `per_page` (max **100**,
   default 10) and iterate `page`. At the time of capture the collection held **471** posts.
   - Read `X-WP-Total` and `X-WP-TotalPages` from the response headers to size the crawl before
     you start, and follow the `Link: <...>; rel="next"` header rather than incrementing blindly.
   - Narrow with `search`, `after` / `before` / `modified_after` / `modified_before` (ISO 8601),
     `categories`, `tags`, `slug`, `orderby` + `order`.
2. **Fetch one article.** Call `getPostsById` — `GET /wp/v2/posts/{id}` with an `id` returned by
   step 1. An unknown id returns HTTP 404 `rest_post_invalid_id`.
3. **List marketing pages.** Call `listPages` — `GET /wp/v2/pages`. Same paging contract. `parent`
   and `menu_order` reconstruct the site hierarchy; `slug` fetches a known page directly.
4. **Fetch one page.** Call `getPagesById` — `GET /wp/v2/pages/{id}`.
5. **Resolve taxonomy.** Call `listCategories` and `listTags` to turn the numeric `categories[]`
   and `tags[]` on a post into names, or filter posts by them in step 1.

## Rules

- **Never exceed `per_page=100`.** `per_page=9999` returns HTTP 400 with
  `{"code":"rest_invalid_param", ... "details":{"per_page":{"code":"rest_out_of_bounds"}}}`.
  Read `data.details[param].message` for the constraint that failed.
- **Do not send `context=edit`.** It requires an authenticated WordPress user and returns
  HTTP 401 `rest_forbidden`. Offerpad issues no self-serve credential, so a 401 here is terminal —
  do not retry it, and do not attempt any write route.
- **Use `_fields`** to trim the payload (post objects are large) and **`_embed`** to inline the
  author, featured media and terms instead of making follow-up calls.
- **There is no rate-limit header.** Nothing signals a quota, but the host sits behind WP Engine
  and Cloudflare — throttle yourself, and back off on any 429 or 5xx.
- Responses are edge-cached (`Cache-Control: max-age=600, must-revalidate`), so a freshly
  published article can lag by up to ten minutes.
- Error envelope is **not RFC 9457**. It is `{"code","message","data":{"status"}}` —
  see `errors/offerpad-problem-types.yml`.
- There is **no idempotency contract** on this API; only method semantics apply.

## References

- Conventions: `conventions/offerpad-conventions.yml`
- Errors: `errors/offerpad-problem-types.yml`
- Entity graph: `data-model/offerpad-data-model.yml`
- Real captured responses: `examples/`
