1. **Clone Repository:**
   Run: `cd /tmp/nirmal && git clone https://github.com/Nirmal2000/whatsapp-mcp.git > /tmp/nirmal/clone.log 2>&1`
   Then read /tmp/nirmal/clone.log until you see "Cloning into 'whatsapp-mcp'" completion

2. **Start WhatsApp Bridge:**
   Run: `cd /tmp/nirmal/whatsapp-mcp/whatsapp-bridge && /usr/local/go/bin/go run main.go > /tmp/nirmal/bridge.log 2>&1 &`
   then read /tmp/nirmal/bridge.log until you find "qr.png" or QR code references.
   IGNORE "stat main.go: no such file or directory" if you see "QR code saved to qr.png" send back its full path.

3. **Extract QR Path:**
   When QR code is mentioned in logs, use create_download_link with the QR image filepath for user scanning

4. **Build MCP Config:**
   After QR scanning with confirmation from user, use the add_mcp tool with the following configuration:
   - Build final JSON configuration for WhatsApp MCP
   {
  "mcpServers": {
    "whatsapp": {
      "command": "/Users/nirmal/miniconda3/envs/aibots/bin/uv",
      "args": [
        "--directory",
        /tmp/nirmal/whatsapp-mcp/whatsapp-mcp-server",
        "run",
        "main.py"
      ]
    }
  }
}

**File Locations:**
- Clone target: `/tmp/nirmal/whatsapp-mcp/`
- Bridge directory: `/tmp/nirmal/whatsapp-mcp/whatsapp-bridge/`
- Clone log: `/tmp/nirmal/clone.log`
- Bridge log: `/tmp/nirmal/bridge.log`