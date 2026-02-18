# Release notes

Release names follow SemVer (MAJOR.MINOR.PATCH-PRERELEASE). Changes to major will mean either changes to API or to the database schema.

## v1.0.0-alpha.1.2

**Feb 18 2026**

Just minor bug fixes and UI improvments.

- Adds some new icons
- Improves layout on ultrawide displays
- Fixes a bug where the container would keep crashing after a bad update to the templates repo
- Fixes a bug where multi selection selected the wrong rows on sorted tables

## v1.0.0-alpha.1.1

**Feb 5 2026**

This is a big update, focusing on performance and usability improvements when working with the cable and device list.

- Cable and device list have a unified design with excel style sorting and filtering per column
- Performance when editing cells and resizing columns is much better
- Page loads are much faster
- Tooltip for port can no longer be hovered, making it impossible to inadvertently zooming the browser when working with the wiring diagram

## v1.0.0-alpha.1.0

**Jan 27 2026**

- Improves edge routing by changing the pre- and postprocessing. Grouped same-side edges should no longer result in spaghetti.
- Fix SVG export when device is selected.
