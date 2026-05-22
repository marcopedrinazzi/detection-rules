## Detection ideas for OpenTelemetry for Claude Code
Test lab: https://github.com/marcopedrinazzi/claude-code-otel-elastic-lab  
Source: https://code.claude.com/docs/en/monitoring-usage

- **Plugin installed from a third-party marketplace**: `event.name: "plugin_installed"`, `marketplace.is_official: "false"`.
- **Plugin loaded**: `event.name: "plugin_loaded"`. Interesting fields: `has_hooks` whether the plugin contributes hooks, `has_mcp` whether the plugin contributes MCP servers, `skill_path_count` number of skill directories the plugin declares, `command_path_count` number of command directories the plugin declares, `agent_path_count` number of agent directories the plugin declares. Good for threat hunting and inventory of plugins loaded.
- **Hook blocked an action**: `event.name: "hook_execution_complete"`, `num_blocking > 0`.
- **Hooks loaded**: `event.name: "hook_registered"`. Interesting fields: `hook_source` where the hook is defined: `"userSettings"`, `"projectSettings"`, `"localSettings"`, `"flagSettings"`, `"policySettings"`, or `"pluginHook"`. Good for threat hunting and inventory of hooks loaded.
- **MCP server connected**: `event.name: "mcp_server_connection"`. Interesting fields: `server_scope` scope the server is configured at, such as `"user"`, `"project"`, or `"local"`, `server_name`, and `transport_type`.
- **High number of auth failed attempts**: `event.name: "auth"`, `success: "true"` or `success: "false"`.
- **Permission mode changes**: `event.name: "permission_mode_changed"`.
- **Audit MCP activities**: `tool_result` event. Each MCP tool call has `tool_name` and `mcp_server_scope`, a `tool_parameters` payload containing `mcp_server_name` and `mcp_tool_name`, and a `tool_input` payload containing the call arguments. The `tool_decision` event records whether the call was allowed or denied, and whether the decision came from `config`, a `hook`, or the user.
- **Audit tool call decisions**: `event.name: "tool_decision"`. Interesting fields are `decision`, `tool_name`, and `source`, where the decision came from: `config`, `hook`, `user_permanent`, `user_temporary`, `user_abort`, or `user_reject`.
- **Audit commands run and files touched**: dangerous commands, sensitive files, etc. via `event.name: "tool_result"`:

```text
tool_parameters (when OTEL_LOG_TOOL_DETAILS=1): JSON string containing tool-specific parameters:
  - For Bash tool: bash_command, full_command, timeout, description, dangerouslyDisableSandbox, and git_commit_id
  - For MCP tools: mcp_server_name, mcp_tool_name
  - For Skill tool: skill_name
  - For Task tool: subagent_type

tool_input (when OTEL_LOG_TOOL_DETAILS=1): JSON-serialized tool arguments. Individual values over 512 characters are truncated, and the full payload is bounded to ~4 K characters. Applies to all tools including MCP tools.
```
- **Cost monitoring** can be done via the `api_request` event. It has a `cost_usd` field.
- **Raw API details**, when enabled, are `api_request_body` and `api_response_body`.
- **User prompts submitted** are monitored by the `user_prompt` event.

**Event correlation** can be done by `prompt.id`.

