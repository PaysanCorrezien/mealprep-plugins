# Mealprep plugin marketplace

Public, credential-free plugin distribution for Mealprep. The application repository and its history are not included.

## Install in ChatGPT or Claude — no terminal needed

Copy this marketplace source:

```text
https://github.com/PaysanCorrezien/mealprep-plugins.git
```

**ChatGPT:** [Open Plugins](https://chatgpt.com/plugins) → **+ → Add plugin marketplace**. Paste the source, set **Git ref** to `main`, leave **Sparse paths** empty, then install **Mealprep**. Complete Mealprep’s built-in OAuth connection. Select your household, with Full access selected by default for owners/editors, or choose Read only. The MCP connection is already bundled; do not add a second server. In a new conversation, select Mealprep with `@`.

**Claude Chat / Cowork / Desktop:** [Open Customize → Plugins](https://claude.ai/customize/plugins) → **Add → Add marketplace**. Paste the same source and add **Mealprep**. Open the plugin’s **Connectors** tab → **Mealprep → Add / Connect**, then complete Mealprep OAuth. The connector must show **Connected** before tools can read your stock. The plugin is saved to your Claude account; a CLI installation is machine-local instead.

Availability depends on the client, account and organization policies. If your ChatGPT mode has no marketplace option, use the custom MCP connection below. Claude also accepts the [plugin ZIP](https://mealprep.tail66a3d.ts.net/plugins/mealprep.zip) through **Add → Upload plugin**.

Try: “Read my stock, suggest three dinners and explain what is missing. Do not change anything yet.”

[Guided setup and connection management](https://mealprep.tail66a3d.ts.net/plugins)

## Already installed but no tools?

Update to **2.3.4**: refresh this marketplace in your client, update Mealprep, and reopen the conversation. Complete the plugin’s built-in OAuth connection. Versions 2.3.0 and 2.3.1 could appear installed while current OpenAI clients silently rejected their MCP authentication metadata. Version 2.3.2 fixed that loader incompatibility. Version 2.3.4 adds Full access as the default consent choice for owners/editors. Since 2.3.3 there is one workflow skill focused on using the tools; authentication uses the client’s built-in Connect flow, with no separate setup skill.

Native acceptance with Codex 0.165.0 verifies bundled server discovery, real browser OAuth, all seven tools, and actual overview/stock calls. Installation alone is not treated as a successful connection. Hosted ChatGPT modes that require a registered cloud connector still have their own account-side registration requirements; this repository does not invent an app ID.

## Marketplace field values

- Source: https://github.com/PaysanCorrezien/mealprep-plugins.git
- Git ref: main
- Sparse paths: leave empty

Select Mealprep from this marketplace, install and enable it. Complete OAuth with your Mealprep account when prompted; select one household and choose Full access (default for owners/editors) or Read only. A Git repository URL belongs in the marketplace Source field. Do not paste an MCP endpoint, ZIP URL or marketplace JSON URL there.

CLI alternative:

```sh
codex plugin marketplace add https://github.com/PaysanCorrezien/mealprep-plugins.git --ref main
codex plugin add mealprep@mealprep-plugins
```

## ChatGPT cloud

A Git marketplace is distinct from a registered ChatGPT cloud connection. Use ChatGPT Plugins > + > Add custom MCP server, URL **https://mealprep.tail66a3d.ts.net/mcp**, OAuth, then Create as a plugin. Account/workspace policies apply. If building a local package around a registered cloud connection, use only the actual plugin_asdk_app ID supplied by your account; none is fabricated in this repository.

## Claude Code

```sh
claude plugin marketplace add https://github.com/PaysanCorrezien/mealprep-plugins.git
claude plugin install mealprep@mealprep-plugins
```

Open /mcp and complete OAuth. For Claude cloud, add the MCP URL in connector settings instead.

## Connection and security

Setup: https://mealprep.tail66a3d.ts.net/plugins

Seven progressively-discovered MCP tools cover recipes, food data, stock, planning, cooking and consumption. Each client must authenticate separately. No passwords, tokens, API keys, client secrets or household data are included. Full access is selected by default for owners/editors when the client requests it; you can choose Read only. Explicit read-only requests and viewer memberships stay read-only. Existing read-only grants require reconnecting and a new consent to enable writes. Preserve client approval prompts and revoke access in Mealprep Settings.

GitHub reachability and Mealprep reachability are separate. If installation succeeds but OAuth times out on a Tailscale client, resolve the deployment's TCP/443 tailnet grant; do not weaken TLS verification or expose its private/LAN auto-login listener.

This repository does not constitute an approved public-directory listing. Successful marketplace installation alone is not evidence of a working ChatGPT conversation.

Official documentation: https://developers.openai.com/plugins/build/plugins, https://developers.openai.com/plugins/deploy/connect-chatgpt and https://claude.com/docs/plugins/overview
