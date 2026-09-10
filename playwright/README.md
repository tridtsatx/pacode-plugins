# playwright

Browser automation through the [Playwright MCP server](https://github.com/microsoft/playwright-mcp).

The server is started on demand with `npx`, so the only requirement is Node.js on
the PATH. On first run Playwright downloads the browser it needs.

## Choosing a browser

The default is Chromium. To use Firefox or WebKit instead, or to reuse a profile,
add the flags to the server's `args` after installing:

```json
"args": ["-y", "@playwright/mcp@latest", "--browser", "firefox"]
```

The manifest lives at `~/.config/pacode/plugins/playwright/.claude-plugin/plugin.json`.

## What it gives the model

Navigation, clicking, typing, form filling, reading page text and the
accessibility tree, screenshots, console messages and network requests — every
one of them as a tool, under the `playwright/playwright` MCP name.
