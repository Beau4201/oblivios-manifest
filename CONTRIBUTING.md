# Contributing

## Status

This repository is published as source only. No builds, images or update service are offered, and no device is supported. Issues can be opened where the host enables them. Pull requests are not accepted yet.

## What this repository is

The pinned upstream baseline of ObliviOS: copies of the GrapheneOS `default.xml` per release tag, the provenance record of each baseline, and an index of the patch packages in `oblivios-platform`. It holds no Android source tree, build output, vendor blob, signing material or device log.

## Rules for a change

- **Upstream copies are never edited.** A manifest copy is the `default.xml` of the tagged commit, byte for byte. A new baseline is a new copy and a new provenance record, never an edit of an old one.
- **A decision first.** A change of baseline is named by a decision record in `oblivios-docs` (`docs/governance/decision-log.md`).
- **State what is not verified.** A provenance record says which checks ran, on what, and which did not.

## Licence

Apache-2.0 (see `LICENSE` and `NOTICE`). The name ObliviOS and its logo are not licensed.

## Commits

Plain, functional, English messages in conventional-commits style.
