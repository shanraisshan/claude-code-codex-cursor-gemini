# Context Window Research Workflow

Execute the research workflow to keep `README.md` up-to-date with the latest context windows.

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
        action: Research Claude Code context windows
        research_topics:
          - Latest Claude models (Opus, Sonnet, Haiku) and their context window sizes
          - Any beta features (extended context like 1M)
          - Max output token limits
          - Model deprecations or new releases
        output: Append findings to research.md under "## Claude Code Research" with subsection "### Context Windows"

      - agent: codex-cli-research-agent
        action: Research Codex CLI context windows
        research_topics:
          - Latest Codex/GPT models and their context window sizes
          - Context compaction features
          - Max output token limits
          - Model deprecations or new releases
        output: Append findings to research.md under "## Codex CLI Research" with subsection "### Context Windows"

      - agent: cursor-research-agent
        action: Research Cursor context windows
        research_topics:
          - All supported models (Anthropic, OpenAI, Google, xAI, DeepSeek, Cursor native)
          - Context window sizes for each model
          - Normal vs Max mode differences
          - Model deprecations or new releases
        output: Append findings to research.md under "## Cursor Research" with subsection "### Context Windows"

      - agent: gemini-cli-research-agent
        action: Research Gemini CLI context windows
        research_topics:
          - Latest Gemini models and their context window sizes
          - Max output token limits
          - Model deprecations timeline
          - New model releases
        output: Append findings to research.md under "## Gemini CLI Research" with subsection "### Context Windows"

  - step: 2
    name: Aggregate & Compare
    description: Compile results and compare with current README
    execution: sequential
    tasks:
      - action: Read all agent findings from research.md
      - action: Read current README.md and reports/context-comparison.md
      - action: Create result.md with aggregated findings
      - action: Generate diff section showing context window changes
      - action: DO NOT update README directly

  - step: 3
    name: User Confirmation
    description: Present findings and request approval
    execution: sequential
    tasks:
      - action: Display summary of context window changes found
      - action: Show diff between current README and proposed updates
      - action: Ask user "These are my findings. Do you want to update the README?"
      - action: Wait for user confirmation before making any changes

  - step: 4
    name: Update "Updated with Claude Code" Badge
    description: After README and report updates are confirmed, refresh the timestamp badge in README.md
    execution: sequential
    tasks:
      - action: Get current Claude Code version via `claude --version` (extract `X.Y.Z`)
      - action: Get current local date/time formatted as `Mon DD, YYYY H:MM AM/PM PKT` via `date +"%b %d, %Y %I:%M %p PKT"`
      - action: URL-encode the inner badge text — replace ` ` with `%20`, `,` with `%2C`, `:` with `%3A`
      - action: Replace the existing badge line in README.md (located directly below the description) with the freshly generated badge
      - action: Confirm only the badge line changed; do NOT add or restore a "Last Updated" plaintext line
```

---

## Research Folder Structure

```
research/
└── {YYYY-MM-DD_HH-MM-SS}/
    ├── research.md      # Individual agent findings (context windows)
    └── result.md        # Aggregated results and diff
```

### research.md Format

```markdown
# Context Window Research Session

**Started:** {timestamp}
**Status:** In Progress

---

## Claude Code Research
**Agent:** Dr. Sarah Chen
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

---

## Codex CLI Research
**Agent:** Marcus Thompson
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

---

## Cursor Research
**Agent:** Elena Rodriguez
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]

---

## Gemini CLI Research
**Agent:** Dr. Raj Patel
**Status:** Pending/Complete

### Context Windows
[Agent writes context window findings here]
```

### result.md Format

```markdown
# Research Results

**Completed:** {timestamp}

## Summary

| Tool | Context Window Changes |
|------|------------------------|
| Claude Code | Yes/No |
| Codex CLI | Yes/No |
| Cursor | Yes/No |
| Gemini CLI | Yes/No |

## Proposed Context Window Updates

[New context window comparison table]

## Diff: Current vs New

### README.md - Context Window Changes
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

**Step 1**: Use the Task tool to launch all 4 research agents in **parallel** (single message with 4 Task tool calls). Each agent researches context window information (models, sizes, limits).

**Step 2**: After all agents complete, read their findings and create `result.md` with:
- Aggregated data from all agents
- Comparison with current README.md context window section
- Clear diff showing what would change

**Step 3**: Present findings to user and ask for confirmation:
> "These are my findings for context windows. Do you want to update the README?"

**IMPORTANT**: Do NOT update README.md or reports/context-comparison.md without explicit user approval.

**Step 4**: After updates are applied, refresh the "updated with Claude Code" badge directly below the description in `README.md`. The badge format is:

```markdown
![updated with Claude Code](https://img.shields.io/badge/updated_with_Claude_Code-v{VERSION}%20({DATE_TIME_URLENCODED})-white?style=flat&labelColor=555)<br>
```

Where:
- `{VERSION}` = output of `claude --version` (just the `X.Y.Z` part)
- `{DATE_TIME_URLENCODED}` = output of `date +"%b %d, %Y %I:%M %p PKT"`, URL-encoded (` ` → `%20`, `,` → `%2C`, `:` → `%3A`)

Example: `v2.1.126%20(May%2002%2C%202026%203%3A07%20PM%20PKT)`

The badge replaces any prior "Last Updated" line — there must be exactly one timestamp source in the README, and it lives in the badge.

---

## Output Format

```yaml
output:
  header: "CONTEXT WINDOW RESEARCH WORKFLOW"
  date: YYYY-MM-DD
  research_folder: research/{timestamp}/

  phase_0_results:
    folder_created: true/false
    research_md_initialized: true/false

  phase_1_results:
    claude_code:
      context_window_changes: true/false
      written_to_research_md: true/false
    codex_cli:
      context_window_changes: true/false
      written_to_research_md: true/false
    cursor:
      context_window_changes: true/false
      written_to_research_md: true/false
    gemini_cli:
      context_window_changes: true/false
      written_to_research_md: true/false

  phase_2_results:
    result_md_created: true/false
    context_window_diff_generated: true/false
    changes_found:
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
3. Each agent researches context windows
4. After agents complete, create result.md with findings and diff
5. Ask user for approval before updating any files
