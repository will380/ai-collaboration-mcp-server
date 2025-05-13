# AI Tool Integration Guide

This guide provides specific instructions for integrating the AI Collaboration MCP Server with Windsurf, Cursor, and Claude Code.

## Prerequisites

- An active license for the AI Collaboration MCP Server
- MCP server running on your machine or a server
- The MCP server URL (default: http://localhost:3000/mcp)
- Your license key

## Claude Code Integration

Claude Code has native support for MCP and can easily connect to your server.

### Setup Steps

1. Open Claude Code in your terminal:
   ```bash
   claude-code
   ```

2. Access the MCP configuration:
   ```bash
   /mcp config
   ```

3. Add your MCP server:
   ```bash
   /mcp add-server
   ```

4. Enter the requested information:
   - Server name: (e.g., "AI Collaboration MCP Server")
   - Server URL: http://localhost:3000/mcp (or your custom URL)
   - License key: Your license key
   - Role: backend_dev (or your preferred role)

5. Connect to the server:
   ```bash
   /mcp connect "AI Collaboration MCP Server"
   ```

6. To view available tools:
   ```bash
   /mcp list-tools
   ```

7. To use a tool, for example creating a task:
   ```bash
   /mcp invoke create-task --title "Implement API endpoint" --description "Create a REST API endpoint for user registration" --type "backend" --priority "high"
   ```

## Cursor Integration

Cursor can be configured to connect to the MCP server through its extension system.

### Setup Steps

1. Open Cursor and navigate to Settings > Extensions

2. Add a new MCP connection with the following parameters:
   - Name: AI Collaboration MCP Server
   - URL: http://localhost:3000/mcp
   - Headers:
     ```json
     {
       "x-license-key": "your-license-key"
     }
     ```
   - Default role: frontend_dev (or your preferred role)

3. Enable the connection by clicking "Connect"

4. Access MCP tools through Cursor's command palette (Ctrl+Shift+P or Cmd+Shift+P):
   ```
   MCP: List Available Tools
   MCP: Invoke Tool
   MCP: Get Tasks
   ```

5. You can also use the Cursor API in scripts:
   ```javascript
   // Example Cursor script to create a task
   cursor.mcp.invoke('create-task', {
     title: 'Implement UI component',
     description: 'Create a reusable button component with variants',
     type: 'frontend',
     priority: 'medium'
   });
   ```

## Windsurf Integration

Windsurf can connect to the MCP server through its plugin system.

### Setup Steps

1. Create a Windsurf plugin configuration file:
   ```bash
   mkdir -p ~/.windsurf/plugins
   touch ~/.windsurf/plugins/mcp-collaboration.json
   ```

2. Add the following configuration to the file:
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
       "autoConnect": true,
       "pollInterval": 5000
     }
   }
   ```

3. Restart Windsurf to load the plugin

4. Access MCP functionality through Windsurf commands:
   ```
   /mcp list-tools
   /mcp get-tasks
   /mcp create-task
   /mcp send-message
   ```

5. To view your assigned tasks:
   ```
   /mcp get-tasks --assignee windsurf
   ```

## Using AI Tools Together

Once all three AI tools are connected to the MCP server, they can collaborate on projects:

1. **Task Assignment**: Assign different tasks to each AI tool based on their strengths:
   - Claude Code: Backend development, API design, data modeling
   - Cursor: Frontend development, UI components, styling
   - Windsurf: Architecture, infrastructure, system design

2. **Message Exchange**: AI tools can communicate with each other about task details:
   ```
   # Claude Code sending a message to Cursor
   /mcp invoke send-message --from claude-code --to cursor --message "The user authentication API is ready at /api/auth" --taskId task-123
   ```

3. **Component Access**: Prevent conflicts when multiple AI tools work on the same project:
   ```
   # Request access to a file
   /mcp invoke request-access --agent claude-code --component "src/api/auth.js" --reason "Implementing authentication logic"
   
   # Release access when done
   /mcp invoke release-access --agent claude-code --component "src/api/auth.js"
   ```

## Troubleshooting

### Connection Issues

If an AI tool can't connect to the MCP server:

1. Verify the MCP server is running:
   ```bash
   npx ai-collaboration-mcp-server status
   ```

2. Check that the correct URL is being used (including the protocol and port)

3. Verify your license key is valid:
   ```bash
   npx ai-collaboration-mcp-server status
   ```

4. Ensure your firewall allows connections to the MCP server port

### Authentication Errors

If you see authentication or license verification errors:

1. Verify your license key is correct and not expired
2. Ensure the AI tool is passing the license key correctly in the headers
3. Try regenerating your license key if the issue persists

### Tool Invocation Errors

If tool invocations fail:

1. Use the appropriate AI tool's command to list available tools first
2. Verify the tool name and parameters are correct
3. Check the MCP server logs for detailed error information

## Next Steps

- [MCP Server API Reference](api-reference.md)
- [Task Management Guide](task-management.md)
- [License Management](license-management.md)