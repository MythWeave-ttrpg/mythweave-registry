## What

<!-- New package, new version, yank, or metadata fix? Link the package. -->

## Checklist

- [ ] The manifest is at `manifests/<package-id>/package.json` and follows `schemas/package.schema.json` (see `examples/example-pack`)
- [ ] The license is an open license and the content is allowed (see the README)
- [ ] Every source URL works over https, and `sha256` and `sizeBytes` describe the exact file it serves
- [ ] The bundle contains a valid `changelog.txt` with an entry for this version
- [ ] Existing versions are untouched (versions are immutable; use `yanked` with a reason to withdraw one)
