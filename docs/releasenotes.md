# Release notes

Release names follow SemVer (MAJOR.MINOR.PATCH-PRERELEASE). Changes to major will mean either changes to the API or to the database schema. Be careful when updating to a new major version!

## v1.0.0-alpha.1.5

**Mar 6 2026**

- sync process no longer crashes when trying to insert a moduleType with an empty array of moduleSlotTypes

## v1.0.0-alpha.1.4

**Feb 23 2026**

Devices can now be moved between locations even after having been added to the diagram. Also bug fixes.

- Adds select inputs in location section of sidebar to move devices. API support for this as well.
- Cmd+K focuses the search bar.
- Ordering of manufacturers fixed.
- Fixes incorrect file suffix for CSV downloads on windows.

## v1.0.0-alpha.1.3

**Feb 19 2026**

Some improvements to keyboard navigation

- On the wiring diagram page Cmd/Ctrl+B triggers a relayout
- Delete can be used to delete elements (in addition to Backspace)

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
