# 🎙️ The Future of Human Perception — Episode Outline
## Research-Backed Edition | Sourced from GitHub AR/MR/Spatial Computing Communities

---

## 📋 Series Overview

**Mission:** Explore the engineering and human science behind how technology reshapes perception — by tracking the hottest open debates in the most active augmented reality, spatial computing, and mixed reality GitHub repositories, and interviewing the developers and researchers pushing those debates forward.

**Production Hub:** This repository manages episode planning, guest research, and debate tracking via GitHub Issues.

---

## 🔬 Research Methodology

All episode topics and guest candidates were identified by:
1. **Repository mining** — Surveying the most-active AR/MR/Spatial Computing repos on GitHub (by stars, recent push activity, and issue engagement)
2. **Issue archaeology** — Digging into open issues and discussions to surface the hottest debates (filtered by reactions, comments, and recency)
3. **Contributor mapping** — Identifying prominent developers and researchers by their contributions, maintainer roles, and community influence

---

## 📡 Repositories Surveyed

| Repository | Stars | Language | Focus Area | Last Active |
|---|---|---|---|---|
| [**AR-js-org/AR.js**](https://github.com/AR-js-org/AR.js) | 5,988 | JavaScript | Web AR (marker, image, location tracking) | Sept 2026 |
| [**jeromeetienne/AR.js**](https://github.com/jeromeetienne/AR.js) | 15,791 | HTML | Legacy AR.js (moved to org) | Sept 2026 |
| [**google/lullaby**](https://github.com/google/lullaby) | 1,197 | C++ | VR/AR framework w/ spatial audio | Sept 2026 |
| [**microsoft/xr-development-for-beginners**](https://github.com/microsoft/xr-development-for-beginners) | 564 | Vue | 8-week XR development curriculum | Sept 2026 |
| [**hiukim/mind-ar-js**](https://github.com/hiukim/mind-ar-js) | 2,733 | JavaScript | Web AR with TensorFlow.js | Sept 2026 |
| [**jeeliz/jeelizFaceFilter**](https://github.com/jeeliz/jeelizFaceFilter) | 2,938 | JavaScript | WebGL face-tracking AR filters | Sept 2026 |
| [**Exyte/ARTetris**](https://github.com/Exyte/ARTetris) | 1,524 | Swift | ARKit + SceneKit AR game | Sept 2026 |

---

## 👥 Potential Guest Contributors

### Tier 1 — Pioneers & Maintainers

| Name | GitHub | Role | Expertise | Episode Fit |
|---|---|---|---|---|
| **Jerome Etienne** | @jeromeetienne | AR.js Creator | Web AR pioneering, marker-based tracking, location-based AR | Ep 1, Ep 3 |
| **Nicolò Carpignoli** | @nicolocarpignoli | AR.js Maintainer | Web AR infrastructure, NFT image tracking, cross-browser AR | Ep 1, Ep 2 |
| **Hiukim** | @hiukim | MindAR.js Creator | TensorFlow.js AR, face/image tracking, ML-powered perception | Ep 1, Ep 2 |

### Tier 2 — Active Contributors & Advocates

| Name | GitHub | Role | Expertise | Episode Fit |
|---|---|---|---|---|
| **Nick W** | @nickw1 | AR.js Maintainer and lead issue filer | Markerless location-based AR, multi-camera support, iOS/Safari device orientation | Ep 1, Ep 3 |
| **Kalwalt** | @kalwalt | AR.js-next ECS lead | Entity-Component-System architecture for AR, modular AR frameworks | Ep 2, Ep 3 |
| **Yann Klein** | @yannklein | AR.js physics integrator | AR-physics integration, A-Frame interaction models | Ep 2 |

### Tier 3 — Educators & Curriculum Designers

| Name | Role | Expertise | Episode Fit |
|---|---|---|---|
| **April Speight** | Microsoft XR Curriculum Co-Author | Spatial design, comfort/cybersickness pedagogy, XR interaction design | Ep 3 |
| **Gustavo Cordido** | Microsoft XR Curriculum Co-Author | XR development fundamentals, Unity-based MR training | Ep 2, Ep 3 |

---

## 🔥 Hot Debates Uncovered from GitHub Issues

### Debate 1: The 20ms Perceptual Latency Gap
**Source:** AR.js Issues #302 (iOS/Safari device orientation), #26 (multi-camera), #288 (markerless placement)

> *"Can the brain forgive lag if foveation rendering tricks the perceptual system?"*

- **The problem:** Motion-to-photon latency above ~20ms triggers vection sickness and breaks the illusion of presence. AR.js's device-orientation code hits Safari-specific bugs (#302, open since 2021) that reintroduce latency on iOS.
- **The debate:** Foveated rendering and predictive tracking can mask latency for central vision, but peripheral awareness still detects mismatch. Does the WebXR spec's lack of a standardized latency budget mean every Web AR app is shipping a different perceptual experience?
- **Key voices:** @nickw1 (filing iOS/Safari issues since 2021), @Nicolò Carpignoli (maintaining cross-browser compatibility)

### Debate 2: The Markerless Tracking Gap in Web AR
**Source:** AR.js Issue #288 — "Markerless location-based AR (more realistic placement of objects)" (open since June 2021, 11 comments, assigned to @nickw1)

> *"Web AR can place objects on horizontal planes — but can it understand what those objects mean?"

- **Current state:** AR.js supports marker-based and location-based AR, but markerless plane understanding remains rudimentary. Objects "dangle randomly above the image" per Issue #274.
- **The gap:** Native ARKit/ARCore understand semantic scenes (walls, floors, furniture). Web AR.js can only do basic horizontal detection. The jump from "I see a plane" to "I know what's in the room" is the next perceptual frontier.
- **Key voices:** @nickw1 (advocating for markerless since 2021), @jeromeetienne (original architecture decisions)

### Debate 3: The Abandoned Open Audio Pipeline
**Source:** google/lullaby spatial audio architecture; WebXR spec absence of spatial audio bindings

> *"Why does the WebXR spec define visual presence but leave spatial audio to proprietary plugins?"

- **The paradox:** Lullaby (Google's C++ VR framework) includes full spatial audio support, ambisonics, and HRTF processing — but the project is effectively dormant (only 2 open issues since 2018). Meanwhile, the WebXR Device API specification has no spatial audio session type.
- **The debate:** The Web is built for audio (HTML5 `<audio>`, Web Audio API). Why is spatial audio — the sense that most powerfully creates "presence" — the missing sense in immersive web? Is this a spec gap or a business gap?
- **Key voices:** Lullaby contributors; WebXR Working Group members; @hiukim (could bridge ML-based audio estimation)

### Debate 4: Mixed Reality Interfaces — Gaze, Hands, or Controllers?
**Source:** Microsoft XR Curriculum Units 3–4 (Spatial Design, Interactions)

> *"The best MR interface is one you forget exists — but which input modality gets us there?"

- **Three paradigms:** Gaze-and-commit (look + dwell to activate), hand tracking (natural but fatiguing), motion controllers (precise but artificial). The Microsoft curriculum explicitly teaches all three but doesn't declare a winner.
- **The perceptual question:** Gaze tracking knows where you're looking, enabling foveated rendering and attention-based UI. But does sustained gaze feel like surveillance? Do hand interactions feel more embodied, or more clumsy?
- **Key voices:** @jeromeetienne (A-Frame AR interaction models); April Speight (pedagogy of comfort in XR)

### Debate 5: WebAR's CORS & Distribution Problem
**Source:** AR.js Issues on CORS proxy requirements, npm package gaps (#7, #234)

> *"If Web AR requires a CORS proxy just to load 3D models, is it truly 'on the web'?"

- **The technical debt:** AR.js's NFT image tracking requires same-server resources or CORS proxies. The npm package still has open issues (#7 since 2020). This friction prevents массовое adoption.
- **The perceptual cost:** Every workaround (proxy, flags, server config) is a barrier between the user and the experience. perception of "the web" assumes instant access. AR on the web currently demands server architecture knowledge that the web famously abstracted away.

---

## 🎙️ Episode Plans

---

### Episode 1: "Latency and the Perceptual Threshold"

**Tagline:** *Why your brain throws up when AR lags — and what 20 milliseconds has to do with it.*

**Core Question:** How does the human perceptual system detect mismatch between motion and visual feedback, and can technology hide the gap?

**Research Topics:**
- Motion-to-photon latency budgets in VR/AR (20ms rule, 11ms for visual cortex)
- AR.js device-orientation pipeline and iOS/Safari latency regressions (Issue #302)
- Foveated rendering as a latency-masking strategy
- Predictive tracking and the vestibular-visual conflict
- WebXR's silence on latency budgets

**Debate Table:**

| Position | Argument | Proponents |
|---|---|---|
| **Foveation wins** | If the fovea (central vision) gets <10ms, peripheral lag is imperceptible | VR research labs, Meta Reality Labs |
| **Full-frame budget** | 20ms end-to-end or the brain knows — partial tricks fail in peripheral tracking | Presence researchers, UXorneys |
| **Spec-level mandate** | WebXR needs a standardized latency budget, not just a frame timing API | WebXR WG, AR.js maintainers |

**Potential Guests:**
- **Jerome Etienne** (@jeromeetienne) — How AR.js's architecture makes latency visible (and invisible)
- **Nicolò Carpignoli** (@nicolocarpignoli) — The cross-browser latency nightmare (Safari vs Chrome)
- **Nick W** (@nickw1) — iOS/Safari device-orientation reimplementation: what changed and what didn't

**Show Notes Format:** 45 min main + 20 min "Debate Table" panel segment

**GitHub Anchors:** AR.js Issues #302, #26, #288; Microsoft XR Curriculum Unit 2 (Comfort)

---

### Episode 2: "Spatial Sound and the Third Dimension"

**Tagline:** *The sense that creates presence is the one the Web forgot.*

**Core Question:** If spatial audio is the strongest cue for "I'm really here," why is it absent from the WebXR specification and mostly abandoned in open-source AR frameworks?

**Research Topics:**
- HRTF (Head-Related Transfer Function) personalization and the "one-size-fits-all" problem
- Ambisonics vs binaural rendering in real-time web applications
- Lullaby's spatial audio architecture (Google's C++ VR framework) and why it went dormant
- The Web Audio API vs WebXR spatial audio binding gap
- Neural network-based HRTF estimation (MindAR.js could bridge ML + audio)

**Debate Table:**

| Position | Argument | Proponents |
|---|---|---|
| **Spec-first** | Spatial audio needs a WebXR-native session type before implementations matter | WebXR WG critics |
| **API-first** | Web Audio API extensions (PannerNode upgrades) beat a new spec branch | Browser vendors |
| **ML bridge** | Neural HRTF estimation can skip the spec debate and ship in JavaScript today | @hiukim, ML researchers |
| **Abandonment critique** | Lullaby proved that even Google can't sustain spatial audio without a spec mandate |

**Potential Guests:**
- **Hiukim** (@hiukim) — Could TensorFlow.js models estimate personalized HRTFs in real time?
- **Kalwalt** (@kalwalt) — How would an ECS architecture for AR.js handle audio entities differently?
- **Gustavo Cordido** — How do you teach spatial audio design when the tooling doesn't exist?

**Show Notes Format:** 45 min main + 20 min "The Lullaby Case Study" deep-dive

**GitHub Anchors:** google/lullaby (spatial audio modules); AR.js Issues #58 (physics-audio interaction); WebXR spec spatial audio absence

---

### Episode 3: "Interfaces Beyond the Flat Screen"

**Tagline:** *Gaze, gesture, or controller — which input makes you forget you're wearing a headset?*

**Core Question:** Mixed reality interfaces claim to free us from the flat screen — but are we just trading a mouse for a laser pointer, or is something genuinely new emerging?

**Research Topics:**
- Gaze-and-commit model: dwell-time activation, line-of-sight UI, attention-based rendering
- Hand tracking vs motion controllers: embodied cognition vs precision tradeoffs
- The Microsoft XR Curriculum's comfort framework: why "neutral head posture" is a design constraint
- Spatial anchoring and hologram persistence: how do digital objects "live" in physical space?
- The WebXR input profile gap: no standardized hand-tracking or gaze API

**Debate Table:**

| Position | Argument | Proponents |
|---|---|---|
| **Gaze is the future** | Eye tracking enables foveated rendering + attention UI + natural selection | Presence researchers, Apple Vision Pro camp |
| **Hands are the bridge** | Hand tracking preserves corporeal awareness — you don't "point," you "reach" | Meta Quest hand-tracking advocates |
| **Controllers win now** | Precise, hierarchical, fatigue-free — the tech isn't there yet for hands-only | Enterprise MR, industrial AR |
| **All three, contextual** | The interface should adapt to the task, not the other way around | Spatial design educators |

**Potential Guests:**
- **Jerome Etienne** (@jeromeetienne) — A-Frame's interaction model: what AR.js chose and what it left out
- **Nick W** (@nickw1) — Multi-camera support (Issue #26) as the gateway to full-body MR tracking
- **April Speight** — Pedagogy of comfort: how you train people to feel at home in MR
- **Kalwalt** (@kalwalt) — AR.js-next's ECS approach: how would an entity-component system model gaze, hand, and controller as interchangeable input entities?

**Show Notes Format:** 45 min main + 20 min "Interface Futurism" speculative segment

**GitHub Anchors:** Microsoft XR Curriculum Units 3–4; AR.js Issues #26, #288, #681 (AR.js-next ECS)

---

## 🗓️ Production Timeline

| Phase | Deliverable | Target |
|---|---|---|
| **Research** | GitHub issue audit complete, guest outreach initiated | Week 1–2 |
| **Scripting** | Episode scripts with debate table segments | Week 3–4 |
| **Recording** | Primary recording sessions | Week 5–6 |
| **Post-production** | Editing, sound design, spatial audio demo clips | Week 7–8 |
| **Release** | Episodes 1–3 launch | Week 9 |

## 🤝 How to Contribute

1. **Comment on an episode issue** (`#13`, `#16`, `#21` or their sequels) with research findings, issue links, or guest suggestions
2. **Tag potential guests** in issues and track outreach status
3. **Submit a PR** with updated episode outlines, new research from GitHub issues, or debate position papers
4. **Fork the repo** and add episode drafts, show notes, or recording materials under `episodes/`

## 🔗 Key GitHub Resources

- [Immersive Web Working Group](https://www.w3.org/immersive-web/)
- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [AR.js (active org)](https://github.com/AR-js-org/AR.js)
- [AR.js Issues — iOS/Safari Latency (#302)](https://github.com/AR-js-org/AR.js/issues/302)
- [AR.js Issues — Markerless AR (#288)](https://github.com/AR-js-org/AR.js/issues/288)
- [Google Lullaby — Spatial Audio Framework](https://github.com/google/lullaby)
- [Microsoft XR Curriculum](https://github.com/microsoft/xr-development-for-beginners)

---

*Last updated: September 2026 | Research sourced from 7 active GitHub repositories, 20+ open issues, and community contributor analysis.*