# CircuitCopilot

Object-aware AI engineering copilot for KiCad combining live design context, engineering documentation, deterministic EE analysis, and safe AI-assisted design workflows.

## Vision

> **CircuitCopilot is an object-aware AI engineering assistant for KiCad that combines live design context, authoritative engineering documentation, deterministic EE tools, and multimodal reasoning to help engineers understand, validate, troubleshoot, learn, and safely modify electronic designs without leaving their EDA workflow.**

The signature interaction CircuitCopilot is working toward:

```
Engineer
  -> hover/select component in KiCad
  -> CircuitCopilot automatically understands the selected object
  -> understands circuit/connectivity context
  -> retrieves authoritative documentation
  -> performs deterministic EE analysis when appropriate
  -> AI explains the result
  -> suggests an engineering action
  -> previews the change
  -> engineer approves
  -> KiCad action occurs
```

The core idea: **AI should understand what the engineer is currently working on without requiring the engineer to manually describe the entire circuit to a chatbot.**

This vision is a working hypothesis and is expected to evolve as the project is built and learned from.

## Why This Project?

General-purpose chatbots can already answer electronics questions, but they have no direct awareness of the object currently selected in an EDA tool, the design's connectivity, the project's state, component relationships, or the engineer's workflow context. CircuitCopilot explores what changes when AI is brought directly into the engineering workflow itself, instead of living in a separate chat window that has to be told everything by hand.

## Core Principles

- Object-aware: understand the design and the selected object, not just free text.
- Evidence-backed: engineering answers should cite authoritative sources.
- Engineering validation: deterministic calculations where practical, not just LLM reasoning.
- Human-in-the-loop: the engineer approves consequential design changes.
- Incremental: build and learn one capability at a time.
- Learning-oriented: understanding the system matters as much as the system working.

See [`docs/architecture/overview.md`](docs/architecture/overview.md) for the full philosophy and architectural categories.

## Current Status

**M0 — Foundations.**

This project is in very early development. No application functionality exists yet: there is no KiCad connection, no agents, no RAG, and no UI. The repository currently contains project structure, documentation, and a roadmap only. See [`progress/CURRENT.md`](progress/CURRENT.md) for the active sprint.

## Proposed Architecture

CircuitCopilot is currently exploring a multi-agent architecture (Orchestrator, Design Agent, Documentation Agent, EE Analysis Agent, Vision Agent, Tutor Agent, Component/Library Agent). **This is provisional and subject to change** — see [`docs/architecture/overview.md`](docs/architecture/overview.md) for details, and note that fewer agents, or a single agent with deterministic tools, may turn out to be the better design. That comparison is itself a planned milestone (M6).

## Roadmap

See [`ROADMAP.md`](ROADMAP.md) for the full milestone plan, from M0 (Foundations) through M10 (Advanced / Innovation Sandbox).

## Learning Project

CircuitCopilot is both an engineering project and a structured learning project. It is being built progressively, on purpose, to learn: EDA automation, KiCad APIs, Python software engineering, Git/GitHub practices, AI/RAG, agent design, multimodal AI, and engineering validation. AI coding assistants are used as pair programmers, reviewers, and instructors — not as a way to generate the whole application at once. See [`CONTRIBUTING.md`](CONTRIBUTING.md) for the AI assistant policy and [`docs/learning-log/`](docs/learning-log/README.md) for what's been learned along the way.

## Repository Structure

```
circuit-copilot/
├── README.md, ROADMAP.md, CONTRIBUTING.md, LICENSE
├── docs/            architecture, decision records, research notes, learning log
├── progress/        current sprint, milestone tracking, idea backlog
├── src/circuitcopilot/   kicad/, agents/, knowledge/, engineering/, vision/, ui/
├── tests/           engineering/, retrieval/, agents/
├── examples/        small runnable examples
├── sample-projects/ sample KiCad projects used for development
└── data/            manifests and small permitted sample data (see data/README.md)
```

## Safety / Engineering Disclaimer

CircuitCopilot is experimental engineering software and should not be relied upon for safety-critical design decisions without independent professional verification.

## License

[MIT](LICENSE)
