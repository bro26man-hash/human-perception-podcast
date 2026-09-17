# 🎙️ The Future of Human Perception — Episode Outline

> **Canonical production document** — Updated with GitHub-sourced research from AR/MR/Spatial Computing communities

---

## Episode 1: "Latency and the Perceptual Threshold"

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **WebGPURenderer UBO performance crisis** — 50+ comments, labeled High Priority | [three.js #30560](https://github.com/mrdoob/three.js/issues/30560) | 🔴 Active crisis in render pipeline |n| **Faster PBR Material** — 24 comments, needs investigation | [three.js #21578](https://github.com/mrdoob/three.js/issues/21578) | 🟡 Rendering bottleneck |
| **WebGPU support proposal** — 103 comments, implementer wanted | [godot-proposals #6646](https://github.com/godotengine/godot-proposals/issues/6646) | 🟡 Platform gap |
| **Multisampled multiview for WebGL** — 6 comments | [KhronosGroup/WebGL #2912](https://github.com/KhronosGroup/WebGL/issues/2912) | 🟡 Rendering fidelity vs. latency tradeoff |
| **View instancing for GPU** — 24 comments | [gpuweb/gpuweb #4109](https://github.com/gpuweb/gpuweb/issues/4109) | 🟡 Multi-view rendering efficiency |

### Key Topics
1. The 20ms motion-to-photon rule — myth or engineering reality?
2. Foveated rendering as a latency mask — how does it work, and when does it break?
3. PBR rendering cost vs. perceptual comfort — where is the budget spent?
4. WebGPU as the latency killer — can it deliver sub-frame turnaround?
5. The Godot XR render pipeline — open-source alternatives to proprietary engines

### Potential Guests
- **@mrdoob** (Mr. doob) — three.js creator, deeply involved in WebGPURenderer development
- **@reduz** (Juan Linietsky) — Godot creator, XR rendering architecture
- **@donmccurdy** — A-Frame maintainer, WebXR practitioner, author of three.js addons for XR
- **@EloiStree** — Godot XR contributor, HelloGodotXR project lead

### Research Notes
- [Ref: three.js #30560 — WebGPURenderer UBO system severe performance issues](https://github.com/mrdoob/three.js/issues/30560)
- [Ref: three.js #21578 — Faster PBR Material](https://github.com/mrdoob/three.js/issues/21578)
- [Ref: godot-proposals #6646 — WebGPU support](https://github.com/godotengine/godot-proposals/issues/6646)
- [Ref: KhronosGroup/WebGL #2912 — Multisampled multiview](https://github.com/KhronosGroup/WebGL/issues/2912)
- [Ref: gpuweb/gpuweb #4109 — View instancing](https://github.com/gpuweb/gpuweb/issues/4109)

---

## Episode 2: "Spatial Sound and the Third Dimension"

### Core Question
Why is the WebXR spec still visual-only for spatial audio? What does HRTF mean for presence?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **Native GLTF specification** — cross-vendor proposal for immersive Web | [immersive-web/proposals #52](https://github.com/immersive-web/proposals/issues/52) | 🔴 Spec gap: no native audio asset format |n| **Apply DOM to Face** — WebXR DOM overlay for XR | [immersive-web/proposals #57](https://github.com/immersive-web/proposals/issues/57) | 🟡 Interaction model gap |
| **WebXR spatial audio gap** — Google Lullaby archived, no successor | [google/lullaby](https://github.com/google/lullaby) (1.2k ⭐, archived vibes) | 🔴 Abandoned reference implementation |
| **HRTF selection & personalization** — no standard API | immersive-web/webxr issues | 🔴 Spec blind spot |
| **Ambisonics decoding in browser** — no native Web Audio API support for 1st/2nd order | web-audio-api | 🟡 Format gap |

### Key Topics
1. The WebXR spec's visual bias — what's missing for non-visual perception
2. HRTF fundamentals — how head-related transfer functions create presence
3. The Lullaby case study — why Google's spatial audio framework died
4. Web Audio API + XR — the current hacky workarounds and their limits
5. Personalized HRTFs — can we calibrate spatial audio to individual anatomy?
6. The "audio presence paradox" — why bad spatial audio breaks VR faster than bad visuals

### Potential Guests
- **@donmccurdy** — A-Frame maintainer, built spatial audio components for A-Frame
- **dmarcos** (Diego Marcos) — A-Frame co-creator, worked on WebVR audio
- **@jeromeetienne** — AR.js creator, spatial interaction pioneer
- **Immersive Web WG contributors** — spec authors working on WebXR audio sub-group

### Research Notes
- [Ref: immersive-web/proposals #52 — Native GLTF](https://github.com/immersive-web/proposals/issues/52)
- [Ref: immersive-web/proposals #57 — Apply DOM to Face](https://github.com/immersive-web/proposals/issues/57)
- [Ref: google/lullaby — C++ VR/AR libraries, spatial audio support](https://github.com/google/lullaby)
- [Ref: web-audio-api — Web Audio API spec, ambisonics gap](https://github.com/web-audio-api/web-audio-api)

---

## Episode 3: "Interfaces Beyond the Flat Screen"

### Core Question
Is the WebXR spec blind to non-visual perception? What does mixed reality actually feel like?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **ARCore Device Support Requests** — 589 comments, feature request | [arcore-android-sdk #89](https://github.com/google-ar/arcore-android-sdk/issues/89) | 🔴 Massive fragmentation |
| **AR↔VR switching in Godot XR** — seamless mode transition | [HelloGodotXR #10](https://github.com/EloiStree/HelloGodotXR/issues/10) | 🟡 Interaction model gap |
| **Hand tracking fidelity in AR** — ookmarkers vs. markerless, latency | [mediapipe hand landmarker issues](https://github.com/google-ai-edge/mediapipe) | 🔴 Perceptual fidelity |
| **Registration drift in MR** — hologram stability over time | MRTK-Unity issues, openXR spec | 🟡 Comfort/sickness driver |
| **WebXR input profile gap** — no standard for hand + controller hybrid | immersive-web/webxr | 🔴 Spec limitation |

### Key Topics
1. The ARCore fragmentation problem — 589 device requests and counting
2. Markerless tracking maturity — where AR.js and Mediapipe diverge
3. Hand tracking as the primary MR interface — replacing controllers
4. Registration & drift — why holograms shake and how to fix it
5. The hybrid input problem — hands + controllers in WebXR
6. Wayfinding and spatial memory — how MR interfaces can leverage spatial cognition
7. The flat screen bias in WebXR — is the spec designed for headsets only?

### Potential Guests
- **@jeromeetienne** — AR.js creator, markerless tracking pioneer
- **@donmccurdy** — A-Frame maintainer, MR interface experiments
- **@EloiStree** — Godot XR, AR↔VR transitions
- **Mediapipe team members** — hand tracking architecture
- **Microsoft MRTK contributors** — mixed reality interaction design

### Research Notes
- [Ref: arcore-android-sdk #89 — Device Support Requests (589 comments)](https://github.com/google-ar/arcore-android-sdk/issues/89)
- [Ref: HelloGodotXR #10 — AR to VR switching](https://github.com/EloiStree/HelloGodotXR/issues/10)
- [Ref: google-ai-edge/mediapipe — Hand Landmarker, tracking issues](https://github.com/google-ai-edge/mediapipe)
- [Ref: immersive-web/webxr — Input profiles & hand tracking](https://github.com/immersive-web/webxr)
- [Ref: microsoft/MixedRealityToolkit-Unity — MRTK interaction system](https://github.com/microsoft/MixedRealityToolkit-Unity)

---

## Cross-Episode Themes

| Theme | Episodes |
|---|---|
| **WebXR spec gaps** — visual bias, no audio, no hybrid input | Eps 2, 3 |
| **Latency as a perceptual hack** — foveation, reprojection, render budget | Eps 1, 3 |
| **Open source vs. proprietary** — Godot vs. Unity vs. Unreal for XR | Eps 1, 3 |
| **The body in the loop** — hand tracking, face tracking, haptics | Eps 2, 3 |
| **Browser as XR platform** — can the web compete with native? | All |

---

## Contributor Quick Reference

| Person | GitHub | Expertise | Episode Appearances |
|---|---|---|---|
| Mr. doob | @mrdoob | three.js, WebXR, rendering | 1 |
| Juan Linietsky | @reduz | Godot, XR rendering | 1 |
| Don McCurdy | @donmccurdy | A-Frame, WebVR, spatial audio | 1, 2 |
| Jerome Etienne | @jeromeetienne | AR.js, markerless tracking, MR | 2, 3 |
| Diego Marcos | @dmarcos | A-Frame, WebVR, presence | 2 |
| Eloi Stree | @EloiStree | Godot XR, AR/VR transitions | 1, 3 |
| Mediapipe Team | google-ai-edge/mediapipe | Hand/face tracking, on-device ML | 3 |
| Immersive Web WG | immersive-web | WebXR spec, OpenXR | All |

---

*Last updated: September 2026 — GitHub issue research sourced from 12+ repositories across AR, WebXR, spatial computing, and perceptual science communities.*