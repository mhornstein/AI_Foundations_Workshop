# MCP Client – Minimal Command Flow

This document shows the minimal set of JSON-RPC messages used within the MCP protocol for a client to interact with an MCP server.

----

## 1. Initialize

```json
{"jsonrpc":"2.0","id":0,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"example-client","version":"1.0"}}}

```

**What it does:**  
Starts the session with the server by performing the initial handshake.

**Structure:**

-   `jsonrpc`: Protocol version (always `"2.0"`)
    
-   `id`: Request identifier (used to match responses)
    
-   `method`: `"initialize"` (handshake start)
    
-   `params`:
    
    -   `protocolVersion`: MCP version
        
    -   `capabilities`: Client-supported features
        
    -   `clientInfo`: Metadata about the client
        

----------

## 2. Initialized (Notification)

```json
{"jsonrpc":"2.0","method":"notifications/initialized"}

```

**What it does:**  
Signals that the client is ready to begin normal interaction after the handshake.

**Structure:**

-   `jsonrpc`: Protocol version
    
-   `method`: Notification name (no `id` → no response expected)
    

----------

## 3. List Tools

```json
{"jsonrpc":"2.0","id":1,"method":"tools/list"}

```

**What it does:**  
Requests the list of available tools from the server.

**Structure:**

-   `id`: Unique request ID
    
-   `method`: `"tools/list"`
    

**Response includes:**

-   Tool names
    
-   Descriptions (from docstrings)
    
-   Input/Output schemas
    

> Note: In real systems, this list may be cached by the client.

----------

## 4. Call Tool

```json
{"jsonrpc":"2.0","id":2,"method":"tools/call","params":{"name":"mojifuzzle","arguments":{"emoji_name":"heart","count":3}}}

```

**What it does:**  
Requests the server to execute a specific tool with given arguments.

**Structure:**

-   `method`: `"tools/call"`
    
-   `params`:
    
    -   `name`: Tool name
        
    -   `arguments`: Input values matching the tool schema
        

**Response includes:**

-   `content`: Human-readable output
    
-   `structuredContent`: Structured result
    
-   `isError`: Indicates success/failure
    

----------

## 🔁 Where the AI Fits In

In real-world AI systems:

-   The **client is often an agent**
    
-   The **LLM decides** which tool to use
    
-   The **client translates that decision into MCP requests**
    

> The LLM does not execute tools — it decides which JSON request to send.

----------

## Optional: Try It Manually (via stdin)

You can run the MCP server directly (e.g., `python server.py`) and send these JSON messages manually through standard input.

This can help illustrate how the protocol works behind the scenes.

⚠️ Notes:

-   Each message must be sent as a single-line JSON object.
    
-   The order of messages matters (initialize → initialized → tools → call).
    
-   This approach is useful for learning, but not practical for real usage.
    

In real systems, a client (or agent) handles this communication automatically.

----------

## Disclaimer

This document was created with the assistance of AI tools — just like the systems it describes.