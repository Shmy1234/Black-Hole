# Black Hole — exterior prototype

Run from this directory:

```sh
python3 -m http.server 8080 --bind 127.0.0.1
```

Open http://127.0.0.1:8080/prototype/ in a desktop browser with WebGL2.

- Drag to look around; use **Inclination** to change the orbital viewing angle.
- Scroll to change observer distance. **Stop** motion first if the distance is locked.
- Use Exposure, Bloom, and Disc Temperature to explore the existing renderer.
- Press Space to hide/show controls. Reload without URL parameters to reset.

This is a local adaptation of Eric Bruneton's Schwarzschild renderer, not a new
physics implementation. It models a nonrotating black hole and a simplified disk.
The background is plain black; stars and the rocket are disabled for this slice.
The upstream drag control changes camera direction, not the observer's orbit.
The original motion controls remain experimental and do not establish correct
horizon-interior rendering. No independent physical-accuracy claim is made.

The shader and data come from https://ebruneton.github.io/black_hole_shader/demo/demo.html.
`prototype/upstream-demo.html` is the unmodified downloaded page;
`prototype/upstream-manifest.json` records source/data SHA-256 hashes.
`prototype/LICENSE` preserves the upstream BSD notice. The app loads its required
assets locally and no longer requests the external font or star catalogue.

Verification and remaining acceptance checks are recorded in
[Docs/progress-tracker.md](Docs/progress-tracker.md).
# Black-Hole
