# Module 13 Completion Report

## MCP Configuration
```json
{
  "servers": {
    "echo-windows": {
      "command": "powershell",
      "args": [
        "-NoProfile",
        "-ExecutionPolicy",
        "Bypass",
        "-File",
        "C:/Users/JogeswaraKore/OneDrive - EPAM/My_Workspace/mgr.ai.ws/hello-genai/.vscode/mcp-echo.ps1"
      ]
    },
    "jira": {
      "command": "C:/Program Files/nodejs/npm.cmd",
      "args": [
        "exec",
        "-y",
        "@nexus2520/jira-mcp-server"
      ],
      "env": {
        "JIRA_BASE_URL": "https://jiraeu.epam.com/secure/Dashboard.jspa",
        "JIRA_EMAIL": "jogeswara_kore@epam.com",
        "JIRA_API_TOKEN": "[REDACTED]",
        "JIRA_PROJECT_KEY": "EPMICMPMD",
        "PATH": "C:/Program Files/nodejs;C:/Windows/System32;C:/Windows"
      }
    }
  }
}
```

## Configured Servers
- echo-windows
- jira

## MCP Tool Test
- Tool used: mcp_jira-mcp-serv_jira_search
- Output:
```text
Error: Jira API Error (500):
Request failed with status code 500
```
