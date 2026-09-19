# 🎙️ The Future of Human Perception — Episode Outline

## Series Overview

A podcast exploring the engineering and human science behind how technology reshapes perception. Each episode is grounded in live GitHub research from the most active AR/MR/Spatial Computing repositories, and each is seeded with potential guests drawn from those communities.

**Research Methodology:** Every episode's topics, debates, and guest suggestions are sourced directly from open issues, PRs, and discussions in the repositories where the perceptual computing community actually works. We follow the arguments, not the press releases.

---

## 🔬 Research Backbone — Most Active Repos Surveyed

| Repo | Stars | Focus | Key Issues Surfaced |
|---|---|---|---|
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 15.8k ⭐ | Web AR (marker, markerless, NFC) | #190 (markerless AR, 59 comments), #469 (AR.js future, 94 comments), #498 (camera feed stretch, 50 comments) |
| [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | 6.1k ⭐ | MRTK v2 — HoloLens & MR | #88 (Vision Pro support), #621 (ObjectManipulator haptics), #830 (passthrough failure) |
| [MixedRealityToolkit/MixedRealityToolkit-Unity](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity) | 550 ⭐ | MRTK v3 — Next-gen MR | #113 (Quest 3 hand tracking ray vanishes), #830 (passthrough), #621 (socket snapping) |
| [microsoft/MixedReality-WebRTC](https://github.com/microsoft/MixedReality-WebRTC) | 944 ⭐ | MR collaboration & spatial audio | #157 (AEC failure), #83 (frame projection matrix), #130 (spatial mesh streaming), #717 (audio roughness) |
| [google/lullaby](https://github.com/google/lullaby) | 1.2k ⭐ | C++ VRSDK incl. spatial audio | Closed-source audio pipeline; internal-only |
| [facebook/immersive-web-sdk](https://github.com/facebook/immersive-web-sdk) | 357 ⭐ | WebXR framework (Three.js-based) | Spatial UI, locomotion, interactions |
| [meta-quest/immersive-web-emulator](https://github.com/meta-quest/immersive-web-emulator) | 464 ⭐ | Quest WebXR dev emulator | Device emulation for spatial testing |
| [immersive-web/webxr](https://github.com/immersive-web/webxr) | 3.1k ⭐ | WebXR spec | #390 (spatial audio, 30 comments), #815 (visual-centric spec, 41 comments), #1420 (foveation) |
| [aframevr/aframe](https://github.com/aframevr/aframe) | 17k ⭐ | WebVR/AR framework | #2281 (VR UI docs incomplete, 9 yrs), #3513 (HoloLens stalled), #5305 (hand misalignment) |

---

## 🎧 Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency & the 20ms rule
**Key Debate:** Can foveation trick the brain into forgiving lag?
**Issue:** [#133](https://github.com/bro26man-hash/human-perception-podcast/issues/133)

### Topics
- Motion-to-photon (MTP) latency: what it is, how it's measured, and why 20ms is the magic number
- The neuroscience of perceptual latency: visual persistence, phi phenomenon, and the brain's prediction engine
- Foveated rendering as a latency-hiding trick — is it cheating or clever engineering?
- Rollout scan simulation in RetroArch and its implications for perceived latency
- Tetherless vs. tethered rendering pipelines and their latency profiles
- The role of predictive tracking (HMD ≠ display)
- **NEW:** Camera↔IMU clock offset — the invisible 13-35ms ([ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779), active 2026)
- **NEW:** ALVR's "missing" 30-50% latency — the number the industry doesn't report ([ALVR #334](https://github.com/polygraphene/ALVR/issues/334))
- **NEW:** Reprojection error as the last line of defense failing ([OpenVR #659](https://github.com/ValveSoftware/openvr/issues/659))
- **NEW:** Standardized latency benchmark crisis — industry can't compare ([OpenVR #249](https://github.com/ValveSoftware/openvr/issues/249))

### GitHub Hot Debates

| Debate | Source | Comments | Core Tension |
|---|---|---|---|
| 20ms rule — physics or culture? | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) | 40 | Brain detects temporal irregularity, not average depth |
| Per-client frame stalls | [WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) | 15+ | `xrEndFrame` stalls cause 47-min freeze; vestibular system notices |
| Missing 30-50% latency | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) | Active | Streaming architectures can't reach the 20ms budget |
| Reprojection timewarp error | [OpenVR #659](https://github.com/ValveSoftware/openvr/issues/659) | Active | Wrong predicted pose → visceral discomfort |
| No standardized benchmark | [OpenVR #249](https://github.com/ValveSoftware/openvr/issues/249) | Active | Industry uses different methodologies; comparisons meaningless |
| Camera↔IMU clock drift | [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | Active (2026) | 13-35ms offset → phantom 100m positional drift |
| Markerless AR tracking pipeline | [AR.js #190](https://github.com/AR-js-org/AR.js/issues/190) | 59 | When tracking fails, presence collapses instantly |
| WebXR on Chrome failure | [A-Frame #4709](https://github.com/aframevr/aframe/issues/4709) | **106** | Most-commented A-Frame issue ever |

### 🎤 Potential Guests

| Name | GitHub Handle | What They Bring | Key Issue |
|---|---|---|---|
| **Jerome Etienne** | @jeromeetienne | Creator of AR.js (15.8k ⭐); founding vision of Web AR at 60fps | [AR.js #190](https://github.com/AR-js-org/AR.js/issues/190), [AR.js #498](https://github.com/AR-js-org/AR.js/issues/498) |
| **Nicolò Carpignoli** | @nicolocarpignoli | AR.js maintainer; kept project alive through org transition | [AR.js #469](https://github.com/AR-js-org/AR.js/issues/469) (94 comments) |
| **Diego Marcos** | @dmarcos | A-Frame co-maintainer; filed the critical 106-comment WebXR-on-Chrome issue | [A-Frame #4709](https://github.com/aframevr/aframe/issues/4709) |
| **Don McCurdy** | @donrmccurdy | A-Frame co-maintainer; built hand-tracking & controller systems | [A-Frame #5305](https://github.com/aframevr/aframe/issues/5305) |
| **WiVRn maintainer** | xytovl | OpenXR streaming; per-client scheduled frame stalls; temporal irregularity forensics | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) |
| **ALVR developer** | jd-3d | VR streaming; the missing 30-50% latency from the encoding side | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) |

### 📋 Episode Segments

1. **The 20ms Myth** — Where did the number come from? Physics or culture?
2. **Motion-to-Photon Pipeline** — From head movement to photon emission, where does time hide?
3. **Foveated Rendering** — Can reducing peripheral resolution cheat the brain?
4. **The Web AR Bottleneck** — Why is the first perceptual failure on a phone, not a headset?
5. **Reprojection Ethics** — Should developers disclose when they're "hiding" latency?
6. **IMU↔Camera Clock Drift** — The invisible latency nobody's measuring

---

## 🔊 Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics & the audio presence paradox
**Key Debate:** Why is the WebXR spec still visual-only for spatial audio?
**Issue:** [#134](https://github.com/bro26man-hash/human-perception-podcast/issues/134)

### Topics
- Head-Related Transfer Functions (HRTFs): how your ears shape what you hear
- Ambisonics vs. binaural: which paradigm wins for presence?
- **The audio presence paradox:** perfect spatial audio can feel *less* real because the brain detects the artifact
- WebXR's systemic neglect of spatial audio — Issue #390 (30 comments, open since 2018)
- Audio-only devices and accessibility — Issue #815 (41 comments, spec editor assigned)
- University of Utah's Audio Mentoring Project and open HRTF datasets
- Dynamic HRTF personalization vs. generic kernels
- **NEW:** Google Lullaby's closed-source spatial audio — what the web can't access
- **NEW:** Bluetooth audio delay per-user manual slider — no automatic calibration ([wolvic #1180](https://github.com/Igalia/wolvic/issues/1180))
- **NEW:** MRTK3 spatial audio system planning — PR #2775 (audio influencers and effects), Issue #2592 (Spatial Audio System vNext)
- **NEW:** MixedReality-WebRTC audio roughness — remote audio not smooth, double audio sources ([#717](https://github.com/microsoft/MixedReality-WebRTC/issues/717))
- **NEW:** WebRTC spatial mesh streaming — open data channel throughput for spatial audio rendering ([#130](https://github.com/microsoft/MixedReality-WebRTC/issues/130))

### GitHub Hot Debates

| Debate | Source | Comments | Core Tension |
|---|---|---|---|
| Spec has no spatial audio channel | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) | **30** | PannerNode head-pose update rate too low; no direct head-pose access |
| Spec literally excludes non-visual XR | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | **41** | "Imagery" definition; assigned to @toji, spec editor — unresolved |
| Google has spatial audio; web doesn't | [google/lullaby](https://github.com/google/lullaby) | — | Internal-only; web can't even **specify** spatial audio |
| Bluetooth delay = per-user slider | [wolvic #1180](https://github.com/Igalia/wolvic/issues/1180) | — | Every user calibrates their own experience |
| AEC failure = spatial collapse | [MR-WebRTC #157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | 17 | Echo cancellation failure destroys spatial model |
| Spatial mesh streaming | [MR-WebRTC #130](https://github.com/microsoft/MixedReality-WebRTC/issues/130) | 7 | Open mesh data channel throughput for spatial audio rendering |
| MRTK audio system planning | [MRTK #2592](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/2592) | 5 | vNext Spatial Audio System — filed 2018, still in planning |

### 🎤 Potential Guests

| Name | GitHub Handle | What They Bring | Key Issue |
|---|---|---|---|
| **cwilso** | @cwilso | W3C Immersive Web member; filed #390 in 2018; knows why spatial audio keeps getting deferred | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) |
| **ddorwin** | @ddorwin | Accessibility advocate; filed #815 exposing visual-centric spec | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) |
| **toji** | @toji | WebXR spec editor; assigned #815; can speak to resolution timeline | WebXR spec |
| **klausw** | — | WebXR contributor; filed #1210 (focus control) and #779 (user activation) | [WebXR #1210](https://github.com/immersive-web/webxr/issues/1210) |
| **Google Lullaby team** | @google | Internal spatial audio engineers; what the web is missing | [google/lullaby](https://github.com/google/lullaby) |
| **HRTF researcher** | 🔍 TBD | Academic spatial audio perception; HRTF personalization | Episode 2 |
| **Web Audio API contributor** | 🔍 TBD | Browser audio spec; PannerNode limitations | Episode 2 |
| **David Kline** | @david-c-kline | MRTK audio lead; ported HTK audio effects; spatial audio system planner | [MRTK PR #2775](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/2775) |

### 📋 Episode Segments

1. **The Spec's Blind Spot** — Why WebXR has no spatial audio channel
2. **HRTFs & Presence** — How head-related transfer functions create the illusion of space
3. **"Imagery" Language** — How a single word excludes audio AR and non-visual devices
4. **The Lullaby Gap** — What Google builds internally vs. what the web can access
5. **Bluetooth Latency** — Why your VR headset's audio is delayed per-user
6. **Ambisonics on the Web** — Can the Web Audio API carry the spatial audio torch?
7. **AEC & Spatial Collapse** — When echo cancellation breaks, the entire spatial model falls

---

## 🕶️ Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift & the WebXR blind spot
**Key Debate:** Is the WebXR specification structurally biased toward visual interfaces?
**Issue:** [#135](https://github.com/bro26man-hash/human-perception-podcast/issues/135)

### Topics
- Is the WebXR spec structurally biased toward visual interfaces?
- Gaze, gesture, voice, and proprioception — what's missing from the spec?
- MRTK3's Vision Pro crisis — is the interface paradigm shifting from hands to gaze+pinch?
- ObjectManipulator socket snapping — when does a virtual object feel "real"?
- Quest 3 hand tracking ray vanishes — tracking dropout as perceptual discontinuity
- Quest 3 passthrough broken — the MR perception pipeline failure
- Markerless AR — the 59-comment unresolved debate about registration fidelity
- Hand-controls misalignment — when your virtual hand doesn't match
- 9 years of incomplete VR UI docs — nobody knows how to design for volumetric space
- HoloLens support stalled — the most important MR device has no web path
- **NEW:** MRTK3 trigger sensitivity as perceptual calibration issue ([MRTK #82](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/82))
- **NEW:** Spatial anchor scale overruled — world-locked content instability ([A-Frame #5630](https://github.com/aframevr/aframe/issues/5630))
- **NEW:** DOM Overlays spec as potential interface solution for HTML-in-canvas
- **NEW:** WebRTC locatable camera projection matrix — the transform passthrough gap ([MR-WebRTC #83](https://github.com/microsoft/MixedReality-WebRTC/issues/83))

### GitHub Hot Debates

| Debate | Source | Comments | Core Tension |
|---|---|---|---|
| Vision Pro interface paradigm shift | [MRTK3 #88](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88) | 28 | Gaze+pinch vs. hands — MRTK building blocks are hand-centric |
| Haptic feedback in socket snapping | [MRTK3 #621](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/621) | 19 | Late haptic feedback breaks contact illusion; assigned to @whebertML |
| Quest 3 hand tracking ray vanishes | [MRTK3 #113](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/113) | 14 | Virtual hand disappears → presence collapses |
| Quest 3 passthrough not working | [MRTK3 #830](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/830) | 7 | Pass-through failure = MR perception pipeline collapse |
| Spec's visual bias | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | **41** | "Imagery" definition excludes audio AR, haptic-only, neuro-stimulation |
| Markerless AR — 59 comments | [AR.js #190](https://github.com/AR-js-org/AR.js/issues/190) | **59** | Is true markerless AR possible or always a compromise? |
| Hand-controls misalignment | [A-Frame #5305](https://github.com/aframevr/aframe/issues/5305) | 20 | Proprioceptive mismatch — strongest presence-breaker |
| 9 years of incomplete VR UI docs | [A-Frame #2281](https://github.com/aframevr/aframe/issues/2281) | 23 | Volumetric interface design — still unsolved after 9 years |
| HoloLens support stalled | [A-Frame #3513](https://github.com/aframevr/aframe/issues/3513) | Stalled | Enterprise MR needs the web; web doesn't support HoloLens |
| WebRTC frame projection | [MR-WebRTC #83](https://github.com/microsoft/MixedReality-WebRTC/issues/83) | **37** | Transform/projection matrix of locatable camera; open since 2019 |

### 🎤 Potential Guests

| Name | GitHub Handle | What They Bring | Key Issue |
|---|---|---|---|
| **Don McCurdy** | @donrmccurdy | A-Frame co-maintainer; built hand-tracking; tracking-misalignment stories | [A-Frame #5305](https://github.com/aframevr/aframe/issues/5305) |
| **Kevin Ngo** | @andgokevin | A-Frame co-maintainer; authored "Building UIs in VR" — incomplete after 9 years | [A-Frame #2281](https://github.com/aframevr/aframe/issues/2281) |
| **MRTK3 team** | @whebertML, @keveleigh, @david-c-kline | ObjectManipulator design; Vision Pro bridging; passthrough perceptual issues | [MRTK3 #88](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88), [#621](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/621) |
| **Jerome Etienne** | @jeromeetienne | AR.js creator; markerless AR 59-comment debate; registration fidelity | [AR.js #190](https://github.com/AR-js-org/AR.js/issues/190) |
| **HoloLens/MR practitioner** | 🔍 TBD | Enterprise MR; WebXR→HoloLens bridge gap; #3513 stagnation | [A-Frame #3513](https://github.com/aframevr/aframe/issues/3513) |

### 📋 Episode Segments

1. **The Spec's Visual Bias** — How "imagery" in the WebXR spec excludes everything but vision
2. **Hand Tracking as Perceptual Interface** — When the virtual hand doesn't match, the brain rejects it
3. **Hologram Drift** — Registration errors that destroy presence one degree at a time
4. **Pass-Through as Perception Pipeline** — Quest 3 passthrough failures and MR perception collapse
5. **The Vision Pro Question** — Are gaze+pinch replacing hands?
6. **9 Years of Incomplete UI Docs** — Why we still don't know how to design for volumetric space
7. **Markerless AR — Compromise or Breakthrough?** — The 59-comment debate
8. **The HoloLens Gap** — Why the most important MR device has no web path

---

## 🗺️ Cross-Episode Threads

These themes weave through all three episodes and should be referenced for continuity:

| Theme | Ep 1 | Ep 2 | Ep 3 |
|---|---|---|---|
| **The 20ms rule vs. temporal irregularity** | ✅ Core | — | ✅ (tracking dropout = temporal discontinuity) |
| **WebXR's "imagery" definition** | — | ✅ Core | ✅ Core |
| **Markerless AR & tracking fidelity** | ✅ | — | ✅ |
| **Perceptual presence collapse** | ✅ (latency) | ✅ (audio) | ✅ (interface) |
| **Closed vs. open spatial computing** | ✅ (AR.js open) | ✅ (Lullaby closed) | ✅ (MRTK/Vision Pro) |
| **Accessibility & non-visual XR** | — | ✅ | ✅ |

---

## 📅 Production Timeline

| Milestone | Target | Notes |
|---|---|---|
| Research audit complete | ✅ Sept 2026 | GitHub issues sourced for all 3 episodes |
| Guest outreach | TBD | Prioritize: jeromeetienne, cwilso, donrmccurdy, whebertML |
| Episode 1 script draft | TBD | Segment: "The 20ms Myth" first |
| Episode 2 script draft | TBD | Segment: "The Spec's Blind Spot" first |
| Episode 3 script draft | TBD | Segment: "The Word That Excluded Your Ears" first |
| Record Ep 1 | TBD | After script approval |
| Record Ep 2 | TBD | After script approval |
| Record Ep 3 | TBD | After script approval |
| Publish | TBD | — |

---

## ✅ Overall Action Items

- [ ] Confirm guest outreach: jeromeetienne, cwilso, donrmccurdy, andgokevin, whebertML, david-c-kline
- [ ] Read full threads: WiVRn #282, #1099; WebXR #390, #815; AR.js #190, #469
- [ ] Interview ALVR developer about missing 30-50% latency
- [ ] Research foveated rendering implementations (Quest Pro, PSVR2, WebXR #1420)
- [ ] Request comment from @toji (WebXR spec editor) on #815 resolution
- [ ] Investigate Lullaby spatial audio architecture via Google's published papers
- [ ] Find academic HRTF researcher for Episode 2
- [ ] Interview MRTK3 team about Vision Pro support and passthrough
- [ ] Investigate HoloLens/MR practitioner for #3513 stagnation story
- [ ] Coordinate episode scripts for cross-thread continuity

---

*This outline is a living document. Contribute findings via GitHub issues or submit a PR with updated research.*
