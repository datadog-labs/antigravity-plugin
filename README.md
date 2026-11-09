# Datadog Antigravity Plugin

Query your Datadog data directly from Antigravity using natural language. Ask about logs, metrics, traces, dashboards, monitors, and more.

## What you need

- A [Datadog](https://www.datadoghq.com/) account
- [Antigravity](https://antigravity.google/) (app, IDE, or CLI) with plugin support

## Getting started

1. Install the Datadog plugin from the Antigravity marketplace, using either the CLI or the app.

   **CLI:**

   ```
   agy plugin install datadog
   ```

   If you're prompted to choose a marketplace, specify it directly with `agy plugin install datadog@antigravity-plugins-partners`. Run `agy plugin list` to confirm that the plugin is installed and enabled. Plugins installed with the CLI are also available in the Antigravity app and IDE.

   **App or IDE:**

   1. In the left-hand sidebar, select **Skills & Customizations** (or go to **Settings → Customizations**).
   2. Open the **Marketplace** tab and search for **Datadog**.
   3. Click **Install**, then restart Antigravity if prompted so the plugin's MCP server and skills load.

   You can also open the plugin controls by typing `/plugin` in the chat input.

2. Run `/ddsetup` in Antigravity to connect the plugin to your Datadog account. The agent will guide you through selecting the correct Datadog MCP domain. You can run this again at any time.
3. Follow the agent's instructions to refresh the MCP servers and sign in to Datadog in your browser.

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
