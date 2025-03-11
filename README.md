# AWS Bedrock Logs MCP

A command-line interface and API for analyzing AWS Bedrock usage and logs through [Anthropic's MCP (Model Control Protocol)](https://www.anthropic.com/news/model-context-protocol).

## Overview

This tool provides a convenient way to analyze AWS Bedrock model invocation logs using Anthropic's Claude model as an interactive interface. It functions as an MCP server that exposes AWS CloudWatch Logs API functionality to Claude, allowing you to query and analyze your Bedrock usage data in natural language.

## Features

- **Model Usage Analysis**: View detailed statistics about Bedrock model usage and token consumption
- **User-based Analytics**: Analyze usage patterns and costs by user
- **Daily Usage Reports**: Track daily usage trends and model invocations
- **Token Consumption Metrics**: Monitor input, completion, and total token usage
- **Interactive Interface**: Use Claude to query your Bedrock usage data through natural language

## Requirements

- Python 3.13+
- AWS credentials with CloudWatch Logs access
- Anthropic API access (for Claude integration)

## Installation

1. Install `uv`:
   ```bash
   # On macOS and Linux
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```
   
   ```powershell
   # On Windows
   powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```

2. Clone this repository:
   ```
   git clone https://github.com/dheerajoruganty/aws-bedrock-logs-mcp.git
   cd aws-bedrock-logs-mcp
   ```

3. Set up the Python virtual environment and install dependencies:
   ```
   uv venv && source .venv/bin/activate && uv pip sync pyproject.toml
   ```
   
4. Configure your AWS credentials:
   ```
   mkdir -p ~/.aws
   # Set up your credentials in ~/.aws/credentials and ~/.aws/config
   ```

## Usage

### Starting the Server

Run the server using:

```
python cloudwatch_mcp_server.py
```

By default, the server uses stdio transport for communication with MCP clients.

### Claude Desktop Configuration

Configure this tool with Claude Desktop:

```json
{
  "mcpServers": {
    "aws_bedrock_logs": {
      "command": "uv",
      "args": [
          "--directory",
          "/path/to/aws-bedrock-logs-mcp",
          "run",
          "cloudwatch_mcp_server.py"
      ]
    }
  }
}
```

Make sure to replace the directory path with the actual path to your repository on your system.

### Available Tools

The server exposes the following tools that Claude can use:

1. **`get_bedrock_logs_df`**: Retrieve raw Bedrock invocation logs as a pandas DataFrame
2. **`get_model_usage_stats`**: Get usage statistics grouped by model
3. **`get_user_usage_stats`**: Get usage statistics grouped by user
4. **`get_daily_usage_stats`**: Get daily usage statistics and trends

### Example Queries

Once connected to Claude through an MCP-enabled interface, you can ask questions like:

- "Show me the Bedrock usage stats for the last 7 days"
- "What's the average token consumption by model?"
- "Who are the top users of Bedrock in terms of total tokens?"
- "Give me a daily breakdown of model invocations"

## Development

### Project Structure

- `cloudwatch_mcp_server.py`: Main server implementation with MCP tools
- `pyproject.toml`: Project dependencies and metadata
- `Dockerfile`: Container definition for deployments

### Dependencies

Key dependencies include:
- `boto3`: AWS SDK for Python
- `mcp[cli]`: Anthropic's Model Control Protocol
- `pandas`: Data manipulation and analysis
- `pydantic`: Data validation using Python type annotations

## License

[MIT License](LICENSE)

## Acknowledgments

- This tool uses Anthropic's MCP framework
- Powered by AWS CloudWatch Logs API
- Built with [FastMCP](https://github.com/jlowin/fastmcp) for server implementation 