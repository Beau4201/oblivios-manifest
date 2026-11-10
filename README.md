# oblivios-manifest

The pinned upstream baseline of ObliviOS: which GrapheneOS and AOSP
revisions the patches of `oblivios-platform` apply to, and the record of how
each baseline was chosen.

## Contents

- `manifest/upstream-<tag>.xml` is `default.xml` of the GrapheneOS repository
  `platform_manifest` at the commit of the GrapheneOS tag `<tag>`, byte for
  byte. It lists every upstream project with the revision to check out.
- `provenance/<tag or build number>.md` records for each baseline or build the tag, the commit it
  resolves to, the signature check of the tag, the hash of the manifest copy, and
  what was built and verified from it.
- `overlays/README.md` is an index of the patch packages in
  `oblivios-platform`.

## Verify a baseline

The manifest is only a copy. Check it against upstream: resolve the tag in
`https://github.com/GrapheneOS/platform_manifest`, verify the tag signature with
the allowed signers that GrapheneOS publishes, and compare `default.xml` at that commit with the copy in `manifest/`, whose SHA-256
is recorded in `provenance/<tag>.md`.

## Stage

Source only. No builds, images or update service are offered, and no device is
supported.

## Licence

Apache-2.0 for the overlays and the provenance records, see `LICENSE` and
`NOTICE`. The manifest copies keep the licence of their upstream, see `NOTICE`.
The name ObliviOS and its logo are not licensed.
