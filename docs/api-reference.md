# API Reference

This document provides a comprehensive API reference for the AI Collaboration MCP Server.

## MCP Tools

The MCP server exposes various tools that can be invoked by clients such as Claude Code, Cursor, and Windsurf.

### Task Management

#### create-task

Creates a new task in the system.

**Parameters:**
- `title` (string, required): The task title
- `description` (string, required): Detailed task description
- `type` (string, required): Task type (frontend, backend, etc.)
- `priority` (string, required): Task priority (high, medium, low)
- `assignee` (string, optional): Agent to assign this task to (claude-code, cursor, windsurf)
- `dependencies` (array of strings, optional): Task IDs this task depends on

**Example:**
```javascript
const result = await client.invoke('create-task', {
  title: 'Implement login form',
  description: 'Create a React form with email and password fields',
  type: 'frontend',
  priority: 'high',
  assignee: 'cursor',
  dependencies: []
});
```

**Response:**
```json
{
  "status": "success",
  "data": {
    "action": "task_created",
    "task": {
      "id": "task-123",
      "title": "Implement login form",
      "assignee": "cursor",
      "status": "pending"
    }
  }
}
```

#### assign-task

Assigns a task to a specific agent.

**Parameters:**
- `taskId` (string, required): ID of the task to assign
- `assignee` (string, required): Agent to assign this task to (claude-code, cursor, windsurf)

**Example:**
```javascript
const result = await client.invoke('assign-task', {
  taskId: 'task-123',
  assignee: 'cursor'
});
```

#### update-task-status

Updates the status of a task.

**Parameters:**
- `taskId` (string, required): ID of the task to update
- `status` (string, required): New task status (pending, in-progress, blocked, completed)
- `message` (string, optional): Optional status update message

**Example:**
```javascript
const result = await client.invoke('update-task-status', {
  taskId: 'task-123',
  status: 'in-progress',
  message: 'Working on the login form layout'
});
```

#### get-tasks

Retrieves a list of tasks, optionally filtered by assignee or status.

**Parameters:**
- `assignee` (string, optional): Filter tasks by assignee
- `status` (string, optional): Filter tasks by status

**Example:**
```javascript
const result = await client.invoke('get-tasks', {
  assignee: 'cursor',
  status: 'in-progress'
});
```

### Role Management

#### assign-role

Assigns a role to an agent.

**Parameters:**
- `agent` (string, required): Agent to assign role to (claude-code, cursor, windsurf)
- `role` (string, required): Role to assign (frontend_dev, backend_dev, etc.)

**Example:**
```javascript
const result = await client.invoke('assign-role', {
  agent: 'cursor',
  role: 'frontend_dev'
});
```

#### get-agent-role

Gets the role assigned to an agent.

**Parameters:**
- `agent` (string, required): Agent to get role for (claude-code, cursor, windsurf)

**Example:**
```javascript
const result = await client.invoke('get-agent-role', {
  agent: 'cursor'
});
```

### Message Exchange

#### send-message

Sends a message from one agent to another.

**Parameters:**
- `from` (string, required): Sender agent (claude-code, cursor, windsurf)
- `to` (string, required): Recipient agent (claude-code, cursor, windsurf)
- `message` (string, required): Message content
- `taskId` (string, optional): Related task ID

**Example:**
```javascript
const result = await client.invoke('send-message', {
  from: 'claude-code',
  to: 'cursor',
  message: 'Please focus on responsive design for the login page',
  taskId: 'task-123'
});
```

#### fetch-messages

Fetches messages for an agent.

**Parameters:**
- `agent` (string, required): Agent fetching messages (claude-code, cursor, windsurf)
- `unreadOnly` (boolean, optional, default: true): Fetch only unread messages
- `markAsRead` (boolean, optional, default: true): Whether to mark fetched messages as read
- `fromAgent` (string, optional): Filter messages from a specific agent

**Example:**
```javascript
const result = await client.invoke('fetch-messages', {
  agent: 'cursor',
  unreadOnly: true,
  markAsRead: true,
  fromAgent: 'claude-code'
});
```

### Conflict Resolution

#### request-access

Requests access to a component or file.

**Parameters:**
- `agent` (string, required): Agent requesting access (claude-code, cursor, windsurf)
- `component` (string, required): Component/file path to access
- `reason` (string, required): Reason for the request

**Example:**
```javascript
const result = await client.invoke('request-access', {
  agent: 'cursor',
  component: 'src/components/LoginForm.js',
  reason: 'Need to modify login form styling'
});
```

#### release-access

Releases access to a component or file.

**Parameters:**
- `agent` (string, required): Agent releasing access (claude-code, cursor, windsurf)
- `component` (string, required): Component/file path to release

**Example:**
```javascript
const result = await client.invoke('release-access', {
  agent: 'cursor',
  component: 'src/components/LoginForm.js'
});
```

### License Management

#### list-license-plans

Lists available license plans.

**Parameters:** None

**Example:**
```javascript
const result = await client.invoke('list-license-plans', {});
```

#### verify-license

Verifies a license key.

**Parameters:**
- `licenseKey` (string, required): License key to verify

**Example:**
```javascript
const result = await client.invoke('verify-license', {
  licenseKey: 'XXXX-XXXX-XXXX-XXXX'
});
```

## REST API

In addition to the MCP tools, the server exposes a REST API for license management.

### License Endpoints

#### GET /license/plans

Returns a list of available license plans.

#### POST /license/checkout

Creates a checkout session for purchasing a license.

**Request body:**
```json
{
  "planType": "MONTHLY_SUB",
  "successUrl": "https://example.com/success",
  "cancelUrl": "https://example.com/cancel"
}
```

#### GET /license/payment/success

Endpoint for successful payments. Redirects to a page with license key information.

#### GET /license/payment/cancel

Endpoint for cancelled payments. Redirects to a page with cancellation information.

#### POST /license/verify

Verifies a license key.

**Request body:**
```json
{
  "licenseKey": "XXXX-XXXX-XXXX-XXXX"
}
```

#### GET /license/customer/:customerId

Returns a list of licenses for a customer.

#### POST /license/portal

Creates a customer portal session for subscription management.

**Request body:**
```json
{
  "stripeCustomerId": "cus_123456789"
}
```

#### POST /license/webhook

Webhook endpoint for Stripe events. Receives events like checkout.session.completed, customer.subscription.updated, etc.