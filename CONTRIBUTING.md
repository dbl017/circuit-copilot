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

## Development Environment

Current development setup:

- OS: Windows, shell: PowerShell
- Python: **3.13.1** (current development interpreter)
- KiCad: 10.0
- Editor: VS Code (not an architectural dependency — just what's currently in use)
- Dependencies: a local `.venv` isolates CircuitCopilot's Python packages from system/global Python. It is created locally and is never committed (`.gitignore` excludes it); the repository holds whatever files/instructions are needed to reproduce it.

**Python 3.13.1 is the version currently used for development — it is not yet a stated minimum supported version.** No compatibility testing across Python versions has been done, so don't assume `Python >= 3.13` is required until that's actually established.

Application dependencies are intentionally not installed yet. The first real dependency, `kicad-python`, arrives with Milestone M1 (see `ROADMAP.md`) as a deliberate, hands-on learning step rather than something to front-load during setup.

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

**Appropriate AI delegation** — things AI assistants can reasonably handle directly:

- repository scaffolding
- environment setup
- repetitive configuration
- formatting
- documentation maintenance
- boilerplate
- code review
- debugging assistance

**Learning-critical work** — should be developed progressively, by me, with actual understanding, even when AI could technically produce it faster:

- KiCad IPC communication
- the KiCad object model
- circuit connectivity representation
- deterministic engineering analysis
- retrieval architecture
- agent/tool architecture
- multimodal processing
- safe design modification

This isn't a ban on AI-generated code in those areas — it's a commitment that the important architecture and engineering behavior stays something I can explain, not just something that exists.

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
