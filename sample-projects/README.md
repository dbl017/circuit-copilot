# Sample Projects

This directory contains KiCad projects used to develop and evaluate CircuitCopilot.

## DAMNED

`DAMNED project demo/` is an existing, working embedded-electronics KiCad project being used as the first realistic CircuitCopilot test fixture. It predates CircuitCopilot and has been opened across more than one KiCad version, so its schematic and PCB files may report different KiCad generator versions from each other and from the currently installed KiCad release — that's expected, and is not something to "fix" by hand.

It will eventually help test:

- KiCad IPC connectivity
- board/component enumeration
- net/connectivity analysis
- component-context extraction
- engineering checks
- documentation retrieval
- object-aware assistance

