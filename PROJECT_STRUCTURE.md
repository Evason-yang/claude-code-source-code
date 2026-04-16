# Claude Code v2.1.88 — Complete Project Structure Analysis

**Date**: 2026-04-15  
**Project**: @anthropic-ai/claude-code-source (Decompiled v2.1.88)  
**Location**: `/Users/yangtianzhi/MyProjects/claude-code-source-code/claude-code-source-code`

---

## Executive Summary

This is the **unbundled TypeScript source** extracted from the npm package `@anthropic-ai/claude-code` v2.1.88. The published package ships as a single bundled `cli.js` (~12MB), while this repository contains the complete source code for research and analysis.

**Key Statistics:**
- **Total Source Files**: 1,884 files (1,332 `.ts` + 552 `.tsx`)
- **Total Lines of Code**: 512,664 LOC
- **Main Directories**: 34 subdirectories in `/src`
- **Build System**: TypeScript + esbuild
- **Node Version**: ≥18.0.0
- **Package Type**: ES Modules (ESM)

---

## 1. Top-Level Directory Structure

```
claude-code-source-code/
├── .git/                          # Git repository
├── .gitignore                      # Git ignore rules
├── docs/                           # Deep analysis reports (EN/JA/KO/ZH)
├── scripts/                        # Build and transformation scripts
├── src/                            # Main TypeScript source code (512K LOC)
├── stubs/                          # Stub modules for bundling
├── tools/                          # Unreleased/experimental tools
├── types/                          # TypeScript type definitions
├── utils/                          # Shared utility modules
├── vendor/                         # Vendored dependencies (native modules)
├── package.json                    # Project metadata & dependencies
├── package-lock.json               # Locked dependencies
├── tsconfig.json                   # TypeScript configuration
├── README.md                       # Main documentation
├── README_CN.md                    # Chinese documentation
├── README_JA.md                    # Japanese documentation
├── README_KR.md                    # Korean documentation
├── QUICKSTART.md                   # Quick start guide
└── PROJECT_ANALYSIS.html           # Previous analysis report
```

---

## 2. Source Code Directory (`/src`) — Detailed Breakdown

### 2.1 Core Entry Points & Main Files

| File | Lines | Purpose |
|------|-------|---------|
| **main.tsx** | 4,683 | Main CLI entry point; initializes app, handles CLI args, launches REPL |
| **QueryEngine.ts** | 1,295 | Orchestrates agent loop; manages tool execution, state, permissions |
| **query.ts** | 1,729 | Query execution engine; processes user input, handles retries |
| **Tool.ts** | 792 | Tool abstraction & registry; base class for all tools |
| **commands.ts** | 754 | Slash command definitions & routing |
| **setup.ts** | 477 | Initial setup & configuration |
| **history.ts** | 464 | Session history management |
| **cost-tracker.ts** | 323 | API usage & cost tracking |
| **context.ts** | 189 | System & user context management |
| **tools.ts** | 389 | Tool loading & initialization |

### 2.2 Major Subsystems (by file count)

| Directory | Files | Purpose |
|-----------|-------|---------|
| **utils/** | 564 | Utility functions (config, env, helpers, settings, etc.) |
| **components/** | 389 | React/Ink UI components (prompts, dialogs, renders) |
| **commands/** | 189 | Slash command implementations (100+ commands) |
| **tools/** | 184 | Tool implementations (40+ tools) |
| **hooks/** | 104 | React hooks (state, permissions, notifications) |
| **ink/** | 96 | Terminal UI rendering (layout, components, events) |
| **services/** | 130 | Business logic services (API, MCP, auth, analytics) |
| **bridge/** | 31 | Bridge protocol & remote session management |
| **cli/** | 19 | CLI utilities & argument parsing |
| **tasks/** | 12 | Task execution system (local, remote, agents) |

### 2.3 Complete Directory Tree with Descriptions

```
src/
├── assistant/                      # Assistant/Kairos mode (1 file)
│   └── sessionHistory.ts           # Session history for assistant mode
│
├── bootstrap/                      # Bootstrap & initialization (1 file)
│   └── state.ts                    # Initial state management
│
├── bridge/                         # Bridge protocol (31 files)
│   ├── bridgeApi.ts                # Bridge API client
│   ├── bridgeConfig.ts             # Bridge configuration
│   ├── bridgeDebug.ts              # Debug utilities
│   ├── bridgeEnabled.ts            # Feature detection
│   ├── bridgeMain.ts               # Main bridge handler
│   ├── bridgeMessaging.ts          # Message routing
│   ├── bridgePermissionCallbacks.ts # Permission handling
│   ├── bridgePointer.ts            # Pointer/cursor management
│   ├── bridgeStatusUtil.ts         # Status utilities
│   ├── bridgeUI.ts                 # UI integration
│   ├── capacityWake.ts             # Capacity management
│   ├── codeSessionApi.ts           # Session API
│   ├── createSession.ts            # Session creation
│   ├── debugUtils.ts               # Debug helpers
│   ├── envLessBridgeConfig.ts      # Environment-agnostic config
│   ├── flushGate.ts                # Message flushing
│   ├── inboundAttachments.ts       # Attachment handling
│   ├── inboundMessages.ts          # Message reception
│   ├── initReplBridge.ts           # REPL bridge init
│   ├── jwtUtils.ts                 # JWT utilities
│   ├── pollConfig.ts               # Config polling
│   ├── pollConfigDefaults.ts       # Default poll config
│   ├── remoteBridgeCore.ts         # Remote bridge core
│   ├── replBridge.ts               # REPL bridge
│   ├── replBridgeHandle.ts         # Bridge handle management
│   ├── replBridgeTransport.ts      # Transport layer
│   ├── sessionIdCompat.ts          # Session ID compatibility
│   ├── sessionRunner.ts            # Session execution
│   ├── trustedDevice.ts            # Trusted device management
│   ├── types.ts                    # Type definitions
│   └── workSecret.ts               # Work secret management
│
├── buddy/                          # Buddy/companion UI (6 files)
│   ├── CompanionSprite.tsx         # Animated companion sprite
│   ├── companion.ts                # Companion logic
│   ├── prompt.ts                   # Buddy prompts
│   ├── sprites.ts                  # Sprite definitions
│   ├── types.ts                    # Type definitions
│   └── useBuddyNotification.tsx    # Notification hook
│
├── cli/                            # CLI utilities (19 files)
│   ├── args.ts                     # Argument parsing
│   ├── banner.ts                   # CLI banner
│   ├── cli.ts                      # CLI main
│   ├── errorHandler.ts             # Error handling
│   ├── helpFormatter.ts            # Help text formatting
│   └── [14 more CLI modules]
│
├── commands/                       # Slash commands (189 files)
│   ├── add-dir/                    # /add-dir command
│   ├── advisor.ts                  # /advisor command
│   ├── agents/                     # /agents command
│   ├── ant-trace/                  # /ant-trace command
│   ├── autofix-pr/                 # /autofix-pr command
│   ├── [180+ more command implementations]
│   └── zoom/                       # /zoom command
│
├── components/                     # React/Ink components (389 files)
│   ├── Dialogs/                    # Dialog components
│   ├── Prompts/                    # Prompt components
│   ├── Renderers/                  # Output renderers
│   ├── Status/                     # Status displays
│   ├── Terminal/                   # Terminal utilities
│   └── [many more UI components]
│
├── constants/                      # Constants (21 files)
│   ├── colors.ts                   # Color definitions
│   ├── keybindings.ts              # Keyboard shortcuts
│   ├── oauth.ts                    # OAuth configuration
│   ├── product.ts                  # Product constants
│   ├── xml.ts                      # XML tag constants
│   └── [16 more constant files]
│
├── context/                        # Context management (9 files)
│   ├── notifications.ts            # Notification context
│   ├── permissions.ts              # Permission context
│   └── [7 more context files]
│
├── coordinator/                    # Agent coordination (1 file)
│   └── index.ts                    # Coordinator implementation
│
├── entrypoints/                    # Entry point modules (8 files)
│   ├── agentSdkTypes.ts            # Agent SDK types
│   ├── cli.ts                      # CLI entrypoint
│   ├── init.ts                     # Initialization
│   └── [5 more entrypoint files]
│
├── hooks/                          # React hooks (104 files)
│   ├── useCanUseTool.ts            # Permission checking hook
│   ├── useMemory.ts                # Memory management hook
│   ├── useNotification.ts          # Notification hook
│   ├── usePermission.ts            # Permission hook
│   ├── useQueryEngine.ts           # Query engine hook
│   └── [99 more custom hooks]
│
├── ink/                            # Terminal UI framework (96 files)
│   ├── components/                 # Ink components
│   │   ├── Box.tsx                 # Box layout
│   │   ├── Text.tsx                # Text rendering
│   │   └── [more components]
│   ├── events/                     # Event handling
│   ├── hooks/                      # Ink hooks
│   ├── layout/                     # Layout system
│   ├── termio/                     # Terminal I/O
│   └── [more ink modules]
│
├── keybindings/                    # Keyboard shortcuts (14 files)
│   ├── vim.ts                      # Vim keybindings
│   ├── emacs.ts                    # Emacs keybindings
│   └── [12 more keybinding files]
│
├── memdir/                         # Memory directory (8 files)
│   ├── memdir.ts                   # Memory management
│   ├── paths.ts                    # Memory paths
│   └── [6 more memory files]
│
├── migrations/                     # Data migrations (11 files)
│   ├── migration001.ts             # Migration 001
│   └── [10 more migration files]
│
├── moreright/                      # More-right feature (1 file)
│   └── index.ts                    # More-right implementation
│
├── native-ts/                      # Native TypeScript (4 files)
│   ├── audio.ts                    # Audio handling
│   └── [3 more native files]
│
├── outputStyles/                   # Output styling (1 file)
│   └── styles.ts                   # Output style definitions
│
├── plugins/                        # Plugin system (2 files)
│   ├── plugins.ts                  # Plugin loader
│   └── types.ts                    # Plugin types
│
├── query/                          # Query system (4 files)
│   ├── query.ts                    # Query execution
│   └── [3 more query files]
│
├── remote/                         # Remote functionality (4 files)
│   ├── remote.ts                   # Remote client
│   └── [3 more remote files]
│
├── schemas/                        # Data schemas (1 file)
│   └── schemas.ts                  # Schema definitions
│
├── screens/                        # Screen components (3 files)
│   ├── MainScreen.tsx              # Main screen
│   └── [2 more screens]
│
├── server/                         # Server functionality (3 files)
│   ├── server.ts                   # Server implementation
│   └── [2 more server files]
│
├── services/                       # Business logic services (130 files)
│   ├── analytics/                  # Analytics & telemetry
│   │   ├── growthbook.ts           # GrowthBook feature flags
│   │   ├── telemetry.ts            # Telemetry client
│   │   └── [more analytics]
│   ├── api/                        # API clients
│   │   ├── claude.ts               # Claude API client
│   │   ├── bootstrap.ts            # Bootstrap API
│   │   ├── filesApi.ts             # Files API
│   │   ├── logging.ts              # Logging service
│   │   └── [more API modules]
│   ├── mcp/                        # Model Context Protocol
│   │   ├── mcp.ts                  # MCP client
│   │   ├── types.ts                # MCP types
│   │   ├── officialRegistry.ts     # Official MCP registry
│   │   └── [more MCP modules]
│   ├── oauth/                      # OAuth handling
│   ├── policyLimits/               # Policy enforcement
│   ├── remoteManagedSettings/      # Remote settings management
│   └── [more service modules]
│
├── skills/                         # Skills system (20 files)
│   ├── skills.ts                   # Skill loader
│   ├── types.ts                    # Skill types
│   └── [18 more skill files]
│
├── state/                          # State management (6 files)
│   ├── AppState.ts                 # Application state
│   └── [5 more state files]
│
├── tasks/                          # Task execution (12 files)
│   ├── LocalAgentTask.ts           # Local agent execution
│   ├── RemoteAgentTask.ts          # Remote agent execution
│   ├── LocalShellTask.ts           # Local shell execution
│   ├── DreamTask.ts                # Dream task execution
│   ├── InProcessTeammateTask.ts    # In-process teammate execution
│   └── [7 more task files]
│
├── tools/                          # Tool implementations (184 files)
│   ├── AgentTool/                  # Agent spawning tool
│   ├── FileEditTool/               # File editing tool
│   ├── FileWriteTool/              # File writing tool
│   ├── ReadTool/                   # File reading tool
│   ├── BashTool/                   # Bash execution tool
│   ├── PowerShellTool/             # PowerShell execution tool
│   ├── WebSearchTool/              # Web search tool
│   ├── WebFetchTool/               # Web fetch tool
│   ├── MCPTool/                    # MCP tool
│   ├── TaskCreateTool/             # Task creation tool
│   ├── TaskUpdateTool/             # Task update tool
│   ├── TaskGetTool/                # Task retrieval tool
│   ├── TaskOutputTool/             # Task output tool
│   ├── TaskStopTool/               # Task stop tool
│   ├── SendMessageTool/            # Message sending tool
│   ├── AskUserQuestionTool/        # User question tool
│   ├── EnterPlanModeTool/          # Plan mode entry tool
│   ├── ExitPlanModeTool/           # Plan mode exit tool
│   ├── TeamCreateTool/             # Team creation tool
│   ├── TeamDeleteTool/             # Team deletion tool
│   ├── SkillTool/                  # Skill execution tool
│   ├── [164 more tool implementations]
│   └── testing/                    # Tool testing utilities
│
├── types/                          # TypeScript types (11 files)
│   ├── message.ts                  # Message types
│   ├── permissions.ts              # Permission types
│   └── [9 more type files]
│
├── upstreamproxy/                  # Upstream proxy (2 files)
│   ├── proxy.ts                    # Proxy implementation
│   └── types.ts                    # Proxy types
│
├── utils/                          # Utility functions (564 files)
│   ├── config.ts                   # Configuration utilities
│   ├── env/                        # Environment utilities
│   ├── settings/                   # Settings management
│   │   ├── mdm/                    # MDM (Mobile Device Management)
│   │   ├── oauth/                  # OAuth settings
│   │   └── [more settings]
│   ├── secureStorage/              # Secure storage (keychain)
│   ├── startupProfiler.ts          # Startup profiling
│   ├── commitAttribution.ts        # Git commit attribution
│   ├── advisor.ts                  # Advisor utilities
│   ├── agentSwarmsEnabled.ts       # Agent swarms feature
│   ├── array.ts                    # Array utilities
│   ├── [554 more utility files]
│   └── [extensive utility library]
│
├── vim/                            # Vim mode support (5 files)
│   ├── vim.ts                      # Vim mode implementation
│   ├── keybindings.ts              # Vim keybindings
│   └── [3 more vim files]
│
├── voice/                          # Voice mode (1 file)
│   └── voice.ts                    # Voice mode implementation
│
├── commands.ts                     # Command registry
├── context.ts                      # Context utilities
├── cost-tracker.ts                 # Cost tracking
├── costHook.ts                     # Cost hook
├── dialogLaunchers.tsx             # Dialog launching
├── history.ts                      # Session history
├── ink.ts                          # Ink initialization
├── interactiveHelpers.tsx          # Interactive helpers
├── main.tsx                        # Main entry point
├── projectOnboardingState.ts       # Onboarding state
├── query.ts                        # Query execution
├── QueryEngine.ts                  # Query engine
├── replLauncher.tsx                # REPL launcher
├── setup.ts                        # Setup utilities
├── Task.ts                         # Task base class
├── tasks.ts                        # Task utilities
├── Tool.ts                         # Tool base class
└── tools.ts                        # Tool registry
```

---

## 3. Configuration Files

### 3.1 TypeScript Configuration (`tsconfig.json`)

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "ESNext",
    "moduleResolution": "bundler",
    "jsx": "react-jsx",
    "outDir": "dist",
    "rootDir": "src",
    "strict": false,
    "skipLibCheck": true,
    "declaration": true,
    "declarationMap": true,
    "sourceMap": true,
    "resolveJsonModule": true
  },
  "include": ["src/**/*", "stubs/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

**Key Characteristics:**
- Targets ES2022 with ESM module system
- React JSX support
- Loose type checking (`strict: false`)
- Source maps enabled for debugging
- Bundler-based module resolution

### 3.2 Package Configuration (`package.json`)

```json
{
  "name": "@anthropic-ai/claude-code-source",
  "version": "2.1.88",
  "description": "Claude Code v2.1.88 — decompiled source for research",
  "type": "module",
  "private": true,
  "scripts": {
    "prepare-src": "node scripts/prepare-src.mjs",
    "build": "npm run prepare-src && node scripts/build.mjs",
    "check": "npm run prepare-src && tsc --noEmit",
    "start": "node dist/cli.js"
  },
  "engines": { "node": ">=18.0.0" },
  "devDependencies": {
    "esbuild": "^0.27.4",
    "typescript": "^6.0.2"
  }
}
```

**Build System:**
- `prepare-src`: Pre-processes source code
- `build`: Compiles with esbuild
- `check`: Type checking via TypeScript
- `start`: Runs compiled CLI

---

## 4. Build & Scripts (`/scripts`)

| Script | Purpose |
|--------|---------|
| **build.mjs** | Main build orchestration; bundles with esbuild |
| **prepare-src.mjs** | Pre-processing; prepares source for compilation |
| **stub-modules.mjs** | Creates stub modules for feature-gated code |
| **transform.mjs** | AST transformations; processes code during build |

---

## 5. Documentation (`/docs`)

Quadrilingual deep analysis reports:

```
docs/
├── en/                              # English
│   ├── 01-telemetry-and-privacy.md
│   ├── 02-hidden-features-and-codenames.md
│   ├── 03-undercover-mode.md
│   ├── 04-remote-control-and-killswitches.md
│   └── 05-future-roadmap.md
├── ja/                              # 日本語 (Japanese)
├── ko/                              # 한국어 (Korean)
└── zh/                              # 中文 (Chinese)
```

**Report Topics:**
1. **Telemetry & Privacy** — Data collection, analytics sinks, opt-out limitations
2. **Hidden Features & Codenames** — Internal features, feature flags, model codenames
3. **Undercover Mode** — AI attribution hiding in open-source projects
4. **Remote Control & Killswitches** — Managed settings, killswitches, model overrides
5. **Future Roadmap** — Unreleased features (Numbat, KAIROS, voice mode, 17+ tools)

---

## 6. Vendor Dependencies (`/vendor`)

Native modules and compiled dependencies:

```
vendor/
├── audio-capture-src/               # Audio capture native module
├── image-processor-src/             # Image processing native module
├── modifiers-napi-src/              # Modifiers NAPI module
└── url-handler-src/                 # URL handler native module
```

---

## 7. Experimental/Unreleased Tools (`/tools`)

```
tools/
├── OverflowTestTool/                # Overflow testing tool
├── TerminalCaptureTool/             # Terminal capture tool
├── TungstenTool/                    # Tungsten tool (unreleased)
├── VerifyPlanExecutionTool/         # Plan verification tool
└── WorkflowTool/                    # Workflow automation tool
```

---

## 8. Type Definitions (`/types` & `/utils/types`)

- **message.ts** — Message, UserMessage, AssistantMessage, SystemMessage types
- **permissions.ts** — PermissionMode, PermissionResult, AdditionalWorkingDirectory
- **tool.ts** — ToolInputJSONSchema, ToolUseContext, ToolResult
- **[8+ more type files]** — Comprehensive TypeScript type system

---

## 9. Stubs (`/stubs`)

```
stubs/
├── bun-bundle.ts                    # Bun bundler integration
└── [stub modules for feature gates]
```

Used for:
- Feature-gated code branches
- Platform-specific implementations
- Dead-code elimination during build

---

## 10. Core Architecture Layers

### 10.1 Data Flow

```
User Input
    ↓
CLI Parser (cli/)
    ↓
Command Router (commands/)
    ↓
QueryEngine (QueryEngine.ts)
    ↓
Tool Execution (tools/)
    ↓
Services Layer (services/)
    ↓
API Clients (services/api/)
    ↓
Output Rendering (components/, ink/)
    ↓
Terminal Display
```

### 10.2 Key Systems

**1. Query Engine (`QueryEngine.ts`)**
- Orchestrates the agent loop
- Manages tool execution
- Handles permissions & state
- Tracks costs & usage

**2. Tool System (`Tool.ts`, `tools/`)**
- 40+ tool implementations
- Permission framework
- Tool registry & loading
- Progress tracking

**3. Services (`services/`)**
- API clients (Claude, Files, Bootstrap)
- MCP (Model Context Protocol) integration
- Authentication & OAuth
- Analytics & telemetry
- Settings management

**4. UI/Terminal (`ink/`, `components/`)**
- Terminal rendering framework
- Interactive dialogs & prompts
- Status displays
- Keyboard handling

**5. State Management (`state/`, `hooks/`)**
- Application state (AppState)
- React hooks for state access
- Permission tracking
- Notification system

**6. Bridge Protocol (`bridge/`)**
- Remote session management
- Message routing
- Session persistence
- Trusted device handling

---

## 11. Feature Gates & Conditional Compilation

The codebase uses `feature()` gates for conditional code:

```typescript
import { feature } from 'bun:bundle'

if (feature('DAEMON')) {
  // Daemon-specific code
}
if (feature('KAIROS')) {
  // Assistant mode code
}
```

**Known Feature Gates:**
- `DAEMON` — Background daemon mode
- `KAIROS` — Fully autonomous agent mode
- `CONTEXT_COLLAPSE` — Context compression
- `COORDINATOR_MODE` — Multi-agent coordination
- `EXPERIMENTAL_SKILL_SEARCH` — Remote skill loading
- `BRIDGE_MODE` — Remote session bridge
- `UNDERCOVER_MODE` — AI attribution hiding

---

## 12. Missing Modules (108 modules)

**Not included in npm package** (feature-gated, dead-code-eliminated):

### Anthropic Internal (~70 modules)
- `daemon/main.js` — Background daemon
- `proactive/index.js` — Proactive notifications
- `contextCollapse/*` — Context compression
- `skillSearch/*` — Remote skill search
- `coordinator/workerAgent.js` — Multi-agent coordination
- `bridge/peerSessions.js` — Peer sessions
- `assistant/index.js` — Kairos assistant mode
- [60+ more internal modules]

### Published but Stubbed (~38 modules)
- Modules referenced but not shipped in npm package
- Replaced with stubs during build

---

## 13. Build Process

### 13.1 Build Steps

1. **prepare-src.mjs** — Pre-processes source
   - Extracts type definitions
   - Prepares feature gates
   - Sets up stub modules

2. **transform.mjs** — AST transformations
   - Processes code during build
   - Optimizes for bundling
   - Removes dead code

3. **build.mjs** — esbuild bundling
   - Bundles all modules
   - Minification & optimization
   - Output: `dist/cli.js` (~12MB)

### 13.2 Output

```
dist/
└── cli.js                           # Single bundled CLI (~12MB)
```

---

## 14. Key Metrics & Statistics

| Metric | Value |
|--------|-------|
| Total Files | 1,884 |
| TypeScript Files (.ts) | 1,332 |
| React/JSX Files (.tsx) | 552 |
| Total Lines of Code | 512,664 |
| Main Subdirectories | 34 |
| Tools Implemented | 40+ |
| Slash Commands | 100+ |
| React Hooks | 104+ |
| Services | 130+ |
| Utility Functions | 564 |
| Node Version Required | ≥18.0.0 |
| Package Type | ESM (ES Modules) |

---

## 15. Important Notes

### 15.1 Limitations

- **Not Directly Compilable** — Missing 108 internal modules
- **Feature-Gated Code** — Many features only in internal builds
- **Incomplete Documentation** — Some internal APIs not documented
- **Build Dependencies** — Requires specific esbuild version

### 15.2 Intellectual Property

> All source code in this repository is the intellectual property of **Anthropic and Claude**. This repository is provided strictly for technical research, study, and educational exchange. **Commercial use is strictly prohibited.**

### 15.3 Decompilation Notice

- Source extracted from npm tarball v2.1.88
- Published package ships as single bundled `cli.js`
- This repository contains unbundled TypeScript source
- Some code may be obfuscated or regenerated from minified output

---

## 16. Quick Navigation Guide

| Want to explore? | Start here |
|------------------|-----------|
| Main CLI logic | `src/main.tsx` |
| Agent loop | `src/QueryEngine.ts` |
| Tool system | `src/Tool.ts`, `src/tools/` |
| Commands | `src/commands/` |
| API integration | `src/services/api/` |
| UI/Terminal | `src/ink/`, `src/components/` |
| State management | `src/state/`, `src/hooks/` |
| Remote sessions | `src/bridge/` |
| Utilities | `src/utils/` |
| Type definitions | `src/types/` |
| Build system | `scripts/`, `tsconfig.json` |
| Documentation | `docs/` |

---

**End of Project Structure Analysis**  
*Generated: 2026-04-15*
