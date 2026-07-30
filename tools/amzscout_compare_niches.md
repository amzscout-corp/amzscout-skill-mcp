# amzscout_compare_niches

## Description
Returns raw head-to-head data for 2–5 Amazon niches / category keywords — per-niche product sets plus computed aggregates (price/sales/revenue distributions, revenue concentration, brand spread). Pure data fetch (no AI analysis).

**Typical use:** Weigh demand (total estimated revenue/sales) against competition (review levels, brand concentration) and price levels per niche, then determine which niche is the better opportunity for a new seller and under what conditions.

For ASIN-level comparison instead of niches, use [`amzscout_compare_products`](./amzscout_compare_products.md).

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `keywords` | array of strings | Yes | 2–5 niches / category keywords to compare, e.g. `["yoga mat", "resistance bands"]` |
| `count` | integer | No | Products fetched per niche (3–25). Default: 10. |
| `marketplace` | string | No | Amazon marketplace code. Default: `COM` (United States). |

## Example Call
```json
{
  "keywords": ["yoga mat", "resistance bands"],
  "count": 15,
  "marketplace": "COM"
}
```

## Returned Data (fields may include)
- Per-niche product sets with price/sales/revenue/reviews
- Aggregate stats per niche (revenue concentration, brand spread)
- Side-by-side comparison basis for demand vs. competition

## Related Tools
- [`amzscout_analyze_niche`](./amzscout_analyze_niche.md) — deep dive on a single niche
- [`amzscout_compare_products`](./amzscout_compare_products.md) — ASIN-level comparison
