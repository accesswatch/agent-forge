---
name: pr-comment
description: "Add line-specific review comments to a PR with interactive file selection"
agent: pr-review
tools:
  - github/*
  - readFile
  - ask_questions
---

Add targeted review comments to specific lines in a pull request.

${input:pr:PR reference — e.g. owner/repo#123 or a GitHub PR URL}

## Steps

1. Parse the PR reference to extract owner, repo, and PR number.
2. Fetch changed files with #tool:mcp_github_github_pull_request_read (method: `get_files`).
3. Also check release context — note if this PR is release-bound so the user can prioritize blocking vs. non-blocking comments.
4. Use #tool:ask_questions to present the changed files as selectable options — include filename, change type, risk level, and changes stats for each option.
5. Show the diff for the selected file with line numbers.
6. Collect from the user:
   - **Line(s):** single line or range (e.g., "42" or "42-50")
   - **Side:** new code (RIGHT) or old code (LEFT) — default to RIGHT
   - **Comment:** what to say
   - **Priority level:** CRITICAL, IMPORTANT, SUGGESTION, NIT, or PRAISE (per code review standards)
7. Preview the comment with code context:
   > **Comment on `{file}` line {N} — {PRIORITY}:**
   > ```
   > {code at that line}
   > ```
   > {comment text}
8. Use #tool:ask_questions: **Submit**, **Edit**, **Add another comment first**, **Cancel**.
9. Create a pending review → add comment(s) → when ready, ask for review event:
   - **Approve** — looks good
   - **Request Changes** — needs work
   - **Comment Only** — feedback without formal verdict
10. Submit with #tool:mcp_github_github_pull_request_review_write (method: `submit_pending`).
11. Confirm with a link to the submitted review.

**Batch mode:** If the user wants to comment on multiple files, loop steps 4-7 before submitting once.

**Release awareness:** If the PR is release-bound, remind the user to separate blocking issues from nice-to-haves for the release.
