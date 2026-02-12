# Contributing to Agent Forge 🔥

Welcome, fellow forge worker! We're excited you're interested in contributing to Agent Forge. Whether you're submitting a new agent, refining a prompt, fixing a typo, or improving documentation — every contribution makes the forge stronger.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Contributions Work](#how-contributions-work)
- [Getting Started](#getting-started)
- [Branch & PR Workflow](#branch--pr-workflow)
- [Commit Standards](#commit-standards)
- [What You Can Contribute](#what-you-can-contribute)
- [Quality Standards](#quality-standards)
- [Review Process](#review-process)
- [Recognition](#recognition)

---

## Code of Conduct

Be kind, be constructive, be welcoming. We're building tools that help developers work better — that starts with treating each other well. Harassment, disrespect, and exclusionary behavior have no place here.

---

## How Contributions Work

Agent Forge uses a **fork-and-pull-request** workflow. The `main` branch is protected — no one pushes directly to it (not even the maintainer). Every change goes through a pull request.

```
Fork → Branch → Commit → Push → Pull Request → Review → Merge 🎉
```

**Why?** Because the agents in this repo are used by real people in their daily workflows. A broken agent or malformed prompt can disrupt someone's morning. PRs with review keep the forge reliable.

---

## Getting Started

### 1. Fork the Repository

Click the **Fork** button at the top-right of the [Agent Forge repo](https://github.com/accesswatch/agent-forge).

### 2. Clone Your Fork

```bash
git clone https://github.com/YOUR-USERNAME/agent-forge.git
cd agent-forge
```

### 3. Add the Upstream Remote

```bash
git remote add upstream https://github.com/accesswatch/agent-forge.git
```

### 4. Keep Your Fork Current

Before starting new work, sync with upstream:
```bash
git fetch upstream
git checkout main
git merge upstream/main
```

---

## Branch & PR Workflow

### Branch Naming Convention

Use descriptive, prefixed branch names:

| Prefix | Purpose | Example |
|---|---|---|
| `agent/` | New or updated agent | `agent/code-formatter` |
| `prompt/` | New or updated prompt | `prompt/dependency-check` |
| `docs/` | Documentation changes | `docs/improve-getting-started` |
| `fix/` | Bug fixes | `fix/triage-sort-order` |
| `feature/` | New features or enhancements | `feature/multi-repo-briefing` |

```bash
git checkout -b agent/my-new-agent
```

### Pull Request Requirements

Every PR must:

1. **Target the `main` branch**
2. **Use our [PR template](.github/pull_request_template.md)** — it loads automatically
3. **Have a clear, descriptive title** — e.g., "Add: code-formatter agent for automated style enforcement"
4. **Include a description** explaining what, why, and how to test
5. **Pass all status checks** before merge
6. **Receive at least one approving review**

### PR Size Guidelines

| PR Size | Files Changed | Guidance |
|---|---|---|
| 🟢 Small | 1–3 files | Ideal — fast to review |
| 🟡 Medium | 4–8 files | Acceptable for related changes |
| 🔴 Large | 9+ files | Split into smaller PRs when possible |

### What Happens After You Submit

1. A maintainer will be automatically assigned via CODEOWNERS
2. Automated checks run (if configured)
3. A reviewer will provide feedback — usually within **48 hours**
4. Address any requested changes by pushing to the same branch
5. Once approved, a maintainer merges your PR
6. Your branch is automatically deleted after merge

---

## Commit Standards

### Message Format

Use clear, conventional commit messages:

```
<type>: <short description>

[optional body with more detail]
```

### Commit Types

| Type | When to Use |
|---|---|
| `Add` | New agent, prompt, file, or feature |
| `Update` | Changes to existing content |
| `Fix` | Bug fixes or corrections |
| `Docs` | Documentation-only changes |
| `Refactor` | Restructuring without behavior change |
| `Remove` | Deleting files or features |

### Examples

```bash
git commit -m "Add: security-scanner agent for dependency auditing"
git commit -m "Update: daily-briefing to include release milestones"
git commit -m "Fix: triage prompt missing frontmatter tools field"
git commit -m "Docs: add Claude integration examples"
```

---

## What You Can Contribute

### 🤖 New Agents

Create a new `.agent.md` file in `.github/agents/`:

1. Follow the naming pattern: `{name}.agent.md`
2. Include comprehensive instructions and behavior rules
3. Reference `shared-instructions.md` for dual-output and accessibility standards
4. Define clear handoff points to other agents
5. Test with real GitHub data across multiple scenarios

### ⚡ New Prompt Commands

Create a new `.prompt.md` file in `.github/prompts/`:

1. Follow the naming pattern: `{name}.prompt.md`
2. Include valid YAML frontmatter:
   ```yaml
   ---
   mode: agent
   agent: associated-agent-name
   description: "Clear description of what this command does"
   tools:
     - githubRepo
     - codebase
   ---
   ```
3. Use variable placeholders: `${input:variable:description}`
4. Write clear, actionable instructions

### 📚 Documentation Improvements

- Fix typos, clarify instructions, add examples
- Improve the Getting Started guide or Complete Guide
- Add new integration guides in `ai-instructions/`
- Translate documentation (open an issue first to coordinate)

### 🐛 Bug Fixes

- Agent not behaving as documented
- Prompt template formatting issues
- Broken links or incorrect references
- YAML frontmatter errors

### 💡 Feature Enhancements

- Improve existing agent capabilities
- Add new slash commands for common workflows
- Enhance accessibility of generated documents
- Better error handling and edge case coverage

---

## Quality Standards

### Every Agent Must Have

- [ ] Clear, specific instructions (not vague or generic)
- [ ] Error handling guidance for common failure scenarios
- [ ] Integration with the preferences system (`preferences.md`)
- [ ] Dual-output support (Markdown + accessible HTML) for generated documents
- [ ] Handoff suggestions to related agents
- [ ] Test coverage across at least 3 different repo scenarios

### Every Prompt Must Have

- [ ] Valid YAML frontmatter with `mode`, `agent`, `description`, and `tools`
- [ ] Clear variable placeholders with descriptions
- [ ] Actionable, user-focused instructions
- [ ] Consistent formatting matching existing prompts

### Accessibility Requirements

All generated HTML must include:
- Skip links and ARIA landmarks
- Proper heading hierarchy (never skip levels)
- Accessible tables with captions and scoped headers
- Descriptive link text (no bare URLs or "click here")
- Status communicated through text, not just color or emoji
- WCAG AA contrast compliance

### Documentation Standards

- Write from the user's perspective ("You can..." not "The system...")
- Include real examples, not placeholders
- Keep language approachable — not everyone is a GitHub power user
- Test all code snippets and commands

---

## Review Process

### What Reviewers Look For

| Area | What We Check |
|---|---|
| **Correctness** | Does the agent/prompt work as described? |
| **Quality** | Clear instructions, good error handling? |
| **Consistency** | Follows existing patterns and conventions? |
| **Accessibility** | HTML output meets WCAG AA standards? |
| **Documentation** | Clear description, examples, and usage? |
| **Security** | No exposed secrets, safe data handling? |
| **Scope** | Focused change, not mixing unrelated work? |

### Review Turnaround

- **First review**: Within 48 hours
- **Follow-up reviews**: Within 24 hours
- **Merge after approval**: Same day when possible

### Addressing Feedback

When a reviewer requests changes:
1. Push new commits to the **same branch** (don't rebase during review)
2. Reply to each comment explaining your change
3. Re-request review when ready
4. After merge, the branch is cleaned up automatically

---

## Recognition

Every contributor is appreciated. We recognize contributions through:

- **GitHub contributors list** — automatically tracked
- **Release notes** — your contributions are credited in releases
- **Agent credits** — new agents include an attribution comment

Your first merged PR? Welcome to the forge. 🔥

---

## Questions?

- **Setup help**: See [SETUP.md](SETUP.md)
- **Usage questions**: Check the [Documentation](Documentation/) folder
- **Feature ideas**: [Open a discussion](https://github.com/accesswatch/agent-forge/discussions)
- **Bug reports**: [Open an issue](https://github.com/accesswatch/agent-forge/issues/new/choose)
- **Security concerns**: See [SECURITY.md](SECURITY.md)

---

*Thank you for helping make Agent Forge better for everyone. Every contribution — from a one-line typo fix to a whole new agent — makes the forge stronger. Let's build something great together.* 🔥