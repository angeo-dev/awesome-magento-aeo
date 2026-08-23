# Comparison

Coverage by project, as of version 1.1.0 (2026-08). `✓` means the project implements the capability, `◐` means partial or bundled inside a broader feature, and `—` means not covered. A dash is not a criticism: a single-purpose module that does one thing well is often the better choice.

**Status** reflects only what each project declares about itself. `Released` means tagged, versioned releases. `In progress` and `Experimental` are the maintainers' own words. `Unlabelled` means the project makes no maturity claim — it is not a criticism, and recent commit activity is a better signal than anything in this table.

Two rows cover many columns: angeo and Mirasvit. Both are suites of separate modules rather than single products, so breadth here is a packaging fact, not a quality judgement. A single-purpose module that does one column well is often the better choice.

Each project appears once in the [main list](README.md), in the section closest to its primary purpose. This table is where the cross-section coverage lives.

## Open source

| Project                         | llms.txt | Crawler policy | Schema | Feed | Checkout | MCP | Audit | License | Status       |
|---------------------------------|----------|----------------|--------|------|----------|-----|-------|---------|--------------|
| adwise/magento2-mcp             | —        | —              | —      | —    | —        | ✓   | —     | OSS     | Unlabelled   |
| aligent/magento2-llms-txt       | ✓        | —              | —      | —    | —        | —   | —     | OSS     | Unlabelled   |
| mage-os/module-llm-txt          | ✓        | —              | —      | —    | —        | —   | —     | OSS     | Unlabelled   |
| mage-os/module-seo              | ✓        | ✓              | ✓      | ◐    | ◐        | —   | —     | OSS     | Unlabelled   |
| mage2kishan/module-llms-txt     | ✓        | —              | —      | —    | —        | —   | —     | OSS     | Unlabelled   |
| magebitcom (3 modules)          | —        | —              | —      | ◐    | ✓        | ✓   | —     | OSS     | In progress  |
| magendooro/magemcp              | —        | —              | —      | —    | —        | ✓   | —     | OSS     | Unlabelled   |
| magenable (2 modules)           | —        | —              | —      | ✓    | —        | ✓   | —     | OSS     | Unlabelled   |
| mageplaza/magento-2-seo         | —        | —              | ✓      | —    | —        | —   | ◐     | OSS     | Released     |
| MaxMage/module-agentic-commerce | —        | —              | —      | —    | ✓        | —   | —     | OSS     | Experimental |
| rkd/module-llms-txt             | ✓        | —              | —      | —    | —        | —   | —     | MIT     | Unlabelled   |
| studioraz/magento2-llms-txt     | ✓        | —              | —      | —    | —        | —   | —     | OSS     | Unlabelled   |
| scandiweb/scandiweb-magento2-mcp| —        | —              | —      | —    | —        | ✓   | —     | OSS     | Unlabelled   |
| thomastx05/magento-mcp          | —        | —              | —      | —    | —        | ✓   | —     | OSS     | Unlabelled   |
| yuriyakishin/magento2-mcp-server| —        | —              | —      | —    | —        | ✓   | —     | OSS     | Unlabelled   |
| angeo (11 modules)              | ✓        | ✓              | ✓      | ✓    | ✓        | ✓   | ✓     | MIT     | Released     |

## Commercial

| Project                      | llms.txt | Crawler policy | Schema | Feed | Checkout | MCP | Audit | Notes                                  |
|------------------------------|----------|----------------|--------|------|----------|-----|-------|----------------------------------------|
| Amasty SEO Toolkit           | ✓        | —              | ✓      | —    | —        | —   | ✓     | llms.txt is Pro and Premium tiers only |
| CodeDecorator LLMs TXT       | ✓        | —              | —      | —    | —        | —   | —     | Per-entity exclusion controls          |
| MageDelight                  | ✓        | —              | ✓      | —    | —        | —   | —     | —                                      |
| Magefan LLMs TXT Generator   | ✓        | —              | —      | —    | —        | —   | —     | Single purpose                         |
| Mageworx SEO Suite Ultimate  | ✓        | ✓              | ✓      | —    | —        | —   | —     | Bot analytics with verification        |
| Meetanshi Agentic Commerce   | ✓        | ✓              | —      | ✓    | ✓        | ✓   | ✓     | Widest single-module coverage here     |
| Meetanshi Google UCP         | —        | —              | —      | ✓    | ✓        | —   | —     | Google Pay, staged regional rollout    |
| Meetanshi LLMs TXT Generator | ✓        | —              | —      | —    | —        | —   | —     | Single purpose                         |
| Mirasvit AI Agent Connector  | —        | —              | ✓      | ✓    | ✓        | ✓   | ✓     | Widest commercial coverage             |
| Mirasvit Agentic Commerce    | ✓        | ✓              | —      | ✓    | —        | ✓   | —     | Discovery only; checkout on roadmap    |
| Plumrocket LLMs TXT          | ✓        | —              | —      | —    | —        | —   | —     | Store-view scoped, Hyvä support        |
| Webkul LLMs TXT Generator    | ✓        | ✓              | —      | —    | —        | —   | —     | Crawler analytics dashboard            |
