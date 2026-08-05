# Awesome Magento AEO [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Modules, specifications and tools that make a Magento 2 or Adobe Commerce store discoverable, readable and transactable by AI systems.

If you have ever asked how to get a Magento store to show up in ChatGPT, how to sell through AI shopping agents, or what to do about AI crawlers hitting your catalog, this list is the index for it.

Answer Engine Optimization (AEO) — also called GEO, LLMO, AI SEO or AI search optimization — is the practice of configuring a site so AI assistants can read it, trust it and recommend it. Magento ships almost none of this out of the box: no `llms.txt`, no AI-bot policy in `robots.txt`, no agentic checkout, no MCP endpoint. This list tracks what the ecosystem has built to close that gap.

**47 projects tracked** — 13 llms.txt implementations, 6 MCP servers, 5 agentic checkout projects, 7 specifications.

Last reviewed: 2026-08.

**This market is roughly a year old.** Discovery files and structured data are settled work with many mature implementations. Everything downstream of that — agentic checkout, MCP, the ACP and UCP protocols — is early: most projects are pre-1.0, several describe themselves as experimental, and the specifications themselves are still moving. A long list should not be read as a mature market. Read the status column before installing anything from the lower sections.

**Disclosure:** this list is maintained by [angeo.dev](https://angeo.dev), which publishes 11 of the entries below. To keep the ordering honest, **entries maintained by angeo.dev are listed last within their section**, after all third-party projects, rather than in alphabetical position. Corrections to any entry are welcome and never need justification. See [Contributing](CONTRIBUTING.md).

## Contents

- [How to Choose](#how-to-choose)
- [At a Glance](#at-a-glance)
- [Specifications and Standards](#specifications-and-standards)
- [Discovery Files](#discovery-files)
- [Crawler Policy and Analytics](#crawler-policy-and-analytics)
- [Structured Data](#structured-data)
- [Product Feeds](#product-feeds)
- [Agentic Checkout](#agentic-checkout)
- [MCP Servers](#mcp-servers)
- [Auditing and Monitoring](#auditing-and-monitoring)
- [Reading](#reading)
- [Related Lists](#related-lists)

## How to Choose

Start from the problem, not the protocol. Each route points at a section, not a product.

- **You want your store to appear in ChatGPT, Claude, Perplexity or Google AI Overviews.** Start with [Discovery Files](#discovery-files) — 13 implementations — then [Structured Data](#structured-data). These two carry most of the result and are the settled part of the field.
- **AI crawlers are hitting your catalog and you want to decide the terms.** Go to [Crawler Policy and Analytics](#crawler-policy-and-analytics). Read RFC 9309 first; the inheritance rule catches almost everyone.
- **You want to sell inside ChatGPT.** Go to [Product Feeds](#product-feeds), then [Agentic Checkout](#agentic-checkout) — 5 projects, none past 1.0. Confirm you can get OpenAI merchant approval in your region before writing any code.
- **You want an AI agent to query or operate the store.** Go to [MCP Servers](#mcp-servers) — 6 servers. Storefront and admin servers are different security problems; do not mix them up.
- **You want to know where you stand before changing anything.** Go to [Auditing and Monitoring](#auditing-and-monitoring). Measure first — most stores fail on schema and robots long before anything agentic matters.
- **You are researching the field rather than a store.** Go to [Specifications and Standards](#specifications-and-standards) — 7 specs — and [Related Lists](#related-lists).

## At a Glance

Coverage by project. `Y` means the project implements the capability; `~` means partial or bundled inside a broader feature.

**Status** reflects only what each project declares about itself. `Released` means tagged, versioned releases. `In progress` and `Experimental` are the maintainers' own words. `Unlabelled` means the project makes no maturity claim — it is not a criticism, and checking recent commit activity is a better signal than anything in this table.

### Open source

| Project | llms.txt | Crawler policy | Schema | Feed | Checkout | MCP | Audit | License | Status |
|---|---|---|---|---|---|---|---|---|---|
| aligent/magento2-llms-txt | Y | | | | | | | OSS | Unlabelled |
| mage-os/module-llm-txt | Y | | | | | | | OSS | Unlabelled |
| mage2kishan/module-llms-txt | Y | | | | | | | OSS | Unlabelled |
| magebitcom (3 modules) | | | | ~ | Y | Y | | OSS | In progress |
| magendooro/magemcp | | | | | | Y | | OSS | Unlabelled |
| magenable (2 modules) | | | | Y | | Y | | OSS | Unlabelled |
| mageplaza/magento-2-seo | | | Y | | | | ~ | OSS | Released |
| MaxMage/module-agentic-commerce | | | | | Y | | | OSS | Experimental |
| rkd/module-llms-txt | Y | | | | | | | MIT | Unlabelled |
| studioraz/magento2-llms-txt | Y | | | | | | | OSS | Unlabelled |
| thomastx05/magento-mcp | | | | | | Y | | OSS | Unlabelled |
| angeo (11 modules) | Y | Y | Y | Y | Y | Y | Y | MIT | Released |

### Commercial

| Project | llms.txt | Crawler policy | Schema | Feed | Checkout | MCP | Audit | Notes |
|---|---|---|---|---|---|---|---|---|
| Amasty SEO Toolkit | Y | | Y | | | | Y | llms.txt is Pro and Premium tiers only |
| Magefan LLMs TXT Generator | Y | | | | | | | Single purpose |
| MageDelight | Y | | Y | | | | | |
| Mageworx SEO Suite Ultimate | Y | Y | Y | | | | | Bot analytics with verification |
| Meetanshi LLMs TXT Generator | Y | | | | | | | Single purpose |
| Mirasvit | | | Y | Y | Y | Y | Y | Widest commercial coverage |
| Webkul LLMs TXT Generator | Y | Y | | | | | | Crawler analytics dashboard |

Two rows cover many columns — angeo and Mirasvit. Both are suites of separate modules rather than single products, so breadth here is a packaging fact, not a quality judgement. A single-purpose module that does one column well is often the better choice.

## Specifications and Standards

The protocols the modules below implement. Read these before evaluating anything.

- [Agentic Commerce Protocol](https://developers.openai.com/commerce) - OpenAI's specification for merchant product feeds and in-chat checkout, including the Shared Payment Token flow. Abbreviated ACP.
- [llms.txt](https://llmstxt.org) - Proposed convention for a Markdown manifest addressed to language models rather than search crawlers.
- [Model Context Protocol](https://modelcontextprotocol.io) - Anthropic's open standard for exposing tools and data to AI agents. Abbreviated MCP.
- [Really Simple Licensing](https://rslstandard.org/rsl) - XML vocabulary for machine-readable content licensing, integrated with robots.txt, HTTP headers and HTML link elements. Abbreviated RSL.
- [RFC 9309](https://www.rfc-editor.org/rfc/rfc9309.html) - The Robots Exclusion Protocol. A matched user-agent group does not inherit rules from the wildcard group, which is the most common cause of broken AI-bot policies.
- [Schema.org Product](https://schema.org/Product) - The vocabulary AI extractors read for price, availability and identifiers.
- [WebMCP](https://github.com/webmachinelearning/webmcp) - Draft web platform API letting a page expose in-page tools to browser agents.

## Discovery Files

Files that tell AI crawlers what the store is and which pages matter. The most crowded and most mature category here.

- [aligent/magento2-llms-txt](https://github.com/aligent/magento2-llms-txt) - Store-scoped generation with configurable entity selection and hourly cron evaluation. Unlabelled.
- [amasty/module-llms-txt](https://amasty.com/seo-toolkit-for-magento-2.html) - Part of SEO Toolkit Pro and Premium, installed through Composer suggest rather than standalone. Commercial.
- [Magefan LLMs TXT Generator](https://magefan.com/magento-2-llms-txt-generator) - Per store view generation with brand metadata blocks and configurable cron frequency. Commercial.
- [mage-os/module-llm-txt](https://github.com/mage-os-lab/llms.txt) - Mage-OS Lab module that collects store data and generates the file through an OpenAI prompt. Unlabelled.
- [mage2kishan/module-blog](https://packagist.org/packages/mage2kishan/module-blog) - Blog extension whose posts feed `llms.txt` and `llms.json`, with IndexNow pinging and a Markdown export endpoint. Unlabelled.
- [mage2kishan/module-llms-txt](https://packagist.org/packages/mage2kishan/module-llms-txt) - Serves `llms.txt`, `llms-full.txt` and `llms.json` with weighted ranking, use-case grouping and cron cache warm-up. Unlabelled.
- [MageDelight LLMs TXT File Generator](https://www.magedelight.com/llms-txt-file-generator-magento-2.html) - Entity selection across products, categories and CMS pages with scheduled regeneration. Commercial.
- [Mageworx SEO Suite Ultimate](https://www.mageworx.com/magento-2-seo-extension.html) - SEO suite that advertises the discovery manifest automatically and keeps it current. Commercial.
- [Meetanshi LLMs TXT Generator](https://meetanshi.com/magento-2-llms-txt-generator.html) - Per store view files with cron auto-update. Commercial.
- [rkd/module-llms-txt](https://github.com/iamrobindhiman/magento2-module-llms-txt) - Cursor-based pagination and PHP generators for large catalogs, with CLI dry-run, validation and REST endpoints. MIT, unlabelled.
- [studioraz/magento2-llms-txt](https://github.com/studioraz/magento2-llms-txt) - Admin-generated Markdown with manual override and awareness of installed feed and point-of-sale modules. Unlabelled.
- [Webkul LLMs TXT Generator](https://commercemarketplace.adobe.com/webkul-module-llms-txt-generator.html) - Marketplace extension serving both files with correct content types, bundled with a crawler analytics dashboard. Commercial.
- [angeo/module-llms-txt](https://github.com/angeo-dev/module-llms-txt) - Generates `llms.txt`, `llms-full.txt`, `llms.jsonl` and on-the-fly Markdown page mirrors, Page Builder aware. MIT, released.

## Crawler Policy and Analytics

Deciding which AI crawlers may enter, verifying they are who they claim, and measuring what they took. A thin category that is likely to grow.

- [Mageworx SEO Suite Ultimate](https://www.mageworx.com/magento-2-seo-extension.html) - Reports which AI crawlers visit and how often, with verification of genuine bots. Commercial.
- [Webkul AI Crawler Analytics](https://webkul.com/blog/magento-2-llms-txt-generator-documentation) - Per-website dashboard of AI bot hits on the discovery files, with an option to discard unrecognised user agents. Commercial.
- [angeo/module-robots-txt-aeo](https://packagist.org/packages/angeo/module-robots-txt-aeo) - Lossless RFC 9309 parsing with a maintained bot catalogue, RSL and Content-Usage emission, and a bot IP verification command. MIT, released.

## Structured Data

Machine-readable product facts. The oldest AEO signal and still the one most stores get wrong.

- [Amasty SEO Toolkit](https://amasty.com/seo-toolkit-for-magento-2.html) - Structured data alongside pagination and AJAX scroll handling, with an AI-assisted metadata fix add-on. Commercial.
- [mageplaza/magento-2-seo](https://github.com/mageplaza) - Free community SEO module covering canonical tags and basic structured data, with the widest install base of any Magento SEO extension. Released.
- [MageDelight SEO](https://www.magedelight.com/blog/best-magento-2-seo-extensions-comparison) - Mid-market SEO suite covering the structured data baseline. Commercial.
- [Mirasvit SEO](https://mirasvit.com/magento-2-mcp-ai-integration.html) - SEO suite covering the structured data baseline, with a full store crawler. Commercial.
- [angeo/module-rich-data](https://packagist.org/packages/angeo/module-rich-data) - Product JSON-LD with offer availability, GTIN and MPN, shipping details, return policy and breadcrumbs. MIT, released.

## Product Feeds

Catalog export in the shapes AI shopping surfaces ingest. Very few projects target this so far, so the sample is small rather than selective. The ACP modules in the next section also generate feeds as part of their integration.

- [magenable/module-openai-agentic-commerce-feed](https://github.com/magenable/module-openai-agentic-commerce-feed) - Cron-driven feed file generation with selectable output format. Unlabelled.
- [angeo/module-openai-product-feed](https://packagist.org/packages/angeo/module-openai-product-feed) - ACP-compliant feed generation across all product types. MIT, released.
- [angeo/module-openai-product-feed-api](https://packagist.org/packages/angeo/module-openai-product-feed-api) - REST surface for the feed with database-persisted output, paginated export and cart rule to promotion mapping. MIT, released.

## Agentic Checkout

Letting an agent complete a purchase rather than only find a product. **The least mature category in this list** — no entry here has a stable 1.0, and the protocols themselves are still changing.

- [magebitcom/magento2-agentic-commerce-module](https://github.com/magebitcom/magento2-agentic-commerce-module) - ACP integration for selling inside ChatGPT, targeting Hyvä, B2B and Adobe Commerce Cloud. In progress.
- [magebitcom/magento2-universal-commerce-module](https://github.com/magebitcom/magento2-universal-commerce-module) - Universal Commerce Protocol implementation. In progress.
- [MaxMage/module-agentic-commerce](https://github.com/MaxMage/module-agentic-commerce) - Agentic checkout flow with HMAC signature verification, idempotency and spec-shaped routes. Experimental.
- [angeo/module-mcp-checkout](https://packagist.org/packages/angeo/module-mcp-checkout) - Guest cart and checkout exposed as MCP tools with server-side guardrails and an order log. MIT, released.
- [angeo/module-ucp](https://packagist.org/packages/angeo/module-ucp) - Publishes a `.well-known/ucp` profile advertising service bindings to UCP-compliant agents. MIT, released.

No module can make a store sellable inside ChatGPT on its own. That also needs merchant approval from OpenAI, currently limited by region, and a payment provider supporting the Shared Payment Token.

## MCP Servers

Exposing the store to AI agents as callable tools. Storefront servers face shoppers; admin servers face staff, and the security model differs sharply between the two.

- [magebitcom/magento2-mcp-module](https://github.com/magebitcom/magento2-mcp-module) - Admin server with per-tool role ACL, two-layer write gating, PII-redacted audit log and optional domain sub-modules. In progress.
- [magendooro/magemcp](https://github.com/magendooro/magemcp) - Standalone Python service exposing catalog, orders, customers and inventory over REST and GraphQL, with PII redaction. Unlabelled.
- [magenable/magento2-mcp](https://github.com/magenable/magento2-mcp) - MCP server module for Magento 2. Unlabelled.
- [Mirasvit AI Agent Connector](https://mirasvit.com/magento-2-mcp-ai-integration.html) - MCP server with OAuth 2.1 and role-based permissions. Commercial.
- [thomastx05/magento-mcp](https://github.com/thomastx05/magento-mcp) - Node administration server with OAuth 1.0 credentials, two-phase commit for bulk operations and guardrails on price and volume. Unlabelled.
- [angeo/module-mcp-server](https://packagist.org/packages/angeo/module-mcp-server) - Read-only storefront catalog access with rate limiting and an extensible tool registry. MIT, released.

## Auditing and Monitoring

Measuring whether any of the above works. Crawl access, citation share and rendering quality are three separate questions, and most auditing still happens inside general SEO suites rather than AEO-specific tools.

- [Amasty SEO Toolkit](https://amasty.com/seo-toolkit-for-magento-2.html) - Page-level one-click analysis with an AI-assisted metadata fix add-on, no full-site crawler. Commercial.
- [mageplaza/magento-2-seo](https://github.com/mageplaza) - Higher tiers add an SEO checklist that tracks pending optimisations as a manual audit guide. Released.
- [Mirasvit SEO](https://mirasvit.com/magento-2-mcp-ai-integration.html) - Store-wide crawler, the most thorough auditing among the commercial suites. Commercial.
- [angeo/module-aeo-audit](https://packagist.org/packages/angeo/module-aeo-audit) - Weighted signal audit across robots, discovery files, schema, sitemap and feed, with CrUX data and a CI failure threshold. MIT, released.
- [angeo/module-aeo-brand-visibility](https://packagist.org/packages/angeo/module-aeo-brand-visibility) - Tracks brand recall and citation rate across major assistants, with competitor share-of-voice. MIT, released.

Two hosted options need no installation: the [angeo.dev AEO scan](https://angeo.dev/ai-magento-audit) reads discovery and agentic signals for any storefront URL, and Bing Webmaster Tools reports AI citation counts and cited pages under its AI Performance view — currently the only free first-party count of how often an AI system quoted a site.

## Reading

Independent write-ups worth reading before choosing anything above.

- [Agentic Commerce for Magento](https://kishansavaliya.com/blog/magento-agentic-commerce-sell-through-ai-agents) - What selling through AI agents actually requires, including the merchant approval prerequisites.
- [Best Magento 2 SEO Extensions 2026](https://www.magedelight.com/blog/best-magento-2-seo-extensions-comparison) - Vendor comparison covering where AI features sit inside the established SEO suites. Published by a vendor in the comparison.
- [Best Magento SEO Extensions 2026](https://kishansavaliya.com/best-magento-seo-extensions) - Opinionated picks covering llms.txt, hreflang and sitemap modules.
- [What Is the Best Magento SEO Extension in 2026](https://121ecommerce.com/best-magento-seo-extension) - Agency-side comparison of the major SEO suites and their AI additions.
- [What is llms.txt for Magento 2](https://kishansavaliya.com/what-is-magento-llms-txt) - Setup walkthrough covering exclusions, canonical handling and staleness.
- [llms.txt for Magento 2: free versus paid](https://angeo.dev/llms-txt-magento-2-free-vs-paid-module-comparison) - Feature comparison of Magento llms.txt solutions, with stated methodology and disclosure.

## Related Lists

This list stays narrow on purpose. Platform-agnostic AEO research, benchmarks, validators and the growing field of AI-visibility monitoring tools are covered better by the lists below than they would be here.

- [aleron75/mageres](https://github.com/aleron75/mageres) - Alessandro Ronchi's list of Magento 1 and Magento 2 resources, with an accompanying monthly digest.
- [amplifying-ai/awesome-generative-engine-optimization](https://github.com/amplifying-ai/awesome-generative-engine-optimization) - GEO guides, research and industry benchmark reports. Vendor-maintained.
- [izak-fisher/generative-engine-optimization-tools](https://github.com/izak-fisher/generative-engine-optimization-tools) - The most complete directory of AI-visibility monitoring and prompt-testing tools.
- [luka2chat/awesome-geo](https://github.com/luka2chat/awesome-geo) - GEO resources, newsletters, communities and llms.txt directories.
- [run-as-root/awesome-magento2](https://github.com/run-as-root/awesome-magento2) - The main Magento 2 list, tracking over 230 projects with weekly automated maintenance and graveyard signals.
- [sunel/awesome-magento](https://github.com/sunel/awesome-magento) - Mixed Magento 1 and Magento 2 resources. Not recently updated.
- [yan253319066/awesome-geo-resources](https://github.com/yan253319066/awesome-geo-resources) - GEO, AI visibility and citation resources. Vendor-maintained.

## Contributing

Read the [guidelines](CONTRIBUTING.md) before opening a pull request. Corrections to your own project's entry are always welcome and never need justification.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](LICENSE)

The list itself is CC0 — the curation, ordering and descriptions are placed in the public domain, including any database rights. The projects it links to keep their own licenses.
