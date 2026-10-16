<p align="center">
  <a href="https://roar-ai.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/roar-logo-white.png">
      <img src="assets/roar-logo-dark.png" alt="Roar AI" width="220">
    </picture>
  </a>
</p>

<h3 align="center">The Roar AI MCP server: every AI model and app hosting, run from your AI assistant</h3>

<p align="center">
  <a href="https://roar-ai.com">Website</a> ·
  <a href="https://roar-ai.com/docs/mcp">MCP docs</a> ·
  <a href="https://roar-ai.com/models">Models</a> ·
  <a href="https://roar-ai.com/pricing">Pricing</a> ·
  <a href="https://cloud.roar-ai.com">Sign in</a>
</p>

<p align="center">
  <a href="https://claude.ai/directory/connectors/roar-ai"><img alt="Listed in Claude's connector directory" src="https://img.shields.io/badge/Claude-connector%20directory-D97757"></a>
  <a href="https://cursor.com/en/install-mcp?name=roar&config=eyJ1cmwiOiJodHRwczovL2Nsb3VkLnJvYXItYWkuY29tL21jcCJ9"><img alt="Add to Cursor" src="https://img.shields.io/badge/Cursor-Add%20to%20Cursor-000000"></a>
  <a href="https://insiders.vscode.dev/redirect/mcp/install?name=roar&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fcloud.roar-ai.com%2Fmcp%22%7D"><img alt="Add to VS Code" src="https://img.shields.io/badge/VS%20Code-Add%20to%20VS%20Code-0098FF"></a>
  <img alt="Remote MCP · Streamable HTTP · OAuth" src="https://img.shields.io/badge/MCP-remote%20%C2%B7%20OAuth-555">
</p>

---

[Roar AI](https://roar-ai.com) is an **[AI gateway](https://roar-ai.com/gateway)** and an **[app hosting platform](https://roar-ai.com/hosting)** for teams. This repository is the home of its **remote MCP server**, the one address that lets Claude, ChatGPT, Codex, Cursor, VS Code and any other MCP client work in your Roar AI account for you:

```
https://cloud.roar-ai.com/mcp
```

Connect once and sign in with your Roar AI account. There is nothing to install, no API key to paste, and no server to run.

## What you can ask

> "Deploy my GitHub repo and give me the live link."
>
> "My last deploy failed. Find out why and fix it."
>
> "Add a Postgres database to my app and wire it up."
>
> "Point app.example.com at my app."
>
> "Create an API key for my app with a $50 monthly limit."
>
> "What did we spend on AI this week, and on which models?"
>
> "Ask a different model to review this function, and compare the two answers."

## Connect it

New to Roar AI? You can create an account during the connect step itself. Your assistant opens a Roar AI sign-in page, you enter your email and a 6-digit code, and you're back in the conversation.

<details open>
<summary><b>Claude</b> (claude.ai and the desktop app)</summary>

**Easiest:** open [Roar AI in Claude's connector directory](https://claude.ai/directory/connectors/roar-ai) and click **Connect**.

**Or add it yourself:** go to **Settings → Connectors → Add custom connector** and paste:

```
https://cloud.roar-ai.com/mcp
```
</details>

<details>
<summary><b>Claude Code</b></summary>

Install it as a plugin from this repository:

```bash
claude plugin marketplace add Roar-AI-Labs/roar-ai-mcp
claude plugin install roar-ai@roar-ai
```

Or add the server directly:

```bash
claude mcp add --transport http roar https://cloud.roar-ai.com/mcp
```

The Claude desktop app does not include the `claude` command. Claude Code is installed separately.
</details>

<details>
<summary><b>ChatGPT</b></summary>

Go to **Settings → Connectors → Advanced**, turn on **Developer mode**, then press **Create**. Name it *Roar AI*, set authentication to **OAuth**, and paste `https://cloud.roar-ai.com/mcp`. ChatGPT then opens the Roar AI sign-in page for you to approve.

A one-click listing in ChatGPT's plugin directory is on its way. Its package lives in [`chatgpt-plugin/`](chatgpt-plugin).
</details>

<details>
<summary><b>Codex</b> (CLI, IDE extension and the ChatGPT desktop app)</summary>

```bash
codex mcp add roar --url https://cloud.roar-ai.com/mcp && codex mcp login roar
```

Or add it to `~/.codex/config.toml`, then run `codex mcp login roar`:

```toml
[mcp_servers.roar]
url = "https://cloud.roar-ai.com/mcp"
```
</details>

<details>
<summary><b>Cursor</b></summary>

[**Add to Cursor**](https://cursor.com/en/install-mcp?name=roar&config=eyJ1cmwiOiJodHRwczovL2Nsb3VkLnJvYXItYWkuY29tL21jcCJ9) in one click, or add this to `~/.cursor/mcp.json` (or `.cursor/mcp.json` for one project):

```json
{
  "mcpServers": {
    "roar": { "url": "https://cloud.roar-ai.com/mcp" }
  }
}
```
</details>

<details>
<summary><b>VS Code / GitHub Copilot</b></summary>

[**Add to VS Code**](https://insiders.vscode.dev/redirect/mcp/install?name=roar&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fcloud.roar-ai.com%2Fmcp%22%7D) in one click, or run **MCP: Open User Configuration** (or create `.vscode/mcp.json`) and add:

```json
{
  "servers": {
    "roar": { "type": "http", "url": "https://cloud.roar-ai.com/mcp" }
  }
}
```

VS Code names this block `servers`. Every other tool names it `mcpServers`, and pasting the wrong one fails without an error.
</details>

<details>
<summary><b>OpenCode</b></summary>

Add this to `opencode.json`:

```json
{
  "mcp": {
    "roar": { "type": "remote", "url": "https://cloud.roar-ai.com/mcp", "enabled": true }
  }
}
```
</details>

<details>
<summary><b>Anything else</b> (Windsurf, Cline, Continue, JetBrains, Zed and more)</summary>

Paste `https://cloud.roar-ai.com/mcp` wherever the tool asks for a remote MCP server. If it uses a config file, this is the standard shape:

```json
{
  "mcpServers": {
    "roar": { "url": "https://cloud.roar-ai.com/mcp" }
  }
}
```
</details>

## What it can do

The server exposes around 90 tools. Your assistant picks the right one from what you ask.

| Area | For example |
|---|---|
| **AI models** | List the [200+ models](https://roar-ai.com/models) you can use, send a message to any of them, generate an image. Calls are billed to your Roar AI account under a monthly cap you set. |
| **API keys and spend** | Create, limit, rotate and revoke API keys, check usage and budgets, and look up a single request when you need to debug it. |
| **App hosting** | Deploy from GitHub or any git repo, watch a deploy until it finishes, read build and runtime logs, fix a failed deploy, roll back, stop and start. |
| **Databases and storage** | Add Postgres to an app, check its health, read its schema, run a query, and add file storage. |
| **Domains** | Add a custom domain or a free one, check its DNS, and choose the primary address. |
| **Config and jobs** | Set environment variables, schedule cron jobs and run them, and manage webhooks. |
| **Projects and team** | Organise apps into projects, and add or remove people. |

## Security and permissions

- **You sign in with OAuth.** Your assistant never sees a password or a long-lived key.
- **It can only do what you can.** Every action goes through the same permission checks as the [Roar AI console](https://cloud.roar-ai.com). A teammate with read-only access gets a read-only assistant.
- **Sensitive reads are opt-in.** Reading the rows inside your app's database, or prompts stored in your request logs, needs a permission you grant separately.
- **One company at a time.** If you belong to more than one, you choose which one your assistant works in, and you can switch by asking it.
- **AI spend has a cap.** The model calls your assistant makes go through their own key with a monthly limit, which you can pause or change in the console.

See [Security at Roar AI](https://roar-ai.com/security) for how we handle data, residency and compliance.

## About Roar AI

Roar AI gives a team two things behind one account:

- **An [OpenAI-compatible AI gateway](https://roar-ai.com/gateway).** One API key reaches [200+ frontier and open-source models](https://roar-ai.com/models), with fixed published prices, spending limits per key and per project, and one bill. Read the [API docs](https://roar-ai.com/docs/api).
- **[App hosting](https://roar-ai.com/hosting) built for people who vibe-code.** Pick a repo and get a live URL, with a database, a domain and logs, without touching a server. Apps run in the region you choose, including [in-country hosting](https://roar-ai.com/sovereign-ai) for teams that need their data to stay local.

Start at [roar-ai.com](https://roar-ai.com), or read the [quickstart](https://roar-ai.com/docs/quickstart).

## What's in this repository

| Path | What it is |
|---|---|
| [`.claude-plugin/`](.claude-plugin) and [`plugins/roar-ai/`](plugins/roar-ai) | A Claude Code plugin marketplace with one plugin, the Roar AI MCP server |
| [`chatgpt-plugin/`](chatgpt-plugin) | The package for OpenAI's ChatGPT and Codex plugin directory |
| [`server.json`](server.json) | The listing for the [official MCP Registry](https://registry.modelcontextprotocol.io) |
| [`docs/publishing.md`](docs/publishing.md) | How each listing is updated (for maintainers) |

The server itself is hosted by Roar AI, so there is no server code here, only the files that tell each assistant where to find it.

## Support

- Something not working? [Open an issue](https://github.com/Roar-AI-Labs/roar-ai-mcp/issues) or [contact us](https://roar-ai.com/contact-us).
- Read the [MCP guide](https://roar-ai.com/docs/mcp) and the [troubleshooting page](https://roar-ai.com/docs/troubleshooting).

## License

The configuration files in this repository are [MIT licensed](LICENSE). Using the Roar AI service is covered by the [Roar AI terms](https://roar-ai.com/terms) and [privacy policy](https://roar-ai.com/privacy).
