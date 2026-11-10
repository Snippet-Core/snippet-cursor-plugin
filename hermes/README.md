# Snippet for Hermes Agent

[Snippet](https://usesnippet.app) helps creators manage brand deals, sponsorship offers and brand replies.

This Portable Agent Plugin contains only `plugin.json`, `mcp.json` and this guide. It does not include Snippet application source. The package is published under the MIT license of [Snippet-Core/snippet-cursor-plugin](https://github.com/Snippet-Core/snippet-cursor-plugin). A Snippet account is required; some actions require an active plan and available allowances. Service terms and pricing remain at [Snippet](https://usesnippet.app); this package grants no paid entitlement.

## Connection

The remote MCP endpoint is `https://usesnippet.app/api/mcp` (Streamable HTTP). After you sign in, the hosted server currently exposes 13 tools: `get_manager_briefing`, `list_deals`, `get_deal`, `search_inbox`, `get_inbox_thread`, `draft_reply`, `send_reply`, `get_rate_card`, `estimate_sponsorship_rate`, `find_brand_matches`, `review_brand_contract`, `get_work_log`, and `answer_decision`. The live tool list comes from the hosted service and is not pinned by this package's commit SHA. There is no local server or package dependency to install.

Use Hermes 0.23.0 or later: that release includes the remote portable transport and the `untrusted` extension this package requests.

Portable MCP has no `auth` field. Do not add OAuth fields or bearer tokens to `mcp.json`. `hermes mcp login snippet` against the portable package entry is not a working sign-in path today (see upstream [issue 87253](https://github.com/NousResearch/hermes-agent/issues/87253)).

To sign in, add a native connection in an interactive session (no credentials in this file):

```bash
hermes mcp add snippet --url https://usesnippet.app/api/mcp --auth oauth
```

Then complete browser authorization when prompted, or use the equivalent `~/.hermes/config.yaml` settings:

```yaml
mcp_servers:
  snippet:
    url: https://usesnippet.app/api/mcp
    auth: oauth
    trust: untrusted
```

A same-name native entry replaces the package's server entry, including the `trust: untrusted` policy. After sign-in, add `trust: untrusted` to `mcp_servers.snippet` if you want Hermes to keep asking before write tools and to block them in unattended runs. If authorization is cancelled or fails, stop and retry interactively; never copy tokens from another client. Do not start OAuth in unattended jobs. Disconnect via Hermes's MCP controls and revoke access in Snippet settings when finished.

Install a reviewed copy of this package with `hermes plugins install <repo> --ref <full-40-character-sha> --no-enable` (use `subdir` `hermes` when installing from this repository), inspect it, then explicitly enable `snippet`.

## Rule 13 disclosures

- **Network and data:** Hermes connects to Snippet's hosted service over HTTPS. Tool arguments and results can contain creator account data, brand correspondence, deal details and contract content. Only connect an account you are authorized to use. The service may use its own downstream integrations; this manifest does not audit or pin the hosted backend. Its deployed behavior, including the tool list, can change independently of the package SHA. See [Privacy](https://usesnippet.app/privacy) and [Terms](https://usesnippet.app/terms).
- **Reads and writes:** Account tools can read private account content. Some tools, including `send_reply`, can send brand messages or change deal or account state. The package requests Hermes's `untrusted` policy so calls without `readOnlyHint: true` require user approval and fail closed unattended. Review tool names, arguments and server annotations; do not treat this as a sandbox or blanket authorization. Other Agent Plugin hosts may ignore the Hermes extension. If you sign in with `hermes mcp add`, preserve `trust: untrusted` as described above.
- **Credentials:** The package contains no credentials, headers, environment secrets or custom credential code. OAuth credentials for the native sign-in path are stored and refreshed by Hermes's MCP client, never read by this package.
- **Local execution/background work:** No executable, shell command, setup hook, dependency, self-updater, UI or background process is supplied. Hermes itself runs its normal MCP client while connected. No local file reader is declared.
- **Telemetry:** The package adds no telemetry or usage-reporting code. Hosted-service logging and analytics follow [Snippet's privacy policy](https://usesnippet.app/privacy).

Support: [Snippet support](https://usesnippet.app/support).
