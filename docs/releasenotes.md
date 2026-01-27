# Release notes

Release names follow SemVer (MAJOR.MINOR.PATCH-PRERELEASE). Changes to major will mean either changes to API or to the database schema.

## v1.0.0-alpha.1.0

**Jan 27 2026**

- Improves edge routing by changing the pre- and postprocessing. Grouped same-side edges should no longer result in spaghetti.
- Fix SVG export when device is selected.
