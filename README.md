# MCP Coinbase Commerce Server

This is a Model Context Protocol (MCP) server that connects to the Coinbase Commerce API, allowing AI assistants like Claude to generate cryptocurrency payment links.

## Features

- Generate Coinbase Commerce payment links
- Retrieve information about existing charges
- Secure API key management
- Easy integration with Claude and other MCP-compatible AI assistants

## Setup

1. Clone this repository
2. Run `npm install` to install dependencies
3. Copy `.env.example` to `.env` and add your Coinbase Commerce API key
4. Build the project: `npm run build`
5. Start the server: `npm start`

## Usage with Claude

Once the server is running, it can be connected to Claude for Desktop using the MCP configuration.

1. Configure Claude for Desktop to use this server
2. Ask Claude to generate a payment link with specified amount and currency
3. Claude will use the tool to create a payment link via the Coinbase Commerce API

## API Tools

- `create-charge`: Generate a new payment link
- `get-charge`: Retrieve information about an existing charge

## License

MIT