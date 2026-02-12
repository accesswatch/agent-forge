# GitHub Copilot Integration Guide

This repository is designed to work natively with GitHub Copilot. Here's how to get the most out of the agent system.

## Native Integration

### Agent Recognition
GitHub Copilot automatically recognizes agents in `.github/agents/` directories and can invoke them using the `@agent-name` syntax.

### File Structure for Copilot
```
.github/
├── agents/
│   ├── preferences.md          # Copilot reads this for context
│   ├── shared-instructions.md   # Common behavior rules
│   └── *.agent.md               # Individual agents
└── prompts/
    └── *.prompt.md              # Prompt templates
```

## Usage Patterns

### Basic Agent Invocation
```
@daily-briefing generate morning briefing
@pr-review analyze #1234 
@issue-tracker triage new issues
@analytics show team dashboard
```

### With Scope and Context
```
@daily-briefing generate briefing for microsoft/vscode
@pr-review quick review of #1234 focusing on security
@issue-tracker search critical bugs in my assigned issues
```

### Prompt Template Usage
Copilot can use prompt templates with variable substitution:
```
/use-prompt daily-briefing scope:morning
/use-prompt pr-review pr_number:1234 focus:security
/use-prompt triage repo:microsoft/vscode
```

## Advanced Features

### Contextual Awareness
Copilot automatically:
- Reads your preferences.md for personalized behavior
- Detects the current repository context
- Applies team settings and reviewer preferences
- Uses your saved searches and templates

### Multi-Step Workflows
```
@daily-briefing generate morning briefing, then @issue-tracker triage any new critical issues
```

### Cross-Agent Collaboration
```
Analyze PR #1234 with @pr-review, then update the daily briefing
```

## Configuration

### Workspace Setup
1. Ensure `.github/agents/` exists in your workspace root
2. Copy `preferences.example.md` to `preferences.md`
3. Customize preferences for your workflow
4. Agents will automatically detect and use your settings

### Team Configuration
In `preferences.md`:
```yaml
team:
  - name: Alice Johnson
    github: alice
    expertise: ["security", "backend"]
    timezone: America/New_York
```

### Default Reviewers
```yaml
reviewers:
  default:
    - alice
    - bob
  by_path:
    "src/security/**":
      - security-team
```

## Best Practices

### Agent Naming
- Use descriptive, action-oriented names
- Follow the pattern: `{function}.agent.md`
- Keep names short for easy invocation

### Preference Organization
- Group related settings in YAML blocks
- Use consistent indentation (2 spaces)
- Include comments explaining custom settings
- Regular review and update team information

### Prompt Development
- Use clear variable names: `${input:pr_number:PR to review}`
- Include descriptions in variable placeholders
- Test prompts with various input scenarios
- Document expected outputs and behaviors

## Troubleshooting

### Agent Not Responding
**Check:**
- File is in `.github/agents/` directory
- File has `.agent.md` extension  
- YAML frontmatter is properly formatted
- No syntax errors in preferences.md

### Unexpected Behavior
**Verify:**
- preferences.md configuration is correct
- Team settings match your actual team
- Repository context is being detected properly
- Agent instructions align with your workflow

### Performance Issues
**Optimize:**
- Keep agent files focused and concise
- Use saved searches instead of complex queries
- Limit the number of monitored repositories
- Regular cleanup of outdated preferences

## VS Code Integration

### Extensions
Recommended extensions that enhance the agent experience:
- GitHub Copilot (required)
- GitHub Repositories
- GitHub Pull Requests and Issues
- Git Graph

### Workspace Settings
Add to `.vscode/settings.json`:
```json
{
  "github.copilot.advanced": {
    "inlineSuggestEnable": true
  },
  "files.associations": {
    "*.agent.md": "markdown",
    "*.prompt.md": "markdown"
  }
}
```

### Keyboard Shortcuts
Useful shortcuts for agent workflows:
- `Ctrl+Shift+I` - Open GitHub Copilot chat
- `Ctrl+I` - Inline Copilot suggestions
- `Ctrl+P` - Quick file navigation

## Security Considerations

### Sensitive Information
- Never include API keys or tokens in agent files
- Be cautious with repository names in public configs
- Use environment variables for sensitive settings
- Regular review of preferences for outdated information

### Repository Access
- Agents operate within your GitHub permissions
- No additional access is granted beyond your account
- Team member information should be publicly available data
- Consider privacy when sharing preference files

## Monitoring and Maintenance

### Regular Tasks
- Update team member information quarterly
- Review and clean saved searches monthly
- Update response templates as workflows evolve
- Archive agents that are no longer used

### Performance Metrics
Monitor agent effectiveness through:
- Reduced manual triage time
- Faster PR review cycles
- Improved issue response times
- Better team coordination

## Getting Help

### Documentation
- Check the `Documentation/` folder
- Review agent-specific instructions
- Consult prompt template examples

### Community
- GitHub Discussions for questions
- Issue tracker for bugs or feature requests
- Contributing guidelines for improvements

### Microsoft Resources
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [VS Code GitHub Integration](https://code.visualstudio.com/docs/editor/github)
- [GitHub CLI](https://cli.github.com/)

Enjoy your enhanced GitHub workflow with Copilot! 🚀