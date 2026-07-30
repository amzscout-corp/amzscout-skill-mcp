# amzscout-agent

## Description
AMZScout's all-in-one Amazon research assistant. Ask anything in natural language (e.g. *"Is B07GQF9D1Z worth selling?"*, *"Analyze the yoga mat niche"*, *"Find products for brand Anker"*) and it returns a finished analysis — it pulls live Amazon data and runs the right analyses internally, so no sub-tool selection is needed.

Best for a hands-off, single-call answer. The granular `amzscout_*` tools (analyze_product, analyze_niche, etc.) are the alternative when step-by-step orchestration or raw data access is preferred.

## Parameters

| Name | Type | Required | Description |
|------|------|----------|--------------|
| `message` | string | Yes | The question or request in natural language |
| `history` | array | No | Optional prior turns for multi-turn context, oldest first. Each item: `{ "role": "user" \| "assistant", "content": string }` |

## Example Call
```json
{
  "message": "Is B07GQF9D1Z worth selling as a new seller?"
}
```

## Example Call (multi-turn)
```json
{
  "message": "What about compared to B08XYZ1234?",
  "history": [
    { "role": "user", "content": "Is B07GQF9D1Z worth selling?" },
    { "role": "assistant", "content": "Yes, moderate opportunity — see analysis..." }
  ]
}
```

## Returned Data
A complete, user-ready report combining relevant Amazon data and AI-generated analysis/verdict, tailored to the question asked.

## Related Tools
All granular `amzscout_*` tools (analyze_product, analyze_niche, compare_products, compare_niches, search_products, find_by_brand, get_keywords) can be used individually for more control over the underlying data.
