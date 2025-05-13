# Installation Guide

This guide walks you through the process of installing and setting up the AI Collaboration MCP Server.

## Prerequisites

- Node.js 16.x or later
- npm 8.x or later
- A Stripe account (for payment processing)
- A Supabase account (for database)

## Quick Installation with NPX

The quickest way to get started is using our npx command:

```bash
# Install and run in trial mode
npx ai-collaboration-mcp-server install
```

This will walk you through the installation process interactively, asking for:

- Installation directory
- Port number for the server
- Environment variables

## Manual Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/your-private-repo.git
cd your-private-repo
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the root directory with the following variables:

```
# Supabase configuration
SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_KEY=your-supabase-key

# JWT configuration
JWT_SECRET=your-jwt-secret

# Stripe configuration
STRIPE_SECRET_KEY=your-stripe-secret-key
STRIPE_WEBHOOK_SECRET=your-stripe-webhook-secret
STRIPE_MONTHLY_PRICE_ID=price_monthly
STRIPE_ANNUAL_PRICE_ID=price_annual
STRIPE_LIFETIME_PRICE_ID=price_lifetime

# Server configuration
SERVER_URL=http://localhost:3000
PORT=3000
REQUIRE_LICENSE=false
```

### 4. Start the Server

```bash
npm start
```

The server will start on the specified port (default: 3000).

## License Setup

To use all features of the MCP server, you need to purchase a license:

1. Run the buy command:

```bash
npx ai-collaboration-mcp-server buy
```

2. Choose your license plan
3. Complete the payment process
4. Set up your license key:

```bash
npx ai-collaboration-mcp-server setup
```

5. When prompted, enter your license key

## Docker Installation

We also provide a Docker image for easy deployment:

```bash
docker pull mcp-server/ai-collaboration:latest

docker run -p 3000:3000 \
  -e SUPABASE_URL=your-supabase-url \
  -e SUPABASE_KEY=your-supabase-key \
  -e JWT_SECRET=your-jwt-secret \
  -e STRIPE_SECRET_KEY=your-stripe-secret-key \
  -e STRIPE_WEBHOOK_SECRET=your-stripe-webhook-secret \
  -e SERVER_URL=http://localhost:3000 \
  -e REQUIRE_LICENSE=false \
  mcp-server/ai-collaboration:latest
```

## Next Steps

- [Configure your server](configuration.md)
- [Set up roles for AI tools](role-based-access.md)
- [Create your first task](task-management.md)