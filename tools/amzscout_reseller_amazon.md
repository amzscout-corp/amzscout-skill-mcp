# amzscout_reseller_amazon

## Description
Returns buy box, competing offers and price/rank statistics for one Amazon product by ASIN. This covers who owns the buy box and at what price, how ownership has split between sellers, and FBA vs FBM offer counts. It also includes the live offer list with seller names and ratings, price levels over 30/90/180/365 days with all-time extremes, sales-rank drops, out-of-stock share, and buy box ownership history. The tool is built for reseller and online-arbitrage questions, not private-label research: use [`amzscout_analyze_product`](./amzscout_analyze_product.md) for demand and revenue estimates. This is a pure data fetch (no AI analysis).

**Typical use:** Judge whether a listing is worth reselling:
- Amazon in the buy box, or a single seller holding most of it, means little room.
- Many FBA offers means price competition.
- A high out-of-stock share means supply gaps you could fill.
- Rank drops indicate how fast it sells.

**How to call:** First call it without `sections`. The compact summary answers most questions, and the reply lists which sections carry data for this ASIN. Request specific sections only when the summary is not enough.

**Cost:** 15,000 tokens per ASIN, flat, whatever sections are requested. Nothing is charged when there is no data for the ASIN.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `asin` | string | Yes | Amazon Standard Identification Number of the product |
| `marketplace` | string | Yes* | Amazon marketplace code. *Without it (and without `?marketplace=` in the connection URL) the tool fetches nothing and replies `MARKETPLACE NEEDED`, free of charge — ask the user once which marketplace they work on, then reuse it for the conversation. Covered: `COM`, `CO_UK`, `DE`, `FR`, `IT`, `ES`, `CA`, `COM_MX`, `COM_BR`, `IN`, `CO_JP` (no data for `COM_AU`, `AE`, `SA`) |
| `sections` | string[] | No | Parts of the data to return in full. Omit for the summary plus the list of available sections. Options below |

### Sections

| Section | Contents |
|---------|----------|
| `buybox` | Who holds the buy box now, at what price, and how ownership split between sellers |
| `competition` | Offer counts by fulfilment, cheapest FBA/FBM sellers, and the live offer list with seller names |
| `pricing` | Current / 30 / 90 / 180 / 365-day price levels plus all-time low and high, per offer type |
| `rank` | Sales rank levels and rank-drop counts — the closest available proxy for sales velocity |
| `availability` | How often the listing had no buyable offer, and the visible stock of Amazon and the buy box winner |
| `history` | Buy box ownership changes over time, resolved to seller names |

## Example Call
```json
{
  "asin": "B0B7CPSN2K",
  "marketplace": "COM"
}
```

With sections:
```json
{
  "asin": "B0B7CPSN2K",
  "marketplace": "COM",
  "sections": ["buybox", "competition"]
}
```

## Returned Data (fields may include)
- Summary: buy box owner and price, whether Amazon or an FBA seller holds it, top seller's and Amazon's share of the buy box, total / FBA / FBM offer counts, unique buy box sellers, 90-day out-of-stock share, current sales rank and 90-day rank drops
- `availableSections` — sections that carry data for this ASIN
- Requested sections in full (see table above)
- When the offer data was last refreshed

Prices are in the marketplace's local currency.

## Related Tools
- [`amzscout_analyze_product`](./amzscout_analyze_product.md) — demand, revenue and listing quality for the same product
- [`amzscout_locate_asin`](./amzscout_locate_asin.md) — which marketplaces list the product
