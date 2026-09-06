# Awesome Magento AEO [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Modules, specifications and tools that make a Magento 2 or Adobe Commerce store discoverable, readable and transactable by AI systems.

If you have ever asked how to get a Magento store to show up in ChatGPT, how to sell through AI shopping agents, or what to do about AI crawlers hitting your catalog, this list is the index for it.

Answer Engine Optimization (AEO) — also called GEO, LLMO, AI SEO or AI search optimization — is the practice of configuring a site so AI assistants can read it, trust it and recommend it. Magento ships almost none of this out of the box: no `llms.txt`, no AI-bot policy in `robots.txt`, no agentic checkout, no MCP endpoint. This list tracks what the ecosystem has built to close that gap.

**52 projects tracked** — 15 discovery file implementations, 9 MCP servers, 8 agentic checkout projects, 7 specifications.

A capability matrix for every project — `llms.txt`, crawler policy, structured data, feeds, checkout, MCP, auditing — is in [COMPARISON.md](COMPARISON.md).

An entry belongs here if it is publicly available, works with Magento 2, Adobe Commerce or Mage-OS, has an identifiable AEO or agentic capability, and has a verifiable repository or product page. Full criteria and entry format are in [CONTRIBUTING.md](CONTRIBUTING.md).

Last reviewed: August 17, 2026. Each project keeps its own license; see the entry for details.

**This ecosystem is roughly a year old.** Discovery files are crowded and structured data is mature. Everything downstream of that — agentic checkout, MCP, the ACP and UCP protocols — is early: most projects are pre-1.0, several describe themselves as experimental, and the specifications themselves are still moving. A long list should not be read as a mature market. Read the status column before installing anything from the lower sections.

**Disclosure:** this list is maintained by [angeo.dev](https://angeo.dev), which publishes 12 of the entries below. To keep the ordering honest, **entries maintained by angeo.dev are listed last within their section**, after all third-party projects, rather than in alphabetical position. Corrections to any entry are welcome and never need justification.

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

## How to Choose

Start from the problem, not the protocol. Each route points at a section below, not at a product.

**You want your store to appear in ChatGPT, Claude, Perplexity or Google AI Overviews.** Start with Discovery Files — 11 implementations — then Structured Data. These two carry most of the result and are the settled part of the field.

**AI crawlers are hitting your catalog and you want to decide the terms.** Read Crawler Policy and Analytics, and read RFC 9309 first. Its group inheritance rule catches almost everyone.

**You want to sell through AI agents.** Start with Product Feeds, not Agentic Checkout. In March 2026 OpenAI scaled Instant Checkout back toward discovery, with the purchase completing on the merchant's own store, so a feed is what puts products in front of shoppers today. Agentic Checkout — 5 projects, none past 1.0 — matters for where the protocols are heading, not for revenue this quarter.

**You want an AI agent to query or operate the store.** Read MCP Servers. Storefront and admin servers are different security problems and should not be mixed up.

**You want to know where you stand before changing anything.** Read Auditing and Monitoring. Measure first — most stores fail on schema and robots long before anything agentic matters.

**You are researching the field rather than a store.** Read Specifications and Standards, then Related Lists.

## At a Glance

The comparison file linked above carries each project's self-declared maturity status alongside its capabilities.

Each project appears once in the sections below, in the place closest to its primary purpose. Several SEO suites cover more than one category; the comparison file is where that shows.

## Specifications and Standards

The protocols the modules below implement. Read these before evaluating anything.

- [Agentic Commerce Protocol](https://developers.openai.com/commerce) - OpenAI's specification for merchant product feeds, promotions and availability, plus a delegated payment flow. Its role in ChatGPT shifted toward discovery in March 2026. Abbreviated ACP.
- [llms.txt](https://llmstxt.org) - Proposed convention for a Markdown manifest addressed to language models rather than search crawlers.
- [Model Context Protocol](https://modelcontextprotocol.io) - Anthropic's open standard for exposing tools and data to AI agents. Abbreviated MCP.
- [Really Simple Licensing](https://rslstandard.org/rsl) - XML vocabulary for machine-readable content licensing, integrated with robots.txt, HTTP headers and HTML link elements. A rights layer rather than a transport or discovery one — it states terms for AI use, it does not carry data. Abbreviated RSL.
- [RFC 9309](https://www.rfc-editor.org/rfc/rfc9309.html) - The Robots Exclusion Protocol. A matched user-agent group does not inherit rules from the wildcard group, which is the most common cause of broken AI-bot policies.
- [Schema.org Product](https://schema.org/Product) - The vocabulary AI extractors read for price, availability and identifiers.
- [WebMCP](https://github.com/webmachinelearning/webmcp) - Proposed web platform API letting a page expose in-page tools to browser agents. Experimental — no shipped browser support, and the Lighthouse audits that check for it are themselves marked experimental.

## Discovery Files

Files served at a known path that tell agents what the store is, which pages matter and what it supports. The most crowded category here.

- [aligent/magento2-llms-txt](https://github.com/aligent/magento2-llms-txt) - Store-scoped generation with configurable entity selection and hourly cron evaluation. Unlabelled.
- [CodeDecorator LLMs TXT Generator](https://commercemarketplace.adobe.com/codedecorator-magento-2-llm-file-generator.html) - Generation in either key-value or Markdown form, with per-entity exclusion of individual CMS pages, categories and products. Commercial.
- [Grazitti LLMs TXT Generator](https://commercemarketplace.adobe.com/grazitti-magento2-llms-txt.html) - Generated fresh on every request from live store data, with optional SKUs and prices, bestseller and new-arrival blocks, brand listings, per-store-view scoping, CDN cache TTL and an `X-Robots-Tag` header to keep the file out of ordinary search results. Commercial.
- [mage-os/module-llm-txt](https://github.com/mage-os-lab/llms.txt) - Mage-OS Lab module that collects store data and generates the file through an OpenAI prompt. Unlabelled.
- [mage2kishan/module-blog](https://packagist.org/packages/mage2kishan/module-blog) - Blog extension whose posts feed `llms.txt` and `llms.json`, with IndexNow pinging and a Markdown export endpoint. Unlabelled.
- [mage2kishan/module-llms-txt](https://packagist.org/packages/mage2kishan/module-llms-txt) - Serves `llms.txt`, `llms-full.txt` and `llms.json` with weighted ranking, use-case grouping and cron cache warm-up. Unlabelled.
- [MageDelight LLMs TXT File Generator](https://www.magedelight.com/llms-txt-file-generator-magento-2.html) - Entity selection across products, categories and CMS pages with scheduled regeneration. Commercial.
- [Magefan LLMs TXT Generator](https://magefan.com/magento-2-llms-txt-generator) - Per store view generation with brand metadata blocks and configurable cron frequency. Commercial.
- [Meetanshi LLMs TXT Generator](https://meetanshi.com/magento-2-llms-txt-generator.html) - Per store view files with cron auto-update. Commercial.
- [Plumrocket LLMs TXT Generator](https://commercemarketplace.adobe.com/plumrocket-llms-txt-generator.html) - Store-view-scoped files with automatic regeneration on catalog and content changes, inclusion controls and Hyvä support. Commercial.
- [rkd/module-llms-txt](https://github.com/iamrobindhiman/magento2-module-llms-txt) - Cursor-based pagination and PHP generators for large catalogs, with CLI dry-run, validation and REST endpoints. MIT, unlabelled.
- [studioraz/magento2-llms-txt](https://github.com/studioraz/magento2-llms-txt) - Admin-generated Markdown with manual override and awareness of installed feed and point-of-sale modules. Unlabelled.
- [Webkul LLMs TXT Generator](https://commercemarketplace.adobe.com/webkul-module-llms-txt-generator.html) - Marketplace extension serving both files with correct content types, bundled with a crawler analytics dashboard. Commercial.
- [angeo/module-llms-txt](https://packagist.org/packages/angeo/module-llms-txt) - Generates `llms.txt`, `llms-full.txt`, `llms.jsonl` and on-the-fly Markdown page mirrors, Page Builder aware. MIT, released.
- [angeo/module-ucp](https://packagist.org/packages/angeo/module-ucp) - Publishes a `.well-known/ucp` profile at spec version 2026-04-08, served by a PHP controller so it carries the JSON content type and CORS headers the spec requires without web-server changes. REST and MCP service bindings, declared payment handlers, ECDSA P-256 public signing keys, and CI validation against the official UCP JSON Schemas. MIT, released.

## Crawler Policy and Analytics

Deciding which AI crawlers may enter, verifying they are who they claim, and measuring what they took. A thin category that is likely to grow.

- [Mageworx SEO Suite Ultimate](https://www.mageworx.com/magento-2-seo-extension.html) - Reports which AI crawlers visit and how often, with verification of genuine bots. Also advertises `llms.txt` automatically. Commercial.
- [Webkul AI Crawler Analytics](https://webkul.com/blog/magento-2-llms-txt-generator-documentation) - Documentation for the per-website dashboard of AI bot hits on the discovery files, with an option to discard unrecognised user agents. Commercial.
- [angeo/module-robots-txt-aeo](https://packagist.org/packages/angeo/module-robots-txt-aeo) - Lossless RFC 9309 parsing with a maintained bot catalogue, RSL and Content-Usage emission, and a bot IP verification command. MIT, released.

## Structured Data

Machine-readable product facts. The oldest AEO signal and still the one most stores get wrong. Each project appears once in this list; the SEO suites here also cover other columns, which the comparison file shows.

- [Amasty SEO Toolkit](https://amasty.com/seo-toolkit-for-magento-2.html) - Structured data with pagination and AJAX scroll handling, plus an AI-assisted metadata fix add-on and page-level analysis. Bundles `llms.txt` in its Pro and Premium tiers. Commercial.
- [mage-os/module-seo](https://github.com/mage-os-lab/module-seo) - SEO, AEO and GEO in one module built from extensible provider pools: 16 product schema templates, FAQ rich results, hreflang and robots meta, plus `llms.txt`, `llms.jsonl`, AI-crawler directives and `.well-known/` manifests for UCP, `ai-plugin.json` and `security.txt`. Unlabelled.
- [mageplaza/magento-2-seo](https://github.com/mageplaza/magento-2-seo) - Free community SEO module covering canonical tags and basic structured data, with the widest install base of any Magento SEO extension. Released.
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
- [Meetanshi Agentic Commerce](https://meetanshi.com/magento-2-agentic-commerce.html) - UCP profile, generic MCP server, WebMCP page tools and OpenAI ACP with checkout sessions mapped to real Magento quotes and delegated payment tokens through Stripe, plus an agent activity dashboard. Commercial.
- [Meetanshi Google UCP Checkout](https://meetanshi.com/magento-2-google-ucp.html) - Headless checkout through Google's UCP with Google Pay, order status webhooks back to Google and per-product eligibility control. Commercial.
- [xpaysh/agentic-commerce-for-magento](https://github.com/xpaysh/agentic-commerce-for-magento) - Node sidecar speaking ACP, UCP and AP2 against Magento's REST API, emitting `llms.txt`, `.well-known/ucp` and product JSON-LD, with signed-JWT cart deeplinks that hand the shopper back to the storefront checkout. Payment is left to the store's own PSP. Apache-2.0, v0.1.
- [angeo/module-mcp-checkout](https://packagist.org/packages/angeo/module-mcp-checkout) - Guest cart and checkout exposed as MCP tools with server-side guardrails and an order log. MIT, released.
- [angeo/module-ucp-catalog](https://packagist.org/packages/angeo/module-ucp-catalog) - Serves the `catalog.search` and `catalog.lookup` endpoints that the UCP profile advertises, with responses validated in CI against the official UCP JSON Schemas at the pinned spec tag. MIT, released.

This category is smaller than it looks. In March 2026 OpenAI pulled back from in-chat Instant Checkout — published figures put the live Shopify merchants at somewhere between a dozen and thirty — and moved toward product discovery with checkout completing on the merchant's own store. ACP itself remains an active open specification, and OpenAI's developer documentation still describes Instant Checkout for approved partners, so treat the direction as clearer than the details. Read the protocol before budgeting engineering time against it.

## MCP Servers

Exposing the store to AI agents as callable tools. Storefront servers face shoppers; admin servers face staff, and the security model differs sharply between the two.

- [adwise/magento2-mcp](https://github.com/adwise/magento2-mcp) - Lightweight MCP server exposing store information, module status, configuration, cache and indexer tools, with optional sub-modules for catalog management and Hyvä CMS page editing. Unlabelled.
- [magebitcom/magento2-mcp-module](https://github.com/magebitcom/magento2-mcp-module) - Admin server with per-tool role ACL, two-layer write gating, PII-redacted audit log and optional domain sub-modules, including a catalog tool extension. In progress.
- [magenable/magento2-mcp](https://github.com/magenable/magento2-mcp) - MCP server module for Magento 2. Unlabelled.
- [magendooro/magemcp](https://github.com/magendooro/magemcp) - Standalone Python service exposing catalog, orders, customers and inventory over REST and GraphQL, with PII redaction. Unlabelled.
- [Mirasvit Agentic Commerce](https://mirasvit.com/magento-2-agentic-commerce.html) - Storefront MCP server and WebMCP tools alongside a UCP profile, `llms.txt`, `agents.md` and an agent discovery sitemap. Discovery only; in-conversation checkout is on the roadmap. Commercial.
- [scandiweb/scandiweb-magento2-mcp](https://github.com/scandiweb/scandiweb-magento2-mcp) - A `POST /mcp` endpoint with OAuth and bearer sign-in, every tool call checked against Magento's own admin role tree, plus an optional content module with CMS, category, product, Hyvä CMS and Snowdog menu tools. OSL-3.0. Unlabelled.
- [thomastx05/magento-mcp](https://github.com/thomastx05/magento-mcp) - Node administration server with OAuth 1.0 credentials, two-phase commit for bulk operations and guardrails on price and volume. Unlabelled.
- [yuriyakishin/magento2-mcp-server](https://github.com/yuriyakishin/magento2-mcp-server) - Free server covering catalog, orders, customers, CMS and sales, secured with OAuth 2.1 and Magento ACL. Unlabelled.
- [angeo/module-mcp-server](https://packagist.org/packages/angeo/module-mcp-server) - Read-only storefront catalog access with rate limiting and an extensible tool registry. MIT, released.

## Auditing and Monitoring

Measuring whether any of the above works. Crawl access, citation share and rendering quality are three separate questions, and most auditing still happens inside general SEO suites rather than AEO-specific tools. Amasty, Mageworx and Webkul all include audit or analytics features and are listed in the sections above.

- [Mirasvit](https://mirasvit.com/magento-2-mcp-ai-integration.html) - Store-wide crawler for issues that block extraction, alongside an MCP server with OAuth 2.1 and role-based permissions and an ACP integration. Commercial.
- [angeo/module-aeo-audit](https://packagist.org/packages/angeo/module-aeo-audit) - Weighted signal audit across robots, discovery files, schema, sitemap and feed, with CrUX data and a CI failure threshold. MIT, released.
- [angeo/module-aeo-brand-visibility](https://packagist.org/packages/angeo/module-aeo-brand-visibility) - Tracks brand recall and citation rate across major assistants, with competitor share-of-voice. MIT, released.

Four options need no Magento module, none of them Magento-specific. Google's [PageSpeed Insights](https://pagespeed.web.dev) added an Agentic Browsing category in Lighthouse 13.3 that grades how ready a page is for AI agents, checking for `llms.txt` at the domain root and registered WebMCP tools; the category is marked experimental. The [Agent Skills for AEO](https://github.com/angeo-dev/skills) marketplace installs into Claude Code and audits any site for crawler access, `llms.txt` and structured data. The [angeo.dev AEO scan](https://angeo.dev/ai-magento-audit) reads discovery and agentic signals for any storefront URL, and Bing Webmaster Tools reports citation counts, cited pages and grounding queries under its AI Performance view — still the only free first-party count of how often an AI system cited a site. Google Search Console added generative AI reporting in June 2026, but it exposes impressions rather than citations.

## Reading

Independent write-ups worth reading before choosing anything above.

- [Agentic Commerce for Magento](https://kishansavaliya.com/blog/magento-agentic-commerce-sell-through-ai-agents) - What selling through AI agents actually requires, including the merchant approval prerequisites.
- [anthropics/commerce-agents](https://github.com/anthropics/commerce-agents) - Anthropic's reference blueprint for shopping and merchant agents built on Claude. Read it for the other side of the interface: what an agent does with the discovery and checkout surfaces the modules in this list publish. [Shopify's implementation](https://github.com/Shopify/claude-for-commerce-examples) drives its shopping agent off any domain serving `.well-known/ucp`. Not Magento-specific.
- [Best Magento 2 SEO Extensions 2026](https://www.magedelight.com/blog/best-magento-2-seo-extensions-comparison) - Vendor comparison covering where AI features sit inside the established SEO suites. Published by a vendor in the comparison.
- [Best Magento SEO Extensions 2026](https://kishansavaliya.com/best-magento-seo-extensions) - Opinionated picks covering llms.txt, hreflang and sitemap modules.
- [What is llms.txt for Magento 2](https://kishansavaliya.com/what-is-magento-llms-txt) - Setup walkthrough covering exclusions, canonical handling and staleness.
- [What Is the Best Magento SEO Extension in 2026](https://121ecommerce.com/best-magento-seo-extension) - Agency-side comparison of the major SEO suites and their AI additions.
- [llms.txt for Magento 2: free versus paid](https://angeo.dev/llms-txt-magento-2-free-vs-paid-module-comparison) - Feature comparison of Magento llms.txt solutions, with stated methodology and disclosure.

## Related Lists

This list stays narrow on purpose. Platform-agnostic AEO research, benchmarks, validators and the growing field of AI-visibility monitoring tools are covered better by the lists below than they would be here.

- [aleron75/mageres](https://github.com/aleron75/mageres) - Alessandro Ronchi's list of Magento 1 and Magento 2 resources, with an accompanying monthly digest.
- [amplifying-ai/awesome-generative-engine-optimization](https://github.com/amplifying-ai/awesome-generative-engine-optimization) - GEO guides, research and industry benchmark reports. Vendor-maintained.
- [izak-fisher/generative-engine-optimization-tools](https://github.com/izak-fisher/generative-engine-optimization-tools) - The most complete directory of AI-visibility monitoring and prompt-testing tools.
- [luka2chat/awesome-geo](https://github.com/luka2chat/awesome-geo) - GEO resources, newsletters, communities and llms.txt directories.
- [MagePsycho/awesome-magento-ai](https://github.com/MagePsycho/awesome-magento-ai) - AI tooling for building and operating Magento: agent skills, dev-side MCP servers, admin and catalog AI modules. The complement to this list, covering AI working inside the store rather than the store as AI reads it.
- [run-as-root/awesome-magento2](https://github.com/run-as-root/awesome-magento2) - The main Magento 2 list, tracking over 230 projects with weekly automated maintenance and graveyard signals.
- [sunel/awesome-magento](https://github.com/sunel/awesome-magento) - Mixed Magento 1 and Magento 2 resources. Not recently updated.
- [xpaysh/awesome-agentic-commerce](https://github.com/xpaysh/awesome-agentic-commerce) - ACP, UCP, AP2 and the payment rails beneath them, with a compatibility matrix, version pinning and a list of well-known paths not to emit.
- [yan253319066/awesome-geo-resources](https://github.com/yan253319066/awesome-geo-resources) - GEO, AI visibility and citation resources. Vendor-maintained.

## Contributing

Read the contribution guidelines linked at the top before opening a pull request. Corrections to your own project's entry are always welcome and never need justification.
