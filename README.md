# [Snippet](https://usesnippet.app) for Cursor and remote MCP

Connect your Snippet talent manager to work on creator brand deals, sponsorship
rates, brand emails, held decisions and contract reviews from Cursor.

This folder is a standalone Agent Plugin. Publish its contents at the root of an
approved public plugin repository, with an owner-approved open-source license.
Do not publish the application repository or the sibling reviewer materials.

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

## Other MCP clients (including Cline)

Connect to `https://usesnippet.app/api/mcp` using Streamable HTTP and your
client's browser-based OAuth flow. No local Snippet server or API key is needed.
See [llms-install.md](llms-install.md) for Cline configuration and safe verification.
A Snippet account with access is required. Stop if OAuth fails; do not invent a
client ID, paste tokens into configuration, or bypass client consent.

## Directory artwork

- [400 × 400 PNG icon](assets/icon-400.png)
- [Transparent padded logo](assets/logo-padded.png) (400 × 400; 40 transparent pixels on every edge)

These assets are derived from the existing Snippet plugin logo. The padded
variant retains the original dark tile within a transparent outer margin so it
stays legible on light and dark surfaces.
