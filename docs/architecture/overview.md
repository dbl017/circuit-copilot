# Architecture Overview

**Status: this document describes a working hypothesis, not a fixed design.** The architecture is expected to change as CircuitCopilot is built and as milestones (particularly M6) test its assumptions directly.

## North-Star Vision

> CircuitCopilot is an object-aware AI engineering assistant for KiCad that combines live design context, authoritative engineering documentation, deterministic EE tools, and multimodal reasoning to help engineers understand, validate, troubleshoot, learn, and safely modify electronic designs without leaving their EDA workflow.

The signature future interaction:

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

The important concept: **AI should understand what the engineer is currently working on without requiring the engineer to manually describe the entire circuit to a chatbot.**

## Project Philosophy

CircuitCopilot is both an engineering project and a structured learning project. Priorities, in order:

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

## Current Architecture Hypothesis (Provisional / Subject to Change)

CircuitCopilot is currently considering a multi-agent architecture:

### Orchestrator
Understands user intent and coordinates the other agents/tools.

### Design Agent
Understands the active KiCad design: components, nets, selected objects, component properties, connectivity, PCB objects, schematic relationships, project hierarchy.

### Documentation Agent
Retrieves authoritative engineering information from sources such as component datasheets, application notes, reference designs, KiCad documentation, manufacturer documentation, and selected engineering references. May eventually use RAG.

### EE Analysis Agent
Uses deterministic engineering tools rather than relying entirely on LLM reasoning. Possible future tools: regulator calculations, power dissipation, LED resistor/current calculations, voltage rating checks, trace current checks, pull-up calculations, decoupling checks, component limit checks, voltage-drop calculations, and other PCB/circuit validation.

The intended pattern: **AI decides what needs to be checked. Python/engineering code performs the calculation. AI explains the verified result.**

### Vision Agent
Possible future capabilities: schematic image understanding, legacy drawing interpretation, OCR, component/symbol detection, wire/connectivity extraction, datasheet figure understanding, and eventually physical PCB imagery.

### Tutor Agent
A potential context-aware KiCad instructor. Instead of only answering "click this menu, then this button," it may eventually understand what the user is currently doing and guide them directly in their EDA workflow.

### Component / Library Agent
Possible future functionality: component discovery, datasheet association, symbol discovery, footprint discovery, 3D model association, library assistance, alternative component suggestions, verified metadata, manufacturer/reference-design information.

**These are architectural placeholders, not a commitment.** We may later discover that fewer agents are better, that one orchestrator plus deterministic tools is better, or that different agent boundaries make more sense. That discovery is part of the learning process, and is explicitly evaluated in Milestone M6.

## Architectural Categories

### Foundational / Currently Locked

- KiCad as the initial EDA platform
- Python as the primary development language
- Git/GitHub
- Object-aware engineering assistance
- Evidence-backed engineering answers
- Deterministic EE validation where practical
- Human approval before consequential design modification
- Incremental development
- Learning rather than blindly generating software

### Current Direction

- Multi-agent architecture
- Engineering RAG / knowledge base
- Datasheet intelligence
- Design review
- Multimodal/vision support
- Context-aware tutoring
- Component/library assistance
- Copilot-like UI

### Open / Experimental

- Exact number of agents
- LLM provider
- Local vs. cloud models
- Agent framework
- Vector database
- UI framework
- Knowledge graph architecture
- Vision architecture
- Hover/select integration details
- Exact KiCad API capabilities
- Data-storage architecture
- Component database architecture
- Future EDA integrations
- ABB-specific direction
- Company/private engineering knowledge integration

These should remain editable throughout development — nothing in this category should be assumed settled.

## Relationship to KiCad

CircuitCopilot does **not** bundle or clone KiCad. KiCad is treated as an external platform/dependency that the user installs and runs separately. CircuitCopilot communicates with a running KiCad instance through KiCad's supported APIs, particularly the modern IPC API / Python bindings (see Milestone M1).
