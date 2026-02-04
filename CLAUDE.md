# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a research and comparison repository for AI coding assistants: **Claude Code**, **Codex CLI**, **Gemini CLI**, and **Cursor**. The repository tracks context window sizes, model availability, and feature comparisons across these tools.

## Project Structure

- `README.md` - Quick comparison tables for context windows and features
- `reports/context-comparison.md` - Detailed model comparison data
- `research/` - Timestamped research session outputs
- `.claude/agents/` - Research agent definitions (claude-code, codex-cli, cursor, gemini-cli)
- `.claude/commands/workflow.md` - The `/workflow` command for research automation
- `.claude/hooks/` - Audio notification system for hook events

## Research Workflow

Use `/workflow` to execute the research process. Each agent researches **two sections**:

1. **Context Windows** - Models, sizes, limits, deprecations
2. **Features** - Hooks, plugins, commands, integrations, etc.

### Workflow Steps

1. Creates timestamped folder in `research/`
2. Launches 4 research agents in **parallel** (must use single message with 4 Task tool calls)
3. Each agent writes findings to shared `research.md` with `### Context Windows` and `### Features` subsections
4. Aggregates results into `result.md` with diff comparison for both sections
5. **Requires user approval** before updating README.md

## Research Agents

Located in `.claude/agents/`, each with specialized persona and tools:

| Agent | Persona | Domain |
|-------|---------|--------|
| claude-code-research-agent | Dr. Sarah Chen | Claude Code, Anthropic models |
| codex-cli-research-agent | Marcus Thompson | Codex CLI, OpenAI models |
| cursor-research-agent | Elena Rodriguez | Cursor IDE, multi-model support |
| gemini-cli-research-agent | Dr. Raj Patel | Gemini CLI, Google models |

## Key Files to Update

When research finds changes:
- `README.md` - Context Window Comparison table, Feature Comparison table
- `reports/context-comparison.md` - Detailed model breakdowns, deprecation timelines

