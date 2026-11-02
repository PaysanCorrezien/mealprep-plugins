# Mealprep · 2.6.0

MCP endpoint: https://mealprep.tail66a3d.ts.net/mcp
Connection page and package updates: https://mealprep.tail66a3d.ts.net/plugins
Privacy: https://mealprep.tail66a3d.ts.net/plugins/privacy
Authentication: OAuth, one household, with Full access selected by default for owners/editors. Choose Read only on the consent page if preferred.
This package contains connection metadata and a workflow skill, with no credentials.

## ChatGPT

Install Mealprep from the marketplace in ChatGPT Plugins and enable it.
The package includes the MCP connection: complete its built-in OAuth prompt, sign in and select the household. No separate MCP registration or copied credential is needed in hosts supporting bundled servers.
If an earlier version was installed, refresh the marketplace and update to 2.6.0 or later, then reopen the conversation.
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
For a CLI client that does not prompt automatically, run codex mcp login mealprep --scopes mealprep.read,mealprep.write. Do not add a duplicate server.

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

Six direct food journal tools support product search, portion resolution, logging, correction, daily intake and explicit favorites. Seven advanced workflow tools progressively reveal other action schemas, and the optional read-only mealprep_render tool shows recipe/nutrition results in compatible hosts. Apply changes only within user authorization. Keep client approval prompts enabled.

## Reachability and security

A private Tailscale Serve address works for clients on the tailnet. It does not automatically work for ChatGPT or Claude cloud. ChatGPT can use a registered Secure MCP Tunnel where supported; both providers can use a separately secured public HTTPS endpoint. Public exposure must use the dedicated authenticated listener, never the LAN/private auto-login listener. This download enables no route or tunnel and does not publish a marketplace listing.

Each client gets a separate revocable OAuth grant. Do not put passwords, API keys or tokens in plugin files. Full access is selected by default for owners/editors when the client requests it; Read only remains available. Viewer memberships and explicit read-only scope requests remain read-only. Existing grants need a new connection and consent to change permissions.

Documentation: https://developers.openai.com/plugins/build/plugins and https://code.claude.com/docs/en/mcp
