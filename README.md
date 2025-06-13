# Python MCP Weather Server with Azure Deployment

A Model Context Protocol (MCP) server built with FastAPI and Python that provides weather information using the National Weather Service API. Ready for deployment to Azure App Service with Azure Developer CLI (azd).

## 🌟 Features

- **FastAPI Framework**: Modern, fast web framework for building APIs
- **MCP Protocol Compliance**: Full support for JSON-RPC 2.0 MCP protocol
- **HTTP Transport**: HTTP-based communication for web connectivity
- **Weather Tools**: 
  - `get_alerts`: Get weather alerts for any US state
  - `get_forecast`: Get detailed weather forecast for any location
- **Azure Ready**: Pre-configured for Azure App Service deployment
- **Web Test Interface**: Built-in HTML interface for testing
- **National Weather Service API**: Real-time weather data from official US government source

## 💻 Local Development

### Prerequisites

- Python 3.8+
- pip (Python package installer)

### Setup & Run

1. **Clone and install dependencies:**
   ```bash
   git clone <your-repo-url>
   cd remote-mcp-webapp-python
   python -m venv venv
   .\venv\Scripts\Activate.ps1  # Windows
   # source venv/bin/activate   # macOS/Linux
   pip install -r requirements.txt
   ```

2. **Start the development server:**
   ```bash
   .\start_server.ps1  # Windows
   # or manually:
   uvicorn main:app --host 0.0.0.0 --port 8000 --reload
   ```

3. **Access the server:**
   - Server: http://localhost:8000/
   - Health Check: http://localhost:8000/health
   - Test Interface: http://localhost:8000/test

## 🔌 Connect to the Local MCP Server

### Using VS Code - Copilot Agent Mode

1. Add MCP Server from command palette and add the URL to your running server's HTTP endpoint:
   ```
   http://localhost:8000
   ```

2. List MCP Servers from command palette and start the server

3. In Copilot chat agent mode, enter a prompt to trigger the tool:
   ```
   What's the weather forecast for San Francisco?
   ```

4. When prompted to run the tool, consent by clicking Continue

### Using MCP Inspector

1. In a new terminal window, install and run MCP Inspector:
   ```bash
   npx @modelcontextprotocol/inspector
   ```

2. CTRL+click the URL displayed by the app (e.g. http://localhost:5173/#resources)

3. Set the transport type to `HTTP`

4. Set the URL to your running server's HTTP endpoint and Connect:
   ```
   http://localhost:8000
   ```

5. List Tools, click on a tool, and Run Tool

## 🚀 Quick Deploy to Azure

### Prerequisites

- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
- [Azure Developer CLI (azd)](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/install-azd)
- Active Azure subscription

### Deploy in 3 Commands

```bash
# 1. Login to Azure
azd auth login

# 2. Initialize the project
azd init

# 3. Deploy to Azure
azd up
```

After deployment, your MCP server will be available at:

- Health Check: `https://<your-app>.azurewebsites.net/health`
- MCP Capabilities: `https://<your-app>.azurewebsites.net/mcp/capabilities`
- Test Interface: `https://<your-app>.azurewebsites.net/test`

## 🔌 Connect to the Remote MCP Server

Follow the same guidance as above, but use your App Service URL instead.

## 🧪 Testing

Visit `/test` endpoint for an interactive testing interface.

## 🌦️ Data Source

This server uses the National Weather Service (NWS) API:

- Real-time weather alerts and warnings
- Detailed weather forecasts
- Official US government weather data
- No API key required
- High reliability and accuracy