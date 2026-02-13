# GitHub Agents -- The Complete Guide

> **Welcome back. You're in the right place.**
>
> If you followed the [Getting Started guide](GETTING-STARTED.md), you already know the basics -- you've run a briefing, explored an issue, tried a slash command, and maybe even left a comment without opening your browser.
>
> This guide goes deeper. Much deeper. But don't worry -- we'll take it one section at a time, at whatever pace feels right. Think of this as a reference you'll keep coming back to as you discover new things you want to do.
>
> **New here?** Start with the [Getting Started guide](GETTING-STARTED.md) first. It'll walk you through setup and your first few commands. Then come back here when you're ready for more.

---

## Table of Contents

Don't feel like you need to read this top to bottom. Jump to whatever catches your eye -- every section is self-contained.

- [What Is This?](#what-is-this)
- [What's New](#whats-new)
- [Quick Start (2 minutes)](#quick-start)
- [Setup & Prerequisites](#setup--prerequisites)
- [The Agents](#the-agents)
  - [Daily Briefing](#daily-briefing)
  - [Issue Tracker](#issue-tracker)
  - [PR Review](#pr-review)
  - [Analytics & Insights](#analytics--insights)
  - [Accessibility Tracker](#accessibility-tracker)
- [Workspace Preferences](#workspace-preferences)
- [The Prompt Commands](#the-prompt-commands)
- [Never Leave Your Editor](#never-leave-your-editor)
  - [PR Commenting & Code Review](#pr-commenting--code-review)
  - [Code Understanding](#code-understanding)
  - [Issue Interactions](#issue-interactions)
  - [Reactions](#reactions)
  - [PR Management](#pr-management)
  - [Issue Management](#issue-management)
  - [Branch Management](#branch-management)
  - [Notifications](#notifications)
  - [Release Management](#release-management)
- [Daily Workflows](#daily-workflows)
  - [Morning Routine](#morning-routine)
  - [PR Review Flow](#pr-review-flow)
  - [Issue Triage Flow](#issue-triage-flow)
  - [Afternoon Check-In](#afternoon-check-in)
  - [Weekly Review](#weekly-review)
  - [Addressing PR Feedback](#addressing-pr-feedback)
  - [Release Prep Flow](#release-prep-flow)
  - [Sprint Review Flow](#sprint-review-flow)
- [Workspace Documents](#workspace-documents)
  - [Dual Format: Markdown + HTML](#dual-format-markdown--html)
  - [Screen Reader Accessibility](#screen-reader-accessibility)
- [Enhanced Activity Signals](#enhanced-activity-signals)
  - [Reactions & Community Sentiment](#reactions--community-sentiment)
  - [Release Awareness](#release-awareness)
  - [GitHub Discussions](#github-discussions)
  - [CI/CD Awareness](#cicd-awareness)
  - [Security & Dependencies](#security--dependencies)
  - [Project Boards](#project-boards)
- [WCAG & ARIA Cross-Referencing](#wcag--aria-cross-referencing)
- [Agent Handoffs](#agent-handoffs)
- [Tips & Tricks](#tips--tricks)
- [Troubleshooting](#troubleshooting)
- [File Reference](#file-reference)

---

## What Is This?

Let's paint the picture.

Right now, when you want to know what's happening on GitHub, you open a browser. You check your notifications. You click into an issue. You read the comments. You switch to a PR. You look at the diff. You go back to your notifications. You open another tab for CI results. Another for the project board. Another for Dependabot alerts.

That's a lot of tabs. A lot of context-switching. A lot of mental overhead just to figure out what to work on.

**These agents change all of that.**

They live right inside VS Code's Copilot Chat -- the same window where you might ask Copilot to help you write code. You type a question in plain English, and they go talk to GitHub for you. They come back with organized, prioritized, thoughtful answers. And when they produce something substantial -- a daily briefing, a code review, a triage dashboard -- they save it as a real file in your workspace that you can edit, annotate, and check off throughout the day.

Here's what they cover:

| What You Need | What the Agents Do for You |
|---------------|---------------------------|
| **A morning overview** | Sweep every repo you touch and build a prioritized briefing with issues, PRs, releases, CI health, security alerts, and community reactions |
| **Code review** | Pull the full diff, show before/after snapshots, assess risk, check CI results, flag security concerns, and let you leave comments right from chat |
| **Issue management** | Smart triage with priority scoring, saved searches, response templates, batch replies, and project board integration |
| **Team insights** | Velocity trends, review turnaround times, bottleneck detection, code churn hotspots, and workload balancing |
| **Release planning** | Auto-categorized release notes, readiness checklists, changelog generation, and post-release workflows |
| **Security monitoring** | Dependabot alerts, security advisories, and dependency update tracking across all your repos |
| **Accessibility tracking** | WCAG/ARIA cross-referenced change tracking across any repos you configure (VS Code by default) |
| **Everything else** | Branch cleanup, notification management, sprint reviews, repo onboarding, and 28 slash commands |

And here's the best part: **there's nothing to install beyond what you probably already have.** If GitHub Copilot is working in your VS Code, you're ready to go. No extra extensions, no CLI tools, no API keys.

---

## What's New

### v3: Your Editor Just Became Your GitHub Command Center

If you've been using an earlier version of these agents, here's everything that's new. If you're just getting started, don't worry about this section -- it's all included in the guide ahead.

**A whole new agent: Analytics & Insights**
- Team velocity, review turnaround times, issue resolution metrics
- See who's overloaded, which PRs are stuck, and which files keep changing
- Personal stats with team comparison -- see how your week stacks up
- New commands: `/team-dashboard` and `/my-stats`

**Workspace Preferences -- teach the agents about your team**
- A single file (`.github/agents/preferences.md`) that every agent reads
- Set your merge strategy, default reviewers, response templates, saved searches
- Add your team roster with expertise areas and timezones
- Configure notification priorities -- what to surface, what to mute

**Release management from start to finish**
- `/draft-release` builds release notes automatically from merged PRs
- `/release-prep` walks you through the entire release preparation checklist

**CI/CD health is now built into everything**
- Your daily briefing shows failing workflows and flaky tests
- PR reviews show which checks passed and which failed
- `/ci-status` gives you a quick health dashboard across repos

**Security monitoring across all your repos**
- Daily briefings now include Dependabot alerts and security advisories
- PR reviews flag changes to security-sensitive files
- `/security-dashboard` gives you the full picture in one view

**Multi-step workflow guides**
- `/release-prep` -- complete release preparation, step by step
- `/sprint-review` -- end-of-sprint summary with velocity and retrospective prompts
- `/onboard-repo` -- first-time scan of a new repository
- `/pr-author-checklist` -- self-review before you request reviews

**Notification management**
- `/notifications` lets you list, filter, mark as read, and unsubscribe -- all from the editor

**Branch management**
- `/manage-branches` -- list, compare, clean up stale branches, check protection rules

**Project board integration**
- Daily briefings now show sprint progress from GitHub Projects
- Issues show their project board status
- `/project-status` gives you a full board overview

**Saved searches and response templates**
- Define named searches once, use them everywhere: `@issue-tracker search critical-bugs`
- Pre-write replies for common situations: `@issue-tracker reply to #42 with template needs-info`

### Dual Output: Markdown + HTML
Every workspace document the agents create comes in **two formats**:
- **`.md`** -- for editing in VS Code, quick scanning, and checking off items
- **`.html`** -- optimized for screen readers, browser viewing, and sharing with your team

The HTML versions aren't an afterthought. They have skip links, ARIA landmarks, proper heading hierarchy, accessible tables, interactive checklists, and automatic light/dark mode support.

### Screen Reader Optimized Documents
All generated HTML follows strict accessibility patterns:
- Skip link as the first focusable element
- Landmark roles for every section
- Descriptive link text (never bare URLs or "click here")
- Tables with captions, header scopes, and row headers
- Status communicated through text labels, not just emoji or color
- Interactive checkboxes with proper labels
- `prefers-reduced-motion` and `prefers-color-scheme` media queries

### Reactions & Community Sentiment
Every issue and PR now includes reaction data -- thumbs up, hearts, rockets, and more. Items with 5+ positive reactions are flagged as community favorites, helping you prioritize what people actually care about.

### Release Awareness
PRs and issues now include release context -- which milestone they belong to, which release they shipped in, and whether they're still unreleased. Release-bound items get a priority boost in triage.

### GitHub Discussions
Agents now monitor GitHub Discussions alongside issues and PRs -- discussions you're part of, discussions linked to your issues, and high-activity threads that might need your attention.

### WCAG & ARIA Cross-Referencing
The accessibility tracker now maps every fix to the specific WCAG success criteria it addresses, identifies the ARIA design patterns involved, and notes which assistive technologies benefit.

### Full GitHub Interaction
You can now do everything from Copilot Chat -- PR comments (general, single-line, multi-line, code suggestions), issue replies, reactions, issue creation, PR merging, label management, and more. Nothing requires opening a browser.

### Configurable Accessibility Repos
Track accessibility changes in any repo, not just VS Code. Point the tracker at your own projects with custom label filters.

---

## Quick Start

If you want to see the whole system come alive in about two minutes, here's how.

1. **Open Copilot Chat** -- press `Ctrl+Shift+I` (or `Cmd+Shift+I` on Mac)
2. **Type this and press Enter:**
   ```
   @daily-briefing morning briefing
   ```
3. **Wait about 30 seconds.** The agent is reaching out across all your repos -- collecting issues, PRs, releases, CI status, security alerts, discussions, and community reactions. It's scoring everything by urgency and assembling it into a document.
4. **Open the file it created:**
   - `.github/reviews/briefings/briefing-{today's date}.md` -- a markdown file you can edit right in VS Code
   - `.github/reviews/briefings/briefing-{today's date}.html` -- an HTML file you can open in your browser (with full screen reader support)

That's it. You now have a prioritized picture of your entire GitHub world. The rest of this guide shows you everything else the agents can do -- and there's a lot.

> **Want a gentler introduction?** The [Getting Started guide](GETTING-STARTED.md) walks you through setup and your first few commands step by step, with no assumptions about what you already know.

---

## Setup & Prerequisites

Good news: if Copilot Chat is already working in your VS Code, you're probably done. Let's just make sure everything is in place.

### Requirements

| What You Need | How to Check |
|---------------|-------------|
| VS Code (or VS Code Insiders) | If you're reading this file in VS Code, you're good |
| GitHub Copilot extension | `Ctrl+Shift+X` --> search "GitHub Copilot" --> should say "Installed" |
| GitHub Copilot Chat extension | Same search --> "GitHub Copilot Chat" --> should say "Installed" |
| Signed in to GitHub | Click the Accounts icon (bottom-left of VS Code) --> should show your GitHub username |
| Agent files in `.github/agents/` | This repo already has them -- that's where this guide lives |
| Prompt files in `.github/prompts/` | Also already here |

### First-Time Setup

If anything above isn't checked off yet:

1. **Sign in to GitHub in VS Code:**
   - Press `Ctrl+Shift+P` --> type "GitHub: Sign In" --> follow the browser auth flow
   - Or click the Accounts icon in the bottom-left corner --> Sign in with GitHub

2. **Verify everything works:**
   - Open Copilot Chat (`Ctrl+Shift+I`)
   - Type: `@issue-tracker how many open issues do I have?`
   - If it responds with a number (even zero), you're all set

3. **If the agents don't appear in chat:**
   - Make sure the `.github/agents/` folder is in your currently open workspace
   - Try reloading VS Code: `Ctrl+Shift+P` --> "Developer: Reload Window"

> **Need more help with setup?** The [Getting Started guide](GETTING-STARTED.md) has a detailed walkthrough with screenshots and troubleshooting for every step.

---

## The Agents

You have five agents, each with its own specialty. You talk to them by typing `@agent-name` in Copilot Chat, followed by what you need. They understand plain English -- no special syntax required.

Let's meet each one.

### Daily Briefing

Think of this agent as your morning assistant. You sit down, you ask for a briefing, and it sweeps across every repo you're involved with. It checks your issues, your PRs, recent releases, CI health, security alerts, accessibility changes, GitHub Discussions, and community reactions. Then it scores everything by urgency and builds you a single, organized document.

**The result?** You know exactly what needs your attention, what can wait, and what happened while you were away. No clicking through tabs, no scrolling through notification emails.

**When to reach for it:**
- Start of your day -- "What happened overnight?"
- After a break -- "What changed since this morning?"
- End of the week -- "Give me a weekly summary"

**Here are some ways to talk to it:**

```
@daily-briefing morning briefing
@daily-briefing what changed since this morning
@daily-briefing weekly report
@daily-briefing just PRs
@daily-briefing just issues for microsoft/vscode
```

**What you get back:**
- A markdown file at `.github/reviews/briefings/briefing-YYYY-MM-DD.md`
- An HTML file at `.github/reviews/briefings/briefing-YYYY-MM-DD.html`
- Sections for: Needs Action, Releases & Deployments, Active Discussions, Monitor, Accessibility Updates, Recently Completed, Dashboard, and Guidance
- Every item is priority-scored -- the most urgent things appear first
- Community reactions and sentiment are included so you can see what people care about
- Action items have checkboxes you can tick off throughout the day
- Run it again later and it updates the same document with NEW markers instead of creating a duplicate

**Here's a quick reference for how it responds to different requests:**

| What You Say | What Happens |
|-------------|-------------|
| "morning briefing" | Full briefing covering the last 24 hours, saved as both markdown and HTML |
| "afternoon update" | Updates today's existing briefing with anything new |
| "weekly" | Extended report with reflection prompts, patterns, and community pulse |
| "just PRs" | Only PR data -- no issues or accessibility updates |
| "quick" | A short summary in chat, no document saved |

---

### Issue Tracker

This is your go-to agent for anything issue-related. It doesn't just list your issues -- it thinks about them. It scores them by urgency, flags community favorites (the ones with lots of thumbs-up reactions), links related PRs, surfaces discussions you might be missing, and checks what's tied to upcoming releases.

But it also does things. You can reply to issues, create new ones, close stale ones, add labels, assign people, set milestones, and even batch-respond to questions -- all from the chat window.

**When to reach for it:**
- "What issues need my attention?"
- "Show me the full story on this specific issue"
- "Help me triage my backlog"
- "Reply to this issue for me"
- "Create a new bug report"
- "Close this as completed"

**Here are some ways to talk to it:**

```
@issue-tracker show my open issues
@issue-tracker triage everything assigned to me
@issue-tracker deep dive into microsoft/vscode#12345
@issue-tracker reply to owner/repo#42
@issue-tracker reply to Alice's comment on #42
@issue-tracker create a bug report for login timeout in owner/repo
@issue-tracker thumbs up owner/repo#42
@issue-tracker close owner/repo#42 as completed
@issue-tracker add bug label to #42
@issue-tracker assign @alice to #42
@issue-tracker set milestone v2.0 on #42
@issue-tracker transfer #42 to owner/other-repo
```

**Everything it can do:**
- **Smart search** that understands natural language dates ("last week", "since Monday")
- **Priority scoring** that weighs reactions, release deadlines, and discussion activity
- **Auto-recovery** -- if a search returns nothing, it automatically broadens and tries again
- **Dual-format documents** for individual issues and triage dashboards
- **Full comment system** -- new comments, replies to specific existing comments, batch replies
- **Issue creation** with smart templates for bugs, features, tasks, and questions
- **Reactions** -- add emoji reactions to issues and comments using natural language
- **Issue management** -- edit, label, assign, close/reopen, lock/unlock, transfer, set milestones
- **Saved searches** -- define named filters in your preferences and use them with one command
- **Response templates** -- pre-written replies for common situations, posted with one command
- **Project board awareness** -- shows which column an issue is in on your project board
- **Community pulse** -- reactions and sentiment for every issue
- **Release awareness** -- flags issues tied to upcoming releases
- **Discussion linking** -- surfaces related GitHub Discussions
- **Cross-referencing** -- automatically finds linked PRs, discussions, and mentions

**The attention signals it shows you:**

| Signal | What It Means |
|--------|--------------|
| Action needed | Someone @mentioned you and you haven't responded yet |
| New activity | New comments since the last time you looked |
| Popular | 5+ positive reactions from the community -- people care about this one |
| Release-bound | This issue is in an upcoming release milestone |
| Discussion | There's a related GitHub Discussion with more context |
| Quiet | No recent activity on this issue |
| Stale | No activity for 30+ days |
| Linked PR | Someone has submitted a pull request that addresses this issue |
| High priority | Has a priority or critical label |

---

### PR Review

This is your code review companion. When you point it at a pull request, it pulls the complete picture: the full diff, every comment thread, which CI checks passed or failed, whether any security-sensitive files were changed, what release milestone the PR belongs to, and community reactions.

Then it builds a structured review document with risk assessment, before/after code snapshots, and a checklist you can work through systematically. When you're ready, you can leave comments -- single-line, multi-line, or even code suggestions that the PR author can apply with one click. And when you're done reviewing, you can approve, request changes, or merge -- all from chat.

**When to reach for it:**
- "Review this PR for me"
- "Show me PRs waiting for my review"
- "Leave a comment on line 42"
- "Explain what this code does"
- "Merge this PR"

**Here are some ways to talk to it:**

```
@pr-review review microsoft/vscode#54321
@pr-review show PRs waiting for my review
@pr-review my open PRs -- which are ready to merge?
@pr-review comment on owner/repo#15
@pr-review comment on line 42 of auth.ts in PR #15
@pr-review comment on lines 40-60 of auth.ts in PR #15
@pr-review suggest a fix for line 42 of auth.ts in PR #15
@pr-review reply to @alice's comment on PR #15
@pr-review explain lines 40-60 in auth.ts on PR #15
@pr-review explain the handleAuth function in PR #15
@pr-review what changed in utils.ts in PR #15
@pr-review merge owner/repo#15
@pr-review request review from @alice on PR #15
@pr-review add bug label to PR #15
@pr-review thumbs up PR owner/repo#15
@pr-review approve owner/repo#15
```

**Everything it can do:**
- **Full asset pull in one sweep** -- metadata, diff, files, comments, commits, reactions
- **File classification** -- Feature / Bug Fix / Refactor / Tests / Config / Docs
- **Risk assessment** per file -- High / Medium / Low with explanations
- **Before/after snapshots** -- side-by-side code comparison for changed files
- **Dual-format review documents** with checklists you can work through
- **Full commenting system** -- general comments, single-line, multi-line range, code suggestion blocks, reply to threads, batch comments
- **Code understanding** -- explain specific lines, functions, or file changes in plain language
- **Reactions** -- add emoji reactions to PRs and individual comments
- **PR management** -- merge (squash/rebase/merge commit), edit title/description, labels, request/dismiss reviewers, draft/ready toggle, close/reopen
- **CI check results** -- which checks passed, which failed, with links to logs
- **Security awareness** -- flags when auth, crypto, or permissions files are modified
- **Release context** -- knows if the PR is release-bound and adjusts advice accordingly
- **Accessibility checklist** -- dedicated section for UI change reviews
- **Community sentiment** -- reactions on the PR and on individual comments

**What's in a review document:**
- Overview table with PR metadata, reactions, and release context
- Changed files summary with risk levels
- File-by-file analysis with before/after code, diffs, and collapsible sections
- Developer discussion thread with reactions
- Related GitHub Discussions
- Commit story (chronological commit messages)
- Review checklist (correctness, security, performance, architecture, testing, docs, accessibility)
- Verdict and recommendations with release context and community sentiment
- A "My Notes" section for your own annotations

---

### Analytics & Insights

This agent is about understanding your team's patterns. Not in a surveillance way -- in a "let's make sure nobody's drowning and our process is healthy" way.

It tracks things like how long PRs sit before someone reviews them, who's carrying the heaviest review load, which files keep changing (and might need a refactor), and whether your team's velocity is trending up or down. When it spots something off -- a teammate with 8 open review requests, a PR that's been waiting 12 days -- it names it and suggests what to do about it.

**When to reach for it:**
- "How's the team doing this sprint?"
- "What's my review turnaround time?"
- "Who's overloaded right now?"
- "Which files change the most?"

**Here are some ways to talk to it:**

```
@analytics team dashboard
@analytics my stats this month
@analytics review turnaround for owner/repo
@analytics bottlenecks
@analytics code hotspots in owner/repo
@analytics velocity last 4 weeks
```

**What it tracks:**
- **Review turnaround** -- time from PR open to first review, to approval, to merge
- **Issue resolution** -- time to close, comments before resolution, reopen rates
- **Contribution activity** -- PRs authored/reviewed, issues closed per person
- **Team velocity** -- throughput trends, WIP counts, cycle time, period-over-period comparison
- **Bottleneck detection** -- stuck PRs, overloaded reviewers, unresponded issues
- **Code churn** -- hotspot files, change coupling, frequently modified areas
- **Health scores** -- composite 0-100 scores for review health, issue health, velocity, and team balance
- **Load balancing** -- reviewer capacity recommendations based on your team roster
- **Anomaly detection** -- flags unusual spikes or drops in activity

**Documents it creates:** Dual-format dashboards at `.github/reviews/analytics/` with health overview, metric tables, bottleneck lists, code churn analysis, and recommendations.

---

### Accessibility Tracker

This agent monitors accessibility changes across any repositories you configure -- with VS Code (both Insiders and Stable builds) tracked by default. But it goes beyond just listing closed issues.

For every accessibility fix, it identifies the specific WCAG success criteria being addressed, the ARIA design patterns involved, the impact level, and which assistive technologies benefit. Monthly reports give you a landscape view of what's improving and what still needs work.

**When to reach for it:**
- "What accessibility changes shipped this week?"
- "Screen reader improvements in February"
- "Give me a full accessibility report for this month"
- "Track accessibility in my own repo"
- "What WCAG criteria were addressed this month?"

**Here are some ways to talk to it:**

```
@insiders-a11y-tracker what's new in accessibility
@insiders-a11y-tracker screen reader changes this month
@insiders-a11y-tracker track a11y in my-org/my-repo
@insiders-a11y-tracker WCAG coverage this month
@insiders-a11y-tracker has minimap accessibility been fixed
```

**Categories it tracks:**

| Category | Examples | WCAG Principles |
|----------|---------|-----------------|
| Screen Reader | ARIA labels, announcements, NVDA/VoiceOver/JAWS | Perceivable, Robust |
| Keyboard Navigation | Focus management, tab order, key bindings | Operable |
| Visual / Contrast | High contrast themes, forced colors, zoom/reflow | Perceivable |
| Audio / Motion | Sound cues, reduced motion settings | Perceivable, Operable |
| Cognitive | Clearer labels, better error messages | Understandable |

**What makes it special:**
- **Configurable repos** -- track any repository, not just VS Code
- **WCAG cross-referencing** -- every fix mapped to specific success criteria with conformance level
- **ARIA pattern mapping** -- identifies which WAI-ARIA design patterns are involved
- **Impact assessment** -- Critical / Major / Minor impact levels
- **Assistive tech listing** -- which screen readers and assistive technologies are affected
- **WCAG coverage analysis** -- shows which principles got the most attention this month
- **Trends and gaps** -- identifies areas that still need accessibility work

**Documents it creates:** Dual-format monthly reports at `.github/reviews/accessibility/a11y-report-YYYY-MM.md` and `.html` with categorized changes, WCAG coverage tables, ARIA pattern summaries, trend analysis, and useful links.

---

## Workspace Preferences

Here's something that makes the whole system feel personal: a single configuration file that every agent reads.

Edit `.github/agents/preferences.md` and the agents learn about your workflow -- which repos to scan, who reviews what, how you prefer to merge, what labels matter, and when your working day starts. You set it up once, and every agent inherits that knowledge from then on.

| What You Can Configure | What It Controls | Which Agents Use It |
|----------------------|-----------------|-------------------|
| `repos` | **Repository discovery and scope** -- which repos to scan, per-repo tracking granularity (issues, PRs, discussions, releases, security, CI), include/exclude lists, label and path filters | All agents |
| `accessibility_tracking` | Which repos to track for a11y changes, per-repo labels and channels, WCAG/ARIA toggles | A11y Tracker, Daily Briefing |
| `merge` | Default merge strategy, whether to delete branches after merge | PR Review, `/merge-pr` |
| `reviewers` | Default and path-based reviewer suggestions | PR Review, `/pr-author-checklist` |
| `labels` | Your priority and type label taxonomy | Issue Tracker, triage |
| `templates` | Canned reply templates for common situations | Issue Tracker, `/issue-reply` |
| `searches` | Named search filters you can run by name | Issue Tracker, all agents |
| `notifications` | Which repos/labels/events to prioritize or mute | Daily Briefing, `/notifications` |
| `team` | Team roster with expertise areas and timezones | Analytics, reviewer suggestions |
| `schedule` | Working hours and timezone | Daily Briefing, time-aware features |
| `ci` | CI/CD monitoring thresholds | Daily Briefing, `/ci-status` |
| `security` | Security alert severity levels to surface | Daily Briefing, `/security-dashboard` |
| `projects` | Active GitHub Projects to track | Daily Briefing, Issue Tracker, `/project-status` |

**The most important setting: `repos.discovery`**

By default, agents search ALL repos you have access to. You can narrow this:

| Mode | What It Scans |
|------|---------------|
| `all` (default) | Every repo you can access -- public, private, org member |
| `starred` | Only repos you have starred |
| `owned` | Only repos you own |
| `configured` | Only repos explicitly listed in `repos.include` |
| `workspace` | Only the repo in the current VS Code workspace |

You can also set **per-repo overrides** to control exactly what gets tracked in each repo -- issues only, PRs only, specific labels, specific file paths, and more. See `preferences.example.md` for the full reference.

**How to get started:**
1. Open `.github/agents/preferences.md` in your editor
2. You'll see sections with YAML code blocks and example values
3. Customize the values that matter to your team -- you don't have to fill everything in
4. The agents read this file at the start of each session, so changes take effect next time you talk to them

**Two features worth highlighting:**

**Saved Searches** let you define named filters and use them by name:
```
@issue-tracker search critical-bugs
@issue-tracker search my-stale-prs
@issue-tracker search needs-triage
```

**Response Templates** let you pre-write replies for common situations and post them with one command:
```
@issue-tracker reply to #42 with template needs-info
@issue-tracker reply to #42 with template duplicate ref:#30
@issue-tracker reply to #42 with template stale-closing
```

> **Don't feel pressured to set this up right away.** The agents work perfectly fine with their defaults. When you're ready to customize -- maybe after a week of use, when you notice patterns -- come back to this section.

---

## The Prompt Commands

Prompt commands are shortcuts. Instead of typing a full sentence to an agent, you type `/` followed by a command name, and the right agent fires up with the right tools already loaded.

**To use one:** Open Copilot Chat, type `/`, and you'll see all available commands in a dropdown. Pick one, add any extra details (like a repo name or issue number), and press Enter.

### All 28 Commands

| Command | Agent | What It Does |
|---------|-------|-------------|
| `/my-issues` | Issue Tracker | Your open issues, priority-sorted with reactions and release context |
| `/my-prs` | PR Review | Your open PRs with review status, CI health, and release status |
| `/review-pr` | PR Review | Full code review with dual-format documents |
| `/pr-report` | PR Review | Save or update a PR review as workspace documents |
| `/pr-comment` | PR Review | Add line-specific comments with priority levels |
| `/explain-code` | PR Review | Understand specific lines, functions, or blocks in a PR diff |
| `/merge-pr` | PR Review | Merge a PR with readiness checks and strategy selection |
| `/pr-author-checklist` | PR Review | Self-review checklist before requesting reviews |
| `/issue-reply` | Issue Tracker | Draft and post a context-aware reply |
| `/create-issue` | Issue Tracker | Create a well-structured issue with smart templates |
| `/manage-issue` | Issue Tracker | Edit, label, assign, close, reopen, lock, transfer, milestone |
| `/react` | Issue Tracker | Add emoji reactions to issues, PRs, and comments |
| `/triage` | Issue Tracker | Prioritized triage dashboard saved as workspace documents |
| `/daily-briefing` | Daily Briefing | Generate your daily briefing in both formats |
| `/a11y-update` | A11y Tracker | Accessibility updates with WCAG cross-references |
| `/refine-issue` | Issue Tracker | Add acceptance criteria with community context |
| `/address-comments` | PR Review | Systematically work through review comments |
| `/team-dashboard` | Analytics | Team activity, review load, bottlenecks, and load balancing |
| `/my-stats` | Analytics | Your personal metrics with team comparison |
| `/draft-release` | Daily Briefing | Draft release notes from merged PRs, auto-categorized |
| `/ci-status` | Daily Briefing | CI/CD health dashboard -- failures, flaky tests, long jobs |
| `/security-dashboard` | Daily Briefing | Dependabot alerts, advisories, dependency update PRs |
| `/release-prep` | Daily Briefing | Complete release preparation workflow with readiness checklist |
| `/sprint-review` | Analytics | End-of-sprint summary with velocity and retrospective prompts |
| `/onboard-repo` | Daily Briefing | First-time repo scan with health check and quick wins |
| `/notifications` | Daily Briefing | List, filter, and manage your GitHub notifications |
| `/manage-branches` | PR Review | List, compare, clean up, and inspect branch protection |
| `/project-status` | Issue Tracker | GitHub Projects overview with column metrics and stale items |

**A few examples to show the pattern:**
```
/review-pr microsoft/vscode#54321
/my-issues last week
/triage frontend-app
/a11y-update screen reader
/daily-briefing morning
/explain-code lines 40-60 in auth.ts on PR #15
/merge-pr owner/repo#15
/create-issue bug: login timeout after 30 seconds in owner/repo
/manage-issue close owner/repo#42 as completed
/react thumbs up owner/repo#42
```

---

## Never Leave Your Editor

This is the heart of the whole system. Every action you'd normally do on github.com -- leaving a comment, merging a PR, closing an issue, reacting to someone's work, checking CI results, managing notifications -- can happen right here in the chat window.

Let's walk through each one.

### PR Commenting & Code Review

You can leave comments at every level -- from general PR discussion down to specific line ranges with code suggestions.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **Leave a general comment** | `@pr-review comment on owner/repo#15: "Looks great overall, just a few nits"` |
| **Comment on a specific line** | `@pr-review comment on line 42 of auth.ts in PR #15: "This needs null checking"` |
| **Comment on a range of lines** | `@pr-review comment on lines 40-60 of auth.ts in PR #15: "This block should be extracted"` |
| **Suggest a code fix** | `@pr-review suggest a fix for line 42 of auth.ts in PR #15` -- the PR author gets a one-click "Apply suggestion" button |
| **Reply to a comment thread** | `@pr-review reply to @alice's comment on PR #15: "Good point, I'll fix that"` |
| **Post all your notes as comments** | After generating a review document and adding notes, the agent can post them all at once |
| **Submit a formal review** | `@pr-review approve owner/repo#15` or `@pr-review request changes on #15` |

**About code suggestions:** These use GitHub's built-in `suggestion` syntax, so the PR author sees an "Apply suggestion" button right on the comment. One click and your fix is committed. No back-and-forth needed.

### Code Understanding

Before you critique code, it helps to understand it. The agent can explain any part of a PR diff in plain language.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **Understand specific lines** | `/explain-code lines 40-60 in auth.ts on PR #15` |
| **Understand a function** | `/explain-code the handleAuth function in PR #15` |
| **Understand what changed in a file** | `/explain-code what changed in utils.ts in PR #15` |
| **Compare before and after** | `@pr-review compare the old and new handleAuth in PR #15` |

After explaining, the agent offers to comment on those lines, suggest a change, or show more context. It's a natural flow: understand first, then respond.

### Issue Interactions

The full comment system -- create, reply, and interact with issues without opening a browser.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **Comment on an issue** | `/issue-reply owner/repo#42` or `@issue-tracker comment on #42` |
| **Reply to a specific person's comment** | `@issue-tracker reply to Alice's comment on #42: "Thanks, I'll investigate"` |
| **Reply to a numbered comment** | The agent numbers all comments -- just pick the one you want to reply to |
| **Reply to several issues at once** | `@issue-tracker reply to all pending questions on my issues` |
| **Create a new issue** | `/create-issue bug: login timeout after 30 seconds in owner/repo` |
| **Create from a repo template** | The agent auto-detects your repo's issue templates and pre-fills them |

**Smart issue creation** picks up on your description:
- Start with "bug:" and it uses a bug template with Steps to Reproduce, Expected/Actual Behavior
- Start with "feature:" and it uses a feature template with Motivation, Proposed Solution, Alternatives
- Start with "task:" and it uses a task template with Acceptance Criteria checklist

### Reactions

Reactions are the lightest way to participate on GitHub. A thumbs up says "I see this and I agree." A rocket says "nice work." A heart says "I appreciate you." Two seconds, and you've made someone's day.

| What You Say | What GitHub Shows |
|-------------|------------------|
| "like", "agree", "thumbs up", "+1" | +1 |
| "disagree", "thumbs down", "-1" | -1 |
| "love", "heart" | heart |
| "celebrate", "hooray", "tada" | hooray |
| "ship it", "rocket", "launch" | rocket |
| "looking", "eyes", "watching" | eyes |
| "funny", "laugh", "lol" | laugh |
| "confused", "huh", "what" | confused |

**Examples:**
```
/react thumbs up owner/repo#42
/react heart the latest comment on #42
/react rocket PR owner/repo#15
@issue-tracker like owner/repo#42
@pr-review rocket PR owner/repo#15
```

You can react to issue bodies, PR bodies, and individual comments. The agent shows you the current reactions before adding yours.

### PR Management

The full PR lifecycle, from requesting a review to merging.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **Merge a PR** | `/merge-pr owner/repo#15` -- checks readiness, picks strategy, confirms before merging |
| **Edit the title or description** | `@pr-review edit title of PR #15 to "Fix auth timeout"` |
| **Add or remove labels** | `@pr-review add bug label to PR #15` |
| **Request reviewers** | `@pr-review request review from @alice and @bob on PR #15` |
| **Dismiss a review** | `@pr-review dismiss @alice's review on PR #15` |
| **Convert to draft** | `@pr-review convert PR #15 to draft` |
| **Mark as ready** | `@pr-review mark PR #15 as ready for review` |
| **Close or reopen** | `@pr-review close PR #15` or `@pr-review reopen PR #15` |

**How merging works** (the `/merge-pr` flow):
1. The agent checks readiness -- approvals, CI status, merge conflicts, branch protection
2. If something is blocking the merge, it tells you exactly what and offers to help
3. If everything is green, it shows your merge strategy options: Squash and merge, Create merge commit, or Rebase and merge
4. It shows the merge commit message and lets you customize it
5. You confirm (this is the point of no return)
6. After merging, it offers to delete the source branch, close linked issues, and update your briefing

### Issue Management

Full issue administration -- everything you'd do on the issue page.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **Edit title or body** | `/manage-issue edit title of owner/repo#42` |
| **Add or remove labels** | `/manage-issue add bug label to #42` |
| **Assign or unassign** | `/manage-issue assign @alice to #42` |
| **Set a milestone** | `/manage-issue set milestone v2.0 on #42` |
| **Close** | `/manage-issue close owner/repo#42 as completed` (or "as not planned") |
| **Reopen** | `/manage-issue reopen owner/repo#42` |
| **Lock** | `/manage-issue lock #42 as resolved` (reasons: off-topic, too heated, resolved, spam) |
| **Unlock** | `/manage-issue unlock #42` |
| **Transfer to another repo** | `/manage-issue transfer #42 to owner/other-repo` |

> **A note about safety:** Every action that changes state -- closing, reopening, locking, transferring, merging -- requires your explicit confirmation. The agent always shows you exactly what will happen before doing it. You're always in control.

### Branch Management

Keep your branches tidy without leaving the editor.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **List all branches** | `/manage-branches list owner/repo` |
| **Find stale branches** | `/manage-branches stale` -- shows branches with no activity in 30+ days |
| **Compare two branches** | `/manage-branches compare main feature/auth` -- ahead/behind analysis |
| **Clean up merged branches** | `/manage-branches cleanup` -- safely delete branches already merged into the default branch |
| **Check protection rules** | `/manage-branches protection` -- what's protected and how |

**How cleanup works:**
1. The agent lists all branches that have been merged into the default branch
2. It excludes any protected branches
3. It shows each one with its last activity date
4. You confirm before anything gets deleted -- no surprises

### Notifications

Your GitHub notifications, managed from the editor.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **See unread notifications** | `/notifications` -- grouped by repo and type |
| **Filter by type** | `/notifications mentions` or `/notifications review requests` |
| **Mark one as read** | `/notifications mark #3 as read` |
| **Mark everything as read** | `/notifications mark all read` |
| **Unsubscribe from a thread** | `/notifications unsubscribe from #3` |

The agent applies your notification preferences from `preferences.md` -- priority repos surface first, muted repos stay hidden unless you ask for them.

### Release Management

The full release lifecycle, from planning to publishing.

| What You Want to Do | How to Do It |
|-------------------|-------------|
| **Draft release notes** | `/draft-release owner/repo v2.0.0` -- auto-categorized from merged PRs |
| **Check release readiness** | `/release-prep owner/repo v2.0.0` -- milestone status, CI health, security, and a readiness checklist |
| **Check CI health** | `/ci-status owner/repo` -- workflow status across repos |
| **Check security** | `/security-dashboard owner/repo` -- Dependabot alerts and advisories |

**How release notes are categorized:**
The agent reads the labels and titles of every merged PR since the last release and organizes them into:
- Breaking Changes (from labels or "BREAKING" in titles)
- Features (from `feature`/`enhancement` labels)
- Bug Fixes (from `bug`/`fix` labels)
- Performance, Documentation, Dependencies, Other

---

## Daily Workflows

Now let's put it all together. These are repeatable routines -- sequences of commands that flow naturally into each other. After a few days, they'll feel like second nature.

### Morning Routine

**What you're doing:** Going from "I just sat down" to "I know exactly what to focus on today."

**Time:** About 5-10 minutes.

```
Step 1: Open Copilot Chat (Ctrl+Shift+I)
Step 2: Type: @daily-briefing morning briefing
Step 3: Wait about 30 seconds for the briefing to generate
Step 4: Open the briefing file:
        - .github/reviews/briefings/briefing-{date}.md (in VS Code)
        - .github/reviews/briefings/briefing-{date}.html (in your browser)
Step 5: Read the "Needs Action" section -- these are your top priorities
Step 6: Check "Releases & Discussions" for anything time-sensitive
Step 7: Check things off throughout the day as you complete them
```

**What typically comes next:**
- See a PR that needs your review? --> `@pr-review review owner/repo#123`
- See an issue where someone's waiting on you? --> `/issue-reply owner/repo#42`
- See a release approaching? --> Prioritize the release-bound items first
- Want a deeper look at your backlog? --> `/triage`

---

### PR Review Flow

**What you're doing:** A thorough, structured code review -- the kind that catches real issues and respects the author's work.

**Time:** About 10-20 minutes, depending on the PR size.

```
Step 1:  /review-pr owner/repo#123
Step 2:  Open the review document (.md or .html)
Step 3:  Check the release context -- is this tied to an upcoming release?
Step 4:  Work through the checklist, checking off items as you verify them
Step 5:  Need to understand something? /explain-code lines 40-60 in auth.ts on PR #123
Step 6:  Add your notes in the "My Notes" section
Step 7:  Leave comments: /pr-comment owner/repo#123
         - Single-line: "comment on line 42 of auth.ts"
         - Range: "comment on lines 40-60 of auth.ts"
         - Suggestion: "suggest a fix for line 42"
Step 8:  Reply to existing threads: @pr-review reply to @alice's comment on PR #123
Step 9:  Submit your review: @pr-review approve owner/repo#123
Step 10: Ready to merge? /merge-pr owner/repo#123
```

---

### Issue Triage Flow

**What you're doing:** Taking control of your backlog instead of letting it pile up.

**Time:** About 10-15 minutes.

```
Step 1:  /triage
Step 2:  Open the triage document (markdown or HTML)
Step 3:  Look at community reactions -- popular issues might deserve a priority bump
Step 4:  Check release context -- release-bound issues have real deadlines
Step 5:  For each issue, decide: Reply / Close / Reassign / Defer
Step 6:  Check boxes in the document as you make decisions
Step 7:  Reply: /issue-reply owner/repo#42
Step 8:  Refine: /refine-issue owner/repo#42
Step 9:  Close: /manage-issue close owner/repo#42 as completed
Step 10: Reassign: /manage-issue assign @alice to #42
Step 11: Show some appreciation: /react thumbs up owner/repo#42
Step 12: Need a new issue? /create-issue feature: add dark mode in owner/repo
```

---

### Afternoon Check-In

**What you're doing:** A quick catch-up on anything that changed since the morning.

**Time:** 2-3 minutes.

```
Step 1: @daily-briefing afternoon update
Step 2: Check the NEW Update section at the top of today's briefing
Step 3: Address anything new that's urgent
```

That's it. The briefing updates in place -- no duplicate files.

---

### Weekly Review

**What you're doing:** Stepping back to see the bigger picture. What went well? What needs attention?

**Time:** About 15-20 minutes.

```
Step 1: @daily-briefing weekly report
Step 2: Review "Recently Completed" -- take a moment to appreciate what got done
Step 3: Check "Community Pulse" -- what resonated with people?
Step 4: Read "Guidance & Patterns" for workflow insights
Step 5: Think about the reflection prompts at the bottom
Step 6: Run /triage to clean up stale issues before next week
Step 7: /a11y-update for this month's accessibility changes
```

---

### Addressing PR Feedback

**What you're doing:** Working through every review comment on your PR, one by one, so nothing slips through the cracks.

**Time:** 5-15 minutes, depending on how many comments there are.

```
Step 1: /address-comments owner/repo#15
Step 2: Check release context -- is this release-bound?
Step 3: Review the organized list of comments with priority levels
Step 4: If release-bound, handle blocking comments (CRITICAL/IMPORTANT) first
Step 5: For each comment: see the context, make the fix, draft a reply
Step 6: After all changes are pushed, let the agent post reply comments
Step 7: The agent drafts a summary comment for the PR thread
```

---

### Release Prep Flow

**What you're doing:** Making sure everything is ready to ship -- no open items, no failing CI, no security surprises.

**Time:** About 15-25 minutes.

```
Step 1:  /release-prep owner/repo v2.0.0
Step 2:  Review the milestone check -- any open items that should be deferred?
Step 3:  Review open PRs -- any that need to merge before the release?
Step 4:  Check CI health on the release branch
Step 5:  Check security -- any critical Dependabot alerts?
Step 6:  Review the auto-generated release notes
Step 7:  Edit the notes if needed
Step 8:  Work through the readiness checklist
Step 9:  Create the GitHub release draft when everything looks good
Step 10: After publishing, run through the post-release checklist
```

---

### Sprint Review Flow

**What you're doing:** Turning a sprint's worth of work into a story your team can learn from.

**Time:** About 15-20 minutes.

```
Step 1:  /sprint-review for milestone "Sprint 5"
Step 2:  Review completed items -- celebrate what got done
Step 3:  Look at carryover items -- understand why they didn't finish
Step 4:  Check velocity metrics -- on track, improving, or declining?
Step 5:  Review team contributions -- is anyone overloaded or underutilized?
Step 6:  Note blockers that need systemic fixes
Step 7:  Use the retrospective prompts for team discussion
Step 8:  /team-dashboard for the broader metrics context
```

---

## Workspace Documents

Everything the agents produce -- briefings, reviews, triage dashboards, analytics reports -- gets saved as real files in your workspace. Not just chat messages that scroll away, but files you can edit, annotate, commit, and share.

### Dual Format: Markdown + HTML

Every document comes in two formats:

```
.github/
+-- reviews/
    +-- briefings/
    |   +-- briefing-2026-02-12.md        <- edit in VS Code
    |   +-- briefing-2026-02-12.html      <- open in browser / screen reader
    +-- issues/
    |   +-- vscode-12345-fix-login.md
    |   +-- vscode-12345-fix-login.html
    |   +-- triage-2026-02-12.md
    |   +-- triage-2026-02-12.html
    +-- prs/
    |   +-- vscode-pr-54321-add-auth.md
    |   +-- vscode-pr-54321-add-auth.html
    +-- accessibility/
    |   +-- a11y-report-2026-02.md
    |   +-- a11y-report-2026-02.html
    +-- analytics/
    |   +-- analytics-2026-02-12.md
    |   +-- analytics-2026-02-12.html
    |   +-- team-dashboard-2026-02-12.md
    |   +-- team-dashboard-2026-02-12.html
    |   +-- my-stats-2026-02-12.md
    |   +-- my-stats-2026-02-12.html
    |   +-- sprint-review-2026-02-12.md
    |   +-- sprint-review-2026-02-12.html
    +-- releases/
    |   +-- release-notes-v2.0.0-2026-02-12.md
    |   +-- release-notes-v2.0.0-2026-02-12.html
    |   +-- release-prep-v2.0.0-2026-02-12.md
    |   +-- release-prep-v2.0.0-2026-02-12.html
    +-- onboarding/
        +-- onboard-vscode-2026-02-12.md
        +-- onboard-vscode-2026-02-12.html
```

**When to use markdown:**
- Editing and previewing in VS Code (`Ctrl+Shift+V` for markdown preview)
- Quick scanning with familiar formatting
- Checking off items by changing `- [ ]` to `- [x]`
- Committing to your repo

**When to use HTML:**
- Screen reader navigation -- landmarks, skip links, and proper heading hierarchy
- Browser viewing with automatic light/dark mode
- Interactive checkboxes (just click them)
- Sharing with teammates who don't have VS Code open
- Printing with proper formatting

### Screen Reader Accessibility

The HTML documents aren't a token gesture. They're built screen-reader-first, and they follow strict standards throughout.

| Feature | How It's Implemented |
|---------|---------------------|
| Skip link | First focusable element on the page -- jumps straight to main content |
| Landmarks | `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>` with descriptive labels |
| Heading hierarchy | Strict h1 --> h2 --> h3, never skipping levels |
| Table accessibility | Every table has a `<caption>`, `<th scope="col/row">`, and header cells |
| Link text | Always descriptive -- "PR #123: Fix login bug", never bare URLs |
| Status indicators | Text labels alongside any emoji or color -- never color-only |
| Interactive checklists | `<input type="checkbox">` with proper `<label>` elements |
| Dark mode | Automatically respects `prefers-color-scheme` |
| Reduced motion | Respects `prefers-reduced-motion` |
| Contrast | Meets WCAG AA standards (4.5:1 minimum ratio) |
| Focus indicators | Visible 2px outline on all interactive elements |
| Table of contents | `<nav>` with links to every document section |

The markdown documents are thoughtful too:
- Item counts in section headings (e.g., "## Needs Action (3 items)")
- Text labels alongside emoji
- Collapsible `<details>` blocks for long content
- Descriptive link text throughout

### Working with Your Documents

These documents are meant to be lived in throughout the day. Here's how to get the most from them:

**Check things off as you go.** In markdown, change `- [ ]` to `- [x]`. In HTML, click the checkbox. By end of day, your briefing becomes a record of everything you accomplished.

**Take notes.** Every document ends with a "My Notes" section -- a comment block in markdown, a `<textarea>` in HTML. Use it for decisions, blockers, questions, or anything else you want to remember.

**They update, not duplicate.** Run the same agent for the same item again and it detects the existing document and adds to it -- timestamped, with NEW badges -- instead of creating a second copy.

**Share them however works for your team.** Both formats are plain files:
- Commit them so your team can see your review notes
- Add `.github/reviews/` to `.gitignore` to keep them private
- Drop the HTML file on a shared drive for browser viewing

### Gitignore Recommendation

If you'd prefer to keep review documents private (most people do), add this to your `.gitignore`:

```
# GitHub agent review documents (personal workspace)
.github/reviews/
```

---

## Enhanced Activity Signals

The agents don't just fetch raw data from GitHub -- they layer on context that helps you understand what matters. Every item comes annotated with signals about urgency, community interest, staleness, and more.

### Reactions & Community Sentiment

When an issue has 15 thumbs-up reactions, that's not vanity -- it's a prioritization signal. The agents track reactions on everything:

| What the Agent Shows | What It Means |
|---------------------|--------------|
| **Popular** | 5+ positive reactions -- the community cares about this one |
| **Controversial** | Mixed positive and negative reactions -- might need extra discussion |
| **Quiet** | 0-1 reactions -- standard priority |

You'll see reactions:
- In issue and PR tables as a "Reactions" column
- On individual comments in deep dives
- In HTML documents as styled `<span>` elements with `aria-label` descriptions
- In the daily briefing's "Community Pulse" section

### Release Awareness

The agents track releases across your active repos and annotate everything with release context:

| Signal | What It Means |
|--------|--------------|
| **Next release** | This item is in the milestone for the next scheduled release |
| **Released** | This fix or feature already shipped in a specific version |
| **Unreleased** | Merged but not yet included in any release |

You'll see release context:
- In PR reviews -- "This PR targets the v2.0 release milestone (deadline: Feb 20)"
- In triage dashboards -- release-bound issues get a priority boost
- In daily briefings -- a dedicated "Releases & Deployments" section
- In the address-comments workflow -- helping you distinguish blocking from deferrable feedback

### GitHub Discussions

The agents monitor GitHub Discussions alongside issues and PRs:

| What's Tracked | Where You'll See It |
|---------------|-------------------|
| Discussions mentioning you | Daily briefing "Active Discussions" section |
| Discussions linked to your issues | Issue deep dives and triage dashboards |
| Discussions linked to PRs | PR review documents |
| High-activity discussions (10+ comments) | Flagged in daily briefing patterns |
| Discussions converted to issues | Cross-referenced in issue documents |

### CI/CD Awareness

The agents surface GitHub Actions workflow status so you don't have to go looking for it:

| What's Tracked | Where You'll See It |
|---------------|-------------------|
| Failing workflows | Daily briefing "CI/CD Health" section |
| Check run results | PR reviews -- inline pass/fail with links to logs |
| Flaky tests | Daily briefing and `/ci-status` dashboard |
| Long-running jobs | Flagged when exceeding your configured threshold |
| Your PRs with failing CI | Daily briefing "Needs Action" section |

You can configure monitoring in `preferences.md` -- set which workflows to watch, flaky test thresholds, and how long is too long for a job.

### Security & Dependencies

The agents keep an eye on security-related activity across your repos:

| What's Tracked | Where You'll See It |
|---------------|-------------------|
| Dependabot alerts (critical/high) | Daily briefing "Security Alerts" section |
| Security advisories | `/security-dashboard` |
| Dependency update PRs | Daily briefing, `/security-dashboard` |
| Security-sensitive file changes | PR reviews -- flagged when auth, crypto, or permissions files are modified |

Configure in `preferences.md` -- set which severity levels to surface and which repos to monitor.

### Project Boards

The agents integrate with GitHub Projects to show your sprint and board context:

| What's Tracked | Where You'll See It |
|---------------|-------------------|
| Sprint/iteration items | Daily briefing "Project Board" section |
| Item column status | Issue tracker -- "Board" column in tables |
| Stale items (7+ days in same column) | Daily briefing, `/project-status` |
| Blocked items | Daily briefing, `/project-status` |
| Sprint progress (% complete) | `/project-status`, `/sprint-review` |

Configure in `preferences.md` -- set active project numbers and whether to include project data in briefings.

---

## WCAG & ARIA Cross-Referencing

The accessibility tracker doesn't just tell you what changed -- it tells you *why it matters* and *who it helps*.

### WCAG Coverage
Every accessibility fix is mapped to the specific WCAG 2.1/2.2 success criteria it addresses:
- **Principle** -- Perceivable, Operable, Understandable, or Robust
- **Criterion** -- the specific success criterion number and name
- **Level** -- A, AA, or AAA conformance level
- Monthly reports include a "WCAG Coverage" section showing which criteria got attention

### ARIA Design Patterns
When a fix involves ARIA, the tracker identifies the relevant WAI-ARIA Authoring Practices pattern:
- Pattern name (e.g., Dialog, Combobox, Tree)
- Key requirements of the pattern
- Monthly reports include an "ARIA Patterns Improved" summary

### Impact Assessment
Each fix includes:
- **Impact level** -- Critical (blocks access entirely), Major (significantly degrades the experience), Minor (an inconvenience)
- **Assistive technologies affected** -- NVDA, JAWS, VoiceOver, TalkBack, and others

### Configurable Repos
You can track accessibility in any repository. VS Code is tracked by default, but you can add any repo:
```
@insiders-a11y-tracker track a11y in my-org/my-repo
@insiders-a11y-tracker track a11y in my-org/my-repo with label:a11y
```

Or configure repos permanently in `preferences.md`:
```yaml
accessibility_tracking:
  repos:
    - repo: my-org/my-app
      labels: ["a11y", "accessibility"]
```

---

## Agent Handoffs

One of the nicest things about this system is that the agents talk to each other. When one agent finishes its work, it offers to hand you off to another agent that might be helpful next -- with full context carried over.

For example: you finish reviewing a PR, and the agent offers to check its linked issues. Or you triage an issue, and it offers to review the PR that fixes it. Or your morning briefing highlights a priority item, and it offers to deep dive into it.

These handoffs appear as clickable buttons below the agent's response in chat. One click and you're in the next agent's hands.

### How the Agents Connect

```
Daily Briefing
+-- --> Issue Tracker (deep dive, reply, create, manage issues)
+-- --> PR Review (review, comment, explain, merge PRs)
+-- --> A11y Tracker (more detail on accessibility changes)
+-- --> Analytics (team metrics and insights)

Issue Tracker
+-- --> PR Review (review linked PRs, comment, merge)
+-- --> Daily Briefing (include issues in next briefing)

PR Review
+-- --> Issue Tracker (check linked issues, create issues, close resolved)
+-- --> Daily Briefing (include PR review in briefing)

Analytics
+-- --> Daily Briefing (include analytics in briefing)
+-- --> PR Review (review bottleneck PRs)
+-- --> Issue Tracker (explore stuck issues)

A11y Tracker
+-- --> Daily Briefing (include a11y updates in briefing)
```

---

## Tips & Tricks

Here are some things that will make the agents feel even more natural to use. You'll discover your own favorites over time -- these are just a starting point.

### 1. Talk Like a Human
You don't need exact syntax. The agents understand what you mean:
- "Show me my stuff" --> lists your issues
- "What PRs are waiting for me" --> lists PRs needing your review
- "Anything urgent?" --> prioritized list of action items
- "What's popular?" --> items with high community reactions
- "Release status" --> PRs and issues tied to upcoming releases

### 2. You Probably Don't Need to Type the Repo Name
If you're in a workspace with a git repo, the agents already know which repo you mean. Just ask `@issue-tracker show my issues` -- no need for `owner/repo`.

### 3. Dates Are Flexible
"Last week", "since Monday", "this month", "between Jan 1 and Feb 15" -- the agents understand all of these. No special date format required.

### 4. The HTML Files Are Worth Opening
Especially if you use a screen reader, but honestly for anyone. They have skip links, landmark navigation, proper heading hierarchy, accessible tables, and interactive checklists. Navigate by heading and every section is one keypress away.

### 5. Track Accessibility in Any Repo
Not just VS Code:
```
@insiders-a11y-tracker track a11y in my-org/my-repo with label:accessible
```

### 6. Release-Aware Reviews Save Time
When a PR is tied to a release milestone, the review document separates "this blocks the release" from "nice to have." That way you don't hold up a ship date debating variable names.

### 7. Community Reactions Are Prioritization Data
Five thumbs-up on a feature request means real people want it. The agents surface this so you can make informed decisions about what to work on next.

### 8. Run Briefings More Than Once a Day
The daily briefing isn't limited to once per day. Run it again at 2pm and it *updates* the existing document -- marking new items with NEW badges instead of creating a duplicate.

### 9. Bulk Operations Work
The agents handle batch requests gracefully:
- "Reply to all issues where someone asked me a question"
- "Review all PRs waiting for me, smallest first"
- "Close all my stale issues labeled 'wontfix'"

### 10. Code Suggestions Are Powerful
```
@pr-review suggest a fix for line 42 of auth.ts in PR #15
```
The PR author gets an "Apply suggestion" button. One click and your fix is committed. No back-and-forth, no "I made the change, please re-review."

### 11. Understand Before You Critique
Use `/explain-code` before `/pr-comment`. First understand what the code does and why it's there. Then your comment has context, and the author knows you read their work thoughtfully.

### 12. A Quick Reaction Goes a Long Way
`/react` takes two seconds. A rocket on someone's merged PR. A heart on a thoughtful comment. It costs you nothing and it means something to the person who receives it.

### 13. Set Up Preferences Once, Benefit Forever
Edit `preferences.md` once. Every agent inherits your merge strategy, reviewer mapping, saved searches, response templates, team roster, and notification preferences. It compounds over time.

### 14. Name Your Searches
Define filters once in preferences, use them anywhere:
```
@issue-tracker search critical-bugs
@issue-tracker search needs-triage
```

### 15. Response Templates Kill Repetition
Instead of typing "Thanks for reporting! Could you provide steps to reproduce..." for the hundredth time:
```
@issue-tracker reply to #42 with template needs-info
```
Consistent, professional, and done in seconds.

### 16. You'll Know When CI Breaks
`/ci-status` gives you the picture across all repos. Or just let the daily briefing tell you -- failing workflows show up automatically in the CI/CD Health section.

### 17. Security Monitoring Is Built In
`/security-dashboard` pulls every Dependabot alert, every advisory, every pending dependency update into one view. Across all your repos. No more visiting each repo's security tab individually.

### 18. Sprint Reviews Write Themselves
`/sprint-review` generates a complete summary with velocity metrics, carryover analysis, and retrospective prompts. Walk into your team standup prepared.

### 19. Onboard to New Repos in Minutes
Joining a new project? `/onboard-repo owner/repo` scans everything -- issues, PRs, releases, CI health, CODEOWNERS, security alerts -- and tells you what needs attention first.

### 20. Self-Review Before Requesting Reviews
`/pr-author-checklist` catches the things that would embarrass you -- leftover debug logging, missing tests, a vague PR title, hardcoded secrets. Run it before anyone else sees your PR.

### 21. Ask About Specific WCAG Criteria
```
@insiders-a11y-tracker what fixes addressed WCAG 2.4.3 this month
@insiders-a11y-tracker keyboard navigation improvements
```

---

## Troubleshooting

If something isn't working, it's almost always one of these five things. Let's walk through each one.

### "I don't see the agents in chat autocomplete"

**What's happening:** The agents need to be in the `.github/agents/` folder of your currently open workspace, and VS Code needs to discover them.

**How to fix it:**
1. Make sure you opened the *folder* that contains `.github/agents/` -- not just a single file
2. Check that the agent files end in `.agent.md`
3. Try reloading VS Code: `Ctrl+Shift+P` --> "Developer: Reload Window"

---

### "The agent says it can't authenticate"

**What's happening:** You're not signed in to GitHub in VS Code, or your session expired.

**How to fix it:**
1. Press `Ctrl+Shift+P` --> type "GitHub: Sign In"
2. Follow the browser authentication flow
3. Come back to VS Code and try again

---

### "The agent returns 0 results"

**What's happening:** The search scope might be too narrow, or you might not have any matching items right now.

**What agents do automatically:** They broaden the search and tell you what they tried.

**If you want to fix it manually:** Be more explicit -- `@issue-tracker show all my open issues with no date filter`

---

### "Rate limited / 403 error"

**What's happening:** You've hit GitHub's API rate limit (5,000 requests per hour).

**How to fix it:** Wait a few minutes and try again. The agent tells you when the rate limit resets.

---

### "The HTML file looks broken"

**What's happening:** It was probably opened in VS Code's text editor instead of a browser.

**How to fix it:** Right-click the `.html` file --> "Open with" --> your browser. Or use VS Code's built-in Simple Browser (`Ctrl+Shift+P` --> "Simple Browser: Open").

---

### "Prompt commands don't appear when I type `/`"

**How to fix it:**
1. Verify files exist in `.github/prompts/` and end in `.prompt.md`
2. Check that each file has valid YAML frontmatter
3. Reload VS Code: `Ctrl+Shift+P` --> "Developer: Reload Window"

---

## File Reference

Here's every file in the system, what it does, and where it lives. Use this as a reference when you need to find or modify something.

### Agents (`.github/agents/`)

| File | What It Is | What It Does |
|------|-----------|-------------|
| `daily-briefing.agent.md` | Daily Briefing agent | Orchestrates all agents into a comprehensive daily briefing with releases, discussions, reactions, CI/CD, security, and project board data |
| `issue-tracker.agent.md` | Issue Tracker agent | Issue command center with reactions, release context, discussion linking, saved searches, templates, and project board integration |
| `pr-review.agent.md` | PR Review agent | Code review with reactions, release awareness, discussion context, CI check runs, and security flags |
| `analytics.agent.md` | Analytics & Insights agent | Team velocity, review turnaround, contribution metrics, bottleneck detection, and code churn analysis |
| `insiders-a11y-tracker.agent.md` | Accessibility Tracker agent | Accessibility tracking across all configured repos with WCAG/ARIA cross-references (VS Code by default) |
| `shared-instructions.md` | Shared instructions | Common rules for dual output, HTML accessibility, preferences loading, CI/CD, security, and project boards |
| `code-review-standards.md` | Code review standards | Quality standards for code reviews with community sentiment and release context |
| `preferences.md` | Workspace preferences | Your team's configuration -- merge strategy, reviewers, labels, templates, searches, team roster, schedule, CI, security, and project settings |

### Prompts (`.github/prompts/`)

| File | Command | Agent | What It Does |
|------|---------|-------|-------------|
| `daily-briefing.prompt.md` | `/daily-briefing` | Daily Briefing | Generate dual-format daily briefing |
| `my-issues.prompt.md` | `/my-issues` | Issue Tracker | Priority-sorted issue dashboard with reactions |
| `my-prs.prompt.md` | `/my-prs` | PR Review | PR dashboard with reviews, CI, and release status |
| `review-pr.prompt.md` | `/review-pr` | PR Review | Full PR review with dual-format documents |
| `pr-report.prompt.md` | `/pr-report` | PR Review | Save/update PR review as workspace documents |
| `pr-comment.prompt.md` | `/pr-comment` | PR Review | Line-specific PR comments with priority levels |
| `explain-code.prompt.md` | `/explain-code` | PR Review | Understand lines, functions, or blocks in a PR diff |
| `merge-pr.prompt.md` | `/merge-pr` | PR Review | Merge a PR with readiness checks and strategy |
| `pr-author-checklist.prompt.md` | `/pr-author-checklist` | PR Review | Self-review checklist for PR authors |
| `issue-reply.prompt.md` | `/issue-reply` | Issue Tracker | Context-aware issue reply |
| `create-issue.prompt.md` | `/create-issue` | Issue Tracker | Create well-structured issues with smart templates |
| `manage-issue.prompt.md` | `/manage-issue` | Issue Tracker | Edit, label, assign, close, reopen, lock, transfer |
| `react.prompt.md` | `/react` | Issue Tracker | Add emoji reactions to issues, PRs, and comments |
| `triage.prompt.md` | `/triage` | Issue Tracker | Dual-format triage dashboard with reactions |
| `a11y-update.prompt.md` | `/a11y-update` | A11y Tracker | Accessibility updates with WCAG cross-references |
| `refine-issue.prompt.md` | `/refine-issue` | Issue Tracker | Issue refinement with community context |
| `address-comments.prompt.md` | `/address-comments` | PR Review | Systematically work through PR review comments |
| `team-dashboard.prompt.md` | `/team-dashboard` | Analytics | Team activity, review load, and bottlenecks |
| `my-stats.prompt.md` | `/my-stats` | Analytics | Personal contribution and review metrics |
| `draft-release.prompt.md` | `/draft-release` | Daily Briefing | Draft release notes from merged PRs |
| `ci-status.prompt.md` | `/ci-status` | Daily Briefing | CI/CD health dashboard across repos |
| `security-dashboard.prompt.md` | `/security-dashboard` | Daily Briefing | Dependabot alerts and security advisories |
| `release-prep.prompt.md` | `/release-prep` | Daily Briefing | Complete release preparation workflow |
| `sprint-review.prompt.md` | `/sprint-review` | Analytics | End-of-sprint summary with velocity |
| `onboard-repo.prompt.md` | `/onboard-repo` | Daily Briefing | First-time repo onboarding scan |
| `notifications.prompt.md` | `/notifications` | Daily Briefing | GitHub notification management |
| `manage-branches.prompt.md` | `/manage-branches` | PR Review | Branch listing, cleanup, and comparison |
| `project-status.prompt.md` | `/project-status` | Issue Tracker | GitHub Projects overview and metrics |

### Generated Documents (`.github/reviews/`)

| Folder | Formats | What's Inside | Created By |
|--------|---------|-------------|-----------|
| `briefings/` | `.md` + `.html` | Daily and weekly briefing documents | Daily Briefing |
| `issues/` | `.md` + `.html` | Issue deep dives and triage dashboards | Issue Tracker |
| `prs/` | `.md` + `.html` | PR review documents with checklists | PR Review |
| `accessibility/` | `.md` + `.html` | Monthly accessibility reports with WCAG analysis | A11y Tracker |
| `analytics/` | `.md` + `.html` | Team dashboards, personal stats, sprint reviews | Analytics |
| `releases/` | `.md` + `.html` | Release notes, readiness checklists, changelogs | Daily Briefing |
| `onboarding/` | `.md` + `.html` | First-time repo health scans | Daily Briefing |

---

## Architecture

Here's how everything connects. The Daily Briefing agent sits at the top, orchestrating the other four agents. Shared instructions and preferences flow through everything. The GitHub API feeds it all.

```
+------------------------------------------------------------------+
|                    Daily Briefing Agent                           |
|   Orchestrates all agents into one report                        |
|   + Releases + Discussions + Reactions + CI/CD + Security        |
|   + Project Board + Notifications                                |
+------------------------------------------------------------------|
|          |           |              |                             |
v          v           v              v                             |
+--------+ +--------+ +------------+ +----------------------+     |
|Issue   | |PR      | |Analytics & | |A11y Tracker          |     |
|Tracker | |Review  | |Insights    | |+ WCAG + ARIA         |     |
|+Search | |+Checks | |+Velocity   | |+ Configurable Repos  |     |
|+Templat| |+Securi | |+Turnaround | |                      |     |
|+Project| |+Project| |+Bottleneck | |                      |     |
|+Manage | |+Merge  | |+Churn      | |                      |     |
|+React  | |+Sugges | |+Team Stats | |                      |     |
+--------+ +--------+ +------------+ +----------------------+     |
     |          |            |                                     |
     +----------+------------+-------------------------------------|
                |            |                                     |
                v (Handoffs between agents)                        |
         +--------------------------+                              |
         |   Shared Instructions    |                              |
         | + Dual Output (MD+HTML)  |                              |
         | + HTML A11y Standards    |                              |
         | + CI/CD Awareness        |                              |
         | + Security Awareness     |                              |
         | + Project Boards         |                              |
         | + Preferences Loading    |                              |
         |   Code Review Standards  |                              |
         +--------------------------+                              |
                    |                                              |
         +----------v---------------+                              |
         |   Workspace Preferences  |                              |
         |   (preferences.md)       |                              |
         | + Merge / Reviewers      |                              |
         | + Templates / Searches   |                              |
         | + Team / Schedule        |                              |
         | + CI / Security / Boards |                              |
         +--------------------------+                              |
                                                                   |
  28 Prompt Commands (/my-issues, /team-dashboard, /ci-status, ..) |
  Dual-Format Workspace Documents                                  |
  (.md + .html in .github/reviews/)                                |
+------------------------------------------------------------------+

                    GitHub API
                    (via MCP)
                       |
                       v
            Issues, PRs, Releases,
            Discussions, Reactions,
            Comments, Reviews, Labels,
            Milestones, Assignees,
            Workflows, Check Runs,
            Dependabot, Projects,
            Notifications, Branches
```

---

*That's the complete picture. 5 agents, 28 commands, and zero browser tabs between you and your entire GitHub world.*

*Take your time with it. Try one new thing each day. And when you discover a workflow that clicks -- that moment where you realize you haven't opened GitHub in your browser all morning -- you'll know the system is working.*

*You've got this.*
