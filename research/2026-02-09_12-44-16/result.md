# Research Results & Proposed Updates

**Research Date:** 2026-02-09 12:44:16 UTC
**Status:** Complete - Awaiting User Approval

---

## Executive Summary

All 4 research agents completed successfully. Significant updates found across context windows and features for all tools.

| Tool | Context Window Changes | Feature Changes | Priority |
|------|------------------------|-----------------|----------|
| **Claude Code** | ✅ Major (Opus 4.6 released) | ✅ Significant (Agent Teams, Chrome beta) | HIGH |
| **Codex CLI** | ✅ Major (GPT-5.3-Codex default) | ✅ Moderate (GitHub integration preview) | HIGH |
| **Cursor** | ✅ Moderate (Multi-model updates) | ✅ Significant (40x faster hooks, Memories) | MEDIUM |
| **Gemini CLI** | ⚠️ Minor (Gemini 3 Preview) | ✅ Significant (A2A protocol, FastMCP) | MEDIUM |

---

## Proposed Context Window Updates

### New Table for README.md

```markdown
| Tool | Largest Context | Best Model | Input $/M | Output $/M | Source |
|------|-----------------|------------|-----------|------------|--------|
| Claude Code | 1M (beta) | Opus 4.6 with `context-1m-2025-08-07` beta | $5.00 | $25.00 | [Anthropic Models](https://docs.anthropic.com/en/docs/about-claude/models) |
| Codex CLI | 400k | GPT-5.3-Codex (Feb 2026) | TBD* | TBD* | [OpenAI Models](https://platform.openai.com/docs/models) |
| Cursor | 2M (native) | Gemini 3 Pro (200k/1M/2M modes) | $2.00** | $12.00** | [Cursor Models](https://cursor.com/docs/models) |
| Gemini CLI | 1M | Gemini 3 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |
```

> \* GPT-5.3-Codex pricing not yet published by OpenAI (Feb 2026 release)
> \*\* Cursor uses subscription pricing ($20/mo Pro); API prices shown are for underlying models

### Changes from Current README

**Claude Code:**
- ✅ No change needed - Already shows Opus 4.6 with 1M beta

**Codex CLI:**
- **CHANGED:** Best model updated from "GPT-5.3-Codex (context compaction)" to "GPT-5.3-Codex (Feb 2026)"
- **REASON:** Research confirms GPT-5.3-Codex is now default model (Feb 2026), context compaction is native

**Cursor:**
- **CHANGED:** Best model from "Grok 4" to "Gemini 3 Pro (200k/1M/2M modes)"
- **CHANGED:** Largest context from "2M (Max mode)" to "2M (native)"
- **CHANGED:** Pricing from "$3.00" / "$15.00" to "$2.00" / "$12.00"
- **REASON:** Research shows Gemini 3 Pro has native 2M context, not just Max mode. Grok 4 Code context is 131k-2M (varies by variant), making Gemini 3 Pro the more reliable 2M option

**Gemini CLI:**
- ✅ No change needed - Already accurate

---

## Proposed Feature Comparison Updates

### New Table for README.md

```markdown
| Feature | Claude Code | Codex CLI | Gemini CLI | Cursor |
|---------|:-----------:|:---------:|:----------:|:------:|
| **Hooks** | ✅ 9+ types | ⚠️ Limited | ✅ 10 events | ✅ 40x faster |
| **Plugins/MCP** | ✅ Full | ✅ Full | ✅ FastMCP | ✅ Full |
| **Sub-agents** | ✅ Teams (exp) | ✅ Beta | ✅ A2A (exp) | ✅ Custom |
| **Slash Commands** | ✅ Custom | ✅ Custom | ✅ Custom | ✅ Custom |
| **Custom Commands** | ✅ Skills | ✅ AGENTS.md | ✅ GEMINI.md | ✅ Rules |
| **IDE Integration** | ✅ VS/JetBrains | ✅ Multi-platform | ✅ VS Code | ✅ Native |
| **Git Integration** | ✅ Hub (beta) | ✅ GitHub (preview) | ✅ Actions (beta) | ✅ Blame (ent) |
| **Web Search** | ✅ US only | ✅ Built-in | ✅ Grounding | ✅ @Web |
| **Image Support** | ✅ Full | ✅ Full | ✅ Full | ✅ Full |
| **Memory/Persistence** | ✅ Session | ✅ Thread | ✅ Project | ✅ Memories |
| **Multi-file Editing** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Composer |
| **Auto-commit** | ⚠️ Via hooks | ⚠️ Manual | ✅ Native | ✅ Native |
| **Custom System Prompts** | ✅ Settings | ✅ AGENTS.md | ✅ GEMINI.md | ✅ Rules |
| **Cost Tracking** | ✅ Dashboard | ⚠️ /status | ✅ /stats | ⚠️ Enterprise |
| **Sandbox Mode** | ✅ Native | ✅ OS-enforced | ✅ Container | ✅ Linux (ent) |
```

### Feature Changes from Current README

**Legend:**
- ✅ = Full support
- ⚠️ = Partial/Limited support
- ❌ = Not supported
- (exp) = Experimental
- (ent) = Enterprise only
- (beta) = Beta/preview

**Key Changes:**

1. **Hooks Row:**
   - Claude Code: Changed from "✅" to "✅ 9+ types" (more specific)
   - Codex CLI: No change (still "⚠️ Limited")
   - Gemini CLI: Changed from "✅" to "✅ 10 events" (more specific)
   - Cursor: Changed from "✅" to "✅ 40x faster" (highlights Jan 2026 performance improvement)

2. **Plugins/MCP Row:**
   - Claude Code: Changed from "✅" to "✅ Full"
   - Codex CLI: Changed from "✅" to "✅ Full"
   - Gemini CLI: Changed from "✅" to "✅ FastMCP" (highlights v2.12.3 integration)
   - Cursor: Changed from "✅" to "✅ Full"

3. **Sub-agents Row:**
   - Claude Code: Changed from "✅" to "✅ Teams (exp)" (highlights Agent Teams experimental feature)
   - Codex CLI: Changed from "✅" to "✅ Beta" (more accurate status)
   - Gemini CLI: Changed from "✅" to "✅ A2A (exp)" (highlights Agent-to-Agent protocol)
   - Cursor: Changed from "✅" to "✅ Custom" (highlights .cursor/agents/ custom agents)

4. **Custom Commands Row:**
   - Claude Code: Changed from "✅" to "✅ Skills" (highlights Skills system)
   - Codex CLI: Changed from "✅" to "✅ AGENTS.md" (specific file format)
   - Gemini CLI: Changed from "✅" to "✅ GEMINI.md" (specific file format)
   - Cursor: Changed from "✅" to "✅ Rules" (highlights .cursor/rules/)

5. **IDE Integration Row:**
   - Claude Code: Changed from "✅" to "✅ VS/JetBrains"
   - Codex CLI: Changed from "✅" to "✅ Multi-platform" (supports VS Code, JetBrains, Visual Studio, Xcode, Eclipse, Cursor, Windsurf)
   - Gemini CLI: Changed from "✅" to "✅ VS Code" (only VS Code supported)
   - Cursor: Changed from "✅" to "✅ Native" (it IS the IDE)

6. **Git Integration Row:**
   - Claude Code: Changed from "✅" to "✅ Hub (beta)" (Claude Hub feature)
   - Codex CLI: Changed from "✅" to "✅ GitHub (preview)" (Feb 4, 2026 public preview)
   - Gemini CLI: Changed from "✅" to "✅ Actions (beta)" (GitHub Actions integration)
   - Cursor: Changed from "✅" to "✅ Blame (ent)" (Cursor Blame enterprise feature)

7. **Web Search Row:**
   - Claude Code: Changed from "✅" to "✅ US only"
   - Codex CLI: Changed from "✅" to "✅ Built-in"
   - Gemini CLI: Changed from "✅" to "✅ Grounding" (Google Search grounding)
   - Cursor: Changed from "✅" to "✅ @Web"

8. **Image Support Row:**
   - Claude Code: Changed from "✅" to "✅ Full"
   - Codex CLI: Changed from "✅" to "✅ Full"
   - Gemini CLI: Changed from "✅" to "✅ Full"
   - Cursor: Changed from "⚠️" to "✅ Full" (research shows full image generation support via Google Nano Banana Pro as of Jan 22, 2026)

9. **Memory/Persistence Row:**
   - Claude Code: Changed from "✅" to "✅ Session" (session restore/teleport)
   - Codex CLI: Changed from "✅" to "✅ Thread" (thread memory summaries)
   - Gemini CLI: Changed from "✅" to "✅ Project" (project-specific memory persistence)
   - Cursor: Changed from "⚠️" to "✅ Memories" (Memories feature released Feb 3, 2026)

10. **Multi-file Editing Row:**
    - Claude Code: Changed from "✅" to "✅ Yes"
    - Codex CLI: Changed from "✅" to "✅ Yes"
    - Gemini CLI: Changed from "✅" to "✅ Yes"
    - Cursor: Changed from "✅" to "✅ Composer" (highlights Composer mode)

11. **Cost Tracking Row:**
    - Claude Code: Changed from "✅" to "✅ Dashboard" (Claudia dashboard)
    - Codex CLI: Changed from "❌" to "⚠️ /status" (partial support via /status command)
    - Gemini CLI: Changed from "✅" to "✅ /stats" (highlights /stats command)
    - Cursor: Changed from "⚠️" to "⚠️ Enterprise" (Conversation Insights is enterprise-only)

12. **Sandbox Mode Row:**
    - Claude Code: Changed from "✅" to "✅ Native" (OS-level native sandboxing)
    - Codex CLI: Changed from "✅" to "✅ OS-enforced"
    - Gemini CLI: Changed from "✅" to "✅ Container" (isolated container execution)
    - Cursor: Changed from "⚠️" to "✅ Linux (ent)" (Linux Sandboxing is enterprise feature, Dec 18, 2025)

---

## Detailed Context Window Changes

### Claude Code

**Current State (README):**
- Largest Context: 1M (beta)
- Best Model: Opus 4.6 with `--betas context-1m-2025-08-07`

**Research Findings:**
- ✅ Opus 4.6 released Feb 5, 2026
- ✅ Context: 200K standard / 1M beta via `context-1m-2025-08-07` header
- ✅ Max output: 128K tokens (largest among all 4.x models)
- ✅ Sonnet 4.5: 200K / 1M beta, 64K output
- ✅ Haiku 4.5: 200K, 64K output
- ✅ Context awareness feature for Sonnet 4.5 and Haiku 4.5

**Recommendation:** No changes needed to README context window table.

**Detailed Report Updates Needed:**
- ✅ Add Opus 4.6 to primary models table
- ✅ Update knowledge cutoffs (Opus 4.6: May 2025 reliable / Aug 2025 training)
- ✅ Clarify 1M context availability (tier 4 orgs, pay-as-you-go, NOT subscription users at launch)
- ✅ Add context awareness feature documentation
- ✅ Update model aliases (`opusplan` hybrid mode)

---

### Codex CLI

**Current State (README):**
- Largest Context: 400k+
- Best Model: GPT-5.3-Codex (context compaction)

**Research Findings:**
- ✅ GPT-5.3-Codex: 400K tokens, NEW DEFAULT as of Feb 2026
- ✅ 25% faster than predecessors
- ✅ GPT-5.2-Codex: 400K tokens (stable)
- ✅ codex-mini-latest: 200K tokens (fine-tuned o4-mini)
- ✅ GPT-4.1: 1M tokens (legacy, still available)
- ⚠️ Pricing for GPT-5.3-Codex NOT YET PUBLISHED

**Recommendation:** Minor update to clarify GPT-5.3-Codex is Feb 2026 release.

**Current:**
```
Best Model: GPT-5.3-Codex (context compaction)
```

**Proposed:**
```
Best Model: GPT-5.3-Codex (Feb 2026)
```

**Detailed Report Updates Needed:**
- ✅ Add GPT-5.3-Codex to primary models (Feb 2026 release)
- ✅ Update codex-mini-latest to 200K tokens (not ~200k)
- ✅ Add o3, o4-mini to reasoning models section
- ✅ Update deprecation timeline (o1-preview/o1-mini deprecated April 28, 2025)
- ⚠️ Mark GPT-5.3-Codex pricing as TBD

---

### Cursor

**Current State (README):**
- Largest Context: 2M (Max mode)
- Best Model: Grok 4
- Pricing: $3.00 / $15.00

**Research Findings:**
- ✅ Multi-model support across 5 providers
- ✅ Claude 4.6 Opus: 200k / 1M (2x cost above 200k)
- ✅ GPT-5.3 Codex: 272k (77.3% Terminal-Bench, Feb 5, 2026)
- ✅ Gemini 3 Pro: 200k / 1M / **2M NATIVE** ($2.00/$12.00)
- ✅ Grok 4 Code: 131k-2M (varies by variant, $3.00/$15.00)
- ✅ Composer 1: 200k native, 250 tok/sec (4x faster)

**Recommendation:** Update to Gemini 3 Pro as best model for largest context.

**Current:**
```
| Cursor | 2M (Max mode) | Grok 4 | $3.00** | $15.00** |
```

**Proposed:**
```
| Cursor | 2M (native) | Gemini 3 Pro (200k/1M/2M modes) | $2.00** | $12.00** |
```

**Reasoning:**
- Gemini 3 Pro has NATIVE 2M context support, not just Max mode
- Grok 4 Code context is 131k-2M (varies), less reliable
- Gemini 3 Pro is more cost-effective ($2/$12 vs $3/$15)
- Gemini 3 Pro leads visual reasoning benchmarks

**Detailed Report Updates Needed:**
- ✅ Add Claude 4.6 Opus (Feb 5, 2026)
- ✅ Add GPT-5.3 Codex (Feb 5, 2026, 272k context)
- ✅ Update Gemini 3 Pro to show 2M native context
- ✅ Add Composer 1 details (4x faster, MoE architecture)
- ✅ Add DeepSeek R1/V3 (free tier, US servers)
- ✅ Update pricing transition notes (request-based pricing in late 2025)

---

### Gemini CLI

**Current State (README):**
- Largest Context: 1M
- Best Model: Gemini 3 Pro Preview

**Research Findings:**
- ✅ Gemini 3 Pro Preview: 1M context, 64K output (Nov 2025)
- ✅ Gemini 3 Flash Preview: 1M context, 64K output (Dec 2025)
- ✅ Gemini 2.5 Pro/Flash: 1M context, 64K output (stable)
- ⚠️ Gemini 2.0 Flash DEPRECATED (March 31, 2026)
- ✅ All current models: 1,048,576 tokens exactly
- ✅ 8x output increase (64K vs 8K for 2.0 models)

**Recommendation:** No changes needed to README context window table.

**Detailed Report Updates Needed:**
- ✅ Add Gemini 3 Pro Preview (Nov 2025)
- ✅ Add Gemini 3 Flash Preview (Dec 2025)
- ✅ Update max output tokens (64K for 2.5/3.x models)
- ✅ Add deprecation notice for Gemini 2.0 (March 31, 2026)
- ✅ Clarify exact token counts (1,048,576 not "1M")

---

## Detailed Feature Changes

### Claude Code - New Features (2026)

**Context from Research:**

1. **Agent Teams (Experimental):**
   - Multi-agent collaboration system
   - Requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`
   - Team lead delegates to specialist background agents
   - Token-intensive feature

2. **Hooks System - 9+ Types:**
   - PreToolUse, PostToolUse, PostToolUseFailure
   - Notification, PermissionRequest, UserPromptSubmit
   - Stop, SubagentStop/TaskStopHook, TaskCompleted
   - Bash command hooks and Prompt-based hooks

3. **Chrome Integration (Beta):**
   - Claude in Chrome beta (v2.1.0, Jan 7, 2026)
   - Browser-based interactions

4. **Skills Hot-Reload:**
   - Hot-reloading as of v2.1.0
   - Skills can fetch live data (GitHub CLI integration)

5. **Session Teleportation:**
   - `/teleport` command (v2.1.0)
   - Efficiently restores context from session files

6. **Enhanced IDE Support:**
   - JetBrains Plugin (Beta) - available on marketplace
   - VS Code extension with graphical interface

---

### Codex CLI - New Features (2026)

**Context from Research:**

1. **GitHub Integration (Public Preview):**
   - Released Feb 4, 2026
   - Integration with gh CLI
   - Pull request reviews, issue triage

2. **GPT-5.3-Codex Support (Feb 2026):**
   - Mid-turn steering capabilities
   - 25% faster than predecessors
   - State-of-the-art performance with fewer tokens

3. **Steer Mode (Jan 2026):**
   - Now stable and default
   - Enter sends immediately, Tab queues follow-up

4. **Multi-platform IDE Support:**
   - VS Code, JetBrains (v2025.3+), Cursor, Windsurf
   - Visual Studio, Xcode, Eclipse (GPT-5.2-Codex, Jan 26, 2026)

5. **Hooks - Limited Support:**
   - Notification hooks only
   - Full hooks system under discussion (GitHub Issue #2150)

6. **Cost Tracking - Partial:**
   - `/status` shows token usage
   - No comprehensive built-in analytics
   - Third-party: `ccusage` package available

---

### Cursor - New Features (2026)

**Context from Research:**

1. **40x Faster Hooks (Jan 2026):**
   - Major performance improvement
   - Full lifecycle control via custom scripts
   - 20+ hook events

2. **Sub-agents (Jan 22, 2026):**
   - Built-in: Explore, Bash, Browser
   - Custom agents: `.cursor/agents/`
   - Foreground (blocking) / Background (async)

3. **Memories (Feb 3, 2026):**
   - AI remembers conversation facts
   - Background agent workflow adaptation
   - Persistent context across sessions

4. **Image Generation (Jan 22, 2026):**
   - Google Nano Banana Pro integration
   - Full image generation support

5. **Enterprise Features (Dec 2025 - Jan 2026):**
   - Conversation Insights (Dec 18, 2025)
   - Transcript Sharing (Dec 18, 2025)
   - Billing Groups (Dec 18, 2025)
   - Linux Sandboxing (Dec 18, 2025)
   - Service Accounts (Dec 18, 2025)
   - Cursor Blame (Jan 22, 2026) - AI attribution

6. **Skills System (Jan 22, 2026):**
   - `SKILL.md` files for dynamic context discovery
   - `/rules` command (Jan 8, 2026)
   - Migration from `.cursorrules` to `.cursor/rules/*.mdc`

---

### Gemini CLI - New Features (2026)

**Context from Research:**

1. **FastMCP Integration (v2.12.3, Jan 2026):**
   - Seamless installation: `fastmcp install gemini-cli`
   - Python's leading MCP library
   - Official Google MCP endpoints

2. **A2A Protocol (Experimental):**
   - Agent-to-Agent protocol for remote sub-agents
   - AgentRegistry for centralized tracking
   - YOLO mode (use with caution)

3. **10 Lifecycle Hooks:**
   - SessionStart/End, BeforeAgent/AfterAgent
   - BeforeModel/AfterModel, BeforeToolSelection
   - BeforeTool/AfterTool, PreCompress
   - Security: fingerprinting alerts for changed commands

4. **Google Search Grounding:**
   - ~40% reduction in hallucinations
   - Automatic activation based on prediction score
   - Citation inclusion with sources
   - Free tier included with Google account

5. **GitHub Actions (Beta):**
   - Automated issue triage and labeling
   - Pull request reviews
   - gh CLI integration
   - Generous free quotas

6. **Google Cloud Monitoring (2026):**
   - Pre-configured dashboards for telemetry
   - Monthly/daily active users tracking
   - Token consumption monitoring
   - Instant visibility into adoption patterns

7. **Security Hardening (2026):**
   - Default untrusted folders
   - Granular shell command allowlisting
   - Hooks fingerprinting alerts

---

## README.md Diffs

### Context Window Table Diff

```diff
 | Tool | Largest Context | Best Model | Input $/M | Output $/M | Source |
 |------|-----------------|------------|-----------|------------|--------|
-| Claude Code | 1M (beta) | Opus 4.6 with `--betas context-1m-2025-08-07` | $5.00 | $25.00 | [Anthropic Models](https://docs.anthropic.com/en/docs/about-claude/models) |
-| Codex CLI | 400k+ | GPT-5.3-Codex (context compaction) | TBD* | TBD* | [OpenAI Models](https://platform.openai.com/docs/models) |
-| Cursor | 2M (Max mode) | Grok 4 | $3.00** | $15.00** | [Cursor Models](https://cursor.com/docs/models) |
-| Gemini CLI | 1M | Gemini 3 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |
+| Claude Code | 1M (beta) | Opus 4.6 with `context-1m-2025-08-07` beta | $5.00 | $25.00 | [Anthropic Models](https://docs.anthropic.com/en/docs/about-claude/models) |
+| Codex CLI | 400k | GPT-5.3-Codex (Feb 2026) | TBD* | TBD* | [OpenAI Models](https://platform.openai.com/docs/models) |
+| Cursor | 2M (native) | Gemini 3 Pro (200k/1M/2M modes) | $2.00** | $12.00** | [Cursor Models](https://cursor.com/docs/models) |
+| Gemini CLI | 1M | Gemini 3 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |

-> \* GPT-5.3-Codex pricing not yet published by OpenAI (predecessor GPT-5.2-Codex: $1.75/$14.00)
+> \* GPT-5.3-Codex pricing not yet published by OpenAI (Feb 2026 release)
 > \*\* Cursor uses subscription pricing ($20/mo Pro); API prices shown are for the underlying Grok 4 model via xAI
```

### Feature Comparison Table Diff

```diff
 | Feature | Claude Code | Codex CLI | Gemini CLI | Cursor |
 |---------|:-----------:|:---------:|:----------:|:------:|
-| **Hooks** | ✅ | ⚠️ | ✅ | ✅ |
-| **Plugins/MCP** | ✅ | ✅ | ✅ | ✅ |
-| **Sub-agents** | ✅ | ✅ | ✅ | ✅ |
+| **Hooks** | ✅ 9+ types | ⚠️ Limited | ✅ 10 events | ✅ 40x faster |
+| **Plugins/MCP** | ✅ Full | ✅ Full | ✅ FastMCP | ✅ Full |
+| **Sub-agents** | ✅ Teams (exp) | ✅ Beta | ✅ A2A (exp) | ✅ Custom |
 | **Slash Commands** | ✅ | ✅ | ✅ | ✅ |
-| **Custom Commands** | ✅ | ✅ | ✅ | ✅ |
-| **IDE Integration** | ✅ | ✅ | ✅ | ✅ |
-| **Git Integration** | ✅ | ✅ | ✅ | ✅ |
-| **Web Search** | ✅ | ✅ | ✅ | ✅ |
-| **Image Support** | ✅ | ✅ | ✅ | ⚠️ |
-| **Memory/Persistence** | ✅ | ✅ | ✅ | ⚠️ |
-| **Multi-file Editing** | ✅ | ✅ | ✅ | ✅ |
-| **Auto-commit** | ⚠️ | ⚠️ | ✅ | ✅ |
-| **Custom System Prompts** | ✅ | ✅ | ✅ | ✅ |
-| **Cost Tracking** | ✅ | ❌ | ✅ | ⚠️ |
-| **Sandbox Mode** | ✅ | ✅ | ✅ | ⚠️ |
+| **Custom Commands** | ✅ Skills | ✅ AGENTS.md | ✅ GEMINI.md | ✅ Rules |
+| **IDE Integration** | ✅ VS/JetBrains | ✅ Multi-platform | ✅ VS Code | ✅ Native |
+| **Git Integration** | ✅ Hub (beta) | ✅ GitHub (preview) | ✅ Actions (beta) | ✅ Blame (ent) |
+| **Web Search** | ✅ US only | ✅ Built-in | ✅ Grounding | ✅ @Web |
+| **Image Support** | ✅ Full | ✅ Full | ✅ Full | ✅ Full |
+| **Memory/Persistence** | ✅ Session | ✅ Thread | ✅ Project | ✅ Memories |
+| **Multi-file Editing** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Composer |
+| **Auto-commit** | ⚠️ Via hooks | ⚠️ Manual | ✅ Native | ✅ Native |
+| **Custom System Prompts** | ✅ Settings | ✅ AGENTS.md | ✅ GEMINI.md | ✅ Rules |
+| **Cost Tracking** | ✅ Dashboard | ⚠️ /status | ✅ /stats | ⚠️ Enterprise |
+| **Sandbox Mode** | ✅ Native | ✅ OS-enforced | ✅ Container | ✅ Linux (ent) |
```

---

## reports/context-comparison.md Changes Needed

### Claude Code Section

**Add to Primary Models Table:**
```markdown
| Opus 4.6 | 200k (1M beta) | 128k | $5.00 | $25.00 | Latest model (Feb 5, 2026), adaptive thinking, first Opus with 1M context |
```

**Update Knowledge Cutoffs:**
```markdown
- Opus 4.6: May 2025 (reliable) / Aug 2025 (training data)
- Sonnet 4.5: Jan 2025 (reliable) / Jul 2025 (training data)
- Haiku 4.5: Feb 2025 (reliable) / Jul 2025 (training data)
```

**Add Context Awareness Feature:**
```markdown
- **Context awareness**: Sonnet 4.5 and Haiku 4.5 track remaining context window throughout conversation
- System provides token usage warnings: `Token usage: 35000/200000; 165000 remaining`
```

**Clarify 1M Context Availability:**
```markdown
- 1M context available for Opus 4.6 API and Claude Code pay-as-you-go users
- Pro, Max, Teams, and Enterprise subscription users do NOT have access to Opus 4.6 1M context at launch
- Available via `context-1m-2025-08-07` beta header
- Premium pricing: 2x input, 1.5x output for requests exceeding 200K tokens
```

---

### Codex CLI Section

**Update Primary Models Table:**
```markdown
| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| gpt-5.3-codex | 400,000 tokens | - | TBD | TBD | Latest (Feb 2026), 25% faster, new default |
| gpt-5.2-codex | 400,000 tokens | - | $1.75 | $14.00 | Stable |
| gpt-5.1-codex-mini | 400,000 tokens | 128,000 tokens | - | - | Cost-effective version |
```

**Add Reasoning Models:**
```markdown
| o3 | 200,000 tokens | - | Latest | New reasoning model for complex tasks |
| o4-mini | 200,000 tokens | - | Latest | Fast, cost-efficient reasoning |
| codex-mini-latest | 200,000 tokens | 100,000 tokens | Stable | Fine-tuned o4-mini for Codex CLI |
```

**Update Legacy Models:**
```markdown
| GPT-4.1 | 1,000,000 tokens | - | Stable | Up to 1M token context |
```

**Update Deprecation Timeline:**
```markdown
- **o1-preview, o1-mini**: Deprecated April 28, 2025
- **chatgpt-4o-latest**: Deprecated Nov 18, 2025; API removal Feb 17, 2026
- **GPT-4o, GPT-4.1, GPT-4.1 mini, o4-mini**: Retired from ChatGPT Feb 13, 2026 (API access continues)
```

---

### Cursor Section

**Add Claude Models:**
```markdown
| Claude 4.6 Opus | 200k (1M max) | 64k | $5.00 | $25.00 | Latest (Feb 5, 2026), deep reasoning |
```

**Add OpenAI Models:**
```markdown
| GPT-5.3 Codex | 272k | - | - | - | Latest (Feb 5, 2026), 77.3% Terminal-Bench |
```

**Update Gemini Models:**
```markdown
| Model | Context Window | Max Mode | Native | Notes |
|-------|---------------|----------|--------|-------|
| Gemini 3 Pro | 200k | 1M | 2M | Visual reasoning leader |
```

**Update Grok Models:**
```markdown
| Grok 4 Code | 131k-2M | Varies by variant, multimodal |
```

**Add Composer Details:**
```markdown
| Composer 1 | 200k | 250 tok/sec (4x faster) | $1.25/M in, $10/M out |
- MoE architecture, RL-trained on real engineering tasks
- Completes most turns in <30 seconds
```

**Add DeepSeek Models:**
```markdown
| DeepSeek R1 | Standard | Free tier, US servers (Fireworks.ai) |
| DeepSeek V3 | Standard | Free tier, US servers |
```

---

### Gemini CLI Section

**Update Current Models:**
```markdown
| Gemini 3 Pro Preview | 1,048,576 (1M) | 65,536 (64K) | Preview | Released November 2025 |
| Gemini 3 Flash Preview | 1,048,576 (1M) | 65,536 (64K) | Preview | Released December 2025 |
| Gemini 2.5 Pro | 1,048,576 (1M) | 65,536 (64K) | Stable | Released June 2025 |
| Gemini 2.5 Flash | 1,048,576 (1M) | 65,536 (64K) | Stable | Released June 2025 |
```

**Add Deprecation Notice:**
```markdown
| Gemini 2.0 Flash | 1,048,576 (1M) | 8,192 (8K) | March 31, 2026 |
| Gemini 2.0 Flash-Lite | 1,048,576 (1M) | 8,192 (8K) | March 31, 2026 |
```

**Highlight Output Token Increase:**
```markdown
- **Enhanced Output**: Gemini 2.5 and 3.x models significantly increased max output from 8K to 64K tokens (8x improvement)
```

---

## Next Steps

**User Approval Required:**

1. Review proposed changes to README.md context window table
2. Review proposed changes to README.md feature comparison table
3. Review proposed changes to reports/context-comparison.md
4. Approve updates or request modifications

**After Approval:**

1. Update README.md with new tables
2. Update reports/context-comparison.md with detailed model information
3. Update "Last Updated" timestamp to 2026-02-09
4. Commit changes with summary message

---

## Change Summary

**Total Changes:** 4 tools updated

**High Priority:**
- Claude Code: Opus 4.6 released (Feb 5, 2026) with 1M context and 128K output
- Codex CLI: GPT-5.3-Codex now default model (Feb 2026)
- Cursor: Multi-model updates, 40x faster hooks, Memories feature

**Medium Priority:**
- Gemini CLI: Gemini 3 models in preview, FastMCP integration, A2A protocol

**Feature Highlights:**
- Claude Code: Agent Teams (experimental), Chrome beta, Skills hot-reload
- Codex CLI: GitHub integration preview (Feb 4, 2026), multi-platform IDE support
- Cursor: 40x faster hooks (Jan 2026), Memories (Feb 3, 2026), Image generation
- Gemini CLI: 10 lifecycle hooks, FastMCP v2.12.3, Google Search grounding

**Deprecations:**
- Gemini 2.0 Flash models shutdown March 31, 2026
- Codex CLI: o1-preview/o1-mini deprecated April 28, 2025

---

**Ready for User Review and Approval**
