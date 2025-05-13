---
layout: default
title: AI Collaboration MCP Server
---

# AI Collaboration MCP Server

<p align="center">
  <b>Coordinate between Claude Code, Cursor, Windsurf, and other AI tools as a collaborative development team</b>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#getting-started">Getting Started</a> •
  <a href="#ai-tool-setup">AI Tool Setup</a> •
  <a href="#pricing">Pricing</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support">Support</a>
</p>

---

## 🚀 Supercharge Your AI Development Team

The AI Collaboration MCP Server is a powerful Model Context Protocol (MCP) server designed to enable seamless collaboration between different AI tools. It creates a virtual development team where each AI agent can contribute its unique strengths to your project.

## ⚙ Features

- **Task Management System**: Create, assign, and track tasks between AI tools
- **Role-Based Collaboration**: Assign specialized roles (frontend, backend, etc.) to different AI agents
- **Conflict Resolution**: Sophisticated system to prevent AI tools from stepping on each other's toes
- **Message Exchange**: Enable direct communication between AI agents for better coordination
- **License Management**: Enterprise-grade licensing system with Stripe integration
- **Secure Storage**: All data is securely stored with proper authentication

## 🚀 Getting Started

### Quick Start with NPX

The fastest way to get started is with our NPX command:

```bash
# Install globally
npm install -g ai-collaboration-mcp-server

# Or use directly with npx
npx ai-collaboration-mcp-server

# Setup with your configuration
npx ai-collaboration-mcp-server setup

# Buy a license
npx ai-collaboration-mcp-server buy

# Start the server
npx ai-collaboration-mcp-server start
```

## 🔧 AI Tool Setup

### Claude Code Setup

```bash
# In Claude Code terminal
/mcp config
/mcp add-server
# Enter server URL and license key when prompted
/mcp connect "AI Collaboration MCP Server"
```

### Cursor Setup

Open Cursor Settings > Extensions and add a new MCP connection with:
- URL: http://localhost:3000/mcp
- Headers: `{"x-license-key": "your-license-key"}`

### Windsurf Setup

Create `~/.windsurf/plugins/mcp-collaboration.json` with:
```json
{
  "name": "AI Collaboration MCP Server",
  "type": "mcp",
  "enabled": true,
  "config": {
    "url": "http://localhost:3000/mcp",
    "headers": {
      "x-license-key": "your-license-key"
    },
    "defaultRole": "architect"
  }
}
```

For full setup details, see our [AI Tool Integration Guide](ai-tool-integration.md).

## 💰 Pricing

We offer flexible pricing options to suit teams of all sizes:

<table align="center">
  <tr>
    <th>Plan</th>
    <th>Price</th>
    <th>Features</th>
  </tr>
  <tr>
    <td><b>Monthly</b></td>
    <td>$9.99/month</td>
    <td>
      - Full MCP server access<br>
      - API access<br>
      - Up to 10 projects<br>
      - Email support
    </td>
  </tr>
  <tr>
    <td><b>Annual</b></td>
    <td>$99.99/year<br><small>(Save 17%)</small></td>
    <td>
      - Full MCP server access<br>
      - API access<br>
      - Unlimited projects<br>
      - Priority email support
    </td>
  </tr>
  <tr>
    <td><b>Lifetime</b></td>
    <td>$299.99<br><small>(One-time)</small></td>
    <td>
      - Full MCP server access<br>
      - API access<br>
      - Unlimited projects<br>
      - Priority support<br>
      - All future updates
    </td>
  </tr>
</table>

## 📖 Documentation

Comprehensive documentation is available for all aspects of the MCP server:

- [Installation Guide](installation.md)
- [AI Tool Integration Guide](ai-tool-integration.md)
- [API Reference](api-reference.md)
- [License Management](license-management.md)

## 👨‍💻 Example Usage

Here's a simple example of how to use the MCP server:

```javascript
// Connect to the MCP server
const transport = new HttpClientTransport({
  url: 'http://localhost:3000/mcp',
  headers: {
    'x-license-key': 'your-license-key'
  }
});

const client = new McpClient();
await client.connect(transport);

// Create a task for the AI team
const result = await client.invoke('create-task', {
  title: 'Build login page',
  description: 'Create a React login page with email and password fields',
  type: 'frontend',
  priority: 'high',
  assignee: 'cursor' // Assign to Cursor
});

// Send a message to Cursor
await client.invoke('send-message', {
  from: 'claude-code',
  to: 'cursor',
  message: 'Please focus on responsive design for the login page',
  taskId: result.data.task.id
});
```

## 👨‍💻 Support

We're here to help you get the most out of your AI collaboration:

- [Documentation](https://github.com/will380/ai-collaboration-mcp-server/tree/main/docs)
- [Email Support](mailto:support@example.com)
- [Discord Community](https://discord.gg/example)

## 📄 License

This package is provided to customers upon purchase of a license. All usage is subject to our [Terms of Service](https://github.com/will380/ai-collaboration-mcp-server/blob/main/docs/terms.md).

---

<p align="center">
  <small>© 2025 AI Collaboration MCP Server. All rights reserved.</small>
</p>