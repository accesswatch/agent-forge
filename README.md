<div align="center">

# 🔥 Agent Forge

### *Where AI Agents Are Forged for GitHub Mastery*

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agents-8957E5?logo=github)](https://docs.github.com/copilot)
[![Agents](https://img.shields.io/badge/Agents-5-brightgreen)](.github/agents/)
[![Prompts](https://img.shields.io/badge/Prompts-28-orange)](.github/prompts/)
[![Accessibility](https://img.shields.io/badge/A11y-WCAG%20AA-success)](Documentation/GUIDE.md#screen-reader-accessibility)

**Stop tab-switching. Start commanding.**
A curated collection of GitHub Copilot agents and prompt templates that turn your editor into a GitHub command center.

[Getting Started](Documentation/GETTING-STARTED.md) · [Full Guide](Documentation/GUIDE.md) · [Contributing](CONTRIBUTING.md) · [Setup](SETUP.md)

</div>

---

## ✨ What Is This?

**Agent Forge** is a handcrafted collection of **5 specialized AI agents** and **28 prompt commands** that live inside VS Code's Copilot Chat. They talk to GitHub for you — finding issues, reviewing code, tracking team progress, managing releases, and monitoring accessibility — all without opening a single browser tab.

Type a question in plain English. Get back organized, prioritized, actionable answers. It's like having a team of tireless assistants who never miss a notification.

## 🎯 What You Can Do

| Capability | What Happens |
|---|---|
| **Morning Briefings** | One command sweeps every repo you touch — issues, PRs, releases, CI, security alerts, community reactions — and builds a prioritized dashboard |
| **Code Reviews** | Full diff analysis with risk assessment, before/after snapshots, CI results, and inline commenting — all from chat |
| **Issue Triage** | Smart priority scoring with community sentiment, release awareness, batch replies, and saved searches |
| **Team Analytics** | Velocity trends, review turnaround, bottleneck detection, code hotspots, and workload balancing |
| **Release Management** | Auto-categorized release notes, readiness checklists, and complete release workflows |
| **Accessibility Tracking** | WCAG/ARIA cross-referenced change monitoring with assistive technology impact analysis |
| **Security Monitoring** | Dependabot alerts, security advisories, and dependency tracking across all repos |
| **Full GitHub Interaction** | Comment, react, merge, close, label, assign, transfer — without opening your browser |

## 🛠️ The Agents

| Agent | Invoke With | Superpower |
|---|---|---|
| **Daily Briefing** | `@daily-briefing` | Your prioritized overview of everything happening across all repos |
| **Issue Tracker** | `@issue-tracker` | Find, triage, reply to, and manage issues with smart search |
| **PR Review** | `@pr-review` | Full code reviews with risk assessment, comments, and merge |
| **Analytics** | `@analytics` | Team metrics, velocity, bottlenecks, and workload insights |
| **A11y Tracker** | `@insiders-a11y-tracker` | Accessibility change tracking with WCAG cross-references |

## 🚀 Quick Start

```
1. Open VS Code with GitHub Copilot installed
2. Open this repo as a workspace folder
3. Press Ctrl+Shift+I to open Copilot Chat
4. Type: @daily-briefing morning briefing
5. ☕ Grab a coffee while your command center comes alive
```

> **That's it.** No API keys. No CLI tools. No configuration required. If Copilot Chat works, the agents work.

For a complete walkthrough, see the [Getting Started Guide](Documentation/GETTING-STARTED.md).

## ⚡ 28 Slash Commands

Type `/` in Copilot Chat and pick from the full menu:

<details>
<summary><strong>View all commands</strong></summary>

| Command | What It Does |
|---|---|
| `/daily-briefing` | Generate your prioritized daily briefing |
| `/my-issues` | Your open issues, sorted by priority |
| `/my-prs` | Your PRs with review status and CI health |
| `/review-pr` | Full code review with dual-format documents |
| `/pr-report` | Save or update a PR review as workspace docs |
| `/pr-comment` | Line-specific PR comments |
| `/explain-code` | Understand lines, functions, or blocks in a PR |
| `/merge-pr` | Merge with readiness checks and strategy selection |
| `/pr-author-checklist` | Self-review before requesting reviews |
| `/issue-reply` | Draft and post context-aware replies |
| `/create-issue` | Create issues with smart templates |
| `/manage-issue` | Edit, label, assign, close, transfer |
| `/react` | Add emoji reactions to anything |
| `/triage` | Prioritized triage dashboard |
| `/refine-issue` | Add acceptance criteria with community context |
| `/address-comments` | Work through PR review comments systematically |
| `/a11y-update` | Accessibility updates with WCAG cross-refs |
| `/team-dashboard` | Team activity and bottleneck overview |
| `/my-stats` | Your personal metrics with team comparison |
| `/draft-release` | Auto-categorized release notes |
| `/ci-status` | CI/CD health dashboard |
| `/security-dashboard` | Dependabot alerts and security advisories |
| `/release-prep` | Complete release preparation workflow |
| `/sprint-review` | End-of-sprint summary with velocity metrics |
| `/onboard-repo` | First-time repo scan and health check |
| `/notifications` | Manage GitHub notifications from the editor |
| `/manage-branches` | Branch listing, cleanup, and comparison |
| `/project-status` | GitHub Projects overview with column metrics |

</details>

## 📂 Repository Structure

```
agent-forge/
├── .github/
│   ├── agents/                    # 🤖 The 5 AI agents + shared config
│   │   ├── daily-briefing.agent.md
│   │   ├── issue-tracker.agent.md
│   │   ├── pr-review.agent.md
│   │   ├── analytics.agent.md
│   │   ├── insiders-a11y-tracker.agent.md
│   │   ├── shared-instructions.md
│   │   ├── code-review-standards.md
│   │   └── preferences.example.md  # Copy → preferences.md & customize
│   ├── prompts/                   # ⚡ 28 slash command templates
│   ├── ISSUE_TEMPLATE/            # 📋 Issue templates for contributions
│   └── pull_request_template.md   # 📝 PR template
├── Documentation/
│   ├── GETTING-STARTED.md         # 🚀 Your first hour with the agents
│   ├── GETTING-STARTED.html
│   ├── GUIDE.md                   # 📚 The complete reference guide
│   └── guide.html
├── ai-instructions/               # 🧠 Integration guides for AI platforms
│   ├── copilot-integration.md
│   ├── claude-instructions.md
│   └── openai-integration.md
├── CONTRIBUTING.md                # 🤝 How to contribute (PR workflow)
├── SETUP.md                       # ⚙️ Setup & configuration
├── SECURITY.md                    # 🔒 Security policy
├── LICENSE                        # MIT License
├── CODEOWNERS                     # 👑 Code ownership rules
└── README.md                      # You are here ✨
```

## 🌟 Why Agent Forge?

<table>
<tr>
<td width="50%">

### Before Agent Forge
- 😩 Open browser, check notifications
- 😩 Click into issue, read comments
- 😩 Switch to PR tab, scan the diff
- 😩 Open CI results in another tab
- 😩 Check Dependabot in yet another tab
- 😩 Repeat for every repo you touch

</td>
<td width="50%">

### After Agent Forge
- ✨ `@daily-briefing morning briefing`
- ✨ Everything. In one document.
- ✨ Prioritized. Actionable. Beautiful.
- ✨ Reply, review, merge — from chat.
- ✨ Zero browser tabs required.
- ☕ More coffee time.

</td>
</tr>
</table>

## ♿ Accessibility First

Every document the agents generate comes in **dual format** — Markdown for editing in VS Code and HTML optimized for screen readers with:

- Skip links and ARIA landmarks
- Proper heading hierarchy (never skipped)
- Accessible tables with captions and scoped headers
- Descriptive link text (never bare URLs)
- Status communicated through text, not just color or emoji
- `prefers-color-scheme` and `prefers-reduced-motion` support
- WCAG AA contrast compliance

## 🧠 Works With Other AI Platforms

Agent Forge is built for GitHub Copilot, but the agents and prompts can be adapted for other AI platforms. See the [ai-instructions](ai-instructions/) folder for integration guides:

- **GitHub Copilot** — Native, zero-config support
- **Claude AI** — Context-based integration
- **ChatGPT / OpenAI** — Custom instructions and API patterns

## 🤝 Contributing

We welcome contributions! Agent Forge uses a **fork-and-pull-request workflow** to keep the `main` branch stable and reliable.

**The golden rules:**

1. **Fork** the repo and create a descriptive feature branch
2. **Make** your changes and test thoroughly
3. **Submit** a PR using our [PR template](.github/pull_request_template.md)
4. **Address** review feedback
5. **Celebrate** when your contribution gets merged 🎉

> **Direct pushes to `main` are not allowed.** All changes must go through a pull request with at least one approval. This keeps the forge strong. 🔥

See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide — branch naming conventions, commit standards, PR requirements, and what makes a great agent submission.

## 🔒 Security

Found a vulnerability? **Please don't open a public issue.** Email jeff@jeffbishop.com or see [SECURITY.md](SECURITY.md) for responsible disclosure instructions.

## 📄 License

[MIT](LICENSE) — Use it, fork it, customize it, make it yours.

---

<div align="center">

**Built with ✨ by [Jeff Bishop](https://github.com/accesswatch)**

*Stop switching tabs. Start forging workflows.*

[⬆ Back to top](#-agent-forge)

</div>