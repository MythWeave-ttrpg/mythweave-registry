# MythWeave Registry

A static index of packs, rules plugins, and sheets for MythWeave. It holds
metadata and links only. **No package files are stored here**: every entry points
to a download that its author hosts.

Design: see `docs/registry.md` in the main
[mythweave](https://github.com/MythWeave-ttrpg/mythweave) repository.

## How it works

1. An author submits a package manifest by pull request (or opens a
   "Submit a package" issue).
2. CI validates the manifest, checks that every download URL works and matches
   the declared size and sha256, and checks the bundle's `changelog.txt`.
3. When merged, CI regenerates `index.json` from all manifests and publishes it.
   The MythWeave app downloads `index.json` and filters it by compatibility.

Versions are immutable. A bad version is **yanked** with a reason, never edited
or deleted.

## Layout

```
manifests/<package-id>/package.json   One manifest per package, versions listed in it
schemas/package.schema.json           JSON Schema for a package manifest
examples/example-pack/package.json    A filled-in example (not published)
scripts/                              Validation, link check, index generation
.github/                              Submission form, PR template, CI
index.json                            Generated. Not edited by hand
```

## Rules for entries

- Every entry has a **license**, and only openly licensed or original content is
  listed (for example SRD content under Creative Commons, ORC, original works).
- No links, https or magnet, to publisher content that is not openly licensed.
- Each version lists one or more `sources`. `https` is required in practice. A
  `magnet` source may be added, and should carry the https URL as its web seed
  (`ws=`).
- `sha256` and `sizeBytes` describe the exact file the sources serve.
- There is a takedown process: open an issue, and affected versions are yanked.

## Status

This repository is a skeleton. Schema validation, the URL checker, and index
generation will come from the shared MythWeave tooling. Until then CI only checks
that the JSON files parse.
