# Context Window Research Session

**Started:** 2026-05-02 14:38:59
**Status:** In Progress

---

## Claude Code Research
**Agent:** Dr. Sarah Chen
**Status:** Complete

### Context Windows

#### Current Models (Active as of 2026-05-02)

| Model | API ID | Context Window | Max Output | Status |
|-------|--------|---------------|------------|--------|
| Claude Opus 4.7 | `claude-opus-4-7` | 1M tokens | 128k tokens | Current |
| Claude Opus 4.6 | `claude-opus-4-6` | 1M tokens | 128k tokens | Legacy (active) |
| Claude Opus 4.5 | `claude-opus-4-5-20251101` | 200k tokens | 64k tokens | Legacy (active) |
| Claude Opus 4.1 | `claude-opus-4-1-20250805` | 200k tokens | 32k tokens | Legacy (active) |
| Claude Sonnet 4.6 | `claude-sonnet-4-6` | 1M tokens | 64k tokens | Current |
| Claude Sonnet 4.5 | `claude-sonnet-4-5-20250929` | 200k tokens | 64k tokens | Legacy (active) |
| Claude Haiku 4.5 | `claude-haiku-4-5-20251001` | 200k tokens | 64k tokens | Current |
| Claude Sonnet 4 | `claude-sonnet-4-20250514` | 200k tokens | 64k tokens | Deprecated |
| Claude Opus 4 | `claude-opus-4-20250514` | 200k tokens | 32k tokens | Deprecated |

#### Claude Code Model Aliases (via `/model` picker)

| Alias | Resolves To (Anthropic API) | Context Window |
|-------|-----------------------------|---------------|
| `opus` / `best` | Claude Opus 4.7 | 1M tokens |
| `sonnet` | Claude Sonnet 4.6 | 1M tokens |
| `haiku` | Claude Haiku 4.5 | 200k tokens |
| `opus[1m]` | Claude Opus 4.7 with 1M context | 1M tokens |
| `sonnet[1m]` | Claude Sonnet 4.6 with 1M context | 1M tokens |
| `opusplan` | Opus (plan mode) + Sonnet (execution) | 200k (plan phase) |

Note: On Bedrock/Vertex/Foundry, `opus` resolves to Opus 4.6 and `sonnet` resolves to Sonnet 4.5. Newer models require explicit model name or environment variable override.

#### Extended Context (1M Token) — Generally Available

The 1M token context window is no longer a beta feature. As of March 13, 2026, Anthropic made the 1M context window generally available for Claude Opus 4.6 and Claude Sonnet 4.6. Claude Opus 4.7 (released April 16, 2026) ships with 1M context by default.

- **Opus 4.7**: 1M context at standard pricing ($5/MTok input, $25/MTok output), no long-context premium
- **Opus 4.6**: 1M context at standard pricing ($5/MTok input, $25/MTok output)
- **Sonnet 4.6**: 1M context at standard pricing ($3/MTok input, $15/MTok output)
- **Haiku 4.5**: 200k context only — no 1M support

Claude Code plan-level availability for 1M context:

| Plan | Opus 1M | Sonnet 1M |
|------|---------|-----------|
| Max, Team, Enterprise | Included with subscription | Requires extra usage |
| Pro | Requires extra usage | Requires extra usage |
| API / pay-as-you-go | Full access | Full access |

`opusplan` mode uses the standard 200k context during the plan phase; the automatic 1M upgrade does not apply to plan-mode sessions.

To disable 1M context: set `CLAUDE_CODE_DISABLE_1M_CONTEXT=1`.

#### Extended Output (300k tokens) — Beta

On the Message Batches API, Opus 4.7, Opus 4.6, and Sonnet 4.6 support up to **300k output tokens** using the `output-300k-2026-03-24` beta header. This does not apply to the synchronous Messages API, where max output remains at the values in the table above.

#### New Model Features (Claude 4.x Generation)

- **Adaptive thinking**: Opus 4.7, Opus 4.6, Sonnet 4.6 — dynamically allocates reasoning per step
- **Extended thinking**: Sonnet 4.6, Haiku 4.5, and all legacy Opus/Sonnet 4.x models
- **Effort levels**: Opus 4.7 supports `low`, `medium`, `high`, `xhigh`, `max`; Opus 4.6 and Sonnet 4.6 support `low`, `medium`, `high`, `max`
- **Claude Mythos Preview**: Invitation-only research preview for defensive cybersecurity (Project Glasswing); 1M context window; not available via standard API

#### New Model Family Since Claude 4.x (Notable Additions)

- **Claude Opus 4.7** (released April 16, 2026): Largest context window (1M), 128k max output, step-change improvement in agentic coding. Uses a new tokenizer (~555k words per 1M tokens vs ~750k for Sonnet 4.6). Most capable generally available model.
- **Claude Opus 4.6** (released February 5, 2026): 1M context, 128k output, adaptive thinking.
- **Claude Mythos Preview** (access via Project Glasswing only): 1M context, specialized for cybersecurity workflows.

#### Deprecations and Retirements

| Model | Status | Deprecated | Retirement Date | Replacement |
|-------|--------|------------|-----------------|-------------|
| `claude-opus-4-20250514` | Deprecated | April 14, 2026 | June 15, 2026 | `claude-opus-4-7` |
| `claude-sonnet-4-20250514` | Deprecated | April 14, 2026 | June 15, 2026 | `claude-sonnet-4-6` |
| `claude-3-haiku-20240307` | Retired | Feb 19, 2026 | April 20, 2026 | `claude-haiku-4-5` |
| `claude-3-5-haiku-20241022` | Retired | Dec 19, 2025 | Feb 19, 2026 | `claude-haiku-4-5` |
| `claude-3-7-sonnet-20250219` | Retired | Oct 28, 2025 | Feb 19, 2026 | `claude-sonnet-4-6` |
| `claude-3-5-sonnet-*` | Retired | Aug 13, 2025 | Oct 28, 2025 | `claude-sonnet-4-6` |
| `claude-3-opus-20240229` | Retired | Jun 30, 2025 | Jan 5, 2026 | `claude-opus-4-7` |

The entire Claude 3.x generation (Opus 3, Sonnet 3.5, Haiku 3, Haiku 3.5) is now fully retired as of 2026.

#### Sources

- [Models Overview — Anthropic Docs](https://platform.claude.com/docs/en/about-claude/models/overview)
- [Model Deprecations — Anthropic Docs](https://platform.claude.com/docs/en/docs/resources/model-deprecations)
- [Claude Code Model Configuration](https://code.claude.com/docs/en/model-config)
- [Introducing Claude Opus 4.6 — Anthropic Blog](https://www.anthropic.com/news/claude-opus-4-6)
- [What's New in Claude Opus 4.7 — Anthropic Docs](https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-7)

---

## Codex CLI Research
**Agent:** Marcus Thompson
**Status:** Complete

### Context Windows

#### Current Models (Active as of 2026-05-02)

| Model | Context Window | Max Output | Status |
|-------|---------------|------------|--------|
| `gpt-5.5` | 1,050,000 tokens (API); ~400,000 tokens (Codex) | 128,000 tokens | Current — newest frontier model (released Apr 23, 2026) |
| `gpt-5.4` | 1,050,000 tokens | 128,000 tokens | Current — flagship model |
| `gpt-5.4-mini` | 400,000 tokens | 128,000 tokens | Current — default mini model |
| `gpt-5.3-codex` | 400,000 tokens | 128,000 tokens | Current — default coding model |
| `gpt-5.3-codex-spark` | 128,000 tokens | Not specified (text-only) | Research preview (ChatGPT Pro only) |
| `gpt-5.2` | 400,000 tokens | 128,000 tokens | Current — previous frontier, still supported |
| `gpt-5-codex` | 400,000 tokens | 128,000 tokens | Deprecated (retirement Jul 23, 2026) |
| `codex-mini-latest` | 200,000 tokens | — | Retired (shutdown Feb 12, 2026) |
| `o4-mini` | 200,000 tokens | — | Deprecated (shutdown Oct 23, 2026) |
| `o3` / `o3-mini` | 200,000 tokens | — | Deprecated (`o3-mini` shutdown Feb 23, 2026) |
| `codex-1` | 192,000 tokens | — | No longer in official docs; superseded by gpt-5-codex family |

**Note on gpt-5.5 Codex vs. API context window:** GPT-5.5 ships with a 1,050,000-token context window in the OpenAI API, but Codex enforces a 400,000-token hard cap for Codex sessions. An active GitHub issue (#19319) further reports that Codex internally encodes only 272,000 tokens as GPT-5.5's window (the input portion of a 272k input + 128k output split), and then applies a 95% auto-compaction threshold — yielding approximately 258,400 effective usable tokens. This discrepancy is under active investigation.

**Note on gpt-5.4 in Codex:** GPT-5.4 supports experimental 1M context in Codex for users who manually configure `model_context_window`. Beyond the default 272,000-token threshold, input pricing doubles from $2.50 to $5.00 per MTok.

#### Codex CLI Model Access by Tier

| Model | Codex CLI & SDK | App & IDE Extension | Cloud | API Access |
|-------|----------------|--------------------|----|---|
| `gpt-5.5` | Yes | Yes | Yes | Yes |
| `gpt-5.4` | Yes | Yes | Yes | Yes |
| `gpt-5.4-mini` | Yes | Yes | Yes | Yes |
| `gpt-5.3-codex` | Yes | Yes | Yes | Yes |
| `gpt-5.3-codex-spark` | No | Yes (ChatGPT Pro only) | No | No |
| `gpt-5.2` | Yes | Yes | Yes | Yes |

#### Context Compaction / Auto-Compact

Codex CLI implements automatic context compaction to prevent fatal context-overflow errors in long sessions. Key details:

- **Trigger:** Compaction fires when conversation history crosses `model_auto_compact_token_limit` (configurable in `config.toml`). When unset, the default threshold is approximately 95% of the model's context window.
- **Mechanism:** Server-side compaction via the OpenAI Responses API. When the rendered token count crosses the threshold, the server runs a compaction pass, emits a `compaction` output item in the stream, and prunes history before continuing inference. Developers can also call the standalone `/responses/compact` endpoint explicitly for stateless compaction in long-running workflows.
- **Post-compaction behavior:** After compaction, Codex injects a lead-in message and automatically re-reads up to 5 recently edited files, with a total budget of 50,000 tokens (5,000 tokens per file).
- **Silent clamp (v0.100.0+):** Any user-defined `model_auto_compact_token_limit` is silently clamped to 90% of `model_context_window`. Explicit values above this ceiling are overridden without warning.
- **GPT-5.1-Codex-Max (historical):** An earlier model announced as natively trained to operate across multiple context windows via compaction — designed for coherent work over millions of tokens within a single task. The `gpt-5.1-codex` snapshot is scheduled for retirement July 23, 2026.
- **Auto 1M context mode (pending):** GitHub issue #13913 proposes an "Auto 1M context mode" for supported models to balance speed/cost against large-context reliability. This feature has not shipped as of 2026-05-02.

Configuration options in `config.toml`:

```toml
model = "gpt-5.5"
model_context_window = 400000           # override the model's context window
model_auto_compact_token_limit = 350000 # trigger compaction before this limit
tool_output_token_limit = 50000         # per-tool-call output token budget
```

Note: `model_auto_compact_token_limit` is clamped to 90% of `model_context_window` in CLI v0.100.0+.

#### Deprecations and Retirements

| Model | Shutdown Date | Replacement |
|-------|--------------|-------------|
| `codex-mini-latest` | February 12, 2026 (retired) | `gpt-5-codex-mini` or `gpt-5.3-codex` |
| `o3-mini` / `o3-mini-2025-01-31` | February 23, 2026 (retired) | `o3` |
| `gpt-5-codex` | July 23, 2026 | `gpt-5.3-codex` |
| `gpt-5.1-codex` | July 23, 2026 | `gpt-5.3-codex` |
| `gpt-5.2-codex` | July 23, 2026 | `gpt-5.3-codex` |
| `o4-mini` / `o4-mini-2025-04-16` | October 23, 2026 | `gpt-5-mini` |
| `o3-deep-research` | July 23, 2026 | `gpt-5.4-pro` |
| `--full-auto` CLI flag | Deprecated (no hard date) | Explicit permission profiles |

**Key change:** The legacy o-series models (o3, o4-mini) that previously underpinned Codex CLI are being retired throughout 2026 as the GPT-5.x family takes over. `codex-mini-latest` — the only model that supported the legacy local shell tool — was shut down February 12, 2026.

#### Notable New Models vs. Prior README Baseline

The prior README tracked: `codex-1` (192k), `codex-mini` (200k), `o3` (200k), `o4-mini` (200k).

Changes detected:

- **`codex-1`**: Not present in current official Codex documentation. Superseded by the gpt-5-codex model family.
- **`codex-mini` / `codex-mini-latest`**: Retired February 12, 2026.
- **`o3`**: `o3-mini` retired February 23, 2026. Base `o3` is deprecated with no confirmed shutdown date yet.
- **`o4-mini`**: Scheduled shutdown October 23, 2026.
- **`gpt-5.5`** (Apr 23, 2026): New default frontier model. 1M API context; Codex-enforced ~400k cap.
- **`gpt-5.4`** (Mar 2026): 1M context; experimental 1M in Codex via manual config.
- **`gpt-5.4-mini`**: 400k context; now the "default" mini designation in OpenAI API docs.
- **`gpt-5.3-codex`** (Feb 2026): Purpose-built coding model; 400k context; marked "Default" coding model.
- **`gpt-5.3-codex-spark`** (Feb 2026): Research preview; 128k context; >1,000 tokens/sec; ChatGPT Pro only.

#### Sources

- [Codex Models — OpenAI Developers](https://developers.openai.com/codex/models)
- [Codex CLI Features — OpenAI Developers](https://developers.openai.com/codex/cli/features)
- [Codex CLI Configuration Reference — OpenAI Developers](https://developers.openai.com/codex/config-reference)
- [Codex Changelog — OpenAI Developers](https://developers.openai.com/codex/changelog)
- [GPT-5.5 Model Specs — OpenAI API Docs](https://developers.openai.com/api/docs/models/gpt-5.5)
- [GPT-5.4 Model Specs — OpenAI API Docs](https://developers.openai.com/api/docs/models/gpt-5.4)
- [GPT-5.4-mini Model Specs — OpenAI API Docs](https://developers.openai.com/api/docs/models/gpt-5.4-mini)
- [GPT-5.3-Codex Model Specs — OpenAI API Docs](https://developers.openai.com/api/docs/models/gpt-5.3-codex)
- [GPT-5-Codex Model Specs — OpenAI API Docs](https://developers.openai.com/api/docs/models/gpt-5-codex)
- [Deprecations — OpenAI API Docs](https://developers.openai.com/api/docs/deprecations)
- [Compaction Guide — OpenAI API Docs](https://developers.openai.com/api/docs/guides/compaction)
- [Introducing GPT-5.5 — OpenAI Blog](https://openai.com/index/introducing-gpt-5-5/)
- [Building more with GPT-5.1-Codex-Max — OpenAI Blog](https://openai.com/index/gpt-5-1-codex-max/)
- [GPT-5.5 context window mismatch issue #19319 — openai/codex GitHub](https://github.com/openai/codex/issues/19319)
- [Support 1M token context for GPT-5.5 issue #19464 — openai/codex GitHub](https://github.com/openai/codex/issues/19464)
- [Auto 1M context mode issue #13913 — openai/codex GitHub](https://github.com/openai/codex/issues/13913)
- [Introducing GPT-5.3-Codex-Spark — OpenAI Blog](https://openai.com/index/introducing-gpt-5-3-codex-spark/)

---

## Cursor Research
**Agent:** Elena Rodriguez
**Status:** Complete

### Context Windows

#### All Supported Models (Active as of 2026-05-02)

| Model | Provider | Normal Context | Max Mode Context | Status |
|-------|----------|---------------|-----------------|--------|
| Claude 4.7 Opus | Anthropic | 200k | 1M | Current |
| Claude 4.6 Opus | Anthropic | 200k | 1M | Current |
| Claude 4.6 Opus (Fast) | Anthropic | 200k | 1M | Limited preview |
| Claude 4.6 Sonnet | Anthropic | 200k | 1M | Current |
| Claude 4.5 Opus | Anthropic | 200k | 200k | Legacy (active) |
| Claude 4.5 Sonnet | Anthropic | 200k | 1M | Legacy (active) |
| Claude 4.5 Haiku | Anthropic | 200k | 200k | Hidden by default |
| Claude 4 Sonnet | Anthropic | 200k | 200k | Hidden by default |
| Claude 4 Sonnet 1M | Anthropic | 200k | 1M | Hidden by default; 2x cost over 200k tokens |
| GPT-5.5 | OpenAI | 200k | 1M | Current |
| GPT-5.4 | OpenAI | 200k | 1M | Current; Max Mode default for legacy billing users |
| GPT-5.4 Mini | OpenAI | 200k | 1M | Current |
| GPT-5.4 Nano | OpenAI | 200k | 1M | Current |
| GPT-5.3 Codex | OpenAI | 272k | 272k | Current |
| GPT-5.2 | OpenAI | 272k | 272k | Active |
| GPT-5.2 Codex | OpenAI | 272k | 272k | Active |
| GPT-5.1 Codex | OpenAI | 272k | 272k | Active |
| GPT-5 | OpenAI | 272k | 272k | Active |
| GPT-5 Mini | OpenAI | 200k | 200k | Active |
| Gemini 3.1 Pro | Google | 200k | 1M | Current |
| Gemini 3 Pro | Google | 200k | 1M | Current |
| Gemini 3 Pro Image Preview | Google | 200k | 1M | Preview |
| Gemini 3 Flash | Google | 200k | 1M | Current |
| Gemini 2.5 Flash | Google | 200k | 1M | Legacy (active) |
| Composer 2 | Cursor (Anysphere) | 200k | 200k | Current; default in Auto mode |
| Composer 1.5 | Cursor (Anysphere) | 200k | 200k | Hidden by default |
| Composer 1 | Cursor (Anysphere) | 200k | 200k | Hidden by default |
| Grok 4.20 | xAI | 200k | 2M | Current |
| Grok Code Fast 1 | xAI | 256k | 256k | Active; may be hidden by default |
| Grok Code | xAI | 256k | 256k | Removed from default list; re-add via custom model ID |
| Kimi K2.5 | Moonshot AI | 200k | 1M | Active |
| DeepSeek V4 Pro | DeepSeek | 1M | 1M | Available via API key / custom model |
| DeepSeek V4 Flash | DeepSeek | 1M | 1M | Available via API key / custom model |

#### Normal vs Max Mode Behavior

**Normal Mode (default):**
- All models use their advertised context window up to approximately 200k–272k tokens depending on the model family.
- Cursor's internal systems (system prompt, codebase index, file contents, conversation history) consume a significant portion of the advertised window. Effective user-available tokens are typically 30–80k depending on mode (chat, composer, agent).
- Context selection is handled automatically via Cursor's relevance algorithm, which pulls in files and symbols most likely to be needed.
- As of early 2026, a key behavioral change occurred: models like Claude Sonnet previously required Max Mode to use 200k context; now 200k is the standard default for all models, no Max Mode required.

**Max Mode:**
- Removes Cursor's context truncation and sends the full context window to the model.
- Most impactful on models with context windows larger than the default ~200k (e.g., Gemini 3 Pro at 1M, Grok 4.20 at 2M).
- Uses token-based pricing, which consumes credits faster than standard request-based usage.
- Available on all models as of current Cursor versions.
- Max Mode is now only needed to unlock 1M+ context windows (e.g., Gemini, Claude 4.6/4.7 Opus, GPT-5.4/5.5). Confirmed by Lee Robinson (VP Developer Education, Vercel/Cursor community): "Max mode is only needed for 1M context windows (e.g. Gemini)."
- Note: GPT-5.4 models were briefly placed in Max Mode by default for legacy billing customers as a migration mechanism toward usage-based pricing.

**Tab Autocomplete (Cursor-small):**
- Uses a separate, smaller model (~8k context window).
- Not configurable for context size; optimized for inline completion speed.

#### Cursor-Native Models: Composer Series

Cursor has developed its own proprietary coding models under the **Composer** brand:

- **Composer 1**: First-generation Cursor proprietary model. 200k context. Hidden by default in the model picker. Supports Agent and image tasks.
- **Composer 1.5**: Released February 2026. Adds Thinking support alongside Agent and Images. 200k context. Hidden by default.
- **Composer 2**: Released March 19, 2026. Third-generation model. 200k context. Built on the Kimi K2.5 (Moonshot AI) base with Cursor's continued pretraining and reinforcement learning applied on top of coding-specific data. Ships in Standard ($0.50/MTok input) and Fast ($1.50/MTok input) variants. Fast variant is the default in Auto mode. Achieves 61.7% on Terminal-Bench 2.0 (vs. 40.0% for Composer 1, over a 50% improvement). Cursor confirmed ~75% of Composer 2's performance characteristics derive from their additional training.

Composer models are the only models with **unlimited access on paid plans** when using Auto mode. Third-party models (Claude, GPT, Gemini, etc.) draw from the monthly credit pool.

#### Notable Model Changes and Deprecations (Recent)

- **Context window expansion (major change, early 2026)**: All models now have larger default context windows without requiring Max Mode. Previously, Claude Sonnet needed Max Mode to use 200k; now 200k is the default for all models, and Max Mode is reserved for 1M+ access.
- **Grok Code (original) removed from defaults**: Cursor quietly removed the original Grok Code model from the default model list due to low usage. It can be re-added manually via Settings → Models → Add Model using the `grok-code-fast-1` identifier.
- **Grok 4.20 is the current primary xAI model** in Cursor, replacing the original Grok Code. It offers 200k default context and up to 2M tokens in long-context mode.
- **GPT-5.4 context discrepancy**: GPT-5.4 has 200k standard context and 272k in Max Mode, despite OpenAI offering larger context on the underlying API. This pattern also applies to GPT-5.2 (272k in Cursor). Cursor has not publicly explained the cap.
- **Claude 4.5 Opus Max Mode capped at 200k**: Unlike Claude 4.6 and 4.7 Opus (which support 1M in Max Mode), Claude 4.5 Opus is capped at 200k even in Max Mode.
- **DeepSeek V4 models**: Available but require user-supplied API keys. Added via the custom model interface. V4 Pro and V4 Flash natively support 1M tokens.
- **Cursor 3.2** (released April 24, 2026) is the current version — focused on multi-tasking agents, workspaces, and background agent tasks. No model deprecations were announced in this release.
- **Composer 2 confirmed as Kimi K2.5 derivative**: Cursor disclosed on March 20, 2026 that Composer 2 is built on Moonshot AI's open-source Kimi K2.5 base model.

#### Sources

- [Cursor Models Documentation](https://cursor.com/docs/models)
- [Cursor Max Mode Documentation](https://cursor.com/docs/context/max-mode)
- [Grok 4.20 in Cursor — Official Docs](https://cursor.com/docs/models/grok-4-20)
- [Lee Robinson on X — Default Context Window Change](https://x.com/leerob/status/1954685896173011319)
- [Cursor Forum — GPT-5.2 272k Context Discussion](https://forum.cursor.com/t/why-is-gpt-5-2-272k-context-and-not-400k/145986)
- [Cursor Forum — GPT-5.4 Out Now](https://forum.cursor.com/t/gpt-5-4-out-now/153744)
- [Cursor Forum — Grok Code Gone](https://forum.cursor.com/t/grok-code-is-gone-bring-it-back/155626)
- [Cursor Forum — Max Mode Only All Latest Models](https://forum.cursor.com/t/max-mode-only-all-latest-models/155684)
- [Cursor Changelog](https://cursor.com/changelog)
- [Cursor 3.0 New Interface](https://cursor.com/changelog/3-0)
- [Composer 2 Review — Build Fast with AI](https://www.buildfastwithai.com/blogs/cursor-composer-2-review-2026)
- [Composer 2 Announcement — Winbuzzer](https://winbuzzer.com/2026/03/20/cursor-unveils-composer-2-for-cheaper-ai-coding-xcxwbn/)
- [Cursor Release Notes — April 2026](https://releasebot.io/updates/cursor)
- [Cursor Context Window Guide — Morph](https://www.morphllm.com/cursor-context-window)
- [How to Optimize Model Usage v3.0 — Cursor Forum](https://forum.cursor.com/t/how-to-optimize-your-usage-the-best-ai-models-to-use-version-3-0/145657)
- [DeepSeek V4 in Cursor — Setup Guide](https://andrew.ooo/answers/how-to-use-deepseek-v4-in-cursor-2026/)
- [Cursor IDE Complete Guide 2026 — Codersera](https://codersera.com/blog/cursor-ide-complete-guide-2026/)

---

## Gemini CLI Research
**Agent:** Dr. Raj Patel
**Status:** Complete

### Context Windows

#### Current Models (Active as of 2026-05-02)

| Model | API ID | Context Window | Max Output | Status |
|-------|--------|---------------|------------|--------|
| Gemini 3.1 Pro Preview | `gemini-3.1-pro-preview` | 1M tokens (1,048,576) | 64k tokens (65,536) | Preview / Current |
| Gemini 3 Flash Preview | `gemini-3-flash-preview` | 1M tokens (1,048,576) | 64k tokens | Preview / Current |
| Gemini 3.1 Flash-Lite Preview | `gemini-3.1-flash-lite-preview` | 1M tokens (1,048,576) | 64k tokens | Preview / Current |
| Gemini 3.1 Flash Image Preview | `gemini-3.1-flash-image-preview` | 128k tokens | 32k tokens | Preview (image gen) |
| Gemini 3 Pro Image Preview | `gemini-3-pro-image-preview` | 65k tokens | 32k tokens | Preview (image gen) |
| Gemini 2.5 Pro | `gemini-2.5-pro` | 1M tokens (1,048,576) | 65,535 tokens | Stable / Active |
| Gemini 2.5 Flash | `gemini-2.5-flash` | 1M tokens (1,048,576) | 65,535 tokens | Stable / Active |
| Gemini 2.5 Flash-Lite | `gemini-2.5-flash-lite` | 1M tokens | 65k tokens | Stable / Active |
| Gemini 2.0 Flash | `gemini-2.0-flash` | 1M tokens | 8k tokens | Deprecated (EOL Jun 1, 2026) |
| Gemini 2.0 Flash Lite | `gemini-2.0-flash-lite` | 1M tokens | 8k tokens | Deprecated (EOL Jun 1, 2026) |
| Gemini 3 Pro Preview (original) | `gemini-3-pro-preview` | 1M tokens | 64k tokens | Discontinued (Mar 26, 2026) |

All Gemini 3 series models are currently in preview release. No stable/GA Gemini 3 model has been announced as of 2026-05-02.

#### Gemini CLI Tool — Model Support

The [Gemini CLI](https://github.com/google-gemini/gemini-cli) (open-source, terminal-based AI agent) is on its latest stable release **v0.40.1** (April 30, 2026). Key model-related details:

- Default model selection uses **intelligent auto-routing**: simple queries are routed to Flash; complex/analytical tasks route to Pro.
- Users can manually override via the `/model` command or the `-m` flag (e.g., `gemini -m gemini-2.5-flash`).
- As of December 2025, **Gemini 3 Flash** became available in Gemini CLI for high-frequency terminal workflows.
- **Gemma 4 models** (experimental local inference) were added in the v0.41.0-preview builds.
- The CLI supports all Gemini API models accessible via an API key, including Gemini 2.5 Pro/Flash and Gemini 3.x preview models.

#### Extended Context Availability

- **1M token context (1,048,576 tokens)** is the standard tier for all current Gemini Pro and Flash models. This applies to both the Gemini 2.5 and Gemini 3 series.
- **2M token context**: Gemini 1.5 Pro historically supported up to 2M tokens, but this model is entering end-of-life. No current Gemini 2.5 or Gemini 3 model offers a 2M token context window as a standard offering — the ceiling is 1M for all active models as of 2026-05-02.
- The Flash Live and audio/TTS variants have reduced context windows (128k tokens) due to real-time streaming constraints.
- Image generation models (`*-image-preview`) are capped at 65k input tokens and 32k output tokens.

#### Deprecations and Retirements

| Model | Status | Discontinuation Date | Replacement |
|-------|--------|----------------------|-------------|
| `gemini-3-pro-preview` | Discontinued | March 26, 2026 | `gemini-3.1-pro-preview` |
| `gemini-2.5-flash-lite-preview-09-2025` | Discontinued | March 31, 2026 | `gemini-2.5-flash-lite` |
| `gemini-robotics-er-1.5-preview` | Shut down | April 30, 2026 | `gemini-robotics-er-1.6-preview` |
| `gemini-2.0-flash` | Deprecated | June 1, 2026 (EOL) | `gemini-2.5-flash` |
| `gemini-2.0-flash-001` | Deprecated | June 1, 2026 (EOL) | `gemini-2.5-flash` |
| `gemini-2.0-flash-lite` | Deprecated | June 1, 2026 (EOL) | `gemini-2.5-flash-lite` |
| `gemini-2.0-flash-lite-001` | Deprecated | June 1, 2026 (EOL) | `gemini-2.5-flash-lite` |
| `gemini-2.5-pro` | Active — guaranteed until | Not before Oct 16, 2026 | Gemini 3.1 Pro (when GA) |
| `gemini-2.5-flash` | Active — guaranteed until | Not before Oct 16, 2026 | Gemini 3 Flash (when GA) |
| `text-embedding-004` | Retired | January 14, 2026 | `text-embedding-005` |

Note: Shutdown dates are the earliest possible dates per Google policy — actual deprecation may be later.

#### Notable Changes Since Last Research

- **Gemini 3 Pro Preview deprecated**: The original `gemini-3-pro-preview` was discontinued on March 26, 2026 and now points to `gemini-3.1-pro-preview`. Users must update integrations.
- **Gemini 3.1 Pro is the current leading model** in the Gemini 3 family — the "3.1" revision supersedes the original 3 Pro.
- **Gemini 3.1 Flash-Lite** (released March 3, 2026) fills the lightweight/cost-efficient tier in the Gemini 3 series.
- **Gemini 2.0 Flash end-of-life** is imminent (June 1, 2026). Migration to Gemini 2.5 Flash is the recommended path — same 1M context, significantly better max output (65k vs 8k tokens).
- **No 2M token models are currently active.** The Gemini 1.5 Pro 2M-context offering has been phased out; all current-gen models top out at 1M.
- **Gemma 4** (Google's open-weights model) was added to Gemini CLI experimental support in v0.41.0-preview builds for local inference — separate from Gemini API models.

#### Sources

- [Models — Gemini API | Google AI for Developers](https://ai.google.dev/gemini-api/docs/models)
- [Gemini 3 Developer Guide — Google AI for Developers](https://ai.google.dev/gemini-api/docs/gemini-3)
- [Gemini Deprecations — Google AI for Developers](https://ai.google.dev/gemini-api/docs/deprecations)
- [Gemini API Changelog — Google AI for Developers](https://ai.google.dev/gemini-api/docs/changelog)
- [Gemini 2.5 Pro — Vertex AI Docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/2-5-pro)
- [Gemini 2.5 Flash — Vertex AI Docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/2-5-flash)
- [Gemini 3 Pro — Vertex AI Docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-pro)
- [Gemini CLI GitHub — google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli)
- [Gemini CLI Releases](https://github.com/google-gemini/gemini-cli/releases)
- [Gemini 3 Flash now available in Gemini CLI — Google Developers Blog](https://developers.googleblog.com/gemini-3-flash-is-now-available-in-gemini-cli/)
- [Gemini 2.0 Flash Deprecation Migration Guide — GemiLab](https://gemilab.net/en/articles/gemini-api/gemini-2-0-flash-deprecation-june-2026-migration-guide)
- [Gemini 3.1 Pro Preview — OpenRouter](https://openrouter.ai/google/gemini-3.1-pro-preview)
- [Gemini 3 Flash Preview — OpenRouter](https://openrouter.ai/google/gemini-3-flash-preview)
