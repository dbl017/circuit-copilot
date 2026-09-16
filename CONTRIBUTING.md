# Contributing to CircuitCopilot

CircuitCopilot is a solo learning and portfolio project, but it follows real engineering practices from day one so the habits (and the Git history) hold up in an interview or a real team later.

## Project Philosophy

1. Understand what we build.
2. Build incrementally.
3. Maintain good Git/GitHub practices.
4. Use AI coding assistants as pair programmers rather than automatic app generators.
5. Keep engineering calculations deterministic where practical.
6. Use AI for language understanding, retrieval, orchestration, explanation, and multimodal reasoning.
7. Keep engineers in control of design modifications.
8. Preserve evidence/provenance for engineering information.
9. Test important engineering behavior.
10. Allow the architecture to evolve as we learn.

The current architecture (see `docs/architecture/overview.md`) is **not permanent**. It is a hypothesis to be tested and revised.

## AI Coding Assistant Policy

AI tools such as Claude, ChatGPT, Codex, and GitHub Copilot may be used throughout this project. However:

AI should function as:

- an instructor
- a pair programmer
- a debugger
- a reviewer
- a brainstorming partner
- a documentation assistant
- a test assistant

AI should **not** be used to blindly generate the entire application.

Before accepting substantial AI-generated code, the goal is to understand:

- what it does
- why it exists
- how it interacts with the architecture
- its major dependencies
- its important failure modes

The bar: I should be able to confidently explain any part of this project in an engineering interview.

## Engineering Safety Philosophy

Consequential design actions follow this pattern:

```
AI agent
  -> proposed engineering action
  -> deterministic validation where possible
  -> preview
  -> human approval
  -> KiCad action
  -> re-validation
```

Never:

```
LLM -> unverified modification
```

Important engineering calculations should eventually have unit tests. AI-generated engineering explanations should preserve source evidence when they are based on documentation.

## Git Strategy

Primary branch: `main`.

Feature branches follow `feature/<short-description>`, e.g.:

- `feature/kicad-connection`
- `feature/component-reader`
- `feature/copilot-ui`
- `feature/datasheet-rag`
- `feature/ee-tools`
- `feature/design-review`

Typical workflow:

```
Issue -> branch -> learn -> implement -> test -> review -> commit -> merge
```

Avoid unnecessary Git complexity while the project is small.

## Commit Philosophy

The Git history should show actual development, not noise.

Avoid commit messages like: `update`, `stuff`, `fix`, `works now`, `final`, `final-final`.

Prefer descriptive, meaningful messages, e.g.:

- `Initialize CircuitCopilot project structure and roadmap`
- `Add KiCad IPC connection prototype`
- `Extract PCB component metadata`
- `Add component connectivity representation`
- `Implement selected-component context`
- `Add datasheet ingestion pipeline`
- `Add regulator thermal validation`

Prefer small, meaningful commits over large, unreviewable ones.

## Architecture Decision Records

Significant architectural decisions are documented in `docs/decisions/` as ADRs. See `docs/decisions/README.md` for the format. Not every choice needs an ADR — use judgment for decisions that would be hard to reconstruct the reasoning for later.

## Learning Log

`docs/learning-log/` documents what is learned while building CircuitCopilot. See that folder's README for the entry format.
