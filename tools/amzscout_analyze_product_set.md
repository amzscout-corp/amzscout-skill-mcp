# amzscout_analyze_product_set

## Description
Returns raw data across an explicit set of 2–100 ASINs — product rows plus computed aggregates (price/sales/revenue/review distributions, revenue concentration, brand spread). Pure data fetch (no AI analysis).

**Typical use:** Treat the set as a mini-market — segment products into groups, spot where demand concentrates, flag outliers (price, sales, review anomalies), and summarize group-level signals.

To discover products from a keyword instead of a fixed ASIN list, use [`amzscout_analyze_niche`](./amzscout_analyze_niche.md).

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `asins` | array of strings | Yes | 2–100 ASINs to fetch as a set (format `B0XXXXXXXX`). 0/O-swapped prefixes are auto-corrected. |
| `marketplace` | string | No | Amazon marketplace code. Default: `COM` (United States). |

## Example Call
```json
{
  "asins": ["B07GQF9D1Z", "B08XYZ1234", "B09ABCD567"],
  "marketplace": "COM"
}
```

## Returned Data (fields may include)
- Per-product rows (price, sales, revenue, reviews, rating)
- Aggregate statistics: price/sales/revenue distributions
- Revenue concentration (e.g. top-N share of total revenue)
- Brand spread across the set

## Related Tools
- [`amzscout_compare_products`](./amzscout_compare_products.md) — focused 2–5 product comparison
- [`amzscout_analyze_niche`](./amzscout_analyze_niche.md) — discover products by keyword instead of ASIN list
