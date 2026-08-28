# Cosmic Conquest — Voxel Demo

A 3D voxel-style playable preview of [Cosmic Conquest](https://github.com/majieddd/majieddd.github.io).

**The mechanics are the same.** The geometry is new.

- Pick a faction at the title (Humanity, Federation, Xeno, Pirates).
- Place units on a floating asteroid arena.
- Send waves (Enter) and defend the lane.
- The full 20-unit roster from `js/factions.js` is translated into voxel rigs:
  - **Humanity** — Trooper, Foo Fighter, Aurora, Black Manta, TR-3B
  - **Federation** — Votary, Censer, Sanctifier, Oriflamme, Luminark
  - **Xeno** — Chitling, Gnawling, Bloatpod, Hivelord, Broodmother
  - **Pirates** — Cutter, Boarder, Scrapjack, Wrecker, Ironhulk

Each unit keeps the same `shape` field as the source (block / diamond / hex / warden / vanguard / obelisk), and is built from a composition of `BoxGeometry` cubes tinted in the faction's palette from the [art bible](https://github.com/majieddd/majieddd.github.io/blob/main/docs/ART-BIBLE.md).

The arena, nebula sky, and distant voxel planets are entirely procedural — single self-contained HTML, no build step, no assets.

## How to run

Just open `index.html` in a modern browser, or serve the directory:

```sh
python3 -m http.server
```

Then visit `http://localhost:8000`.

## Controls

- **1–4**: pick a unit card
- **Click** a highlighted tile to place it
- **Enter** / **Space**: send the next wave
- **P**: pause
- **0**: recenter camera (3D scene auto-tracks, but in idle)
- **Mouse drag** (when no unit armed): orbit the scene
- **Mouse wheel**: zoom

## How the voxel rigs were translated

For each `shape` field from the source, a rig builder composes boxes into a recognizable silhouette in the faction palette:

| Shape       | Reads as                                |
|-------------|------------------------------------------|
| `block`     | humanoid line infantry / censer            |
| `diamond`   | flying wedge (Foo Fighter, Cutter)        |
| `hex`       | wide armoured walker                     |
| `warden`    | heavy anchored unit (Black Manta, Hivelord) |
| `vanguard`  | aura-broadcaster (TR-3B, Oriflamme)      |
| `obelisk`   | tall radiant column (Luminark)            |

The colours come directly from `BRAND.md` and `LOOKBOOK.md`:
`#38e8ff` cyan (Humanity), `#fbbf24` gold (Federation), `#7c3aed` violet (Xeno), `#ef4444` crimson (Pirates).

Everything is hand-typed — no asset pipeline, no model files, just a single HTML.
