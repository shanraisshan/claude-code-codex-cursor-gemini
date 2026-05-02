# Context Window Comparison Report

> **Last Updated:** 2026-05-02

## Claude Code

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| Opus 4.7 | 1M (GA) | 128k | $5.00 | $25.00 | Latest flagship (Apr 16, 2026), 1M GA, adaptive thinking, new tokenizer (~555k words/1M) |
| Opus 4.6 | 1M (GA) | 128k | $5.00 | $25.00 | Released Feb 5, 2026; 1M GA since Mar 13, 2026; adaptive thinking |
| Sonnet 4.6 | 1M (GA) | 64k | $3.00 | $15.00 | 1M GA since Mar 13, 2026; default for Pro/Enterprise/API plans |
| Sonnet 4.5 | 200k | 64k | $3.00 | $15.00 | Legacy (active); no 1M context |
| Haiku 4.5 | 200k | 64k | $1.00 | $5.00 | Fastest; no 1M context support; no adaptive thinking |
| Opus 4.5 | 200k | 64k | $5.00 | $25.00 | Legacy (active) |
| Opus 4.1 | 200k | 32k | $5.00 | $25.00 | Legacy (active) |

**Reference:** [Anthropic Models](https://platform.claude.com/docs/en/about-claude/models/overview)

### Model Selection

- During session: `/model <alias>`
- At startup: `claude --model <alias>`
- Environment: `ANTHROPIC_MODEL=<alias>`
- Aliases: `opus` / `best` (→ Opus 4.7), `sonnet` (→ Sonnet 4.6), `haiku` (→ Haiku 4.5), `opusplan`
- Explicit 1M variants: `opus[1m]`, `sonnet[1m]`
- Bedrock/Vertex/Foundry: `opus` resolves to Opus 4.6, `sonnet` resolves to Sonnet 4.5
- Disable 1M: `CLAUDE_CODE_DISABLE_1M_CONTEXT=1`

### Key Features

- **1M context is GA** (no longer beta) for Opus 4.7, Opus 4.6, and Sonnet 4.6 as of March 13, 2026
- **300k output tokens (Beta)** on Message Batches API for Opus 4.7 / Opus 4.6 / Sonnet 4.6 via `output-300k-2026-03-24` header
- **Adaptive thinking**: Opus 4.7, Opus 4.6, Sonnet 4.6 — dynamically allocates reasoning per step
- **Effort levels**: Opus 4.7 supports `low`, `medium`, `high`, `xhigh`, `max`; Opus 4.6 / Sonnet 4.6 support `low`, `medium`, `high`, `max`
- `opusplan` uses standard 200k context during plan phase (no automatic 1M upgrade)

### Plan-Level 1M Context Availability

| Plan | Opus 1M | Sonnet 1M |
|------|---------|-----------|
| Max, Team, Enterprise | Included with subscription | Requires extra usage |
| Pro | Requires extra usage | Requires extra usage |
| API / pay-as-you-go | Full access | Full access |

### Deprecations and Retirements

| Model | Status | Deprecated | Retirement | Replacement |
|-------|--------|------------|------------|-------------|
| `claude-opus-4-20250514` | Deprecated | Apr 14, 2026 | Jun 15, 2026 | `claude-opus-4-7` |
| `claude-sonnet-4-20250514` | Deprecated | Apr 14, 2026 | Jun 15, 2026 | `claude-sonnet-4-6` |
| `claude-3-haiku-20240307` | Retired | Feb 19, 2026 | Apr 20, 2026 | `claude-haiku-4-5` |
| `claude-3-5-haiku-20241022` | Retired | Dec 19, 2025 | Feb 19, 2026 | `claude-haiku-4-5` |
| `claude-3-7-sonnet-20250219` | Retired | Oct 28, 2025 | Feb 19, 2026 | `claude-sonnet-4-6` |
| `claude-3-5-sonnet-*` | Retired | Aug 13, 2025 | Oct 28, 2025 | `claude-sonnet-4-6` |
| `claude-3-opus-20240229` | Retired | Jun 30, 2025 | Jan 5, 2026 | `claude-opus-4-7` |

> **Note:** The entire Claude 3.x generation (Opus 3, Sonnet 3.5, Haiku 3, Haiku 3.5) is fully retired as of 2026.

---

## Codex CLI

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| gpt-5.5 | 1.05M (API) / ~400k (Codex) | 128k | TBD | TBD | Latest frontier (Apr 23, 2026); Codex caps at 400k; known issue #19319 may reduce effective ctx to ~258k |
| gpt-5.4 | 1.05M | 128k | $2.50 (doubles >272k) | TBD | Flagship; experimental 1M in Codex via `model_context_window` config |
| gpt-5.4-mini | 400k | 128k | TBD | TBD | Default mini model |
| gpt-5.3-codex | 400k | 128k | TBD | TBD | Default coding model (Feb 2026) |
| gpt-5.3-codex-spark | 128k | N/A | N/A | N/A | Research preview; ChatGPT Pro only; >1,000 tokens/sec |
| gpt-5.2 | 400k | 128k | $2.00 | $8.00 | Previous frontier; still supported |
| gpt-5-codex | 400k | 128k | $1.25 | $10.00 | **DEPRECATED** — retires Jul 23, 2026 |
| gpt-5.1-codex | 400k | 128k | $1.25 | $10.00 | **DEPRECATED** — retires Jul 23, 2026 |
| gpt-5.2-codex | 400k | 128k | $1.75 | $14.00 | **DEPRECATED** — retires Jul 23, 2026 |
| codex-mini-latest | 200k | — | — | — | **RETIRED** Feb 12, 2026 |
| o4-mini | 200k | — | $1.10 | $4.40 | **DEPRECATED** — shutdown Oct 23, 2026 |
| o3-mini | 200k | — | — | — | **RETIRED** Feb 23, 2026 |
| o3 | 200k | — | — | — | **DEPRECATED** |

**Reference:** [Codex Models](https://developers.openai.com/codex/models)

### Key Features

- **Auto-compaction** triggers at 95% of `model_context_window` by default; in CLI v0.100.0+ user-defined limit is silently clamped to 90%
- **Server-side compaction** via OpenAI Responses API; emits `compaction` output item in stream
- After compaction, Codex re-reads up to 5 recently edited files (50k token budget, 5k per file)
- Configurable via `model_auto_compact_token_limit` in `config.toml`
- ChatGPT account sign-in (no manual API key needed)
- Standalone `/responses/compact` endpoint available for stateless compaction

### Configuration Example

```toml
model = "gpt-5.5"
model_context_window = 400000
model_auto_compact_token_limit = 350000
tool_output_token_limit = 50000
```

### Deprecation Timeline

| Model | Shutdown Date | Replacement |
|-------|---------------|-------------|
| `codex-mini-latest` | Feb 12, 2026 (retired) | `gpt-5.3-codex` |
| `o3-mini` | Feb 23, 2026 (retired) | `o3` (also deprecated) |
| `gpt-5-codex` | Jul 23, 2026 | `gpt-5.3-codex` |
| `gpt-5.1-codex` | Jul 23, 2026 | `gpt-5.3-codex` |
| `gpt-5.2-codex` | Jul 23, 2026 | `gpt-5.3-codex` |
| `o3-deep-research` | Jul 23, 2026 | `gpt-5.4-pro` |
| `o4-mini` | Oct 23, 2026 | `gpt-5-mini` |

---

## Cursor

### Anthropic Models

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| Claude 4.7 Opus | 200k (1M Max) | 128k | $5.00 | $25.00 | Current flagship Anthropic |
| Claude 4.6 Opus | 200k (1M Max) | 128k | $5.00 | $25.00 | Current; deep reasoning |
| Claude 4.6 Sonnet | 200k (1M Max) | 64k | $3.00 | $15.00 | Current; 1M Max Mode |
| Claude 4.5 Opus | 200k (200k Max) | 64k | $5.00 | $25.00 | Legacy; Max Mode capped at 200k |
| Claude 4.5 Sonnet | 200k (1M Max) | 64k | $3.00 | $15.00 | Legacy (active) |
| Claude 4.5 Haiku | 200k (200k Max) | 64k | $1.00 | $5.00 | Hidden by default |
| Claude 4 Sonnet 1M | 200k (1M Max) | 64k | $3.00 | $15.00 | Hidden; 2x cost over 200k tokens |
| Claude 4 Sonnet | 200k (200k Max) | 64k | $3.00 | $15.00 | Hidden by default |

### OpenAI Models

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| GPT-5.5 | 200k (1M Max) | 128k | TBD | TBD | Newest OpenAI in Cursor |
| GPT-5.4 | 200k (1M Max) | 128k | $2.50 | TBD | Briefly defaulted to Max Mode for legacy billing |
| GPT-5.4 Mini | 200k (1M Max) | 128k | TBD | TBD | Mini variant |
| GPT-5.4 Nano | 200k (1M Max) | 128k | TBD | TBD | Smallest variant |
| GPT-5.3 Codex | 272k (272k Max) | 128k | TBD | TBD | Coding-optimized |
| GPT-5.2 | 272k (272k Max) | 128k | $2.00 | $8.00 | Active |
| GPT-5.2 Codex | 272k (272k Max) | 128k | $1.75 | $14.00 | Active |
| GPT-5.1 Codex | 272k (272k Max) | 128k | $1.25 | $10.00 | Active |
| GPT-5 | 272k (272k Max) | 128k | $1.25 | $10.00 | Active |
| GPT-5 Mini | 200k (200k Max) | 128k | $0.40 | $1.60 | Active |

### Google Models

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| Gemini 3.1 Pro | 200k (1M Max) | 64k | $2.00 | $12.00 | Current Google leader |
| Gemini 3 Pro | 200k (1M Max) | 64k | $2.00 | $12.00 | Current |
| Gemini 3 Pro Image Preview | 200k (1M Max) | 32k | $2.00 | $12.00 | Multimodal preview |
| Gemini 3 Flash | 200k (1M Max) | 64k | $0.50 | $3.00 | Fast inference |
| Gemini 2.5 Flash | 200k (1M Max) | 65k | $0.30 | $2.50 | Legacy (active) |

### xAI Models

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| Grok 4.20 | 200k (2M Max) | — | $3.00 | $15.00 | Primary xAI model; replaces Grok Code |
| Grok Code Fast 1 | 256k | — | $0.60 | $4.00 | Active; may be hidden by default |
| Grok Code (original) | 256k | — | $2.00 | $10.00 | Removed from default list; re-add via custom model ID |

### Cursor Native Models (Composer)

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| Composer 2 | 200k | — | $0.50 (Std) / $1.50 (Fast) | — | Default in Auto mode (Mar 19, 2026); built on Kimi K2.5 base |
| Composer 1.5 | 200k | — | N/A | N/A | Hidden by default; adds Thinking support |
| Composer 1 | 200k | — | N/A | N/A | First-gen; hidden by default |

### Other Providers

| Model | Context Window | Max Output | Input $/M | Output $/M | Notes |
|-------|----------------|------------|-----------|------------|-------|
| Kimi K2.5 (Moonshot) | 200k (1M Max) | — | TBD | TBD | Active |
| DeepSeek V4 Pro | 1M (1M Max) | — | TBD | TBD | Custom model / API key required |
| DeepSeek V4 Flash | 1M (1M Max) | — | TBD | TBD | Custom model / API key required |

> **Note:** Cursor uses subscription pricing (Pro / Business). Composer models have **unlimited access on paid plans** in Auto mode. Third-party models draw from the monthly credit pool. API prices shown are underlying provider rates, not what Cursor users pay directly.

**Reference:** [Cursor Models](https://cursor.com/docs/models)

### Normal vs Max Mode (Major Behavioral Change — Early 2026)

- **200k is now the default context for all models** — previously Claude Sonnet required Max Mode to reach 200k.
- **Max Mode is reserved exclusively for 1M+ context access** (e.g., Gemini 3 Pro at 1M, Grok 4.20 at 2M).
- Max Mode uses token-based pricing (consumes credits faster than request-based).
- Tab Autocomplete (Cursor-small) uses a separate ~8k context model, not configurable.
- Confirmed by Lee Robinson (Cursor): "Max mode is only needed for 1M context windows."

### Key Features

- Dynamic context discovery reduces token usage for MCP tool calls
- Automatic summarization when context window fills
- Cursor 3.2 (Apr 24, 2026) is current — multi-tasking agents, workspaces, background agent tasks

---

## Gemini CLI

| Model | Context Window | Max Output | Input $/M | Output $/M | Status |
|-------|----------------|------------|-----------|------------|--------|
| Gemini 3.1 Pro Preview | 1M | 64k | $2.00 | $12.00 | Current flagship; supersedes `gemini-3-pro-preview` |
| Gemini 3 Flash Preview | 1M | 64k | $0.50 | $3.00 | Available in Gemini CLI since Dec 2025 |
| Gemini 3.1 Flash-Lite Preview | 1M | 64k | TBD | TBD | New (Mar 3, 2026); cost-efficient tier |
| Gemini 3.1 Flash Image Preview | 128k | 32k | TBD | TBD | Image generation preview |
| Gemini 3 Pro Image Preview | 65k | 32k | $2.00 | $12.00 | Multimodal with image generation |
| Gemini 2.5 Pro | 1M | 65k | $1.25 | $10.00 | Stable / Active — guaranteed not before Oct 16, 2026 |
| Gemini 2.5 Flash | 1M | 65k | $0.30 | $2.50 | Stable / Active — guaranteed not before Oct 16, 2026 |
| Gemini 2.5 Flash-Lite | 1M | 65k | $0.10 | $0.40 | Stable / Active |
| Gemini 2.0 Flash | 1M | 8k | $0.10 | $0.40 | **Deprecated** — EOL Jun 1, 2026 |
| Gemini 2.0 Flash-Lite | 1M | 8k | $0.08 | $0.30 | **Deprecated** — EOL Jun 1, 2026 |
| Gemini 3 Pro Preview (original) | 1M | 64k | — | — | **DISCONTINUED** Mar 26, 2026 — redirects to 3.1 |

**Reference:** [Gemini API](https://ai.google.dev/gemini-api/docs/models)

### Gemini CLI Notes

- Gemini CLI **v0.40.1** (Apr 30, 2026) is current stable
- **Intelligent auto-routing**: simple queries → Flash, complex tasks → Pro
- Manual override: `/model` command or `-m` flag (e.g., `gemini -m gemini-2.5-flash`)
- **Gemma 4** experimental local-inference support added in v0.41.0-preview builds

### Deprecation Timeline

| Model | Shutdown Date |
|-------|---------------|
| `gemini-3-pro-preview` (original) | March 26, 2026 (discontinued) |
| `gemini-2.5-flash-lite-preview-09-2025` | March 31, 2026 (discontinued) |
| `gemini-robotics-er-1.5-preview` | April 30, 2026 (shut down) |
| Gemini 2.0 Flash | June 1, 2026 (EOL) |
| Gemini 2.0 Flash-Lite | June 1, 2026 (EOL) |
| Gemini 2.5 Pro | Not before October 16, 2026 |
| Gemini 2.5 Flash | Not before October 16, 2026 |

### Retired Models

| Model | Context Window | Retirement Date |
|-------|----------------|-----------------|
| `text-embedding-004` | — | January 14, 2026 |
| Gemini 1.5 Pro | 2M | Sept 24, 2025 |
| Gemini 1.5 Flash | 1M | Sept 24, 2025 |

> **Note:** The 2M token context window is no longer available in any active Gemini model. Maximum context is now 1M tokens for all current-gen Gemini Pro and Flash models.

---

## Research Sources

### Claude Code
- [Anthropic Models Overview](https://platform.claude.com/docs/en/about-claude/models/overview)
- [Model Deprecations](https://platform.claude.com/docs/en/docs/resources/model-deprecations)
- [Claude Code Model Configuration](https://code.claude.com/docs/en/model-config)
- [What's New in Claude Opus 4.7](https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-7)

### Codex CLI
- [Codex Models](https://developers.openai.com/codex/models)
- [Codex CLI Features](https://developers.openai.com/codex/cli/features)
- [Codex CLI Configuration Reference](https://developers.openai.com/codex/config-reference)
- [Codex Changelog](https://developers.openai.com/codex/changelog)
- [OpenAI Deprecations](https://developers.openai.com/api/docs/deprecations)

### Cursor
- [Cursor Models Documentation](https://cursor.com/docs/models)
- [Cursor Max Mode Documentation](https://cursor.com/docs/context/max-mode)
- [Cursor Changelog](https://cursor.com/changelog)
- [Grok 4.20 in Cursor](https://cursor.com/docs/models/grok-4-20)

### Gemini CLI
- [Gemini API Models](https://ai.google.dev/gemini-api/docs/models)
- [Gemini 3 Developer Guide](https://ai.google.dev/gemini-api/docs/gemini-3)
- [Gemini Deprecations](https://ai.google.dev/gemini-api/docs/deprecations)
- [Gemini CLI GitHub](https://github.com/google-gemini/gemini-cli)
