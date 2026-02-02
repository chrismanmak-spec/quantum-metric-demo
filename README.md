# Quantum Metric Demo — Unified Quantum Geometry Observables

A compact interactive demo visualizing how an emergent "Quantum Metric" can distort carrier trajectories and produce observable effects across transport, optical, and spin observables. This repository contains a single-page static demo (index.html) that drives a canvas-based particle simulation and a Chart.js panel that maps metric strength to observable signals.

This project is intended as an educational / demonstrative visualization and prototyping playground for geometric electronic effects (e.g., geometric Hall-like responses, circular dichroism, and spin-momentum locking) rather than production-ready physics software.

## Live demo
- The demo entrypoint is `index.html` at the repository root. Once the repository is deployed (GitHub Pages or a static server) that file is the UI and visualization.

## Features
- Interactive metric slider controlling a "Quantum Metric" strength (0.0–1.0).
- Three observable modes: Transport (non-linear Hall / geodesic steering), Optical (circular dichroism-like response), and Spin (spin-momentum locking visualization).
- Multi-nucleus particle systems (He-4, Li-11, Fe-56) with per-nucleus halo intensity (psiMinus) driving halo leakage heatmaps.
- Chart.js panel showing a qualitative mapping of metric strength to observable signal.

## How to run locally
Option A — Minimal (no install required)
- Open `index.html` directly in a modern browser. For some browsers, canvas and local file access is sufficient.

Option B — Serve via a static server (recommended)
- Using Python 3.x:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

- Using Node (serve):

```bash
npx serve .
# or
npm install -g serve
serve .
```

Option C — Use a real dev server
- If you add a node toolchain (Vite/Parcel/Webpack), add scripts in package.json. This repo currently ships as a static single file demo.

## Project structure
- `index.html` — main demo page (UI, canvas, chart and integrated JS).
- (future) `src/` — recommended place to split UI, simulation, and chart modules for maintainability.

## Key implementation notes
- The simulation uses a single animation loop (`requestAnimationFrame`) for consistent rendering.
- `nucleusData` contains the per-species configuration used by the simulation. Each nucleus object has the shape:

```js
{ name: 'Li-11', color: '#f59e0b', psiMinus: 0.7 }
```

- `psiMinus` is treated as the halo/"leakage" intensity and is multiplied by the metric slider value to compute halo opacity and influence particle rendering.
- Particle collections are stored per-nucleus in `nucleusParticles` and updated each frame.

## Recommended next steps / improvements
- Split JavaScript into modules (UI, sim, chart) and add a minimal build/dev environment (Vite or Parcel).
- Add a `package.json` with scripts for `start` and `build` to ease local development.
- Add unit tests for parameter normalization and small deterministic parts of the simulation.
- Replace hard-coded constants with a small configuration object or JSON file.
- Add graceful fallbacks and feature detection for older browsers.

## Publication & citation advice
If you plan to publicize or publish this demo, consider the following steps:
- Clean and document physics assumptions (what `psiMinus` and other parameters mean physically).
- Add a LICENSE (MIT/Apache-2.0 recommended) and a CITATION file describing how to cite the demo.
- Deploy to GitHub Pages for a live demo URL and create a release; optionally archive the release on Zenodo to mint a DOI prior to academic publication.
- Write a short methods note (blog post or arXiv preprint) explaining the mapping from theoretical quantities to visualized observables.

## Contributing
- Issues and pull requests are welcome. If you make substantial changes (refactors, added modules, or physics models), please open a PR describing the change and include screenshots or short recordings of the updated demo.

## License
- This repository does not include a license by default. If you want to make the project reusable, add a LICENSE file (MIT is a good default for demos).

## Maintainer / Contact
- Maintainer: chrismanmak-spec
- For issues about the demo or publication support, please open an issue in this repository.
