# OBLE Profile Claims

Status: Draft

This document defines a practical way to talk about implementation status
profile by profile.

## Claim levels

### `Implemented`

The implementation has:

- real semantics for the profile
- explicit import/export or equivalent interchange behavior where appropriate
- executable tests or conformance coverage backing the claim

### `Implemented with reconstruction`

The implementation supports the profile, but some lifecycle-derived material is
not replayed blindly from imported packets.

Instead, the engine reconstructs the derived state from safe imported inputs.

This is common for:

- close/reopen-derived artifacts
- revaluation-derived artifacts

### `Export-first`

The implementation can express the profile honestly in exports, but does not
yet freeze a full import/replay contract for that profile.

### `Draft-aligned`

The implementation appears semantically aligned, but the profile boundary is
not yet strong enough to make a clean conformance claim.

## Current Heft claims

| Profile | Claim level | Notes |
| --- | --- | --- |
| `OBLE Core` | `Implemented` | Core packet export/import and round-trip verification exist. |
| `Counterparties / Open Items` | `Implemented` | Export/import and round-trip support exist. |
| `Policy / Designations` | `Implemented` | Safe user-authored policy packets round-trip today. |
| `Multi-Currency` | `Implemented with reconstruction` | Foreign-currency packets export cleanly; lifecycle-derived revaluation behavior is reconstruction-oriented on import, and translated statement results are export-first derived outputs. |
| `Close / Reopen` | `Implemented with reconstruction` | Export is explicit; imported lifecycle state is reconstructed rather than naively replayed, and integrity summaries are export-first verification outputs. |
| `Classifications / Report Structures` | `Implemented` | Heft now exposes a classification profile bundle through Zig and C export surfaces, supports session-oriented Zig import with logical-ID resolution, and also exports classified, core-statement, comparative-statement, and equity result packets as explicit derived-output layers. |
| `Dimensions / Analytics` | `Implemented` | Heft now exposes a dimension profile bundle through Zig and C export surfaces, supports session-oriented Zig import with logical-ID resolution, and also exports summary and rollup result packets as an explicit derived-output layer. |
| `Budgets / Planning` | `Implemented` | Heft now exposes a budget profile bundle through Zig and C export surfaces, supports session-oriented Zig import with logical-ID resolution, and also exports budget-analysis result packets as an explicit derived-output layer. |
| `Audit / Provenance` | `Export-first` | Heft now exports audit-trail result packets with immutable audit records and hash-chain visibility for inspection, while richer native audit internals remain engine-specific. |

## Practical downstream note

Heft's native ABI is now deliberately richer than the minimum OBLE packet
surface in a few areas that help clients implement the profiles safely:

- preview-close output for generated lifecycle entries
- structured verification diagnostics
- explicit error names/messages
- runtime-published fixed-point scales

Those helpers should be treated as implementation conveniences that make profile
claims easier to exercise and debug. They are not a substitute for the profile
packets themselves.

## Why this matters

These claim levels are more honest than a single binary statement like
`fully implements OBLE`.

They let an implementer say:

- what is truly stable
- what is available but reconstruction-oriented
- what is still export-first

That is especially important for accounting lifecycle behavior where
reconstructing derived state is often safer than replaying opaque packets.
