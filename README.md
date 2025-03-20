# Unity MCP for Cursor [![](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white 'LinkedIn')](https://www.linkedin.com/in/amengol/)

[![](https://badge.mcpx.dev?type=server 'MCP Server')](https://modelcontextprotocol.io/introduction)

> This is a fork of [Arodoid's UnityMCP](https://github.com/Arodoid/UnityMCP) modified to work with Cursor.

Unity MCP for Cursor is a powerful Unity Editor integration that implements the Model Context Protocol (MCP), enabling seamless interaction between Unity and Cursor AI. It provides real-time editor state monitoring, remote command execution, and comprehensive logging capabilities.

![Unity MCP in action](unity-mcp-cursor.gif)

## Architecture

The project consists of two main components:

### 1. Unity Package (unity-mcp-package)

A Unity Editor package that provides:
- Debug window for connection status and monitoring
- WebSocket client for real-time communication
- C# code execution engine
- Comprehensive logging system
- Editor state tracking and serialization

### 2. MCP Server (unity-mcp-server)

A TypeScript-based MCP server that exposes Unity Editor functionality through standardized tools:

#### Available Tools

1. `get_editor_state`
   - Retrieves current Unity Editor state
   - Includes active GameObjects, selection state, play mode status
   - Provides scene hierarchy and project structure
   - Supports different output formats (Raw, scripts only, no scripts)

2. `execute_editor_command`
   - Executes C# code directly in the Unity Editor
   - Full access to UnityEngine and UnityEditor APIs
   - Real-time execution with comprehensive error handling
   - Command timeout protection

3. `get_logs`
   - Retrieves and filters Unity Editor logs
   - Supports filtering by type, content, and timestamp
   - Customizable output fields
   - Buffer management for optimal performance

## Installation

### Prerequisites
- Unity 2020.3 or later
- Node.js 18 or later
- npm 9 or later
- Cursor AI installed

### Unity Package Installation

There are two ways to install the Unity MCP package:

#### Option 1: Install via Package Manager (Recommended)

1. In Unity, open Window > Package Manager
2. Click the "+" button in the top-left corner
3. Select "Add package from git URL..."
4. Enter the repository URL: `https://github.com/amengol/UnityMCP-Cursor.git?path=/unity-mcp-package`
5. Click "Add"

#### Option 2: Manual Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/amengol/UnityMCP-Cursor.git
   ```
2. In Unity, open Window > Package Manager
3. Click the "+" button in the top-left corner
4. Select "Add package from disk..."
5. Navigate to the cloned repository and select the `unity-mcp-package` folder
6. Click "Open"

### MCP Server Setup

1. Clone this repository if you haven't already
2. Install dependencies and build the server:
   ```bash
   cd unity-mcp-server
   npm install
   npm run build
   ```

### Cursor Configuration

To set up the MCP server with Cursor:

1. Create a `cursor-mcp.json` file in your project root (or use the provided one)
2. Configure it with the path to the built MCP server:

```json
{
  "mcpServers": {
    "unity-mcp": {
      "command": "node",
      "args": ["PATH_TO_YOUR_REPO/unity-mcp-server/build/index.js"],
      "env": {}
    }
  }
}
```

3. Replace `PATH_TO_YOUR_REPO` with your actual repository path

## Usage

### Starting the Server

The server will be started automatically by Cursor when needed. You can also start it manually:

```bash
cd unity-mcp-server
node build/index.js
```

### Connecting from Unity

1. Open your Unity project
2. Open the UnityMCP Debug Window (Window > UnityMCP > Debug Window)
3. The plugin will automatically attempt to connect to the MCP server
4. Monitor connection status and logs in the debug window

### Using with Cursor

1. Open your Unity project in the Unity Editor
2. Open Cursor and navigate to your project directory
3. Make sure the Unity Editor's UnityMCP Debug window is open and connected
4. Use Cursor's AI features which will now have access to your Unity Editor state

### Example: Executing Commands

You can use Cursor to send C# commands to Unity:

```csharp
// Center the selected object
Selection.activeGameObject.transform.position = Vector3.zero;

// Toggle play mode
EditorApplication.isPlaying = !EditorApplication.isPlaying;

// Create a new cube
GameObject.CreatePrimitive(PrimitiveType.Cube);
```

## Development

### Building the Server

```bash
cd unity-mcp-server
npm run build
```

### Watching for Changes

```bash
npm run watch
```

### Inspecting MCP Communication

```bash
npm run inspector
```

## Technical Details

### Communication Protocol

- WebSocket-based communication on port 8080
- Bidirectional real-time updates
- JSON message format for all communications
- Automatic reconnection handling

### Security Features

- Command execution timeout protection
- Error handling and validation
- Log buffer management
- Connection state monitoring

### Error Handling

The system provides comprehensive error handling for:
- Connection issues
- Command execution failures
- Compilation errors
- Runtime exceptions
- Timeout scenarios

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT license.
