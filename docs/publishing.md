# Publishing and updating the listings

For maintainers. Every listing points at the same hosted server, `https://cloud.roar-ai.com/mcp`, so a new tool appears everywhere without touching this repository. Only a change to a listing's own wording, logo or metadata needs an update here.

| Where | What lists us | How it updates |
|---|---|---|
| Claude's connector directory | Anthropic's listing at claude.ai/directory/connectors/roar-ai | Edited in Anthropic's submissions portal. Edits go through review |
| Claude Code | [`.claude-plugin/marketplace.json`](../.claude-plugin/marketplace.json) and [`plugins/roar-ai/`](../plugins/roar-ai) | Push to `main`. Raise `version` in `plugins/roar-ai/.claude-plugin/plugin.json` so installs pick it up |
| ChatGPT and Codex | [`chatgpt-plugin/`](../chatgpt-plugin) | Build the ZIP and upload it at platform.openai.com/plugins. An organisation owner submits |
| Official MCP Registry | [`server.json`](../server.json) | Raise `version`, then publish with `mcp-publisher` (below) |

## ChatGPT and Codex

Three things the review needs that are not in the ZIP:

1. **Domain verification.** The portal shows a token. Roar AI serves it at `https://cloud.roar-ai.com/.well-known/openai-apps-challenge` once an operator saves it in the Roar AI operator console. Then press Verify in the portal.
2. **A reviewer account** in the portal's *Review details* form. It must sign in without email codes or MFA, so it is a password account, in a demo workspace with credit and at least one live app, because the review cases list apps, read logs and report spend.
3. **A demo video** of the five positive review cases, linked from `extensions.com.openai.review.demo_recording_url` in `plugin.json`.

The positive review cases name real tools (`list_apps`, `get_deploy_status`, `get_app_logs`, `create_key`, `check_usage`). If one is renamed on the server, update the case here.

## Official MCP Registry

`server.json` uses the domain namespace `com.roar-ai/mcp`, so publishing proves control of `roar-ai.com` through a DNS record:

```bash
mcp-publisher login dns --domain roar-ai.com --private-key <key>
mcp-publisher publish
```

The DNS step adds a TXT record on `roar-ai.com` with the public key. See the registry's [authentication guide](https://github.com/modelcontextprotocol/registry/tree/main/docs) for generating the key pair.

## Checking a change

```bash
claude plugin validate .                     # the Claude Code marketplace and plugin
python3 -m json.tool server.json > /dev/null # and the same for each JSON file
```
