# Kolbo AI plugin for Claude Code

Use [Kolbo.AI](https://kolbo.ai) generation tools — image, video, music, speech, chat, App Builder, artifact publishing — as native tools inside Claude Code.

## Install

```bash
claude plugin marketplace add Zoharvan12/kolbo-claude-plugin
claude plugin install kolbo@kolbo
```

You'll be prompted for your **Kolbo API key** once. Create one at https://app.kolbo.ai/settings/api-keys. The key is stored in your OS keychain.

That's it. Open a new Claude Code session and ask things like:

- "Generate an image of a sunset over mountains"
- "Make a 5-second video of waves crashing"
- "Lipsync this audio to this video"
- "Publish this HTML as a shareable page"
- "What's my Kolbo credit balance?"

The bundled skill teaches Claude Code how to route requests to the right Kolbo tool.

## Why this repo is intentionally tiny

Claude Code's plugin marketplace clones the entire source repo to disk on install. Some antivirus products (Bitdefender, Norton, etc.) trigger false-positive heuristics on large monorepos with thousands of build-tool files, fonts, and configs.

This repo deliberately ships **only the files Claude Code needs to load the plugin** — manifest, MCP pointer, skill markdown, README. Nothing else. The total install footprint is a handful of kilobytes, so AV has effectively nothing to scan.

## What's in here

| File | Purpose |
|---|---|
| `.claude-plugin/plugin.json` | Plugin manifest + `userConfig` for the API-key prompt |
| `.claude-plugin/marketplace.json` | One-line marketplace listing pointing at this repo |
| `.mcp.json` | Runs `npx -y @kolbo/mcp` with the user's key |
| `skills/kolbo/SKILL.md` | **Auto-generated** — synced from `kolbo-code/packages/opencode/skills/kolbo/SKILL.md` |

`SKILL.md` is a build artifact. Do not edit it here — edit the canonical source in [kolbo-code](https://github.com/Zoharvan12/kolbo-code) and a GitHub Action will mirror it.

## Updating

```bash
claude plugin update kolbo
```

New plugin versions ship whenever the canonical skill or MCP surface changes.

## Whitelabel / self-hosted

When installing, override the **API Endpoint** prompt with your tenant's URL (for example a Sapir or NakedJim whitelabel). The API key prompt accepts a tenant-specific key the same way.

## Links

- [Kolbo.AI platform](https://kolbo.ai)
- [API documentation](https://docs.kolbo.ai/developer-api)
- [`@kolbo/mcp` on npm](https://www.npmjs.com/package/@kolbo/mcp)
- [Canonical skill source (kolbo-code)](https://github.com/Zoharvan12/kolbo-code/blob/master/packages/opencode/skills/kolbo/SKILL.md)
- [Issues / feedback](https://github.com/Zoharvan12/kolbo-claude-plugin/issues)

## License

MIT
