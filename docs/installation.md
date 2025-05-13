# Installation Guide

This guide walks you through the process of installing and setting up the AI Collaboration MCP Server.

## Prerequisites

- Node.js 18.x or later
- npm 8.x or later

## Quick Installation with NPX

The quickest way to get started is using our npx command:

```bash
# Install the package globally
npm install -g ai-collaboration-mcp-server

# Or use it directly with npx
npx ai-collaboration-mcp-server
```

## Commands Overview

The MCP client provides several commands:

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

## Setup Process

1. Run the setup command:

```bash
npx ai-collaboration-mcp-server setup
```

2. Follow the prompts to configure:
   - Server port (default: 3000)
   - Server host (default: localhost)
   - HTTP/HTTPS preference
   - License key (if available)

This will create a `.env` file with your configuration.

## License Purchase

To buy a license:

```bash
npx ai-collaboration-mcp-server buy
```

This will:
1. Display available plans
2. Let you select a plan
3. Open a secure Stripe checkout page in your browser
4. Email you a license key upon successful payment

## Starting the Server

After setup, start your server:

```bash
npx ai-collaboration-mcp-server start
```

Or with custom options:

```bash
npx ai-collaboration-mcp-server start --port 8080 --host 0.0.0.0 --http
```

## Manual Installation

If you prefer to manually install:

1. Clone the repository
2. Install dependencies:

```bash
git clone https://github.com/will380/ai-collaboration-mcp-server.git
cd ai-collaboration-mcp-server
npm install
```

3. Set up your environment by creating a `.env` file:

```
# Server configuration
PORT=3000
HOST=localhost
USE_HTTP=true
LICENSE_KEY=your-license-key-if-available
```

4. Start the server:

```bash
npm start
```

## Checking License Status

To check your license status:

```bash
npx ai-collaboration-mcp-server status
```

This will display:
- License validity
- Plan type
- Customer information
- Expiration date

## Next Steps

- [Configure your server](configuration.md)
- [Set up roles for AI tools](role-based-access.md)
- [Create your first task](task-management.md)