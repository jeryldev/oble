# OBLE

OBLE stands for Open Bookkeeping Ledger Exchange.

This repository is the standalone standards home for the current OBLE draft.

Current draft version:

- `draft-0`

## What OBLE is

OBLE is an open standard for exchanging ledger meaning across:

- books
- accounts
- periods
- entries
- lines
- lifecycle and invariants
- named interoperability profiles layered on top of the core

OBLE is not an accounting engine.

It is a common language for engines, tools, migration workflows, and agents to
exchange ledger meaning without reducing everything to app-specific exports.

## Repository layout

- [spec/](spec/)
  Numbered drafts, introduction, and glossary
- [spec/why-oble.md](spec/why-oble.md)
  Purpose and positioning
- [examples/](examples/)
  Canonical draft example payloads
- [schema/](schema/)
  Draft JSON Schemas and validation guidance
- [profiles/](profiles/)
  Profile matrix and import-boundary guidance
- [conformance/](conformance/)
  Conformance checklist and current Heft implementation status

## Reading order

1. [spec/introduction.md](spec/introduction.md)
2. [spec/why-oble.md](spec/why-oble.md)
3. [spec/0000-vision.md](spec/0000-vision.md)
4. [spec/0001-core-model.md](spec/0001-core-model.md)
5. [spec/0002-lifecycle-invariants.md](spec/0002-lifecycle-invariants.md)
6. [spec/0003-counterparties-subledgers.md](spec/0003-counterparties-subledgers.md)
7. [spec/0004-serialization-conformance.md](spec/0004-serialization-conformance.md)
8. [spec/0009-classifications-and-report-structures.md](spec/0009-classifications-and-report-structures.md)
9. [spec/0010-dimensions-and-analytics.md](spec/0010-dimensions-and-analytics.md)
10. [spec/0011-budgets-and-planning.md](spec/0011-budgets-and-planning.md)
11. [spec/0012-classified-result-packets.md](spec/0012-classified-result-packets.md)
12. [spec/0013-dimension-summary-result-packets.md](spec/0013-dimension-summary-result-packets.md)
13. [spec/0014-budget-analysis-result-packets.md](spec/0014-budget-analysis-result-packets.md)
14. [spec/0015-core-statement-result-packets.md](spec/0015-core-statement-result-packets.md)
15. [spec/0016-comparative-and-equity-result-packets.md](spec/0016-comparative-and-equity-result-packets.md)
16. [spec/0017-indirect-cash-flow-and-integrity-result-packets.md](spec/0017-indirect-cash-flow-and-integrity-result-packets.md)
17. [spec/0018-translated-statement-result-packets.md](spec/0018-translated-statement-result-packets.md)
18. [spec/0019-audit-trail-and-provenance-result-packets.md](spec/0019-audit-trail-and-provenance-result-packets.md)
19. [profiles/profile-matrix.md](profiles/profile-matrix.md)
20. [conformance/conformance-checklist.md](conformance/conformance-checklist.md)
21. [conformance/profile-claims.md](conformance/profile-claims.md)

## Draft status

This repository should be treated as a working standard, not a frozen one.

The current intent is:

- `draft-0` defines the first coherent public standard surface
- `Heft` is the reference implementation candidate
- future implementations should be able to build against these artifacts
  without reading the full Heft codebase first

## License

This repository is licensed under [Apache-2.0](LICENSE).

See also:

- [STATUS.md](STATUS.md)
- [VERSIONING.md](VERSIONING.md)
- [IMPLEMENTATIONS.md](IMPLEMENTATIONS.md)
- [IMPLEMENTER_QUICKSTART.md](IMPLEMENTER_QUICKSTART.md)

## Validation

Use the local validation helper:

```bash
bash scripts/validate-oble.sh
```

That checks:

- schema/example map consistency
- JSON parsing for all examples
- selected docs cross-references

You can also use the same artifact set from the `Heft` repo by pointing its
validator at this repository:

```bash
OBLE_SOURCE=/path/to/oble-repo bash scripts/validate-oble.sh
```

## Relationship to Heft

`Heft` remains the engine and reference implementation.

`OBLE` remains the standard.

Heft should validate against OBLE artifacts, but OBLE should not become a
runtime dependency of the Heft engine.
