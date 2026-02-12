# OpenAI/ChatGPT Integration Guide

Integrate the GitHub agents and prompts with OpenAI's ChatGPT, GPT-4, or API for automated GitHub workflows.

## Integration Methods

### 1. ChatGPT Custom Instructions
Set up agents as custom instructions for persistent behavior.

### 2. System Prompts (API)
Use agent content as system prompts for programmatic integration.

### 3. Function Calling (API)
Implement agents as functions with structured inputs/outputs.

## Setup Methods

### ChatGPT Custom Instructions

**Custom Instructions Setup:**
```
You are a GitHub workflow assistant. Follow these core behaviors:
[Insert content from shared-instructions.md]

My workspace configuration:
[Insert relevant sections from preferences.md]

When I mention specific agents like @daily-briefing or @pr-review, follow the detailed instructions for those specific workflows.
```

**Agent-Specific Instructions:**
For each agent you use frequently, add to custom instructions:
```
For daily briefings:
[Insert content from daily-briefing.agent.md]

For PR reviews:
[Insert content from pr-review.agent.md]
```

### API Integration with System Prompts

```python
import openai

def create_agent_client(agent_file_content, preferences_content):
    system_prompt = f"""
    You are a GitHub workflow assistant specialized in the following role:
    
    {agent_file_content}
    
    User preferences and configuration:
    {preferences_content}
    
    Follow the shared instructions for consistent behavior:
    - Be direct and efficient
    - Use GitHub URLs for all references
    - Provide actionable insights
    - Suggest next steps proactively
    """
    
    return openai.ChatCompletion.create(
        model="gpt-4",
        messages=[
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": user_query}
        ]
    )
```

### Function Calling for Automation

```python
functions = [
    {
        "name": "daily_briefing",
        "description": "Generate a daily GitHub briefing",
        "parameters": {
            "type": "object",
            "properties": {
                "scope": {
                    "type": "string",
                    "enum": ["morning", "afternoon", "weekly"],
                    "description": "Briefing scope and timeframe"
                },
                "repositories": {
                    "type": "array",
                    "items": {"type": "string"},
                    "description": "Specific repositories to focus on"
                }
            },
            "required": ["scope"]
        }
    },
    {
        "name": "review_pull_request", 
        "description": "Review a GitHub pull request",
        "parameters": {
            "type": "object",
            "properties": {
                "pr_url": {
                    "type": "string",
                    "description": "GitHub PR URL"
                },
                "review_type": {
                    "type": "string",
                    "enum": ["quick", "thorough", "security"],
                    "description": "Type of review to perform"
                },
                "focus_areas": {
                    "type": "array",
                    "items": {"type": "string"},
                    "description": "Specific areas to focus on"
                }
            },
            "required": ["pr_url"]
        }
    }
]
```

## Usage Patterns

### Daily Briefing with ChatGPT

**User Input:**
```
@daily-briefing generate morning briefing for microsoft/vscode
```

**Expected GPT Behavior:**
```
I'll generate your morning briefing focused on microsoft/vscode. Let me provide:

## Daily GitHub Briefing - Morning Update
**Repository:** microsoft/vscode  
**Date:** [current date]

### High Priority Items
- Issues assigned to you: [list with links]
- PRs awaiting your review: [list with links]
- Your PRs needing attention: [list with links]

### Recent Activity
- New issues since yesterday: [summary]
- PR updates: [summary]
- CI/CD status: [summary]

### Suggested Actions
1. Review PR #[number] - [description]
2. Respond to issue #[number] - [description]
3. Check failing CI on PR #[number]

Want to dive deeper into any of these items?
```

### PR Review with API

```python
def review_pr_with_gpt(pr_url, review_type="thorough"):
    # Fetch PR data
    pr_data = github_api.get_pr(pr_url)
    
    # Build context
    context = f"""
    PR Review Request:
    URL: {pr_url}
    Title: {pr_data['title']}
    Author: {pr_data['author']}
    Files Changed: {len(pr_data['files'])}
    Lines Added/Removed: +{pr_data['additions']}/-{pr_data['deletions']}
    
    Description:
    {pr_data['description']}
    """
    
    # Get agent instructions
    pr_review_agent = load_agent_instructions("pr-review.agent.md")
    
    # Generate review
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[
            {"role": "system", "content": pr_review_agent},
            {"role": "user", "content": f"{review_type} review: {context}"}
        ],
        functions=functions,
        function_call={"name": "review_pull_request"}
    )
    
    return response
```

### Issue Triage Automation

```python
def auto_triage_issues(repo_owner, repo_name):
    # Get new issues
    issues = github_api.get_issues(
        repo=f"{repo_owner}/{repo_name}",
        state="open",
        labels="needs-triage"
    )
    
    # Load issue tracker agent
    issue_agent = load_agent_instructions("issue-tracker.agent.md")
    
    results = []
    for issue in issues:
        # Build issue context
        context = f"""
        Issue: #{issue['number']}
        Title: {issue['title']}
        Author: {issue['user']['login']}
        Labels: {[label['name'] for label in issue['labels']]}
        
        Body:
        {issue['body']}
        """
        
        # Get triage suggestion
        response = openai.ChatCompletion.create(
            model="gpt-4",
            messages=[
                {"role": "system", "content": issue_agent},
                {"role": "user", "content": f"Triage this issue: {context}"}
            ]
        )
        
        results.append({
            'issue_number': issue['number'],
            'triage_suggestion': response.choices[0].message.content
        })
    
    return results
```

## Prompt Engineering Tips

### Template Adaptation

**Original Template:**
```markdown
Generate briefing for ${input:scope:morning/afternoon/weekly}
Repository: ${input:repo:optional repository name}
```

**GPT Adaptation:**
```python
def format_briefing_prompt(scope, repo=None):
    prompt = f"Generate briefing for {scope}"
    if repo:
        prompt += f"\nRepository: {repo}"
    return prompt
```

### Response Formatting

**Structure GPT Responses:**
```
Provide responses in this format:

## Summary
[Brief overview]

## Key Items
1. [Item with GitHub URL]
2. [Item with GitHub URL]

## Suggested Actions
- [ ] [Actionable item]
- [ ] [Actionable item]

## Next Steps
[Proactive suggestions]
```

### Variable Handling

```python
import re

def process_prompt_template(template, **variables):
    """Convert agent template to GPT prompt with variables"""
    
    # Replace ${input:var:desc} with actual values
    def replace_variable(match):
        var_name = match.group(1)
        return variables.get(var_name, f"[{var_name} not provided]")
    
    pattern = r'\$\{input:([^:]+):([^}]+)\}'
    processed = re.sub(pattern, replace_variable, template)
    
    return processed

# Usage
template = "Review PR ${input:pr_number:PR number} with ${input:focus:review focus}"
processed = process_prompt_template(template, pr_number="#1234", focus="security")
# Result: "Review PR #1234 with security"
```

## Advanced Automation

### Webhook Integration

```python
from flask import Flask, request
import openai

app = Flask(__name__)

@app.route('/github-webhook', methods=['POST'])
def handle_github_webhook():
    payload = request.json
    
    if payload['action'] == 'opened' and 'pull_request' in payload:
        # Auto-review new PRs
        pr_data = payload['pull_request']
        
        # Generate initial review
        review = review_pr_with_gpt(pr_data['html_url'], 'quick')
        
        # Post as PR comment
        github_api.create_pr_comment(
            pr_data['url'],
            review['content']
        )
    
    elif payload['action'] == 'labeled' and 'issue' in payload:
        # Auto-respond to labeled issues
        if 'needs-info' in [label['name'] for label in payload['issue']['labels']]:
            # Generate needs-info response
            response = generate_template_response('needs-info', payload['issue'])
            
            github_api.create_issue_comment(
                payload['issue']['url'],
                response
            )
    
    return '', 200
```

### Batch Processing

```python
def batch_process_with_gpt(items, agent_type, batch_size=10):
    """Process multiple GitHub items with GPT in batches"""
    
    agent_instructions = load_agent_instructions(f"{agent_type}.agent.md")
    results = []
    
    for i in range(0, len(items), batch_size):
        batch = items[i:i+batch_size]
        
        # Create batch prompt
        batch_context = "\n\n".join([
            f"Item {j+1}: {format_item(item)}"
            for j, item in enumerate(batch)
        ])
        
        response = openai.ChatCompletion.create(
            model="gpt-4",
            messages=[
                {"role": "system", "content": agent_instructions},
                {"role": "user", "content": f"Process these items:\n\n{batch_context}"}
            ]
        )
        
        results.extend(parse_batch_response(response.choices[0].message.content))
    
    return results
```

## Monitoring and Optimization

### Usage Tracking

```python
import time
from collections import defaultdict

class GPTAgentTracker:
    def __init__(self):
        self.usage_stats = defaultdict(list)
    
    def track_request(self, agent_name, tokens_used, response_time):
        self.usage_stats[agent_name].append({
            'timestamp': time.time(),
            'tokens': tokens_used,
            'response_time': response_time
        })
    
    def get_stats(self, agent_name=None):
        if agent_name:
            return self.usage_stats[agent_name]
        return dict(self.usage_stats)
```

### Cost Optimization

```python
def optimize_prompt_length(agent_content, max_tokens=2000):
    """Optimize agent instructions to fit token limits"""
    
    # Priority sections to keep
    priority_sections = [
        'Core Behavior',
        'Response Format', 
        'Key Instructions'
    ]
    
    # Truncate less critical sections
    optimized = extract_priority_content(agent_content, priority_sections)
    
    if count_tokens(optimized) > max_tokens:
        # Further optimization needed
        optimized = summarize_agent_instructions(optimized, max_tokens)
    
    return optimized
```

## Troubleshooting

### Common Issues

**GPT Doesn't Follow Agent Format**
- Use more explicit formatting instructions
- Include example responses in system prompt
- Break complex agents into smaller, focused prompts

**Inconsistent Responses**
- Set temperature to 0.1-0.3 for more consistent outputs
- Use more specific instructions and examples
- Implement response validation and retry logic

**Token Limits Exceeded**
- Summarize agent instructions
- Split large prompts into multiple requests
- Use function calling for structured interactions

### Best Practices

- **Start Simple** - Begin with basic agent behavior
- **Iterate** - Gradually add complexity and refinement
- **Test Thoroughly** - Validate with real GitHub scenarios
- **Monitor Usage** - Track token usage and optimize costs
- **Version Control** - Keep prompt versions for rollback

## Security Considerations

- **API Keys** - Store securely, rotate regularly
- **Data Privacy** - Be mindful of sensitive GitHub data
- **Rate Limiting** - Implement appropriate limits
- **Input Validation** - Sanitize all inputs
- **Audit Trail** - Log all automated actions

With proper setup, OpenAI integration can provide powerful automation for your GitHub workflows while maintaining the structured behavior of the agent system!