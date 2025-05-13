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

### Available Commands

```bash
# Setup your server configuration
npx ai-collaboration-mcp-server setup

# Purchase a license
npx ai-collaboration-mcp-server buy

# Check your license status
npx ai-collaboration-mcp-server status

# Start the MCP server
npx ai-collaboration-mcp-server start

# Install dependencies
npx ai-collaboration-mcp-server install
```

## 🔧 AI Tool Setup

### Setting Up Claude Code

Claude Code comes with built-in MCP support that makes integration straightforward:

1. Open Claude Code in your terminal:
   ```bash
   claude-code
   ```

2. Configure MCP connection:
   ```bash
   /mcp config
   /mcp add-server
   ```

3. When prompted, enter:
   - Server name: "AI Collaboration MCP Server"
   - Server URL: http://localhost:3000/mcp (or your custom URL)
   - License key: Your license key
   - Role: backend_dev (or your preferred role)

4. Connect to the server:
   ```bash
   /mcp connect "AI Collaboration MCP Server"
   ```

5. Use MCP tools:
   ```bash
   /mcp list-tools
   /mcp invoke create-task --title "Implement API" --description "Create REST API endpoint" --type "backend" --priority "high"
   ```

### Setting Up Cursor

Cursor can be configured through its extension system:

1. Open Cursor and go to Settings > Extensions

2. Add a new MCP connection with:
   - Name: AI Collaboration MCP Server
   - URL: http://localhost:3000/mcp
   - Headers:
     ```json
     {
       "x-license-key": "your-license-key"
     }
     ```
   - Default role: frontend_dev (or your preferred role)

3. Access MCP tools through Cursor's command palette (Ctrl+Shift+P or Cmd+Shift+P):
   ```
   MCP: List Available Tools
   MCP: Invoke Tool
   MCP: Get Tasks
   ```

### Setting Up Windsurf

Windsurf connects via its plugin system:

1. Create a configuration file:
   ```bash
   mkdir -p ~/.windsurf/plugins
   touch ~/.windsurf/plugins/mcp-collaboration.json
   ```

2. Add the following configuration:
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
       "defaultRole": "architect",
       "autoConnect": true
     }
   }
   ```

3. Restart Windsurf to load the plugin

4. Access MCP functionality:
   ```
   /mcp list-tools
   /mcp get-tasks
   /mcp create-task
   ```

For more detailed setup instructions and troubleshooting, see our [AI Tool Integration Guide](https://github.com/will380/ai-collaboration-mcp-server/blob/main/docs/ai-tool-integration.md).

## 💰 Pricing

We offer flexible pricing options to suit teams of all sizes:

<table align="center">
  <tr>
    <th>Plan</th>
    <th>Price</th>
    <th>Features</th>
  </tr>
  <tr>
    <td><b>Monthly Subscription</b></td>
    <td>$9.99/month</td>
    <td>
      - Full MCP server access<br>
      - API access<br>
      - Up to 10 projects<br>
      - Email support
    </td>
  </tr>
  <tr>
    <td><b>Annual Subscription</b></td>
    <td>$99.99/year<br><small>(Save 17%)</small></td>
    <td>
      - Full MCP server access<br>
      - API access<br>
      - Unlimited projects<br>
      - Priority email support
    </td>
  </tr>
  <tr>
    <td><b>Lifetime License</b></td>
    <td>$299.99<br><small>(One-time payment)</small></td>
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

- [Installation Guide](https://github.com/will380/ai-collaboration-mcp-server/blob/main/docs/installation.md)
- [AI Tool Integration Guide](https://github.com/will380/ai-collaboration-mcp-server/blob/main/docs/ai-tool-integration.md)
- [API Reference](https://github.com/will380/ai-collaboration-mcp-server/blob/main/docs/api-reference.md)
- [License Management](https://github.com/will380/ai-collaboration-mcp-server/blob/main/docs/license-management.md)

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