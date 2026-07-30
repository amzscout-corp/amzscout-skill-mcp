# amzscout_search_knowledge

## Description
TF-IDF search across the AMZScout knowledge base (Amazon-seller tutorials, brand reference, glossary). Returns the top-K relevant chunks with title, source URL, and text.

**Typical use:** Ground answers in factual AMZScout reference material — e.g. definitions, how-to guides, terminology.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `query` | string | Yes | Search phrase (2–300 chars) |
| `topK` | integer | No | How many knowledge chunks to return (1–20). Default: 5. |

## Example Call
```json
{
  "query": "what is FBA listing quality score",
  "topK": 5
}
```

## Returned Data (fields may include)
- Title of the source article/chunk
- Source URL
- Relevant text excerpt

## Related Tools
- [`amzscout_recommend_tool`](./amzscout_recommend_tool.md) — recommend an AMZScout tool for a use case
