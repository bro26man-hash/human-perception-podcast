# 🔬 Research Summary — Sept 16, 2026

> Live audit of GitHub issues, contributors, and hot debates across the most active AR/MR/Spatial Computing repositories.

## Repositories Surveyed

| Repository | Stars | Language | Focus |
|---|---|---|---|
| `mrdoob/three.js` | 115,575 | JavaScript | 3D library, foundational for AR/VR web apps |
| `AR-js-org/AR.js` | 15,789 | HTML | Web AR — marker-based & location-based |
| `playcanvas/engine` | 16,703 | JavaScript | Web graphics runtime (WebGL/WebGPU/WebXR) |
| `hiukim/mind-ar-js` | 2,725 | JavaScript | Web AR with TensorFlow.js image/face tracking |
| `jeeliz/jeelizFaceFilter` | 2,938 | JavaScript | Real-time multi-face AR filters on the web |
| `microsoft/MixedRealityToolkit-Unity` | 6,076 | C# | MRTK for HoloLens & immersive headsets (legacy v2) |
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | 550 | C# | MRTK v3 (the future of MR tooling) |
| `microsoft/MixedReality-WebRTC` | 944 | C# | MR audio/video real-time communication |
| `microsoft/MixedRealityCompanionKit` | 594 | C# | MR calibration, hologram registration, SpectatorView |
| `immersive-web/webxr` | 3,150 | Bikeshed | WebXR Device API specification |
| `Hubs-Foundation/hubs` | 2,215 | JavaScript | Multi-user virtual spaces (A-Frame based) |
| `WiVRn/WiVRn` | 1,639 | C++ | Linux OpenXR streaming to standalone headsets |
| `tentone/nunuStudio` | 2,230 | JavaScript | WebXR game engine |
| `StereoKit/StereoKit` | 1,078 | C# | XR engine with OpenXR + WebXR backends |
| `google/lullaby` | 1,197 | C++ | VR/AR C++ libraries |
| `KhronosGroup/OpenXR-SDK` | 1,139 | C++ | OpenXR loader & SDK headers |
| `IvanCampos/visionOS-examples` | 405 | Swift | visionOS / Apple Vision Pro spatial examples |
| `microsoft/xr-development-for-beginners` | 564 | Vue | Spatial computing learning curriculum |
| `google/spatial-media` | 2,116 | C++ | 360° video + spatial audio tooling |
| `GoogleChrome/omnitone` | 911 | JavaScript | Web spatial audio rendering (FOA/HOA) |
| `leomccormack/Spatial_Audio_Framework` | 748 | C | Cross-platform spatial audio algorithms |
| `freeman-jiang/beatsync` | 3,158 | JavaScript | High-precision multi-device spatial audio |
| `markdaws/arkit-by-example` | 481 | Objective-C | Apple ARKit example app |
| `microsoft/MixedReality-WebRTC` | 944 | C# | MR audio/video real-time communication |

---

## Hottest Open Issues by Episode

### Episode 1 — Perceptual Latency

| Issue | Repo | Comments | Key Insight |
|---|---|---|---|
| WiVRn #282 — Stuttering headset/controller position | WiVRn/WiVRn | 40 | Maintainer `xytovl` traced stutter to >10ms reception-time variability — temporal irregularity, not pipeline depth, is the real culprit |
| WiVRn #234 — Unstable controller tracking feeling | WiVRn/WiVRn | 20 | Low-frequency jitter feels "wrong" even when point-to-point accuracy is fine — perceptual vs. measured discrepancy |
| WiVRn #741 — Passthrough activation lockup | WiVRn/WiVRn | 15 | Passthrough mode triggers full system lockup — perceptual break at the OS level |
| WiVRn #873 — Compositor changes cause GPU perf drops | WiVRn/WiVRn | 16 | Platform-level performance regression breaks latency budget on consumer hardware |
| ARCore Unity SDK #206 — Instant Preview not connecting | google-ar/arcore-unity-sdk | 44 | Dev workflow latency erases creative confidence |
| ARCore Unity SDK #277 — Camera feed drop on GLES2 | google-ar/arcore-unity-sdk | 25 | GPU path selection breaks perceptual continuity |
| ARFoundation Samples #1113 — AsyncOperation iOS slowdown | Unity-Technologies/arfoundation-samples | 16 | Frame drops cause vestibular-visual conflict — 20ms threshold violated |
| ARFoundation Samples #615 — TrueDepth front-facing depth | Unity-Technologies/arfoundation-samples | 21 | Depth sensor latency limits avatar fidelity — your face isn't where your head is |

### Episode 2 — Spatial Audio

| Issue / PR | Repo | Comments | Key Insight |
|---|---|---|---|
| Omnitone: FOA vs. HOA rendering gap | GoogleChrome/omnitone | — | Web spatial audio lacks the resolution for true externalization; HOA is computationally out of reach for browsers today |
| Spatial_Audio_Framework: Personalized HRTF challenge | leomccormack/Spatial_Audio_Framework | — | Generic HRTFs don't work for everyone; individual ear geometry makes a difference we can't easily measure at scale |
| beatsync: Clock sync across devices | freeman-jiang/beatsync | — | Multi-device spatial audio requires clock precision that current web APIs don't expose |
| Mach1 Studios: Real-time binaural on mobile | Avnerus (external) | — | Constrained hardware can still deliver HRTF rendering if you architect for it — a counterpoint to "browsers can't do it" |
| WebXR spec: No spatial audio API | immersive-web/webxr | — | The spec defines `viewer` and `local` reference spaces but has zero spatial audio support — a fundamental gap |

### Episode 3 — MR Interfaces & Spatial UI

| Issue | Repo | Comments | Key Insight |
|---|---|---|---|
| MixedRealityCompanionKit #228 — SpectatorView calibration fails | microsoft/MixedRealityCompanionKit | 19 | Hologram registration that works once and never twice — blocks research reproducibility and everyday MR use |
| OpenXR-MR #131, #132 — HoloLens 2 viewfinder issues | microsoft/MixedRealityToolkit-Unity | — | Direct3D 12 path stability; frame-timestamp precision for viewfinder reliability |
| StereoKit: MR interaction design patterns | StereoKit/StereoKit | — | How do you design UI that exists in 3D space? Interaction patterns that work across OpenXR and WebXR |
| AR.js 2→3 rebuild | AR-js-org/AR.js | — | Community-driven transition — what does it mean for the future of web-based spatial interfaces? |

---

## Key GitHub Contributors Surfaced

| Username | Repo(s) | Domain | Why They Matter |
|---|---|---|---|
| **xytovl** | WiVRn | VR streaming / OpenXR | Traced stutter to temporal irregularity — reframes latency science |
| **leinardi** | SteamVR-for-Linux | VR latency debugging | Open-source VR performance forensics |
| **jd-3d** | ALVR | VR streaming | Discovered 30–50% latency underreporting in VR stacks |
| **leomccormack** | Spatial_Audio_Framework | Spatial audio | Cross-platform ambisonics & HRTF implementation in C |
| **jeromeetienne** | AR.js | Web AR | Creator of the most-starred web AR framework; leading AR.js 3 rebuild |
| **hiukim** | MindAR | Web AR | On-device AR with TensorFlow.js; production-ready tracking |
| **maluoi** | StereoKit | XR engine | Dual OpenXR + WebXR backend architecture; performance optimization |
| **freeman-jiang** | beatsync | Spatial audio sync | Multi-device clock synchronization for presence maintenance |
| **orighst (Boris Smus)** | omnitone | Web spatial audio | Google's FOA/HOA web implementation; the gap between web and native |
| **BinWang28** | audio-ai-hub | HRTF research | Personalized HRTF modeling; spatial speech perception |
| **ademlek** | MixedRealityToolkit-Unity | MR tooling | MRTK contributor; interface design patterns for HoloLens 2 |

---

## Cross-Cutting Observations

1. **Temporal irregularity > average latency** — The WiVRn #282 discussion is a paradigm shift. The community is moving from "reduce ms" to "stabilize frame delivery." This should frame Episode 1's narrative.
2. **Web spatial audio is stranded** — Omnitone implements FOA but not full binaural rendering. The WebXR spec has no spatial audio API. Native platforms (Apple, Meta) ship proprietary spatial audio. The web is the only truly open platform for spatial audio — and it's falling behind.
3. **The WebXR spec is visual-centric** — Haptics, spatial audio, and biometric sensors are afterthoughts. For MR, where the physical world is the backdrop, this is an architectural gap that the immersive-web working group has not seriously addressed.
4. **MR calibration is unsolved** — SpectatorView calibration (MixedRealityCompanionKit #228) works once and never twice. Persistent hologram registration remains a lab-only solution. This is a core Episode 3 topic.
5. **Accessibility is the next frontier** — Spatial audio for the visually impaired (Amelia Eckard's Vision Pro research, Sound of Vision), personalized HRTFs for users with hearing differences, and haptic wayfinding are growing research areas that the podcast should spotlight.

---

*This document is a living audit. Contribute by adding new issues, PRs, and researcher profiles as comments on the relevant episode issue.*
