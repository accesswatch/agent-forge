# Getting Started -- Your First Hour with GitHub Agents

> **You're about to do something pretty cool.**
>
> By the end of this guide, you'll have an AI assistant inside your code editor that talks to GitHub for you -- finding your issues, reviewing code, tracking your team's progress, and saving you hours of tab-switching every week.
>
> No prior GitHub expertise needed. We'll walk through everything together.

---

## Before We Begin

Let's make sure you have what you need. Don't worry if some of these terms are unfamiliar -- we'll explain each one as we go.

### What You Need

1. **VS Code** -- a free code editor from Microsoft. If you're reading this file in VS Code right now, you're already set. If not, grab it from [code.visualstudio.com](https://code.visualstudio.com).

2. **A GitHub account** -- GitHub is where developers store code, track bugs, and collaborate. If you don't have an account yet, go to [github.com](https://github.com) and sign up. It's free.

3. **GitHub Copilot** -- this is an AI coding assistant that runs inside VS Code. It has a chat window where you can type questions and commands. You'll need a Copilot subscription (there's a free tier for individual use).

That's the full list. No command-line tools, no API keys, no complex configuration.

---

## Step 1: Install the Extensions

If you already have GitHub Copilot working in VS Code, skip to [Step 2](#step-2-sign-in-to-github).

Open VS Code and let's install two extensions:

1. **Open the Extensions panel** -- click the square icon on the left sidebar, or press `Ctrl+Shift+X` (on Mac: `Cmd+Shift+X`). A search bar appears at the top.

2. **Search for "GitHub Copilot"** -- type it in the search bar. You'll see two extensions:
   - **GitHub Copilot** -- install this one first. Click the blue "Install" button.
   - **GitHub Copilot Chat** -- install this one too. This gives you the chat window where you'll talk to the agents.

3. **Wait for them to finish installing.** You'll see a small spinning icon while they download. When it stops, you're good.

> **What just happened?** You added two tools to VS Code. "Copilot" helps you write code. "Copilot Chat" gives you a conversation window where you can ask questions -- and where our agents live.

---

## Step 2: Sign In to GitHub

The agents need to talk to GitHub on your behalf -- to read your issues, check your pull requests, and so on. For that, VS Code needs to know who you are on GitHub.

1. **Open the Command Palette** -- press `Ctrl+Shift+P` (on Mac: `Cmd+Shift+P`). A text box drops down from the top of VS Code.

2. **Type "GitHub: Sign In"** -- as you type, you'll see it appear in the list. Click on it.

3. **A browser window opens** -- GitHub asks you to authorize VS Code. Click "Authorize" and follow the prompts. You might need to enter your GitHub password.

4. **Come back to VS Code** -- once you authorize, VS Code will show your GitHub username in the bottom-left corner (click the little person icon to check). If you see your username, you're signed in.

> **What just happened?** VS Code now has permission to talk to GitHub as you. It can read your issues, your pull requests, your notifications -- everything the agents need to help you.

---

## Step 3: Open This Workspace

The agents are special files that live inside this project. VS Code discovers them automatically -- but only if you have the right folder open.

1. **Open this folder in VS Code** -- go to File > Open Folder (or `Ctrl+K Ctrl+O`) and navigate to the folder that contains the `.github` directory. That's the folder you're in right now if you can see this file.

2. **Check that the agents are loaded** -- open Copilot Chat by pressing `Ctrl+Shift+I` (on Mac: `Cmd+Shift+I`). In the chat input box, type `@` -- you should see a dropdown list that includes names like `@daily-briefing`, `@issue-tracker`, `@pr-review`. If you see those, the agents are ready.

> **Don't see the agents?** Make sure you opened the *folder* (not just a single file) that contains `.github/agents/`. Try File > Open Folder and pick the right directory. If that doesn't work, try reloading VS Code: press `Ctrl+Shift+P`, type "Developer: Reload Window", and press Enter.

---

## Step 4: Say Hello

Let's try the simplest thing first. In the Copilot Chat window:

**Type this and press Enter:**
```
@issue-tracker how many open issues do I have?
```

Wait a few seconds. The agent will:
1. Check who you are on GitHub
2. Search for your open issues
3. Come back with a count and a summary

**Did it work?** If you see a number and maybe a table of issues -- congratulations, everything is connected. The agent just talked to GitHub for you.

**Did it say "no issues found"?** That's fine too! It means you don't have any open issues right now. The connection is working.

**Did it ask you to sign in?** Go back to [Step 2](#step-2-sign-in-to-github) and make sure you're authenticated.

---

## Step 5: Your First Briefing

Now let's do something magical. This is the moment where everything clicks.

**Type this in Copilot Chat:**
```
@daily-briefing morning briefing
```

**Then wait about 30 seconds.** Here's what's happening behind the scenes:

The Daily Briefing agent is waking up and fanning out across your GitHub world. It's checking:
- Every issue assigned to you, mentioning you, or created by you
- Every pull request waiting for your review
- Every PR you authored and its CI status
- Recent releases across your repos
- Active GitHub Discussions you're part of
- Accessibility changes in VS Code (if you track that)
- Community reactions on everything

It's scoring all of these by urgency -- who's waiting on you, what's deadline-bound, what the community cares about -- and assembling them into a document.

When it finishes, it saves two files in your workspace:
- **`.github/reviews/briefings/briefing-{today's date}.md`** -- a markdown file you can read and edit right here in VS Code
- **`.github/reviews/briefings/briefing-{today's date}.html`** -- an HTML file you can open in a browser (with full screen reader support)

**Open the markdown file.** You'll see sections like:
- **Needs Your Action** -- things where someone is specifically waiting on you
- **Monitor & Follow Up** -- things happening that you should know about
- **Recently Completed** -- your recent accomplishments
- **Guidance** -- the agent's suggestions for what to focus on

**This is your daily dashboard.** You can check off items as you complete them throughout the day.

> **Feeling overwhelmed?** Don't worry -- you don't need to understand every section right away. The most important one is "Needs Your Action" at the top. Start there. Everything else can wait.

---

## Step 6: Explore One Issue

Let's go deeper. Pick an issue from your briefing (or any issue you know about) and ask the agent to show you the details.

**Type something like:**
```
@issue-tracker deep dive into owner/repo#42
```

Replace `owner/repo#42` with a real issue. For example, if you have an issue number 42 in a repository called `my-project` owned by `my-username`, you'd type:
```
@issue-tracker deep dive into my-username/my-project#42
```

> **Not sure what to type?** If you're inside a git repository, you can just use the issue number:
> ```
> @issue-tracker show me issue #42
> ```
> The agent is smart enough to figure out which repo you mean from the folder you have open.

The agent will pull the full issue: description, every comment, reactions, linked pull requests, and any related discussions. It saves this as a workspace document too -- a detailed file you can review offline.

---

## Step 7: Try a Slash Command

Slash commands are shortcuts. Instead of typing a full sentence to an agent, you type `/` followed by a command name, and the agent knows exactly what to do.

**Try this:**
```
/my-issues
```

That's it. Just `/my-issues` and press Enter. The Issue Tracker agent will search for all your open issues and show them sorted by priority.

**Here are a few more to try:**

| Type this | What happens |
|-----------|-------------|
| `/my-prs` | Shows your open pull requests with review status and CI health |
| `/triage` | Creates a prioritized triage dashboard and saves it to your workspace |
| `/notifications` | Shows your unread GitHub notifications grouped by type |
| `/ci-status` | Shows CI/CD health across your repos -- any failing builds? |

> **See the `/` autocomplete?** When you type `/` in the chat input, VS Code shows you all available commands in a dropdown. Browse through them -- there are 28 in total, and you can explore them at your own pace.

---

## Step 8: Leave a Comment Without Opening GitHub

This is where it gets really fun. You can reply to issues and pull requests without ever opening your browser.

**Type something like:**
```
@issue-tracker reply to owner/repo#42
```

The agent will:
1. Show you the recent conversation on that issue
2. Ask what you want to say
3. Draft a reply for you
4. Show you a preview of exactly what will be posted
5. Ask you to confirm: **Post**, **Edit**, or **Cancel**

Nothing gets posted until you say "Post." You're always in control.

> **Nervous about posting?** Totally normal. The agents *always* preview before posting. They'll show you exactly what will appear on GitHub, and they'll wait for your explicit confirmation. Think of it like a "Send" button on an email -- you get to review first.

---

## Step 9: React to Something

Reactions are the lightest-weight way to participate on GitHub -- a thumbs up, a heart, a rocket. They take two seconds and they let people know you've seen their work.

**Try:**
```
/react thumbs up owner/repo#42
```

Or in natural language:
```
@issue-tracker like issue #42
```

The agent shows the current reactions, adds yours, and confirms. That's it. Someone's morning just got a little brighter.

---

## Step 10: Make It Yours

Now that you've seen what the agents can do, you can customize how they work for you.

**Open `.github/agents/preferences.md`** in your editor. This file controls things like:

- **Your default merge strategy** -- squash, rebase, or merge commit?
- **Your team roster** -- names, GitHub handles, expertise areas, and timezones
- **Saved searches** -- name your favorite filters so you can run them with one command
- **Response templates** -- pre-written replies for common situations ("Thanks for reporting! Could you provide steps to reproduce?")
- **Notification preferences** -- which repos matter most, which ones to mute

You don't need to change anything right now. The agents work fine with their defaults. But when you're ready to make the system feel like *yours*, this is where you go.

---

## What to Do Tomorrow Morning

Here's your new morning routine. It takes about 5 minutes:

1. **Open VS Code** and Copilot Chat (`Ctrl+Shift+I`)
2. **Type** `@daily-briefing morning briefing`
3. **Open the briefing** -- scan "Needs Your Action" first
4. **Work through the top items:**
   - Need to review a PR? Type `@pr-review review owner/repo#123`
   - Need to reply to an issue? Type `/issue-reply owner/repo#42`
   - Want to triage your backlog? Type `/triage`
5. **Check things off** in the briefing document as you complete them

That's it. By the end of your first week, this will feel as natural as checking email.

---

## Quick Reference Card

Keep this handy until the commands become second nature.

### The Agents

| Agent | What to type | What they do |
|-------|-------------|-------------|
| Daily Briefing | `@daily-briefing` | Your prioritized overview of everything happening |
| Issue Tracker | `@issue-tracker` | Find, triage, reply to, and manage issues |
| PR Review | `@pr-review` | Review code, leave comments, merge PRs |
| Analytics | `@analytics` | Team metrics, velocity, bottlenecks |
| A11y Tracker | `@insiders-a11y-tracker` | Accessibility change tracking |

### Most Useful Commands for Beginners

| Command | What it does |
|---------|-------------|
| `/my-issues` | "What issues need my attention?" |
| `/my-prs` | "What's happening with my pull requests?" |
| `/triage` | "Help me prioritize my backlog" |
| `/review-pr owner/repo#N` | "Give me a full review of this PR" |
| `/issue-reply owner/repo#N` | "Help me reply to this issue" |
| `/react thumbs up owner/repo#N` | "I like this" |
| `/notifications` | "What notifications do I have?" |
| `/daily-briefing` | "Give me the full picture" |

### Things You Can Say in Plain English

You don't need to memorize commands. Try these:

```
@issue-tracker show me what needs my attention
@issue-tracker what's the most urgent issue?
@pr-review which PRs are waiting for my review?
@pr-review explain what changed in auth.ts in PR #15
@daily-briefing what happened since yesterday?
@analytics how's the team doing this sprint?
```

The agents understand intent. If your phrasing isn't perfect, they'll figure out what you mean.

---

## Glossary

If any of these terms are new to you, here's a quick reference:

| Term | What it means |
|------|--------------|
| **Repository (repo)** | A project folder on GitHub that holds code, issues, and history |
| **Issue** | A task, bug report, or feature request tracked on GitHub |
| **Pull Request (PR)** | A proposed code change that others can review before it's merged |
| **Merge** | Combining a pull request's changes into the main codebase |
| **Branch** | A parallel version of the code -- like a draft you can edit without affecting the original |
| **CI/CD** | Automated tests and builds that run when you push code |
| **Milestone** | A collection of issues/PRs grouped toward a release or goal |
| **Label** | A tag on an issue or PR (like "bug", "feature", "P0") |
| **Reaction** | An emoji response to an issue, PR, or comment (thumbs up, heart, rocket) |
| **Triage** | The process of reviewing issues and deciding what to do with each one |
| **Diff** | The difference between two versions of code -- what was added, changed, or removed |
| **Code review** | Reading someone else's code changes and giving feedback before they're merged |
| **Dependabot** | GitHub's automated tool that warns you about security issues in your dependencies |
| **WCAG** | Web Content Accessibility Guidelines -- standards for making things accessible |
| **Screen reader** | Software that reads screen content aloud for users who are blind or have low vision |

---

## When You're Ready for More

This guide got you started. When you're comfortable with the basics, the **[Complete Guide](GUIDE.md)** covers everything:

- All 5 agents in full detail
- All 28 slash commands
- Advanced workflows: release management, sprint reviews, branch cleanup, security monitoring
- Team analytics and bottleneck detection
- Workspace preferences and customization
- Screen reader accessibility features
- How the agents hand off to each other

Take your time. There's no rush. The agents will be here whenever you're ready to explore the next thing.

---

*You just set up a personal GitHub command center inside your code editor. That's not nothing. Go get a coffee -- you earned it.*
