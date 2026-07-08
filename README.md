# 🔬 Optics Lab — 빛의 굴절과 프리즘 (Prism Refraction & Dispersion)

> 어두운 공간에 삼각형 유리 프리즘을 배치하고 백색 광선을 비추면, **스넬의 법칙(Snell's Law)** 에 따라 빛이 굴절되고 분산(Dispersion)되어 무지개 스펙트럼으로 나뉘는 2D 광학 실험 시뮬레이터. 프리즘의 굴절률과 입사각을 슬라이더로 자유롭게 조절할 수 있습니다.

---

## 🎬 라이브 데모 (Live Demo)

- **GitHub Pages**: https://sigco3111.github.io/optics-prism-lab/ (배포 후 활성화)
- 로컬 실행: `index.html` 더블클릭 또는 `python3 -m http.server 8000`

---

## 🤖 생성 정보 (Attribution)

이 프로젝트의 코드는 **OpenCode CLI** + **MiniMax-M3** 모델로 생성되었습니다.

- **Tool**: [OpenCode](https://github.com/snymann/opencode) (AI 코딩 어시스턴트)
- **Model**: MiniMax-M3 (provider: minimax)
- **Generation mode**: 단일 HTML 임베드 (모든 의존관계 코드 1파일, CDN 없음)

프롬프트 원문은 본 README 하단 "프롬프트 이력" 절 참조.

---

## ✨ 주요 특징 (Features)

- 🔺 **삼각형 유리 프리즘** — 정삼각형 또는 임의 각도 프리즘, 회전 가능
- 🌈 **분산(Dispersion) 시뮬레이션** — R(적), G(녹), B(청) 3색 광선을 약간 다른 굴절률로 동시 캐스팅 → 무지개 스펙트럼
- 📐 **스넬의 법칙 정밀 계산** — `n₁ sin θ₁ = n₂ sin θ₂`로 입사/굴절각 정확 계산
- 🎚️ **인터랙티브 슬라이더** — 굴절률(n), 입사각(θ), 프리즘 회전, 분산 강도 실시간 조절
- 🌑 **어두운 실험실 분위기** — 검정 배경 + 글로우 광선 + 프리즘 유리 반사/투과 표현
- 📊 **각도/굴절률 실시간 HUD** — 입사각·굴절각·편각(Deviation) 측정값 표시
- 🌐 **단일 HTML** — 외부 빌드 도구 없이 브라우저에서 바로 실행

---

## 🚀 실행 방법 (Quick Start)

```bash
# 옵션 A: 브라우저에서 직접 열기
open index.html

# 옵션 B: 로컬 정적 서버 (권장 — 콘솔 로깅 깨끗)
python3 -m http.server 8000
# → http://localhost:8000 접속
```

> **참고**: 외부 의존성 0개 — 순수 HTML5 Canvas + Vanilla JavaScript. 모든 물리 계산과 렌더링이 `index.html` 하나에 포함됩니다.

---

## 🎮 조작법 (Controls)

| 입력 | 동작 |
|---|---|
| **굴절률 슬라이더 (n)** | 프리즘 유리 굴절률 1.3 ~ 2.5 |
| **입사각 슬라이더 (θ)** | 백색 광선의 입사각 0° ~ 80° |
| **프리즘 회전 슬라이더** | 프리즘 회전 각도 (광선 방향 최적화) |
| **분산 강도 슬라이더** | R/G/B 굴절률 차이 (무지개 폭) |
| **프리즘 종류 토글** | 정삼각형 ↔ 60° 프리즘 |
| **광선 토글 버튼** | 단색(R/G/B/White) ↔ 무지개 표시 |

---

## 🛠️ 기술 스택 (Tech Stack)

| 분류 | 선택 |
|---|---|
| **렌더링** | HTML5 Canvas 2D (glow 효과는 shadowBlur) |
| **물리 계산** | 순수 JS — 스넬의 법칙, 선-선 교차, 벡터 반사 |
| **광선 추적** | 2D Ray Tracing (Segment-Segment Intersection) |
| **분산 모델** | Cauchy 근사 — `n(λ) = A + B/λ²` |
| **입력** | 마우스(프리즘 드래그) + 슬라이더/버튼 |
| **번들링** | 없음 (단일 HTML) |
| **언어** | Vanilla JavaScript (ES6+) |

---

## 🎨 디자인 결정 (Design Choices)

1. **단일 HTML 임베드** — `canvas-static-site-pipeline` 패턴 준수. CDN 의존성 0개라 오프라인/내부 호스팅 즉시 전환 가능.
2. **삼각형 = 정삼각형 기본** — 60° 각도의 정삼각형이 분산 효과가 가장 잘 보이는 클래식 광학 실험 조건. 다른 각도로 바꾸면 내부 반사(TIR) 시연 가능.
3. **분산 = R/G/B 3색 이중 굴절률** — 풀 연속 스펙트럼은 비싸고 시각적 차이가 미미. R/G/B 3색만 캐스팅해도 무지개 효과가 명확.
4. **선-선 교차 직접 계산** — 매 프레임 광선-프리즘 엣지 교차를 직접 계산 (물리엔진 불필요). 2D라 `ccw` 부호 비교로 교차 판정.
5. **편각(Deviation) 표시** — 입사광 방향과 출사광 방향의 각도 차를 HUD로 표시 → "프리즘이 빛을 얼마나 휘게 하는가" 정량 확인.
6. **글로우 효과** — Canvas `shadowBlur`로 광선이 어두운 배경에서 빛나게 표현. `globalCompositeOperation = 'lighter'`로 가산 혼합.

---

## 🧠 동작 원리 (How It Works)

```
백색 광선 (입사각 θ₁)
        │
        ▼
   ┌─────────────────────────────────┐
   │ 1. 광선 vs 프리즘 좌측 엣지 교차 │ ← Segment Intersection
   │ 2. 교차점에서 법선(Normal) 계산  │ ← 엣지 방향의 수직 벡터
   │ 3. 스넬의 법칙 굴절 계산         │ ← n₁sinθ₁ = n₂sinθ₂
   │ 4. R/G/B 각각 다른 n 으로 3번    │ ← 분산 (Dispersion)
   └─────────────────────────────────┘
        │
        ▼
   프리즘 내부 (굴절된 R/G/B 광선)
        │
        ▼
   ┌─────────────────────────────────┐
   │ 5. 광선 vs 프리즘 우측 엣지 교차 │
   │ 6. 다시 굴절 계산 (n₂→n₁)        │
   │ 7. 출사 방향 벡터 도출            │
   │ 8. 편각(Deviation) 계산          │
   └─────────────────────────────────┘
        │
        ▼
   R / G / B 분리된 출사광 → 무지개 스펙트럼
```

핵심은 **스넬의 법칙 + 선-선 교차**입니다.
- `n₁sinθ₁ = n₂sinθ₂` → 굴절각 `θ₂ = asin(n₁sinθ₁/n₂)`
- 내부 전반사(TIR) 판정: `n₁sinθ₁ > n₂` 면 굴절 없이 반사
- 분산: Cauchy 근사로 R(n≈1.513) / G(n≈1.520) / B(n≈1.532) 차등 적용

---

## 🔬 검증 (Verification)

- `python3 -m http.server`로 로컬 서빙 후 페이지 로드 확인
- 슬라이더 조절 시 → 굴절각·편각 HUD 수치가 즉시 갱신
- 굴절률 n↑ → 출사광이 더 많이 휘어짐 (스넬 법칙 일치)
- 입사각 0° (수직 입사) → 굴절 없이 직진
- 입사각 > 임계각 → 프리즘 내부에서 전반사(TIR) 발생
- 콘솔 에러 0개 확인
- 비트-퍼펙트 사이즈: `curl -sS -w "%{size_download}" -o /dev/null http://localhost:8000/` ≡ `wc -c < index.html`

---

## 📝 프롬프트 이력 (Prompt Log)

원본 미션 지시 (2026-07-09):

> 어두운 공간에 삼각형 유리 프리즘을 배치하고 백색 광선을 비췄을 때, 스넬의 법칙(Snell's Law)에 따라 빛이 굴절되고 분산되어 무지개 스펙트럼(Dispersion)으로 나뉘는 광학 실험을 시뮬레이션하되, 프리즘의 굴절률과 빛의 입사각을 조절할 수 있는 인터페이스를 포함해줘.
>
> **Implementation Advice**: Use **HTML5 Canvas**. Implement Ray Tracing logic in 2D. Calculate ray-line intersections. For dispersion (rainbow), cast multiple rays (R, G, B) with slightly different refractive indices. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.

---

## 📄 License

MIT