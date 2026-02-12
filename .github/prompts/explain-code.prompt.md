---
name: explain-code
description: "Understand specific lines, functions, or blocks of code in a PR diff — plain language explanations with context"
agent: pr-review
tools:
  - github/*
  - fetch
  - readFile
  - codebase
  - ask_questions
---

Explain specific code in a pull request — what it does, why it's there, and what changed.

${input:target:What to explain — e.g. 'lines 40-60 in auth.ts on PR #15', 'the handleAuth function in PR owner/repo#15', 'what changed in utils.ts'}

## Steps

1. Parse the target to extract: PR reference, file path (if specified), and line numbers or function name.
2. Fetch the PR metadata and changed files list.
3. **If lines are specified** (e.g., "lines 40-60 in auth.ts"):
   - Fetch the full file from the PR's head branch using #tool:mcp_github_github_get_file_contents.
   - Also fetch the base branch version to show what changed.
   - Display the target lines with ~10 lines of surrounding context, with line numbers.
   - Explain:
     - **What this code does** — line-by-line plain language breakdown
     - **Why it's here** — purpose inferred from PR description, commit messages, and surrounding code
     - **What changed** — before vs. after if these lines were modified
     - **Side effects** — downstream impacts, state mutations, API calls, error paths
     - **Potential concerns** — edge cases, missing error handling, performance implications

4. **If a function/class is specified** (e.g., "the handleAuth function"):
   - Search the PR diff for the function definition.
   - Show the full function with context.
   - Explain at a higher level: purpose, parameters, return values, error handling, and how it fits the broader change.

5. **If a file is specified without lines** (e.g., "what changed in utils.ts"):
   - Show the full diff for that file.
   - Explain each change hunk: what was added/removed/modified and why.

6. After explaining, offer:
   _"Want me to comment on these lines, suggest a change, or see more context?"_
