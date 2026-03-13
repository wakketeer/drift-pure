# DRIFT // PURE

A minimalist, single-file browser drift racing game. No dependencies, no build step — just open and race.

**[Play now → wakketeer.github.io/drift-pure](https://wakketeer.github.io/drift-pure)**

---

## Overview

DRIFT // PURE is a top-down canvas racing game built around one mechanic: drifting. Chain slides together to build multipliers, post your score to the live leaderboard, and master five hand-crafted tracks across five distinct environments.

Everything — physics, rendering, audio, UI, and leaderboard — lives in a single `index.html` file.

---

## Tracks

| Track | Subtitle | Environment | Laps | Character |
|---|---|---|---|---|
| **SHŪKAI** | The Gathering | Forest | 3 | Wide, flowing — a clean introduction |
| **MUGEN** | Infinity | Desert | 3 | Long sweeping S-curves, high speed |
| **NAGARE** | The Flow | Snow | 3 | Technical — hairpins and linked sweepers |
| **TŌGE** | Mountain Pass | Water | 2 | Wide hairpins, elevation feel |
| **KANSEI** | Perfection | Night | 3 | Grand Prix layout, varied corner radius |

Each track has a unique accent colour and atmospheric environment — rain, snow, desert heat haze, floating petals, or city stars.

---

## Cars

| Car | Style | Drift Bonus | Notes |
|---|---|---|---|
| **TOUGE** | Balanced | 1.0× | Good all-rounder to learn on |
| **KAZE** | Loose & fast | 1.3× | Light, snappy, rewarding |
| **TETSU** | Grip monster | 0.8× | Hardest to slide, highest top speed |
| **YŪREI** | Drift king | 1.5× | Made for maximum combo chaining |

---

## Scoring

Drift score accumulates while your rear tyres are sliding:

```
combo += driftAngle × speed × 0.5 × carDriftBonus × dt
```

Hold the drift longer to climb the multiplier ladder:

| Multiplier | Colour |
|---|---|
| 1× | White |
| 2× | Yellow |
| 3× | Orange |
| 4× | Red |
| 5× | Pink |

When the drift ends, `floor(combo × multiplier)` is added to your race total. Hitting a wall resets your combo — protect it.

---

## Controls

**Keyboard**

| Input | Action |
|---|---|
| `↑` / `W` | Accelerate |
| `↓` / `S` / `Space` | Brake / Reverse |
| `←` / `A` | Steer left |
| `→` / `D` | Steer right |
| `Esc` | Pause |

**Touch (mobile)**

| Zone | Action |
|---|---|
| Left side — drag left/right | Steer |
| Right side — swipe up | Gas |
| Right side — swipe down | Brake |

---

## Leaderboard

Scores are saved to Firebase Realtime Database — one entry per player per track (highest score wins). The top 5 for each track are displayed in-game.

---

## Technical

- **Single file** — all game logic, rendering, audio, and UI in `index.html`
- **Canvas 2D** rendering — no WebGL
- **Web Audio API** — procedural engine, drift, and UI sounds; no audio files
- **Catmull-Rom splines** — smooth track geometry from a small set of control points
- **localStorage** — best scores and times persist locally
- **Firebase Realtime Database** — global leaderboard

---

## Development

```bash
git clone https://github.com/wakketeer/drift-pure.git
cd drift-pure
# Open index.html in a browser — no build step required
```

Hosted on GitHub Pages. Any push to `main` goes live automatically.

---

*DRIFT // PURE — Chase the perfect slide.*
