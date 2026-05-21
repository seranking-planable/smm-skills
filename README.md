# Planable MCP Skills

Production-ready Claude Agent Skills for social media managers, paired with the [Planable MCP server](https://mcp.planable.io/mcp). Each skill is a packaged instruction set Claude loads automatically when relevant — turning Planable data (companies, pages, posts, approvals, comments, media, analytics) into a finished SMM deliverable: post batches, approval roundups, performance reports, content calendar audits, cross-client overviews, and content pattern analysis.

These skills follow [Anthropic's Agent Skills spec](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview): each `SKILL.md` has YAML frontmatter that tells Claude when to use it, and the body is loaded only when triggered (progressive disclosure).

## Skills

| Skill | What it produces | Primary triggers |
|---|---|---|
| [smm-draft-post-batch](skills/smm-draft-post-batch/SKILL.md) | Platform-adapted draft posts created directly in Planable from a brief, with preview before commit, varied hooks, and validation flags | "draft posts", "write 5 LinkedIn posts", "create a post batch" |
| [smm-pending-approvals-roundup](skills/smm-pending-approvals-roundup/SKILL.md) | Single roundup of every post awaiting sign-off across all client workspaces, with 48h-deadline posts called out and publishing errors flagged separately | "what's pending approval", "approval queue", "what needs sign-off" |
| [smm-monthly-performance-summary](skills/smm-monthly-performance-summary/SKILL.md) | Client-ready HTML report from Planable analytics or any CSV export — KPI cards, per-platform breakdowns, top 5 posts, what worked / what to watch | "monthly report", "performance summary", "client report" |
| [smm-content-calendar-audit](skills/smm-content-calendar-audit/SKILL.md) | This-week schedule mapped by day with approval status, draft/missing-date callouts, gap detection, and an offer to draft fill-in content | "what's going out this week", "calendar audit", "weekly planning" |
| [smm-cross-client-metrics-overview](skills/smm-cross-client-metrics-overview/SKILL.md) | Comparative table across every client/workspace ranked by engagement rate, impressions, or volume — with top performer, most improved, and engagement-drop flags | "compare clients", "agency overview", "cross-workspace metrics" |
| [smm-content-pattern-intelligence](skills/smm-content-pattern-intelligence/SKILL.md) | 2–4 named recurring patterns per lens (engagement, impressions, engagement rate) with real post examples and specific hypotheses to test next | "what's working", "content patterns", "what should I test next" |

Two skills work without a Planable account by accepting a CSV export from any analytics tool: `smm-monthly-performance-summary` and `smm-content-pattern-intelligence`.

## How to use

1. Connect the [Planable MCP server](https://mcp.planable.io/mcp) to Claude (Pro, Max, or Teams plan; Planable Team plan or higher).
2. Make these skills available to Claude — see [Anthropic's Agent Skills docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for installation in your surface (Claude.ai projects, Claude Desktop, Claude Code).
3. Just describe what you want — Claude picks the right skill automatically based on its frontmatter.

## How these skills chain

A typical agency week:

1. `smm-pending-approvals-roundup` Monday morning — clear the queue.
2. `smm-content-calendar-audit` — see what's going out this week.
3. `smm-draft-post-batch` — fill any gaps.
4. End-of-month: `smm-monthly-performance-summary` per client + `smm-cross-client-metrics-overview` for the agency view.
5. Quarterly: `smm-content-pattern-intelligence` — set hypotheses for the next batch.

## Requirements

- **Claude plan**: Pro, Max, or Teams (Skills are not available on free tier).
- **Planable plan**: MCP access on Team plan or higher. Analytics add-on required for the analytics columns in `smm-cross-client-metrics-overview` and the Planable mode of `smm-monthly-performance-summary` / `smm-content-pattern-intelligence`.
- **Permissions**: Skills inherit the connected user's Planable permissions.
- **Drafts only**: `smm-draft-post-batch` creates drafts; nothing publishes to social platforms without explicit user action in Planable.

## Links

- Planable: https://planable.io
- Planable remote MCP: https://mcp.planable.io/mcp
- Planable MCP help: https://help.planable.io/hc/en-us/articles/27538577098780-How-to-connect-Planable-MCP-to-your-AI-tools
- Anthropic Agent Skills spec: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

## License

MIT. See `LICENSE`.

## Contributing

Bug reports and improvements welcome. Open an issue with the skill name, the input, and the unexpected output.