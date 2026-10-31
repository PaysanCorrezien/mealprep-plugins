# Mealprep plugin marketplace

Public, credential-free plugin distribution for Mealprep. The application repository and its history are not included.

## ChatGPT Desktop / Codex: Add plugin marketplace

- Source: https://github.com/PaysanCorrezien/mealprep-plugins.git
- Git ref: main
- Sparse paths: leave empty

Select Mealprep from this marketplace, install and enable it. Complete OAuth with your Mealprep account when prompted; select one household and begin with read-only access. A Git repository URL belongs in the marketplace Source field. Do not paste an MCP endpoint, ZIP URL or marketplace JSON URL there.

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

Seven progressively-discovered MCP tools cover recipes, food data, stock, planning, cooking and consumption. Each client must authenticate separately. No passwords, tokens, API keys, client secrets or household data are included. Read-only is the default; write access needs an explicit household grant. Preserve client approval prompts and revoke access in Mealprep Settings.

GitHub reachability and Mealprep reachability are separate. If installation succeeds but OAuth times out on a Tailscale client, resolve the deployment's TCP/443 tailnet grant; do not weaken TLS verification or expose its private/LAN auto-login listener.

This repository does not constitute an approved public-directory listing. Successful marketplace installation alone is not evidence of a working ChatGPT conversation.

Official documentation: https://developers.openai.com/plugins/build/plugins and https://developers.openai.com/plugins/deploy/connect-chatgpt
