# Snippet for Cursor

Connect your Snippet talent manager to work on creator brand deals, sponsorship
rates, brand emails, held decisions and contract reviews from Cursor.

This repository is the standalone public Cursor Agent Plugin for Snippet (MIT).
It contains only the plugin package. It does not include Snippet application source.

## Connect

Install the plugin from Cursor's marketplace once approved. Enable the Snippet
MCP server and follow Cursor's OAuth sign-in flow to connect your Snippet account.
The remote endpoint is `https://usesnippet.app/api/mcp` using Streamable HTTP.
No local server, API key or environment variables are required. A Snippet account
is required; available account features depend on the account's access.

Ask “What brand deals need me today?” or “How much should I charge for a YouTube
sponsorship?” The talent-manager skill explains the tools and requires explicit
approval before sending a brand email or applying a held decision. Tool results
are the source of truth; do not invent rates, brands or deal progress.

If connection fails, check that the server is enabled and reconnect through
Cursor's MCP controls. Do not paste access tokens into prompts or config files.
Disconnect the client from Snippet settings to revoke access.

Website: https://usesnippet.app · Privacy: https://usesnippet.app/privacy ·
Terms: https://usesnippet.app/terms · Support: https://usesnippet.app/support

## License

MIT. See [LICENSE](LICENSE).
