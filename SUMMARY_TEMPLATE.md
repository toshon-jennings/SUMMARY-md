# SUMMARY.md — Agent Orientation Cheat Sheet

> **PURPOSE:** This file exists to prevent unnecessary full-repo scans. AI
> agents MUST read this file first when they need orientation. It provides
> a map of the codebase so agents can jump directly to the relevant files
> instead of scanning every directory.

> **RULE:** Do NOT grep or glob the entire repo to find things. Use this
> document's pointers to navigate directly. Only search broadly when the
> answer isn't found via these pointers.

---

## Project

**Name:** {{PROJECT_NAME}}
**Description:** {{ONE_LINE_DESCRIPTION}}
**Target Platform:** {{web / desktop / cli / api / mobile}}
**Primary Language:** {{LANG}}
**Framework:** {{FRAMEWORK}}

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | {{UI_FRAMEWORK}} |
| Backend | {{BACKEND}} |
| Database | {{DATABASE}} |
| Build | {{BUILD_TOOL}} |
| Desktop Shell | {{ELECTRON_TAURI_ETC_OR_NONE}} |
| Testing | {{TEST_FRAMEWORK}} |
| Styling | {{CSS_APPROACH}} |

---

## Source Map

> **Convention:** `src/` is the source root. Paths below are relative to repo root.

### Entry Points
| File | Role |
|------|------|
| `{{ENTRY_FILE}}` | App bootstrap / React root |
| `{{MAIN_FILE}}` | Electron main process (if applicable) |
| `{{PRELOAD_FILE}}` | Electron preload (if applicable) |

### Core Directories
| Directory | Contains |
|-----------|----------|
| `{{SRC_DIR}}/components/` | UI components |
| `{{SRC_DIR}}/{{CONTEXT_OR_STATE_DIR}}/` | Global state management |
| `{{SRC_DIR}}/{{LOGIC_DIR}}/` | Business logic, utilities |
| `{{SRC_DIR}}/hooks/` | Custom React hooks |
| `{{SRC_DIR}}/screens/` | Top-level page components |
| `{{SRC_DIR}}/services/` | API client wrappers |
| `{{SRC_DIR}}/contexts/` | React context providers |
| `api/` | Serverless/API routes (if applicable) |

### Cross-cutting Concerns
| Concern | Location |
|---------|----------|
| Routing | `{{ROUTING_FILE}}` |
| Authentication | `{{AUTH_DIR}}` |
| i18n / Strings | `{{I18N_DIR}}` |
| Types / Schemas | `{{TYPES_DIR}}` |
| Constants | `{{CONSTANTS_FILE}}` |
| Styles / Theme | `{{THEME_FILE}}` |

---

## Key Architectural Patterns

{{DESCRIBE_2-3_KEY_PATTERNS}}

Examples:
- **Window system:** Dashboard is the always-mounted desktop; every other mode
  opens as a floating window managed by `ModeContext`. Windows persist across
  reloads via localStorage.
- **IPC bridge:** Electron preload exposes `window.electron.*` to the renderer.
  Main process handles are in `electron/main.cjs` and `electron/preload.cjs`.
- **Context-based state:** Each major feature has its own React context provider
  under `src/contexts/`. Global state lives in `ModeContext` and `ChatContext`.

---

## What NOT to Touch

| Path | Why |
|------|-----|
| `{{DEAD_CODE_PATH}}` | Legacy / unused. Not loaded by the app. |
| `node_modules/` | Dependencies — don't edit directly. |
| `{{BUILD_OUTPUT}}` | Build artifacts — regenerated. |

---

## Common Gotchas

1. **{{GOTCHA_1}}** — {{EXPLANATION}}
2. **{{GOTCHA_2}}** — {{EXPLANATION}}
3. **{{GOTCHA_3}}** — {{EXPLANATION}}

---

## How to Navigate by Task

| If you need to... | Go to... |
|--------------------|------------------|
| Change UI layout | `{{SRC_DIR}}/components/{{COMPONENT}}.jsx` |
| Modify global state | `{{SRC_DIR}}/contexts/{{CONTEXT}}.jsx` |
| Add a new screen | `{{SRC_DIR}}/screens/{{SCREEN}}/` + register in `{{ROUTING_FILE}}` |
| Change API calls | `{{SRC_DIR}}/services/{{SERVICE}}.ts` |
| Fix a bug in IPC | `electron/main.cjs` or `electron/preload.cjs` |
| Add a new mode/window | `src/contexts/ModeContext.jsx` (define MODES key, add component in App.jsx) |
| Change styling | `{{THEME_FILE}}` or component-level Tailwind classes |
