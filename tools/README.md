# AMZScout MCP Tools

This folder documents every tool exposed by the AMZScout MCP server.

| Tool | What it does |
|------|--------------|
| [`amzscout_analyze_product`](./amzscout_analyze_product.md) | Full raw data for a single product by ASIN |
| [`amzscout_compare_products`](./amzscout_compare_products.md) | Side-by-side raw data for 2–5 products |
| [`amzscout_analyze_product_set`](./amzscout_analyze_product_set.md) | Raw data + aggregates across 2–100 ASINs |
| [`amzscout_analyze_niche`](./amzscout_analyze_niche.md) | Market snapshot for a niche/keyword |
| [`amzscout_compare_niches`](./amzscout_compare_niches.md) | Head-to-head comparison of 2–5 niches |
| [`amzscout_search_products`](./amzscout_search_products.md) | Keyword search returning raw product rows |
| [`amzscout_find_by_brand`](./amzscout_find_by_brand.md) | List products under a specific brand |
| [`amzscout_get_keywords`](./amzscout_get_keywords.md) | Keyword / SEO / PPC data (ASIN or niche scope) |
| [`amzscout_locate_asin`](./amzscout_locate_asin.md) | Marketplace availability + local prices for an ASIN |
| [`amzscout_reseller_amazon`](./amzscout_reseller_amazon.md) | Buy box, offer counts, and sales-rank data for an ASIN |
| [`amzscout_recommend_tool`](./amzscout_recommend_tool.md) | Recommend the right AMZScout tool for a use case |
| [`amzscout_search_knowledge`](./amzscout_search_knowledge.md) | Search the AMZScout knowledge base |
| [`amzscout_usage`](./amzscout_usage.md) | Check remaining AI-agent token balance |

## Choosing between tools

- Want raw data to reason over yourself, with full control? Use the granular `amzscout_*` tools above.
- Working with a single product vs. a set vs. a niche: `analyze_product` → `analyze_product_set` → `analyze_niche` (or their `compare_*` counterparts) scale up in scope.
