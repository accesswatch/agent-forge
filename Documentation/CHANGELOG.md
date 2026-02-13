# Changelog

All notable changes to Agent Forge are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [Unreleased]

*No unreleased changes.*

---

## [v1.1.0] - 2026-02-13

### Added

- **Line-Numbered Diff Display** -- PR Review agent now shows every diff with dual line numbers (old file / new file), making it trivial to reference any line in a review. Users can say "comment on L42" or "explain L40-L60" to interact with code directly from the diff output.
- **Change Map** -- Each file in a review includes a hunk-by-hunk summary table showing old/new line ranges and developer intent, giving reviewers a bird's-eye view of what changed and why before diving into the code.
- **Annotated Diff Format** -- Diffs use a clean `Old | New | code` column layout with `+`/`-` markers, at least 5 lines of surrounding context per hunk, and `...` dividers between non-adjacent changed regions.
- **Inline Intent Annotations** -- Complex changes get blockquote explanations between diff hunks, inferred from commit messages and code context, so reviewers understand *why* something changed, not just *what* changed.
- **Interactive L-Number Prompts** -- After every diff display, an action menu appears: comment, explain, suggest fix, or view before/after -- all by referencing line numbers from the output.
- **Before/After Snapshots with Line Numbers** -- Collapsible before/after code comparisons include line numbers on every line and a "Lines to watch" callout highlighting the most review-worthy sections.
- **Cross-repo search by default** -- All agents now search every repo the user has access to when no specific repo is mentioned. No configuration required; it works out of the box via the GitHub Search API with the authenticated user's token.
- **Repository Discovery & Scope system** -- New `repos` configuration block in `preferences.md` with five discovery modes: `all` (default), `starred`, `owned`, `configured`, `workspace`. Users can precisely control which repos agents scan.
- **Per-repo tracking overrides** -- Each repo can be configured with granular tracking toggles for issues, pull requests, discussions, releases, security alerts, and CI status. Supports label filters (`labels.include` / `labels.exclude`), path filters, and assignee filters.
- **Per-repo include/exclude lists** -- Explicitly include or exclude repos from agent scans via `repos.include` and `repos.exclude` configuration.
- **Organization-wide search** -- All discovery prompts and agents now accept `org:orgname` to scope searches to a specific GitHub organization.
- **Cross-repo intelligence** -- Agents detect cross-repo references (e.g., "See also owner/other-repo#45"), surface related items across repos, deduplicate results, and group output by repository.
- **Accessibility Tracking configuration** -- New `accessibility_tracking` config block allowing users to track accessibility changes in any repo, not just VS Code. Supports per-repo labels, channels, WCAG/ARIA toggles, and briefing limits.
- **Briefing preferences** -- New `briefing` config block with per-section toggles, cross-repo related item surfacing, and configurable output formats.
- **Search & Discovery preferences** -- New `search` config block with default date windows, auto-broaden/narrow behavior, cross-reference following, and org-level search toggles.
- **Repository Discovery & Scope** section added to `shared-instructions.md` -- ensures all agents share consistent cross-repo behavior.
- **Repository Discovery & Scope** added as the primary configuration section in `SETUP.md`.
- **CHANGELOG.md** -- This file, tracking all changes.

### Changed

- **All 5 agent files** updated for cross-repo awareness:
  - `daily-briefing.agent.md` -- Step 1 now loads repo scope from preferences; accessibility section (2e) now reads from `accessibility_tracking` config with `microsoft/vscode` as fallback default.
  - `issue-tracker.agent.md` -- Step 1 loads repo scope; Step 3 searches all repos by default with scope narrowing support.
  - `pr-review.agent.md` -- Step 1 loads repo scope and per-repo path filters; Step 3 searches all repos by default.
  - `analytics.agent.md` -- Step 1 loads full preferences; supports org-wide scope for analytics.
  - `insiders-a11y-tracker.agent.md` -- Renamed from "VS Code Accessibility Tracker" to "Accessibility Tracker"; now supports multi-repo tracking with configurable query templates; VS Code remains the default tracked repo.
- **All 15 aggregation prompt files** updated for cross-repo defaults:
  - `my-issues.prompt.md` -- Searches all repos by default; accepts `org:orgname` filter.
  - `my-prs.prompt.md` -- Searches all repos by default; accepts `org:orgname` filter.
  - `daily-briefing.prompt.md` -- Scans all discovered repos; accepts `org:orgname` scope.
  - `triage.prompt.md` -- Cross-repo triage by default; loads repo scope from preferences.
  - `notifications.prompt.md` -- Cross-repo by nature; now references preferences for priority/mute settings.
  - `a11y-update.prompt.md` -- Tracks all configured repos; removed hardcoded VS Code reference from description.
  - `team-dashboard.prompt.md` -- Aggregates across all accessible repos; accepts `org:orgname`.
  - `sprint-review.prompt.md` -- Cross-repo sprint data; accepts `org:orgname`.
  - `security-dashboard.prompt.md` -- Loads repo scope from preferences; all repos by default.
  - `my-stats.prompt.md` -- Cross-repo metrics by default; accepts `org:orgname`.
  - `project-status.prompt.md` -- Loads repo scope from preferences; accepts `org:orgname`.
  - `ci-status.prompt.md` -- Loads repo scope from preferences; all repos by default.
  - `onboard-repo.prompt.md` -- Offers to add onboarded repo to preferences for persistent tracking.
- **`preferences.example.md`** -- Massively expanded with `repos`, `accessibility_tracking`, `briefing`, and `search` configuration sections. Serves as the complete configuration reference.
- **`preferences.md` (setup guide)** -- Rewritten with Repository Discovery & Scope as the most prominent section; expanded agent usage examples showing cross-repo commands.
- **`shared-instructions.md`** -- Expanded "Smart Defaults & Inference" section; added comprehensive "Repository Discovery & Scope" section covering all 5 discovery modes, cross-repo intelligence rules, and per-repo tracking granularity.
- **`Documentation/GUIDE.md`** -- Updated Workspace Preferences section with `repos` and `accessibility_tracking` as top configuration items; renamed "VS Code Accessibility Tracker" to "Accessibility Tracker" throughout; added discovery mode table; updated File Reference.
- **`SETUP.md`** -- Added Repository Discovery & Scope as configuration sections 1-2; added Accessibility Tracker agent usage examples; renumbered existing sections.
- **`README.md`** -- Updated capabilities table to emphasize cross-repo defaults; added "Cross-Repo by Default" capability row; updated agent descriptions and slash command descriptions.

### Fixed

- **Non-ASCII character cleanup** -- Removed all non-ASCII characters (emoji, box-drawing, arrows, em-dashes, en-dashes, curly quotes, ellipsis) from 51 files. All markdown files now contain only ASCII characters.
- **Hardcoded repo references** -- Replaced all hardcoded `repo:microsoft/vscode` search queries with configurable defaults that fall back to `microsoft/vscode` when no preferences are set.
- **`accesswatch` assumptions** -- Ensured no agent assumes the user is working on a specific project. Owner credits (Jeff Bishop / accesswatch) preserved as repository metadata, not operational assumptions.

### Changed (PR Review Agent)

- **Step 6 redesigned** -- Replaced the basic "Generate Before/After Snapshots" step with a comprehensive "Line-Numbered Diff Display" system containing 5 substeps (6a-6e).
- **Step 7 templates updated** -- Both markdown and HTML review document templates now include Change Map tables, line-numbered code blocks, annotated diffs with dual line numbers, intent annotations, and "Lines to watch" callouts.
- **Step 8b (Single-Line Comment)** -- Now accepts `L42` format from the numbered diff output; previews show 5 surrounding numbered lines with a `<-- your comment here` indicator.
- **Step 8c (Multi-Line Range Comment)** -- Now accepts `L42-L50` format; previews show the full selected range from the numbered diff.
- **Core Capabilities list** -- Expanded from 15 to 17 items with dedicated entries for Line-Numbered Diff Display and Before/After Snapshots.
- **Prompt files updated** -- `review-pr.prompt.md`, `pr-comment.prompt.md`, `pr-report.prompt.md`, `explain-code.prompt.md`, and `address-comments.prompt.md` updated with Change Map generation, L-number format, line-numbered code previews, and synchronized before/after references.
- **Documentation updated** -- `GUIDE.md` PR Review section rewritten with line-numbered diff description, PR Commenting section updated with L-number format examples, Code Understanding section updated with synchronized before/after examples. `README.md` capabilities table updated.

---

## [v1.0.0] - 2026-02-11

### Added

- Analytics & Insights agent (`@analytics`)
- Workspace Preferences system (`preferences.md`)
- Release management commands (`/draft-release`, `/release-prep`)
- CI/CD health monitoring (`/ci-status`)
- Security dashboard (`/security-dashboard`)
- Notification management (`/notifications`)
- Branch management (`/manage-branches`)
- Project board integration (`/project-status`)
- Sprint review workflow (`/sprint-review`)
- Repo onboarding (`/onboard-repo`)
- PR author self-review checklist (`/pr-author-checklist`)
- Dual-format output (Markdown + HTML) for all generated documents
- Screen reader optimized HTML with skip links, ARIA landmarks, accessible tables
- Reactions and community sentiment tracking
- Release awareness across all agents
- GitHub Discussions monitoring
- WCAG/ARIA cross-referencing in accessibility tracker
- Saved searches and response templates
- Full GitHub interaction from chat (comments, reactions, merge, close, label, assign, transfer)
- 28 total slash commands

---

*For the complete feature reference, see the [Full Guide](GUIDE.md).*
