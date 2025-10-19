
# Azure DevOps MCP Server

> **Model Context Protocol (MCP) Server for Azure DevOps Integration**

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-blue?style=flat-square&logo=github)](https://github.com/Tiberriver256/mcp-server-azure-devops)
[![npm package](https://img.shields.io/badge/npm-@tiberriver256/mcp--server--azure--devops-red?style=flat-square&logo=npm)](https://www.npmjs.com/package/@tiberriver256/mcp-server-azure-devops)

## 📋 Overview

This MCP server provides seamless integration with Azure DevOps, enabling AI assistants to interact with your Azure DevOps projects, work items, builds, and more through the Model Context Protocol.

## 🚀 Quick Start

### Installation

The server can be run directly using `npx` without installation:

```bash
npx -y @tiberriver256/mcp-server-azure-devops
```

### Configuration

#### MCP Settings Configuration

Add the following configuration to your MCP settings file:

```json
{
  "DevOps2": {
    "command": "npx",
    "args": ["-y", "@tiberriver256/mcp-server-azure-devops"],
    "env": {
      "AZURE_DEVOPS_ORG_URL": "https://{name}/tfs/SchultzCollection",
      "AZURE_DEVOPS_AUTH_METHOD": "pat",
      "AZURE_DEVOPS_PAT": "xxx",
      "AZURE_DEVOPS_DEFAULT_PROJECT": "Schultz.Fasit",
      "AZURE_DEVOPS_API_VERSION": "7.1-preview.1"
    }
  }
}
```

## ⚙️ Environment Variables

| Variable | Description | Required | Default |
|----------|-------------|----------|---------|
| `AZURE_DEVOPS_ORG_URL` | Your Azure DevOps organization URL | ✅ | - |
| `AZURE_DEVOPS_AUTH_METHOD` | Authentication method (`pat` or `oauth`) | ✅ | `pat` |
| `AZURE_DEVOPS_PAT` | Personal Access Token | ✅ | - |
| `AZURE_DEVOPS_DEFAULT_PROJECT` | Default project name | ✅ | - |
| `AZURE_DEVOPS_API_VERSION` | Azure DevOps API version | ❌ | `7.1-preview.1` |

### 🔐 Setting up Personal Access Token (PAT)

1. Go to your Azure DevOps organization
2. Navigate to **User Settings** → **Personal Access Tokens**
3. Click **New Token**
4. Configure the following scopes:
   - **Work Items**: Read & Write
   - **Build**: Read
   - **Code**: Read
   - **Project and Team**: Read

> ⚠️ **Security Note**: Never commit your PAT to version control. Use environment variables or secure configuration management.

## 🏗️ Project Configuration

### Current Project Setup

- **Organization**: Schultz Collection
- **Server URL**: `https://{Name}/tfs/SchultzCollection`
- **Default Project**: `Schultz.Fasit`
- **API Version**: `7.1-preview.1`

## 📚 Features

- 🔍 **Work Item Management**: Query, create, and update work items
- 🏗️ **Build Integration**: Access build definitions and status
- 📊 **Project Insights**: Retrieve project information and statistics
- 🔄 **Real-time Updates**: Monitor changes and updates
- 🤖 **AI-Friendly**: Optimized for AI assistant interactions



## 🤝 Contributing

Contributions are welcome! Please visit the [GitHub repository](https://github.com/Tiberriver256/mcp-server-azure-devops) for:

- 🐛 Bug reports
- 💡 Feature requests
- 🔄 Pull requests
- 📖 Documentation improvements

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/Tiberriver256/mcp-server-azure-devops/blob/main/LICENSE) file for details.

---

*Last updated: October 2025*