# The Sphere

An interactive particle-field installation controlled entirely by hand gestures
through a webcam. Built as a single self-contained HTML file — no build step,
no dependencies to install.

Branded for **Maison Thai** as a table-side "while you wait" experience.

## Gestures

| Gesture | Effect |
| --- | --- |
| Move one hand | Drag and spin the sphere |
| Pinch and hold, then release | Charge a burst, then explode the particles |
| Two hands, spread or close | Grow or shrink the sphere |
| Change extended finger count (1–5) | Shifts the particle colour |
| Thumbs up | Morph the particles into the text "MAISON THAI" |

Sound is synthesised live with the Web Audio API — charge whine, explosion
noise burst, and chimes. There are no audio files.

## Running it

The page needs `localhost` or HTTPS: browsers refuse camera access
(`getUserMedia`) on a `file://` path, so opening `index.html` by double-clicking
will not work.

```bash
npx -y serve -l 5173 .
```

Then open <http://localhost:5173> and allow camera access when prompted.

## Built with

- [Three.js](https://threejs.org) 0.160.0 — WebGL particle rendering (3000 points,
  Fibonacci sphere distribution, spring physics, additive blending, trail-fade pass)
- [MediaPipe Hands](https://developers.google.com/mediapipe) — webcam hand landmark tracking
- Web Audio API — synthesised sound

Both libraries load from CDN at runtime, so an internet connection is required.

## Layout

Everything lives in [`index.html`](index.html): markup, styles, and the full
application module in one file. Tunable constants (particle count, spring
stiffness, pinch threshold, gesture sensitivity, morph text) are grouped in the
`CONFIG` block at the top of the script.
