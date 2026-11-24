---
name: visualizations
description: Choosing and presenting charts or product views to explore Datadog data, understand findings, or investigate issues, including without an explicit visualization request. Reuse helpful views and respect text/data-only requests. This is the plugin's local copy of the `datadog/visualizations` server skill; prefer it over fetching the server version.
---

# Visualization Guide

## When the Visualization Tools Are Unavailable

Discover `show_ui`, `get_widget`, or `visualize_tabular_data` on the plugin's Datadog MCP server if they are not exposed upfront. Use only tools that are actually available. If `show_ui` is absent, continue with direct `get_widget` or `visualize_tabular_data` as appropriate. If none of these tools can be discovered:

- If other Datadog MCP tools are available, the `visualizations` toolset may be disabled. Tell the user that Datadog charts are unavailable and suggest running `/ddtoolsets` to enable visualizations.
- If no Datadog MCP tools are available, the server is not set up or not working. Suggest running `/ddsetup`.

Then answer with the data you can retrieve, as text or a table. In this case only, the visualization rules below do not apply.

Use interactive views when they help users explore data, understand findings, or investigate an issue. Use them standalone or after analysis with other tools, including code execution. Consider useful views proactively; visualization is optional unless explicitly requested. Reuse existing helpful views, skip views that add no value, and respect text/data-only requests.

## Choose a view

Discover any tool named below if it is not already exposed.

- For new Datadog charts, use `show_ui` with source `get_widget` instead of calling `get_widget` directly. If `show_ui` is unavailable, use `get_widget` directly.
- For saved widget IDs or URLs, call `get_widget` directly, even when display is requested; do not wrap saved widgets in `show_ui`.
- For a supported product view, use `show_ui`, select a source from its live catalog, and follow the source schema. Do not infer support for unlisted sources.
- For computed rows that cannot be queried as a Datadog widget, call `visualize_tabular_data` directly. It is not a `show_ui` source.

Choose a time series for change over time, a toplist for ranked contributors, a query value for a KPI, or a distribution for spread. Use the incident view for event timelines; tabular charts need numeric values, not timestamps masquerading as measurements.

## Prepare and present

For explicit chart requests, render the requested view rather than stopping at retrieved data or a markdown table.

Use real identifiers, queries and time ranges from the investigation. For a saved widget, call `get_widget` directly with its URL or dashboard/widget IDs without rebuilding its definition. For a new definition, consult `ask_widget_expert` and replace placeholders with discovered telemetry.

For `show_ui`, pass source arguments in `data_tool_args`; omit widget `layout_args` except an optional `caption`. `show_ui` fetches its source data. Earlier investigation calls are fine; do not prefetch the source again just to prepare the view.

On explanatory follow-ups, refer to the existing view and evidence. Update it for new data, a different object, query, time range or filter, or an explicit request for a different presentation.

## Failures

Follow returned recovery guidance. For a new widget's schema error, continue the expert session with the failing field and error, then retry. For an empty saved widget, check its time range and filters. After two failed attempts at the same visualization, explain the blocker. A successful payload does not prove the view painted.
