# 🔬 Optics Lab

> 2D prism refraction + dispersion simulator built on HTML5 Canvas
> HTML5 Canvas 기반 2D 프리즘 굴절 + 분산 시뮬레이터

A 2D optics lab simulator. A triangular glass prism is placed in a dark room and a white light ray is projected through it. The light refracts and **disperses into a 7-band rainbow** following **Snell's Law** (`n₁ sin θ₁ = n₂ sin θ₂`). Refractive index and incidence angle are fully adjustable via interactive sliders.

[🇰🇷 한국어](./README.md) · [🇺🇸 English (default)](#)

---

## 🎬 Live Demo

> **👉 [https://optics-prism-lab.vercel.app/](https://optics-prism-lab.vercel.app/)** — Run directly in the browser (Canvas 2D, 60fps)

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Foptics--prism--lab-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/optics-prism-lab) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-0-9CA3AF?style=flat-square) |

### 🎮 Quick usage
1. Click the demo link above → page opens in your browser
2. **Refractive index slider (n)** — 1.30 (acrylic) ~ 2.50 (diamond)
3. **Incidence angle slider (θ)** — 0° (perpendicular) ~ 80° (near critical angle)
4. **Dispersion strength** — Adjust 7-band rainbow width (Δn 0.04 ~ 0.18)
5. **Prism type** — Equilateral (60°) / custom angle
6. **Ray mode** — 7-band rainbow / RGB / monochrome white

---

## 🤖 Attribution

This project's code was **auto-generated** using the model and prompt below.

| Item | Value |
|---|---|
| **Model** | MiniMax-M3 |
| **Runtime** | OpenCode CLI |
| **Repository** | [`sigco3111/optics-prism-lab`](https://github.com/sigco3111/optics-prism-lab) |
| **License** | MIT |
| **Dependencies** | None (Vanilla JS, single HTML) |

### 📝 Prompt used (verbatim, KR)

```
어두운 공간에 삼각형 유리 프리즘을 배치하고 백색 광선을 비췄을 때,
스넬의 법칙(Snell's Law)에 따라 빛이 굴절되고 분산되어 무지개 스펙트럼
(Dispersion)으로 나뉘는 광학 실험을 시뮬레이션하되, 프리즘의 굴절률과
빛의 입사각을 조절할 수 있는 인터페이스를 포함해줘.
Implementation Advice: Use HTML5 Canvas. Implement Ray Tracing logic in 2D.
Calculate ray-line intersections. For dispersion (rainbow), cast multiple rays
(R, G, B) with slightly different refractive indices. 모든 의존관계의 코드를
하나의 HTML에 담는 형태로 코드 작성.
```

---

## ✨ Features

- 🔺 **Triangular glass prism** — Equilateral / custom angle toggle, drag-to-rotate with mouse
- 🌈 **7-band dispersion simulation** — Violet/Indigo/Blue/Green/Yellow/Orange/Red + Cauchy equation
- 📐 **Precise Snell's Law** — `n₁ sin θ₁ = n₂ sin θ₂` for exact incidence/refraction angle calculation
- 🎛️ **Interactive sliders** — Refractive index (n), incidence angle (θ), dispersion strength, prism rotation, ray mode
- 🌓 **Dark lab atmosphere** — Black background + glow rays + glass transmission/reflection rendering
- 📊 **Real-time angle/IOR HUD** — Live display of incidence, refraction, deviation angles
- 💻 **Single HTML** — Zero external dependencies, open one file to run
- 🔒 **On-device** — All physics + rendering inside the browser (zero server)

---

## 🚀 Quick Start

### Option 1: Live demo (Vercel, easiest)
Open the URL in the "Live Demo" section above. Zero external deps, runs immediately.

### Option 2: Open directly in a browser
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Option 3: Local static server (recommended — cleaner console logs)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

> **Note**: Zero external dependencies — no `<script src>` or `<link href>`. All physics + rendering is inlined into one `index.html`.

---

## 🎮 Controls

| Input | Action |
|---|---|
| **Refractive index slider (n)** | Glass IOR 1.30 ~ 2.50 (other sliders' n auto-update on drag) |
| **Incidence angle slider (θ)** | White ray incidence angle 0° ~ 80° (ray recomputes immediately) |
| **Dispersion strength slider** | Δn between 7 bands (0.04 ~ 0.18, controls rainbow width) |
| **Prism rotation slider** | Rotate the prism itself (optimize ray incidence direction) |
| **Prism type toggle** | Equilateral (60°) ↔ custom angle |
| **Ray mode toggle** | 7-band rainbow ↔ RGB 3-color ↔ monochrome white |
| **Pause toggle** | Freeze animation (for HUD value inspection) |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Rendering** | HTML5 Canvas 2D (glow via `shadowBlur` + additive blending) |
| **Physics** | Pure JS — Snell's Law, segment-segment intersection, vector reflect/refract |
| **Ray tracing** | 2D Ray Tracing (Segment-Segment Intersection, CCW winding) |
| **Dispersion model** | Cauchy approximation — `n(λ) = A + B/λ²` + 7-band wavelength→color map |
| **Input** | Mouse (drag for prism rotation) + sliders + toggles |
| **Bundling** | None (single HTML) |
| **Language** | Vanilla JavaScript (ES6+) |

---

## 📂 Project Structure

```
optics-prism-lab/
├── index.html      # Single HTML (all physics + rendering code inline)
├── README.md       # Korean (default)
├── README.en.md    # English (this file)
└── LICENSE         # MIT
```

---

## 🎨 Design Choices

Seven decisions from the brainstorming stage:

| Decision | Choice | Rationale |
|---|---|---|
| **Background tone** | Dark lab (`#04060c` → `#0a1020` gradient) | Glass/glow effects read best on dark backgrounds |
| **Prism form** | Equilateral by default, custom angle as option | 60° angle is the classic optics lab condition that maximizes visible dispersion |
| **Dispersion model** | 7-band (380~660nm) + Cauchy equation | Full continuous spectrum is expensive with little visual gain; 7 bands reproduce the textbook rainbow cleanly |
| **Refraction math** | Per-frame Segment-Segment Intersection | Precise math with zero physics engine dependency. CCW winding comparison for intersection test in 2D |
| **Deviation display** | HUD shows Deviation = θ_out − θ_in live | Quantifies how much the prism bends the light |
| **Glow effect** | Canvas `shadowBlur` + `globalCompositeOperation='lighter'` | Additive blend gives natural color overlap on the rainbow fan |
| **Bundling** | None (single HTML) | Zero CDN deps → instant offline / internal hosting swap |

### Want to customize?

Tweak these constants near the top of `index.html` to change physics & visuals:

```js
const DEFAULTS = Object.freeze({
  thetaDeg: 0,           // perpendicular entry — maximum dispersion
  ior_x100: 145,         // 1.45 — acrylic / light flint
  apexDeg: 60,           // equilateral prism angle
  disp_x100: 150,        // 1.5× — exaggerated for clearly visible rainbow
  rotationDeg: 0,        // prism rotation
  scale_x100: 100,       // prism size
  prismMode: 'equi',     // 'equi' | 'custom'
  rayMode: 'rainbow',    // 'rainbow' | 'rgb' | 'white'
  paused: false,
});

// 7-band rainbow wavelengths (nm)
const WAVELENGTHS = [
  { name:'Violet',   nm:380, color:'#a17cff' },
  { name:'Indigo',   nm:440, color:'#5b8cff' },
  { name:'Blue',     nm:490, color:'#3ec0ff' },
  { name:'Green',    nm:540, color:'#5dff8a' },
  { name:'Yellow',   nm:580, color:'#ffe25a' },
  { name:'Orange',   nm:610, color:'#ffa658' },
  { name:'Red',      nm:660, color:'#ff5d6c' },
];
```

Lower `disp_x100` to `50` for subtle real-glass-like dispersion; raise it to `200` for a dramatic rainbow fan. Lower `apexDeg` to `40` and Total Internal Reflection (TIR) triggers more often.

---

## 🧠 How It Works

```
White ray (incidence angle θ₁)
       │
       ▼
  ┌─────────────────────────────────────┐
  │ 1. Ray vs prism left edge intersect │ ← Segment Intersection
  │ 2. Compute Normal at intersection   │ ← Perpendicular to edge direction
  │ 3. Snell's law refraction          │ ← n₁sinθ₁ = n₂sinθ₂
  │ 4. 7 wavelengths × different n      │ ← Dispersion
  └─────────────────────────────────────┘
       │
       ▼
  Inside prism (refracted 7-color rays)
       │
       ▼
  ┌─────────────────────────────────────┐
  │ 5. Ray vs prism right edge intersect│
  │ 6. Refraction again (n₂→n₁)        │
  │ 7. Extract exit direction vector   │
  │ 8. Compute Deviation               │
  └─────────────────────────────────────┘
       │
       ▼
  R / G / B separated exit rays → rainbow spectrum
```

The core is **Snell's Law + segment-segment intersection**:
- `n₁ sin θ₁ = n₂ sin θ₂` → refraction angle `θ₂ = asin(n₁ sin θ₁ / n₂)`
- Total Internal Reflection (TIR) check: if `n₁ sin θ₁ > n₂`, reflect instead of refract
- Dispersion: Cauchy approximation `n(λ) = A + B/λ²` gives per-wavelength `n` for all 7 bands

### Why 7 bands

The original Implementation Advice suggested R/G/B 3-color rays, but RG / Indigo / B / Violet gaps left the output looking like "three colored lines", not a rainbow. **7 bands fill the visible spectrum** and match the textbook `ROYGBIV` mnemonic. Cauchy handles arbitrary band count at the same per-frame cost, so 3→7 adds no overhead.

---

## 🔬 Verification

| Item | Value |
|---|---|
| **Local index.html** | 38,434 B |
| **Vercel alias response** | HTTP 200 · 38,434 B (bit-perfect match) |
| **Dependencies** | None (0 CDN scripts, 0 `<link>` tags) |
| **Rendering** | Canvas 2D, 60fps (`requestAnimationFrame` loop) |
| **Physics step** | Per-frame 7-band refraction computation |
| **Anchor breakage** | 0 (KR/EN mixed headings: 0) |

---

## 📝 Prompt Log

| Round | When | Work |
|---|---|---|
| Round 1 | 2026-07-09 06:54 | Coding-mission scaffolding — README + placeholder `index.html` |
| Round 2 | 2026-07-09 09:35 | OpenCode implements full simulator (Snell's law + 7-band dispersion + HUD) |
| Round 3 | 2026-07-09 10:00 | Vercel deployment + multi-layer README v1.0 (this file) |

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

This project was generated with [MiniMax-M3](https://example.com) in the OpenCode CLI environment. Prompt engineering and design decisions were made directly by the repository owner.

- **Coding-mission reference page**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
