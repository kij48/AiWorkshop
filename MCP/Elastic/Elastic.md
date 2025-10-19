# Elasticsearch MCP Server

> **Model Context Protocol (MCP) Server for Elasticsearch Integration**

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-blue?style=flat-square&logo=github)](https://github.com/kij48/ElasticMcp)
[![Elasticsearch](https://img.shields.io/badge/Elasticsearch-7.x%2B-yellow?style=flat-square&logo=elasticsearch)](https://www.elastic.co/)
[![Node.js](https://img.shields.io/badge/Node.js-16%2B-green?style=flat-square&logo=node.js)](https://nodejs.org/)

## 📋 Overview

This MCP server provides seamless integration with Elasticsearch, enabling AI assistants to search, query, and analyze log data through the Model Context Protocol. Perfect for log analysis, correlation tracking, and observability workflows.

## 🚀 Quick Start

### Prerequisites

- **Node.js** 16.x or higher
- **Elasticsearch** cluster access
- **API Key** with appropriate permissions

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/kij48/ElasticMcp.git
   cd ElasticMcp
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

### Configuration

#### MCP Settings Configuration

Add the following configuration to your MCP settings file:

```json
{
  "elastic": {
    "command": "node",
    "args": ["C:\\repos\\MCP\\ElasticMcp\\index.js"],
    "env": {
      "ELASTICSEARCH_NODE": "https://{name}.es.westeurope.azure.elastic-cloud.com:9243",
      "ELASTICSEARCH_API_KEY": "xxxxx",
      "ELASTICSEARCH_INDEX_PATTERN": ".ds-fasit-apex-*",
      "CORRELATION_ID_FIELD": "fields.CorrelationIdentifier",
      "PII_MASKING_ENABLED": "true",
      "PII_MASK_SSN": "true"
    }
  }
}
```

## ⚙️ Environment Variables

| Variable | Description | Required | Default |
|----------|-------------|----------|---------|
| `ELASTICSEARCH_NODE` | Elasticsearch cluster endpoint URL | ✅ | - |
| `ELASTICSEARCH_API_KEY` | Authentication API key | ✅ | - |
| `ELASTICSEARCH_INDEX_PATTERN` | Index pattern for searches | ✅ | `.ds-fasit-apex-*` |
| `CORRELATION_ID_FIELD` | Field name for correlation tracking | ✅ | `fields.CorrelationIdentifier` |
| `PII_MASKING_ENABLED` | Enable PII data masking | ❌ | `false` |
| `PII_MASK_SSN` | Mask Social Security Numbers | ❌ | `false` |

### 🔐 Setting up Elasticsearch API Key

1. Log into your Elasticsearch cluster
2. Navigate to **Stack Management** → **API Keys**
3. Click **Create API Key**
4. Configure the following privileges:
   - **Cluster**: `monitor`
   - **Index**: `read`, `view_index_metadata` for your target indices

> ⚠️ **Security Note**: Never commit your API key to version control. Use environment variables or secure configuration management.

## 🏗️ Current Deployment Configuration

### Elasticsearch Cluster

- **Endpoint**: `fasit-test-logs.es.westeurope.azure.elastic-cloud.com:9243`
- **Region**: West Europe (Azure)
- **Index Pattern**: `.ds-fasit-apex-*`
- **Correlation Field**: `fields.CorrelationIdentifier`

### Privacy & Security

- **PII Masking**: ✅ Enabled
- **SSN Masking**: ✅ Enabled
- **Secure Connections**: ✅ HTTPS Only

## 📚 Features

- 🔍 **Log Search**: Advanced query capabilities across indices
- 🔗 **Correlation Tracking**: Follow request flows via correlation IDs
- 📊 **Data Analysis**: Aggregate and analyze log patterns
- 🛡️ **PII Protection**: Built-in data masking for sensitive information
- ⚡ **Real-time Queries**: Fast search across large datasets
- 🎯 **Pattern Matching**: Support for complex search patterns
- 📈 **Metrics & Analytics**: Extract insights from log data

## 🛠️ Usage Examples

### Basic Log Search

```javascript
// Search for specific events
await mcp.callTool("search_logs", {
  query: "ERROR",
  index_pattern: ".ds-fasit-apex-*",
  size: 100
});
```

### Correlation ID Tracking

```javascript
// Follow a request through the system
await mcp.callTool("search_by_correlation_id", {
  correlation_id: "abc-123-def-456",
  sort_order: "asc"
});
```

### Custom Query DSL

```javascript
// Advanced Elasticsearch queries
await mcp.callTool("custom_search", {
  query_dsl: {
    "query": {
      "bool": {
        "must": [
          {"match": {"level": "ERROR"}},
          {"range": {"@timestamp": {"gte": "now-1h"}}}
        ]
      }
    }
  }
});
```

## 🔧 Available MCP Tools

| Tool | Description | Parameters |
|------|-------------|------------|
| `search_by_correlation_id` | Search logs by correlation ID | `correlation_id`, `size`, `sort_order` |
| `custom_search` | Execute custom Query DSL | `query_dsl`, `index_pattern`, `size` |
| `get_document` | Retrieve specific document | `index`, `document_id` |
| `get_index_mapping` | Get index field mappings | `index` |
| `list_indices` | List available indices | `pattern` |

## 🏃‍♂️ Running the Server

### Development Mode

```bash
# Start the MCP server locally
node index.js
```

### Production Deployment

```bash
# Set environment variables
export ELASTICSEARCH_NODE="your-cluster-url"
export ELASTICSEARCH_API_KEY="your-api-key"

# Start the server
node index.js
```

## 🧪 Testing

```bash
# Run tests
npm test

# Test connection to Elasticsearch
npm run test:connection
```

## 📊 Monitoring & Observability

### Health Checks

The server provides built-in health monitoring:

- **Elasticsearch Connection**: Automatic connectivity checks
- **Index Availability**: Validates accessible indices
- **Query Performance**: Monitors search latency

### Logging

- **Structured Logging**: JSON format for easy parsing
- **Correlation Tracking**: Request tracing throughout the system
- **Error Handling**: Comprehensive error logging and recovery

## 🤝 Contributing

Contributions are welcome! Please visit the [GitHub repository](https://github.com/kij48/ElasticMcp) for:

- 🐛 Bug reports
- 💡 Feature requests
- 🔄 Pull requests
- 📖 Documentation improvements

### Development Setup

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## 🚨 Troubleshooting

### Common Issues

- **Connection Errors**: Verify your Elasticsearch endpoint and API key
- **Index Not Found**: Check your index pattern configuration
- **PII Masking**: Ensure proper field mapping for sensitive data
- **Performance**: Consider index optimization for large datasets

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/kij48/ElasticMcp/blob/main/LICENSE) file for details.

---

*Last updated: October 2025*