# Context Window & Features Research Session

**Started:** 2026-02-09 12:44:16 UTC
**Status:** In Progress

---

## Claude Code Research
**Agent:** Dr. Sarah Chen
**Status:** Complete

### Context Windows

**Latest Models (2026)**

| Model | Context Window | Max Output | Status |
|-------|---------------|------------|--------|
| Claude Opus 4.6 | 200K / 1M (beta) | 128K tokens | Latest (Released Feb 5, 2026) |
| Claude Sonnet 4.5 | 200K / 1M (beta) | 64K tokens | Current |
| Claude Haiku 4.5 | 200K | 64K tokens | Current |

**Extended Context (1M Token Window)**
- Available for Opus 4.6, Sonnet 4.5, and Sonnet 4 via `context-1m-2025-08-07` beta header
- Currently in beta for organizations in usage tier 4 and organizations with custom rate limits
- Available on Claude API, Microsoft Foundry, Amazon Bedrock, and Google Cloud Vertex AI
- Premium pricing applies: 2x input, 1.5x output for requests exceeding 200K tokens
- For Opus 4.6: 1M context is available for API and Claude Code pay-as-you-go users
- Pro, Max, Teams, and Enterprise subscription users do NOT have access to Opus 4.6 1M context at launch

**Claude Code Model Aliases**
- `default` - Recommended model (Opus 4.6 for Max/Teams/Pro users)
- `opus` - Latest Opus model (currently Opus 4.6)
- `sonnet` - Latest Sonnet model (currently Sonnet 4.5)
- `haiku` - Fast and efficient Haiku model
- `sonnet[1m]` - Sonnet with 1 million token context window
- `opusplan` - Special hybrid mode: uses Opus during planning, switches to Sonnet for execution

**Context Awareness**
- Claude Sonnet 4.5 and Haiku 4.5 feature context awareness
- Models track remaining token budget throughout conversation
- System provides token usage warnings: `Token usage: 35000/200000; 165000 remaining`
- Enables more effective execution on long-running tasks

**Context Management**
- Server-side compaction available (beta for Opus 4.6) - automatically condenses earlier conversation parts
- Context editing strategies: tool result clearing, thinking block clearing
- Extended thinking blocks automatically stripped from context window in subsequent turns
- Models return validation errors when exceeding context window (no silent truncation)

**Legacy Models**
- Opus 4.5 (200K context, 64K output) - May 2025 cutoff
- Opus 4.1 (200K context, 32K output) - Jan 2025 cutoff
- Sonnet 4 (200K / 1M beta, 64K output) - Jan 2025 cutoff
- Sonnet 3.7 (200K, 64K / 128K beta output) - Oct 2024 cutoff
- Opus 4 (200K, 32K output) - Jan 2025 cutoff
- Haiku 3 (200K, 4K output) - Aug 2023 cutoff

**Knowledge Cutoffs**
- Opus 4.6: May 2025 (reliable) / Aug 2025 (training data)
- Sonnet 4.5: Jan 2025 (reliable) / Jul 2025 (training data)
- Haiku 4.5: Feb 2025 (reliable) / Jul 2025 (training data)

### Features

**Hooks System**
- **Hook Types Available:**
  - `PreToolUse` - Fires before tool execution with tool_name, tool_input, tool_use_id
  - `PostToolUse` - Fires after successful tool completion with tool_input and tool_response
  - `PostToolUseFailure` - Fires after failed tool execution
  - `Notification` - Fires when Claude sends notifications (permission requests or 60s idle)
  - `PermissionRequest` - Fires when permission dialog shown
  - `UserPromptSubmit` - Fires when user submits prompt
  - `Stop` - Fires when Claude Code finishes responding
  - `SubagentStop` / `TaskStopHook` - Fires when subagents (Task tools) finish
  - `TaskCompleted` - Fires when task completes

- **Hook Implementations:**
  - Bash command hooks (type: "command")
  - Prompt-based hooks (type: "prompt") - use LLM to evaluate actions
  - Decision control: allow, deny, or ask for permission
  - Dynamic control over tool usage validation

**MCP (Model Context Protocol) Support**
- Full MCP server support with --agents flag accepting JSON configuration
- Sub-agents can access SDK-provided MCP tools (synced to shared application state)
- Pre-configured OAuth client credentials for MCP servers without Dynamic Client Registration
- Use --client-id and --client-secret flags with `claude mcp add`
- Slack and other OAuth providers supported

**Sub-agents & Agent Teams**
- Autonomous AI workers that Claude spawns for specific tasks
- Run up to 7 simultaneous parallel operations
- Dramatically speeds up complex workflows (codebase exploration, multi-file analysis)
- Research preview: Agent Teams for multi-agent collaboration
  - Token-intensive feature
  - Requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`
  - Team lead agent plans and delegates to specialist background agents

**Slash Commands**
- User-invoked workflow templates stored as Markdown files
- Every skill requires SKILL.md file with YAML frontmatter
- Name field becomes the /slash-command
- Built-in commands: /model, /status, /teleport, /fast, /workflow
- Custom commands can be created in .claude/commands/

**Skills System**
- Custom commands/skills support with hot-reloading (as of v2.1.0)
- Skills can fetch live data (e.g., GitHub CLI: `gh pr diff`, `gh pr view --comments`)
- Output automatically inserted into prompts
- Organized plugins covering cloud platforms (GitHub, Azure, MongoDB)

**IDE Integrations**
- **VS Code Extension** (Native):
  - Native graphical interface integrated directly into IDE
  - Review and edit Claude's plans before accepting
  - Auto-accept edits as they're made
  - @-mention files with specific line ranges
  - Access conversation history
  - Multiple conversations in separate tabs/windows
  - See current file, selected code, error messages automatically

- **JetBrains Plugin** (Beta):
  - Available for IntelliJ IDEA, PyCharm, WebStorm, GoLand, etc.
  - Runs Claude Code CLI inside IDE's integrated terminal
  - Opens proposed changes in IDE's diff viewer
  - Available from JetBrains Marketplace

**Git Integration**
- Handles git workflows through natural language commands
- Execute routine tasks, explain complex code
- Claude Hub: connects to GitHub repositories
  - AI-powered code assistance in PRs and issues
  - Analyze repositories via @mentions
  - Answer technical questions
  - Help developers understand and improve codebase
- Session Restore: efficiently restores context from session files and git history
- Automatic git history analysis

**Web Search Capability**
- Web search functionality available (US only as of documentation)
- Domain filtering supported (include/block specific websites)
- Results formatted as search result blocks with markdown links

**Sandboxing & Security**
- Native sandboxing with OS-level primitives
- Filesystem and network isolation enforced
- Reduces permission prompts by 84% in internal usage
- Web-based Claude Code: isolated sandbox per session
- Sensitive credentials kept outside sandbox
- Vercel Sandbox integration available

**Cost Tracking**
- Real-time cost tracking via Claudia dashboard
- See expenses by project/model
- Enhanced statusline tools include cost tracking
- MCP server monitoring in status line

**Background Agents**
- Background agent support added in v2.1.0 (January 7, 2026)
- Swarms feature (experimental): team lead agent delegates to specialist background agents
  - Discovered via feature flags (January 24, 2026)
  - Provides multi-agent orchestration

**Additional Features (2026)**
- Session teleportation via /teleport (v2.1.0)
- Claude in Chrome beta (v2.1.0)
- Language settings customization (v2.1.0)
- 3x memory improvement (v2.1.0)
- Effort levels for Opus 4.6: low/medium/high (controls adaptive reasoning)
- Prompt caching with granular control (per-model disable options)
- Token counting API for usage estimation
- Fast mode: same model with faster output (toggle with /fast)
- Extended thinking with adaptive thinking (Opus 4.6)
- Interleaved thinking: think between tool calls (Claude 4 models)
- Plan Mode: special reasoning mode for architecture decisions

**Configuration**
- Environment variables for model control:
  - `ANTHROPIC_DEFAULT_OPUS_MODEL`
  - `ANTHROPIC_DEFAULT_SONNET_MODEL`
  - `ANTHROPIC_DEFAULT_HAIKU_MODEL`
  - `CLAUDE_CODE_SUBAGENT_MODEL`
  - `CLAUDE_CODE_EFFORT_LEVEL`
  - `DISABLE_PROMPT_CACHING` (and per-model variants)
  - `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS`
- Settings file configuration for permissions, model, effortLevel
- Command-line flags: --model, --agents, --client-id, --client-secret

---

## Codex CLI Research
**Agent:** Marcus Thompson
**Status:** Complete

### Context Windows

**Research Date:** 2026-02-09
**Sources:** [OpenAI Codex Models](https://developers.openai.com/codex/models/), [OpenAI Platform Docs](https://platform.openai.com/docs/models), [OpenAI Blog](https://openai.com/index/introducing-gpt-5-3-codex/)

#### Primary Models (Recommended)

| Model | Context Window | Max Output | Status | Notes |
|-------|---------------|------------|--------|-------|
| gpt-5.3-codex | 400,000 tokens | - | Latest | Default for Codex CLI, 25% faster |
| gpt-5.2-codex | 400,000 tokens | - | Stable | Succeeded by GPT-5.3-Codex |
| gpt-5.1-codex-mini | 400,000 tokens | 128,000 tokens | Stable | Cost-effective version |

#### Reasoning Models (o-series)

| Model | Context Window | Max Output | Status | Notes |
|-------|---------------|------------|--------|-------|
| o3 | 200,000 tokens | - | Latest | New reasoning model for complex tasks |
| o4-mini | 200,000 tokens | - | Latest | Fast, cost-efficient reasoning |
| codex-mini-latest | 200,000 tokens | 100,000 tokens | Stable | Fine-tuned o4-mini for Codex CLI |
| o1 | 200,000 tokens | 100,000 tokens | Stable | Previous generation reasoning |
| o1-preview | 128,000 tokens | 32,768 tokens | Deprecated | Removed April 28, 2025 |
| o1-mini | 128,000 tokens | 65,536 tokens | Deprecated | Removed April 28, 2025 |

#### Legacy Models

| Model | Context Window | Max Output | Status | Notes |
|-------|---------------|------------|--------|-------|
| GPT-4.1 | 1,000,000 tokens | - | Stable | Up to 1M token context |
| GPT-4.1 mini | 1,000,000 tokens | - | Stable | Improved instruction following |
| GPT-4o | 128,000 tokens | 16,384 tokens | API Only | Retired from ChatGPT Feb 13, 2026 |
| GPT-4o mini | 128,000 tokens | 16,384 tokens | Stable | - |

#### Model Deprecations (2025-2026)

- **o1-preview, o1-mini**: Deprecated April 28, 2025
- **chatgpt-4o-latest**: Deprecated Nov 18, 2025; API removal Feb 17, 2026
- **GPT-4o, GPT-4.1, GPT-4.1 mini, o4-mini**: Retired from ChatGPT Feb 13, 2026 (API access continues)

#### Context Window Features

- **Context Compaction**: `/compact` slash command - summarizes conversations while preserving critical details
- **Token Usage Tracking**: `/status` command shows model, approval policy, and current token usage
- **Efficient Token Usage**: GPT-5.3-Codex achieves state-of-the-art performance with fewer tokens than any prior model

### Features

**Research Date:** 2026-02-09
**Sources:** [Codex CLI Features](https://developers.openai.com/codex/cli/features/), [Codex Changelog](https://developers.openai.com/codex/changelog/), [GitHub Releases](https://github.com/openai/codex/releases)

#### 1. Hooks Support
**Status:** Limited Support

- **Notification Hooks**: Triggered when Codex completes a task
- **Note**: Full hooks system is under active discussion in the community (GitHub Issue #2150)

#### 2. MCP (Model Context Protocol) Support
**Status:** Full Support

- **STDIO Servers**: Local process servers started by command
- **HTTP Servers**: Remote servers accessed at an address
- **Configuration**: `codex mcp add <server-name>` command
- **Config Files**: `~/.codex/config.toml` or `.codex/config.toml` for project-specific
- **Codex as MCP Server**: Exposes `codex()` and `codex-reply()` tools
- **Agents SDK Integration**: Compatible with OpenAI Agents SDK for orchestration

#### 3. Sub-agents Capability
**Status:** Beta Support

- **Agents SDK Integration**: Full integration with OpenAI Agents SDK
- **Multi-agent Workflows**: Codex can be orchestrated as part of larger workflows
- **Personal Skills**: Load from `~/.agents/skills` directory
- **Collaboration Mode**: Beta feature with plan → execute handoff

#### 4. Slash Commands
**Status:** Full Support

**Built-in Commands:**
- `/status` - View active model, approval policy, writable roots, token usage
- `/compact` - Summarize long conversations to free context
- `/mention` - Add files to conversation by path
- `/new` - Start fresh conversation in same CLI session
- `/resume` - Continue previous saved sessions
- `/fork` - Clone current conversation into new thread
- `/init` - Create AGENTS.md scaffold for repository conventions
- `/review` - Summarize issues in working tree
- `/model` - Switch between models or adjust reasoning levels
- `/permissions` (or `/approvals`) - Manage approval settings
- `/debug-config` - Inspect effective configuration
- `/plan` - Accepts inline prompt arguments and pasted images

**Custom Commands:**
- Team-specific shortcuts supported
- Reusable prompts for common workflows

#### 5. IDE Integrations
**Status:** Full Support (Multi-platform)

**Supported IDEs:**
- **VS Code**: Official Codex VS Code extension
- **JetBrains IDEs** (v2025.3+): IntelliJ, PyCharm, WebStorm, Rider
  - Native integration in AI chat
  - Authentication: JetBrains AI, ChatGPT, or BYOK
- **Cursor**: Compatible with Codex IDE extension
- **Windsurf**: Compatible with Codex IDE extension
- **Visual Studio, Xcode, Eclipse**: GPT-5.2-Codex available (Jan 26, 2026)

#### 6. Git Integration Features
**Status:** Full Support

- **Change Tracking**: Shows changes as diffs before committing
- **Commit Workflow**: Auto-commit with meaningful messages
- **Code Review**:
  - Review against base branch
  - Review uncommitted changes
  - Review specific commits by SHA
- **Safety Features**: Git command safety hardened; destructive operations require approval
- **Transcript History**: All actions surfaced for git review/rollback
- **GitHub Integration**: Public preview (Feb 4, 2026)

#### 7. Web Search Capability
**Status:** Built-in Tool

- **First-party Search**: Enabled by default for local tasks
- **Caching**: Uses cached results or live fetching based on configuration
- **No Setup Required**: Works out of the box

#### 8. Sandbox/Approval Modes
**Status:** Full Support

**Three Approval Modes:**
- **Suggest Mode** (default): Requires approval for all actions
- **Auto-Edit Mode**: Auto-applies file changes; requires approval for shell commands
- **Full-Auto Mode**: Fully autonomous without user input

**Sandbox Controls:**
- **OS-enforced Sandbox**: Limits workspace access, network reach, command execution
- **Approval Policy**: When Codex must ask before acting
- **Network Sandbox**: Policy enforcement proxy for outbound network access
- **Switch Modes**: Via `/approvals` or `/permissions` command

#### 9. Cost Tracking Options
**Status:** Partial Support

**Available:**
- `/status` command shows current token usage and remaining limits
- Codex usage dashboard shows limits
- **Third-party Tool**: `ccusage` package for analyzing token usage/costs from local JSONL files

**Missing:**
- No comprehensive built-in cost analytics (GitHub Issue #5085 tracking feature request)

**Pricing:**
- Included with ChatGPT Plus ($20/month) or Pro ($200/month)
- API access: codex-mini-latest ($1.50/M input, $6.00/M output)

#### 10. Additional Features (2026)

**New in 2026:**
- **Steer Mode** (Jan 2026): Stable and default - Enter sends immediately, Tab queues follow-up
- **GPT-5.3-Codex Support** (Feb 2026): Mid-turn steering capabilities
- **Codex Desktop Launch** (Jan 2026): `codex app <path>` on macOS
- **Image Inputs**: Screenshots and design specs alongside prompts
- **Non-interactive Automation**: `exec` subcommand for scripting and CI integration
- **Cloud Integration**: Launch and manage Codex cloud tasks from terminal
- **Shell Completions**: bash, zsh, and fish auto-completion
- **Conversation Resuming**: Local transcript storage with resume capability
- **Memory Features**: Initial memory plumbing with thread memory summaries
- **GitHub Integration**: Public preview (Feb 4, 2026)

**Core Features:**
- **Interactive Mode**: Full-screen terminal UI with real-time review
- **Code Review**: Dedicated reviewer accessible via `/review`
- **Multi-directory Coordination**: `--add-dir` flag
- **Quick Shortcuts**: File search (`@`), command injection (`!`), transcript navigation (Esc)

#### Summary

Codex CLI is a production-ready CLI coding agent with:

**Strengths:**
- Multiple model options (400k to 1M token context windows)
- Full MCP integration for extensibility
- Native IDE support across major platforms
- Robust git workflow integration
- Flexible approval and sandbox controls
- Web search and multi-modal inputs
- Active development with frequent updates

**Limitations:**
- Limited hooks support (only notification hooks)
- No comprehensive built-in cost tracking/analytics

**Best For:**
- Teams using OpenAI models
- Multi-platform IDE integration needs
- Developers prioritizing model variety (reasoning vs speed)
- Projects requiring MCP extensibility

---

## Cursor Research
**Agent:** Elena Rodriguez
**Status:** Complete

### Context Windows

**Research Date:** 2026-02-09
**Sources:** [Cursor Models](https://cursor.com/docs/models), [Cursor Changelog](https://cursor.com/changelog), [Composer Blog](https://cursor.com/blog/composer)

Cursor supports frontier models from four major providers plus its own native model.

#### Anthropic Claude Models

| Model | Context Window | Max Mode | Notes |
|-------|---------------|----------|-------|
| Claude 4.6 Opus | 200k | 1M | Latest (Feb 5, 2026), 2x cost above 200k |
| Claude 4.5 Sonnet | 200k | 1M | 2x cost above 200k |
| Claude 4 Sonnet | 200k | 1M | Hidden by default, 2x cost above 200k |

#### OpenAI GPT Models

| Model | Context Window | Notes |
|-------|---------------|-------|
| GPT-5.3 Codex | 272k | Latest (Feb 5, 2026), 77.3% Terminal-Bench |
| GPT-5.2 | 272k | Stable |
| GPT-5 series | Various | Most hidden by default |

#### Google Gemini Models

| Model | Context Window | Max Mode | Native | Notes |
|-------|---------------|----------|--------|-------|
| Gemini 3 Pro | 200k | 1M | 2M | Visual reasoning leader |
| Gemini 3 Flash | 200k | 1M | - | - |
| Gemini 2.5 Flash | 200k | 1M | - | Hidden, $0.3M input |

#### xAI Grok Models

| Model | Context Window | Notes |
|-------|---------------|-------|
| Grok 4 Code | 131k-2M | Varies by variant, multimodal |
| Grok Code Fast 1 | 1M | Cost-effective: $0.2M input |

#### Cursor Native Models

| Model | Context Window | Speed | Pricing |
|-------|---------------|-------|---------|
| Composer 1 | 200k | 250 tok/sec (4x faster) | $1.25/M in, $10/M out |

- MoE architecture, RL-trained on real engineering tasks
- Completes most turns in <30 seconds

#### DeepSeek Models

| Model | Context Window | Notes |
|-------|---------------|-------|
| DeepSeek R1 | Standard | Free tier, US servers (Fireworks.ai) |
| DeepSeek V3 | Standard | Free tier, US servers |

#### Context Features
- **Standard**: 200k tokens (~15,000 lines of code)
- **Max Mode**: 1M-2M tokens (model-dependent)
- **Cost**: 2x for Claude/Gemini above 200k
- **Privacy**: Encrypted storage, obfuscated filenames

#### Recent Changes
- **Late 2025**: Free models moved to request-based pricing
- **Dec 2025**: v2.1.42 temporarily removed models
- **2025**: Token-based → unified request-based pricing

### Features

**Research Date:** 2026-02-09

#### 1. Hooks System (Jan 2026 - 40x faster)
**Full lifecycle control via custom scripts**

**Events:** sessionStart/End, preToolUse, postToolUse/Failure, subagentStart/Stop, beforeShellExecution, afterShellExecution, beforeMCPExecution, afterMCPExecution, beforeReadFile, afterFileEdit, beforeTabFileRead, afterTabFileEdit, beforeSubmitPrompt, preCompact, stop, afterAgentResponse, afterAgentThought

**Config:** `.cursor/hooks.json` (project), `~/.cursor/hooks.json` (user), system paths

**Types:** Command-based (shell) or Prompt-based (LLM policies)

**Partners:** MintMCP, Oasis, Runlayer, Corridor, Semgrep, Endor Labs, Snyk, 1Password

#### 2. MCP (Model Context Protocol)
**External tools and data sources**

- Automatic OAuth callback handling
- `/mcp list`, `/mcp enable`, `/mcp disable`
- On-demand JSON loading in `.cursor/`
- Immediate authenticated MCP access
- Jan 2026: Improved login, reduced tokens

#### 3. Sub-Agents (Jan 22, 2026)
**Parallel independent agents**

**Built-in:** Explore (codebase), Bash (shell isolation), Browser (MCP interactions)

**Custom:** `.cursor/agents/` or `~/.cursor/agents/`

**Modes:** Foreground (blocking) / Background (async)

**Limits:** Single-level only, token multiplication in parallel

#### 4. Slash Commands
- `/plan` - Design with clarifying questions
- `/ask` - Non-destructive exploration
- `/models` - List/switch models
- `/rules` - Edit rules
- `/mcp enable/disable` - MCP management
- `/summarize` - Context summarization

#### 5. Custom Rules
**AI behavior configuration**

- **Legacy:** `.cursorrules` (deprecated, will be removed)
- **Current:**
  - User Rules: Settings > General > Rules for AI
  - Project Rules: `.cursor/rules/*.mdc`
  - Skills: `SKILL.md` (Jan 22, 2026) - dynamic context discovery
- `/rules` command (Jan 8, 2026)

#### 6. Composer/Agent Mode (Cursor 2.0 - Nov 2025)
**Multi-file editing, agent-centric interface**

- Native ultra-fast model (4x speed)
- Agents/plans/runs as sidebar objects
- Multiple parallel agents per project
- 4 layouts: agent, editor, zen, browser (⌘⌥⇥)
- Clarifying questions mid-conversation (Jan 22, 2026)
- Word-level inline diffs (CLI - Jan 16, 2026)

#### 7. Git Integration
- Commit Composer - AI-organized messages
- @Branch, @Git context symbols
- Stage, commit, push/pull automation
- **Cursor Blame** (Enterprise, Jan 22, 2026) - AI attribution
- GitButler hooks (v1.7) - Auto-commits from chats

#### 8. Web Search (@Web)
- `@Web [query]` in prompts
- Settings > Features > Web Search (off by default)
- "Always search" option
- Fairness limits apply

#### 9. Background/Cloud Agents (2025 release)
- Prepend `&` to push to cloud
- Clone GitHub repos, separate branches
- Ubuntu-based isolated machines
- Continue at cursor.com/agents
- Use cases: parallel dev, long-running tasks

#### 10. Codebase Indexing
- Merkle tree of file hashes
- 10-minute incremental sync
- Server-side embedding (Turbopuffer)
- Encrypted storage, obfuscated filenames
- `.cursorignore` exclusions

#### 11. VS Code Extension Compatibility
- 99%+ extensions work
- Open VSX Registry (not MS Marketplace per ToS)
- One-Click Import on first launch
- **Problematic:** Pylance (use BasedPyright), C# Dev Kit, C/C++ (use clangd), Live Share
- 90% cross-published to both registries

#### 12. Memories (Cursor 1.0 - Feb 3, 2026)
- AI remembers conversation facts
- Background Agent workflow adaptation
- Tailored support across sessions
- **Ecosystem:** Memory Bank (community), SpecStory (durable knowledge)

#### 13. Enterprise Features
- **Conversation Insights** (Dec 18, 2025) - Analytics
- **Transcript Sharing** (Dec 18, 2025) - Read-only with fork
- **Billing Groups** (Dec 18, 2025) - Spend tracking
- **Linux Sandboxing** (Dec 18, 2025) - Configurable access
- **Service Accounts** (Dec 18, 2025) - Non-human automation
- **Cursor Blame** (Jan 22, 2026) - AI attribution

#### 14. Additional Features
- **Image Generation** (Jan 22, 2026) - Google Nano Banana Pro
- **Browser:** 10x faster, drag-and-drop, locking
- **Auto Model Selection:** Performance-based switching
- **Layout:** 4 switchable presets

#### Summary

Cursor is a multi-model IDE with comprehensive features:

**Strengths:**
- Multi-provider support (Claude, GPT, Gemini, Grok, DeepSeek, Composer)
- 200k-2M context windows with Max Mode
- Extensive hooks (40x faster in 2026)
- Full MCP + sub-agents + cloud execution
- VS Code compatibility (99%+)
- Enterprise analytics and attribution
- Memories for persistent context

**Limitations:**
- Rules migration from .cursorrules to .cursor/rules/
- VS Code Marketplace restrictions (MS proprietary extensions)
- Max Mode 2x pricing above 200k for Claude/Gemini

**Best For:**
- Teams wanting model flexibility
- Projects needing parallel agent workflows
- Organizations with VS Code infrastructure
- Developers prioritizing speed (Composer 1)

---

## Gemini CLI Research
**Agent:** Dr. Raj Patel
**Status:** Complete

### Context Windows

**Research Date:** 2026-02-09
**Sources:** [Gemini API Models](https://ai.google.dev/gemini-api/docs/models), [Gemini CLI GitHub](https://github.com/google-gemini/gemini-cli)

#### Current Models (February 2026)

| Model Name | Context Window | Max Output Tokens | Status | Notes |
|------------|---------------|-------------------|---------|-------|
| Gemini 3 Pro Preview | 1,048,576 (1M) | 65,536 (64K) | Preview | Released November 2025 |
| Gemini 3 Flash Preview | 1,048,576 (1M) | 65,536 (64K) | Preview | Released December 2025 |
| Gemini 2.5 Pro | 1,048,576 (1M) | 65,536 (64K) | Stable | Released June 2025 |
| Gemini 2.5 Flash | 1,048,576 (1M) | 65,536 (64K) | Stable | Released June 2025 |
| Gemini 2.5 Flash-Lite | 1,048,576 (1M) | 65,536 (64K) | Stable | Released July 2025 |

#### Deprecated Models

| Model Name | Context Window | Max Output Tokens | Shutdown Date |
|------------|---------------|-------------------|---------------|
| Gemini 2.0 Flash | 1,048,576 (1M) | 8,192 (8K) | March 31, 2026 |
| Gemini 2.0 Flash-Lite | 1,048,576 (1M) | 8,192 (8K) | March 31, 2026 |

#### Key Findings

- **Industry-Leading Context**: All current Gemini models support 1M token context windows (1,048,576 tokens exactly)
- **Enhanced Output**: Gemini 2.5 and 3.x models significantly increased max output from 8K to 64K tokens compared to 2.0 models
- **Model Transition**: Gemini 2.0 Flash models are being phased out on March 31, 2026
- **Context Capabilities**: 1M tokens = ~1,500 pages of text or ~30,000 lines of code
- **Multimodal Support**: Context window handles text, code, images, and video
- **Token Caching**: Built-in token caching optimizes performance and costs for repeated context

### Features

**Research Date:** 2026-02-09
**Sources:** [Gemini CLI Docs](https://geminicli.com/docs/), [Gemini CLI Hooks](https://geminicli.com/docs/hooks/), [Google Developers Blog](https://developers.googleblog.com/)

#### 1. Hooks Support
**Status:** Full Support

- **10 Lifecycle Events**: SessionStart, SessionEnd, BeforeAgent, AfterAgent, BeforeModel, AfterModel, BeforeToolSelection, BeforeTool, AfterTool, PreCompress
- **Hook Types**: Scripts/programs executed at specific points in the agentic loop
- **Configuration**: Defined in settings.json with matcher patterns, timeouts, and commands
- **Security**: Hooks execute with user privileges; fingerprinting alerts for changed commands
- **Management**: `/hooks` command panel, enable/disable individual or all hooks
- **Exit Codes**: 0 (success), 2 (system block), other (warning)
- **JSON Communication**: Strict JSON communication via stdin/stdout for hook responses

#### 2. Extensions/MCP Support
**Status:** Full Support via Model Context Protocol

- **MCP Servers**: Connect to external services using Model Context Protocol
- **Custom Tools**: Expose tools and resources through MCP
- **Prompts as Commands**: MCP servers can expose prompts as slash commands
- **FastMCP Integration**: Seamless integration with FastMCP (Python's leading MCP library) as of FastMCP v2.12.3
- **Official Google MCP**: Enterprise-ready endpoints for Google and Google Cloud services
- **Installation**: `fastmcp install gemini-cli` command
- **Extensions System**: Create custom tools and behaviors

#### 3. Sub-agents Capability
**Status:** Experimental (Preview)

- **Specialized Agents**: Operate within main session for specific tasks
- **Independent Context**: Each sub-agent has own system prompt, persona, and toolset
- **Tool Delegation**: Exposed to main agent as tools for task delegation
- **JSON Schema**: Sub-agents use JSON schema for input
- **AgentRegistry**: Tracked by centralized AgentRegistry
- **A2A Protocol**: Supports Agent-to-Agent protocol for remote sub-agents (experimental)
- **YOLO Mode**: Currently operates without individual confirmation (use with caution)
- **Use Cases**: Deep codebase analysis, documentation lookup, domain-specific reasoning

#### 4. Slash Commands
**Status:** Full Support

Built-in commands include:
- `/version` - Show version info
- `/auth` - Change authentication method
- `/bug` - File issue about Gemini CLI
- `/chat` - Save and resume conversation history
- `/checkpoint` - Save conversation state with tags
- `/export` - Write conversation to Markdown/JSON
- `/copy` - Copy last output to clipboard
- `/docs` - Open documentation in browser
- `/help` - Display help information
- `/hooks` - Show all hooks and status
- `/hooks enable-all` / `/hooks disable-all` - Toggle hooks globally
- `/hooks enable <name>` / `/hooks disable <name>` - Toggle individual hooks
- `/agents refresh` - Update agent configurations
- `/skills reload` - Refresh skill definitions
- `/skills install/uninstall` - Manage Agent Skills
- `/stats` - Show token usage and cached token savings
- `/subagents` - Manage sub-agents

#### 5. Custom Commands (GEMINI.md, TOML config)
**Status:** Full Support

- **GEMINI.md**: Project-specific persistent context files
- **TOML Configuration**: Define custom slash commands in .toml files
- **MCP Prompts**: Custom commands via Model Context Protocol prompts
- **System Prompt Override**: Customize core model instructions
- **Custom Shortcuts**: Create reusable prompts for common workflows
- **Configuration Layers**: Project (.gemini/settings.json), User (~/.gemini/settings.json), System (/etc/gemini-cli/settings.json), Extensions
- **Memory Persistence**: Store facts about projects across sessions

#### 6. IDE Integrations
**Status:** Visual Studio Code Only

- **VS Code Extension**: Gemini CLI Companion (official)
- **Workspace Context**: Auto-awareness of 10 most recent files, cursor position, selected text (16KB limit)
- **Native Diffing**: View code changes in VS Code's native diff viewer
- **Command Palette**: Access Gemini CLI features via VS Code commands
  - "Gemini CLI: Run"
  - "Gemini CLI: Accept Diff"
  - "Gemini CLI: Close Diff Editor"
- **Validated Version**: v0.23.0+ (as of January 8, 2026)
- **Context-Aware Workflows**: Seamless integration with editor state

#### 7. Git Integration Features
**Status:** Full Support

- **Git Operations**: Analyze repository changes, pull requests, complex rebases
- **Git History Analysis**: Intelligent summaries of code evolution
- **Interactive Commands**: Support for interactive git rebase within CLI
- **GitHub Actions**: Beta integration for automated workflows
  - Issue triage and labeling based on content analysis
  - Pull request reviews
  - Automated issue management
  - gh CLI integration for powerful automations
  - Extensible tool-calling capabilities
- **PR Creator Skill**: New skill for creating pull requests (2026)
- **Security Enhancements**: Default folder trust set to untrusted, granular allowlisting for shell commands
- **Commit Management**: Interactive git commands with AI assistance

#### 8. Web Search (Google Search Grounding)
**Status:** Built-in Tool

- **Grounding with Google Search**: Connects Gemini to real-time web content
- **All Languages**: Works with all available languages
- **Automatic Activation**: Model analyzes prompt and assigns prediction score (0-1) to decide if web search would help
- **Query Generation**: Automatically generates one or more search queries when beneficial
- **Result Synthesis**: Model processes search results and formulates response
- **Citation Inclusion**: Responses include grounding metadata with sources, search queries, web results
- **Hallucination Reduction**: ~40% reduction compared to non-grounded responses
- **Increased Factual Accuracy**: Base responses on real-world information
- **Real-time Information**: Access recent events and topics
- **Free Tier**: Included with Google account authentication
- **Paid Tier**: Each search query is billable
- **Configuration**: Can be disabled by adding google_web_search to tools.exclude array in settings.json

#### 9. Sandbox Modes
**Status:** Full Support

- **Isolated Execution**: Execute untrusted code/tools in secure, isolated container
- **Checkpointing**: Save and restore workspace state
- **Headless Mode**: Run in scripts or CI/CD pipelines for automated reasoning
- **Security Isolation**: Protects host system from potentially harmful operations
- **Untrusted Projects**: Safe handling of project-level hooks from untrusted sources

#### 10. Google Cloud Integration
**Status:** Full Support

- **Cloud Monitoring**: Pre-configured dashboards for telemetry and metrics (2026 enhancement)
- **Usage Metrics**: Monthly/daily active users, installs, token consumption
- **Performance Tracking**: Lines of code added/removed, API/tool calls
- **Vertex AI**: Integration with Google Cloud's Vertex AI platform
- **Enterprise Features**: Official MCP endpoints for Google Cloud services
- **Instant Visibility**: High-level visibility into adoption, interaction patterns, and performance
- **Dashboard Metrics**: Immediate access to CLI usage and performance data

#### 11. Cost Tracking (/stats)
**Status:** Full Support

- **Stats Command**: `/stats` displays model usage summary
- **Exit Summary**: Token usage presented on session exit
- **Token Tracking**: Input tokens, output tokens, cached tokens
- **Cached Token Savings**: Shows efficiency gains from token caching
- **Monitoring Dashboards**: Google Cloud Monitoring integration (2026 enhancement)
- **Community Enhancements**: Developers have added spending calculations based on Gemini API pricing
- **Billing Transparency**: Clear visibility into usage costs

#### 12. New Features (Late 2025 - Early 2026)

**Recent Additions:**
- **Gemini 3 Models**: Preview releases (November-December 2025) with improved reasoning and 1M token context
- **FastMCP v2.12.3 Integration**: Seamless MCP server installation (January 2026)
- **Monitoring Dashboards**: Pre-configured Google Cloud dashboards for instant visibility (2026)
- **PR Creator Skill**: Automated pull request creation (2026)
- **Security Hardening**: Default untrusted folders, granular shell command allowlisting (2026)
- **VS Code Enhancements**: Native diffing and context-aware workflows
- **GitHub Actions Beta**: Automated issue triage and PR reviews with generous free quotas
- **Agent Registry**: Centralized tracking for sub-agents
- **A2A Protocol**: Remote sub-agent support (experimental)
- **Hooks Fingerprinting**: Security alerts for modified hook commands
- **Memory Persistence**: Store and recall project-specific facts across sessions
- **Agent Skills**: Add specialized expertise and workflows
- **Theme Customization**: UI theme options
- **Telemetry Controls**: User control over data collection
- **.geminiignore Files**: Exclude files from context
- **Trusted Folders**: Security configuration for project access

#### Summary

Gemini CLI offers a comprehensive feature set with industry-leading 1M token context windows across all current models. Key strengths include:

1. **Extensibility**: Robust hooks system (10 lifecycle events) + full MCP support with FastMCP integration
2. **Agentic Capabilities**: Experimental sub-agents with specialized task delegation and A2A protocol
3. **Developer Experience**: Rich slash commands, custom configurations, VS Code integration, GEMINI.md files
4. **Web Intelligence**: Built-in Google Search grounding reduces hallucinations by ~40%
5. **Enterprise Ready**: Google Cloud integration, monitoring dashboards, cost tracking, security hardening
6. **Git-First**: Native GitHub Actions, interactive git operations, PR automation, issue triage
7. **Multimodal Context**: 1M token window handles text, code, images, and video
8. **Security Focus**: Hooks fingerprinting, default untrusted folders, granular permissions

The CLI is actively developed with significant enhancements in late 2025 and early 2026, particularly around security, monitoring, and agentic workflows. Gemini 2.0 models are being deprecated (March 31, 2026) in favor of Gemini 2.5 and 3.x models with 8x larger output tokens (64K vs 8K).
