# AI TERMS


## AI Intelligence Levels

| Term | Author | Definition |
|------|--------|------------|
| AGI (Artificial General Intelligence) | [Shane Legg](https://en.wikipedia.org/wiki/Shane_Legg) (DeepMind co-founder) | Hypothetical AI matching human cognitive abilities across any task — can generalize, transfer skills, and solve novel problems without task-specific training |
| AGI Levels Framework | [Meredith Ringel Morris](https://x.com/meraboringmorris) & [Shane Legg](https://en.wikipedia.org/wiki/Shane_Legg) (Google DeepMind) | Five performance levels: Emerging, Competent, Expert, Virtuoso, Superhuman — classifying progress toward AGI |
| ANI (Artificial Narrow Intelligence) | | AI confined to a single well-defined task — all current AI systems are ANI (e.g., Siri, AlphaGo, ChatGPT) |
| ASI (Artificial Superintelligence) | [Nick Bostrom](https://nickbostrom.com/) (Oxford) | Hypothetical AI that vastly outperforms the best human abilities across every cognitive domain |
| Strong AI | [John Searle](https://en.wikipedia.org/wiki/John_Searle) (UC Berkeley) | AI that truly understands and has genuine mental states — contrasted with "Weak AI" that merely simulates intelligence |
| Weak AI | [John Searle](https://en.wikipedia.org/wiki/John_Searle) (UC Berkeley) | AI that simulates cognition without true understanding — all current AI systems fall under this category |


## Agents & Orchestration

| Term | Author | Definition |
|------|--------|------------|
| Agent = LLM + memory + planning + tools | [Lilian Weng](https://lilianweng.github.io/) (ex-OpenAI) | Foundational framework defining LLM-powered autonomous agents |
| Agentic Design Patterns | [Andrew Ng](https://www.deeplearning.ai/) (DeepLearning.AI) | Four core patterns: Reflection, Tool Use, Planning, Multi-Agent Collaboration |
| Agent Swarms | | Multiple AI agents working in parallel on subtasks, coordinating autonomously to solve a larger problem — swarm intelligence applied to LLM-based agents |
| Agentic Engineering | [Andrej Karpathy](https://x.com/karpathy) (Eureka Labs, ex-OpenAI) | Orchestrating AI agents that write code, with humans providing oversight |
| Agentic Workflow | | Structured sequence of AI agent tasks to complete a goal |
| Orchestration | | Coordinating multiple AI agents or steps in a workflow |
| The Holy Trinity | | Skills + Agents + Hooks architecture pattern |


## Human-AI Collaboration

| Term | Author | Definition |
|------|--------|------------|
| AI Engineer | [Swyx / Shawn Wang](https://www.smol.ai/) (Smol.ai) | Engineer building with AI APIs without deep ML expertise — a new role distinct from ML Engineer |
| Centaur Work | [Ethan Mollick](https://www.oneusefulthing.org/) (Wharton) | Human-AI collab with clear division — human does X, AI does Y, switching strategically |
| Cyborg Work | [Ethan Mollick](https://www.oneusefulthing.org/) (Wharton) | Human-AI collab deeply intertwined — moving fluidly between human and AI contributions |
| Vibe Coding | [Andrej Karpathy](https://x.com/karpathy) (Eureka Labs, ex-OpenAI) | Letting AI generate code without reading diffs — "give in to the vibes" |


## Context Management

| Term | Author | Definition |
|------|--------|------------|
| Context Bloat | | Excess context degrading AI performance and accuracy |
| Context Engineering | [Dexter Horthy](https://www.humanlayer.dev/) (HumanLayer) | Managing context provided to AI agents for maximum effectiveness |
| Context Rot | | Context becoming stale or irrelevant over long sessions |
| Dumb Zone | | Context window region where AI performance degrades |
| Progressive Disclosure | | Revealing context to AI incrementally as needed |
| Token Burn | | Wasting tokens on irrelevant or redundant context |


## Prompting & Techniques

| Term | Author | Definition |
|------|--------|------------|
| Chain-of-Thought Prompting | [Jason Wei](https://x.com/jabornewe) (Google/OpenAI) | Intermediate reasoning steps to improve LLM performance on complex tasks |
| One Shot | | Single-attempt task completion by AI |
| Prompt Injection | [Simon Willison](https://simonwillison.net/) | Malicious inputs that manipulate LLM system instructions — analogous to SQL injection |
| RAG (Retrieval-Augmented Generation) | [Patrick Lewis](https://www.patricklewis.io/) (Meta AI) | Combining model knowledge with external retrieval for grounded generation |


## AI Safety & Risk

| Term | Author | Definition |
|------|--------|------------|
| AI Alignment | [Paul Christiano](https://paulfchristiano.com/) (ARC, ex-OpenAI) | Ensuring AI systems behave in accordance with human values, preferences, and ethical principles |
| AI Safety | [Stuart Russell](https://people.eecs.berkeley.edu/~russell/) (UC Berkeley) | Research field focused on making AI systems safe, robust, and beneficial to humanity |
| Doom / AI Doom | [Eliezer Yudkowsky](https://www.yudkowsky.net/) (MIRI) | Belief that advanced AI will likely cause human extinction or civilizational collapse |
| Existential Risk (X-Risk) | [Nick Bostrom](https://nickbostrom.com/) (Oxford) | Risk threatening premature extinction of humanity or permanent destruction of its future potential |
| Intelligence Explosion | [I.J. Good](https://en.wikipedia.org/wiki/I._J._Good) (Mathematician) | Self-improving AI triggering a runaway feedback loop of ever-increasing intelligence |
| P(doom) | [Eliezer Yudkowsky](https://www.yudkowsky.net/) (MIRI) / Rationalist community | Estimated probability that AI causes human extinction — popularized in 2023 after GPT-4 release |
| Singularity (Technological) | [Ray Kurzweil](https://en.wikipedia.org/wiki/Ray_Kurzweil) (Google) / [Vernor Vinge](https://en.wikipedia.org/wiki/Vernor_Vinge) | The point where AI self-improvement becomes uncontrollable, fundamentally transforming civilization |


## AI Behavior & Quality

| Term | Author | Definition |
|------|--------|------------|
| AI Slop | [Simon Willison](https://simonwillison.net/) & [Casey Newton](https://www.platformer.news/) | Low-quality AI-generated content produced in quantity |
| Ghost Intelligence | [Andrej Karpathy](https://x.com/karpathy) (Eureka Labs, ex-OpenAI) | LLM intelligence as "summoning ghosts" — emphasizing alien cognitive architecture |
| Hallucination | | AI generating plausible but incorrect information |
| Jagged Intelligence | [Andrej Karpathy](https://x.com/karpathy) (Eureka Labs, ex-OpenAI) | AI excels at complex tasks while failing at simple ones — uneven capability profile |


## Tools & Infrastructure

| Term | Author | Definition |
|------|--------|------------|
| Harness | | Framework wrapping AI for controlled execution |
| MCP (Model Context Protocol) | [David Soria Parra](https://x.com/anthropaborting) & [Justin Spahr-Summers](https://x.com/jspahrsummers) (Anthropic) | Universal standard for connecting AI to external tools and data |
| Scaffolding | | Supporting structure around AI for reliable output |
| Telemetry | | Data collected by AI tools about usage patterns, performance metrics, and errors — often sent to providers for improvement, raising privacy and transparency concerns |


## Workflow Patterns & Practices

| Term | Author | Definition |
|------|--------|------------|
| Closing the Loop | | Ensuring AI output feeds back for validation and correction |
| Ralph Loop | [Geoffrey Huntley](https://ghuntley.com/) | Continuous agent loop pattern (`while :; do cat PROMPT.md \| claude-code ; done`) |
| Rate Limit Jail | | Hitting API rate limits repeatedly, blocking progress |
| Slot Machine Method | | save→run→revert→retry pattern for non-deterministic AI |
| Stop | | Knowing when to halt AI generation to avoid degradation |


## Project Types

| Term | Author | Definition |
|------|--------|------------|
| Brownfield Project | | An existing codebase or system that must be maintained, extended, or modernized — working within legacy constraints, technical debt, and established architecture |
| Greenfield Project | | A new project built from scratch with no legacy constraints — freedom to choose architecture, tools, and patterns without existing technical debt |
