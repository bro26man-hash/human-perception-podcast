# 🎙️ The Future of Human Perception — Initial Episode Outline

> **Research sync: September 2026** — Consolidated from live GitHub issue audits across AR.js, MRTK, WebXR Spec, Lullaby, MindAR, WiVRn, ALVR, and Spatial_Audio_Framework repositories.

---

## Series Vision

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast tracks the fiercest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Key Repos | Stars |
|---|---|---|
| Web AR | `AR-js-org/AR.js`, `hiukim/mind-ar-js`, `jeeliz/jeelizFaceFilter` | 6.0k / 2.7k / 2.9k |
| WebXR & 3D | `mrdoob/three.js`, `playcanvas/engine`, `immersive-web/webxr` | 115k / 16.7k / 3.1k |
| Mixed Reality | `MixedRealityToolkit/MixedRealityToolkit-Unity` (MRTK3), `microsoft/MixedReality-WebRTC` | 550 / 944 |
| Open-source VR | `WiVRn/WiVRn`, `polygraphene/ALVR`, `ValveSoftware/openvr` | Active |
| AR SDKs | `google-ar/arcore-android-sdk`, `google-ar/arcore-unity-sdk`, `Unity-Technologies/arfoundation-samples` | 5.2k / 1.4k / 3.4k |
| Spatial Audio | `leomccormack/Spatial_Audio_Framework`, `GoogleChrome/omnitone`, `google/spatial-media` | 748 / 911 / 2.1k |
| Standards | `KhronosGroup/glTF`, `KhronosGroup/OpenXR-SDK`, `StereoKit/StereoKit` | 10k+ / 1.1k / 1.1k |
| Internal/Closed | `google/lullaby` (VR/AR C++ engine) | 1.2k |

---

## 🔥 Top Repos & What They Reveal

### 1. AR-js-org/AR.js (6.0k ⭐) — The Living Web AR Library
- **Maintained** by Nicolò Carpignoli after migration from jeromeetienne
- Active issues: ImageTracking demo broken (#826), location-based examples failing (#825), THREE.mathUtils renameBreaking changes (#822)
- **Podcast story:** The tension between rapid web standards evolution (Three.js breaking API) and the need for stable AR tracking pipelines. Jerome Etienne can speak to the founding vision; Nicolò can speak to the community maintenance reality.

### 2. MixedRealityToolkit/MixedRealityToolkit-Unity (MRTK3 — 550 ⭐) — The MR Standard
- Built on Unity XR Interaction Toolkit + OpenXR
- **Key open issues:**
  - [#88](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88) — Apple Vision Pro support (28 comments) — *Is the MR interface paradigm shifting from hands to gaze?*
  - [#621](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/621) — ObjectManipulator socket snapping (19 comments) — *Haptic feedback registration latency*
  - [#113](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/113) — Quest 3 hand tracking ray vanishes when MetaXR enabled (14 comments) — *Tracking dropout = perceptual discontinuity*
  - [#830](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/830) — Quest 3 passthrough not working (7 comments) — *Pass-through is the MR PERCEPTION pipeline; when it breaks, the world collapses*
- **Podcast angle:** MRTK3 is the bridge between OpenXR spec and real devices. Every bug is a perceptual failure.

### 3. immersive-web/webxr (3.1k ⭐) — The Spec Itself
- **The three hottest open issues:**
  - [#390](https://github.com/immersive-web/webxr/issues/390) — **Sound source nodes in WebXR** (30 comments, filed by W3C member @cwilso) — *Should WebXR provide HRTF-based spatial audio? The spec is visual-only.*
  - [#815](https://github.com/immersive-web/webxr/issues/815) — **Spec language precludes non-visual uses** (41 comments, @ddorwin, a11y-tracker) — *"An XR device is a physical unit of hardware that can present imagery to the user" — what about audio AR?*
  - [#1396](https://github.com/immersive-web/webxr/issues/1396) — **Actual vs. internal visibility** — *Fundamental MR rendering question: what's real?*
  - [#1420](https://github.com/immersive-web/webxr/issues/1420) — **Dynamic foveation** (proposed by @AdaRoseCannon) — *Can the renderer reduce peripheral resolution to cheat the brain?*
- **Podcast angle:** The spec is the ground zero for all perception debates. What gets specified gets built. What doesn't gets forgotten.

### 4. google/lullaby (1.2k ⭐) — The Closed Door
- Google's internal VR/AR C++ engine with **full spatial audio support**
- Used by: VR Home, Play Store, YouTube, Play Movies, Earth
- **"We are unable to take your pull requests at this time"** — no external contributions
- **Podcast story:** Google can build spatial audio into every app internally. The web can't even specify it. That gap is a whole episode.

### 5. WiVRn & ALVR — The Streaming Forensics
- **WiVRn #1099** — Per-client scheduled frames stall xrEndFrame (15+ comments, 2026) — *47-minute freeze after Quest 3 refocus; brain's vestibular system notices*
- **WiVRn #282** — Temporal irregularity vs. average latency (40 comments) — *Stutter = irregularity, not depth; brain detects pacing, not absolute ms*
- **ALVR #334** — "Missing" 30-50% latency in VR streaming — *Optimizing against the wrong number; the 20ms rule may be unreachable*
- **OpenVR #659** — Reprojection error in timewarp — *Wrong predicted pose → visceral discomfort; last line of defense failing*
- **OpenVR #249** — No standardized latency benchmark — *Metrology crisis; industry uses different methodologies*

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20ms motion-to-photon latency remains so hard to deliver.

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### 🔥 GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Perception Impact |
|---|---|---|---|---|
| 1 | Per-client scheduled frames stall xrEndFrame | WiVRn #1099 | 🔴 15+ comments, 2026 | 47-min freeze after Quest 3 refocus; vestibular disconnect |
| 2 | Temporal irregularity vs. average latency | WiVRn #282 | 🔴 40 comments | Brain detects pacing, not absolute ms — stutter is the enemy |
| 3 | "Missing" 30-50% latency in VR streaming | ALVR #334 | 🔴 Active | Optimizing against wrong number; 20ms rule may be unreachable |
| 4 | Camera↔IMU clock offset 13-35ms | ARCore #1779 | 🔴 Active, 2026 | Invisible to devs; phantom 100m path from in-place rotation |
| 5 | Acoustic echo cancellation broken in MR | MixedReality-WebRTC #157 | 🔴 17 comments | AEC failure = spatial audio collapse; perceptual calibration failure |
| 6 | No standardized latency benchmark | OpenVR #249 | 🔴 Metrology crisis | Comparisons meaningless; industry uses different methodologies |
| 7 | Reprojection error in timewarp | OpenVR #659 | 🔴 Active | Wrong predicted pose → visceral discomfort; last line failing |
| 8 | Web AR tracking failure | AR.js #826, #825 | 🟡 First bottleneck | Real-time tracking as first perceptual bottleneck on web |

### 🎤 Potential Guests

| Name | Role | GitHub | What They Bring |
|---|---|---|---|
| **Jerome Etienne** | Creator of AR.js | @jeromeetienne | Founding vision of Web AR; markerless vs. marker debate (#190, 59 comments); pipeline latency stories from AR.js #498 (50 comments) |
| **Nicolò Carpignoli** | AR.js maintainer | @nicolocarpignoli | Kept AR.js alive through org transition; knows Web AR's pain points from #469 (94 comments) and #544 (NFT tracking) |
| **Diego Marcos** | A-Frame co-maintainer | @dmarcos | Filed the critical WebXR-on-Chrome issue (#4709, **106 comments** — most-commented A-Frame issue); WebXR runtime performance gap |
| **Don McCurdy** | A-Frame co-maintainer | @donrmccurdy | Built hand-tracking & controller systems; tracking-misalignment bugs (#5305, 20 comments); MR registration failures (#5630) |
| **WiVRn maintainer** (xytovl) | OpenXR streaming | — | Scheduled frame stalls, temporal irregularity forensics, the 20ms rule from the inside |
| **ALVR developer** (jd-3d) | VR streaming latency | — | Missing 30-50% latency mystery; reprojection error analysis |

### Key Segments
1. **The 20ms Myth** — Where did the number come from? Is it physics or culture?
2. **Motion-to-Photon Pipeline** — From head movement to光子发射, where does time hide?
3. **Foveated Rendering** — Can reducing peripheral resolution cheat the brain?
4. **The Web AR Bottleneck** — Why is the first perceptual failure on a phone, not a headset?
5. **Reprojection Ethics** — Should developers disclose when they're "hiding" latency?

### Sources & Issues
- [WiVRn #1099 — Per-client scheduled frames](https://github.com/WiVRn/WiVRn/issues/1099)
- [WiVRn #282 — Temporal irregularity](https://github.com/WiVRn/WiVRn/issues/282)
- [ALVR #334 — Missing latency](https://github.com/polygraphene/ALVR/issues/334)
- [OpenVR #659 — Reprojection error](https://github.com/ValveSoftware/openvr/issues/659)
- [OpenVR #249 — No standardized benchmark](https://github.com/ValveSoftware/openvr/issues/249)
- [ARCore #1779 — Camera/IMU offset](https://github.com/google-ar/arcore-android-sdk/issues/1779)
- [AR.js #190 — Is Markerless AR possible?](https://github.com/AR-js-org/AR.js/issues/190)
- [A-Frame #4709 — WebXR on Chrome](https://github.com/aframevr/aframe/issues/4709)
- [MixedReality-WebRTC #157 — AEC failure](https://github.com/microsoft/MixedReality-WebRTC/issues/157)

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How do HRTFs, ambisonics, and room modeling create the illusion of space from two speakers — and why is the WebXR spec still visual-only?

### Core Question
Is spatial audio a "nice to have" or a "must have" for presence? What happens when the spec ignores your ears?

### 🔥 GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Perception Impact |
|---|---|---|---|---|
| 1 | Sound source nodes absent from WebXR | WebXR #390 | 🔴 30 comments, 7+ years open | W3C member @cwilso proposed HRTF integration in 2018 — still deferred |
| 2 | Spec language precludes non-visual uses | WebXR #815 | 🔴 41 comments, a11y-tracker | "Imagery" requirement makes audio AR technically out of scope |
| 3 | Bluetooth audio delay = per-user manual slider | Igalia/wolvic #1180 | 🔴 Active | No automatic calibration, no HRTF adaptation, no room modeling |
| 4 | Google Lullaby has spatial audio — web doesn't | google/lullaby | 🔴 Closed source | The gap between internal capability and web accessibility is the story |
| 5 | AEC failure destroys spatial audio | MixedReality-WebRTC #157 | 🔴 17 comments | Echo cancellation breakage = spatial model collapse |

### 🎤 Potential Guests

| Name | Role | GitHub | What They Bring |
|---|---|---|---|
| **cwilso** | W3C Immersive Web member | @cwilso | Filed the sound source nodes issue (#390); knows exactly why spatial audio is deferred |
| **ddorwin** | Accessibility advocate | @ddorwin | Filed #815 — spectral language excluding non-visual XR; the intersection of a11y and spatial audio |
| **toji** | WebXR spec editor | @toji | Assigned #815; can speak to why the spec has remained visual-centric |
| **klausw** | WebXR focus control | — | Filed #1210 (focus control for handheld AR); the interaction model gap |
| **Google Lullaby team** | Spatial audio engineers | @google | Internal spatial audio pipeline; why it can't be open-sourced; what the web is missing |
| **HRTF researcher** (TBD) | Spatial audio perception | — | Personalization of HRTFs; the "one-size-fits-all" problem; biometric audio |
| **Web Audio API contributor** (TBD) | Browser audio spec | — | PannerNode limitations; ambisonics in the browser; the Web Audio ↔ WebXR integration gap |

### Key Segments
1. **The Spec's Blind Spot** — Why WebXR has no spatial audio channel and what that means for developers
2. **HRTFs & Presence** — How head-related transfer functions create the illusion of space
3. **The Lullaby Gap** — What Google builds internally vs. what the web can access
4. **Bluetooth Latency** — Why your VR headset's audio is delayed per-user, not per-system
5. **AEC & Spatial Collapse** — When echo cancellation breaks, the entire spatial model falls
6. **Ambisonics on the Web** — Can the Web Audio API carry the spatial audio torch?

### Sources & Issues
- [WebXR #390 — Sound source nodes](https://github.com/immersive-web/webxr/issues/390)
- [WebXR #815 — Spec precludes non-visual](https://github.com/immersive-web/webxr/issues/815)
- [WebXR #1396 — Actual vs. internal visibility](https://github.com/immersive-web/webxr/issues/1396)
- [WebXR #1420 — Dynamic foveation](https://github.com/immersive-web/webxr/issues/1420)
- [Igalia/wolvic #1180 — Bluetooth audio delay](https://github.com/Igalia/wolvic/issues/1180)
- [MixedReality-WebRTC #157 — AEC failure](https://github.com/microsoft/MixedReality-WebRTC/issues/157)
- [google/lullaby — Spatial audio (closed)](https://github.com/google/lullaby)

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift, hand tracking, and the question: is the WebXR spec blind to non-visual perception?

### Core Question
Is the WebXR specification structurally biased toward visual interfaces? What about gaze, gesture, voice, and proprioception?

### 🔥 GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Perception Impact |
|---|---|---|---|---|
| 1 | Vision Pro support request | MRTK3 #88 | 🔴 28 comments | *Is the MR interface paradigm shifting from hands to gaze+pinch?* |
| 2 | ObjectManipulator socket snapping | MRTK3 #621 | 🔴 19 comments | *Haptic feedback registration latency; when does the virtual object feel "real"?* |
| 3 | Quest 3 hand tracking ray vanishes | MRTK3 #113 | 🔴 14 comments | *Tracking dropout = perceptual discontinuity; the hand disappears and so does your presence* |
| 4 | Quest 3 passthrough broken | MRTK3 #830 | 🔴 7 comments | *Pass-through is the MR perception pipeline; when it fails, the world collapses* |
| 5 | Spec precludes non-visual uses | WebXR #815 | 🔴 41 comments | *The word "imagery" in the spec technically excludes audio AR and other non-visual modalities* |
| 6 | Markerless AR impossibility debate | AR.js #190 | 🔴 59 comments | *Is markerless tracking a perceptual compromise? What's the registration fidelity cost?* |
| 7 | Hand-controls misalignment | A-Frame #5305 | 🔴 20 comments | *When your virtual hand doesn't match your real hand, the brain rejects the illusion* |
| 8 | HoloLens support stalled | A-Frame #3513 | 🔴 Stalled | *The WebXR → HoloLens bridge is broken; MR practitioners have no web path* |
| 9 | UI in VR docs incomplete | A-Frame #2281 | 🔴 23 comments, 9 years | *We still don't know how to design interfaces for volumetric space* |

### 🎤 Potential Guests

| Name | Role | GitHub | What They Bring |
|---|---|---|---|
| **Don McCurdy** | A-Frame co-maintainer | @donrmccurdy | Built hand-tracking & controller systems; tracking-misalignment stories (#5305); MR registration failures (#5630) |
| **Kevin Ngo** | A-Frame co-maintainer | @andgokevin | Authored "Building UIs in VR" guide (#2281, incomplete after 9 years); the interface design gap |
| **MRTK3 team** (whebertML, keveleigh) | Microsoft MR developers | @whebertML, @keveleigh | ObjectManipulator design; spatial manipulation; the gap between spec statements and device reality |
| **HoloLens/MR practitioner** (TBD) | Enterprise MR | — | WebXR → HoloLens bridge gap; #3513 stagnation; why enterprise MR needs the web |
| **Jerome Etienne** | AR.js creator | @jeromeetienne | Markerless AR debates; registration fidelity; the perceptual cost of tracking compromises |

### Key Segments
1. **The Spec's Visual Bias** — How "imagery" language in WebXR excluding audio AR and non-visual devices
2. **Hand Tracking as Perceptual Interface** — When the virtual hand doesn't match, the brain rejects it
3. **Hologram Drift** — Registration errors that destroy presence one degree at a time
4. **Pass-Through as Perception Pipeline** — Quest 3 passthrough failures and the MR perception collapse
5. **The Vision Pro Question** — Are gaze+pinch replacing hands? What does that mean for interface design?
6. **9 Years of Incomplete UI Docs** — Why we still don't know how to design for volumetric space
7. **Markerless AR — Compromise or Breakthrough?** — The 59-comment debate that never resolved

### Sources & Issues
- [WebXR #815 — Spec precludes non-visual](https://github.com/immersive-web/webxr/issues/815)
- [WebXR #390 — Sound source nodes](https://github.com/immersive-web/webxr/issues/390)
- [MRTK3 #88 — Vision Pro support](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88)
- [MRTK3 #621 — ObjectManipulator sockets](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/621)
- [MRTK3 #113 — Quest hand tracking ray](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/113)
- [MRTK3 #830 — Quest 3 passthrough](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/830)
- [AR.js #190 — Is Markerless AR possible?](https://github.com/AR-js-org/AR.js/issues/190)
- [A-Frame #5305 — Hand-controls misaligned](https://github.com/aframevr/aframe/issues/5305)
- [A-Frame #3513 — HoloLens support](https://github.com/aframevr/aframe/issues/3513)
- [A-Frame #2281 — UI in VR docs](https://github.com/aframevr/aframe/issues/2281)

---

## 🗺️ Series Roadmap

| Episode | Title | Core Debate | Primary Repo Sources | Key Guests |
|---|---|---|---|---|
| **1** | Latency and the Perceptual Threshold | Can foveation trick the brain? | WiVRn, ALVR, OpenVR, ARCore, AR.js | Jerome Etienne, Diego Marcos, WiVRn/ALVR devs |
| **2** | Spatial Sound and the Third Dimension | Is WebXR blind to ears? | WebXR #390, #815, Lullaby, Wolvic | @cwilso, @ddorwin, Google Lullaby team, HRTF researcher |
| **3** | Interfaces Beyond the Flat Screen | Is the spec visually biased? | MRTK3, WebXR #815, AR.js, A-Frame | Don McCurdy, Kevin Ngo, MRTK3 team, MR practitioner |
| **4** | *(Planned)* | *TBD from GitHub watchlist* | *To be determined from live audit* | *TBD*

---

## How to Contribute

1. **Pick an episode issue** — There are individual issues for each episode with specific research tasks
2. **Add issue links** — Found a hot debate in an AR/MR repo? Comment with the link
3. **Suggest guests** — Know someone working on these issues? Tag them in an issue
4. **Submit a PR** — Update episode outlines, add research notes, or fix the research database
5. **Join the Gitter** — [AR.js Gitter](https://gitter.im/AR-js/Lobby) for Web AR community discussion

---

## Quick Reference: Key GitHub Issues for Episode Teams

| Issue | Repo | Topic | Episode | Comments |
|---|---|---|---|---|
| [#390](https://github.com/immersive-web/webxr/issues/390) | webxr | Sound source nodes / HRTF | Ep 2 | 30 |
| [#815](https://github.com/immersive-web/webxr/issues/815) | webxr | Spec precludes non-visual | Ep 2, 3 | 41 |
| [#1099](https://github.com/WiVRn/WiVRn/issues/1099) | WiVRn | Scheduled frame stalls | Ep 1 | 15+ |
| [#282](https://github.com/WiVRn/WiVRn/issues/282) | WiVRn | Temporal irregularity | Ep 1 | 40 |
| [#334](https://github.com/polygraphene/ALVR/issues/334) | ALVR | Missing 30-50% latency | Ep 1 | Active |
| [#659](https://github.com/ValveSoftware/openvr/issues/659) | openvr | Reprojection error | Ep 1 | Active |
| [#249](https://github.com/ValveSoftware/openvr/issues/249) | openvr | No standardized benchmark | Ep 1 | Active |
| [#1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | ARCore | Camera/IMU clock offset | Ep 1 | Active |
| [#190](https://github.com/AR-js-org/AR.js/issues/190) | AR.js | Markerless AR possible? | Ep 1, 3 | 59 |
| [#498](https://github.com/AR-js-org/AR.js/issues/498) | AR.js | Stretched camera feed | Ep 1 | 50 |
| [#4709](https://github.com/aframevr/aframe/issues/4709) | A-Frame | WebXR on Chrome | Ep 1 | 106 |
| [#5305](https://github.com/aframevr/aframe/issues/5305) | A-Frame | Hand-controls misaligned | Ep 3 | 20 |
| [#88](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88) | MRTK3 | Vision Pro support | Ep 3 | 28 |
| [#157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | MixedReality-WebRTC | AEC failure | Ep 1, 2 | 17 |

---

*Last updated: September 2026 | Research sourced from 10+ GitHub repositories and 50+ open issues*
