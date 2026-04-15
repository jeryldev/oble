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
| `Counterparty / Open Item` | `Implemented` | Export/import and round-trip support exist. |
| `Policy / Designations` | `Implemented` | Safe user-authored policy packets round-trip today. |
| `Multi-Currency` | `Implemented with reconstruction` | Foreign-currency packets export cleanly; lifecycle-derived revaluation behavior is reconstruction-oriented on import. |
| `Close / Reopen` | `Implemented with reconstruction` | Export is explicit; imported lifecycle state is reconstructed rather than naively replayed. |
| `Classifications / Report Structures` | `Export-first` | Heft now exposes a classification profile bundle through Zig and C export surfaces, while import remains Zig-first and the broader packet/examples/schema story is still emerging. |
| `Dimensions / Analytics` | `Export-first` | Heft now exposes a dimension profile bundle through Zig and C export surfaces, while import remains Zig-first and the broader packet/examples/schema story is still emerging. |
| `Budgets / Planning` | `Export-first` | Heft now exposes a budget profile bundle through Zig and C export surfaces, while import remains Zig-first and the broader packet/examples/schema story is still emerging. |

## Why this matters

These claim levels are more honest than a single binary statement like
`fully implements OBLE`.

They let an implementer say:

- what is truly stable
- what is available but reconstruction-oriented
- what is still export-first

That is especially important for accounting lifecycle behavior where
reconstructing derived state is often safer than replaying opaque packets.
