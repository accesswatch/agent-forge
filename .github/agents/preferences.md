# Workspace Preferences

All agents read this file at startup to personalize their behavior. Edit the YAML blocks below to configure your workspace.

---

## Merge Strategy

Default merge method when using `/merge-pr`. Agents will pre-select this option but always confirm before merging.

```yaml
merge:
  default_strategy: squash    # squash | rebase | merge
  delete_branch_after: true   # auto-offer to delete source branch after merge
  require_ci_pass: true       # block merge suggestion if CI is failing
```

---

## Default Reviewers

Agents suggest these reviewers when creating or updating PRs. Paths support glob patterns.

```yaml
reviewers:
  default:
    - alice
    - bob
  by_path:
    "src/auth/**":
      - charlie      # security team
    "src/ui/**":
      - dana         # frontend team
    "docs/**":
      - eve          # documentation team
```

---

## Labels & Priority System

Define your label taxonomy so agents can classify and filter consistently.

```yaml
labels:
  priority:
    - P0          # critical — drop everything
    - P1          # high — this sprint
    - P2          # medium — next sprint
    - P3          # low — backlog
  type:
    - bug
    - feature
    - enhancement
    - task
    - documentation
  status:
    - needs-triage
    - needs-info
    - in-progress
    - blocked
```

---

## Response Templates

Canned replies for common situations. Use with: `@issue-tracker reply to #42 with template needs-info`

```yaml
templates:
  needs-info: |
    Thanks for reporting! Could you provide:
    1. Steps to reproduce
    2. Expected vs actual behavior
    3. Environment details (OS, version, etc.)
  duplicate: |
    Closing as duplicate of #{ref}. Please follow that issue for updates.
  wontfix: |
    After discussion, we've decided not to pursue this. {reason}
    Thanks for the suggestion — feel free to reopen if circumstances change.
  welcome: |
    Welcome to the project! Thanks for your first contribution.
    A maintainer will review this shortly.
  stale-closing: |
    This issue has been inactive for 30+ days with no response.
    Closing for now — feel free to reopen if this is still relevant.
```

---

## Saved Searches

Named filters that any agent can use. Invoke with: `@issue-tracker search critical-bugs`

```yaml
searches:
  critical-bugs: "is:open label:bug label:P0"
  my-stale-prs: "is:open is:pr author:@me updated:<7-days-ago"
  needs-triage: "is:open no:label no:assignee"
  my-review-backlog: "is:open is:pr review-requested:@me"
  release-blockers: "is:open label:P0,P1 milestone:*"
  community-popular: "is:open sort:reactions-+1-desc"
  no-response: "is:open label:needs-info updated:<14-days-ago"
```

---

## Notification Preferences

Control which repos, labels, and event types get priority or are muted in briefings.

```yaml
notifications:
  priority_repos:
    - microsoft/vscode
    - my-org/core-api
  muted_repos:
    - my-org/archived-project
  priority_labels:
    - P0
    - P1
    - critical
    - security
  muted_labels:
    - wontfix
    - duplicate
  priority_events:
    - review_requested
    - mentioned
    - ci_failed
  muted_events:
    - subscribed      # auto-subscribed threads
```

---

## Team Roster

Team members, their GitHub handles, expertise areas, and timezones. Used for reviewer suggestions, load balancing, and time-aware briefings.

```yaml
team:
  - name: Alice Smith
    github: alice
    expertise:
      - backend
      - security
      - databases
    timezone: America/New_York
  - name: Bob Chen
    github: bob
    expertise:
      - frontend
      - accessibility
      - CSS
    timezone: America/Los_Angeles
  - name: Charlie Kumar
    github: charlie
    expertise:
      - devops
      - CI/CD
      - infrastructure
    timezone: Europe/London
  - name: Dana Rodriguez
    github: dana
    expertise:
      - frontend
      - React
      - design-systems
    timezone: America/Chicago
```

---

## Working Hours & Timezone

Used for time-aware briefings — the agent adjusts "since yesterday" and "morning" based on your working hours.

```yaml
schedule:
  timezone: America/New_York
  working_hours:
    start: "09:00"
    end: "17:00"
  working_days:
    - Monday
    - Tuesday
    - Wednesday
    - Thursday
    - Friday
```

---

## CI/CD Preferences

Configure which workflows and repos to monitor for CI/CD health.

```yaml
ci:
  monitored_workflows:
    - "Build and Test"
    - "Deploy"
    - "Lint"
  flaky_test_threshold: 3       # flag tests that fail N+ times in 7 days
  long_running_threshold: 30    # flag jobs running longer than N minutes
  monitored_repos:              # leave empty to use all active repos
    - my-org/core-api
    - my-org/frontend
```

---

## Security Preferences

Configure security monitoring thresholds and alert levels.

```yaml
security:
  alert_severity:
    - critical
    - high
    # - medium              # uncomment to include medium severity
    # - low                 # uncomment to include low severity
  auto_flag_dependabot: true    # flag Dependabot PRs in briefings
  monitored_repos:              # leave empty for all repos
    - my-org/core-api
```

---

## Project Board Preferences

Configure which GitHub Projects to surface in briefings and dashboards.

```yaml
projects:
  active:
    - project_number: 1
      org: my-org
      name: "Q1 Sprint Board"
    - project_number: 5
      org: my-org
      name: "Roadmap"
  show_in_briefing: true        # include project status in daily briefings
  show_in_issues: true          # show project column for issues
```

---

## How Agents Use These Preferences

1. **At startup**, every agent checks for `.github/agents/preferences.md` in the workspace.
2. If found, the agent parses the YAML blocks and applies them as defaults.
3. Preferences are **suggestions, not hard rules** — the user can always override in conversation.
4. If `preferences.md` doesn't exist, agents use their built-in defaults.
5. Agents reference specific sections — e.g., the PR Review agent reads `merge` and `reviewers`, the Daily Briefing agent reads `notifications` and `schedule`.
