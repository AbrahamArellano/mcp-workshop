# Model Context Protocol (MCP) Labs

This repository contains a series of labs for learning how to build and use Model Context Protocol (MCP) servers and integrate them with AI Agents.

## What is MCP?

The Model Context Protocol (MCP) is a standardized protocol that enables AI models to interact with external tools and data sources. MCP follows a client-server architecture:

- **Host**: The application that needs AI capabilities
- **Client**: Part of the host that manages connections to MCP servers
- **Server**: Provides tools and resources that the AI can use

MCP enables AI models to:

- **Execute Tools**: Perform actions like searching, calculating, or accessing external systems
- **Access Resources**: Retrieve data from structured sources via URI templates
- **Get Contextual Information**: Receive additional context to improve responses

This standardized approach allows AI capabilities to be portable across different platforms and models, creating a consistent interface for AI-powered functionality.

## Lab Structure

- **Lab 01: Hello Claude** - A minimal MCP server with Claude Desktop integration for interactive testing
- **Lab 02: Retail MCP Servers** - Multiple MCP servers working together for a retail use case
- **Lab 03: AWS Cloud Deployment** - Deploy MCP servers to AWS Fargate with HTTPS and streaming support
- *(More labs will be added in the future)*

## Getting Started

Each lab directory contains its own README with specific instructions:

1. Start with **Lab 01** to learn the basics of MCP server implementation and Claude Desktop integration:
```bash
cd lab01-hello-claude
```

2. Continue with **Lab 02** to explore how multiple MCP servers can work together:
```bash
cd lab02-retail-mcp-servers
```

3. Advance to **Lab 03** to deploy MCP servers to AWS with Fargate:
```bash
cd lab03-aws-cloud-deployment
```

## Authentication Requirements

Starting with Lab 03, the MCP servers require JWT bearer token authentication. This security feature ensures that only authorized clients can access your MCP services. Make sure to:

1. Configure your JWT token in the authentication settings
2. Set up proper authorization headers in your clients
3. Include proper token validation in your server implementations

## Protocol Support

This workshop uses the latest MCP protocol implementation including:

- **Streamable HTTP Transport**: The modern alternative to Server-Sent Events (SSE), offering improved performance and reliability for real-time communication
- **Bidirectional Streaming**: Supports both client-to-server and server-to-client streaming capabilities
- **Binary Data Support**: Handles both JSON and binary data formats

## Deployment Automation

The workshop includes GitHub Actions workflows for automating deployments:

- **Deploy MCP Workshop Lab to AWS**: Deploys the entire lab infrastructure to AWS
- **Update MCP Playground**: Updates only the MCP Playground container for faster iterations
- **Destroy MCP Workshop AWS Resources**: Safely removes all created AWS resources

These workflows enable you to focus on learning the MCP concepts without getting bogged down in deployment details.

## Troubleshooting Common Issues

### Authentication Errors

If you see errors like `AttributeValue for a key attribute cannot contain an empty string value. Key: PK`, this typically indicates missing or invalid JWT authentication. Make sure you've:

1. Set up a valid JWT token in the client configuration
2. Properly formatted the Authorization header as `Bearer <token>`
3. Included the token in all requests to authenticated endpoints

### Conversation Flow Issues

If conversations terminate prematurely when using tool calls, particularly in multi-step workflows:

1. Enable debug logging for more visibility
2. Check for proper error handling in tool call sequences
3. Use the "Force Continue" option in the MCP Playground interface if needed

## Resources

- [Model Context Protocol Specification](https://modelcontextprotocol.io)
- [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- [Anthropic Claude Documentation](https://docs.anthropic.com/en/docs/agents-and-tools/mcp)
- [StreamableHTTP Protocol Reference](https://modelcontextprotocol.io/reference/extensions/streaming)