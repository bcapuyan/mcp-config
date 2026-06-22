# MCP Configuration

This repository contains Model Context Protocol (MCP) server configurations for Claude integration.

## Files Included

- **`mcp-config.json`** - Public configuration with all MCP server URLs (no credentials)
- **`mcp-config.local.template.json`** - Template showing how to add authentication
- **`.gitignore`** - Prevents accidental credential commits

## Setup Instructions

### For New Developers

1. **Clone the repo**
   ```bash
   git clone <your-repo-url>
   cd <repo-name>
   ```

2. **Create your local config**
   ```bash
   cp mcp-config.local.template.json mcp-config.local.json
   ```

3. **Add your credentials**
   - Open `mcp-config.local.json`
   - Fill in your ServiceNow username, password, or API tokens
   - Fill in Microsoft 365 OAuth credentials if needed
   - Save locally (this file is ignored by git)

4. **Use in your environment**
   - Reference `mcp-config.json` for the server URLs
   - Use `mcp-config.local.json` for authenticated requests

### Available MCP Servers

| Server | URL | Purpose |
|--------|-----|---------|
| BT1_MCP | buildtools1.service-now.com | Build tools integration |
| CSP MCP | success.servicenow.com | Customer Success Platform |
| Data_Analytics_Connection | apicid.servicenow.com/v1/mcp/edp | Analytics & data retrieval |
| GTM MCP | apicid.servicenow.com/v1/mcp/gtm | Go-to-Market data |
| Marketing MCP | apicid.servicenow.com/v1/mcp/marketing | Marketing operations |
| Microsoft 365 | microsoft365.mcp.claude.com | Microsoft integration |
| Sales Success Center | apicid.servicenow.com/v1/mcp/gtm/semantic-retriever | Sales content retrieval |
| SURF_CORE_MCP | surf.service-now.com | Core SURF platform |
| Usage Insights | apicid.servicenow.com/v1/mcp/uxa-usage-insights | Usage analytics |
| ValueMelody | apicid.servicenow.com/v1/mcp/value-melody | Value analysis |

## Security

⚠️ **IMPORTANT:** 
- Never commit `mcp-config.local.json` to version control
- Never share credentials in chat, PRs, or issues
- Use environment variables for production deployments
- Rotate credentials regularly

The `.gitignore` file prevents accidental commits of credential files.

## Environment Variables (Recommended)

For production or CI/CD, use environment variables:

```bash
export SERVICENOW_USER="your_username"
export SERVICENOW_PASSWORD="your_password"
export MICROSOFT_CLIENT_ID="your_client_id"
export MICROSOFT_CLIENT_SECRET="your_client_secret"
```

Then reference them in your config:
```json
{
  "auth": {
    "username": "${SERVICENOW_USER}",
    "password": "${SERVICENOW_PASSWORD}"
  }
}
```

## Support

For issues or questions about these MCPs:
1. Check the official documentation for each service
2. Contact your ServiceNow or Microsoft account team
3. Open an issue in this repo (without sensitive data)

## License

Add your license here if applicable.
