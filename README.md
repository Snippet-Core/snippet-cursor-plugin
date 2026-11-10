# Snippet: Brand Deals for Creators (MCP server and Cursor plugin)

Brand offer in your inbox? Get a 0-100 contract score, a fair rate range from your views, and a reply you approve before it sends.

Snippet is an AI talent manager for UGC, YouTube, TikTok and Instagram creators. This MCP server connects your Snippet account to Claude, ChatGPT, Cursor and other MCP clients so you can price sponsorships, review brand contracts, read brand emails and answer brands, with your approval on every send.

Remote server: https://usesnippet.app/api/mcp (Streamable HTTP, OAuth, Snippet account required)

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

## Tools

The remote MCP server at `https://usesnippet.app/api/mcp` exposes these 13 tools after you sign in with a Snippet account:

| Tool | What it does |
| --- | --- |
| get_manager_briefing | Summarizes what needs you, deals in motion, and this week's work. Read-only. |
| list_deals | Lists your brand deals, with stage, offer value, and what is waiting on you. Read-only. |
| get_deal | Returns one deal in full, including terms, recommended rate, and linked email threads. Read-only. |
| search_inbox | Finds brand-deal email conversations. Not a general mailbox search. Read-only. |
| get_inbox_thread | Reads one brand email thread and any reply Snippet already prepared. Read-only. |
| draft_reply | Drafts a brand reply in your voice. It sends nothing until you approve the text. |
| send_reply | Sends the approved reply from your Gmail. Use only after you approve the exact text. |
| get_rate_card | Returns what you charge and will accept, plus measured views per platform. Read-only. |
| estimate_sponsorship_rate | Returns a low-to-high rate range and a recommended ask from your measured views and published CPM benchmarks. Read-only. |
| find_brand_matches | Lists brands Snippet has matched to you, with a reason each one fits. Read-only. |
| review_brand_contract | Reviews a brand contract with a 0-100 creator-friendliness score and the clauses that cost you. Advisory, not legal advice. |
| get_work_log | Lists what Snippet has done for you, newest first. Read-only. |
| answer_decision | Acts on a decision Snippet is holding, only after you give an explicit yes. |

## Example prompts

- What brand deals need me today?
- How much should I charge for a YouTube sponsorship?
- Read my latest brand email and draft a reply that asks for a higher rate.

## Other MCP clients (including Cline)

Connect to `https://usesnippet.app/api/mcp` using Streamable HTTP and your
client's browser-based OAuth flow. No local Snippet server or API key is needed.
See [llms-install.md](llms-install.md) for Cline configuration and safe verification.
A Snippet account with access is required. Stop if OAuth fails; do not invent a
client ID, paste tokens into configuration, or bypass client consent.

## Hermes Agent

A Portable Agent Plugin for [Hermes Agent](https://hermes-agent.nousresearch.com) is in [`hermes/`](hermes/) (`plugin.json`, `mcp.json`, and a Hermes-specific guide). It uses the same remote MCP endpoint, `https://usesnippet.app/api/mcp`. The public plugin-only package, including that directory, is MIT licensed.

## Directory artwork

- [400 × 400 PNG icon](assets/icon-400.png)
- [Transparent padded logo](assets/logo-padded.png) (400 × 400; 40 transparent pixels on every edge)

These assets are derived from the existing Snippet plugin logo. The padded
variant retains the original dark tile within a transparent outer margin so it
stays legible on light and dark surfaces.
