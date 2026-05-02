# Agenting Engineering

Does code matter?

![updated with Claude Code](https://img.shields.io/badge/updated_with_Claude_Code-v2.1.126%20(May%2002%2C%202026%203%3A07%20PM%20PKT)-white?style=flat&labelColor=555)<br>

![AI Coding Tools](!/banner-pills.svg)

![Battle of the AI Agents](!/claude-mascot.svg)
![Battle of the AI Agents](!/codex-mascot.svg)
![Battle of the AI Agents](!/cursor-mascot.svg)
![Battle of the AI Agents](!/gemini-mascot.svg)

![AI Models](!/banner-models.svg)

<p align="center">
  <img src="!/claude-mascot.svg" alt="Claude" width="50">
  <img src="!/codex-mascot.svg" alt="Codex" width="25">
  <img src="!/cursor-mascot.svg" alt="Cursor" width="25">
  <img src="!/gemini-mascot.svg" alt="Gemini" width="25">
</p>

## Does code matter?

### ✅ Yes

| Video | Author | Description |
|-------|--------|-------------|
| [Full Walkthrough: Workflow for AI Coding](https://youtu.be/-QFHIoCo-Ko) — 24 Apr 2026 | Matt Pocock | Matt argues against the "specs to code" movement — editing only the spec while ignoring the generated code is just vibe coding by another name, and it doesn't work. You have to keep a handle on the code, understand what's in it, and shape it, because **"the code is your battleground."** |
| [Everything We Got Wrong About Research-Plan-Implement](https://youtu.be/YwZR6tc7qYg?t=541) — 24 Mar 2026 | Dex Horthy | Dex publicly reverses his earlier "don't read the code, just ship the plan" advice: **"Please read the code. We tried not reading the code for like six months. It did not end well — we had to rip out and replace large parts of that system."** New rule: don't read the plans, read the code. Don't outsource the thinking. |

### ❌ No

| Video | Author | Description |
|-------|--------|-------------|
| [From Vibe Coding to Agentic Engineering](https://www.youtube.com/watch?v=96jN2OCOfLs) — 02 May 2026 | Andrej Karpathy | Karpathy argues code itself is becoming vestigial. After vibe-coding MenuGen, he saw the Software 3.0 version — just hand a photo to Gemini + Nanobanana — and concluded: **"All of my MenuGen is spurious. That app shouldn't exist."** Extrapolating: *"A lot of this code shouldn't exist and it's just neural network doing most of the work."* The neural net becomes the host process; code is the historical appendage. |
| [Building Claude Code with Boris Cherny](https://youtu.be/julbw1JuAz0) — 04 Mar 2026 | Boris Cherny | Boris's first PR at Anthropic was rejected — not because the code was bad, but because he wrote it by hand. He now ships **20–30 pull requests a day with zero handwritten code**, while Claude reviews 100% of PRs before a human ever sees them. |
| [Head of Claude Code: What happens after coding is solved](https://youtu.be/We7BZVKbCVw) — 19 Feb 2026 | Boris Cherny | Boris opens with: **"100% of my code is written by Claude Code. I have not edited a single line by hand since November. Every day I ship 10, 20, 30 pull requests."** Lenny cites that 4% of all GitHub commits are now AI-authored, and Spotify's best developers haven't written a line of code since December. |

<p align="center">
  <img src="!/claude-mascot.svg" alt="Claude" width="50">
  <img src="!/codex-mascot.svg" alt="Codex" width="25">
  <img src="!/cursor-mascot.svg" alt="Cursor" width="25">
  <img src="!/gemini-mascot.svg" alt="Gemini" width="25">
</p>

## AI Terms

| | | | | |
|---|---|---|---|---|
| Agentic Engineering | AI Slop | Context Bloat | Context Engineering | Context Rot |
| Dumb Zone | Hallucination | Scaffolding | Orchestration | Vibe Coding |

[**See Complete List →**](/reports/ai-terms.md)

<p align="center">
  <img src="!/claude-mascot.svg" alt="Claude" width="50">
  <img src="!/codex-mascot.svg" alt="Codex" width="25">
  <img src="!/cursor-mascot.svg" alt="Cursor" width="25">
  <img src="!/gemini-mascot.svg" alt="Gemini" width="25">
</p>

## Context Window Comparison

| Tool | Largest Context | Best Model | Input $/M | Output $/M | Source |
|------|-----------------|------------|-----------|------------|--------|
| Claude Code | 1M (GA) | Opus 4.7 | $5.00 | $25.00 | [Anthropic Models](https://platform.claude.com/docs/en/about-claude/models/overview) |
| Codex CLI | 1M (API) / 400k (Codex cap) | GPT-5.5 | TBD* | TBD* | [OpenAI Codex Models](https://developers.openai.com/codex/models) |
| Cursor | 2M (Max Mode) | Grok 4.20 | $3.00** | $15.00** | [Cursor Models](https://cursor.com/docs/models) |
| Gemini CLI | 1M | Gemini 3.1 Pro Preview | $2.00 | $12.00 | [Gemini API](https://ai.google.dev/gemini-api/docs/models) |

[**See Complete List →**](reports/context-comparison.md)

<p align="center">
  <img src="!/claude-mascot.svg" alt="Claude" width="50">
  <img src="!/codex-mascot.svg" alt="Codex" width="25">
  <img src="!/cursor-mascot.svg" alt="Cursor" width="25">
  <img src="!/gemini-mascot.svg" alt="Gemini" width="25">
</p>

## Other Repos

<table>
<tr>
<td align="center" width="140">
  <a href="https://github.com/shanraisshan/claude-code-best-practice"><img src="!/claude-jumping.svg" alt="Claude Code Best Practice" width="64" height="64"></a><br>
  <a href="https://github.com/shanraisshan/claude-code-best-practice"><strong>Claude Code<br>Best Practice</strong></a>
</td>
<td align="center" width="140">
  <a href="https://github.com/shanraisshan/claude-code-hooks"><img src="!/claude-speaking.svg" alt="Claude Code Hooks" width="64" height="64"></a><br>
  <a href="https://github.com/shanraisshan/claude-code-hooks"><strong>Claude Code<br>Hooks</strong></a>
</td>
<td align="center" width="140">
  <a href="https://github.com/shanraisshan/codex-cli-best-practice"><img src="!/codex-jumping.svg" alt="Codex CLI Best Practice" width="64" height="64"></a><br>
  <a href="https://github.com/shanraisshan/codex-cli-best-practice"><strong>Codex CLI<br>Best Practice</strong></a>
</td>
<td align="center" width="140">
  <a href="https://github.com/shanraisshan/codex-cli-hooks"><img src="!/codex-speaking.svg" alt="Codex CLI Hooks" width="64" height="64"></a><br>
  <a href="https://github.com/shanraisshan/codex-cli-hooks"><strong>Codex CLI<br>Hooks</strong></a>
</td>
<td align="center" width="140">
  <a href="https://github.com/shanraisshan/gemini-cli-best-practice"><img src="!/gemini-jumping.svg" alt="Gemini CLI Best Practice" width="64" height="64"></a><br>
  <a href="https://github.com/shanraisshan/gemini-cli-best-practice"><strong>Gemini CLI<br>Best Practice</strong></a>
</td>
<td align="center" width="140">
  <a href="https://github.com/shanraisshan/gemini-cli-hooks"><img src="!/gemini-speaking.svg" alt="Gemini CLI Hooks" width="64" height="64"></a><br>
  <a href="https://github.com/shanraisshan/gemini-cli-hooks"><strong>Gemini CLI<br>Hooks</strong></a>
</td>
</tr>
</table>
