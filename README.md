# WebDecoy for AI assistants

Connect your AI assistant to [WebDecoy](https://webdecoy.com) to install bot
detection in your app and ask about your sites: whether protection is actually
enforced, which bots were seen, and what an actor did.

Everything goes through WebDecoy's hosted MCP server at
`https://mcp.webdecoy.com/mcp`. You sign in with your WebDecoy account, then
choose which sites each assistant may see. Review or disconnect an assistant
any time in **Settings, Connected apps**.

## Claude Code

```
/plugin marketplace add WebDecoy/claude-plugins
/plugin install webdecoy@webdecoy
```

Restart Claude Code, run `/mcp` and sign in to **webdecoy**. Then ask it to
"install WebDecoy in this app", or run `/webdecoy:install`.

The plugin adds the MCP server, an install skill that follows WebDecoy's own
guide for your stack, and the `/webdecoy:install` command.

## Claude.ai and Claude Desktop

Settings, Connectors, **Add custom connector**, and enter:

```
https://mcp.webdecoy.com/mcp
```

## Codex

```
codex mcp add webdecoy --url https://mcp.webdecoy.com/mcp
codex mcp login webdecoy --scopes mcp:read,mcp:setup,offline_access
```

## ChatGPT

Settings, Apps and Connectors, **Create** (developer mode), and enter
`https://mcp.webdecoy.com/mcp` as the server URL with OAuth authentication.
Under the advanced OAuth settings, choose dynamic client registration.

## What the assistant can do

| Tool | What it does |
| --- | --- |
| `list_properties` | The sites you approved for this assistant |
| `get_protection_status` | Whether a site is actually protected, and why not |
| `search_detections` | Bot detections on a site, filterable by time and score |
| `get_actor_evidence` | What one actor did across a site |
| `get_current_policy` | What the site's policy is configured to do |
| `get_install_guide` | Install steps for your stack, with your public IDs filled in |
| `get_install_status` | Whether the install is reporting, plus a test request |
| `create_script_tag` | Create a site's detection script (needs setup permission) |
| `verify_install` | Check your own page serves the WebDecoy tag (needs setup permission) |
| `list_decoys` | The decoys on a site and their URLs |
| `create_decoy` | Create a decoy and get the code to hide it in your site (needs setup permission) |
| `create_site` | Add a new site, if you own the organization (needs setup permission) |

The assistant reads by default. The setup tools need you to tick **Also
allow setup** when you approve it; sites and decoys it creates count toward
your plan, and a site it adds joins only that assistant's access. It can never change your policies,
enforcement, settings or billing, and it never receives secret keys: install
guides name the environment variables and you set them yourself.

## Links

- Docs: https://docs.webdecoy.com
- Privacy: https://webdecoy.com/privacy
- Support: https://webdecoy.com/contact

## License

MIT
