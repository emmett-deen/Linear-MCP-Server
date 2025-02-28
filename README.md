# Linear-MCP-Server
[![smithery badge](https://smithery.ai/badge/@emmett-deen/linear-mcp-server)](https://smithery.ai/server/@emmett-deen/linear-mcp-server)

A Model Context Protocol (MCP) server implementation for the Linear GraphQL API that enables Claude to interact with Linear project management systems through user tokens.

## Overview

Linear-MCP-Server bridges the gap between Claude (AI assistant) and Linear (project management tool) by implementing the MCP protocol. This allows Claude to:

- Retrieve issues, projects, teams, and other data from Linear
- Create and update issues
- Change issue status
- Assign issues to team members
- Add comments
- Create projects and teams

The server uses Linear's GraphQL API and authenticates via user tokens (not OAuth) for simplicity.

## Getting Started

### Prerequisites

- Node.js (v18+)
- NPM or Yarn
- Linear API token

### Installing via Smithery

To install linear-mcp-server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@emmett-deen/linear-mcp-server):

```bash
npx -y @smithery/cli install @emmett-deen/linear-mcp-server --client claude
```

### Installation

```bash
# Install globally
npm install -g linear-mcp-server

# Or clone and install locally
git clone https://github.com/yourusername/Linear-MCP-Server.git
cd Linear-MCP-Server
npm install
npm link  # Makes the package available globally
```

### Running the Server

Run the server with your Linear API token:

```bash
linear-mcp-server --token YOUR_LINEAR_API_TOKEN
```

Or set the token in your environment and run without arguments:

```bash
export LINEAR_API_TOKEN=YOUR_LINEAR_API_TOKEN
linear-mcp-server
```

## Using with Claude Desktop

To use this MCP server with Claude Desktop:

1. Enable Developer Mode in Claude Desktop (from the menu bar)
2. Go to Settings > Developer options
3. Click "Add Server"
4. Configure with the following settings:
   - **Name**: Linear MCP Server
   - **Type**: Local Process
   - **Command**: linear-mcp-server
   - **Arguments**: --token YOUR_LINEAR_API_TOKEN

Alternatively, manually edit the config file:

```json
{
  "mcp": {
    "servers": [
      {
        "name": "Linear MCP Server",
        "transport": {
          "type": "stdio",
          "command": "linear-mcp-server",
          "args": ["--token", "YOUR_LINEAR_API_TOKEN"]
        }
      }
    ]
  }
}
```

5. Save the config
6. Restart Claude Desktop (quit completely and reopen)
7. You should now see Linear MCP Server available as a tool in Claude

## Available Tools

The Linear MCP Server provides a comprehensive set of tools to interact with the Linear API. For a detailed list of all implemented tools and planned future additions, see the [TOOLS.md](./TOOLS.md) document.

Some key tools include:

- Get information about users, teams, projects, and issues
- Create and update issues
- Search for issues with filters
- Create and manage projects
- Add comments to issues

## Example Claude Prompts

Once connected to Claude Desktop, you can use prompts like:

- "Show me all my Linear issues"
- "Create a new issue titled 'Fix login bug' in the Frontend team"
- "Change the status of issue FE-123 to 'In Progress'"
- "Assign issue BE-456 to John Smith"
- "Add a comment to issue UI-789: 'This needs to be fixed by Friday'"

## Development

To develop locally:

```bash
# Clone the repository
git clone https://github.com/yourusername/Linear-MCP-Server.git
cd Linear-MCP-Server

# Install dependencies
npm install

# Run in development mode
npm run dev -- --token YOUR_LINEAR_API_TOKEN
```

### Extending the Server

To add new tools to the server:

1. Follow the implementation guide in the [TOOLS.md](./TOOLS.md) document
2. Make sure to follow the established code structure in the `src/` directory
3. Update the documentation to reflect your changes

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
