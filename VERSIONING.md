# OBLE Versioning

OBLE versions should be independent from `Heft` engine versions.

Recommended shape:

- `draft-0`
- `draft-1`
- `draft-2`

or, later:

- `0.1-draft`
- `0.2-draft`
- `1.0`

Current version:

- `draft-0`

Compatibility statements should look like:

- `Heft 0.1.1 implements OBLE draft-0 core and the current named profiles.`

They should not imply:

- that `Heft 0.1.1` and `OBLE draft-0` are the same release
- that every Heft feature is part of the OBLE standard
- that OBLE is frozen just because Heft has a release number
