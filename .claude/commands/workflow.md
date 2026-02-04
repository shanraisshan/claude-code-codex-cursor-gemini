# Context Window & Features Research Workflow

Execute the research workflow to keep `README.md` up-to-date with the latest context windows and features.

---

## Agents

```yaml
agents:
  - name: claude-code-research-agent
    persona: Dr. Sarah Chen
    experience: 12 years @ Anthropic
    domain: Claude Code & Anthropic models

  - name: codex-cli-research-agent
    persona: Marcus Thompson
    experience: 10 years @ OpenAI
    domain: Codex CLI & OpenAI models

  - name: cursor-research-agent
    persona: Elena Rodriguez
    experience: 8 years @ Anysphere
    domain: Cursor IDE & multi-model support

  - name: gemini-cli-research-agent
    persona: Dr. Raj Patel
    experience: 10 years @ DeepMind
    domain: Gemini CLI & Google models
```

---

## Steps

```yaml
steps:
  - step: 0
    name: Initialize Research Session
    description: Create timestamped research folder
    execution: sequential
    tasks:
      - action: Create folder in research/ with timestamp format YYYY-MM-DD_HH-MM-SS
        path: ${CLAUDE_PROJECT_DIR}/research/{timestamp}/
      - action: Initialize research.md in the folder with header and metadata

  - step: 1
    name: Parallel Research
    description: Launch all 4 research agents simultaneously
    execution: parallel
    tasks:
      - agent: claude-code-research-agent
        action: Research Claude Code - TWO SECTIONS REQUIRED
        research_topics:
          1_context_windows:
            - Latest Claude models (Opus, Sonnet, Haiku) and their context window sizes
            - Any beta features (extended context like 1M)
            - Max output token limits
            - Model deprecations or new releases
          2_features:
            - Hooks support and event types
            - MCP/Plugin support
            - Sub-agents capability
            - Slash commands available
            - Custom commands/skills
            - IDE integrations
            - Git integration features
            - Web search capability
            - Sandbox/security features
            - Cost tracking options
        output: Append findings to research.md under "## Claude Code Research" with subsections for "### Context Windows" and "### Features"

      - agent: codex-cli-research-agent
        action: Research Codex CLI - TWO SECTIONS REQUIRED
        research_topics:
          1_context_windows:
            - Latest Codex/GPT models and their context window sizes
            - Context compaction features
            - Max output token limits
            - Model deprecations or new releases
          2_features:
            - Hooks support
            - MCP/Plugin support
            - Sub-agents capability
            - Slash commands available
            - Custom commands
            - IDE integrations
            - Git integration features
            - Web search capability
            - Sandbox/approval modes
            - Cost tracking options
        output: Append findings to research.md under "## Codex CLI Research" with subsections for "### Context Windows" and "### Features"

      - agent: cursor-research-agent
        action: Research Cursor - TWO SECTIONS REQUIRED
        research_topics:
          1_context_windows:
            - All supported models (Anthropic, OpenAI, Google, xAI, DeepSeek, Cursor native)
            - Context window sizes for each model
            - Normal vs Max mode differences
            - Model deprecations or new releases
          2_features:
            - Hooks support
            - VS Code extension compatibility
            - Sub-agents/parallel agents
            - Slash commands available
            - Custom rules (.cursorrules)
            - Composer/Agent mode capabilities
            - Git integration features
            - Web search (@Web)
            - Background agents
            - Codebase indexing
            - MCP support
        output: Append findings to research.md under "## Cursor Research" with subsections for "### Context Windows" and "### Features"

      - agent: gemini-cli-research-agent
        action: Research Gemini CLI - TWO SECTIONS REQUIRED
        research_topics:
          1_context_windows:
            - Latest Gemini models and their context window sizes
            - Max output token limits
            - Model deprecations timeline
            - New model releases
          2_features:
            - Hooks support
            - Extensions/MCP support
            - Sub-agents capability
            - Slash commands available
            - Custom commands (TOML)
            - IDE integrations
            - Git integration features
            - Web search (Google Search grounding)
            - Sandbox modes
            - Google Cloud integration
            - Cost tracking (/stats)
        output: Append findings to research.md under "## Gemini CLI Research" with subsections for "### Context Windows" and "### Features"

  - step: 2
    name: Aggregate & Compare
    description: Compile results and compare with current README
    execution: sequential
    tasks:
      - action: Read all agent findings from research.md
      - action: Read current README.md and reports/context-comparison.md
      - action: Create result.md with aggregated findings
      - action: Generate diff section showing changes for BOTH context windows AND features
      - action: DO NOT update README directly

  - step: 3
    name: User Confirmation
    description: Present findings and request approval
    execution: sequential
    tasks:
      - action: Display summary of changes found (context windows AND features)
      - action: Show diff between current README and proposed updates
      - action: Ask user "These are my findings. Do you want to update the README?"
      - action: Wait for user confirmation before making any changes
```

---

## Research Folder Structure

```
research/
└── {YYYY-MM-DD_HH-MM-SS}/
    ├── research.md      # Individual agent findings (context windows + features)
    └── result.md        # Aggregated results and diff
```

### research.md Format

```markdown
# Context Window & Features Research Session

**Started:** {timestamp}
**Status:** In Progress

---

## Claude Code Research
**Agent:** Dr. Sarah Chen
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

### Features
[Agent writes feature findings here]

---

## Codex CLI Research
**Agent:** Marcus Thompson
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

### Features
[Agent writes feature findings here]

---

## Cursor Research
**Agent:** Elena Rodriguez
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

### Features
[Agent writes feature findings here]

---

## Gemini CLI Research
**Agent:** Dr. Raj Patel
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

### Features
[Agent writes feature findings here]
```

### result.md Format

```markdown
# Research Results

**Completed:** {timestamp}

## Summary

| Tool | Context Window Changes | Feature Changes |
|------|------------------------|-----------------|
| Claude Code | Yes/No | Yes/No |
| Codex CLI | Yes/No | Yes/No |
| Cursor | Yes/No | Yes/No |
| Gemini CLI | Yes/No | Yes/No |

## Proposed Context Window Updates

[New context window comparison table]

## Proposed Feature Updates

[New feature comparison table]

## Diff: Current vs New

### README.md - Context Window Changes
```diff
- old line
+ new line
```

### README.md - Feature Changes
```diff
- old line
+ new line
```

### reports/context-comparison.md Changes
```diff
- old line
+ new line
```
```

---

## Instructions

Execute this workflow by following these steps:

**Step 0**: Create the research folder with timestamp
```bash
mkdir -p ${CLAUDE_PROJECT_DIR}/research/{YYYY-MM-DD_HH-MM-SS}
```

**Step 1**: Use the Task tool to launch all 4 research agents in **parallel** (single message with 4 Task tool calls). Each agent must research BOTH:
- Context window information (models, sizes, limits)
- Feature information (hooks, plugins, commands, integrations, etc.)

**Step 2**: After all agents complete, read their findings and create `result.md` with:
- Aggregated data from all agents
- Comparison with current README.md (both context window AND feature sections)
- Clear diff showing what would change

**Step 3**: Present findings to user and ask for confirmation:
> "These are my findings for context windows and features. Do you want to update the README?"

**IMPORTANT**: Do NOT update README.md or reports/context-comparison.md without explicit user approval.

---

## Output Format

```yaml
output:
  header: "CONTEXT WINDOW & FEATURES RESEARCH WORKFLOW"
  date: YYYY-MM-DD
  research_folder: research/{timestamp}/

  phase_0_results:
    folder_created: true/false
    research_md_initialized: true/false

  phase_1_results:
    claude_code:
      context_window_changes: true/false
      feature_changes: true/false
      written_to_research_md: true/false
    codex_cli:
      context_window_changes: true/false
      feature_changes: true/false
      written_to_research_md: true/false
    cursor:
      context_window_changes: true/false
      feature_changes: true/false
      written_to_research_md: true/false
    gemini_cli:
      context_window_changes: true/false
      feature_changes: true/false
      written_to_research_md: true/false

  phase_2_results:
    result_md_created: true/false
    context_window_diff_generated: true/false
    feature_diff_generated: true/false
    changes_found:
      context_windows:
        - description of change 1
      features:
        - description of change 1

  phase_3_results:
    user_prompted: true/false
    user_approved: true/false
    readme_updated: true/false
    report_updated: true/false

  status: COMPLETE/PARTIAL/FAILED/AWAITING_APPROVAL
```

---

Begin execution now:
1. First, create the timestamped research folder and initialize research.md
2. Then launch all 4 research agents in parallel using a single message with multiple Task tool calls
3. Each agent MUST research BOTH context windows AND features
4. After agents complete, create result.md with findings and diff for both sections
5. Ask user for approval before updating any files
