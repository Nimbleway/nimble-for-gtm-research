# Nimble for GTM Research

Agent skills that give your AI agent (Claude, ChatGPT, Cursor, Codex and others) the live web as cited, structured data for go-to-market work: account research, buying signals, prospect lists and CRM enrichment, powered by [Nimble](https://www.nimbleway.com).

| Skill | What it does |
| - | - |
| [`onboard-your-gtm-agent`](skills/onboard-your-gtm-agent/SKILL.md) | Start here. Shows the GTM benchmark chart (deep research task comparison for GTM) and the five use cases as tiles for testing Nimble's APIs in your AI plus a tile for integrating them into your stack, gets you onto a free Nimble trial and connected, then routes your request. |
| [`account-deep-research`](skills/account-deep-research/SKILL.md) | Cited account research with 12 GTM Web Search Agents (account brief, account signals, buying trigger monitor, decision makers, competitive intelligence, brand intelligence, social media monitor, account enrichment, GTM account enrichment, account discovery, ICP discovery, local business discovery), plus a playbook for building your own agent when none fits. |
| [`account-fast-search`](skills/account-fast-search/SKILL.md) | Answers in seconds with Nimble Search, Extract and Extract Templates: query patterns, first-party source priority, date scoping, entity disambiguation and privacy-safe sourcing for any account, person or competitor question. |
| [`people-research`](skills/people-research/SKILL.md) | People research at two speeds: the Search API answers who holds a role, verified as current, in seconds; six people agents go deeper (people discovery from an ICP, person brief, decision makers, buying committee map, contact job-change monitor, social media monitor). Includes person disambiguation and privacy rules. |
| [`account-lists-and-enrichment`](skills/account-lists-and-enrichment/SKILL.md) | Build ICP and local account lists with near-misses, and enrich CSVs and CRM records at scale: batching, concurrency, verification gates, precedence rules for conflicting sources and safe CRM write-back. Includes the Search API pipeline for when your code owns the workflow. |
| [`gtm-data-at-scale`](skills/gtm-data-at-scale/SKILL.md) | Track GTM signals over time with Extract Templates: hiring across target accounts, software and employee reviews, local business listings, search and AI-answer visibility, social activity. Batch runs of up to 1,000 inputs, scheduled Extract Jobs into S3 or Databricks, and template generation for sites without one. |

## Quick start

1. **Get a free trial:** https://online.nimbleway.com/signup
2. **Install the skills.** One command for Claude Code, Codex, Cursor and other agents:

   ```bash
   npx skills add Nimbleway/nimble-for-gtm-research
   ```

   Other ways to install:

   - **Claude Code, with the MCP server bundled (one step instead of two):** `claude plugin marketplace add Nimbleway/nimble-for-gtm-research`, then `claude plugin install nimble-gtm-research@nimble-gtm-research`.
   - **ChatGPT (Business, Enterprise and Edu):** zip a folder under `skills/` and upload it under **Skills → Create → Upload from your computer**, one zip per skill. On other plans, add the `SKILL.md` files to a project or custom GPT's instructions.
   - **Claude.ai:** zip a folder under `skills/` and upload it under **Customize → Skills**.
   - **Any other agent:** add the `SKILL.md` files to its instructions.

3. **Say "onboard my agent for GTM research"**, or try *"Prepare me for a meeting with Gong (gong.io)."* The onboarding skill checks whether Nimble is connected and, if not, walks you through it for your host. The Nimble MCP server (`https://mcp.nimbleway.com/mcp`) uses OAuth, so no API key is needed:

   | Host | Connect Nimble |
   | - | - |
   | Claude Code | `claude mcp add --transport http --scope user nimble https://mcp.nimbleway.com/mcp`, then run `/mcp` and authorize **nimble** (already bundled if you installed the plugin) |
   | ChatGPT | Settings → Apps & Connectors → add a custom connector with URL `https://mcp.nimbleway.com/mcp` (developer mode on some plans) |
   | Claude.ai / Claude Desktop | **Customize → Connectors** → add a custom connector at `https://mcp.nimbleway.com/mcp` |
   | Codex, Cursor and other MCP clients | Add the server URL above to the client's MCP config; the first tool call starts OAuth |

   For enriching whole CSVs, template batches and scheduled Jobs, also install the CLI (`npm i -g @nimble-way/nimble-cli`) and set `NIMBLE_API_KEY` from https://online.nimbleway.com/settings/api-keys.

   To call the same APIs from your own code, agents or warehouse, see https://docs.nimbleway.com/integrations/overview.

## Example requests

- "Prepare me for a meeting with Gong (gong.io). I'm meeting their VP of RevOps."
- "Check Mercury (mercury.com) for changes since 2026-09-21."
- "Monitor Cato Networks, Mark43, BlueVoyant and commercetools for buying triggers in the last 30 days. We sell revenue software to B2B SaaS companies."
- "At Brex, find the current head of data, VP engineering, head of revenue operations and CFO." (people research)
- "Brief me on Shane Evans at Gong before my call." (people research)
- "Check which of these 40 champions changed jobs since June." (people research)
- "Find 15 heads of RevOps at US B2B SaaS companies with 200 to 2,000 employees that raised since 2025." (people research)
- "Compare Slack, Microsoft Teams and Google Chat on published pricing, target customers and recent launches."
- "Who is Datadog's current CRO, and since when?" (people research, fast path)
- "Find up to 15 US legal AI companies, Series A to C since April 2025, 50 to 500 employees, hiring AEs. Show near-misses." (lists)
- "Enrich these 200 domains with HQ, headcount, last round and CRO, and flag conflicts before we import to Salesforce." (enrichment)
- "Track new sales job postings at our top 300 accounts every Monday." (GTM data at scale)
- "Every week, ask ChatGPT, Perplexity and Google AI Mode the 20 buyer questions in our category and track whether we are mentioned." (GTM data at scale)

## Principles every skill follows

- **Public information only.** No logged-in, paywalled or purchased data, and no emails or phone numbers constructed from patterns.
- **First-party sources first.** The company's own site, newsroom, careers page and ATS board, then filings and registries, then reputable press; aggregators are for discovery.
- **Every value is sourced and dated.** If nobody published a value, it is reported as not found, not estimated. Lists are never padded to reach a count.
- **Event dates, not article dates.** A signal counts when the event happened in the window, not when a story about it was republished.

## Benchmark

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="skills/onboard-your-gtm-agent/assets/benchmark-chart-dark.svg">
  <img alt="Deep research task comparison for GTM: accuracy + coverage score vs. cost per run. Claude Opus 5.5 0.520 at $0.28, Nimble 0.497 at $0.10, GPT-6.1 Sol 0.448 at $0.21, Exa 0.405 at $0.10, Parallel 0.357 at $0.10, Firecrawl 0.316 at $0.10." src="skills/onboard-your-gtm-agent/assets/benchmark-chart-light.svg" width="640">
</picture>

*GTM Use-Case Benchmark v2, 10 tasks, November 2026. Higher and further left is better.*

In Nimble's public GTM Use-Case Benchmark v2 (meeting prep and signal tracking, 10 tasks, six providers, November 2026), Nimble scored highest of the four research APIs at the same $0.10 a run (0.497), found the most verified facts of any provider and had the best signal-tracking score, at about a third of Claude Opus 5.5's cost. Claude Opus 5.5 scored higher overall (0.520), mostly on meeting prep. Tables, method and caveats: [`benchmark/README.md`](benchmark/README.md).

## Layout

```
skills/
  onboard-your-gtm-agent/SKILL.md
  onboard-your-gtm-agent/assets/                # prebuilt benchmark chart + tiles (inline fragment, page, PNG, SVGs) and build.py
  account-deep-research/SKILL.md
  account-deep-research/agents/*.json           # 12 agent specs: skill, output schema, example questions
  account-fast-search/SKILL.md
  account-fast-search/references/source-map.md
  people-research/SKILL.md
  people-research/agents/*.json                 # 6 people agent specs
  account-lists-and-enrichment/SKILL.md
  gtm-data-at-scale/SKILL.md
  gtm-data-at-scale/references/template-catalog.md
benchmark/README.md                             # GTM Use-Case Benchmark v2 results
.claude-plugin/                                 # Claude Code plugin + marketplace manifests
.mcp.json                                       # Nimble MCP server, bundled with the Claude Code plugin
```

Every agent spec is a snapshot of a Nimble Web Search Agent gallery template. Three of them (`gtm-buying-trigger-monitor`, `gtm-account-enrichment`, `gtm-icp-discovery`) started in Nimble's [GTM developer guide](https://www.nimbleway.com/blog/building-gtm-agents-three-use-cases-with-nimbles-apis) and its runnable apps in [Nimbleway/cookbook](https://github.com/Nimbleway/cookbook/tree/main/apps).

## Docs

- Nimble docs: https://docs.nimbleway.com (machine index: https://docs.nimbleway.com/llms.txt)
- Web Search Agents: https://docs.nimbleway.com/nimble-sdk/web-search-agents/overview
- Running agents at scale: https://docs.nimbleway.com/nimble-sdk/web-search-agents/best-practices/running-at-scale
- Search: https://docs.nimbleway.com/nimble-sdk/web-tools/search
- Extract Templates: https://docs.nimbleway.com/nimble-sdk/web-tools/extract/template
- Extract Jobs: https://docs.nimbleway.com/nimble-sdk/agentic/jobs

## License

MIT
