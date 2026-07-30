# amzscout_analyze_product

## Description
Returns full raw data for a single Amazon product by ASIN — price, estimated sales/revenue, reviews, rating, listing quality, sellers, plus sales/price/revenue history when available. This is a pure data fetch (no AI analysis); the calling model or application is expected to reason over the returned data.

**Typical use:** Audit a product like a sourcing analyst — assess demand trend and seasonality from sales history, pricing direction and margin risk from price history and FBA fees, competition from sellers/reviews, and listing quality from LQS, in order to reach a GO / NO-GO verdict on entering that product.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `asin` | string | Yes | Amazon Standard Identification Number of the product to analyze |
| `marketplace` | string | No | Amazon marketplace code. Default: `COM` (United States). One of: `COM`, `CO_UK`, `DE`, `FR`, `IT`, `ES`, `CA`, `COM_MX`, `COM_BR`, `IN`, `CO_JP`, `COM_AU`, `AE`, `SA` |

## Example Call
```json
{
  "asin": "B07GQF9D1Z",
  "marketplace": "COM"
}
```

## Returned Data (fields may include)
- Current price and pricing history
- Estimated monthly sales and revenue (with history where available)
- Review count, rating, and listing quality score (LQS)
- Seller count and buy box information
- FBA fee estimates

## Related Tools
- [`amzscout_compare_products`](./amzscout_compare_products.md) — compare 2–5 products side by side
- [`amzscout_analyze_product_set`](./amzscout_analyze_product_set.md) — bulk analysis across many ASINs
