---
name: review-pr
description: "Full PR review with diff analysis, before/after snapshots, reactions, release context, and saved workspace documents in markdown + HTML"
agent: pr-review
tools:
  - github/*
  - fetch
  - readFile
  - codebase
  - createFile
  - createDirectory
  - editFiles
  - ask_questions
---

Perform a comprehensive code review of the specified pull request and save review documents to the workspace in both markdown and HTML formats.

${input:pr:PR reference — e.g. owner/repo#123 or a GitHub PR URL}

## Steps

1. Parse the PR reference (supports `owner/repo#N`, `#N` with workspace repo, or full URL).
2. Fetch all PR assets in one sweep:
   - Metadata via #tool:mcp_github_github_pull_request_read (method: `get`)
   - Changed files via #tool:mcp_github_github_pull_request_read (method: `get_files`)
   - Full diff via #tool:mcp_github_github_pull_request_read (method: `get_diff`)
   - Review comments via #tool:mcp_github_github_pull_request_read (method: `get_review_comments`)
   - Commits via #tool:mcp_github_github_list_commits
   - Reactions on the PR description and comments
   - Release context — check if targeting a release branch or in a milestone
   - Related GitHub Discussions
3. For key changed files (not config/lock files), fetch before/after content via #tool:mcp_github_github_get_file_contents for both base and head branches.
4. Classify each file change (Feature / Bug Fix / Refactor / Tests / Config / Docs) and assess risk (High / Medium / Low).
5. Generate a comprehensive review in chat with: overview table, file-by-file analysis with diffs and before/after, developer comments thread, reactions summary, release context, and verdict.
6. **Save BOTH review documents:**
   - Markdown: `.github/reviews/prs/{repo}-pr-{number}.md`
   - HTML: `.github/reviews/prs/{repo}-pr-{number}.html`
   Include the checklist, action items, reactions, release context, and a "My Notes" section.
7. After completion, offer: _"Review documents saved. Want to comment on specific files, approve, or request changes?"_
