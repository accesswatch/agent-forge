# Claude AI Instructions for GitHub Agent Workflows

These instructions help you use the GitHub agents and prompts from this repository with Claude AI.

## Setup for Claude

1. **Load Context**: Begin your conversation by sharing the content of relevant agent files
2. **Reference Preferences**: Include your `preferences.md` configuration 
3. **Use Prompt Templates**: Copy and adapt prompts from the `.github/prompts/` folder

## Key Files to Reference

### Core Behavior
- `.github/agents/shared-instructions.md` - Core agent behavior rules
- `.github/agents/preferences.md` - Your workspace configuration

### Specific Agents  
- `.github/agents/daily-briefing.agent.md` - Daily GitHub briefing generation
- `.github/agents/pr-review.agent.md` - Pull request review assistance  
- `.github/agents/issue-tracker.agent.md` - Issue management and triage
- `.github/agents/analytics.agent.md` - GitHub analytics and insights

## Usage Patterns

### Starting a Session

```
I'm working with a GitHub repository and want you to act as my GitHub agent assistant. 

Here's my configuration:
[paste your preferences.md content]

And here are the core behavior rules:
[paste shared-instructions.md content]

I'd like you to help me with [specific task].
```

### Daily Briefing

```
I need a daily GitHub briefing. Use the daily-briefing agent behavior:
[paste daily-briefing.agent.md content]

Generate a briefing covering:
- My open PRs and issues
- Items needing my review  
- Recent activity in my key repositories
- Action items for today

Scope: [morning/afternoon/weekly/specific repo]
```

### PR Review

```
I need help reviewing a pull request. Use the pr-review agent behavior:
[paste pr-review.agent.md content]

PR details:
- Repository: owner/repo
- PR number: #123
- Review type: [quick/thorough/security-focused]

[Include PR link or description]
```

### Issue Triage

```
Help me triage issues using the issue-tracker agent:
[paste issue-tracker.agent.md content]

Repository: owner/repo
Action: triage new issues / review my assigned issues / search for duplicates

[Include relevant issue details]
```

## Prompt Templates

Use these templates from `.github/prompts/` by copying the content and replacing variables:

### Variables Format
Replace `${input:variable:description}` with actual values:
- `${input:scope:morning/afternoon/weekly}` → `morning` 
- `${input:repo:repository name}` → `microsoft/vscode`
- `${input:pr_number:PR number}` → `#1234`

### Example Template Usage

**Original prompt template:**
```markdown
@daily-briefing generate briefing for ${input:scope:morning/afternoon/weekly}
Repository focus: ${input:repo:optional repository name}
```

**Adapted for Claude:**
```markdown
@daily-briefing generate briefing for morning
Repository focus: microsoft/vscode
```

## Response Templates

Configure these based on your preferences.md:

```yaml
templates:
  needs-info: |
    Thanks for reporting! Could you provide:
    1. Steps to reproduce
    2. Expected vs actual behavior  
    3. Environment details
```

**Usage with Claude:**
```
I need to reply to an issue that needs more information. Use this template:
[paste template content]

Adapt it for this specific issue:
[paste issue details]
```

## Advanced Workflows

### Multi-Repository Analysis

```
Analyze activity across multiple repositories:
- company/frontend
- company/backend  
- company/mobile

Focus on:
- Cross-repo dependencies in open PRs
- Issues that might affect multiple repos
- Coordination needs between teams

Use the analytics agent behavior for insights.
```

### Security Review Focus

```
Review this PR with security focus:
[paste pr-review.agent.md sections related to security]

PR: [link or description]

Pay special attention to:
- Authentication/authorization changes
- Data validation
- Dependency updates
- API endpoint modifications
```

### Team Coordination

```
Generate a team status update using:
- Issues assigned to team members
- PRs awaiting review from team  
- Blocked items needing attention
- Sprint progress overview

Team members: [list from preferences.md]
Focus repositories: [list from preferences.md]
```

## Integration Tips

### Conversation Memory
- Reference agent files at the start of conversations
- Keep preferences handy for consistent behavior
- Use agent names in your requests for context

### Batch Operations
- Process multiple issues/PRs in one conversation
- Use saved searches from preferences.md
- Group similar tasks for efficiency

### Follow-up Actions
- Ask Claude to format responses as GitHub comments
- Request specific markdown formatting for issues/PRs
- Generate action item lists for next steps

## Limitations

Claude cannot directly:
- Access live GitHub data (you need to provide)  
- Post comments or make changes (you handle the actions)
- Execute GitHub CLI commands (you run them)

Claude can help with:
- Analyzing provided GitHub data
- Generating responses and comments
- Planning and structuring workflows
- Creating formatted reports and summaries

## Example Workflow

1. **Load Context**: Share agent files and preferences
2. **Provide Data**: Copy/paste GitHub information
3. **Request Analysis**: Ask for specific agent behavior
4. **Review Output**: Check generated responses/reports
5. **Take Action**: Use Claude's output in GitHub

This approach gives you the benefits of the agent system while working within Claude's capabilities.