# Security Policy

## Supported Versions

We provide security updates for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| Latest  | Yes |
| < Latest| No                 |

## Reporting a Vulnerability

We take security vulnerabilities seriously. If you discover a security vulnerability in this repository, please follow these guidelines:

### How to Report

**For security vulnerabilities, please do NOT create a public issue.**

Instead:
1. **Email**: Send details to `jeff@jeffbishop.com`
2. **Include**: 
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Any suggested fixes

### Response Timeline

- **Initial Response**: Within 24-48 hours
- **Status Update**: Within 7 days
- **Resolution**: Varies based on severity and complexity

## Security Considerations for Agent Usage

### Data Privacy

- **Repository Access**: Agents operate within your GitHub permissions
- **Sensitive Data**: Never include API keys, tokens, or credentials in agent files
- **Team Information**: Only include publicly available team member data
- **Review Data**: The `.github/reviews/` folder is excluded by default for privacy

### Safe Configuration

#### Preferences.md Security
```yaml
# SAFE: Public GitHub usernames
team:
  - name: Alice Johnson
    github: alice-dev
    expertise: ["backend"]

# UNSAFE: Never include
# api_token: ghp_xxxxxxxxxxxx
# email: alice@company-internal.com
# private_repo_access: secret-project
```

#### Environment Variables
Use environment variables for sensitive data:
```bash
# In your environment, not in agent files
export GITHUB_TOKEN=your_token_here
export SLACK_WEBHOOK=your_webhook_here
```

### GitHub Permissions

#### Required Permissions
Agents need these GitHub permissions:
- **Read** access to repositories
- **Read** access to issues and pull requests
- **Read** access to repository metadata
- **Write** access (only if posting comments/updates)

#### Recommended Scope Limitation
- Use fine-grained personal access tokens
- Limit scope to specific repositories when possible
- Regular review and rotation of access tokens
- Enable two-factor authentication

### Best Practices

#### Repository Security
- **Branch Protection**: Enable for main branches
- **Review Requirements**: Require PR reviews
- **Status Checks**: Require passing CI/CD
- **Signed Commits**: Consider requiring signed commits

#### Agent Security
- **Regular Updates**: Keep agent instructions current
- **Access Review**: Regularly review team members and permissions
- **Audit Trail**: Monitor agent-generated actions
- **Principle of Least Privilege**: Grant minimum necessary access

#### Workspace Security
```yaml
# In preferences.md - security settings
security:
  alert_severity:
    - critical
    - high
  auto_flag_dependabot: true
  monitored_repos:
    - company/production-app
    # Don't list internal/sensitive repo names publicly
```

### Common Security Issues

#### What NOT to Include in Agent Files

```yaml
# These should NEVER appear in agent files:
api_keys:
  github: "ghp_xxxxxxxxxxxx"  # DO NOT include API tokens
    slack: "xoxb-xxxxxxxxxxxxx"   # DO NOT include Bot tokens

credentials:
  database_url: "postgresql://user:pass@host/db"  # DO NOT include Connection strings
  aws_secret: "AKIA..."        # DO NOT include AWS credentials

internal:
  server_ips: ["10.0.1.5"]     # DO NOT include Internal infrastructure
  employee_emails: [...]        # DO NOT include Internal contact info
```

#### Safe Alternatives

```yaml
# Use public information and environment references:
team:
  - name: "Alice Johnson"        # Public name
    github: "alice"             # Public GitHub username  
    timezone: "America/New_York" # Public timezone

repositories:
  monitored:
    - "microsoft/vscode"        # Public repositories
    - "company/public-docs"     # Public company repos

workflow:
  use_environment_tokens: true  # Reference to env vars
```

### Incident Response

#### If Sensitive Data is Exposed

1. **Immediate Actions**:
   - Revoke any exposed API keys/tokens
   - Change exposed passwords
   - Review access logs
   - Remove sensitive commits from history

2. **Repository Cleanup**:
   ```bash
   # Remove sensitive file from history
   git filter-branch --force --index-filter \
     'git rm --cached --ignore-unmatch sensitive-file.md' \
     --prune-empty --tag-name-filter cat -- --all
   ```

3. **Prevention**:
   - Update .gitignore
   - Add pre-commit hooks
   - Team security training
   - Regular security reviews

### Regular Security Tasks

#### Monthly
- [ ] Review team member access
- [ ] Update preferences.md with team changes
- [ ] Check for exposed sensitive data
- [ ] Review GitHub repository permissions

#### Quarterly  
- [ ] Rotate API tokens and keys
- [ ] Security audit of agent configurations
- [ ] Review and update security policies
- [ ] Team security training refresh

#### Annually
- [ ] Comprehensive security review
- [ ] Update security documentation
- [ ] Review and update incident response procedures
- [ ] External security assessment (if applicable)

### Contact Information

For security questions or concerns:
- **Security Team**: jeff@jeffbishop.com
- **General Questions**: Use GitHub Discussions
- **Urgent Issues**: Contact repository maintainers directly

---

## Disclaimer

This security policy applies to the agent configuration files and templates. Users are responsible for securing their own GitHub accounts, repositories, and any data processed by the agents.

The maintainers of this repository are not responsible for security issues arising from misconfiguration or misuse of the provided agents and templates.