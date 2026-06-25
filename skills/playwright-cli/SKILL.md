---
name: playwright-cli
description: "Automate browser interactions, test web pages and work with Playwright tests. Microsoft's official browser automation CLI with agent skills for coding agents like Claude Code, GitHub Copilot, etc."
description_zh: "Playwright浏览器自动化CLI：微软官方浏览器自动化工具，为编码Agent（Claude Code/GitHub Copilot等）提供令牌高效的浏览器控制能力，支持导航、点击、填表、截图、视频录制、网络拦截等"
allowed-tools: Bash(playwright-cli:*) Bash(npx:*) Bash(npm:*)
source: https://github.com/microsoft/playwright-cli
---

# Browser Automation with playwright-cli

## Quick start

```bash
# open new browser
playwright-cli open
# navigate to a page
playwright-cli goto https://playwright.dev
# interact with the page using refs from the snapshot
playwright-cli click e15
playwright-cli type "page.click"
playwright-cli press Enter
```

## Core Capabilities

### Basic Browser Operations
- **Open/Close browser** — `open`, `close`
- **Navigation** — `goto`, `go-back`, `go-forward`, `reload`
- **Element interaction** — `click`, `dblclick`, `fill`, `type`, `hover`, `drag`, `drop`, `select`
- **Form operations** — `check`, `uncheck`, `upload`
- **Screenshot/PDF** — `screenshot`, `pdf`

### Advanced Features
- **Multi-tab management** — `tab-list`, `tab-new`, `tab-select`, `tab-close`
- **Keyboard/Mouse control** — `press`, `keydown`, `keyup`, `mousemove`, `mousedown`, `mouseup`, `mousewheel`
- **Dialog handling** — `dialog-accept`, `dialog-dismiss`
- **Storage state** — cookies, localStorage, sessionStorage CRUD
- **Network interception/mock** — `route`, `unroute`, `route-list`

### Developer Tools Integration
- **Console logs** — `console`
- **Network requests** — `requests`, `request`
- **Code execution** — `run-code`, `eval`
- **Tracing** — `tracing-start`, `tracing-stop`
- **Video recording** — `video-start`, `video-stop`, `video-show-actions`
- **UI inspection** — `show --annotate` (annotate feedback on page)
- **Element locator generation** — `generate-locator`
- **Element highlighting** — `highlight`

### Browser Session Management
```bash
# Named session
playwright-cli -s=mysession open example.com --persistent
# Attach to external browser
playwright-cli attach --cdp=http://localhost:9222
playwright-cli attach --extension=chrome
```

## Key Features

| Feature | Description |
|---------|-------------|
| **Snapshot mechanism** | Auto snapshot after each command, locate elements by `ref` (e.g., `e15`) |
| **Multiple locators** | Supports ref, CSS selector, Playwright locator (`getByRole`, `getByTestId`) |
| **Raw output** | `--raw` flag strips extra info for piping; `--json` for structured output |
| **Multi-browser** | Chrome, Firefox, WebKit, Microsoft Edge |
| **Persistent config** | Persistent user data and custom config directory |

## Installation

```bash
# Global install
npm install -g @playwright/cli@latest
# Local use
npx playwright-cli <command>
```

## Typical Workflows

### Form Submission
```bash
playwright-cli open https://example.com/form
playwright-cli fill e1 "user@example.com"
playwright-cli fill e2 "password123"
playwright-cli click e3
```

### Debugging Workflow
```bash
playwright-cli open https://example.com
playwright-cli click e4
playwright-cli console
playwright-cli requests
```

### UI Review (Get user feedback)
```bash
playwright-cli open https://example.com
playwright-cli show --annotate
```

## Reference Documentation

- **playwright-tests.md** — Running and debugging Playwright tests
- **request-mocking.md** — Network request mocking
- **running-code.md** — Executing Playwright code
- **session-management.md** — Browser session management
- **spec-driven-testing.md** — Specification-driven testing
- **storage-state.md** — Storage state management
- **test-generation.md** — Test generation
- **tracing.md** — Tracing and debugging
- **video-recording.md** — Video recording
- **element-attributes.md** — Inspecting element properties

---

**Source**: [microsoft/playwright-cli](https://github.com/microsoft/playwright-cli) — Microsoft Official
