# 👥 Guest Directory — The Future of Human Perception

> Potential guests identified from GitHub research across AR/MR/Spatial Computing communities.

---

## Tier 1 — Confirmed高分 Contributors (from GitHub issue analysis)

### Jerome Etienne — @jeromeetienne
- **GitHub**: [jeromeetienne](https://github.com/jeromeetienne)
- **Role**: Creator of AR.js (15,791 ⭐ on old repo; 5,988 ⭐ on AR-js-org/AR.js)
- **Expertise**: Marker-based AR, markerless AR, Web AR, location-based AR
- **Why a great guest**: Founded the open-source Web AR movement. Can speak to how markerless tracking pipelines introduce variability in latency budgets (AR.js #190: "Is Markerless AR possible?" had 59 comments, #503 had 24 comments — both foundational debates).
- **Episode fit**: Episode 1 (Latency) — the AR.js tracking pipeline stories are unmatched.

### Diego Marcos — @dmarcos
- **GitHub**: [dmarcos](https://github.com/dmarcos)
- **Role**: A-Frame co-maintainer
- **Expertise**: WebXR runtime, A-Frame architecture, VR performance
- **Why a great guest**: Filed the critical WebXR-on-Chrome issue (#4709, **106 comments** — the most-commented A-Frame issue). Deeply embedded in WebXR standards work.
- **Episode fit**: Episode 1 (Latency) — the WebXR runtime performance gap story.
- **Also filed**: A-Frame #5305 (hand-controls misalignment), #5658 (3D Gaussian splats PR — cutting edge!)

### Don McCurdy — @donrmccurdy
- **GitHub**: [donrmccurdy](https://github.com/donrmccurdy)
- **Role**: A-Frame co-maintainer
- **Expertise**: Hand tracking, controller systems, MR input
- **Why a great guest**: Built the hand-controls & controller systems in A-Frame. Firsthand experience with tracking-misalignment bugs (#5305, 20 comments).
- **Episode fit**: Episode 3 (Interfaces) — MR input models; also Episode 1 (Latency) via #5305.

### Nicolò Carpignoli — @nicolocarpignoli
- **GitHub**: [nicolocarpignoli](https://github.com/nicolocarpignoli)
- **Role**: AR.js maintainer (moved project to AR-js-org)
- **Expertise**: Web AR ecosystem, community building
- **Why a great guest**: Kept AR.js alive through its transition to community ownership. Knows the Web AR ecosystem's pain points from the inside (issues #544 on NFT tracking, #469 "Ensure the future of AR.js" with 94 comments).
- **Episode fit**: Episode 1 (Latency) — can contextualize the tracking challenges.

### Kevin Ngo — @andgokevin
- **GitHub**: [andgokevin](https://github.com/andgokevin)
- **Role**: A-Frame co-maintainer
- **Expertise**: VR UI design, interaction design
- **Why a great guest**: Authored "Building UIs in VR" documentation guide (#2281, 23 comments — still incomplete after 9 years). Focused on the interface design gap.
- **Episode fit**: Episode 3 (Interfaces) — MR UI design.

---

## Tier 2 — Emerging Voices (from repo analysis)

### Hiuk Kim — @hiukim
- **GitHub**: [hiukim](https://github.com/hiukim)
- **Role**: Creator of MindAR (2,731 ⭐)
- **Expertise**: TensorFlow.js-based image tracking, face tracking for the web
- **Why relevant**: MindAR was specifically recommended in the AR.js README as the "brand new OSS Web AR JS library around." Could discuss the evolution from AR.js to MindAR and where image tracking latency stands.

### jeeliz团队 — @jeeliz
- **GitHub**: [jeeliz](https://github.com/jeeliz)
- **Role**: Creators of jeelizFaceFilter (2,938 ⭐)
- **Expertise**: Real-time multi-face detection, tracking, AR face filters
- **Why relevant**: Face tracking is a different form of perceptual interface — how do we design for eyes rather than hands?

### Google Lullaby team — @google (org)
- **GitHub**: [google/lullaby](https://github.com/google/lullaby)
- **Role**: Google's VR/AR C++ engine
- **Expertise**: Spatial audio, ECS architecture, Material VR, multiplatform VR
- **Why relevant**: "Support for full 3D VR environments, including geometric worlds, panoramic images, and spatial audio" — but it's internal only. The gap between what Google can build internally and what the web can access is a huge story.
- **Note**: "We are unable to take your pull requests at this time" — so the roadmap is opaque. An interview request would be news.

---

## Tier 3 — Research & Cross-Industry (to be identified)

| Role | Expertise | Episode | Status |
|---|---|---|---|
| Academic HRTF researcher | Spatial audio presence, personalization | Episode 2 | 🔍 To find |
| Web Audio API & PannerNode contributor | Browser audio spec limitations | Episode 2 | 🔍 To find |
| HoloLens/MR practitioner | WebXR→HoloLens bridge gap | Episode 3 | 🔍 To find |
| WiVRn maintainer (xytovl) | OpenXR streaming, stutter analysis | Episode 1 | 🔍 Bonus pick |
| ALVR developer (jd-3d) | VR streaming latency forensics | Episode 1 | 🔍 Bonus pick |

---

## Cross-Link: Key GitHub Issues for Guest Briefing

| Issue | Repo | Topic | Guest Angle |
|---|---|---|---|
| [#498](https://github.com/AR-js-org/AR.js/issues/498) | AR.js | Stretched camera feed (50 comments) | Jerome Etienne — pipeline latency stories |
| [#190](https://github.com/AR-js-org/AR.js/issues/190) | AR.js | Is Markerless AR possible? (59 comments) | Jerome Etienne — markerless vs. marker debates |
| [#4709](https://github.com/aframevr/aframe/issues/4709) | A-Frame | WebXR not working on Chrome (106 comments!) | Diego Marcos — runtime performance gap |
| [#5305](https://github.com/aframevr/aframe/issues/5305) | A-Frame | Hand-controls misaligned (20 comments) | Don McCurdy — tracking latency in VR |
| [#5630](https://github.com/aframevr/aframe/issues/5630) | A-Frame | Spatial anchor scale overruled | Don McCurdy / Kevin Ngo — MR registration |
| [#3513](https://github.com/aframevr/aframe/issues/3513) | A-Frame | HoloLens Support (stalled) | HoloLens practitioner — MR bridge gap |
| [#2281](https://github.com/aframevr/aframe/issues/2281) | A-Frame | UI in VR docs incomplete | Kevin Ngo — MR interface design gap |

_Last updated: September 2026_
