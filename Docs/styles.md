# Visual reference and interaction direction

Status: reference analysis and proposals, not an approved interface design.

## Observed in the supplied image

The image is a wide cinematic composition, approximately 2.39:1. The dark central
region is positioned toward the right and is partially outside the frame. A bright
disk crosses diagonally from the lower left to the upper right. A broad, luminous
arc extends over the dark region, with a thinner curved band visible below it.

The disk has a cream-white luminous core, peach and orange outer layers, and fine
streaks and filaments. Dark space occupies much of the left side, with a sparse
background and a small dark foreground object. Broad glow softens the brightest
areas. The image contains no website controls, typography, or navigation.

The attachment's original provenance and reuse rights have not been established.
Treat it as a composition reference; it is not a licensed texture or an approved
website asset. The small foreground object is not a confirmed feature request.

## How to translate the appearance

The apparent arcs should arise from light-path calculations. NASA explains that
the disk's far side can appear above and below the black hole due to lensing, and
that these shapes change with viewing angle. The approaching disk side also
appears brighter and bluer. See [NASA's anatomy guide](https://science.nasa.gov/universe/black-holes/anatomy/).

Proposed rendering responsibilities:

| Visible feature | Implementation responsibility | Verification |
| --- | --- | --- |
| Dark central region and curved disk images | Relativistic ray mapping | Compare the declared model against independent numeric results |
| Diagonal sweep and off-center framing | Camera orientation, field of view, and composition | Save a reproducible camera preset and compare it to the reference |
| Fine disk filaments | Animated disk emission texture sampled at physical ray intersections | Check the same pattern remains attached to the disk while orbiting |
| Bright inner material and color variation | Declared emission and frequency-shift model | Inspect before display grading and bloom |
| Soft luminous halo | HDR exposure, tone mapping, and bounded bloom | Ensure glow does not hide the resolved shadow and thin images |
| Background distortion | Ray-mapped star/environment sampling | Orbit and approach without seams or obvious aliasing |

Procedural filaments would be an illustration of disk structure, not evidence of a
magnetohydrodynamic plasma simulation. Bloom is a display/camera effect. Neither
should be offered as proof of physical correctness.

## Proposed control meanings

The user's word "zoom" needs a precise interaction contract. Moving the camera
changes the observer's position; changing field of view magnifies the view from
the same position. An approach experience should define which operation occurs.

Orbiting, approaching, and falling are distinct camera states. Free fall requires
an observer trajectory as well as light-path calculations. An artistic transition
must be identified as such if chosen. A reset is a new simulation state, not a
physical escape from inside the horizon.

Color controls should identify their target: physical emission settings or an
artistic palette. The horizon itself is not a glowing colored surface. A proposal
is to keep the same lensing calculations in both physical and artistic displays,
with clear labels for the color interpretation.

## Decisions to resolve after audience

Desktop and mobile controls, initial camera framing, UI density, keyboard access,
reduced-motion behavior, reset behavior, and whether close approach requires an
explicit action. No UI framework, typography, or tokens are selected yet.
