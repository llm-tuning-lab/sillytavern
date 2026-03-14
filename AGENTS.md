# SILLYTAVERN — AGENTS.md

**Generated:** 2026-03-10  
**Project:** SillyTavern  
**Stack:** Node.js 18+, JavaScript (ES6), Express.js  
**License:** AGPL-3.0

---

## OVERVIEW

LLM frontend for power users. Multi-runtime support (Node/Electron/Deno/Bun) with character management, API integration, and extensible plugin system.

---

## STRUCTURE

```
sillytavern/
├── server.js                 # Main entry point
├── src/
│   ├── server-global.js      # Global CLI entry
│   ├── middleware/           # Express middleware
│   ├── electron/             # Electron runtime
│   └── png/                  # PNG metadata handling
├── public/
│   ├── scripts/              # Client-side JS (333 files)
│   ├── css/                  # Stylesheets
│   ├── img/                  # Assets
│   ├── locales/              # i18n translations
│   └── lib/                  # Third-party libraries
├── data/                     # User data (characters, chats)
├── default/                  # Default content & scaffold
└── package.json              # Dependencies & scripts
```

---

## WHERE TO LOOK

| Task | File | Notes |
|------|------|-------|
| **Start server** | `server.js` | `npm start` (Node), `npm run start:electron` (Electron), `npm run start:deno` (Deno), `npm run start:bun` (Bun) |
| **Character management** | `public/scripts/` | Character card loading, chat history |
| **API integration** | `src/middleware/` | LLM provider routing (OpenAI, Claude, local) |
| **Plugin system** | `plugins/` | Custom extensions via `npm run plugins:install` |
| **Linting** | `.eslintrc` | ESLint config (4-space indent, single quotes) |
| **Global CLI** | `src/server-global.js` | `npm run start:global` for system-wide install |

---

## CONVENTIONS

**JavaScript:**
- **Indent:** 4 spaces
- **Quotes:** Single quotes (`'string'`)
- **Linter:** ESLint (see `package.json` rules)
- **Type Hints:** JSDoc comments (optional, no TypeScript)
- **Module System:** ES6 modules (`import`/`export`)

**File Organization:**
- Server logic: `src/`
- Client logic: `public/scripts/`
- Styles: `public/css/`
- Assets: `public/img/`, `public/lib/`

---

## COMMANDS

```bash
# Server startup (multi-runtime)
npm start                    # Node.js (default)
npm run start:electron       # Electron desktop app
npm run start:deno          # Deno runtime
npm run start:bun           # Bun runtime
npm run start:global        # Global CLI install
npm run start:no-csrf       # Disable CSRF protection (dev only)
npm run debug               # Node with --inspect flag

# Code quality
npm run lint                # ESLint check
npm run lint:fix            # Auto-fix linting issues

# Plugin management
npm run plugins:install     # Install plugins
npm run plugins:update      # Update plugins

# Post-install
npm run postinstall         # Runs post-install.js
```

---

## NOTES

- **Multi-Runtime:** Supports Node.js, Electron, Deno, Bun via conditional scripts
- **Character Cards:** Stored in `data/` directory (JSON + PNG metadata)
- **API Providers:** Extensible middleware for OpenAI, Claude, local LLMs, AI Horde
- **Tokenization:** Built-in tokenizers (Tiktoken, SentencePiece) for prompt counting
- **Image Processing:** JIMP library for character avatar manipulation
- **WebSocket:** Real-time chat via `ws` library
- **Security:** CSRF protection via `csrf-sync`, Helmet headers, rate limiting
- **Localization:** Multi-language support via `public/locales/`
- **No CI/CD:** Local Makefile-driven execution (see parent AGENTS.md)
