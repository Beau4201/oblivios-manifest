# ObliviOS source overlays — index

This directory does **not** hold patch content. By design (the source patch tracking design, not published),
patch bytes live in `oblivios-platform` (non-AOSP infrastructure tooling is
kept elsewhere); duplicating them
here would immediately drift. This file is a pointer index only — one row
per ObliviOS patch package of `oblivios-platform`, with the upstream projects its patches change.

| Component trees | Package |
| --- | --- |
| `frameworks/base`, `packages/apps/Settings`, `packages/modules/Bluetooth`, `vendor/adevtool` | `oblivios-platform/airpods/` |
| `build/make`, `frameworks/base` | `oblivios-platform/branding/boot/` |
| `build/release`, `frameworks/base`, `packages/apps/Multiuser`, `packages/apps/Settings` | `oblivios-platform/credential/duress-unlock-decoy/` |
| `frameworks/base`, `system/core`, `system/sepolicy` | `oblivios-platform/credential/duress-unlock-dummy/` |
| `frameworks/base`, `system/sepolicy`, `vendor/adevtool` | `oblivios-platform/datamap/` |
| `packages/inputmethods/LatinIME` | `oblivios-platform/keyboard/autofill-chips/` |
| `packages/inputmethods/LatinIME` | `oblivios-platform/keyboard/restyle/` |
| `packages/apps/Launcher3` | `oblivios-platform/launcher/app-drawer/` |
| `frameworks/base`, `vendor/adevtool` | `oblivios-platform/memory/cached-process-cap/` |
| `frameworks/base`, `vendor/adevtool` | `oblivios-platform/memory/decoy-stop-on-switch/` |
| `vendor/adevtool` | `oblivios-platform/memory/zram-size/` |
| `frameworks/base`, `vendor/adevtool` | `oblivios-platform/passwords/` |
| `frameworks/base`, `packages/apps/Settings` | `oblivios-platform/physical/grab-detection/` |
| `frameworks/base`, `frameworks/native`, `packages/modules/Bluetooth`, `packages/modules/Connectivity`, `packages/modules/Wifi`, `packages/services/Telephony`, `system/sepolicy`, `vendor/adevtool` | `oblivios-platform/privacy/compartments-profiles/` |
| `packages/apps/Settings`, `packages/modules/Connectivity`, `packages/modules/DnsResolver`, `system/sepolicy`, `vendor/adevtool` | `oblivios-platform/privacy/exit/` |
| `frameworks/native`, `packages/modules/Wifi`, `system/sepolicy` | `oblivios-platform/privacy/identity-surface/` |
| `frameworks/base`, `packages/modules/Connectivity`, `packages/providers/MediaProvider`, `system/sepolicy` | `oblivios-platform/privacy/linkability/` |
| `frameworks/base` | `oblivios-platform/privacy/screenshot-detection/` |
| `packages/apps/Updater` | `oblivios-platform/release/ota-server-url/` |

Each package's own `README.md`/`SOURCE.md` is the authoritative provenance
record (base commit, exact patch files, apply instructions, approving ADRs) — this table
exists only so a reader starting from `oblivios-manifest` can find the real location without already knowing
`oblivios-platform`'s internal layout.

Before trusting this table, confirm it's current: `grep -c '| \`' overlays/README.md`
should equal the number of package rows above (19 as of 2026-11-16, the number of patch packages of `oblivios-platform`); if a
patch package exists in `oblivios-platform` with no row here, this index has
drifted and needs a manual row added. The SBOM of `oblivios-docs` (`sbom/`) is built from the same mapping and fails when a package has no row.
