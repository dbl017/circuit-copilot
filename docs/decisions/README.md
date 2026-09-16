# Architecture Decision Records (ADRs)

This folder preserves **why** architectural decisions were made, not just what was decided. Code and comments show *what* the system does; ADRs show the reasoning, alternatives, and tradeoffs behind a choice, so that reasoning survives even after the decision itself is later replaced.

## When to write one

Write an ADR for a decision that would be hard or costly to reconstruct the reasoning for later — for example, choosing an LLM provider, a vector database, an agent framework, or a KiCad integration strategy. Do not write an ADR for every small choice; use judgment. Per the project philosophy, do not create unnecessary ADRs, especially during early setup.

## Format

Name files `ADR-NNN-short-title.md` (e.g. `ADR-001-example.md`), numbered sequentially.

```markdown
# Decision

## Problem
What problem are we solving?

## Options
What alternatives were considered?

## Decision
What did we choose?

## Why
Why was this chosen?

## Tradeoffs
What are the disadvantages?

## Status
Proposed / Accepted / Replaced / Deprecated
```

## Status lifecycle

- **Proposed** — under consideration, not yet acted on.
- **Accepted** — the current decision in effect.
- **Replaced** — superseded by a later ADR (link to it).
- **Deprecated** — no longer applicable, but kept for history.

No ADRs exist yet as of project initialization.
