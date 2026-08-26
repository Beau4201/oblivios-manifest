# AegisOS source overlays — index

This directory does **not** hold patch content. Per the design at
`aegisos-foundation/docs/superpowers/specs/2026-08-25-aegisos-source-patch-tracking-design.md`,
patch bytes live in `aegisos-platform` (or, for non-AOSP infra like the
sign-vm's Caddy DNS plugin, `aegisos-foundation/tools/`); duplicating them
here would immediately drift. This file is a pointer index only — one row
per known AegisOS overlay, kept in sync manually whenever a new one is
exported.

| Component tree | Package | Approving ADR |
| --- | --- | --- |
| `frameworks/base` | `aegisos-platform/branding/boot/` | ADR-019 |
| `frameworks/base`, `system/core`, `system/sepolicy` | `aegisos-platform/credential/duress-unlock-dummy/` | ADR-040 |
| `frameworks/base` (continues the row above) | `aegisos-platform/credential/duress-unlock-decoy/` | ADR-053 (amends ADR-042) |
| `vendor/adevtool` | `aegisos-platform/guardian/patches/vendor-adevtool/` | ADR-035 |
| `device/generic/goldfish` | `aegisos-platform/guardian/patches/device-generic-goldfish/` | ADR-051 (amends ADR-033) |
| `packages/apps/Updater` | `aegisos-platform/release/ota-server-url/` | ADR-052 (amends ADR-045) |

Each package's own `README.md`/`SOURCE.md` is the authoritative provenance
record (base commit, exact patch files, apply instructions) — this table
exists only so a reader starting from `aegisos-manifest` (the repository
`docs/architecture/repository-topology.md` designates as the entry point
for "local overlays") can find the real location without already knowing
`aegisos-platform`'s internal layout.

Before trusting this table, confirm it's current: `grep -c '| \`' overlays/README.md`
should equal the number of package rows above (6 as of 2026-08-26); if a
patch package exists in `aegisos-platform` with no row here, this index has
drifted and needs a manual row added.
