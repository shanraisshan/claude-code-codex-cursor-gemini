# claude-code-codex-cursor-gemini

![AI Coding Tools](!/banner-pills.svg)

![Battle of the AI Agents](!/claude-mascot.svg)
![Battle of the AI Agents](!/codex-mascot.svg)
![Battle of the AI Agents](!/cursor-mascot.svg)
![Battle of the AI Agents](!/gemini-mascot.svg)

![AI Models](!/banner-models.svg)

> **Last Updated:** 2026-02-09

**AI TERMS:**

| | | | | |
|---|---|---|---|---|
| Agentic Engineering | AI Slop | Context Bloat | Context Engineering | Context Rot |
| Dumb Zone | Hallucination | Scaffolding | Orchestration | Vibe Coding |

[**See Complete List →**](/reports/ai-terms.md)

## Context Window Comparison

| Tool | Largest Context | Best Model | Input $/M | Output $/M | Source |
|------|-----------------|------------|-----------|------------|--------|
| Claude Code | 1M (beta) | Opus 4.6 with `context-1m-2025-08-07` beta | $5.00 | $25.00 | [Anthropic Models](https://docs.anthropic.com/en/docs/about-claude/models) |
| Codex CLI | 400k | GPT-5.3-Codex (Feb 2026) | TBD* | TBD* | [OpenAI Models](https://platform.openai.com/docs/models) |
| Cursor | 2M (native) | Gemini 3 Pro (200k/1M/2M modes) | $2.00** | $12.00** | [Cursor Models](https://cursor.com/docs/models) |
| Gemini CLI | 1M | Gemini 3 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |

> \* GPT-5.3-Codex pricing not yet published by OpenAI (Feb 2026 release)
> \*\* Cursor uses subscription pricing ($20/mo Pro); API prices shown are for underlying models

[View Full Report](reports/context-comparison.md)

---

## Feature Comparison

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

[View Full Report](reports/feature-comparison.md)
