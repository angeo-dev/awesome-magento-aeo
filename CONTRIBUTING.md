# Contributing

Thanks for helping keep this list accurate.

## Scope

Magento 2 and Adobe Commerce, crossed with AI discovery and agentic commerce. Something belongs here if it helps a store be **found**, **read**, **trusted** or **transacted with** by an AI system.

Out of scope: general Magento extensions, general SEO tooling with no AI surface, AI features aimed only at internal store operations, MCP servers unrelated to Magento, and other ecommerce platforms.

## Inclusion criteria

An entry needs all of:

1. **Public and reachable.** A working repository, marketplace listing or product page.
2. **Real, not announced.** Installable or usable today. Work in progress is welcome but must be labelled.
3. **Specific.** It does something concrete for AI discovery or agentic commerce, not a page claiming to be AI-powered.
4. **Honest about maintenance.** Archived projects may stay if they remain the reference implementation of something, labelled as such.

Commercial products are welcome and sit in the same functional sections as free ones, marked `Commercial.` They are not segregated, because a merchant choosing an llms.txt module needs to see all the options in one place.

## Entry format

```
- [name](url) - Description, capitalised, ending in a period. Status or license last.
```

- One line. If it needs two, it needs a shorter description.
- Composer `vendor/package` for modules, product name for commercial extensions.
- No superlatives, no marketing verbs, no emoji.
- Alphabetical within each section, case-insensitive, with one exception: entries maintained by the list maintainer are placed last in their section, regardless of name. This is deliberate. Alphabetical order would otherwise put `angeo/` first almost everywhere, which is not a fact about the projects.
- Status labels: `MIT.` `Commercial.` `In progress.` `Experimental.` `Archived.`
- No trailing slashes in URLs. The linter rejects them.
- Describe what it does, not what it lets you imagine.

## How to submit

Open a pull request, or an issue if you would rather not. Include the link, the proposed section, a one-line description in the format above, and one sentence on why it meets the criteria.

If you are affiliated with the project, say so. It does not count against you; undisclosed affiliation does.

## Corrections

If a description is wrong, outdated or unfair to your project, open an issue and it will be fixed. This applies especially to entries owned by the list maintainer. Being on the list is not a claim of quality, and being described accurately is not a favour.

## Removals

Entries are removed when a link dies, a project is delisted, or a description can no longer be made accurate. Removal is not a judgement about the project.

## Review cadence

The list carries a `Last reviewed` date. Links are checked weekly by CI; descriptions and status labels are re-read by a human at least quarterly. If the date is stale, open an issue.
