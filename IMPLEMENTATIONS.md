# Implementations

Current reference implementation candidate:

- `Heft`

Implementation roles should stay distinct:

- `OBLE` defines the standard
- an implementation proves which parts it supports

Suggested implementation status language:

- `implements OBLE Core`
- `implements the OBLE Counterparties / Open Items profile`
- `implements the OBLE Policy/Designations profile`
- `implements the OBLE FX and Close/Reopen profiles with reconstruction-oriented lifecycle handling`

The current `Heft` repository remains the main implementation repo and should
keep:

- import/export code
- conformance tests
- semantic verification
- reconstruction helpers

The OBLE repo should remain implementation-neutral even if Heft is the first
serious reference implementation.
