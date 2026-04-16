# Why OBLE

OBLE exists because accounting systems often move data without moving enough of
the accounting meaning behind that data.

CSV exports, proprietary APIs, and one-off migration scripts can move rows, but
they often lose or flatten the things that matter most:

- what a book represents
- what an account means
- how periods affect lifecycle behavior
- how reversals relate to originals
- how counterparties and open items behave
- what a report result actually represents

OBLE is an attempt to define a portable accounting exchange language instead of
just another export format.

## The problem OBLE is solving

Accounting systems already exchange data, but they often do it in ways that
are:

- lossy
- proprietary
- app-specific
- weak on lifecycle semantics
- difficult to validate across tools

That makes migration, interoperability, and automation harder than they need to
be.

OBLE exists so systems can exchange:

- structure
- accounting events
- lifecycle state
- profile-specific extensions
- derived result packets

without reducing them to a lowest-common-denominator dump.

## What OBLE is

OBLE is:

- an open bookkeeping ledger exchange standard
- centered on ledger semantics, not runtime behavior
- profile-based rather than all-or-nothing
- expressed through drafts, examples, schemas, and conformance language

It covers:

- books
- accounts
- periods
- entries and lines
- lifecycle and invariants
- counterparties and open items
- multi-currency and policy surfaces
- classifications, dimensions, and budgets
- portable result packets for reports and summaries

## What OBLE is not

OBLE is not:

- an accounting engine
- a database
- a hosted ledger service
- a claim that every system must implement every profile

It is a language for exchange.

## Why not just use CSV

CSV is useful, but it is weak at conveying meaning.

A CSV file usually does not tell you enough about:

- period state
- lifecycle rules
- reversal structure
- control-account semantics
- open-item identity
- how a report result should be interpreted

OBLE tries to preserve those semantics so data can be exchanged with less
guesswork.

## Why profiles matter

Not every implementation needs the same accounting surface.

That is why OBLE is profile-based.

The core can stay small and useful, while other systems can add:

- counterparty and open-item behavior
- multi-currency behavior
- policy and designation semantics
- classifications, dimensions, and budgets
- result-packet families

This makes it easier to adopt incrementally instead of treating the standard as
an all-or-nothing commitment.

## Why the standard is separate from Heft

Heft is the reference implementation candidate.

OBLE is the standard.

That separation matters because a good standard should be useful even to people
who do not want to adopt a specific engine.

By keeping the standard separate:

- other engines can implement it
- migration tools can target it
- validators can target it
- agents and integration workflows can reason about it

without treating Heft as the only valid center of gravity.

## The short version

OBLE exists so accounting systems can exchange:

- ledger structure
- accounting events
- lifecycle state
- profile-specific meaning
- report and verification results

with less loss of meaning than a generic export gives you.

It is best thought of as:

**an open exchange language for ledger meaning, not just ledger files.**
