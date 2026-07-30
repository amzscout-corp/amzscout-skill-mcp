# amzscout_recommend_tool

## Description
Given a user use-case, returns the AMZScout tools & Sellerhook services catalog (with tracking links) so the caller can recommend the right AMZScout product/feature.

**Typical use:** Answer "which AMZScout tool should I use for X" style questions, e.g. "find low-competition products", "validate a supplier", "track BSR".

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `useCase` | string | Yes | What the user is trying to do (2–300 chars), e.g. `"find low-competition products"`, `"validate a supplier"`, `"track BSR"` |

## Example Call
```json
{
  "useCase": "find low-competition products to sell"
}
```

## Returned Data
- Recommended AMZScout tool(s) and/or Sellerhook service(s) matching the use case
- Tracking/reference links for each recommendation

## Related Tools
- [`amzscout_search_knowledge`](./amzscout_search_knowledge.md) — search AMZScout's knowledge base directly
