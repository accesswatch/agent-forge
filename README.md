# GitHub Copilot Agents Repository

This repository contains a collection of GitHub Copilot agents and prompts designed to enhance productivity and automate various development workflows.

## Repository Structure

### 📁 `.github/agents/`
Contains various agent configurations and instructions:
- **analytics.agent.md** - Analytics and metrics tracking
- **code-review-standards.md** - Code review guidelines and standards
- **daily-briefing.agent.md** - Daily briefing and status reports
- **insiders-a11y-tracker.agent.md** - Accessibility tracking for VS Code Insiders
- **issue-tracker.agent.md** - Issue management and tracking
- **pr-review.agent.md** - Pull request review automation
- **preferences.md** - Agent preferences and settings
- **shared-instructions.md** - Common instructions shared across agents

### 📁 `.github/prompts/`
A comprehensive collection of prompt templates for various development tasks:
- **Repository Management**: onboard-repo, manage-branches, manage-issue
- **Code Review**: review-pr, pr-comment, address-comments, pr-author-checklist
- **Issue Management**: create-issue, refine-issue, triage, issue-reply
- **Release Management**: draft-release, release-prep
- **Team Collaboration**: daily-briefing, team-dashboard, sprint-review
- **Development Workflow**: explain-code, react, ci-status
- **Project Management**: project-status, my-issues, my-prs, my-stats
- **Security & Accessibility**: security-dashboard, a11y-update
- **Notifications**: notifications, merge-pr

### 📁 `Documentation/`
Project documentation in multiple formats:
- **GETTING-STARTED.md/.html** - Quick start guide
- **GUIDE.md/.html** - Comprehensive usage guide

## Getting Started

1. Refer to the [Getting Started Guide](Documentation/GETTING-STARTED.md) for setup instructions
2. Review the [Complete Guide](Documentation/GUIDE.md) for detailed documentation
3. Explore the agent configurations in `.github/agents/` to understand available automation
4. Browse prompt templates in `.github/prompts/` for ready-to-use workflows

## Usage

These agents and prompts are designed to work with GitHub Copilot to:
- Automate code reviews and quality checks
- Streamline issue and PR management
- Generate consistent project documentation
- Provide team insights and analytics
- Enhance accessibility and security practices

## Contributing

When contributing to this repository:
1. Follow the existing structure and naming conventions
2. Document new agents and prompts thoroughly
3. Test agents before submission
4. Update relevant documentation

## Note

This repository excludes review data and sensitive information through `.gitignore` configuration.