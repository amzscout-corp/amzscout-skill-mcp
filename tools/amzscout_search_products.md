# amzscout_search_products

## Description
Keyword search against Amazon — returns the top N products with price, sales, revenue, reviews, and rating. Pure data fetch (no AI analysis).

Best when raw product rows are needed with a specific sort order or filters. [`amzscout_analyze_niche`](./amzscout_analyze_niche.md) additionally returns computed market aggregates on top of the same rows.

**Typical use:** Scan the rows for demand leaders, price clusters, and low-review listings that still sell — those are the entry-opportunity signals.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `query` | string | Yes | Search keyword / phrase (2–100 chars) |
| `count` | integer | No | How many products to return (1–100). Default: 100. |
| `filters` | object | No | Filter products by price / sales / revenue / reviews / rating |
| `sort` | string | No | Result sort order: `revenue`, `sales`, `rating`, `reviews` (descending); `price-low` / `price-high`; `newest` (by first-listed date). Default: `revenue`. |
| `marketplace` | string | No | Amazon marketplace code. Default: `COM` (United States). |

### `filters` object
| Field | Type | Description |
|-------|------|--------------|
| `minPrice` / `maxPrice` | number | Unit price range (USD) |
| `minEstSales` / `maxEstSales` | number | Estimated monthly sales range (units) |
| `minEstRev` / `maxEstRev` | number | Estimated monthly revenue range (USD) |
| `minReviews` / `maxReviews` | number | Review count range |
| `minRating` / `maxRating` | number | Average rating range (0–5) |

## Example Call
```json
{
  "query": "resistance bands",
  "count": 30,
  "sort": "revenue",
  "filters": { "maxReviews": 200 }
}
```

## Returned Data (fields may include)
- Product rows: title, ASIN, price, estimated sales/revenue, review count, rating

## Related Tools
- [`amzscout_analyze_niche`](./amzscout_analyze_niche.md) — same search plus market-level aggregates
- [`amzscout_find_by_brand`](./amzscout_find_by_brand.md) — search scoped to a specific brand
