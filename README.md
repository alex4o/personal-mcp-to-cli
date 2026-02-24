# MCP Client Generator

A tool that generates standalone CLI binaries from MCP (Model Context Protocol) servers using [mcporter](https://github.com/anomalyco/mcporter).

## Supported MCP Servers

- **Linear** - Issue tracking and project management
- **Sentry** - Error tracking and monitoring
- **Context7** - Documentation context retrieval

## Installation

```bash
bun install
```

## Building

Generate TypeScript clients from MCP servers and compile to standalone binaries:

```bash
bun run build
```

This will:
1. Generate TypeScript clients in `generated/` for each MCP server
2. Compile them to standalone binaries in `bin/`

### Individual Commands

```bash
# Generate all clients
bun run generate

# Compile all binaries
bun run compile

# Or do one at a time
bun run generate:linear
bun run compile:linear
```

## Usage

After building, use the compiled binaries:

```bash
./bin/linear --help
./bin/sentry --help
./bin/context7 --help
```

## Configuration

MCP server endpoints are configured in `config/mcporter.json`.
