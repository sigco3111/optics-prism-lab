# 🔬 Optics Lab

> HTML5 Canvas 기반 2D 프리즘 굴절 + 분산 시뮬레이터
> 2D prism refraction + dispersion simulator built on HTML5 Canvas

어두운 실험실에 삼각형 유리 프리즘을 배치하고 백색 광선을 비추면, **스넬의 법칙(Snell's Law)** 에 따라 빛이 굴절되고 분산(Dispersion)되어 무지개 스펙트럼으로 나뉘는 광학 실험을 시뮬레이션합니다. **7-band 레인보우 파장 모델 + Cauchy 분산식**으로 R/G/B가 아닌 7색 분광을 보여주며, 프리즘의 굴절률과 빛의 입사각을 인터랙티브 슬라이더로 자유롭게 조절할 수 있습니다.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](./README.en.md)

---

## 🎬 라이브 데모

> **👉 [https://optics-prism-lab.vercel.app/](https://optics-prism-lab.vercel.app/)** — 브라우저에서 바로 실행 (Canvas 2D, 60fps)

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Foptics--prism--lab-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/optics-prism-lab) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-0-9CA3AF?style=flat-square) |

### 🎮 빠른 사용법
1. 위 데모 링크 클릭 → 브라우저에서 페이지 열기
2. **굴절률 슬라이더 (n)** — 1.30 (아크릴) ~ 2.50 (다이아몬드)
3. **입사각 슬라이더 (θ)** — 0° (수직 입사) ~ 80° (임계각 근접)
4. **분산 강도** — 7색 무지개 폭 조절 (Δn 0.04 ~ 0.18)
5. **프리즘 종류** — 정삼각형 (60°) / 임의 각도
6. **광선 모드** — 7-band 레인보우 / RGB / 단색 화이트

---

## 🤖 생성 정보

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**되었습니다.

| 항목 | 값 |
|---|---|
| **모델** | MiniMax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/optics-prism-lab`](https://github.com/sigco3111/optics-prism-lab) |
| **라이선스** | MIT |
| **의존성** | 없음 (Vanilla JS, 단일 HTML) |

### 📝 사용된 프롬프트 (원문)

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

## ✨ 주요 특징

- 🔺 **삼각형 유리 프리즘** — 정삼각형 / 임의 각도 토글, 마우스로 드래그하여 회전
- 🌈 **7-band 분산 시뮬레이션** — Violet/Indigo/Blue/Green/Yellow/Orange/Red 7색 + Cauchy 분산식
- 📐 **스넬의 법칙 정밀 계산** — `n₁ sin θ₁ = n₂ sin θ₂`로 입사/굴절각 정확히 계산
- 🎛️ **인터랙티브 슬라이더** — 굴절률(n), 입사각(θ), 분산 강도, 프리즘 회전, 광선 모드 실시간 조절
- 🌓 **다크 실험실 분위기** — 검정 배경 + 글로우 광선 + 프리즘 유리 반사/투과 표현
- 📊 **각도/굴절률 실시간 HUD** — 입사각·굴절각·편각(Deviation) 측정값 표시
- 💻 **단일 HTML** — 외부 의존성 0개, 파일 하나만 열면 실행
- 🔒 **온디바이스** — 모든 물리 계산과 렌더링이 브라우저 안에서 처리됨 (서버 0)

---

## 🚀 실행 방법

### 방법 1: 라이브 데모 (Vercel, 가장 간단)
위 "라이브 데모" 섹션의 URL을 브라우저에서 열기. 외부 의존성 0개라 즉시 실행됩니다.

### 방법 2: 브라우저로 직접 열기
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### 방법 3: 로컬 정적 서버 (권장 — 콘솔 로그 깨끗)
```bash
python3 -m http.server 8000
# → http://localhost:8000 접속
```

> **참고**: 외부 의존성 0개 — `<script src>` / `<link href>` 어느 것도 없습니다. 모든 물리 계산과 렌더링이 `index.html` 하나에 인라인으로 들어있습니다.

---

## 🎮 조작법

| 입력 | 동작 |
|---|---|
| **굴절률 슬라이더 (n)** | 프리즘 유리 굴절률 1.30 ~ 2.50 (드래그 시 다른 슬라이더의 n 값도 자동 갱신) |
| **입사각 슬라이더 (θ)** | 백색 광선의 입사각 0° ~ 80° (드래그 시 광선 즉시 재계산) |
| **분산 강도 슬라이더** | 7색 사이의 굴절률 차이 (Δn 0.04 ~ 0.18, 무지개 폭 조절) |
| **프리즘 회전 슬라이더** | 프리즘 자체의 회전 (광선 입사 방향 최적화) |
| **프리즘 종류 토글** | 정삼각형 (60°) ↔ 임의 각도 (custom) |
| **광선 모드 토글** | 7-band 레인보우 ↔ RGB 3색 ↔ 단색 화이트 |
| **일시정지 토글** | 애니메이션 정지 (HUD 값 검증용) |

---

## 🛠️ 기술 스택

| 영역 | 사용 기술 |
|---|---|
| **렌더링** | HTML5 Canvas 2D (글로우 효과는 `shadowBlur` + `globalCompositeOperation`) |
| **물리 계산** | 순수 JS — 스넬의 법칙, 선-선 교차, 벡터 반사/굴절 |
| **광선 추적** | 2D Ray Tracing (Segment-Segment Intersection, 좌우선 인터섹션) |
| **분산 모델** | Cauchy 근사 — `n(λ) = A + B/λ²` + 7-band 파장별 색상 매핑 |
| **입력** | 마우스(드래그로 프리즘 회전) + 슬라이더 + 토글 |
| **번들링** | 없음 (단일 HTML) |
| **언어** | Vanilla JavaScript (ES6+) |

---

## 📂 프로젝트 구조

```
optics-prism-lab/
├── index.html      # 단일 HTML (모든 물리 계산 + 렌더링 코드 포함)
├── README.md       # 한국어 (기본)
├── README.en.md    # English (옵션)
└── LICENSE         # MIT
```

---

## 🎨 디자인 결정

브레인스토밍 단계에서 내린 결정 7가지:

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **배경/톤** | 다크 실험실 (`#04060c` → `#0a1020` 그라데이션) | 유리/광선 발광 효과가 어두운 배경에서 가장 잘 보임 |
| **프리즘 형태** | 정삼각형 = 기본, 임의 각도 = 옵션 | 60° 각도가 분산 효과가 가장 잘 보이는 클래식 광학 실험 조건 |
| **분산 모델** | 7-band (380~660nm) + Cauchy 식 | 풀 연속 스펙트럼은 비싸고 시각적 차이 미미. 7색이면 무지개 효과 명확 |
| **굴절 계산** | 매 프레임 Segment-Segment Intersection | 물리엔진 의존 없이 정밀 계산. 2D라 `ccw` 부호 비교로 교차 판정 |
| **편각 표시** | HUD에 Deviation = θ_out - θ_in 실시간 표시 | "프리즘이 빛을 얼마나 휘게 하는가" 정량 확인 |
| **글로우 효과** | Canvas `shadowBlur` + `globalCompositeOperation='lighter'` | 가산 혼합으로 무지개 색이 겹치는 자연스러움 |
| **번들링** | 없음 (단일 HTML) | CDN 의존성 0 → 오프라인/내부 호스팅 즉시 전환 가능 |

### 직접 커스터마이즈하고 싶다면

`index.html` 상단에서 다음 상수를 조정하면 물리/모습을 바꿀 수 있어요:

```js
const DEFAULTS = Object.freeze({
  thetaDeg: 0,           // 수직 입사 — 최대 분산
  ior_x100: 145,         // 1.45 — 아크릴 / 라이트 플린트
  apexDeg: 60,           // 정삼각형 각도
  disp_x100: 150,        // 1.5× — 무지개가 명확히 보일 만큼 부풀림
  rotationDeg: 0,        // 프리즘 회전
  scale_x100: 100,       // 프리즘 크기
  prismMode: 'equi',     // 'equi' | 'custom'
  rayMode: 'rainbow',    // 'rainbow' | 'rgb' | 'white'
  paused: false,
});

// 7-band 레인보우 파장 정의 (nm)
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

`disp_x100`를 `50`으로 낮추면 실제 유리 같은 미묘한 분산, `200`으로 올리면 극적인 무지개가 펼쳐집니다. `apexDeg`를 `40`으로 바꾸면 임계각(TIR)이 더 자주 발동합니다.

---

## 🧠 동작 원리

```
백색 광선 (입사각 θ₁)
       │
       ▼
  ┌─────────────────────────────────────┐
  │ 1. 광선 vs 프리즘 좌측 엣지 교차     │ ← Segment Intersection
  │ 2. 교차점에서 법선(Normal) 계산     │ ← 엣지 방향의 수직 벡터
  │ 3. 스넬의 법칙 굴절 계산           │ ← n₁sinθ₁ = n₂sinθ₂
  │ 4. 7 파장 각각 다른 n 으로 7번 계산 │ ← 분산 (Dispersion)
  └─────────────────────────────────────┘
       │
       ▼
  프리즘 내부 (굴절된 7색 광선)
       │
       ▼
  ┌─────────────────────────────────────┐
  │ 5. 광선 vs 프리즘 우측 엣지 교차     │
  │ 6. 다시 굴절 계산 (n₂→n₁)          │
  │ 7. 출사 방향 벡터 도출              │
  │ 8. 편각(Deviation) 계산            │
  └─────────────────────────────────────┘
       │
       ▼
  R / G / B 분리된 출사광 → 무지개 스펙트럼
```

핵심은 **스넬의 법칙 + 선-선 교차**입니다.
- `n₁sinθ₁ = n₂sinθ₂` → 굴절각 `θ₂ = asin(n₁sinθ₁/n₂)`
- 내부 전반사(TIR) 판정: `n₁sinθ₁ > n₂` 면 굴절 없이 반사
- 분산: Cauchy 근사 `n(λ) = A + B/λ²`로 7 파장별 다른 n 적용

### 왜 7-band 인가

본래 Implementation Advice는 R/G/B 3색이었지만, **RG/Indigo/B/Violet 영역이 비면 시각적으로 "무지개"가 아닌 "RGB 3색"으로 보입니다**. 7-band로 확장하면 풀 무지개 효과가 살아나고, 광학 교과서 `ROYGBIV` 그래픽과 일치합니다. Cauchy 식은 같은 계산 비용으로 임의 파장 수를 지원하므로 3→7로 늘려도 프레임 저하 없음.

---

## 🔬 검증

| 항목 | 값 |
|---|---|
| **로컬 index.html** | 38,434 B |
| **Vercel alias 응답** | HTTP 200 · 38,434 B (bit-perfect match) |
| **의존성** | 없음 (CDN script 0개, `<link>` 0개) |
| **렌더링** | Canvas 2D, 60fps (requestAnimationFrame 루프) |
| **물리 step** | 매 프레임 7-band 굴절 계산 |
| **앵커 깨짐** | 0개 (KR/EN 혼합 헤딩 0) |

---

## 📝 프롬프트 이력

| 차수 | 시점 | 작업 |
|---|---|---|
| 1차 | 2026-07-09 06:54 | 코딩미션 scaffolding — README + placeholder index.html |
| 2차 | 2026-07-09 09:35 | OpenCode가 풀 시뮬레이터 본체 구현 (스넬 법칙 + 7-band 분산 + HUD) |
| 3차 | 2026-07-09 10:00 | Vercel 배포 + README 다층 v1.0 (현재) |

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 [MiniMax-M3](https://example.com) 모델과 OpenCode CLI 환경에서 생성되었습니다. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행했습니다.

- **코딩미션 참조 페이지**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
