# ObliviOS source overlays — index

This directory does **not** hold patch content. By design (the source patch tracking design, not published),
patch bytes live in `oblivios-platform` (non-AOSP infrastructure tooling is
kept elsewhere); duplicating them
here would immediately drift. This file is a pointer index only — one row
per known ObliviOS overlay, kept in sync manually whenever a new one is
exported.

| Component tree | Package | Approving ADR |
| --- | --- | --- |
| `frameworks/base` | `oblivios-platform/branding/boot/` | ADR-019 |
| `frameworks/base`, `system/core`, `system/sepolicy` | `oblivios-platform/credential/duress-unlock-dummy/` | ADR-040 |
| `frameworks/base` (continues the row above) | `oblivios-platform/credential/duress-unlock-decoy/` | ADR-053 (amends ADR-042) |
| `packages/apps/Updater` | `oblivios-platform/release/ota-server-url/` | ADR-052 (amends ADR-045) |

Each package's own `README.md`/`SOURCE.md` is the authoritative provenance
record (base commit, exact patch files, apply instructions) — this table
exists only so a reader starting from `oblivios-manifest` (the repository
`docs/architecture/repository-topology.md` designates as the entry point
for "local overlays") can find the real location without already knowing
`oblivios-platform`'s internal layout.

Before trusting this table, confirm it's current: `grep -c '| \`' overlays/README.md`
should equal the number of package rows above (4 as of 2026-11-16, after Guardian was removed, ADR-240); if a
patch package exists in `oblivios-platform` with no row here, this index has
drifted and needs a manual row added.
