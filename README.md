# studio zazeno agent plugins

Plugins and skills by [studio zazeno](https://zazeno.com) for Claude and other AI agents.

## Install

**Claude Code**

```
/plugin marketplace add studio-zazeno/agent-plugins
/plugin install <plugin>@zazeno
```

**claude.ai and the Claude desktop app:** Customize → Plugins → Add marketplace → `studio-zazeno/agent-plugins`, then add the plugin.

**Other agents (Cursor, Codex, GitHub Copilot and more):** the skills follow the open Agent Skills format. Install them with

```
npx skills add studio-zazeno/agent-plugins
```

## Plugins

| Plugin | What it does | Install |
|---|---|---|
| `weniger` | Gives a site the Dieter Rams treatment: 20 principles for purpose, depth, measure, colour and motion. Skill `weniger-ui`. Page: [zazeno.com/weniger](https://zazeno.com/weniger/) | `/plugin install weniger@zazeno` |
| `lgtu` | LGTU (Looks Good To Users): a senior product designer's review of what you or your agent built, before you ship it. Skill `lgtu`. Page: [zazeno.com/lgtu](https://zazeno.com/lgtu/) | `/plugin install lgtu@zazeno` |

## License

Skills (everything under `plugins/*/skills/`): © 2026 studio zazeno, [CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0/). Use them, also at work, and share them unchanged with credit and a link to zazeno.com. The `DESIGN.md` template that comes with Weniger is the exception: CC0, yours to change. Everything else: MIT. See `LICENSE`.
