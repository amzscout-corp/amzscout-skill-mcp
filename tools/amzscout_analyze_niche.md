# amzscout_analyze_niche

## Description
Returns a market snapshot for an Amazon niche/keyword — top products by revenue plus computed aggregates (price/sales/revenue/review distributions, revenue concentration, brand spread). Pure data fetch (no AI analysis).

**Typical use:** Judge niche attractiveness — demand concentration (high top-5 revenue share = winner-takes-all, low = fragmented/open), price bands and where the money sits, review counts as entry moats, brand dominance vs. no-name spread, and standout products (high sales + weak rating/reviews = displacement opportunity).

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `keyword` | string | Yes | Niche, category, or product search keyword |
| `count` | integer | No | How many top products to pull from Amazon (5–100). Default: 100. |
| `filters` | object | No | Filter products by price / sales / revenue / reviews / rating (see below) |
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
  "keyword": "yoga mat",
  "count": 50,
  "filters": { "minEstRev": 5000 },
  "marketplace": "COM"
}
```

## Returned Data (fields may include)
- Top products for the keyword, ranked by revenue
- `revenueTop5SharePercent` — demand concentration indicator
- Price/sales/revenue/review distributions across the niche
- Brand spread / dominance

## Related Tools
- [`amzscout_compare_niches`](./amzscout_compare_niches.md) — head-to-head comparison of 2–5 niches
- [`amzscout_search_products`](./amzscout_search_products.md) — raw keyword search without aggregates
