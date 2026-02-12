# AI Integration Instructions

This directory contains guides for integrating the GitHub agents and prompts with different AI models and platforms.

## Available Integrations

### 🤖 [GitHub Copilot Integration](copilot-integration.md)
- **Native support** - Agents work directly with Copilot
- **Workspace detection** - Automatic configuration loading
- **@agent syntax** - Direct agent invocation
- **VS Code integration** - Seamless workflow integration

### 🎨 [Claude AI Instructions](claude-instructions.md)  
- **Context setup** - How to provide agent context to Claude
- **Prompt adaptation** - Converting templates for Claude use
- **Workflow patterns** - Common usage scenarios
- **Variable substitution** - Adapting dynamic prompts

### 💬 [ChatGPT/OpenAI Integration](openai-integration.md)
- **Custom instructions** - Setting up agent behavior
- **Prompt engineering** - Optimizing for GPT models
- **API integration** - Programmatic usage patterns
- **Function calling** - Advanced automation workflows

## Quick Start by AI Platform

### GitHub Copilot (Recommended)
```
1. Copy agents to .github/agents/ in your workspace
2. Customize .github/agents/preferences.md
3. Use @agent-name syntax in Copilot chat
```

### Claude AI
```
1. Load agent content as conversation context
2. Include your preferences.md configuration
3. Use adapted prompt templates
4. Reference shared-instructions.md for behavior
```

### ChatGPT/OpenAI
```
1. Set up custom instructions with agent behavior
2. Use system prompts for consistent responses
3. Adapt templates for GPT prompt format
4. Consider API integration for automation
```

## Universal Concepts

### Agent Structure
All agents follow this pattern:
- **Metadata** - Name, description, capabilities
- **Instructions** - Detailed behavior guidelines  
- **Examples** - Usage scenarios and expected outputs
- **Integration** - How to work with other agents

### Prompt Templates
Prompts use variable substitution:
- `${input:variable:description}` format
- Clear parameter descriptions
- Flexible scope and context options
- Consistent output formatting

### Configuration System
The `preferences.md` file provides:
- Team member information
- Default behaviors and settings
- Response templates
- Saved searches and filters
- Workflow customization

## Choosing the Right Integration

| Feature | GitHub Copilot | Claude AI | ChatGPT/OpenAI |
|---------|----------------|-----------|----------------|
| **Native Support** | ✓ Full | ✗ Manual | ✗ Manual |
| **Workspace Context** | ✓ Automatic | ✗ Manual | ✗ Manual |
| **Real-time Data** | ✓ Yes | ✗ Provided by user | ✗ API required |
| **GitHub Integration** | ✓ Direct | ✗ Copy/paste | ✓ API possible |
| **Customization** | ✓ preferences.md | ✓ Conversation | ✓ System prompts |
| **Learning Curve** | � Low | 🟡 Medium | 🟡 Medium |

## Migration Between Platforms

### From Copilot to Claude
1. Extract agent content from .agent.md files
2. Copy preferences.md configuration  
3. Adapt prompts by replacing variables
4. Set up conversation context

### From Claude to OpenAI
1. Convert conversation context to system prompts
2. Adapt response formatting for GPT models
3. Consider function calling for GitHub actions
4. Set up custom instructions

### From OpenAI to Copilot
1. Convert system prompts to .agent.md format
2. Extract preferences into preferences.md
3. Adapt prompts to use ${input:} variables
4. Set up workspace structure

## Best Practices

### Universal Guidelines
- **Consistency** - Use the same agent behavior across platforms
- **Documentation** - Keep clear records of customizations
- **Testing** - Verify agent behavior with real scenarios
- **Maintenance** - Regular updates to preferences and team info

### Platform-Specific Tips
- **Copilot** - Leverage workspace context and automatic detection
- **Claude** - Provide rich context at conversation start
- **OpenAI** - Use system prompts and function calling for automation

### Security Considerations
- Never include sensitive data in agent files
- Be mindful of data sharing between platforms
- Use environment variables for credentials
- Regular review of shared information

## Contributing

Help improve AI integration:

1. **Test** agents with different AI platforms
2. **Document** platform-specific quirks and solutions  
3. **Share** successful integration patterns
4. **Report** issues with platform compatibility

### Adding New Platform Support

1. Create `{platform}-integration.md` file
2. Follow the established documentation pattern
3. Include setup, usage, and troubleshooting
4. Test thoroughly with real workflows
5. Submit PR with examples

## Need Help?

- **General Questions** - Check the main documentation
- **Platform Issues** - Refer to platform-specific guides
- **Agent Problems** - Review agent documentation in `.github/agents/`
- **Contribution Ideas** - Open a discussion or issue

Choose your platform and start enhancing your GitHub workflow! 🚀