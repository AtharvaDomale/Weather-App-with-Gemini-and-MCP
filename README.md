# 🌦️ Gemini-MCP Tool Integration

This project connects a **Gemini client** (powered by Google Generative AI) to a custom **FastMCP server**, enabling natural language interaction with custom tools like weather alerts, weather forecasts.

---

## 🧠 Features

### ✅ Gemini Client
- Connects to a FastMCP server using `mcp` and `stdio_client`
- Uses Gemini 2.0 (`gemini-2.0-flash-001`) to:
  - Parse natural language queries
  - Dynamically select and call appropriate MCP tools
  - Respond with tool results in plain language

### ✅ FastMCP Server
Provides 2 tools:
1. **`get_alerts(state)`**
   - Fetch active weather alerts by US state code (e.g., `"CA"`).
2. **`get_forecast(latitude, longitude)`**
   - Get a 5-period forecast for a given geo-location.

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/AtharvaDomale/Weather-App-with-Gemini-and-MCP.git
cd Weather-App-with-Gemini-and-MCP
```

### 2. Create a virtual environment

```bash
uv venv
Activate with: source .venv/bin/activate
```

### 3. Install dependencies

```bash
uv pip install -r requirements.txt
```

> **`requirements.txt`** should include:
> ```txt
> mcp
> google-generativeai
> httpx
> python-dotenv
> ....
> ```

### 4. Add your environment variables

Add GEMINI_API_KEY In `.env` file:

```env
GEMINI_API_KEY=your_google_gemini_api_key_here
```
---

## 🚀 Running the Project

In **terminal**:

```bash
uv run client.py path/to/server.py # python server
```

---

## 💬 Example Queries

Once the client is running, type queries like:

### 🌩️ Weather Alerts
```
Are there any active weather alerts in TX?
```

### 🌤️ Forecast
```
What's the weather forecast for latitude 40.7128 and longitude -74.0060?
```

---

## 📦 Tool JSON Mapping

The client converts FastMCP tool schemas into Gemini-compatible JSON function declarations dynamically using the schema from each tool.

---

## 📌 Notes
- The project uses `stdio` transport for simplicity and flexibility.
- Gemini is configured in `"AUTO"` tool-calling mode.

---

## 🧹 Cleanup

The client ensures all async sessions and transports are properly cleaned up using `AsyncExitStack`.

---

