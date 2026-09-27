# THE NIGHT PORTER — Hotel Vesperine

Original first-person horror browser game (Three.js r169, WebAudio). 60 procedurally generated rooms
from a seed; all models, textures and sounds are generated at runtime (no external assets).

## Keep count
There is no room counter on screen: the only numbers are the brass plates on the doors. Every 5–8 rooms
you reach a *numbered vestibule* with 3–4 identical doors. Only the one numbered right after the last door
you opened is the real exit; the others are decoys (they rattle, and occasionally one slams back and hurts you).

## Run
- **Double-click `index.html`** (loads `game.js`, works from file:// and offline), or
- open **`the-night-porter.html`** — a single self-contained file (everything inlined), or
- serve the folder (`python3 -m http.server`) and open `dev.html` for the unbundled ES-module source (`src/`, import map → `vendor/three.module.js`).
- URL options: `?seed=1234` (replay a hotel), `?quality=high|medium|low`.

## Controls
WASD move · Mouse look (pointer lock) · Shift sprint (stamina) · C / Ctrl crouch · E open / take / hide / step out ·
1–4 or mouse wheel select item · R use / toggle the selected item (click only captures the mouse) · Esc pause · ` (backquote) perf overlay.

Mouse look: pointer-lock movement (unaccelerated where the browser supports it) is applied to the look
target on every input event. The camera follows it with very light, frame-rate-independent smoothing
(default 0.3 ≈ 20–30 ms settle; 0 = fully raw). Sensitivity (default 1.6, range 0.2–5) and Mouse smoothing
(0–1) are in the pause menu (Esc) and are saved in localStorage. If frames get slow, the render resolution
drops automatically to keep input responsive.

## Rebuild
`node build.mjs` (needs esbuild; bundles `src/` + `vendor/` + `audio.js` + `entities.js` → `game.js`, `index.html`, `the-night-porter.html`, `dev.html`).
