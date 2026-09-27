# amzscout_locate_asin

## Description
Finds which Amazon marketplaces list an ASIN and returns its product link on every marketplace. For each marketplace where the product is listed it also returns the title, the price in that marketplace's local currency, and estimated monthly sales. The same ASIN is a separate listing on each marketplace, with its own price, sales and reviews. This is a pure data fetch (no AI analysis).

**Typical use:** Answer "where / on which Amazon marketplaces is this product sold?", or give a product's links on other marketplaces. Call it only when the user asks this question. You don't need it to pick a marketplace for an analysis: ask the user once which marketplace they work on and reuse it for the rest of the conversation.

**Cost:** 1,000 tokens per marketplace checked, per ASIN (14,000 tokens for one ASIN). Nothing is charged when the ASIN is not listed on any marketplace, and marketplaces whose lookup failed are not charged.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `asins` | string[] | Yes | 1–5 ASINs to locate (`B0` + 8 characters). Pass several only when they will be analyzed together — a marketplace counts as listed when it carries all of them |

## Example Call
```json
{
  "asins": ["B0CLVN1TYZ"]
}
```

## Returned Data (fields may include)
- `listedOn` — codes of the marketplaces that list all requested ASINs, most active first
- Per marketplace (all 14): code, country, Amazon domain, currency, whether it is listed, whether the lookup succeeded
- Per ASIN on each marketplace: product link (`https://www.<domain>/dp/<ASIN>`), whether it is listed there, title, price in local currency, estimated monthly sales

Checked marketplaces: `COM` (US), `CO_UK`, `DE`, `FR`, `IT`, `ES`, `CA`, `COM_MX`, `COM_BR`, `IN`, `CO_JP`, `COM_AU`, `AE`, `SA`.

## Related Tools
- [`amzscout_analyze_product`](./amzscout_analyze_product.md) — full data for the product on the marketplace the user picks
- [`amzscout_reseller_amazon`](./amzscout_reseller_amazon.md) — buy box and offer data for the product on one marketplace
- [`amzscout_get_keywords`](./amzscout_get_keywords.md) — keywords the product ranks for on one marketplace
