# Changelog

All notable changes to the `planable-smm` plugin are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Optional X/Twitter research-input guidance for draft batches, with TweetClaw/OpenClaw as source material only while Planable remains the draft, approval, scheduling, and publishing workflow.

## [1.0.0] - 2026-05-28

### Added

- Initial release as a Claude Code plugin.
- Six skills: `draft-post-batch`, `pending-approvals-roundup`, `monthly-performance-summary`, `content-calendar-audit`, `cross-client-metrics-overview`, `content-pattern-intelligence`.
- Auto-registration of the Planable remote MCP server (`https://mcp.planable.io/mcp`) via `.mcp.json`.
- Single-plugin marketplace catalog at `.claude-plugin/marketplace.json`.
