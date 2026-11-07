# Roar AI plugin for ChatGPT and Codex

The package for OpenAI's plugin directory, which ChatGPT and Codex share. It is in OpenAI's "Agent Plugins" layout:

| File | What it holds |
|---|---|
| [`plugin.json`](plugin.json) | The listing (name, subtitle, description, starter prompts, links, logo) and the review test cases |
| [`mcp.json`](mcp.json) | The server: `https://cloud.roar-ai.com/mcp` over streamable HTTP. Sign-in is OAuth, which ChatGPT discovers from the server, so the package carries no credentials |
| [`assets/logo.png`](assets/logo.png) | The square logo |
| [`skills/get-started/SKILL.md`](skills/get-started/SKILL.md) | The onboarding skill (`onboardingSkill` in `plugin.json`): ChatGPT runs it when someone sets the plugin up. It asks for their name and company, saves them with `set_up_account`, then shows what Roar AI can do |

The tool list is not in the package. OpenAI reads it from the server and re-scans daily, so a new tool reaches the listing without a new upload. A change to anything in `plugin.json` needs one.

## Build the ZIP

```bash
cd chatgpt-plugin && zip -r ../roar-ai-chatgpt-plugin.zip plugin.json mcp.json assets skills
```

Until the directory listing is live, anyone can connect ChatGPT to Roar AI by hand. See [Connect it](../README.md#connect-it).
