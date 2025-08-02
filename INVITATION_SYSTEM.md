# 🚀 MCA NITW Organization Invitation System

This repository contains the automated system for managing membership requests to the MCA NITW GitHub Organization.

## 📋 How It Works

### For New Members

1. **Submit a Request**: Use our [Join Request Template](https://github.com/MCA-NITW/.github/issues/new?assignees=&labels=join-request&template=join-request.yml&title=%5BJoin+Request%5D+%40your-username)
2. **Automatic Processing**: Our bot will attempt to send an invitation automatically
3. **Receive Invitation**: Check your email for the GitHub organization invitation
4. **Accept & Join**: Click the invitation link and start contributing!

### For Administrators

The system provides both automatic and manual invitation capabilities:

#### Automatic Invitations

- Triggered when a `join-request` label is added to an issue
- Extracts username from issue title or body
- Sends invitation via GitHub API
- Posts status comment with next steps

#### Manual Commands

Administrators can use these commands in issue comments:

- `/manual-invite @username` - Manually send invitation to specific user
- `/approve` - Approve a request and trigger automatic invitation

## 🔧 Setup Instructions

### Prerequisites

1. **Organization Permissions**: You need to be an organization owner or have appropriate permissions
2. **Personal Access Token**: Create a token with `admin:org` scope
3. **Repository Secrets**: Configure the required secrets

### Configuration Steps

#### 1. Create Personal Access Token

1. Go to GitHub Settings > Developer settings > Personal access tokens
2. Click "Generate new token (classic)"
3. Select the following scopes:
   - `admin:org` (for sending invitations)
   - `repo` (for accessing repository)
4. Copy the generated token

#### 2. Add Repository Secrets

Add these secrets to your repository (Settings > Secrets and variables > Actions):

- `ORG_INVITE_TOKEN`: Your personal access token from step 1

#### 3. Create Required Labels

Ensure these labels exist in your repository:

- `join-request` (automatically applied by template)
- `invite-sent` (added when invitation is successful)
- `invite-failed` (added when invitation fails)
- `pending-review` (for manual review cases)

You can create them via GitHub UI or use this command:

```bash
# Create labels via GitHub CLI
gh label create "join-request" --color "0052cc" --description "Request to join organization"
gh label create "invite-sent" --color "28a745" --description "Organization invitation sent"
gh label create "invite-failed" --color "d73a49" --description "Failed to send invitation"
gh label create "pending-review" --color "fbca04" --description "Requires manual review"
```

### 4. Enable Issues

Make sure issues are enabled in your repository settings.

## 📁 File Structure

```text
.github/
├── ISSUE_TEMPLATE/
│   ├── join-request.yml      # Join request form template
│   └── config.yml           # Issue template configuration
├── workflows/
│   └── auto-invite.yml      # GitHub Actions workflow
└── profile/
    └── README.md            # Organization profile with join instructions
```

## 🔍 How the Automation Works

### Workflow Triggers

The GitHub Actions workflow (`auto-invite.yml`) is triggered by:

1. **Label Addition**: When `join-request` label is added to an issue
2. **Comment Creation**: When specific commands are used in comments

### Processing Steps

1. **Label Check**: Verifies the issue has the `join-request` label
2. **Username Extraction**: Extracts GitHub username from:
   - Issue title (format: `[Join Request] @username`)
   - Issue body (from the form field)
3. **API Call**: Sends organization invitation via GitHub API
4. **Status Update**:
   - Adds appropriate status label
   - Posts comment with next steps or error message

### Error Handling

- Invalid usernames
- API rate limits
- Network issues
- Permission problems

## 🛠️ Troubleshooting

### Common Issues

#### 1. Token Permissions

**Error**: "Resource not accessible by integration"
**Solution**: Ensure your token has `admin:org` scope

#### 2. User Already Member

**Error**: User is already a member
**Solution**: Check organization members list

#### 3. Invalid Username

**Error**: User not found
**Solution**: Verify the username is correct

#### 4. Rate Limiting

**Error**: API rate limit exceeded
**Solution**: Wait and retry, or implement rate limiting

### Manual Intervention

If automation fails, administrators can:

1. **Use Manual Command**: Comment `/manual-invite @username`
2. **Send Direct Invitation**: Use GitHub's organization settings
3. **Check Logs**: Review workflow logs for detailed error information

## 📊 Monitoring & Analytics

### Tracking Invitations

- Monitor workflow runs in the Actions tab
- Check issue labels for status tracking
- Review comment history for invitation confirmations

### Metrics to Track

- Number of join requests per month
- Success rate of automatic invitations
- Time from request to acceptance
- Most common failure reasons

## 🔒 Security Considerations

### Token Security

- Use repository secrets for tokens
- Regularly rotate access tokens
- Monitor token usage in organization audit logs

### Spam Prevention

- Form validation in issue template
- Manual review for suspicious requests
- Rate limiting on invitation endpoints

### Access Control

- Only organization members can use manual commands
- Workflow permissions are restricted
- Regular review of organization members

## 🤝 Contributing to This System

### Improving the Template

- Update form fields in `join-request.yml`
- Add validation rules
- Enhance user experience

### Enhancing Automation

- Add more sophisticated username extraction
- Implement retry logic for failed invitations
- Add notification integrations (Slack, Discord)

### Documentation

- Update this README for any changes
- Add troubleshooting guides
- Create video tutorials

## 📞 Support

### Support for New Members

- Comment on your join request issue
- Ask in [organization discussions](https://github.com/orgs/MCA-NITW/discussions)
- Contact administrators

### Support for Administrators

- Check GitHub Actions logs
- Review repository issues
- Consult GitHub's API documentation

## 📝 License

This automation system is open source and available for other organizations to adapt and use.

---

**Need help?** Open an issue or start a discussion in our community forums!
