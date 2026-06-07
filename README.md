# Planable MCP Skills

Production-ready Claude Agent Skills for social media managers, paired with the [Planable MCP server](https://mcp.planable.io/mcp). Each skill is a packaged instruction set Claude loads automatically when relevant — turning Planable data (companies, pages, posts, approvals, comments, media, analytics) into a finished SMM deliverable: post batches, approval roundups, performance reports, content calendar audits, cross-client overviews, and content pattern analysis.

These skills follow [Anthropic's Agent Skills spec](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview): each `SKILL.md` has YAML frontmatter that tells Claude when to use it, and the body is loaded only when triggered (progressive disclosure).

## Skills

| Skill | What it produces | Primary triggers |
|---|---|---|
| [draft-post-batch](skills/draft-post-batch/SKILL.md) | Platform-adapted draft posts created directly in Planable from a brief, with preview before commit, varied hooks, and validation flags | "draft posts", "write 5 LinkedIn posts", "create a post batch" |
| [pending-approvals-roundup](skills/pending-approvals-roundup/SKILL.md) | Single roundup of every post awaiting sign-off across all client workspaces, with 48h-deadline posts called out and publishing errors flagged separately | "what's pending approval", "approval queue", "what needs sign-off" |
| [monthly-performance-summary](skills/monthly-performance-summary/SKILL.md) | Client-ready HTML report from Planable analytics or any CSV export — KPI cards, per-platform breakdowns, top 5 posts, what worked / what to watch | "monthly report", "performance summary", "client report" |
| [content-calendar-audit](skills/content-calendar-audit/SKILL.md) | This-week schedule mapped by day with approval status, draft/missing-date callouts, gap detection, and an offer to draft fill-in content | "what's going out this week", "calendar audit", "weekly planning" |
| [cross-client-metrics-overview](skills/cross-client-metrics-overview/SKILL.md) | Comparative table across every client/workspace ranked by engagement rate, impressions, or volume — with top performer, most improved, and engagement-drop flags | "compare clients", "agency overview", "cross-workspace metrics" |
| [content-pattern-intelligence](skills/content-pattern-intelligence/SKILL.md) | 2–4 named recurring patterns per lens (engagement, impressions, engagement rate) with real post examples and specific hypotheses to test next | "what's working", "content patterns", "what should I test next" |

Two skills work without a Planable account by accepting a CSV export from any analytics tool: `monthly-performance-summary` and `content-pattern-intelligence`.

## Install

This repo doubles as a [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces). Installing the `planable-smm` plugin registers all six skills and auto-configures the Planable remote MCP server in one step.

### Claude Code (terminal)

```bash
/plugin marketplace add Planable/smm-skills
/plugin install planable-smm@planable
```

Skills appear under the `planable-smm` namespace — e.g. `/planable-smm:draft-post-batch`. Or just describe what you want (*"draft 5 LinkedIn posts for Acme"*, *"what's pending approval"*) and Claude picks the right skill automatically based on its frontmatter. Update later with `/plugin marketplace update planable`.

### Claude Desktop

If you use Cowork in Claude Desktop, install via the UI:

1. Open **Customize** in the sidebar.
2. Click **Personal plugin** → **+ Create plugin**.
3. Click **Add marketplace** and enter `Planable/smm-skills`.
4. Install `planable-smm` once the marketplace loads.

### Connect Planable

The Planable remote MCP (`https://mcp.planable.io/mcp`) auto-registers when you install the plugin — there's no separate `claude mcp add` step. On your first session, run `/mcp` and sign in via OAuth. No API token to manage.

If you don't have a Planable account yet, [sign up](https://planable.io) — a Team plan (or higher) is required for MCP access.

### Claude.ai projects (manual)

The plugin format is Claude Code / Desktop only. If you use Claude.ai projects instead, attach the individual `SKILL.md` files (or a zip of the `skills/` folder) to a Project — see [Anthropic's Agent Skills docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview). You'll also need to connect the [Planable MCP server](https://mcp.planable.io/mcp) separately via your Claude.ai integrations.

## How these skills chain

A typical agency week:

1. `pending-approvals-roundup` Monday morning — clear the queue.
2. `content-calendar-audit` — see what's going out this week.
3. `draft-post-batch` — fill any gaps.
4. End-of-month: `monthly-performance-summary` per client + `cross-client-metrics-overview` for the agency view.
5. Quarterly: `content-pattern-intelligence` — set hypotheses for the next batch.

## Requirements

- **Claude plan**: Pro, Max, or Teams (Skills are not available on free tier).
- **Planable plan**: MCP access on Team plan or higher. Analytics add-on required for the analytics columns in `cross-client-metrics-overview` and the Planable mode of `monthly-performance-summary` / `content-pattern-intelligence`.
- **Permissions**: Skills inherit the connected user's Planable permissions.
- **Optional X/Twitter research input**: Teams that already use OpenClaw can use [TweetClaw](https://www.npmjs.com/package/@xquik/tweetclaw) (`@xquik/tweetclaw`) to collect source material such as search tweets, search tweet replies, user lookup, or follower export summaries before drafting. Planable remains the place for drafts, approvals, scheduling, and publishing.
- **Drafts only**: `draft-post-batch` creates drafts; nothing publishes to social platforms without explicit user action in Planable.

## Links

- Planable: https://planable.io
- Planable remote MCP: https://mcp.planable.io/mcp
- Planable MCP help: https://help.planable.io/hc/en-us/articles/27538577098780-How-to-connect-Planable-MCP-to-your-AI-tools
- Anthropic Agent Skills spec: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

## License

MIT. See `LICENSE`.

## Contributing

Bug reports and improvements welcome. Open an issue with the skill name, the input, and the unexpected output.
