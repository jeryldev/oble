# OBLE Implementer Quickstart

This document is for people building an engine, adapter, importer/exporter, or
tool against OBLE.

If you want the shortest path in, start here.

## 1. Read the minimum set first

Read these in order:

1. [spec/introduction.md](spec/introduction.md)
2. [spec/0000-vision.md](spec/0000-vision.md)
3. [spec/0001-core-model.md](spec/0001-core-model.md)
4. [spec/0002-lifecycle-invariants.md](spec/0002-lifecycle-invariants.md)
5. [profiles/profile-matrix.md](profiles/profile-matrix.md)

That is enough to understand:

- what OBLE is for
- what counts as core
- what is profile-level
- how ambitious your first implementation needs to be

## 2. Start with OBLE Core

Do not start with every profile at once.

A first implementation should usually support:

- book
- accounts
- periods
- entry
- lines
- lifecycle state representation
- balance preservation

Use the example and schema set for the core packet first:

- [examples/core-book.json](examples/core-book.json)
- [examples/core-accounts.json](examples/core-accounts.json)
- [examples/core-periods.json](examples/core-periods.json)
- [examples/core-entry-posted.json](examples/core-entry-posted.json)
- [schema/book.schema.json](schema/book.schema.json)
- [schema/accounts.schema.json](schema/accounts.schema.json)
- [schema/periods.schema.json](schema/periods.schema.json)
- [schema/entry.schema.json](schema/entry.schema.json)

## 3. Pick profiles deliberately

The first useful profiles after core are usually:

- Counterparties / Open Items
- Policy / Designations

Add these only after core is solid.

Treat these as later:

- Multi-Currency
- Close / Reopen
- Classifications / Report Structures
- Dimensions / Analytics
- Budgets / Planning

Those profiles are real, but they carry more lifecycle nuance and
coverage and reconstruction concerns.

## 4. Validate examples early

Run:

```bash
bash scripts/validate-oble.sh
```

That checks the shipped example and schema bundle.

## 5. Make your first conformance claim narrow

Good early claim:

- `implements OBLE Core`

Better later claims:

- `implements the OBLE Counterparties/Open Items profile`
- `implements the OBLE Policy/Designations profile`

Avoid saying:

- `fully implements OBLE`

until you actually support the relevant profiles and lifecycle behavior.

## 6. Use Heft as a reference implementation, not as the spec

The current reference implementation candidate is `Heft`, but the standard
should still be read from the OBLE repo first.

Heft can help answer:

- how a real engine maps to the drafts
- how import/export packets can work in practice
- what conformance looks like in code

## 7. Keep your architecture layered

A healthy implementation split is:

- OBLE Core
- OBLE Profiles
- runtime/storage/transport details

Do not let storage details become your semantic model.
