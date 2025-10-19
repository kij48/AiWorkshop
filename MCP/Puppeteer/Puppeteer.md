# Puppeteer MCP Server

> **Model Context Protocol (MCP) Server for Browser Automation with Puppeteer**

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-blue?style=flat-square&logo=github)](https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer)
[![Puppeteer](https://img.shields.io/badge/Puppeteer-Latest-green?style=flat-square&logo=puppeteer)](https://pptr.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green?style=flat-square&logo=node.js)](https://nodejs.org/)

## 📋 Overview

The Puppeteer MCP server enables AI assistants to interact with web pages through browser automation. It provides tools for web scraping, automated testing, PDF generation, and general browser automation tasks through the Model Context Protocol.

## 🚀 Quick Start

### Prerequisites

- **Node.js** 18.x or higher
- **Chrome/Chromium** browser (automatically installed with Puppeteer)
- **Sufficient disk space** for browser installation (~300MB)

### Installation

#### Option 1: Using npx (Recommended)

```bash
npx @modelcontextprotocol/server-puppeteer
```

#### Option 2: Global Installation

```bash
npm install -g @modelcontextprotocol/server-puppeteer
```

### Configuration

#### MCP Settings Configuration

Add the following configuration to your MCP settings file:

```json
{
  "puppeteer": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-puppeteer"],
    "env": {
      "PUPPETEER_HEADLESS": "true",
      "PUPPETEER_SLOWMO": "0",
      "PUPPETEER_TIMEOUT": "30000",
      "PUPPETEER_VIEWPORT_WIDTH": "1920",
      "PUPPETEER_VIEWPORT_HEIGHT": "1080",
      "PUPPETEER_USER_AGENT": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
    }
  }
}
```


## ⚙️ Environment Variables

| Variable | Description | Required | Default |
|----------|-------------|----------|---------|
| `PUPPETEER_HEADLESS` | Run browser in headless mode | ❌ | `true` |
| `PUPPETEER_SLOWMO` | Slow down operations (ms) | ❌ | `0` |
| `PUPPETEER_TIMEOUT` | Default timeout for operations (ms) | ❌ | `30000` |
| `PUPPETEER_VIEWPORT_WIDTH` | Browser viewport width | ❌ | `1920` |
| `PUPPETEER_VIEWPORT_HEIGHT` | Browser viewport height | ❌ | `1080` |
| `PUPPETEER_USER_AGENT` | Custom user agent string | ❌ | Default Chrome UA |
| `PUPPETEER_EXECUTABLE_PATH` | Custom Chrome/Chromium path | ❌ | Auto-detected |
| `PUPPETEER_DISABLE_WEB_SECURITY` | Disable web security features | ❌ | `false` |

### 🔧 Advanced Configuration

#### Launch Options

```json
{
  "puppeteer": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-puppeteer"],
    "env": {
      "PUPPETEER_LAUNCH_OPTIONS": "{\"headless\": false, \"devtools\": true, \"args\": [\"--no-sandbox\", \"--disable-setuid-sandbox\"]}"
    }
  }
}
```

#### Security Settings

For development environments, you might need additional Chrome flags:

```json
{
  "PUPPETEER_CHROME_ARGS": "[\"--no-sandbox\", \"--disable-setuid-sandbox\", \"--disable-dev-shm-usage\", \"--disable-accelerated-2d-canvas\", \"--no-first-run\", \"--no-zygote\", \"--single-process\", \"--disable-gpu\"]"
}
```

## 🏗️ Current Setup Recommendations

### Development Environment

- **Headless Mode**: `false` (for debugging)
- **Slow Motion**: `100ms` (easier to follow actions)
- **DevTools**: `true` (for inspection)
- **Viewport**: `1920x1080` (standard desktop)

### Production Environment

- **Headless Mode**: `true` (performance)
- **Slow Motion**: `0ms` (maximum speed)
- **Timeout**: `30000ms` (30 seconds)
- **Memory Optimization**: Enable garbage collection flags

## 📚 Features

- 🌐 **Web Navigation**: Navigate to URLs and handle page loads
- 🖱️ **Element Interaction**: Click, type, hover, and form filling
- 📸 **Screenshots**: Capture full pages or specific elements
- 📄 **PDF Generation**: Convert web pages to PDF documents
- 🔍 **Web Scraping**: Extract data from web pages
- 📱 **Mobile Emulation**: Simulate mobile devices and viewports
- 🍪 **Cookie Management**: Handle authentication and sessions
- 📋 **Form Automation**: Fill and submit forms automatically
- ⏱️ **Wait Strategies**: Smart waiting for dynamic content
- 🧪 **Testing Support**: Automated UI testing capabilities

## 🛠️ Available MCP Tools

| Tool | Description | Parameters |
|------|-------------|------------|
| `puppeteer_navigate` | Navigate to a URL | `url`, `launchOptions?`, `allowDangerous?` |
| `puppeteer_click` | Click an element | `selector` |
| `puppeteer_fill` | Fill an input field | `selector`, `value` |
| `puppeteer_screenshot` | Take a screenshot | `name`, `selector?`, `width?`, `height?`, `encoded?` |
| `puppeteer_select` | Select from dropdown | `selector`, `value` |
| `puppeteer_hover` | Hover over element | `selector` |
| `puppeteer_evaluate` | Execute JavaScript | `script` |

## 🔨 Usage Examples

### Basic Web Navigation

```javascript
// Navigate to a website
await mcp.callTool("puppeteer_navigate", {
  url: "https://example.com"
});

// Take a screenshot
await mcp.callTool("puppeteer_screenshot", {
  name: "homepage",
  width: 1920,
  height: 1080
});
```

### Form Automation

```javascript
// Fill out a login form
await mcp.callTool("puppeteer_fill", {
  selector: "#username",
  value: "user@example.com"
});

await mcp.callTool("puppeteer_fill", {
  selector: "#password",
  value: "securepassword"
});

await mcp.callTool("puppeteer_click", {
  selector: "button[type=submit]"
});
```

### Data Extraction

```javascript
// Extract data using JavaScript
await mcp.callTool("puppeteer_evaluate", {
  script: `
    const titles = Array.from(document.querySelectorAll('h2'))
      .map(h2 => h2.textContent.trim());
    return titles;
  `
});
```

### Advanced Interactions

```javascript
// Hover over an element to reveal dropdown
await mcp.callTool("puppeteer_hover", {
  selector: ".menu-item"
});

// Select from dropdown
await mcp.callTool("puppeteer_select", {
  selector: "#country-select",
  value: "US"
});

// Take screenshot of specific element
await mcp.callTool("puppeteer_screenshot", {
  name: "dropdown-menu",
  selector: ".dropdown-menu"
});
```

## 🏃‍♂️ Running the Server

### Development Mode

```bash
# Run with debug output
DEBUG=* npx @modelcontextprotocol/server-puppeteer

# Run with custom options
PUPPETEER_HEADLESS=false npx @modelcontextprotocol/server-puppeteer
```

### Docker Deployment

```dockerfile
FROM node:18-alpine

# Install Chrome dependencies
RUN apk add --no-cache \
    chromium \
    nss \
    freetype \
    freetype-dev \
    harfbuzz \
    ca-certificates \
    ttf-freefont

# Set Chrome path
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium-browser

# Install MCP server
RUN npm install -g @modelcontextprotocol/server-puppeteer

CMD ["npx", "@modelcontextprotocol/server-puppeteer"]
```

## 🧪 Testing

### Basic Connection Test

```bash
# Test server startup
npx @modelcontextprotocol/server-puppeteer --test

# Test browser launch
node -e "
const puppeteer = require('puppeteer');
(async () => {
  const browser = await puppeteer.launch();
  console.log('Browser launched successfully!');
  await browser.close();
})();
"
```

### Integration Testing

```javascript
// Test MCP tool calls
const testNavigation = async () => {
  await mcp.callTool("puppeteer_navigate", {
    url: "https://httpbin.org/html"
  });
  
  const screenshot = await mcp.callTool("puppeteer_screenshot", {
    name: "test-page"
  });
  
  console.log("Navigation test passed!");
};
```

## 📊 Performance Optimization

### Memory Management

```javascript
// Launch options for memory optimization
{
  "launchOptions": {
    "args": [
      "--memory-pressure-off",
      "--max_old_space_size=4096",
      "--disable-dev-shm-usage",
      "--disable-extensions"
    ]
  }
}
```

### Speed Optimization

```javascript
// Disable unnecessary features
{
  "launchOptions": {
    "args": [
      "--disable-web-security",
      "--disable-features=TranslateUI",
      "--disable-ipc-flooding-protection",
      "--disable-background-timer-throttling",
      "--disable-backgrounding-occluded-windows",
      "--disable-renderer-backgrounding"
    ]
  }
}
```

## 🚨 Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| **Chrome won't launch** | Install missing dependencies: `apt-get install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget` |
| **Permission denied** | Add `--no-sandbox` to Chrome args |
| **Screenshots empty** | Wait for page load before taking screenshot |
| **Elements not found** | Use proper wait strategies and selectors |
| **Memory issues** | Enable memory optimization flags |

### Debugging Tips

```bash
# Enable verbose logging
DEBUG=puppeteer:* npx @modelcontextprotocol/server-puppeteer

# Run in non-headless mode for debugging
PUPPETEER_HEADLESS=false npx @modelcontextprotocol/server-puppeteer

# Check Chrome installation
node -e "console.log(require('puppeteer').executablePath())"
```

## 🔒 Security Considerations

### Safe Browsing

- **Never navigate to untrusted URLs** without proper validation
- **Sanitize user inputs** before using in selectors or scripts
- **Use allowlist approach** for allowed domains
- **Disable dangerous Chrome flags** in production

### Network Security

```json
{
  "launchOptions": {
    "args": [
      "--disable-web-security",
      "--disable-plugins",
      "--disable-extensions",
      "--disable-images"
    ]
  }
}
```

## 🤝 Contributing

The Puppeteer MCP server is part of the official MCP servers collection. Contributions are welcome!

- 🐛 **Bug Reports**: [GitHub Issues](https://github.com/modelcontextprotocol/servers/issues)
- 💡 **Feature Requests**: [GitHub Discussions](https://github.com/modelcontextprotocol/servers/discussions)
- 🔄 **Pull Requests**: Follow the contribution guidelines
- 📖 **Documentation**: Help improve this guide

### Development Setup

```bash
git clone https://github.com/modelcontextprotocol/servers.git
cd servers/src/puppeteer
npm install
npm run build
npm run test
```

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/modelcontextprotocol/servers/blob/main/LICENSE) file for details.

## 🔗 Related Resources

- 📚 [Puppeteer Documentation](https://pptr.dev/)
- 🏠 [MCP Protocol Specification](https://modelcontextprotocol.io/)
- 🛠️ [MCP Servers Collection](https://github.com/modelcontextprotocol/servers)
- 🎥 [Browser Automation Best Practices](https://developers.google.com/web/tools/puppeteer/articles/puppeteer-performance)

---

*Last updated: October 2025*