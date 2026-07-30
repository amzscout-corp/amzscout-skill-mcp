# amzscout_find_by_brand

## Description
Lists products under a specific Amazon brand. Pre-validates the brand name via a cached AI check, then filters keyword-search results to rows whose `brand` field actually matches. If there's no match, returns the brands that did appear in the keyword pool so callers can suggest alternatives.

**Typical use:** Assess a brand's Amazon footprint — lineup breadth, price range, which products carry the revenue, and how strong its review moat is.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `brand` | string | Yes | Amazon brand name to search by (2–80 chars) |
| `count` | integer | No | How many products to return (1–100). Default: 100. |
| `filters` | object | No | Filter products by price / sales / revenue / reviews / rating |
| `sort` | string | No | Result sort order: `revenue`, `sales`, `newest`, `rating`, `reviews`. Default: `revenue`. |
| `marketplace` | string | No | Amazon marketplace code. Default: `COM` (United States). |

## Example Call
```json
{
  "brand": "Anker",
  "count": 50,
  "sort": "revenue"
}
```

## Returned Data (fields may include)
- Matched products under the brand (price, sales, revenue, reviews, rating)
- On no exact match: list of brands actually found in the keyword pool, for suggesting alternatives

## Related Tools
- [`amzscout_search_products`](./amzscout_search_products.md) — general keyword search
