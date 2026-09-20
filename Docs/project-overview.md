# Black Hole Visualizer

## Status

A local exterior prototype has been implemented from the approved Bruneton baseline.
Visual/runtime acceptance is pending; see the current checkpoint.
The workspace initially contained only this empty `Docs` directory. It does not
have a project-local Git repository; Git resolves to a parent outside the project.

## Confirmed intent

Create an interactive, highly detailed black-hole visualizer for the web.
The visitor can change their view, move closer until they experience being drawn
into the black hole, move farther away until it appears small, and change colors.
Physics accuracy is a stated requirement. The supplied image is the visual reference.

The research covers public GitHub implementations, browser rendering approaches,
and how to reproduce the reference's appearance. One Astra research lead and two
Sol researchers were requested. The selected `grill-with-docs` workflow follows
research with an interview, resolving one consequential decision at a time.

## First decision still open

Who is the first version for, and what should that visitor accomplish in their
first minute? The answer determines whether the interface prioritizes exploration,
explanation, or image creation. No audience has been assumed.

## Other unresolved requirements

- The physical model and the accuracy standard used to judge it.
- Whether camera approach means controlled movement, simulated free fall, or a
  cinematic transition, and what happens at the event horizon.
- Whether color controls change physical emission parameters, apply an artistic
  palette, or offer explicitly distinguished modes.
- Target devices, browsers, resolution, and acceptable frame time.
- Whether spin, explanatory overlays, saved views, or exports belong in scope.

## Shared terms

- **Accretion disk:** luminous material around the black hole; the requested color
  control needs to specify which visible material or display palette it changes.
- **Gravitational lensing:** curved light paths that change the apparent location
  and shape of the disk and background.
- **Schwarzschild:** the spacetime model for a nonrotating, uncharged black hole.
- **Kerr:** the spacetime model for a rotating, uncharged black hole.
- **Geodesic:** a freely traveling particle or light ray's path through spacetime.

These distinctions follow [NASA's anatomy guide](https://science.nasa.gov/universe/black-holes/anatomy/)
and the [DNGR paper](https://arxiv.org/abs/1502.03808). A simulation can be accurate
within a declared model without simulating every property of astrophysical plasma.

## Owning documents

- [Research and implementation options](library-docs.md)
- [Visual reference and interaction questions](styles.md)
- [Milestone plan](build-plan.md)
- [Current checkpoint](progress-tracker.md)

Architecture, code standards, a UI registry, and the implementation spec will be
written when the interview establishes decisions or code supplies actual facts.
