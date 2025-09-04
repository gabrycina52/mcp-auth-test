# EMU MCP Server

A Model Context Protocol (MCP) server with JWT authentication for secure tool access.

## 🚀 Features

- **JWT Authentication**: Secure access with OAuth 2.1 compliance
- **Mock Tools**: `file_search` and `competitive_edge` for testing
- **Resources**: Company database access
- **Prompts**: Competitive analysis templates
- **FastMCP**: Built with the FastMCP framework

## 🔧 Setup

```bash
# Install dependencies
uv add fastmcp pyjwt

# Run the server
uv run python3 main.py
```

Server runs on `http://localhost:8000`

## 🔐 Authentication

The server enforces JWT authentication. All requests must include a valid Bearer token.

### Configuration

Update `main.py` with your OAuth endpoints:

```python
auth = JWTVerifier(
    jwks_uri="https://your-company-auth.com/.well-known/jwks.json",
    issuer="https://your-company-auth.com", 
    audience="emu-mcp-server"
)
```

### Testing with MCP Inspector

1. Start the server: `uv run python3 main.py`
2. Run inspector: `npx @modelcontextprotocol/inspector`
3. **Expected**: HTTP 401 errors (authentication required)
4. **To test**: Provide valid JWT token in Authorization header

## 🛠️ Available Tools

- **`file_search`**: Search files and documents
- **`competitive_edge`**: Get competitive intelligence data

## 📚 Resources

- **Company Database**: Access to internal company data

## 🎯 Prompts

- **Competitive Analysis**: Template for market analysis

## 🔍 Testing

```bash
# Test authentication (should fail)
curl -X POST http://localhost:8000/mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"tools/list","id":1}'

# Expected response: HTTP 401 "Authentication required"
```

## 📖 Learn More

- [MCP Specification](https://modelcontextprotocol.io/)
- [FastMCP Documentation](https://gofastmcp.com/)
- [JWT Authentication](https://gofastmcp.com/servers/auth/authentication)
