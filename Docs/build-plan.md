# Build plan

Status markers: `[]` not started, `[*]` in progress, `[x]` completed.
This is the sole project checklist. Proposed implementation work is not authorized
by completion of the research or by selection of the interview workflow.

## Phase 1 — Research and define the experience

[x] M1 — Compare implementations and record a recommendation

Outcome: Source-backed repository, browser-rendering, and visual-reference findings.
Acceptance check: The report identifies candidates, license evidence, physical
scope, implementation costs, proposed verification, and untested assumptions.
Boundary: Public-source research and project documentation; no application code,
dependency installation, connected-account access, or runtime benchmarks.

- [x] Inspect the workspace and selected workflow instructions.
- [x] Analyze the supplied image's visible characteristics.
- [x] Compare repositories and rendering methods using one Astra lead and two Sol researchers.
- [x] Record the combined research and check document links and status claims.

[*] M2 — Establish the intended visitor and first useful outcome

Outcome: One agreed audience and first-minute user journey.
Acceptance check: The visitor, their action, and the observable successful result
are recorded in the project overview without assuming an answer.
Boundary: One interview decision; no implementation or exhaustive questionnaire.

- [] Ask the highest-impact audience/outcome question.
- [] Record the answer and identify the next consequential decision.

## Phase 2 — Define the first implementation slice

[] M3 — Agree the physical model, interaction contract, and target hardware.

Outcome: A bounded feature spec and proposed architecture.
Acceptance check: Accuracy, approach/horizon behavior, color semantics, target
browser/device, and performance conditions have explicit meanings and checks.
Keep this phase brief until M2 determines the product's purpose.

[] M4 — Select a minimal renderer experiment.

Proposed experiment: Render the shadow of a nonrotating black hole against a
simple background, expose observer distance, and compare the ray-capture boundary
with the analytic critical impact parameter, accounting for the observer-to-ray mapping. Record performance on one
named device and browser. No final disk art, full UI, spin, or horizon crossing.
This proposal may change if the interview establishes Kerr or physical infall as
the essential first outcome. Numerical formulas and suggested tolerances belong
in [the research report](library-docs.md).

## Phase 3 — Implement agreed behavior

[] M5 — Add disk appearance and view/color controls with declared physical limits.

[] M6 — Implement the agreed close-approach experience and device fallback.

[] M7 — Verify the complete agreed journey and visual acceptance criteria.

Implementation phases require selected milestones. Split them into smaller slices
when their actual scope is known; these entries are directions, not time estimates.

## Selected prototype milestone — 2026-09-20

[*] P1 — Run Bruneton's exterior renderer locally with existing controls.

User approved this slice after the research/interview proposal. Broader audience
and release questions remain open and do not block this experiment.

- [x] Vendor the upstream renderer, required disk/lookup data, source hashes, and license.
- [x] Adapt asset loading for a self-contained plain-background prototype.
- [x] Preserve viewing, inclination, and distance controls; document their meanings.
- [x] Check JavaScript syntax and binary lookup-data sizes.
- [] Verify a rendered disk, inclination changes, and decreasing apparent size with distance.
- [] Record observed performance on a named browser/device.

Boundary: local nonrotating exterior prototype using existing controls.
P1's visible-control interface is superseded by the user's P2 request. Underlying
disk and view/distance behavior were verified during P2; its original remaining
checklist is retained above as the historical boundary.

## Selected full-screen milestone — 2026-09-20

[x] P2 — Show only the black hole and verify with two Sol reviewers.

Outcome: full-screen exterior scene with no demo panels or labels, preserving
drag/scroll interaction and keyboard access.

- [x] Permanently remove panels and labels from layout and accessibility navigation.
- [x] Preserve interaction bindings and prevent hidden demo shortcuts.
- [x] Confirm a visible disk and shadow; correct overexposure found by review.
- [x] Browser-check drag, outward scroll, keyboard inclination, and Space behavior.
- [x] Obtain two Sol reviews and retain screenshots/results in verification/.

Evidence: [current checkpoint](progress-tracker.md). This milestone does not
claim Kerr, horizon-interior rendering, or complete astrophysical validation.
