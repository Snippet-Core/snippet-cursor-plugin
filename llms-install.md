# Install Snippet remote MCP

Homepage: https://usesnippet.app
Endpoint: `https://usesnippet.app/api/mcp`
Transport: Streamable HTTP. Authentication: browser OAuth with a Snippet account.
No local server, package build, environment variables or pasted API key required.

## Cline IDE extension

1. Open Cline's MCP Servers panel, then Remote Servers.
2. Add server name `snippet`, the endpoint above, and Streamable HTTP transport.
3. Follow Cline's OAuth sign-in/authorization flow for your Snippet account.
   Stop on any OAuth error and report the exact sanitized error. Do not invent
   client IDs, replace credentials, disable authentication, or retry through
   another account. Never put tokens in this repository or chat.
4. Verify the server is connected and tools are listed. Keep automatic tool
   approval disabled. Setup is not proven until this client completes OAuth
   and discovers tools.
5. In an approved sandbox only, explicitly approve one read-only call such as
   `get_manager_briefing`. Confirm its returned result; do not infer success
   from an HTTP 401 challenge or from a saved configuration entry.

For manual configuration, merge this entry under the existing `mcpServers`
object in Cline's Configure MCP Servers settings. Preserve all other entries.
This is the documented IDE format. Cline CLI 3.0.74 writes a nested
`transport` object instead; use its wizard/add command rather than replacing
CLI-generated settings with this IDE example.
Cline uses camelCase `streamableHttp`; do not copy the plugin manifest's
hyphenated `streamable-http` value into Cline settings.

```json
{
  "mcpServers": {
    "snippet": {
      "type": "streamableHttp",
      "url": "https://usesnippet.app/api/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

For current Cline CLI versions, `cline mcp` opens the MCP wizard with add/list
and Authorize OAuth actions. Use a dedicated test configuration directory;
check `cline --help` and `cline mcp --help` for the installed version. Do not
start an agent task or configure a paid model just to test the connection.

## Safety and troubleshooting

Do not call `send_reply` or `answer_decision` during installation QA. No email,
held decision, consequential write, account creation or spend is authorized.
If the client has no OAuth support, stop and use a supported client version.
If consent succeeds but tools do not appear, record the version, transport and
sanitized error rather than claiming compatibility. Disconnect using the
client's controls and revoke its connection in Snippet settings after QA.

Sources checked 2026-11-07:
- https://docs.cline.bot/mcp/mcp-overview
- https://github.com/cline/mcp-marketplace
