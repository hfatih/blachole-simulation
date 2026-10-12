<div align="center">

# ✦ Kerr Black Hole Simulation

**Real-Time General Relativistic Ray Tracing in WebGL 2**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-e7a0b9?style=for-the-badge&logo=github&logoColor=white)](https://hfatih.github.io/blachole-simulation/)
[![Live Site](https://img.shields.io/badge/Live%20Site-blackhole.hfatih.com-f0abc5?style=for-the-badge&logo=googlechrome&logoColor=white)](https://blackhole.hfatih.com)
[![Design](https://img.shields.io/badge/Design-Starlit%20Celestial%20Rose-ffb6c1?style=for-the-badge&logo=sparkles&logoColor=white)](#starlit--celestial-rose-design-system)

<br/>

[![WebGL 2](https://img.shields.io/badge/WebGL-2.0-blue.svg?style=flat-square)](https://www.khronos.org/registry/webgl/specs/latest/2.0/)
[![Vanilla JavaScript](https://img.shields.io/badge/JavaScript-Vanilla%20ES2022-yellow.svg?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![GLSL](https://img.shields.io/badge/Shaders-GLSL%203.00%20ES-orange.svg?style=flat-square)](https://www.khronos.org/registry/OpenGL/specs/es/3.0/GLSL_ES_Specification_3.00.pdf)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0-brightgreen.svg?style=flat-square)](#)

[✦ Live Simulation (blackhole.hfatih.com)](https://blackhole.hfatih.com) · [GitHub Pages](https://hfatih.github.io/blachole-simulation/) · [English](README.md) · [Türkçe](README.tr.md)

<br/>

<p align="center">
  <img src="assets/preview.png" alt="Kerr Black Hole Simulation Starlit UI Preview" width="880" style="border-radius: 14px; box-shadow: 0 10px 40px rgba(240,171,197,0.20);" />
</p>

<p align="center">
  <img src="assets/loader.png" alt="3D Rotating Black Hole Loader" width="520" style="border-radius: 12px; box-shadow: 0 8px 30px rgba(0,0,0,0.85); margin-top: 6px;" /><br/>
  <em>Instant 3D rotating optical black hole loader with dual-layer relativistic disk and micro-starfield.</em>
</p>

<p align="center">
  <em>Interactive geodesic light ray tracing through the curved spacetime of a spinning Kerr black hole.<br/>Styled with the <strong>Starlit / Celestial Rose</strong> design system: deep obsidian plum, celestial rose luminescence, glassmorphism, and instant 3D black hole loader.</em>
</p>

</div>

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Starlit / Celestial Rose Design System](#starlit--celestial-rose-design-system)
  - [UI & Palette Philosophy](#ui--palette-philosophy)
  - [3D Rotating Black Hole Loader](#3d-rotating-black-hole-loader)
- [Physics & Relativistic Optics](#physics--relativistic-optics)
  - [Kerr-Schild Metric & Geodesics](#kerr-schild-metric--geodesics)
  - [Novikov–Thorne Accretion Disk](#novikovthorne-accretion-disk)
  - [Doppler Beaming & Gravitational Redshift](#doppler-beaming--gravitational-redshift)
  - [Shadow, Photon Ring & Ergosphere](#shadow-photon-ring--ergosphere)
  - [Timelike Free-Fall (Observer Plunge)](#timelike-free-fall-observer-plunge)
  - [Simulated Event Horizon Telescope (EHT)](#simulated-event-horizon-telescope-eht)
- [Graphics Pipeline & Engine Architecture](#graphics-pipeline--engine-architecture)
  - [Progressive, Zero-Freeze Startup](#progressive-zero-freeze-startup)
  - [Temporal Anti-Aliasing & Upsampling (TAAU)](#temporal-anti-aliasing--upsampling-taau)
  - [Dual-Pyramid Bloom & Post-Processing](#dual-pyramid-bloom--post-processing)
  - [Procedural Cosmic Environment](#procedural-cosmic-environment)
- [Quick Start](#quick-start)
- [Interactive Controls & Shortcuts](#interactive-controls--shortcuts)
- [Presets](#presets)
- [URL Query Parameters](#url-query-parameters)
- [Analytical Validation](#analytical-validation)
- [Project Structure](#project-structure)
- [Scientific References](#scientific-references)

---

## Overview

This project is a real-time, browser-based physical simulation of a rotating (Kerr) black hole. Every visible pixel is computed by integrating null geodesics (light paths) backwards in time from the observer's camera tetrad through curved spacetime according to Einstein's General Theory of Relativity.

Unlike conventional graphics simulations that use texture tricks or pre-rendered approximations, this engine computes:
- Exact Kerr-Schild spacetime metric equations and Christoffel connections analytically.
- Novikov–Thorne relativistic thin accretion disk temperature profiles and Keplerian orbital velocity fields.
- Chromatic Planck spectrum integration with Doppler amplification ($g^4$) and gravitational time dilation.
- Timelike free-fall trajectories passing through the event horizon into the Cauchy horizon.
- Zero external assets or 3D models: stars, nebulas, dust lanes, accretion turbulence, and blackbody color maps are generated dynamically in code.

---

## Key Features

- **Physically Rigorous**: Solves Hamilton's equations of motion for null and timelike geodesics using adaptive 4th-order Runge-Kutta (RK4) integration in horizon-penetrating Kerr-Schild coordinates.
- **Accretion Disk Physics**: Novikov–Thorne (Page–Thorne) relativistic thin disk with inner truncation at the Innermost Stable Circular Orbit ($r_{\text{ISCO}}$), differential rotation, turbulence shear, and light travel time delay.
- **Relativistic Optics**: Gravitational lensing, Einstein rings, multiple image formation, Doppler beaming (approaching side blue-shifted and magnified; receding side red-shifted and dimmed), and gravitational redshift.
- **Timelike Free Fall**: Step inside the black hole along a true timelike geodesic with real-time HUD telemetry reporting proper time ($\tau$), metric coefficients, and horizon penetration.
- **Interactive Light Diagram**: Real-time 2D equatorial plane diagram showing light rays emitted from the camera deflected around the photon sphere and shadow.
- **Simulated EHT Mode**: 1.3 mm VLBI radio telescope resolution simulation using multi-scale Gaussian beam convolution mimicking images from the Event Horizon Telescope (M87* and Sgr A*).
- **Ultra-Smooth Startup**: Progressive asynchronous compilation, phased cubemap generation, and offscreen GPU pipeline warmup with an animated celestial loading screen (no stutter, no freezes).
- **Starlit / Celestial Rose Aesthetics**: Deep obsidian plum theme (`#150a14`), glowing celestial rose controls (`#f0abc5`), translucent glassmorphic cards (`blur(20px)`), and instant 3D rotating black hole loader.
- **Adaptive Performance**: Dynamic resolution scaling and TAAU target a locked 60 FPS across high-end desktop GPUs down to lightweight laptops.

---

## Starlit / Celestial Rose Design System

The simulation's interface is built on the signature **Starlit / Celestial Rose** design language, unifying cosmic telemetry with celestial aesthetics:

<div align="center">
  <img src="assets/preview.png" alt="Starlit Design System Overview" width="880" style="border-radius: 14px; box-shadow: 0 12px 36px rgba(240,171,197,0.18);" />
</div>

<br/>

### UI & Palette Philosophy

| Token / Layer | Color Code | Visual Role & Implementation |
| :--- | :---: | :--- |
| **Cosmic Deep Space** | `#150a14` · `#07040a` | Deep obsidian plum and velvet space background void |
| **Glassmorphic Panels** | `rgba(25, 12, 24, 0.68)` | Multi-pass background blur (`backdrop-filter: blur(20px)`), `18px` rounded corners, and soft inner glow |
| **Border Accents** | `rgba(240, 171, 197, 0.20)` | Subtle rose hairline borders separating telemetry controls from cosmic rays |
| **Celestial Rose** | `#f0abc5` | Primary telemetry glow, active state rings, and ISCO characteristic orbit indicators |
| **Starlight Pink** | `#ffd3e0` | Secondary highlights, gradient slider progress fill, and typography accents |
| **Doppler Cyan** | `#8fb7ff` | Relativistic kinematic blueshift indicators and escaping light ray vectors |
| **Mode Capsule** | Floating Pill | Floating pill navigation island with glowing rose active states (`.on`) |
| **2D Equatorial Canvas** | Canvas HUD | Real-time deflection tracks with `#f0abc5` ISCO, spin direction arrow, and camera position |

### 3D Rotating Black Hole Loader

<div align="center">
  <img src="assets/loader.png" alt="3D Black Hole Loader Detail" width="560" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.9);" />
</div>

<br/>

Borrowed from the portfolio site design and adapted for real-time physics:
- **3D Optical Occlusion**: Built using two independent depth layers (`.loader__disk` in the background, and `.loader__disk--front` with `clip-path: inset(50% 0 0 0)` positioned inside the shadow). This correctly renders the front half of the disk in front of the event horizon and the rear half behind it, creating an authentic 3D optical lens illusion.
- **Dual Counter-Rotating Conic Convection**: Two layered noise gradients spin at $2.8\text{ s}$ and $7.0\text{ s}$ with an axial tilt of $6^\circ$, modeling turbulent differential shearing.
- **Zero-Delay Instant First-Paint**: Positioned at the very top of `<body>` with zero entrance delays or CSS blur latencies. The entire 3D black hole, starry sky, and loading telemetry render immediately on frame 0, eliminating blank screens.
- **Tabular Mono Telemetry**: Monospace progress counter (`000%` to `100%`) with animated gradient fill bar and smooth scale-dissolve exit (`.is-leaving`).

---

## Physics & Relativistic Optics

### Kerr-Schild Metric & Geodesics

The spacetime surrounding an uncharged, spinning black hole of mass $M$ and spin parameter $a = J/M$ is described in Cartesian Kerr-Schild coordinates $(t, x, y, z)$. The metric tensor takes the form:

$$g_{\mu\nu} = \eta_{\mu\nu} + 2 H l_\mu l_\nu$$

where $\eta_{\mu\nu} = \text{diag}(-1, 1, 1, 1)$ is the Minkowski metric, $l_\mu$ is a null vector field ($g^{\mu\nu} l_\mu l_\nu = 0$), and the scalar function $H$ is:

$$H = \frac{M r^3}{r^4 + a^2 z^2}$$

The radial coordinate $r$ is defined implicitly by the spheroidal equation:

$$\frac{x^2 + y^2}{r^2 + a^2} + \frac{z^2}{r^2} = 1$$

Kerr-Schild coordinates are **horizon-penetrating and regular** across the outer event horizon:

$$r_+ = M + \sqrt{M^2 - a^2}$$

and the inner Cauchy horizon:

$$r_- = M - \sqrt{M^2 - a^2}$$

Light trajectories obey the Hamiltonian system with $H(x, p) = \frac{1}{2} g^{\mu\nu} p_\mu p_\nu = 0$:

$$\frac{dx^\mu}{d\lambda} = g^{\mu\nu} p_\nu, \quad \frac{dp_\mu}{d\lambda} = -\frac{1}{2} \partial_\mu g^{\alpha\beta} p_\alpha p_\beta$$

Because the derivatives $\partial_\mu g^{\alpha\beta}$ are calculated analytically in `js/physics.js` and `js/shaders.js`, numerical precision is maintained without finite-difference drift.

### Novikov–Thorne Accretion Disk

The accretion disk follows the relativistic thin-disk model of Novikov & Thorne (1973) and Page & Thorne (1974). Gas orbits on equatorial circular geodesics between the Innermost Stable Circular Orbit ($r_{\text{ISCO}}$) and outer radius $r_{\text{out}}$ with Keplerian angular velocity:

$$\Omega_K = \frac{\sqrt{M}}{r^{3/2} + a \sqrt{M}}$$

The effective temperature profile $T(r)$ reaches thousands of Kelvin, truncates sharply at $r_{\text{ISCO}}$, and peaks around $r \approx 1.5 - 1.8 \, r_{\text{ISCO}}$:

$$T(r) = T_{\text{max}} \cdot f_{\text{NT}}(r, a)^{1/4}$$

### Doppler Beaming & Gravitational Redshift

Photons emitted by the disk gas with 4-velocity $u^\mu_{\text{em}}$ and observed with 4-velocity $u^\mu_{\text{obs}}$ experience an energy shift ratio (Doppler factor $g$):

$$g = \frac{p_\mu u^\mu_{\text{obs}}}{p_\nu u^\nu_{\text{em}}}$$

- **Kinematic Doppler Effect**: The side of the disk rotating towards the observer travels at relativistic speeds ($v \approx 0.3 - 0.5c$), causing strong blue-shifting and intense amplification. The receding side is red-shifted and dimmed.
- **Gravitational Redshift**: Photons climbing out of the deep gravitational potential well lose energy, shifting towards longer wavelengths.
- **Bolometric Flux**: The observed radiant flux scales with the 4th power of the Doppler factor:

$$I_{\text{obs}} = g^4 I_{\text{em}}$$

Each disk point radiates as a local blackbody. The observed chromatic spectrum is derived from the Planck function at effective temperature $T_{\text{obs}} = g \cdot T_{\text{local}}$.

### Shadow, Photon Ring & Ergosphere

- **Event Horizon & Ergosphere**: The static limit (ergosphere boundary) is located at $r_E(\theta) = M + \sqrt{M^2 - a^2 \cos^2\theta}$. Inside the ergosphere, spacetime is dragged by frame dragging (Lense-Thirring effect) such that no stationary observer can exist.
- **Black Hole Shadow**: The central dark region is not merely the event horizon; it is the projection of the photon capture sphere. For non-rotating Schwarzschild holes ($a=0$), the shadow radius is analytically $r_{\text{shadow}} = 3\sqrt{3}M \approx 5.196 M$. For rotating Kerr holes ($a \to M$), frame dragging pulls the photon orbit closer on the prograde side, making the shadow distinctly asymmetric (D-shaped).
- **Photon Ring & Multiple Images**: Light rays passing just outside the critical impact parameter loop around the black hole 1, 2, or more times before escaping, generating infinite nested sub-rings and showing the backside of the accretion disk wrapped simultaneously above and below the hole.

### Timelike Free-Fall (Observer Plunge)

Switching to Fall Mode (`D` key) drops the camera from rest into the black hole along a true timelike geodesic ($u^\mu u_\mu = -1$). 
- As the camera approaches the horizon, the outside universe is compressed into an optical aberration ring overhead.
- Because Kerr-Schild coordinates are non-singular at $r_+$, the simulation crosses the event horizon smoothly.
- Inside the horizon, radial coordinate $r$ acts as a timelike coordinate, inevitably carrying the observer towards the inner Cauchy horizon ($r_-$ for $a > 0$) or the central singularity ($a = 0$).

### Simulated Event Horizon Telescope (EHT)

Toggling EHT view (`eht: true`) applies a multi-scale Gaussian convolution filter calibrated to simulate the 20 microarcsecond angular resolution of the Event Horizon Telescope at 1.3 mm (230 GHz) VLBI, reproducing the characteristic crescent shadow observed in M87* and Sagittarius A*.

---

## Graphics Pipeline & Engine Architecture

```
                  ┌────────────────────────────────────────┐
                  │          Camera & Geodesic Ray         │
                  └───────────────────┬────────────────────┘
                                      │
                                      ▼
                  ┌────────────────────────────────────────┐
                  │       trace.frag (Kerr RK4 Trace)      │
                  │   - Hamilton equations & KS metric     │
                  │   - Novikov-Thorne disk & Doppler (g⁴) │
                  │   - Procedural stars & background sky  │
                  └───────────────────┬────────────────────┘
                                      │
                                      ▼
                  ┌────────────────────────────────────────┐
                  │     neigh.frag (Neighborhood Stats)    │
                  └───────────────────┬────────────────────┘
                                      │
                                      ▼
                  ┌────────────────────────────────────────┐
                  │       taa.frag (TAAU Upsampling)       │
                  │   - Sub-pixel Halton jitter            │
                  │   - Variance clipping & history blend  │
                  └───────────────────┬────────────────────┘
                                      │
                                      ▼
                  ┌────────────────────────────────────────┐
                  │     down.frag / up.frag (Bloom Mips)   │
                  │   - 13-tap dual-pyramid filter chain   │
                  └───────────────────┬────────────────────┘
                                      │
                                      ▼
                  ┌────────────────────────────────────────┐
                  │      composite.frag (Tonemapping)      │
                  │   - ACES-like curve, Vignette, Grain   │
                  │   - Optional EHT VLBI resolution blur  │
                  └───────────────────┬────────────────────┘
                                      │
                                      ▼
                               Canvas Display
```

### Progressive, Zero-Freeze Startup

Heavy raytracing shaders and procedural generation can easily stall the browser main thread if loaded synchronously. This simulation features a phased asynchronous startup pipeline:
1. **Asynchronous Shader Compilation**: Shaders (`skygen`, `trace`, `taa`, `neigh`, `down`, `up`, `comp`, `skyview`, `maxlum`, `autoexp`) compile in staged ticks, yielding execution frames to ensure smooth 60 FPS CSS loader animation.
2. **Progressive Cubemap Generation**: The 6-face 1024x1024 HDR cosmic cubemap is rendered face-by-face over multiple animation frames with real-time percentage feedback.
3. **Offscreen GPU Warmup**: Before the loading screen is dismissed, 2 offscreen warmup frames are rendered to allow GPU drivers to compile pipeline state objects (PSO) and cache textures, eliminating any initial frame drops.
4. **Cinematic Dismissal**: The celestial black hole loader dissolves with a smooth cubic-bezier transition, seamlessly unveiling a live, stutter-free simulation.

### Temporal Anti-Aliasing & Upsampling (TAAU)

- **Halton Jitter**: Camera sub-pixel coordinates are jittered across a 16-phase low-discrepancy Halton sequence.
- **Neighborhood Bounding Box Clamping**: History samples are clamped against current-frame variance ($\mu \pm 1.25\sigma$) to reject ghosting on moving edges.
- **Dynamic Upsampling**: Renders ray tracing at lower internal resolutions (e.g. 0.6x - 0.85x) while reconstructing razor-sharp native display resolution with temporal accumulation.

### Dual-Pyramid Bloom & Post-Processing

- An 8-level downsampling and upsampling pyramid using a 13-tap box filter with partial sub-sampling prevents fireflies and generates smooth, physical accretion disk glare.
- Reinhard / ACES tone mapping preserves high-dynamic-range Planck intensities ($10^0$ to $10^5$) without clipping color subtleties.

### Procedural Cosmic Environment

No external PNG/JPG textures are bundled with the repository. The cosmic skybox is computed procedurally using:
- 9-octave 3D Fractional Brownian Motion (FBM) for nebular gas clouds.
- 8-octave ridged multifractal noise for dark interstellar dust lanes.
- Analytical exponential galactic disk density profile and spiral galaxy arms.
- Deterministic 3D spatial hashing for over 20,000 background stars with realistic spectral types.

---

## Quick Start

### Requirements
- Any modern web browser with **WebGL 2** support (Google Chrome, Microsoft Edge, Mozilla Firefox, Apple Safari).
- No Node.js packages, npm dependencies, or build tools are required to run the simulation.

### Option 1: Direct File Opening
Simply open `index.html` directly in your browser.

### Option 2: Local HTTP Server (Recommended)
Using Python:
```bash
# Python 3
python -m http.server 8000
```

Using Node.js:
```bash
npx serve .
```

Then navigate to [http://localhost:8000](http://localhost:8000).

---

## Interactive Controls & Shortcuts

| Action | Mouse / Touch | Keyboard Shortcut |
| :--- | :--- | :--- |
| **Orbit Camera** | Left-click drag | Arrow keys / drag |
| **Look Around** | `Shift` + drag | `Shift` + drag |
| **Zoom Distance / FOV** | Mouse wheel / Pinch | Wheel |
| **Cinematic Mode** | — | `C` |
| **Free Orbit Mode** | — | `O` |
| **Free Fall (Plunge)** | Click header button | `D` |
| **Automated Tour** | Click header button | `T` |
| **Pause / Resume Time** | Toggle switch | `Space` |
| **Presets (1–8)** | Click preset button | `1` to `8` |
| **Toggle UI Overlays** | — | `H` |
| **Toggle Settings Panel**| Bottom button | `P` |
| **Show Physics Guide** | Info button | `I` or `?` |
| **Full Screen** | — | `F` |
| **High-Res Screenshot** | — | `S` |
| **Reset Look Angles** | Double-click canvas | Double-click |

---

## Presets

The simulation includes 8 curated astrophysical and cinematic configurations:

| Key | Preset | Spin ($a/M$) | Inclination | Description |
| :---: | :--- | :---: | :---: | :--- |
| `1` | **Physical View** | `0.900` | $82^\circ$ | Realistic Novikov–Thorne disk with active Doppler shift and bolometric beaming. |
| `2` | **Gargantua** | `0.990` | $87^\circ$ | *Interstellar*-inspired view: near-extremal spin, thick disk, cinematic exposure. |
| `3` | **Polar Orbit** | `0.900` | $6^\circ$ | Top-down view showing concentric Einstein rings and symmetric accretion structure. |
| `4` | **Edge-On** | `0.900` | $89.5^\circ$ | Extreme equatorial view showing disk light bent over and under the event horizon. |
| `5` | **Close Flyby** | `0.900` | $84^\circ$ | Camera at $r = 7.5M$ with wide $75^\circ$ FOV revealing gravitational lensing distortion. |
| `6` | **Lensing Map** | `0.000` | $90^\circ$ | Disk disabled, celestial coordinate grid enabled to illustrate light deflection. |
| `7` | **M87* (EHT)** | `0.900` | $17^\circ$ | EHT radio telescope resolution simulation matching the famous M87* ring observation. |
| `8` | **Relativistic Jet** | `0.900` | $64^\circ$ | Collimated relativistic synchrotron plasma jet erupting along the black hole spin axis. |

---

## URL Query Parameters

Customize simulation launch parameters directly via URL query parameters for sharing or embedding:

```text
http://localhost:8000/?preset=gargantua&scale=0.85&ui=1
```

| Parameter | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `preset` | string | `fiziksel` | Initial preset (`fiziksel`, `gargantua`, `kutup`, `kenar`, `yakin`, `lens`, `m87`, `jet`). |
| `mode` | string | `cinematic` | Camera mode (`cinematic`, `orbit`, `plunge`, `tour`). |
| `spin` | float | `0.9` | Black hole spin parameter $a/M$ ($0.0$ to $0.998$). |
| `dist` | float | `28.0` | Camera distance in gravitational radii $M$. |
| `incl` | float | `82.0` | Camera inclination angle in degrees ($1.5^\circ$ to $178.5^\circ$). |
| `fov` | float | `50.0` | Camera field of view in degrees. |
| `scale` | float | dynamic | Fixed render resolution scale ($0.3$ to $1.0$). Disables auto-resolution. |
| `quality` | string | `yuksek` | Step count preset (`dusuk`: 220, `orta`: 320, `yuksek`: 460, `ultra`: 800). |
| `skysize` | int | `1024` | Resolution per face of the background cubemap ($512$, $1024$, $2048$). |
| `eht` | bool | `false` | Enable simulated Event Horizon Telescope blur (`1` or `true`). |
| `ui` | bool | `1` | Set to `0` to hide all UI elements on launch. |
| `panel` | bool | `1` | Set to `0` to launch with settings panel collapsed. |
| `diagram`| bool | `1` | Set to `0` to hide light path diagram canvas. |

---

## Analytical Validation

The mathematical core in `js/physics.js` is verified against exact closed-form general relativity solutions:

```bash
node dev/test_physics.js
```

### Verified Benchmarks
- **Null Constraint Deviation**: $|H| = |g^{\mu\nu} p_\mu p_\nu| < 10^{-4}$ maintained along geodesic paths.
- **Schwarzschild Shadow Radius**: Numerical ray shooting matches the exact analytical radius $b_{\text{crit}} = 3\sqrt{3}M \approx 5.19615 M$ to within 4 decimal places.
- **Kerr Shadow Critical Impact Parameters**: Prograde and retrograde equatorial critical impact parameters for $a = 0.0, 0.5, 0.9, 0.99$ match Carter constant solutions to within $0.02M$:
  - $a = 0.5$: Prograde $b = 4.096$, Retrograde $b = 6.138$
  - $a = 0.9$: Prograde $b = 2.844$, Retrograde $b = 6.832$
  - $a = 0.99$: Prograde $b = 2.252$, Retrograde $b = 6.983$
- **ISCO Radius**: Analytical match across all spins ($a=0 \implies r_{\text{ISCO}}=6M$, $a=0.9 \implies r_{\text{ISCO}}=2.321M$).
- **Free-Fall Proper Time**: Radial free-fall proper time $\tau$ matches analytical Painlevé–Gullstrand integration within $0.01\%$.

---

## Project Structure

```text
blachole-simulation/
├── index.html              # Interface markup, styles, loading screen, and canvas
├── js/
│   ├── physics.js          # CPU physics core: Kerr metric, Christoffel, RK4, Novikov-Thorne
│   ├── shaders.js          # GLSL shaders: Raymarcher, TAAU, cubemap generator, bloom, tone mapping
│   └── main.js             # WebGL2 engine: Progressive loader, camera, controls, HUD, render loop
├── dev/
│   ├── test_physics.js     # Analytical general relativity test suite (Node.js)
│   ├── step_accuracy.js    # Step-size benchmark and convergence analysis
│   ├── qgrowth.js          # Momentum vector growth analysis for ray termination
│   └── cdp.js              # Headless Chrome DevTools Protocol automation and test harness
├── assets/
│   ├── preview.png         # Simulation Starlit UI screenshot
│   └── loader.png          # 3D rotating black hole loader screenshot
├── README.md               # English documentation
└── README.tr.md            # Turkish documentation
```

---

## Scientific References

1. **Kerr, R. P.** (1963). *Gravitational Field of a Spinning Mass as an Example of Algebraically Special Metrics*. Physical Review Letters, 11(5), 237–238.
2. **Bardeen, J. M.** (1973). *Timelike and null geodesics in the Kerr metric*. Black Holes (Les Houches 1972), 215–239.
3. **Novikov, I. D., & Thorne, K. S.** (1973). *Astrophysics of black holes*. Black Holes (Les Houches 1972), 343–450.
4. **Page, D. N., & Thorne, K. S.** (1974). *Disk-Accretion onto a Black Hole. I. Accretion Spectrum*. The Astrophysical Journal, 191, 499–506.
5. **Luminet, J.-P.** (1979). *Image of a spherical black hole with thin accretion disk*. Astronomy and Astrophysics, 75, 228–235.
6. **Marck, J.-A.** (1996). *Short-cut method of solution of geodesic equations for spinning black holes*. Classical and Quantum Gravity, 13(3), 393.
7. **James, O., von Tunzelmann, E., Franklin, P., & Thorne, K. S.** (2015). *Gravitational lensing by spinning black holes in astrophysics, and in the movie Interstellar*. Classical and Quantum Gravity, 32(6), 065001.
8. **Event Horizon Telescope Collaboration** (2019). *First M87 Event Horizon Telescope Results. I. The Shadow of the Supermassive Black Hole*. The Astrophysical Journal Letters, 875(1), L1.

---

<div align="center">
  <sub>Developed with passion for astrophysics and real-time computer graphics. Released under the MIT License.</sub>
</div>
