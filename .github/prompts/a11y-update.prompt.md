---
name: a11y-update
description: "Get the latest accessibility improvements across VS Code and tracked repos — with WCAG cross-references and ARIA pattern mapping"
agent: insiders-a11y-tracker
tools:
  - github/*
  - createFile
  - createDirectory
  - ask_questions
---

Show me the latest accessibility improvements across tracked repositories.

${input:scope:Optional: 'insiders', 'stable', 'both', a specific month, 'screen reader', search keywords, or 'track owner/repo' to add a new repo}

## Behavior

Interpret the scope:

- **No input / "both"** → show recent a11y changes from both Insiders and Stable channels plus any tracked repos
- **"insiders"** → only Insiders-released changes
- **"stable"** → only Stable-released changes
- **Month name** (e.g., "February", "last month") → search that month's milestone
- **Category** (e.g., "screen reader", "keyboard", "contrast") → filter results by that category
- **Keywords** (e.g., "minimap", "terminal", "editor") → search with those terms + accessibility label
- **"track owner/repo"** → add a new repository to the tracking list for this session
- **"WCAG"** or **"criteria"** → emphasize WCAG cross-references in the output
- **"ARIA"** or **"patterns"** → emphasize ARIA design pattern mapping

Present results as a categorized list grouped by: Screen Reader, Keyboard Navigation, Visual/Contrast, Audio/Motion, Cognitive, Other.

For each issue, include:
- WCAG success criteria reference (e.g., "WCAG 2.4.3 Focus Order (Level A)")
- ARIA design pattern if applicable (e.g., "Dialog pattern")
- Impact level: Critical / Major / Minor
- Assistive technologies affected

After showing results, offer: _"Want me to generate a full monthly accessibility report with WCAG coverage analysis, or dive into a specific change?"_
