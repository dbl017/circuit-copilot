# 000 — Environment Setup

**What was configured:** a local Python virtual environment (`.venv`), Git/`.gitignore` hygiene for the Python + KiCad mix this project involves, and verification that the DAMNED sample KiCad project is tracked correctly.

**Why a virtual environment?** It isolates CircuitCopilot's Python dependencies from the system-wide Python install and from unrelated projects on the same machine, so installing something here can't quietly break (or get broken by) something else.

**Important distinction:** `.venv` exists locally but is never committed to Git. The repository instead holds whatever files or instructions are needed to reproduce it (right now, that's just "run `python -m venv .venv`" — a `requirements.txt` or similar will show up once there are actual dependencies to pin).

**Current Python:** 3.13.1 is the interpreter currently used for development. No minimum supported version has been established yet — that would require actually testing compatibility across versions, which hasn't happened.

**Next concept:** the KiCad IPC API (Milestone M1) — this is the first place the project needs real, hands-on understanding rather than delegated setup work.

*Note: this environment scaffolding pass was assisted by an AI coding tool (Claude), per the AI delegation policy in `CONTRIBUTING.md`.*
