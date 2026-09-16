# CircuitCopilot Roadmap

These are **capability milestones, not hard deadlines**. Order matters more than timing: each milestone builds the foundation the next one needs, and the plan is expected to change as the project is learned into existence.

---

## M0 — Foundations

**Goal:** Establish development environment and basic engineering/software workflow.

**Learn:** Git, GitHub, commits, branches, issues, pull requests, Python environments, KiCad fundamentals, repository organization.

**Deliverable:** A clean GitHub repository and one simple KiCad PCB project. No AI.

---

## M1 — Hello, KiCad

**Goal:** Communicate with a running KiCad instance from Python.

**Learn:** APIs, the KiCad IPC API, Python bindings, client/server concepts, objects/classes, debugging.

**Example deliverable:**

```
CircuitCopilot connected ✓
Project: example-board
Components: 27
Nets: 14
```

---

## M2 — Object Awareness

**Goal:** Understand KiCad design objects programmatically.

**Potential information:** selected component, reference, value, footprint, nets, component properties, neighboring/connected components, circuit relationships.

This establishes the object-aware foundation of CircuitCopilot.

---

## M3 — Clicky UI

**Goal:** Create an interactive assistant experience.

**Potential interaction:** select a component -> CircuitCopilot automatically updates, with controls like Explain / Check / Datasheet / Ask AI.

**Learn:** GUI concepts, event-driven programming, UI state, frontend/backend interaction.

Do not overcommit to a UI framework yet.

---

## M4 — Engineering Knowledge / RAG

**Goal:** Connect engineering documentation to design context.

Start small: roughly 10–30 carefully selected authoritative documents for the components in the sample project. Do not build a massive PDF dataset first.

**Learn:** document ingestion, chunking, embeddings, vector search, retrieval, metadata, citations, RAG evaluation.

**Example:** select a component -> ask an engineering question -> retrieve the relevant datasheet section -> answer with citation/evidence.

---

## M5 — Deterministic EE Intelligence

**Goal:** Add actual engineering analysis.

**Potential tools:** `check_regulator()`, `check_power_dissipation()`, `check_led_current()`, `check_voltage_rating()`, `check_trace_current()`, `check_pullup()`, `check_decoupling()`, `check_component_limits()`.

**Core principle: AI orchestrates; engineering code calculates.**

**Learn:** engineering rule representation, tool calling, testing, validation, numerical reliability.

---

## M6 — Multi-Agent Experimentation

Only at this point formally evaluate the multi-agent architecture: Orchestrator, Design Agent, Documentation Agent, EE Analysis Agent, Tutor Agent, Vision Agent, Component/Library Agent.

**Learn:** orchestration, agent communication, shared state, tool selection, failure modes, evaluation.

Explicitly compare **multi-agent architecture** vs. **single agent + tools**. Do not assume multi-agent is automatically better.

---

## M7 — Automated Design Review

**Potential workflow:** review project -> traverse design -> run checks -> generate findings -> categorize severity -> click a finding -> highlight the relevant KiCad object -> explain evidence -> suggest a possible fix.

**Example:**

```
DESIGN REVIEW

Critical:
- regulator operating limit exceeded

Warnings:
- insufficient voltage-rating margin
- decoupling configuration requires review

Passed:
- 31 checks
```

---

## M8 — Safe Agentic Actions

**Goal:** Allow CircuitCopilot to propose modifications.

**Required pattern:**

```
AI suggestion -> deterministic/engineering validation -> preview
  -> USER APPROVAL -> KiCad modification -> re-validation
```

Do not allow unrestricted autonomous modification. Human-in-the-loop is foundational, not optional.

---

## M9 — Vision / Multimodal Engineering

**Potential capability:** legacy schematic image -> detect symbols -> identify labels -> detect wires -> infer connectivity -> construct circuit graph.

**Learn:** computer vision, multimodal LLMs, OCR, symbol detection, graph extraction, multimodal evaluation.

This may eventually become its own research-sized subproject.

---

## M10 — Advanced / Innovation Sandbox

Open-ended ideas to explore once the foundation above is solid:

- **Interactive Tutor** — teach KiCad directly in context.
- **Component Intelligence** — find suitable parts based on engineering requirements.
- **Library Assistant** — help locate/import symbols, footprints, 3D models, datasheets.
- **Reference Design Assistant** — compare designs against manufacturer reference designs.
- **PCB Review** — layout, thermal, EMI, routing, and design heuristics.
- **Natural Language Design Actions** — e.g. "Highlight everything powered by this regulator," "Show every component connected to this I2C bus."
- **Design Comparison** — "What changed between these revisions?"
- **Company Knowledge** — layer private/company engineering standards over general engineering knowledge.
- **Future EDA Integrations** — investigate other engineering tools after KiCad support is mature.
