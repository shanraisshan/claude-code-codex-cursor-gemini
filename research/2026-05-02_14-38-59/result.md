# Research Results

**Completed:** 2026-05-02 14:38:59

## Summary

| Tool | Context Window Changes |
|------|------------------------|
| Claude Code | Yes — Opus 4.7 (1M GA), Sonnet 4.6 (1M GA), 1M no longer beta |
| Codex CLI | Yes — GPT-5.5 / 5.4 / 5.4-mini / 5.3-codex now current; 1M API context for 5.4/5.5 |
| Cursor | Yes — Composer 2 added; Grok 4.20 (2M Max) replaces Grok Code; Claude 4.7/4.6 added; GPT-5.4/5.5 added |
| Gemini CLI | Yes — Gemini 3.1 Pro replaces Gemini 3 Pro (discontinued Mar 26, 2026); 2M tier no longer exists |

---

## Proposed Context Window Updates

### New README.md "Context Window Comparison" table

| Tool | Largest Context | Best Model | Input $/M | Output $/M | Source |
|------|-----------------|------------|-----------|------------|--------|
| Claude Code | 1M (GA) | Opus 4.7 | $5.00 | $25.00 | [Anthropic Models](https://platform.claude.com/docs/en/about-claude/models/overview) |
| Codex CLI | 1M (API) / 400k (Codex cap) | GPT-5.5 | TBD* | TBD* | [OpenAI Codex Models](https://developers.openai.com/codex/models) |
| Cursor | 2M (Max Mode) | Grok 4.20 | $3.00** | $15.00** | [Cursor Models](https://cursor.com/docs/models) |
| Gemini CLI | 1M | Gemini 3.1 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |

\* Pricing TBD pending publication of GPT-5.5 rates.
\** Cursor passes through underlying provider rates; Grok 4.20 pricing follows xAI rates.

---

## Diff: Current vs New

### README.md — Context Window Changes

```diff
-> **Last Updated:** 2026-02-09
+> **Last Updated:** 2026-05-02

 | Tool | Largest Context | Best Model | Input $/M | Output $/M | Source |
 |------|-----------------|------------|-----------|------------|--------|
-| Claude Code | 1M (beta) | Opus 4.6 with `context-1m-2025-08-07` beta | $5.00 | $25.00 | [Anthropic Models](https://docs.anthropic.com/en/docs/about-claude/models) |
-| Codex CLI | 400k | GPT-5.3-Codex (Feb 2026) | TBD* | TBD* | [OpenAI Models](https://platform.openai.com/docs/models) |
-| Cursor | 2M (native) | Gemini 3 Pro (200k/1M/2M modes) | $2.00** | $12.00** | [Cursor Models](https://cursor.com/docs/models) |
-| Gemini CLI | 1M | Gemini 3 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |
+| Claude Code | 1M (GA) | Opus 4.7 | $5.00 | $25.00 | [Anthropic Models](https://platform.claude.com/docs/en/about-claude/models/overview) |
+| Codex CLI | 1M (API) / 400k (Codex cap) | GPT-5.5 | TBD* | TBD* | [OpenAI Codex Models](https://developers.openai.com/codex/models) |
+| Cursor | 2M (Max Mode) | Grok 4.20 | $3.00** | $15.00** | [Cursor Models](https://cursor.com/docs/models) |
+| Gemini CLI | 1M | Gemini 3.1 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |
```

### reports/context-comparison.md — Key Changes

**Claude Code section:**
```diff
-> **Last Updated:** 2026-02-06
+> **Last Updated:** 2026-05-02

-| Opus 4.6 | 200k (1M beta) | 128k | ... | Latest model (Feb 5, 2026), adaptive thinking, first Opus with 1M context |
-| Opus 4.5 | 200k | 64k | ... | Premium model, complex reasoning, 67% lower cost than predecessor |
-| Sonnet 4.5 | 200k (1M beta) | 64k | ... | Recommended default, context awareness feature, best coding model |
-| Haiku 4.5 | 200k | 64k | ... | Fastest, context awareness feature, unbeatable for UI work |
+| Opus 4.7 | 1M (GA) | 128k | $5.00 | $25.00 | Latest flagship (Apr 16, 2026), 1M GA, adaptive thinking, new tokenizer |
+| Opus 4.6 | 1M (GA) | 128k | $5.00 | $25.00 | Released Feb 5, 2026; 1M GA since Mar 13, 2026 |
+| Sonnet 4.6 | 1M (GA) | 64k | $3.00 | $15.00 | Released early 2026; 1M GA since Mar 13, 2026; default for Pro/API |
+| Haiku 4.5 | 200k | 64k | $1.00 | $5.00 | Fastest, no 1M context support |
```
- Add deprecations: `claude-opus-4` and `claude-sonnet-4` retiring Jun 15, 2026
- Note: Entire Claude 3.x generation fully retired in 2026
- Add 300k output Beta (Batch API) for Opus 4.7 / Opus 4.6 / Sonnet 4.6

**Codex CLI section:**
```diff
-| GPT-5.3-Codex | 400k | 128k | TBD | TBD | Latest model (Feb 5, 2026), "Perfect Recall" attention, 25% faster |
-| GPT-5.2-Codex | 400k | 128k | $1.75 | $14.00 | Native compaction, reliable tool calling (Jan 14, 2026) |
-| GPT-5.1-Codex-Max | Multi-window (millions) | N/A | $1.25 | $10.00 | First model natively trained for compaction |
-| GPT-5-Codex | 200k | N/A | $1.25 | $10.00 | Standard model with 200K context window |
-| codex-mini-latest | ~200k | N/A | - | - | **DEPRECATED** - Removed Jan 16, 2026 |
+| gpt-5.5 | 1.05M (API) / ~400k (Codex) | 128k | TBD | TBD | Latest frontier (Apr 23, 2026); Codex caps at 400k |
+| gpt-5.4 | 1.05M | 128k | $2.50 (doubles >272k) | TBD | Flagship; experimental 1M in Codex via config |
+| gpt-5.4-mini | 400k | 128k | TBD | TBD | Default mini model |
+| gpt-5.3-codex | 400k | 128k | TBD | TBD | Default coding model (Feb 2026) |
+| gpt-5.3-codex-spark | 128k | N/A | N/A | N/A | Research preview; ChatGPT Pro only |
+| gpt-5.2 | 400k | 128k | $2.00 | $8.00 | Previous frontier, still supported |
+| gpt-5-codex | 400k | 128k | $1.25 | $10.00 | Deprecated — retires Jul 23, 2026 |
+| codex-mini-latest | 200k | — | — | — | **RETIRED** Feb 12, 2026 |
+| o4-mini | 200k | — | $1.10 | $4.40 | **DEPRECATED** — shutdown Oct 23, 2026 |
+| o3 / o3-mini | 200k | — | — | — | **DEPRECATED**; o3-mini shut down Feb 23, 2026 |
```
- Add note: Codex auto-compact triggers at 95% (clamped to 90% in v0.100.0+)
- Add note: GPT-5.5 has known internal context bug (#19319) reducing effective context to ~258k

**Cursor section:**
```diff
+ Add Anthropic: Claude 4.7 Opus, Claude 4.6 Opus, Claude 4.6 Sonnet (200k/1M Max each)
- Remove obsolete Claude 3.5/3.7 from primary listing (retired upstream)
+ Add OpenAI: GPT-5.5, GPT-5.4, GPT-5.4 Mini, GPT-5.4 Nano, GPT-5.3 Codex (200k/1M Max for 5.4/5.5)
+ Add Google: Gemini 3.1 Pro (200k/1M Max), update Gemini 3 Pro/Flash entries
+ Add Cursor Native: Composer 2 (200k, default in Auto), Composer 1.5 (200k, hidden)
+ Update xAI: Grok 4.20 (200k/2M Max) — Grok Code removed from defaults
+ Add Moonshot: Kimi K2.5 (200k/1M Max)
+ Update DeepSeek: V4 Pro / V4 Flash (1M/1M, custom-model only)
+ Update behavioral note: 200k is now default for ALL models; Max Mode reserved for 1M+
```

**Gemini CLI section:**
```diff
-| Gemini 3 Pro Preview | 1M | 65k | $2.00 | $12.00 | Current flagship |
+| Gemini 3.1 Pro Preview | 1M | 64k | $2.00 | $12.00 | Current flagship; supersedes gemini-3-pro-preview |
+| Gemini 3 Pro Preview (original) | 1M | 64k | — | — | **DISCONTINUED** Mar 26, 2026 |
+| Gemini 3.1 Flash-Lite Preview | 1M | 64k | TBD | TBD | New (Mar 3, 2026) |
+| Gemini 3.1 Flash Image Preview | 128k | 32k | TBD | TBD | Image gen preview |
```
- Update Gemini 2.0 Flash deprecation: EOL **June 1, 2026** (was March 31, 2026 in current README)
- Add note: Gemini CLI v0.40.1 (Apr 30, 2026) is current stable; Gemma 4 in v0.41.0-preview
- Confirm: 2M context window no longer exists in any active Gemini model

---

## Changes Summary

| # | Change | Severity |
|---|--------|----------|
| 1 | Claude Code: Opus 4.7 launched (Apr 16, 2026); flagship is now 4.7 not 4.6 | HIGH |
| 2 | Claude Code: 1M context is GA (no longer beta) for Opus 4.7/4.6 and Sonnet 4.6 | HIGH |
| 3 | Claude Code: Sonnet 4.6 with 1M GA replaces Sonnet 4.5 in current README | HIGH |
| 4 | Codex CLI: GPT-5.5 is new flagship (Apr 23, 2026); 1M API / 400k Codex cap | HIGH |
| 5 | Codex CLI: GPT-5.4 family (5.4, 5.4-mini, 5.4-nano) added | HIGH |
| 6 | Codex CLI: GPT-5.1-Codex-Max & GPT-5-Codex deprecated; codex-mini retired | MEDIUM |
| 7 | Cursor: Composer 2 (Mar 19, 2026) is default in Auto mode | HIGH |
| 8 | Cursor: Grok 4.20 (200k/2M) replaces Grok Code as primary xAI model | HIGH |
| 9 | Cursor: Default 200k for all models; Max Mode now reserved for 1M+ | HIGH |
| 10 | Gemini CLI: gemini-3-pro-preview discontinued Mar 26, 2026 → 3.1-pro-preview | HIGH |
| 11 | Gemini CLI: Gemini 2.0 Flash EOL is June 1, 2026 (not March 31) | LOW |
| 12 | Gemini CLI: No 2M context exists; ceiling is 1M for all active models | MEDIUM |

---

## Recommendation

The README "Context Window Comparison" table is significantly out of date. All four tools have new flagship models since the last update (2026-02-09). Recommend updating both `README.md` and `reports/context-comparison.md` to reflect the 2026-05-02 state.
