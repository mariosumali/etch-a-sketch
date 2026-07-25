# Etch A Sketch

A browser-based Etch A Sketch. Same idea as the toy: two knobs, one line, no undo.

![Idle screen](screenshots/idle.png)

## Try it

Open `Etch.dc.html` in a browser. That's it — no build step, no install.

## Controls

- **A / D** or **←/→** — move horizontal
- **W / S** or **↑/↓** — move vertical
- Drag the knobs directly with your mouse or finger, they have real momentum
- **Hold Space** — shake the whole thing and erase the screen
- Shaking the mouse back and forth fast enough also triggers an erase
- On a phone or tablet with a motion sensor, physically shaking the device erases it too

![Mid-doodle](screenshots/doodle.png)

Needs a keyboard to draw, so on touch-only phones it just shows a note telling you to grab a laptop or a tablet with one attached.

## How it works

It's one HTML file. The knobs, the case, the aluminum-powder screen texture, the shake-to-erase animation — all drawn with CSS and a `<canvas>`, driven by a small React component. Lines snap to a grid as you draw, which is what gives diagonals their stair-stepped look, just like the real thing.

`support.js` is the runtime that loads React and Babel and mounts the component defined inside `Etch.dc.html`.
