# AI Workshop

> **Comprehensive collection of AI development tools, MCP servers, and productivity resources**

[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-blue?style=flat-square)](https://modelcontextprotocol.io/)
[![Azure DevOps](https://img.shields.io/badge/Azure%20DevOps-Integration-0078d7?style=flat-square&logo=azuredevops)](https://azure.microsoft.com/en-us/products/devops)
[![Elasticsearch](https://img.shields.io/badge/Elasticsearch-Logging-yellow?style=flat-square&logo=elasticsearch)](https://www.elastic.co/)
[![Puppeteer](https://img.shields.io/badge/Puppeteer-Automation-green?style=flat-square&logo=puppeteer)](https://pptr.dev/)

## 📋 Overview

This repository contains a curated collection of AI development tools, Model Context Protocol (MCP) server configurations, and productivity resources designed to enhance development workflows with AI assistance.

## 🗂️ Repository Structure

```
AiWorkshop/
├── 📁 MCP/                    # Model Context Protocol Servers
│   ├── DevOps/               # Azure DevOps MCP Server
│   ├── Elastic/              # Elasticsearch MCP Server  
│   └── Puppeteer/            # Browser Automation MCP Server
├── 📁 Prompts/               # AI Assistant Prompts & Templates
│   └── implement.md          # Development workflow instructions
└── 📄 README.md              # This file
```

## 🚀 Quick Start

### Prerequisites

- **Node.js** 18.x or higher
- **Git** for version control
- **VS Code** or **Cursor** (recommended)
- **AI Assistant** (GitHub Copilot, Claude, or equivalent)

### Setup

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd AiWorkshop
   ```

2. **Choose your MCP servers:**
   - Browse the `MCP/` directory
   - Follow individual setup guides for each server

3. **Configure AI prompts:**
   - Use prompts from `Prompts/` directory
   - Follow the AI setup guide for your preferred assistant

## 🔧 MCP Servers

### Available Servers

| Server | Purpose | Status | Documentation |
|--------|---------|--------|---------------|
| **Azure DevOps** | Work items, builds, project management | ✅ Ready | [Setup Guide](./MCP/DevOps/DevOps.md) |
| **Elasticsearch** | Log search, correlation tracking, analytics | ✅ Ready | [Setup Guide](./MCP/Elastic/Elastic.md) |
| **Puppeteer** | Browser automation, web scraping, testing | ✅ Ready | [Setup Guide](./MCP/Puppeteer/Puppeteer.md) |

### Installation Overview

Each MCP server can be installed using one of these methods:

```bash
# Method 1: Direct npx execution (recommended)
npx -y @package/mcp-server-name

# Method 2: Local installation
npm install -g @package/mcp-server-name

# Method 3: Development setup
git clone <server-repo>
cd server && npm install && npm run build
```

### Configuration Template

Add servers to your MCP settings file:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "@package/mcp-server-name"],
      "env": {
        "API_KEY": "your-api-key",
        "SERVER_URL": "your-server-url"
      }
    }
  }
}
```

## 📝 AI Prompts & Templates

### Development Workflow Prompts

The `Prompts/` directory contains structured development prompts:

| File | Purpose | Usage |
|------|---------|-------|
| `implement.md` | Structured development workflow | AI implementation tasks |

### Workflow Phases

All prompts follow a structured 4-phase approach:

1. **🔍 ANALYZE** - Understand requirements and codebase
2. **📋 PLAN** - Create implementation plan and checklist  
3. **⚡ EXECUTE** - Write clean, documented code
4. **🧪 TEST** - Verify quality and functionality

### AI Assistant Integration

- **VS Code**: Place prompts in `%APPDATA%\Code\User\prompts\`
- **Claude**: Use as Project Instructions with slash commands
- **Cursor**: Configure via `.cursorrules` file

## 🛠️ Development Tools Integration

### Supported AI Assistants

| Assistant | Integration Type | Features |
|-----------|------------------|----------|
| **GitHub Copilot** | Native VS Code | Custom instructions, chat integration |
| **Claude** | Web/API | Project instructions, slash commands |
| **Cursor AI** | Built-in editor | Rules-based configuration |

### Recommended Setup

1. **Choose your primary AI assistant**
2. **Install relevant MCP servers** based on your tech stack  
3. **Configure development prompts** for consistent workflows
4. **Set up project-specific rules** in `.cursorrules` or VS Code settings

## 📊 Use Cases

### DevOps & Project Management
- **Work item tracking** with Azure DevOps MCP
- **Build status monitoring** and automation
- **Sprint planning** and task management

### Observability & Debugging  
- **Log analysis** with Elasticsearch MCP
- **Correlation tracking** across microservices
- **Performance monitoring** and alerting

### Testing & Automation
- **Browser automation** with Puppeteer MCP
- **End-to-end testing** workflows
- **Web scraping** and data extraction

### Development Workflows
- **Structured implementation** using AI prompts
- **Code review automation** with quality checks
- **Documentation generation** and maintenance

## 🚀 Getting Started Examples

### Example 1: Azure DevOps Integration

```bash
# Install Azure DevOps MCP server
npx -y @tiberriver256/mcp-server-azure-devops

# Configure environment variables
export AZURE_DEVOPS_ORG_URL="https://your-org.visualstudio.com"
export AZURE_DEVOPS_PAT="your-personal-access-token"
export AZURE_DEVOPS_DEFAULT_PROJECT="your-project"

# Use with AI assistant
# Ask: "Show me all active work items in current sprint"
```

### Example 2: Log Analysis with Elasticsearch

```bash
# Configure Elasticsearch MCP server
export ELASTICSEARCH_NODE="https://your-cluster.es.cloud.com:9243"
export ELASTICSEARCH_API_KEY="your-api-key"
export ELASTICSEARCH_INDEX_PATTERN=".ds-logs-*"

# Use with AI assistant  
# Ask: "Find all ERROR logs from the last hour for correlation ID abc-123"
```

### Example 3: Browser Automation

```bash
# Install Puppeteer MCP server
npx -y @modelcontextprotocol/server-puppeteer

# Use with AI assistant
# Ask: "Navigate to example.com, fill the login form, and take a screenshot"
```

## 📚 Documentation

### Individual Server Guides

- **[Azure DevOps MCP](./MCP/DevOps/DevOps.md)** - Complete setup and configuration
- **[Elasticsearch MCP](./MCP/Elastic/Elastic.md)** - Log analysis and search capabilities  
- **[Puppeteer MCP](./MCP/Puppeteer/Puppeteer.md)** - Browser automation and testing

### Development Resources

- **[Implementation Prompts](./Prompts/implement.md)** - Structured development workflows
- **[AI Setup Guide](./Prompts/ai-setup-guide.md)** - Configure AI assistants with custom prompts

## 🤝 Contributing

We welcome contributions to expand this AI development toolkit!

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/new-mcp-server`
3. **Add your MCP server or prompt**: Follow existing structure
4. **Update documentation**: Include setup guide and examples
5. **Submit a pull request**: Describe your changes and benefits

### Contribution Areas

- 🔌 **New MCP Servers** - Additional integrations and tools
- 📝 **Prompt Templates** - Specialized development workflows  
- 📖 **Documentation** - Setup guides and best practices
- 🐛 **Bug Fixes** - Configuration and compatibility issues
- ✨ **Enhancements** - Improved features and usability

## 🔧 Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| **MCP server won't start** | Check Node.js version (18+), verify environment variables |
| **Authentication failures** | Validate API keys and tokens, check permissions |
| **Port conflicts** | Update server configurations, use different ports |
| **AI assistant not responding** | Restart assistant, check MCP server status |

### Debug Commands

```bash
# Check Node.js version
node --version

# Test MCP server connectivity
npx @package/mcp-server-name --test

# View server logs
DEBUG=* npx @package/mcp-server-name

# Validate configuration
cat .cursorrules
cat .vscode/settings.json
```

## 📄 License

This project is licensed under the MIT License - see individual MCP servers for their specific licenses.

## 🔗 Related Resources

- 🏠 **[Model Context Protocol](https://modelcontextprotocol.io/)** - Official MCP documentation
- 🛠️ **[MCP Servers Collection](https://github.com/modelcontextprotocol/servers)** - Official server implementations
- 📚 **[AI Development Best Practices](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/)** - GitHub's prompt engineering guide
- 🎯 **[Cursor AI Documentation](https://docs.cursor.sh/)** - Cursor-specific features and setup

---

## 🎯 Next Steps

1. **Explore MCP servers** - Review available integrations
2. **Configure your AI assistant** - Set up prompts and commands  
3. **Start with a simple project** - Try Azure DevOps or Elasticsearch integration
4. **Join the community** - Contribute and share your experiences

*Last updated: October 2025*