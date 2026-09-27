# THE NIGHT PORTER — Hotel Vesperine

Original first-person horror browser game (Three.js r169, WebAudio). 60 procedurally generated rooms
from a seed; all models, textures and sounds are generated at runtime (no external assets).

## Keep count
There is no room counter on screen: the only numbers are the brass plates on the doors. Every 5–8 rooms
you reach a *numbered vestibule* with 3–4 identical doors. Only the one numbered right after the last door
you opened is the real exit; the others are decoys (they rattle, and occasionally one slams back and hurts you).

## Check-in
Every run begins at the reception desk. The receptionist greets you, a short check-in dialogue plays (E to continue),
you receive your keycard, and the door to the rooms opens. After the first check-in of a session, retries start with the door open.

## What lives in the hotel
**Pacing.** The first encounter comes by room 3–4. After that a pace director makes sure something happens
every 2–3 rooms. Between the big encounters there are small scares: the lights black out, a door
slams behind you, footsteps in the corridor, a shadow crossing a doorway, whispers. The lights only flicker when the
Rush is coming (a lamp or two may waver gently when nothing is around).

**Monsters** (all original):
- **The Bellhop Rush** — the lights flicker, the rumble grows, and it charges through. You get about 5–6 s to hide in a
  wardrobe (about 7 s the first time). It never comes before room 6, is rare until room 15, and from room 15 it can turn round and charge back 1–2 more times, so if you leave the wardrobe too early, it kills you. Camera
  shake grows with how close it is: faint when it's far away, strong as it passes. The shake only moves the camera,
  never turns it, and it's capped at 3.5 cm.
- **The Portrait** — glowing eyes in a painting. It drains your health while you look at it. Look away.
- **The Night Manager** (Mr. Valmont) — a giant who patrols libraries and the archive, and sleeps in the kitchen pantry.
  He hears noise: crouch (C toggles) or walk slowly. Sprinting, slamming doors or a wrong lock combination bring him running.
  His eye is nearly blind: he only sees you up close in front of him (about 2.5 m, 1.5 m crouched) when you are not hidden.
  An intro card introduces him the first time you enter his room.
- **Housekeeping** — stay in a wardrobe too long (about 14 s) and a hand drags you out. You get a warning at 10 s.
- **Small scares** — a linen spider in some drawers and dryers, and a wardrobe that is already occupied.
- **The long corridor** — every 20 rooms, a chase with no hiding places. Chandeliers fall in front of you and carts
  block the lanes. At the end are two numbered doors; only the next number is real.

**Bellboys.** Every few rooms a pale, glowing ghost bellboy stands in a corner. He wears a red uniform with gold
piping and buttons, a pillbox hat with a chin strap and white gloves. Real ones stand straight, follow you with
their eyes, bow as you come near, and hold out a battery, lighter, key or a whispered hint ("don't hide in the next
room", "the real door is on the left"). Fakes never look at you: the head is crooked, or he faces the wall. Get
close and his neck snaps round, then he lunges. Back away or hide.

**Guide bellboys.** The linen maze rooms are pitch dark, and the three doors at the end all show the same number.
A guide bellboy walks ahead holding a lantern and beckons when you fall behind. Walk exactly where he walks: step
off his path and something in the dark pulls at you. At the end he points to the real door, and it opens.

**Task rooms**
- **Archive** — glowing books hold the 4 digits of the next door's code lock while the Night Manager patrols.
  Combination lock: ←/→ (or A/D) choose a dial, ↑/↓ or 0–9 set it, Enter tries, Esc steps away. A wrong code is loud.
- **Electrical room** — the power is out. Find 3 fuses (spares lie in the two dark rooms before it) and put them in
  the fuse box to open the electric bolt.
- **Laundry** — the key is in one of the dryers. Open a dryer (E) and take what's inside (E again). Not every
  dryer is empty.
- **Kitchen** — something sleeps in the pantry. Stay quiet: crouch, walk slowly and avoid the pots on the floor.
  The noise meter shows how close he is to waking.
- **Locked doors** — the key (an antique brass key) is hidden in the room. Using it on the heavy padlock plays a
  short animation: the key goes in and turns, the shackle pops and the lock drops to the floor.

## Run
- **Double-click `index.html`** (loads `game.js`, works from file:// and offline), or
- open **`the-night-porter.html`** — a single self-contained file (everything inlined), or
- serve the folder (`python3 -m http.server`) and open `dev.html` for the unbundled ES-module source (`src/`, import map → `vendor/three.module.js`).
- URL options: `?seed=1234` (replay a hotel), `?quality=high|medium|low`.

## Controls
WASD move · Mouse look (pointer lock) · Shift sprint (stamina) · C / Ctrl crouch (toggle: press again to stand) · E open / take / hide / step out ·
1–4 or mouse wheel select item · R use / toggle the selected item (click only captures the mouse) · Esc pause · ` (backquote) perf overlay.
Combination lock: ←/→ dial · ↑/↓ or 0–9 set · Enter try · Esc close. Fuse cabinet: 1–3 fit a fuse · Enter pull the lever · Esc close.

Mouse look: pointer-lock movement (unaccelerated where the browser supports it) is applied to the look
target on every input event. The camera follows it with very light, frame-rate-independent smoothing
(default 0.3 ≈ 20–30 ms settle; 0 = fully raw). Sensitivity (default 1.6, range 0.2–5) and Mouse smoothing
(0–1) are in the pause menu (Esc) and are saved in localStorage. If frames get slow, the render resolution
drops automatically to keep input responsive.

## Rebuild
`node build.mjs` (needs esbuild; bundles `src/` + `vendor/` + `audio.js` + `entities.js` → `game.js`, `index.html`, `the-night-porter.html`, `dev.html`).

## Credits
Character and prop models (bellboys, Night Manager, housekeeping hand, linen spider, portrait, key, padlock): Saint Micheal. Audio layer, jumpscare stings, entity intro card and task UI (combination lock, fuse cabinet, pickup toasts, bellboy whispers): Peter.
