# Current checkpoint

Current milestone: [P2 — Full-screen visualizer](build-plan.md), completed
2026-09-20. Work ran from 09:01 to 09:06 UTC.

## Changes

Only the black-hole canvas is visible in normal operation. Demo panels, orbit
diagram, attribution overlay, and status strip are permanently hidden. Required
upstream DOM bindings remain. Attribution is retained in the source and LICENSE.
Drag/scroll work; focused-canvas arrows and plus/minus provide keyboard controls.
Old demo shortcuts cannot restore panels or start hidden motion. Reduced exposure
and bloom make the central shadow visible. Asset errors still surface in an alert.
See [run instructions](../README.md).

## Evidence

- Isolated Chrome 153.0.8010.50 on arm64 macOS 26.5.2, viewport 1280×800.
- Real rendered disk confirmed in [final screenshot](../verification/rendered.png).
- Zero captured browser errors; normal visible body text is empty.
- Passed drag/view, outward scroll, keyboard inclination, and Space/no-panel checks.
- Outward scroll increases radius from 12.7975 to 13.4498; the
  [farther screenshot](../verification/farther.png) shows reduced apparent size.
- Thirty requestAnimationFrame intervals: median 16.7 ms, p95 16.7 ms. This is a
  short frame-callback sample, not a GPU benchmark or sustained performance claim.
- Two Sol agents independently reviewed rendering and UI/event wiring. Their
  overexposure finding was corrected and the final image independently accepted.
- [Results](../verification/browser-result.json) and
  [browser check](../verification/browser-check.cjs) are retained. The script uses
  an existing machine-local Playwright installation; it installs no dependencies.

## Next action

Review the clean scene at http://127.0.0.1:8080/prototype/. The local server is
running in session 48065; browser checks have exited. The original blank capture
was not reproduced after waiting for rendering; its historical cause is unknown.
This remains a Schwarzschild exterior renderer with a simplified disk. Physical
infall, touch interaction, cross-browser/mobile checks, and independent physics
validation are outside this completed screen-cleanup slice.
