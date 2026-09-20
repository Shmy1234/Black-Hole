# Black-hole web renderer research

Research date: 2026-09-20. One Astra lead coordinated two Sol researchers, covering
repositories and browser/physics options. The main agent inspected the workspace,
analyzed the supplied image, cross-checked key sources, and assembled this report.

Evidence is public documentation, selected source/license inspection, and research
papers. No candidate was installed, run, benchmarked, or independently numerically
validated. Rankings express suitability for this project, not universal quality.
No dependency versions or commit hashes are pinned; do so before implementation.

## Recommendation

Use **Bruneton's WebGL2 Schwarzschild renderer as the first exterior-view
experiment**, conditional on the interview confirming that a nonrotating exterior
view is a useful first slice. It has a documented method, reusable shader core,
and an inspected license. It offers a stronger starting point than independently
inventing approximate light bending from an attractive screenshot.

If rotating Kerr geometry or physical horizon crossing is essential immediately,
evaluate a direct geodesic renderer before adopting that foundation. Neither is a
routine switch on a nonrotating lookup-table implementation. This recommendation
is a proposed experiment, not an approved stack or a guarantee of target performance.

## GitHub shortlist

| Candidate | Best use | Evidence | Limits and reuse status |
| --- | --- | --- | --- |
| [ebruneton/black_hole_shader](https://github.com/ebruneton/black_hole_shader) | Preferred documented exterior baseline | WebGL2 implementation of a published nonrotating beam-tracing method | Schwarzschild; not an established Kerr/interior solution. BSD-3-Clause license text inspected. |
| [kotsoft/fable-experiments](https://github.com/kotsoft/fable-experiments) | Kerr feasibility candidate and tutorial reference | README describes Schwarzschild and Kerr renderers, orbit/zoom, and validation code | Experimental; claims not independently reproduced. README and GitHub declare MIT, but full license file fetch failed. |
| [oseiskar/black-hole](https://github.com/oseiskar/black-hole) | Simpler numerical comparison and learning reference | WebGL/Three.js Schwarzschild ODE integration with documented limitations | Older implementation; MIT project code, separately licensed libraries and background asset. |
| [kyleyhw/black_hole](https://github.com/kyleyhw/black_hole) | Feature and architecture research | Project advertises Kerr–Schild integration, falling camera, and validation | No license located in this review; do not adopt its code on the basis of public visibility. |
| [richafltr/kerr-blackhole](https://github.com/richafltr/kerr-blackhole) | Descent and moving-camera research | Project describes GPU light transport and a falling probe | No license located; project documentation includes unfinished validation/profiling work. |

### Why Bruneton leads

The method precomputes ray/scene intersections into lookup tables and filters
light sources over beams, helping resolve narrow features and stars. Its generic
GLSL core is separated from the demonstration interface. Preprocessing is a
separate build concern: the published build uses C++ tooling and dependencies,
so this is not simply an npm component installation. The demo also includes
camera/orbit state, relativistic effects, and appearance controls. See the
[author's implementation documentation](https://ebruneton.github.io/black_hole_shader/).

The [paper](https://ebruneton.github.io/black_hole_shader/paper.pdf) uses spherical
symmetry to make the rendering practical; it treats a simplified thin disk and
leaves Kerr and interior-horizon extensions for future work. A reusable physical
model still has explicit limits. More detailed disk textures do not extend those
limits or turn the renderer into a fluid simulation.

The [BSD-3-Clause license](https://github.com/ebruneton/black_hole_shader/blob/master/LICENSE)
was read. Retain its notices and conditions when reusing code. Inventory separate
assets and submodules before copying a complete demo into the website.

### Where the other candidates help

Fable's [README](https://github.com/kotsoft/fable-experiments) describes a Kerr
Hamiltonian integrator in Cartesian Kerr–Schild coordinates, RK4 integration with
numerical gradients, and spin-dependent disk geometry. It points to
[`scripts/validate-kerr.mjs`](https://github.com/kotsoft/fable-experiments/blob/main/scripts/validate-kerr.mjs).
That makes it worth a bounded audit if rotation matters. Neither the README's
accuracy language nor the existence of a validation script establishes that its
rendered output meets this project's requirements. Full license text and shader
behavior still need verification before reuse.

Oseiskar's [README](https://github.com/oseiskar/black-hole) explicitly reports
excess bending at low solver step counts and star-sampling artifacts. That candor
makes it a useful reference for numerical failure cases. Its
[copyright inventory](https://github.com/oseiskar/black-hole/blob/master/COPYRIGHT.md)
states that the Milky Way image uses CC-BY-NC 2.0, separately from the MIT project
code. Replace that asset or establish permitted use if adopting the renderer.
Do not treat the entire repository as uniformly MIT-licensed.

## Browser implementation options

| Method | Practical advantage | Main cost | Fit here |
| --- | --- | --- | --- |
| Precomputed Schwarzschild ray/beam tables | Bounded per-pixel lookup work; documented path to stable images | Preprocessing, table precision, restricted physical model | Best initial candidate if exterior/nonrotating scope is acceptable |
| Direct Schwarzschild geodesic integration | Relatively accessible equations and an independent comparison method | Step count, error control, expensive near-critical rays | Useful for learning, validation, or a small alternate prototype |
| Direct Kerr geodesic integration | Handles rotating spacetime; can support a broader camera model | More complex equations, numerical stability, observer frames, GPU cost | Evaluate first if spin or physical descent is essential |
| Ordinary mesh with glow and distortion | Quick composition experiment | Cannot establish correct light capture, multiple images, or camera behavior | Visual mockup only; fails the requested physics foundation |

The first row follows [Bruneton's method](https://arxiv.org/abs/2010.08735).
The numerical options are demonstrated by the repositories above. The suitability
and cost judgments are our engineering assessment, not measured performance.

**WebGL2 first is a proposal.** A fullscreen fragment shader can map camera rays
to the disk/background, with separate render targets for postprocessing.
[WebGL2's specification](https://registry.khronos.org/webgl/specs/latest/2.0/)
defines the rendering facilities. [WebGPU](https://www.w3.org/TR/webgpu/) also
provides compute and storage resources, useful for more flexible work scheduling
or progressive still rendering. Those capabilities do not guarantee faster black
hole rendering. Actual API availability, limits, precision behavior, and device
performance must be tested on the chosen targets.

Keep the initial application shell small. A framework is not responsible for
relativity; it should manage controls and page state around a rendering module.
No React, Three.js, build tool, or framework version is selected yet. Reuse the
candidate's native rendering path for the first experiment before adding a wrapper.

## Proposed rendering responsibilities

1. **Physical scene parameters:** mass/length units, spin if applicable, disk
   bounds, emission assumptions, and a finite supported parameter range.
2. **Observer:** position, orientation, field of view, and velocity/local frame
   when simulating motion. Distance changes and field-of-view changes are separate.
3. **Light transport:** determine whether a ray reaches the disk, background, or
   capture region; account for the declared frequency/intensity model.
4. **Emission:** evaluate disk structure at ray intersections. Animate procedural
   filaments in disk coordinates so they remain coherent when orbiting.
5. **Display:** exposure, tone mapping, antialiasing, and bloom after light transport.
6. **Controls and diagnostics:** pass bounded values to the renderer, expose a
   reproducible camera preset, and record quality/performance settings.

This is a proposed separation of responsibilities, not existing code. Disk
temperature and color depend on the emission assumptions and observation band;
arbitrary hue should be described as an artistic palette. A physical view could
expose temperature/exposure while an artistic view adds palette and bloom controls.
The interview must approve those semantics before UI implementation.

## Matching the supplied image

The [visual analysis](styles.md) owns the composition details: oblique disk,
off-center dark region, bright upper arc, thin lower image, cream/peach emission,
filaments, broad glow, and sparse surroundings. A shader should generate the
lensed images from the same disk instead of placing a separate ring above it.

The [Interstellar renderer paper](https://arxiv.org/pdf/1502.03808) describes both
relativistic rendering and deliberate cinematic choices, including suppressed
Doppler color/brightness shifts and added lens flare. It is an explanation of
methods, not a browser-ready implementation. The supplied image resembles that
visual language; its provenance has not been verified.

Our recommendation is to preserve the physical ray paths while allowing clearly
identified artistic display settings. Judge lensing with bloom disabled, then
judge the desired composition and glow separately. For temporal quality, inspect
camera movement and animated disk structure; one screenshot cannot reveal flicker.

## Approach, zoom, and falling

For an inspection camera, changing distance at fixed field of view produces a
different observation point. Changing field of view merely changes framing at
the same point. A possible interaction is scroll-to-approach plus a deliberate
Dive action, but this remains a proposal.

True free fall needs a timelike observer trajectory and a correctly moving local
camera frame alongside the null light rays. An orbit controller is not itself a
free-fall model. Exterior lookup code cannot be assumed valid after crossing its
documented domain.

NASA's [horizon-crossing simulation description](https://www.nas.nasa.gov/SC24/research/project19.php)
states that the camera can still see the exterior sky after entering the horizon.
An automatic black screen at that boundary would therefore be a storytelling
choice, not a general prediction of what the falling observer sees. The separate
[NASA journey article](https://science.nasa.gov/universe/black-holes/supermassive-black-holes/new-nasa-black-hole-visualization-takes-viewers-beyond-the-brink/)
distinguishes an escaping trajectory from a plunging one. Its offline rendering
cost is not a browser benchmark or proof that every interactive approximation
requires a supercomputer.

If physical crossing is required, test a formulation that remains well behaved at
the horizon and validate the observer frame. Define where the simulated journey
ends. A reset starts a new state; it does not depict escape from within the horizon.

## Turning accuracy into observable checks

The phrase "super detailed and physics accurate" needs two independent standards:
image quality and error within a declared physical model. The following are
proposed checks, not passed tests or accepted numerical tolerances.

| Check | Evidence to collect | What it establishes |
| --- | --- | --- |
| Schwarzschild capture boundary | With geometric units G=c=1, compare the critical impact parameter to b_c = 3√3 M = (3√3/2) r_s | A basic capture/lensing check; impact parameter is not automatically the screen-space radius for a nearby camera |
| Numerical convergence | Reduce integration step size, or increase table precision/resolution, and compare selected rays | Whether the solution stabilizes, especially near the critical boundary |
| Solver invariants | Evaluate the null constraint and applicable conserved quantities | Covered numerical consistency, not all image physics |
| Camera-frame consistency | Check normalization and the frame's relation to observer velocity | A prerequisite for reliable moving-observer effects |
| View continuity | Sweep face-on, oblique, and edge-on views; approach and retreat | Discontinuities, seams, clipping, unstable thin features, or invalid values |
| Relativistic display | Compare approaching/receding sides before tone mapping; document the spectral model | Whether stated frequency/intensity behavior survives the rendering pipeline |
| Kerr extension | Recover the zero-spin limit and compare appropriate critical curves | Spin implementation checks beyond an attractive asymmetric silhouette |
| Infall extension | Check a trajectory and frame across the horizon in suitable coordinates | Continuity within the chosen model, not realism of an arbitrary ending |

The capture threshold is documented in the
[Fable mathematical tutorial description](https://github.com/kotsoft/fable-experiments)
and the Schwarzschild methods above. Compare screen-space measurements using the
actual observer model; do not confuse horizon radius, photon-sphere radius, and
apparent shadow size. Independent validation should use a separate derivation or
reference solver rather than copying the shader's equations into a matching test.

## Smallest useful renderer experiment

Suggested outcome: determine whether the exterior baseline is suitable before
investing in final artwork or a control system. The
[plan](build-plan.md) proposes starting with a simple background and capture
boundary; a subsequent oblique disk preset can assess the image structure.

Record the device/GPU, OS, browser, framebuffer resolution, device-pixel ratio,
quality settings, warmup, and a repeatable camera path. Measure median and p95 frame
intervals and report loading/preprocessing separately. Agree a required budget
after the target device is known. Published repository FPS claims are not results
for this project.

Potential quality controls include framebuffer scale, integration/table quality,
star filtering, and postprocessing cost. Reduce display work before silently
loosening a promised numerical accuracy bound. Check context/device loss and
unsupported API behavior when implementing the browser shell. No fallback design
or supported-device promise has been agreed yet.

## Decisions that change the recommendation

First resolve the intended visitor and their first useful outcome. Then resolve
whether rotation and literal horizon crossing belong in the first release, the
physical meaning of color controls, and target devices. These determine the
implementation boundary. No application work should infer answers from the
reference image alone.
