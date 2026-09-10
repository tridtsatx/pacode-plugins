# pacode-plugins

The plugin marketplace pacode browses from `/plugins`.

It uses the Claude Code marketplace layout, so a plugin written for Claude Code
works here unchanged: this repository holds `.claude-plugin/marketplace.json`
listing the plugins, and one directory per plugin containing its own
`.claude-plugin/plugin.json`.

## Adding a plugin

Put the plugin in a directory named after it, then add an entry to
`.claude-plugin/marketplace.json`:

```json
{
  "name": "my-plugin",
  "source": "./my-plugin",
  "description": "One line about what it does",
  "version": "1.0.0",
  "author": "you",
  "category": "tools",
  "keywords": ["example"]
}
```

A plugin directory looks like this:

```
my-plugin/
  .claude-plugin/plugin.json
  skills/<skill>/SKILL.md
```

## What pacode runs

| Component | Status |
|---|---|
| `skills` | run — read from `<plugin>/skills/*/SKILL.md` |
| `mcpServers` | run — joined to the MCP pool as `<plugin>/<server>` |
| `commands` | accepted, not run — pacode's slash commands come from its own plugin runtime |
| `hooks` | accepted, not run |
| `agents` | accepted, not run — pacode has its own subagent model |

What a plugin declares and pacode will not run is listed on the `/plugins`
screen rather than dropped in silence.

## Browsing it

```
/plugins                       # opens on this marketplace
/plugins owner/repo            # points at another one and remembers it
```
