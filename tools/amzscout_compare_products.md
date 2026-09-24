# amzscout_compare_products

## Description
Returns side-by-side raw data for 2–5 Amazon products by ASIN — price, sales/revenue estimates, reviews, listing quality, plus history when available. Pure data fetch (no AI analysis); the caller does the comparison.

**Typical use:** Compare demand (estimated sales), revenue, review moat and rating, price positioning, listing quality, and historical trends (growing vs. declining) across a shortlist of products, then determine which is the stronger opportunity and why.

For a single ASIN, use [`amzscout_analyze_product`](./amzscout_analyze_product.md) instead.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `asins` | array of strings | Yes | 2–5 ASINs to compare. Each must be a real Amazon ASIN (format `B0XXXXXXXX`). 0/O-swapped prefixes are auto-corrected. |
| `marketplace` | string | Yes* | Amazon marketplace code — all ASINs are looked up on this one marketplace. *Without it (and without `?marketplace=` in the connection URL) the tool fetches nothing and replies `MARKETPLACE NEEDED`, free of charge: the same ASIN is a separate listing on each marketplace, so it is never assumed to be the US. Ask the user once which marketplace they work on, then reuse it for the rest of the conversation. |

## Example Call

```json
{
  "asins": ["B07GQF9D1Z", "B08XYZ1234"],
  "marketplace": "COM"
}
```

## Returned Data (fields may include)
- Per-product price, estimated sales/revenue, reviews, rating
- Listing quality score per product
- Historical trend data where available

Prices and revenue are in the marketplace's local currency.

## Related Tools
- [`amzscout_analyze_product`](./amzscout_analyze_product.md) — single-product deep dive
- [`amzscout_analyze_product_set`](./amzscout_analyze_product_set.md) — up to 100 ASINs with market-level aggregates
```
