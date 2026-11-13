# Changelog

All notable changes to the `planable-smm` plugin are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2026-11-13

### Changed

- `draft-post-batch`: drafts can now be edited with `update_post`; media goes in `mediaUrls` or `mediaIds`, and files from the user's computer through the upload card; `scheduledAt` stays a proposed date unless the user asks to schedule with `publishAtScheduledDate`; suggested dates from `get_posting_times`; `teamOnly` is left to the workspace default unless the user asks; times are converted from the workspace timezone, and the user is warned before posts are scheduled for publishing.
- `pending-approvals-roundup`: offers to approve (`approve_post`) after the user confirms, warning about auto-scheduling and grouped posts, or to send a post back with a `create_comment` reason; pages through all results.
- `content-calendar-audit`: uses the `show_calendar` calendar card for calendar weeks and months, counting only posts confirmed for publishing; separates posts that failed to publish (`PUBLISHED_WITH_ERRORS`) from posts with incompatible content (`WITH_ERRORS`); pages through `list_posts` results.
- `monthly-performance-summary`: ranks top posts over the whole period instead of taking the 5 newest, checking the count against `totalPosts`; notes the analytics add-on, X coverage and data refresh.
- `cross-client-metrics-overview`: reports workspaces without the analytics add-on as "No data".
- `seo-ai-social-report`, `client-onboarding-proposal`: rank top posts over the period instead of taking the 5 newest.
- README: `draft-post-batch` schedules posts for publishing only when asked.

### Added

- Listing details for the Claude directory: display name "Planable", icon, and support, privacy and terms links.
- `content-pattern-intelligence`: checks and refreshes post-level metrics (`get_post_metrics_summary`, `refresh_post_metrics`), treats refreshes as queued syncs that land after a few minutes, and checks fetched posts against `totalPosts`.

## [1.0.0] - 2026-05-28

### Added

- Initial release as a Claude Code plugin.
- Six skills: `draft-post-batch`, `pending-approvals-roundup`, `monthly-performance-summary`, `content-calendar-audit`, `cross-client-metrics-overview`, `content-pattern-intelligence`.
- Auto-registration of the Planable remote MCP server (`https://mcp.planable.io/mcp`) via `.mcp.json`.
- Single-plugin marketplace catalog at `.claude-plugin/marketplace.json`.
