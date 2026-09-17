# 🔬 GitHub Research Addendum — September 2026

> Live audit of AR/MR/Spatial Computing GitHub repositories, issues, and contributors surfaced during podcast pre-production research.

---

## Most Active Repositories Surveyed

### Tier 1 — Massive Community (10k+ ⭐)

| Repo | Stars | Language | Focus |
|---|---|---|---|
| `AR-js-org/AR.js` | 5,988 | JavaScript | Web AR: marker, image, location-based |
| `aframevr/aframe` | 17,638 | JavaScript | Web framework for 3D/AR/VR experiences |
| `jeromeetienne/AR.js` (archived) | 15,791 | HTML | Original AR.js — moved to AR-js-org |

### Tier 2 — Significant Community (1k–5k ⭐)

| Repo | Stars | Language | Focus |
|---|---|---|---|
| `google/lullaby` | 1,197 | C++ | VR/AR dev kits — spatial audio, ECS architecture |
| `hiukim/mind-ar-js` | 2,731 | JavaScript | Web AR: image & face tracking via TF.js |
| `jeeliz/jeelizFaceFilter` | 2,938 | JavaScript | WebGL face tracking & AR filters |
| `exyte/ARTetris` | 1,524 | Swift | ARKit + SceneKit AR game |
| `thomwolf/Magic-Sand` | 1,018 | C++ | AR sandbox software |
| `ventusff/neurecon` | 861 | Python | Neural rendering 3D reconstruction |
| `artoolkitx/artoolkitx` | 511 | C | Native AR tracking (iOS/Android/macOS/Windows) |

---

## Key Contributors & Potential Guests

| Name | GitHub | Repo | Role | Why They'd Be Great on the Show |
|---|---|---|---|---|
| **Jérôme Etienne** | `jeromeetienne` | AR.js (15.8k ⭐) | Creator | Web AR pioneer; built the most-used open-source web AR library; deep thinker on perceptual thresholds in browser AR |
| **Nicolò Carpignoli** | `nicolocarpignoli` | AR.js (5.9k ⭐) | Former Maintainer | Kept AR.js alive for years; community building; transition from individual to org governance |
| **Ricardo Cabello** | `brqx` | A-Frame (17.6k ⭐) | Creator | Built the web's leading 3D/VR framework; entity-component architecture philosophy; WebXR advocacy |
| **Hideki Kimura** | `hiukim` | MindAR (2.7k ⭐) | Creator | On-device ML-based AR tracking; TensorFlow.js integration; production-ready AR for the web |
| **Maluoi** | Maluoi | StereoKit (1.1k ⭐) | Maintainer | XR engine with OpenXR + WebXR dual backend; performance optimization for spatial computing |
| **Diego Marcos** | `dmarcos` | A-Frame | Maintainer | WebXR runtime architecture; cross-platform VR/AR rendering |
| **Don McCurdy** | `donrmccurdy` | A-Frame | Maintainer | 3D rendering pipeline; AR/VR interaction patterns |
| **Kevin Ngo** | `andgokevin` | A-Frame | Maintainer | WebXR input systems; spatial interaction design |

---

## Hottest Open Issues & Debates (from AR.js — the most active web AR repo)

### 🔥 Issue #498 — "[bug report] Stretched camera feed" (50 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/498
- **Topic**: Perceptual rendering calibration — the camera feed appears stretched on certain devices, breaking the spatial alignment between real and virtual content
- **Podcast angle**: When the camera feed itself is distorted, the entire perceptual model collapses. This isn't just a rendering bug — it's a *reality calibration* failure.

### 🔥 Issue #278 — "Content 'sticking to' camera on certain devices" (40 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/278
- **Labels**: bug, location based
- **Topic**: AR content fails to detach from the camera on some Android devices — the virtual content "sticks" to the camera view instead of being anchored in the real world
- **Podcast angle**: This is a *presence* failure. When virtual content sticks to the camera, the brain can't separate real from virtual — the fundamental promise of AR breaks.

### 🔥 Issue #217 — "Markerless tracking without Tango (/iOS equivalent)" (22 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/217
- **Labels**: enhancement, question
- **Topic**: AR.js relies on marker-based or location-based tracking, but there's no markerless SLAM solution for the web. Tango was Google's answer but it failed commercially. iOS has ARKit but no open web equivalent.
- **Podcast angle**: The missing piece of web AR is true 6-DoF spatial understanding. Without markerless tracking, web AR is stuck in the "flat card" era while native apps have moved to "spatial computing."

### 🔥 Issue #288 — "Markerless location-based AR (more realistic placement of objects)" (11 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/288
- **Labels**: enhancement, location based
- **Topic**: Location-based AR currently snaps objects to GPS coordinates (~5m accuracy). For perceptual realism, you need centimeter-accurate placement using visual-inertial odometry.
- **Podcast angle**: GPS-level accuracy is not spatial computing. The difference between "I see a virtual coin on the sidewalk" and "I see a virtual coin precisely on that crack" is the difference between AR and magic.

### 🔥 Issue #193 — "Playing a video on Safari 14 slows down tracking (Framerate)" (11 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/193
- **Topic**: Playing video content in an AR scene causes framerate drops on Safari, directly impacting the perceptual experience — lag = sickness
- **Podcast angle**: This is perceptual latency in its purest form. The moment video playback steals rendering budget from tracking, the brain detects the irregularity. Frame pacing matters more than frame rate.

### 🔥 Issue #466 — "DeviceOrientationControls iOS initial heading/alpha correction" (26 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/466
- **Labels**: bug, location based, iOS
- **Topic**: iOS device orientation reporting has heading drift and alpha correction issues that break spatial alignment in location-based AR
- **Podcast angle**: The IMU (inertial measurement unit) is the bridge between the physical and digital worlds. When the IMU lies, the virtual world drifts.

### 🔥 Issue #40 — "Raycaster is off center or scaled based on window size" (27 comments)
- **URL**: https://github.com/AR-js-org/AR.js/issues/40
- **Labels**: bug, assignee: kalwalt
- **Topic**: The raycaster (used for raycasting from camera to world) is miscalibrated relative to the viewport, causing misalignment between user intent and virtual object interaction
- **Podcast angle**: Interaction Raycaster misalignment means the user points at something and the virtual object reacts to a different point. This is a *perceptual proprioception* failure — the brain's hand-eye coordination is violated.

---

## Google Lullaby — Spatial Audio & VR Architecture

### Repo Overview
- **URL**: https://github.com/google/lullaby
- **Stars**: 1,197 | **Language**: C++ | **License**: Apache-2.0
- **Key Feature**: Full 3D VR environments including **geometric worlds, panoramic images, and spatial audio**
- **Architecture**: Entity-Component-System for efficient runtime performance

### Open Issues
Only 2 open issues — the project is relatively stable but no longer actively accepting PRs (Google internal use only). Key areas:
- Issue #13: Build system questions
- Issue #14: VectorPacked compilation error

### Podcast Angle
Lullaby is a case study in **closed-source-after-open-source**: Google open-sourced the libraries but stopped accepting external contributions. The spatial audio architecture (-nav-room, audio renderer, spatial audio sources) is documented but not extensible. This raises the question: **can open-source spatial audio ever compete with proprietary native implementations when the open-source project is abandoned by its corporate steward?**

---

## Cross-Research Synthesis: The Three Perceptual Fault Lines

### 1. Calibration Fault (Episode 1 Extend)
玻璃般的现实与数字世界的对齐精度决定了感知是否成立。AR.js issues #498, #278, #40, #466 all describe calibration failures — not "features missing" but "reality breaking." The camera feed stretches, content sticks, the raycaster misaligns. These aren't bugs; they're *perceptual contradictions* that the brain treats as reality errors.

### 2. Tracking Fault (Episode 1 Extend)
Issues #217 and #288 reveal that web AR lacks true spatial understanding. Without markerless SLAM, web AR cannot anchor virtual objects to the physical world with the precision the brain expects. GPS accuracy is 5 meters; the perceptual threshold for "this virtual object is really there" is centimeters.

### 3. Latency Fault (Episode 1 Core + Episode 2 Cross)
Issue #193 (Safari video → framerate drop) is the smoking gun: when one subsystem steals budget from another, the brain detects the resulting irregularity before it can name it. This connects to the broader question of whether WebXR's single-threaded rendering architecture is fundamentally flawed for multi-sensory perceptual delivery.

---

## Suggested New Episode Extensions

### Episode 1 Extension: "Calibration Reality"
Add a segment on the calibration fault line — how AR.js issues #498, #278, and #40 demonstrate that "correct" rendering isn't enough; the camera feed, the raycasting, and the spatial anchoring must all be calibrated to the brain's perceptual thresholds. Guest: `jeromeetienne` or `nicolocarpignoli`.

### Episode 2 Extension: "Abandoned Open Audio"
Use Lullaby as a case study — what happens when a company open-sources a spatial audio stack and then walks away? Can community-maintained open audio compete with Apple'sSpatial Audio and Meta's Resonance Audio? Guest: `Maluoi` or a Lullaby contributor.

### Episode 3 Extension: "Web AR's Markerless Gap"
The #217 issue — no markerless SLAM on the web — is the biggest unpaid debt in web spatial computing. Without it, the web platform is relegated to "VR cards in space" while native apps build true spatial computing. What does it take to get markerless tracking in the browser? Guest: `hiukim` (MindAR creator, who solved on-device tracking for the web).

---

*This addendum was generated from a live GitHub audit on September 2026. See `EPISODE_OUTLINE.md` for the canonical episode structure and `HOT-DEBATES-AUDIT.md` for the full cross-repo issue tracker.*