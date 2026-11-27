# Datadog Antigravity Plugin

Query your Datadog data directly from Antigravity using natural language. Ask about logs, metrics, traces, dashboards, monitors, and more.

## What you need

- A [Datadog](https://www.datadoghq.com/) account
- [Antigravity](https://antigravity.google/) (app, IDE, or CLI) with plugin support

## Getting started

Setup takes four steps. For a full walkthrough with screenshots and troubleshooting, see the [installation guide](docs/plugin-installation.md).

1. **Install the plugin.** In **Customizations**, search the **Marketplace** tab for **Datadog** and click **+**. An MCP error at this point is expected, because the Datadog site isn't set up yet. From the CLI, run `agy plugin install datadog@antigravity-plugins-partners` instead.
2. **Run `/ddsetup`** in the chat and choose your Datadog site.
3. **Restart the Datadog MCP server** from the plugin's **MCP** tab (⋮ → **Restart**).
4. **Sign in** from the plugin's **Accounts** tab and approve access in your browser.

### Notes

If you already have a Datadog MCP server registered separately (for example, a `datadog` entry in your own `mcp_config.json`), disable or remove it to avoid conflicts.

## Using the plugin

Once connected, just ask the agent anything about your Datadog data:

```
Show me error logs for the "checkout" service from the last hour
```

```
What monitors are currently alerting?
```

```
Find traces for service "api-gateway" with latency > 500ms
```

```
List my dashboards
```

## Can't connect?

**Never connected before?** Run the `/ddsetup` command in Antigravity. It will help you provide the correct Datadog MCP domain and set up the MCP server.

**Was working before but stopped?** Run the `/ddconfig` command in Antigravity. It will check your site, authentication status, and network access to help diagnose the issue.

**Stopped working after a plugin update?** Updating the plugin resets its configuration. Run `/ddsetup` again to reconnect.

## Changing settings

The plugin provides a few commands you can run in the agent to manage configuration:

- `/ddconfig` — change your Datadog site or switch organizations
- `/ddtoolsets` — enable or disable groups of tools

After any configuration change, refresh the MCP servers before the new setting takes effect — the agent will tell you how.

## Good to know

- Authentication is handled via OAuth in your browser.
- No Datadog credentials are sent to the AI model provider.

## Support

- [Datadog MCP Server Documentation](https://docs.datadoghq.com/mcp_server/)

## Legal

See the [LICENSE](LICENSE) and [NOTICE](NOTICE) files included with this plugin.

For details on how Datadog handles your data, see the [Datadog Privacy Policy](https://www.datadoghq.com/legal/privacy).
