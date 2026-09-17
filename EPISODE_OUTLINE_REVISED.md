# 🎙️ The Future of Human Perception — Episode Outline (Sept 2026 GitHub Audit)

> _A collaborative podcast series exploring the engineering and human science behind how technology reshapes perception._

**Last updated: September 2026 — sourced from a live GitHub audit of AR.js, A-Frame, Google Lullaby, three.js, MindAR, and Jeeliz FaceFilter.**

---

## 📋 Source & Methodology

This outline was built from a live audit of the most active AR/MR/Spatial Computing
repositories on GitHub, surfacing the **hottest open debates** (by issue activity,
reactions, and comment volume) and identifying **leading contributors** who are
shipping the code that defines our perceptual future.

### Research Backbone — Most Active Repos

| Repo | Stars | Focus | Key Debates surfacing from Issues |
|---|---|---|---|
| **[AR-js-org/AR.js](https://github.com/AR-js-org/AR.js)** | 5,988 ⭐ | Web AR (marker, image, location) | Tracking drift, camera pipeline latency, iOS sensor fusion, NFT reliability |
| **[aframevr/aframe](https://github.com/aframevr/aframe)** | 17,638 ⭐ | Web VR/AR framework (A-Frame) | WebXR runtime performance, hand-controls misalignment, spatial anchor stability, HoloLens UX |
| **[mrdoob/three.js](https://github.com/mrdoob/three.js)** | 115,601 ⭐ | Foundational 3D library | Underpins all WebXR/AR rendering; performance & GPU latency |
| **[google/lullaby](https://github.com/google/lullaby)** | 1,197 ⭐ | Google VR/AR C++ engine | Spatial audio, Entity-Component-System architecture, Material VR UI |
| **[hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js)** | 2,731 ⭐ | Web AR (image + face tracking) | TensorFlow.js tracking latency, multi-image tracking performance |
| **[jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter)** | 2,938 ⭐ | Real-time face detection/tracking | Multi-face tracking latency, AR face filter rendering pipeline |

### Research Backbone — Key Contributors & Potential Guests

| Name | GitHub | Role | Why They're a Great Guest |
|---|---|---|---|
| **Jerome Etienne** | @jeromeetienne | Creator of AR.js | Founded the open-source Web AR movement; deep perspective on marker-based vs. markerless tracking |
| **Nicolò Carpignoli** | @nicolocarpignoli | AR.js maintainer | Kept AR.js alive through its transition to community ownership; knows the Web AR ecosystem intimately |
| **Diego Marcos** | @dmarcos | A-Frame co-maintainer | Filed the critical WebXR-on-Chrome issue (#4709, 106 comments); deeply embedded in WebXR standards work |
| **Don McCurdy** | @donrmccurdy | A-Frame co-maintainer | Built the hand-controls & controller systems in A-Frame; firsthand experience with tracking-misalignment bugs |
| **Kevin Ngo** | @andgokevin | A-Frame co-maintainer | Focused on VR UI / Interaction design; authored the "Building UIs in VR" docs guide |

---

## 🎧 Episode 1 — "Latency and the Perceptual Threshold"

**Core Question:** Can foveation trick the brain into forgiving lag?

### Hot Debates (from GitHub Issues)

| Debate | Source | Key Points |
|---|---|---|
| **Stretched camera feed — rendering pipeline latency** | AR.js #498 (50 comments) | Camera frame distribution causes visual stretch; directly impacts motion-to-photon latency |
| **Content "sticking to" camera on certain devices** | AR.js #278 (40 comments) | AR content doesn't match real-world motion — tracking-to-render pipeline delay on mid-range phones |
| **Webcam NotReadable errors on Samsung Galaxy** | AR.js #121 (29 comments) | Hardware access contention adds unpredictable latency to the AR pipeline |
| **iOS DeviceOrientation heading correction** | AR.js #466 (26 comments) | Sensor fusion on iOS has initial heading drift — the perceptual cost of imprecise orientation |
| **WebXR not working on Chrome Desktop** | A-Frame #4709 (106 comments) | The most-commented A-Frame issue — WebXR runtime performance & compatibility gaps |
| **Initial camera rotation incorrect on Chrome/Android** | A-Frame #3650 (25 comments) | Motion-to-photon mismatch on mobile — the 20ms rule violated before rendering even starts |
| **Hand-controls misaligned with HTC Vive controllers** | A-Frame #5305 (20 comments) | Tracking latency causes visible controller drift — breaking presence |
| **Samsung S8 double/blurry vision in VR (Cardboard)** | A-Frame #3223 (22 comments) | Rendering latency causes stereoscopic misalignment — direct path to motion sickness |

### Key Concepts
- **Motion-to-Photon Latency**: The end-to-end delay from physical movement to pixel change. The industry "magic number" is <20ms.
- **Foveated Rendering**: Rendering only the foveal region at full resolution — can it mask latency?
- **Prediction & Warping**: Techniques to extrapolate head position and pre-render what the user will see.
- **Sensor Fusion Drift**: When IMU + camera + GPS pipelines disagree, the perceptual result is "something feels wrong."

### Suggested Guests
- **Jerome Etienne** — From AR.js: how markerless tracking pipelines introduce variability in latency budgets
- **Don McCurdy** — From A-Frame: the hand-controls misalignment story as a case study in tracking latency
- **Diego Marcos** — From A-Frame: the WebXR-on-Chrome saga as a window into runtime performance gaps

### Reading & Listening Queue
- AR.js #498: [Stretched camera feed](https://github.com/AR-js-org/AR.js/issues/498)
- A-Frame #4709: [WebXR not working on Chrome Desktop Windows](https://github.com/aframevr/aframe/issues/4709)
- A-Frame #5305: [hand-controls misaligned with HTC Vive controllers](https://github.com/aframevr/aframe/issues/5305)
- AR.js #278: [Content 'sticking to' camera on certain devices](https://github.com/AR-js-org/AR.js/issues/278)

---

## 🎧 Episode 2 — "Spatial Sound and the Third Dimension"

**Core Question:** Why does spatial audio lag so far behind visual tracking in the web?

### The Gap We're Investigating

The WebXR Device API specification is overwhelmingly **visual-only** for spatial interaction.
There is **no standardized spatial audio API in WebXR**. Meanwhile:

- **Google Lullaby** supports spatial audio in its VR engine (C++), but the implementation
  isn't exposed to the web.
- **A-Frame** has a positional-audio component, but it's community-maintained, not core.
- **HRTF (Head-Related Transfer Function)** rendering is well-researched in academia but
  barely accessible in real-time web engines.

### Hot Debate Topics (surfaced from cross-repo research)

| Debate | Key Points |
|---|---|
| **WebXR spec is visual-only for spatial audio** | No spatial audio entities in the WebXR Device API; developers must roll their own Web Audio + HRTF pipeline |
| **Lullaby's spatial audio exists behind a C++ wall** | "Support for full 3D VR environments, including geometric worlds, panoramic images, and spatial audio" — but only in Google's internal C++ framework |
| **Positional audio in A-Frame is a community component** | Not maintained by core devs; inconsistent across versions; no spatial anchor integration |
| **HRTF personalization problem** | HRTFs are individualized — generic templates sound "off" for most users, reducing presence |

### Key Concepts
- **The Audio Presence Paradox**: Visual tracking latency is measured in milliseconds; spatial audio rendering latency is effectively **unmeasured** because no standard exists to even quantify it.
- **HRTF**: How your ears filter sound based on head shape and position — the key to 3D audio presence, but hard to compute in real-time on the web.
- **Ambisonics vs. HRTF**: Binaural rendering (HRTF) for headphones vs. first-order ambisonics for speakers — each has tradeoffs for presence and compute cost.
- **Web Audio API + PannerNode**: The current web standard for spatial audio, but it's a simplified model that doesn't capture true HRTF behavior.

### Suggested Guests
- **Google Lullaby maintainer** (TBD) — How Google built spatial audio internally and why it hasn't reached the web
- **Web Audio API community member** — The PannerNode limitations story
- **Academic HRTF researcher** — Personalization vs. generic templates for presence

### Reading & Listening Queue
- Google Lullaby: [Spatial audio in the README](https://github.com/google/lullaby)
- A-Frame positional-audio component (search GitHub for `aframe-component-positionitional-audio`)
- W3C WebXR spec: [WebXR Device API](https://immersive-web.github.io/webxr/) — note the absence of spatial audio entities

---

## 🎧 Episode 3 — "Interfaces Beyond the Flat Screen"

**Core Question:** Is the WebXR spec blind to non-visual perception?

### Hot Debates (from GitHub Issues)

| Debate | Key Points |
|---|---|
| **Spatial anchors cause scale to be overruled** | MR spatial understanding is fragile — anchoring content to the real world still has drift/fidelity problems (A-Frame #5630) |
| **Spatial anchor space vs. entity position** | The spec gives spatial anchors position+orientation, but developers need finer control (A-Frame #5633) |
| **HoloLens support (stalled)** | MR interface support on HoloLens was attempted years ago — never completed; the WebXR→HoloLens bridge remains broken (A-Frame #3513, #4120) |
| **Windows Mixed Reality controllers** | MR input support was merged but has drifted; the spec doesn't capture the full MR controller capability space (A-Frame #3013) |
| **Dynamic switch between controller & hand models** | MR interaction design needs to smoothly transition between input paradigms (A-Frame #5373) |
| **Building UIs in VR (docs still a guide)** | Kevin Ngo's UI-in-VR documentation was never completed — MR interface design is still an open problem (A-Frame #2281) |

### Key Concepts
- **Registration & Drift**: The fundamental MR problem — virtual content must stay registered with the physical world, but environmental changes cause drift.
- **Spatial Anchors**: Cloud-anchored content that persists across sessions — but scale/orientation fidelity remains buggy.
- **Mixed Reality Input Models**: Controllers, hand tracking, gaze, and voice — each creates a different paradigm; WebXR doesn't unify them well.
- **The "Flat Screen Bias" in WebXR**: The spec was designed for VR headset rendering; MR concepts are bolted on rather than built in.

### Suggested Guests
- **Kevin Ngo** (@andgokevin) — A-Frame co-maintainer; authored the "Building UIs in VR" docs guide; can speak to the MR interface design gap
- **Don McCurdy** (@donrmccurdy) — A-Frame co-maintainer; built hand-controls & controller systems; can speak to MR input models
- **HoloLens/MR developer** (TBD) — The HoloLens + WebXR bridge was never completed; a practitioner can speak to the real-world gap

### Reading & Listening Queue
- A-Frame #5630: [Spatial anchor causes scale to get overruled](https://github.com/aframevr/aframe/issues/5630)
- A-Frame #3513: [HoloLens Support](https://github.com/aframevr/aframe/issues/3513)
- A-Frame #3013: [Windows Mixed Reality controllers](https://github.com/aframevr/aframe/pull/3013)
- A-Frame #5373: [Dynamic switch between controller and hand models](https://github.com/aframevr/aframe/issues/5373)

---

## 🗓️ Production Timeline

| Milestone | Target | Status |
|---|---|---|
| Research complete | ✅ Sept 2026 | GitHub audit done |
| Episode 1 script | Oct 2026 | Drafting — see [Issue #43](https://github.com/bro26man-hash/human-perception-podcast/issues/43) |
| Episode 1 recording | Oct 2026 | Scheduling guests |
| Episode 2 script | Nov 2026 | Research phase — see [Issue #44](https://github.com/bro26man-hash/human-perception-podcast/issues/44) |
| Episode 2 recording | Nov 2026 | Scheduling guests |
| Episode 3 script | Dec 2026 | Research phase — see [Issue #45](https://github.com/bro26man-hash/human-perception-podcast/issues/45) |
| Episode 3 recording | Dec 2026 | Scheduling guests |

---

## 🤝 How to Contribute

1. **Pick an episode issue** (`#43`, `#44`, or `#45`)
2. **Add research findings, issue links, or potential guest suggestions** as comments
3. **Submit a PR** with updated episode outlines or new research
4. **Tag potential guests** and track outreach status in the issue comments

---

_Last updated: September 2026 — sourced from a live GitHub audit of AR.js, A-Frame, Google Lullaby, three.js, MindAR, and Jeeliz FaceFilter._
