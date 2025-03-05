# MCP Coinbase Commerce Server

This is a Model Context Protocol (MCP) server that connects to the Coinbase Commerce API, allowing AI assistants like Claude to generate cryptocurrency payment links.

## Features

- Generate Coinbase Commerce payment links with customizable amount, currency, and description
- Retrieve information about existing charges
- Secure API key management
- Easy integration with Claude and other MCP-compatible AI assistants

## Prerequisites

- Node.js 16.0+
- A Coinbase Commerce account
- Coinbase Commerce API key ([Get one here](https://commerce.coinbase.com/dashboard/settings))

## Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/zhangzhongnan928/mcp-coinbase-commerce.git
   cd mcp-coinbase-commerce
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Copy `.env.example` to `.env` and add your Coinbase Commerce API key:
   ```bash
   cp .env.example .env
   # Edit .env file with your API key
   ```

4. Build the project:
   ```bash
   npm run build
   ```

5. Start the server:
   ```bash
   npm start
   ```

## Usage with Claude for Desktop

Once the server is running, you can connect it to Claude for Desktop:

1. Open Claude for Desktop
2. Click on the Claude menu → Settings → Developer
3. Click "Edit Config" to open `claude_desktop_config.json`
4. Add the MCP server configuration:

```json
{
  "mcpServers": {
    "coinbase-commerce": {
      "command": "node",
      "args": ["/path/to/mcp-coinbase-commerce/dist/index.js"],
      "env": {
        "COINBASE_COMMERCE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

5. Save the file and restart Claude for Desktop
6. You should now see a hammer icon in the chat interface, indicating available tools

## Example Prompts for Claude

Once connected, you can ask Claude to generate payment links:

- "Can you create a payment link for $10 USD donations to my project?"
- "Generate a Coinbase Commerce payment link for my coffee shop with a price of $5.50"
- "Look up the payment status for charge ID 93e23c3e-8220-4e6c-9bc3-ea3548339621"

Claude will use the appropriate tools to fulfill these requests, generating payment links you can share with customers.

## API Tools

### `create-charge`

Generates a new payment link with the following parameters:

- `name`: Name of the payment/product
- `description`: Description of what the payment is for
- `amount`: Payment amount (e.g., "10.00")
- `currency`: Currency code (e.g., "USD", "EUR", "BTC")
- `redirectUrl` (optional): URL to redirect after payment completes

### `get-charge`

Retrieves information about an existing charge using:

- `chargeId`: ID of the charge to retrieve

## Development

To run the server in development mode:

```bash
npm run dev
```

## Testing with MCP Inspector

You can test the server using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector):

```bash
npx @modelcontextprotocol/inspector node dist/index.js
```

## License

MIT