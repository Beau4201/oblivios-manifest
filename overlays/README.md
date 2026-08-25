# AegisOS source overlays

This directory is the designated source-of-truth location for local AegisOS
overlays/patches against the pinned upstream manifest
(`../manifest/upstream-2026071500.xml`), per
`aegisos-foundation/docs/architecture/repository-topology.md`'s integration
rules. It does not yet hold any actual patch content — see the gap below.

## Known overlays (tracked elsewhere, not mirrored here)

- `frameworks-base-boot-background.patch`, `frameworks-base-boot-framerate.patch`
  (ADR-019, boot-identity) — tracked as files in
  `aegisos-platform/branding/boot/patches/`. Applied to the build server's
  `platform-primary/frameworks/base` checkout as local git branch
  `aegisos-boot-identity` (commit `7d7001f9c4e4`).

## Known overlays with NO tracked-repo copy anywhere (open gap)

The following AegisOS changes exist **only** as local git branches inside
individual AOSP component checkouts on the build server
(`/srv/aegisos/platform-primary/...`), each with `origin`/`grapheneos` still
pointing at the upstream GrapheneOS repo (fetch+push) and no AegisOS-owned
remote configured at all. They are not exported as `.patch` files, not
mirrored here, and not tracked in any repository this project controls:

- `frameworks/base` branch `aegisos-duress-decoy-switch` (commit `bc0f20e0`)
- `frameworks/base` branch `aegisos-duress-dummy-primitive` (commit `e6e5746`)
- `packages/apps/Updater` branch `aegisos-ota-server` (commit `7a0d44d`,
  points the Updater app at the private lynx OTA server instead of
  `releases.grapheneos.org`)

This means: if the build server's disk is lost, this history is gone (it is
re-derivable from decision-log prose, but that is not a real backup); no one
other than the current operator can review, diff, or reproduce these changes
without SSH access to that one VM; and `aegisos-manifest`'s own stated role
as "source of truth for local overlays" is not currently being honored for
this class of change. Revisit before any second operator, external
reviewer, or CI system needs to touch AegisOS source patches.

## Provenance-record gap

`provenance/` currently holds only the record for the original manifest
sync (`2026071500.md`). Later AegisOS build revisions built from this same
manifest tag are not individually recorded here — see
`provenance/2026082417.md` for the one exception added so far (the
`OFFICIAL_BUILD=true` fix, ADR-047), and its own note on the remaining gap.
