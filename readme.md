# MCP with Ollama Integration

This project demonstrates how to run [MCP Host](https://github.com/mark3labs/mcphost) with [Ollama](https://ollama.com/) models and additional tools.

---

## Installation

### 1. Install Ollama

Follow the [Ollama installation guide](https://ollama.com/download) for your OS.

**On macOS:**
```sh
ollama run llama3.2:latest
```

### 2. Install Go

Download and install Go from [golang.org](https://golang.org/dl/).

**Verify installation:**
```sh
go version
```

**Add Go bin to your PATH:**
```sh
export PATH="$PATH:$(go env GOPATH)/bin"
```

### 3. Install MCP Host (Go)

Install MCP Host using Go:
```sh
go install github.com/mark3labs/mcphost@latest
```

**Verify installation:**
```sh
mcphost --version
```
---

## Create a Configuration File

Edit `config.json` to define your MCP servers and tools. Example:

```json
{
	"globalShortcut": "cmd+Space",
	"mcpServers": {
		"sqlite": {
			"command": "uvx",
			"args": [
				"mcp-server-sqlite",
				"--db-path",
				"/Users/fnc11/playground/mcp_with_ollama/dbs/Car_Database.db"
			]
		},
		"ddg-search": {
			"command": "uvx",
			"args": [
				"duckduckgo-mcp-server"
			]
		},
		"filesystem": {
			"command": "npx",
			"args": [
				"-y",
				"@modelcontextprotocol/server-filesystem",
				"/Users/fnc11/playground/mcp_with_ollama/"
			]
		}
	}
}
```

---

## Running Ollama Model with MCP Host

To run the `llama3.2:latest` model with MCP Host and your tools config:

```sh
mcphost --config ./config.json
```

---

## License

MIT