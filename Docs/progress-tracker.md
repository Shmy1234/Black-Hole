# Current checkpoint

Current milestone: [P1 — Local exterior prototype](build-plan.md).
Started 2026-09-20 08:46 UTC. Paused at the five-minute implementation boundary.

## Changes

`prototype/index.html` adapts the downloaded Bruneton demo. The five required
lookup/noise assets are local; original source, SHA-256 manifest, and BSD notice
are retained alongside it. External font, star-catalogue downloads, and rocket
loading are removed. Blank cubemaps supply a plain black background.
Existing controls remain; drag changes look direction and Inclination changes
orbital viewing angle. Defaults aim at the hole from a stationary exterior view.
See [run instructions](../README.md).

## Evidence

- JavaScript extracted from the page passes `node --check`.
- Lookup dimensions and expected binary byte counts pass; see
  [asset checks](../verification/asset-checks.json).
- The escalated local server serves the page. Isolated Chrome produced
  [an initial screenshot](../verification/initial.png): controls appear, but no disk
  is visible in the captured frame. Chrome logged macOS display-link errors.
  This does not establish whether the cause is capture timing, headless rendering,
  or an application issue; rendering acceptance has not passed.
- No visual acceptance, frame-rate result, independent numerical validation, or
  completed milestone is claimed.

## Next action

Investigate why the initial browser capture shows no disk, then vary
Inclination, and increase distance. Record performance and any rendering errors.
Current sessions at pause: server 9079; isolated Chrome check 65010.
