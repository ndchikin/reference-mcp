# CiteAssist MCP server

[![LightNow capabilities](https://lightnow.ai/badge/io.github.ndchikin/reference-mcp)](https://lightnow.ai/servers/io.github.ndchikin/reference-mcp)

A Model Context Protocol server that provides BibTeX-formatted citation data from CiteAs and Google Scholar. Enhance your research workflow by integrating citation retrieval directly into your applications.

## Components

### Tools

* `get_citeas_data` - Retrieve BibTeX-formatted citation for the specified resource from the CiteAs
  * `resource` (string, required): DOI, URL, keyword
* `get_scholar_data` - Retrieve BibTeX-formatted citations from the Google Scholar
  * `query` (string, required): Search query
  * `results` (integer, optional): Number of results (default: 2)

## Quickstart

### Install

#### Claude Desktop

On MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`

On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

Development/Unpublished Servers Configuration:

```json
"mcpServers": {
  "reference-mcp": {
    "command": "uv",
    "args": [
      "--directory",
      "/path/to/project/dir",
      "run",
      "reference-mcp"
    ]
  }
}
```

Published Servers Configuration:

```json
"mcpServers": {
  "reference-mcp": {
    "command": "uvx",
    "args": [
      "reference-mcp"
    ]
  }
}
```

### Installing via Smithery

To install reference-mcp for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@ndchikin/reference-mcp):

```bash
npx -y @smithery/cli install @ndchikin/reference-mcp --client claude
```

## Development

### Building and Publishing

To prepare the package for distribution:

1. Sync dependencies and update lockfile:
```bash
uv sync
```

2. Build package distributions:
```bash
uv build
```

This will create source and wheel distributions in the `dist/` directory.

3. Publish to PyPI:
```bash
uv publish
```

Note: You'll need to set PyPI credentials via environment variables or command flags:
- Token: `--token` or `UV_PUBLISH_TOKEN`
- Or username/password: `--username`/`UV_PUBLISH_USERNAME` and `--password`/`UV_PUBLISH_PASSWORD`

### Debugging

Since MCP servers run over stdio, debugging can be challenging. For the best debugging
experience, we strongly recommend using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector).

You can launch the MCP Inspector via [`npm`](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) with this command:

```bash
npx @modelcontextprotocol/inspector uv --directory /path/to/project/dir run reference-mcp
```

Upon launching, the Inspector will display a URL that you can access in your browser to begin debugging.
