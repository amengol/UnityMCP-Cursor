# Unity MCP Package for Cursor

This Unity package enables seamless integration between Unity and Cursor AI via the Model Context Protocol (MCP). It provides real-time editor state monitoring, remote command execution, and comprehensive logging capabilities.

## Features

- Debug window for connection status and monitoring
- WebSocket client for real-time communication
- C# code execution engine
- Comprehensive logging system
- Editor state tracking and serialization

## Installation

### Option 1: Install via Package Manager (Recommended)

1. In Unity, open Window > Package Manager
2. Click the "+" button in the top-left corner
3. Select "Add package from git URL..."
4. Enter the repository URL: `https://github.com/amengol/UnityMCP-Cursor.git?path=/UnityMCPPlugin`
5. Click "Add"

### Option 2: Manual Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/amengol/UnityMCP-Cursor.git
   ```
2. In Unity, open Window > Package Manager
3. Click the "+" button in the top-left corner
4. Select "Add package from disk..."
5. Navigate to the cloned repository and select the `UnityMCPPlugin` folder
6. Click "Open"

## Usage

1. Open the Unity MCP Debug Window from the menu: Window > UnityMCP > Debug Window
2. The package will automatically attempt to connect to the MCP server
3. Monitor connection status and logs in the debug window

## Requirements

- Unity 2020.3 or later
- MCP server running (typically handled by Cursor)

## License

This package is licensed under the MIT license. 