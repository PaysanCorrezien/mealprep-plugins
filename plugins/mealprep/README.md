# Mealprep · seven tools

MCP endpoint: https://mealprep.tail66a3d.ts.net/mcp
Connection page and package updates: https://mealprep.tail66a3d.ts.net/plugins
Privacy: https://mealprep.tail66a3d.ts.net/plugins/privacy
Authentication: OAuth, one household and read-only permission by default.
This package contains connection metadata and a workflow skill, with no credentials.

## ChatGPT

Install Mealprep from the marketplace in ChatGPT Plugins and enable it.
The package includes the MCP connection: complete its built-in OAuth prompt, sign in and select the household. No separate MCP registration or copied credential is needed in hosts supporting bundled servers.
If an earlier version was installed, refresh the marketplace and update to 2.3.3 or later, then reopen the conversation.
Account/workspace policies apply. Hosts that do not support bundled MCP servers need a registered cloud connector; this package does not fabricate an app ID.

## Claude

For Claude cloud, open connector settings, add the endpoint and authenticate with OAuth.
For Claude Code 2.1.224+, add the hosted marketplace:
claude plugin marketplace add https://mealprep.tail66a3d.ts.net/plugins/marketplace.json
claude plugin install mealprep@mealprep-plugins
Then open /mcp and authenticate.

Offline alternative: extract as mealprep-agent, run claude --plugin-dir ./mealprep-agent, then open /mcp and authenticate.
Alternatively: claude mcp add --transport http mealprep 'https://mealprep.tail66a3d.ts.net/mcp'

## Codex / portable plugin hosts

Install this directory through a local marketplace; its MCP server is bundled automatically. Complete OAuth when prompted.
For a CLI client that does not prompt automatically, run codex mcp login mealprep --scopes mealprep.read. Do not add a duplicate server.

For hosts supporting Agent Plugins,
Merge this entry into .agents/plugins/marketplace.json without replacing other entries:

{
  "name": "local-mealprep",
  "plugins": [
    {
      "name": "mealprep",
      "source": {
        "source": "local",
        "path": "./plugins/mealprep"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Productivity"
    }
  ]
}

## First request

“Look at my stock, suggest three dinners, and explain what I need. Do not change anything yet.”

The seven tools progressively reveal exact action schemas. Read before changing data; preview, explain and apply only within user authorization. Keep client approval prompts enabled.

## Reachability and security

A private Tailscale Serve address works for clients on the tailnet. It does not automatically work for ChatGPT or Claude cloud. ChatGPT can use a registered Secure MCP Tunnel where supported; both providers can use a separately secured public HTTPS endpoint. Public exposure must use the dedicated authenticated listener, never the LAN/private auto-login listener. This download enables no route or tunnel and does not publish a marketplace listing.

Each client gets a separate revocable OAuth grant. Do not put passwords, API keys or tokens in plugin files. Read-only is the default; request mealprep.write and explicitly grant it only when changes are needed.

Documentation: https://developers.openai.com/plugins/build/plugins and https://code.claude.com/docs/en/mcp
