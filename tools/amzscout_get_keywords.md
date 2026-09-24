# amzscout_get_keywords

## Description
Amazon keyword / SEO / PPC data for either a single product (ASIN-scope — terms the product ranks for) or a niche/category (keyword-scope — search data around the term). Returns keyword rows with search volume, CPC, and competition where available. Pure data fetch (no AI analysis).

**Typical use:** Pick high-volume / low-competition terms for SEO and PPC targeting, use CPC as ad-cost pressure, sum search volumes to gauge niche demand. For ASIN-scope, check organic vs. sponsored ranks to spot listing-optimization gaps.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `asin` | string | No* | ASIN-scope: keywords this product ranks for |
| `keyword` | string | No* | Keyword-scope: search data around this niche term (2–100 chars) |
| `marketplace` | string | Depends | Amazon marketplace code. **With `asin`: required** — without it (and without `?marketplace=` in the connection URL) the tool fetches nothing and replies `MARKETPLACE NEEDED`, free of charge; ask the user once which marketplace they work on and reuse it for the conversation. **With `keyword`: optional**, default `COM` (United States). |

\* Provide either `asin` or `keyword` to scope the request.

## Example Call (ASIN scope)
```json
{
  "asin": "B07GQF9D1Z",
  "marketplace": "COM"
}
```

## Example Call (keyword scope)
```json
{
  "keyword": "yoga mat"
}
```

## Returned Data (fields may include)
- Keyword rows with search volume, CPC, competition level
- For ASIN scope: organic and sponsored rank per keyword

CPC is in the marketplace's local currency.

## Related Tools
- [`amzscout_analyze_niche`](./amzscout_analyze_niche.md) — broader niche market snapshot
