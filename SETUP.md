# Setup Guide for GitHub Copilot Agents

This guide will help you set up and configure the GitHub Copilot agents in your workspace.

## Quick Start

1. **Clone or copy this repository structure** to your workspace
2. **Configure your preferences** in `.github/agents/preferences.md`
3. **Start using agents** with GitHub Copilot

## Directory Structure

Ensure your workspace has this structure:

```
your-workspace/
+-- .github/
|   +-- agents/
|   |   +-- preferences.md         # Your configuration
|   |   +-- shared-instructions.md  # Core agent behavior
|   |   +-- *.agent.md              # Individual agents
|   +-- prompts/
|       +-- *.prompt.md             # Prompt templates
+-- your-project-files...
```

## Configuration

### 1. Repository Discovery & Scope (Most Important)

Control which repos the agents scan. By default, agents search ALL repos you have access to.

```yaml
repos:
  # How agents discover repos. Options: all | starred | owned | configured | workspace
  discovery: all  # Default -- searches everything you can access

  # Optional: only scan these repos
  include:
    - my-org/main-app
    - my-org/api-service

  # Optional: never scan these repos
  exclude:
    - my-org/archived-project

  # Optional: per-repo overrides for granular control
  overrides:
    my-org/main-app:
      track:
        issues: true
        pull_requests: true
        discussions: true
        releases: true
        security: true
        ci: true
      labels:
        include: ["P0", "P1", "bug"]
      paths:
        - "src/**"

  # Defaults for repos without explicit overrides
  defaults:
    track:
      issues: true
      pull_requests: true
      discussions: false
      releases: true
      security: true
      ci: true
```

### 2. Accessibility Tracking

Track accessibility changes across repos (VS Code is tracked by default):

```yaml
accessibility_tracking:
  repos:
    - repo: microsoft/vscode
      labels: ["bug", "feature-request"]
      channels: ["insiders", "stable"]
    - repo: my-org/my-app
      labels: ["a11y", "accessibility"]
  wcag_references: true
  aria_patterns: true
  briefing_limit: 10
```

### 3. Customize Preferences

Edit `.github/agents/preferences.md` to match your workflow:

```yaml
# Example: Set your merge strategy
merge:
  default_strategy: squash
  delete_branch_after: true
  require_ci_pass: true

# Example: Configure team members
team:
  - name: Your Name
    github: your-username
    expertise:
      - backend
      - frontend
    timezone: America/New_York
```

### 4. Update Team Roster

Add your team members to enable smart reviewer suggestions:

```yaml
team:
  - name: Alice Smith
    github: alice
    expertise: ["security", "backend"]
    timezone: America/New_York
  - name: Bob Chen  
    github: bob
    expertise: ["frontend", "React"]
    timezone: America/Los_Angeles
```

### 5. Configure Default Reviewers

Set up path-based reviewer suggestions:

```yaml
reviewers:
  default:
    - alice
  by_path:
    "src/security/**":
      - alice
    "src/ui/**":
      - bob
```

### 6. Set Up Response Templates

Customize response templates for common scenarios:

```yaml
templates:
  needs-info: |
    Thanks for reporting! Could you provide:
    1. Steps to reproduce
    2. Expected vs actual behavior
    3. Environment details
```

## Agent Usage

### Daily Briefing Agent

```
@daily-briefing generate morning briefing          # All repos by default
@daily-briefing afternoon update
@daily-briefing weekly summary
@daily-briefing just PRs for org:my-org            # Scope to an org
```

### PR Review Agent

```
@pr-review analyze #123                            # Workspace repo
@pr-review my open PRs                             # Cross-repo by default
@pr-review review owner/repo#45678                 # Specific repo
@pr-review detailed review focusing on security
```

### Issue Tracker Agent

```
@issue-tracker my issues needing attention          # All repos by default
@issue-tracker triage new issues for my-org/app     # Specific repo
@issue-tracker search critical bugs org:my-org      # Org-wide
@issue-tracker show issues labeled P0               # Cross-repo label search
```

### Accessibility Tracker Agent

```
@insiders-a11y-tracker what's new in accessibility  # All tracked repos
@insiders-a11y-tracker track a11y in owner/my-app   # Add a repo
@insiders-a11y-tracker WCAG coverage this month
```

## AI Model Integration

### GitHub Copilot

- Agents work natively with GitHub Copilot
- Use `@agent-name` syntax to invoke agents
- Agents automatically read preferences and adapt behavior

### Claude Integration

For Claude users:

1. Copy the agent content as context
2. Reference the shared-instructions.md for behavior guidelines
3. Use the prompt templates as structured inputs

### Other AI Models

The agents and prompts can be adapted for:

- OpenAI ChatGPT (copy as custom instructions)
- Anthropic Claude (use as conversation context)
- Local models (adapt prompt formatting as needed)

## Troubleshooting

### Agent Not Responding

1. Check that `.github/agents/` directory exists in your workspace
2. Verify agent files have `.agent.md` extension
3. Ensure preferences.md is properly formatted YAML

### Permissions Issues

1. Verify GitHub authentication in VS Code
2. Check repository access permissions
3. Ensure GitHub Copilot has required scopes

### Unexpected Behavior

1. Check preferences.md configuration
2. Review shared-instructions.md for behavior rules
3. Verify agent-specific instructions in the .agent.md file

## Advanced Configuration

### Custom Searches

Create saved searches for quick access:

```yaml
searches:
  my-critical: "is:open label:P0 assignee:@me"
  stale-prs: "is:open is:pr updated:<7-days-ago"
  security-alerts: "is:open label:security"
```

### Notification Preferences

Control which updates appear in briefings:

```yaml
notifications:
  priority_repos:
    - my-org/critical-service
  priority_labels:
    - P0
    - security
  muted_labels:
    - duplicate
```

### CI/CD Monitoring

```yaml
ci:
  monitored_workflows:
    - "Build and Test"
    - "Deploy Production"
  flaky_test_threshold: 3
  long_running_threshold: 30
```

## Need Help?

- **Documentation**: See the `Documentation/` folder
- **Examples**: Check existing agent and prompt files
- **Issues**: Create an issue if something isn't working
- **Discussions**: Use GitHub Discussions for questions

Enjoy your enhanced GitHub workflow!