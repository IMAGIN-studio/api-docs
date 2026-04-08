# AI-Powered API Documentation Search for Developers

Give your AI coding assistant direct access to the full IMAGIN.studio documentation, from CDN data points and getImage parameters to paint matching, 360° spinners and deployment guides, so you can build faster without leaving your editor.

### What it does

The IMAGIN.studio MCP server is a plugin for AI coding assistants that lets them search our documentation in real time. Instead of switching between your editor and the docs site, you ask your assistant directly and get answers pulled straight from the source.

**Ask things like:**

* "What parameters do I need for a getImage call?"
* "How does zoomType adaptive vs relative work?"
* "What are the CDN response headers I should check for substituted images?"
* "How do I build a 360° spinner using angles 200 to 231?"

**Or go further and build with it:**

* "Replace all car listing images with IMAGIN.studio imagery, matched down to trim level"
* "Embed IMAGIN.studio lifestyle images with lazy loading for Core Web Vitals"
* "Add a color picker that fetches swatches from the paint API and updates the hero image"

Your assistant reads our docs and writes the integration code for you.

### Quick Setup

Add this to your AI coding assistant's MCP configuration:

```json
{
  "mcpServers": {
    "imagin-docs": {
      "command": "uvx",
      "args": ["imagin-studio-api-docs-mcp"]
    }
  }
}
```

Or just tell your assistant:

> Install this MCP server: https://pypi.org/project/imagin-studio-api-docs-mcp/

That's it. Most MCP-compatible agents will walk you through the rest.

> **First run note:** The MCP server downloads dependencies and builds its search index on first launch. Most clients will time out and report a connection failure. This is expected. Just reconnect and it will work. Subsequent starts are near-instant.

### Supported AI Coding Assistants

The MCP server works with any assistant that supports the Model Context Protocol, including Claude Code, Claude Desktop, Cursor, Windsurf, VS Code + GitHub Copilot, Cline and Zed.

Step-by-step setup instructions for each of these agents are on the [PyPI setup guide](https://pypi.org/project/imagin-studio-api-docs-mcp/).

### Links & Registries

| Registry           | Link                                                                                                       |
| ------------------ | ---------------------------------------------------------------------------------------------------------- |
| **Source code**    | [github.com/IMAGIN-studio/api-docs-mcp](https://github.com/IMAGIN-studio/api-docs-mcp)                     |
| **Package (PyPI)** | [pypi.org/project/imagin-studio-api-docs-mcp](https://pypi.org/project/imagin-studio-api-docs-mcp/)        |
| **PulseMCP**       | [pulsemcp.com/servers/imagin-studio-api-docs](https://www.pulsemcp.com/servers/imagin-studio-api-docs)     |
| **Glama**          | [glama.ai/mcp/servers/IMAGIN-studio/api-docs-mcp](https://glama.ai/mcp/servers/IMAGIN-studio/api-docs-mcp) |

### Requirements

You'll need **uv**, a fast Python package manager ([install guide](https://docs.astral.sh/uv/getting-started/installation/)). This is required regardless of whether you use `uvx` or `npx`. Python 3.10+ is also needed but is managed automatically by `uv`.

If your agent can't find `uvx`, you can use `npx` as an alternative (requires Node.js 18+). See the [PyPI setup guide](https://pypi.org/project/imagin-studio-api-docs-mcp/) for details.
