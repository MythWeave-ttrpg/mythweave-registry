# Scripts

Planned, not written yet. They will come from the shared MythWeave tooling so the
registry, the template repositories, and the app all use the same validation code
instead of copies of it.

| Script | What it does |
| --- | --- |
| validate | Check every `manifests/*/package.json` against `schemas/package.schema.json` and the structural rules (hash, size, source shape, yanked reason) |
| check-links | For every source: success status over https only, size matches `sizeBytes`, sha256 matches, bundle manifest matches the entry, `changelog.txt` parses |
| build-index | Generate `index.json` from the validated manifests, adding each version's changelog section |

The same checks run on submission and on a schedule (link rot). A failed
scheduled check marks the version unavailable in the next index and opens an
issue for the author. It never deletes an entry.
