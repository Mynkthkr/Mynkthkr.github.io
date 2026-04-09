# Mynkthkr.github.io

## Local setup (using an existing open-source repo)

Use the existing `samuelgursky/davinci-resolve-mcp` repository locally (do not create a new repo).

### 1) Install prerequisites
- DaVinci Resolve Studio 20 (Studio is required for scripting)
- Python 3.10–3.12
- In Resolve: **Preferences → General → External scripting using → Local**

### 2) Clone the open-source repo
```bash
git clone https://github.com/samuelgursky/davinci-resolve-mcp.git
cd davinci-resolve-mcp
```

### 3) Start DaVinci Resolve first
Open Resolve 20 and keep it running before setup/server start.

### 4) Run the installer
```bash
python install.py
```
This sets up a virtual environment, installs dependencies, and can configure your MCP client.

### 5) Launch the MCP server
```bash
# recommended compound server
python src/server.py

# optional full granular server
python src/resolve_mcp_server.py --full
```

### 6) Point your MCP client to the server
Example configuration:

```json
{
  "mcpServers": {
    "davinci-resolve": {
      "command": "python",
      "args": ["/absolute/path/to/davinci-resolve-mcp/src/server.py"]
    }
  }
}
```

### 7) Verify
From your MCP client, run a simple call such as:
- Get Resolve version
- List projects

If it fails, check:
- Resolve is open
- External scripting is set to Local
- You are using Resolve Studio
- Python is 3.10–3.12
