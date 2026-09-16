# GitHub Research Addendum — The Future of Human Perception

> Research conducted 2026-09-16. Hot issues, contributor names, and debate topics mined from the most active AR/MR/Spatial Computing repositories on GitHub.

---

## Repositories Surveyed (Expanded)

| Repository | Stars | Language | Focus |
|---|---|---|---|
| `playcanvas/engine` | 16,703 | JavaScript | Web graphics runtime (WebGL/WebGPU/WebXR) |
| `mrdoob/three.js` | 115,575 | JavaScript | 3D library, foundational for AR/VR web apps |
| `jeromeetienne/AR.js` → `AR-js-org/AR.js` | 15,789 | HTML | Web AR — marker-based & location-based |
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
| `XuanJi-ISA/Isaac-Sim-Addons` | — | Python | Sonic Palette — color-hearing for the blind |

---

## Hottest Open Issues by Episode Topic

### Episode 1 — Perceptual Latency

| # | Issue | Repo | Comments | Why it's hot |
|---|---|---|---|---|
| 1 | Stuttering headset/controller position | `WiVRn/WiVRn #282` | 40 | Maintainer `xytovl` traced it to >10ms reception-time variability — each spike causes a dropped/mangled frame. Core debate: is it *temporal irregularity* the brain detects, not just pipeline latency? |
| 2 | Unstable feeling controller tracking | `WiVRn/WiVRn #234` | 20 | Low-frequency jitter that feels "wrong" even when point-to-point accuracy is fine — textbook perceptual-vs-measured discrepancy. |
| 3 | Passthrough activation / 72Hz lockup | `WiVRn/WiVRn #741` | 15 | Passthrough mode triggers a full system lockup — a perceptual break at the OS level. |
| 4 | Compositor changes cause NVIDIA GPU performance drops | `WiVRn/WiVRn #873` | 16 | Platform-level performance regression breaks the latency budget on consumer hardware. |
| 5 | Instant Preview not connected after first run | `google-ar/arcore-unity-sdk #206` | 44 | Dev workflow latency erases creative confidence — if the tool lags, the creator doubts the output. |
| 6 | Camera feed drop on GLES2 | `google-ar/arcore-unity-sdk #277` | 25 | GPU path selection breaks perceptual continuity — the camera feed vanishing is a direct presence breaker. |
| 7 | AsyncOperation iOS slowdown | `Unity-Technologies/arfoundation-samples #1113` | 16 | Frame drops directly cause vestibular-visual conflict — the 20ms threshold violated in practice. |
| 8 | TrueDepth front-facing depth map | `Unity-Technologies/arfoundation-samples #615` | 21 | Depth sensor latency limits avatar fidelity — your face isn't where your head is. |
| 9 | Missing latency in VR streaming | `polygraphene/ALVR #334` | — | Researcher found ~33.6ms of unaccounted latency; VR stacks underreport total system latency by 30–50%. |
| 10 | Calibration instability (SpectatorView) | `microsoft/MixedRealityCompanionKit #228` | 19 | Works once, never twice — blocks research reproducibility in spatial tracking. |

### Episode 2 — Spatial Audio

| # | Issue | Repo | Comments | Why it's hot |
|---|---|---|---|---|
| 1 | Support for mobile browsers | `GoogleChrome/omnitone #2` | 23 | Open since 2016, still unfixed. Billion mobile users can't experience 3D audio. |
| 2 | Improve audio spatialization behaviors | `Hubs-Foundation/hubs #1853` | 30 | Hubs is the most-populated social VR platform; spatial audio quality is the #1 UX complaint. |
| 3 | >20 people in room causes audio issues | `Hubs-Foundation/hubs #5057` | 24 | Spatial audio doesn't scale for social XR — the cocktail party problem is unsolved at the engine level. |
| 4 | Consider hooking up sound source nodes | `immersive-web/webxr #390` | 30 | Open since 2018 — the WebXR spec still has no native spatial-audio API. Sound is an afterthought. |
| 5 | ISM RIR incorrect summing of bands | `leomccormack/Spatial_Audio_Framework #58` | — | Fundamental bug in room-acoustics modeling that undermines perceptual realism. |
| 6 | HRTF dataset loading bugs | `leomccormack/Spatial_Audio_Framework #55` | — | Even the dataset loading is broken — researchers can't reproduce results. |
| 7 | ADM2 does not play any sound | `microsoft/MixedReality-WebRTC #573` | — | Spatial audio breaks when communication stacks mix with spatial rendering. |
| 8 | Spec language precludes non-visual uses | `immersive-web/webxr #815` | 41 | The WebXR spec is architecturally visual — audio and haptics are afterthoughts. |
| 9 | Sonic Palette (color-hearing for the blind) | `XuanJi-ISA #62` | 6 | Cross-modal spatial audio — using sound to substitute for vision in navigation. |

### Episode 3 — Mixed Reality Interfaces

| # | Issue | Repo | Comments | Why it's hot |
|---|---|---|---|---|
| 1 | Holograms sticking to camera (SpectatorView) | `microsoft/MixedRealityCompanionKit #221` | 18 | Core MR presence failure — geometrically correct placement isn't enough; the brain rejects drifting holograms. |
| 2 | SpectatorView calibration fragility | `microsoft/MixedRealityCompanionKit #228` | 19 | Works once, never twice — blocks research reproducibility in spatial tracking. |
| 3 | MX Ink MR Stylus for Meta Quest | `MixedRealityToolkit/MixedRealityToolkit-Unity #914` | — | Platform convergence without interface abstraction: a Quest user wants HoloLens tools. High-priority, still unimplemented. |
| 4 | Missing docs on HoloLens 2 mixed reality capture | `MixedRealityToolkit/MixedRealityToolkit-Unity #987` | 4 | Even Microsoft's own toolkit can't document how to turn on MRC for HoloLens 2. |
| 5 | Vendor plugin architecture in MRTK | `MixedRealityToolkit/MixedRealityToolkit-Unity #511` | 2 | Should vendor RealityProviders live in core MRTK or as plugins? Architectural question shaping MR dev for the next decade. |
| 6 | Content in immersive session search around | `immersive-web/webxr #992` | 36 | Wayfinding: users don't know where they are in immersive sessions — a fundamental spatial-awareness gap. |
| 7 | Give developers control over "overlay" browser | `immersive-web/webxr #1365` | 16 | UI/UX design in XR — composite 2D UI into 3D worlds without killing performance. |
| 8 | WebXR integration with HTML-in-canvas | `immersive-web/webxr #1414` | — | DOM overlays in XR canvas — how do you layer 2D UI into 3D without performance collapse? |
| 9 | Dynamic foveation | `immersive-web/webxr #1420` | — | Rendering asymmetry (high-res center, low-res periphery) as a perceptual-performance lever. |
| 10 | AR Foundation — Image Tracking Offset/Drift | `Unity-Technologies/arfoundation-samples #1220` | 0 | Large-scale model tracking drift under real-world motion — the registration problem at scale. |

---

## Prominent Developers & Researchers (Potential Guests)

### AR / Web AR
| Name | Repo / Role | Relevance |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR godfather; marker-based & geospatial AR |
| **hiukim** | Creator, MindAR (2.7k ⭐) | On-device image/face tracking, TensorFlow.js |

### Latency & Streaming
| Name | Repo / Role | Relevance |
|---|---|---|
| **leinardi** | Maintainer, SteamVR-for-Linux | Motion-to-photon latency, open VR |
| **jd-3d** | Developer, ALVR | VR streaming stack forensics; discovered "missing" latency |
| **xytovl** | Maintainer, WiVRn (1.6k ⭐) | OpenXR streaming; packet-timing & pacing algorithm design; traced stutter to temporal irregularity |
| **AaronMillward** | Contributor, WiVRn | Field reports of perceptual stutter & motion sickness from real users |

### Mixed Reality / HoloLens
| Name | Repo / Role | Relevance |
|---|---|---|
| **brycehutchings** | Microsoft OpenXR contributor (MRTK3) | MR performance, Direct3D 12 |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform advocacy & developer ecosystem |
| **emaschino** | Microsoft MRC | HoloLens 2 performance & mixed-reality compositor |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration assignee (#221, #228) |
| **keveleigh** | Microsoft MRTK maintainer | MRTK #511 vendor architecture, #987 docs |
| **StephenHodgson, FejZa, jdwalker** | XRTK core team | MR interaction design & rendering architecture |
| **dongyoonpark** | Microsoft MRDL | Periodic Table on HoloLens 2; tactile MR design |

### WebXR / Immersive Web
| Name | Repo / Role | Relevance |
|---|---|---|
| **toji** | WebXR spec maintainer | Overall spec direction & spec language |
| **cwilso** | W3C Immersive Web | Dynamic foveation & visibility masking |
| **cabanier** | W3C Immersive Web | WebXR DOM overlays & visibility |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation & accessibility; spec language for non-visual XR |
| **himorin** | WebXR contributor | Security & privacy of spatial mapping |
| **chrisdavidmills** | WebXR editor | Visibility-mask events & compositing layers |
| **danrossi** | WebXR layers work | Projection-layer rendering & scaling |
| **aphillia** | WebXR contributor | Input profiles & i18n for XR |
| **jayefuu** | WebXR contributor | Visibility & projection layer work |
| **ddorwin** | Accessibility lead | Non-visual spec language (#815) |
| **idrisshah** | Accessibility lead | Immersive content search & wayfinding (#992) |

### Spatial Audio
| Name | Repo / Role | Relevance |
|---|---|---|
| **leomccormack** | Creator, Spatial_Audio_Framework (748 ⭐) & SPARTA | Ambisonics, HRTFs, ISM room modeling |
| **crlandsc, ali-vosoughi, jacobhollebon** | Contributors, Spatial_Audio_Framework | Spatialization algorithms |
| **fabiangiovagnoli** | Creator, beatsync (3.2k ⭐) | High-precision multi-device spatial audio |
| **hoch** | Maintainer, Omnitone | Mobile browser spatial audio gap (#2) |
| **misslivirose** | Hubs-Foundation | Audio spatialization & accessibility |
| **robertlong** | Hubs-Foundation | Audio reliability engineering |
| **BinWang28** | audio-ai-hub | HRTF research & spatial speech perception |
| **edurnebernal** | Researcher | Audio-visual spatial perception in VR |
| **TheBarmaEffect** | echo engine | Perception-first spatial audio engine |
| **ameliaeckard** | Researcher | Spatial audio for visual impairment (Apple Vision Pro) |
| **Boris Smus / Brandon Jones / Julius Kammerl** | Google / Omnitone | Web binaural rendering |

### XR Engine / Framework
| Name | Repo / Role | Relevance |
|---|---|---|
| **maluoi** | Maintainer, StereoKit (1.1k ⭐) | XR engine, OpenXR backend & rendering pipeline |
| **paulmelis** | StereoKit contributor | Rendering & interaction systems |

### Neuroadaptive & Cross-Modal
| Name | Repo / Role | Relevance |
|---|---|---|
| **S. Hussain Ather, Alif Jakir, Tsing Liu, Yechan Ian Seo** | Team Syncer (OpenGalea) | Neuroadaptive MR — 8-channel EEG + Quest 3 for brain-controlled experiences |

---

## Cross-Cutting Hot Debates

### 1. Perceptual Latency: Temporal Irregularity > Average Latency
The WiVRn #282 finding is paradigm-shifting: maintainer `xytovl` traced headset/controller stutter to >10ms of *reception-time variability*, not raw pipeline latency. Each spike causes a dropped/mangled frame. The community debate: **is the brain detecting average pipeline latency, or temporal frame irregularity?** If it's the latter, current optimization targets (reduce average ms) are wrong — we need to stabilize frame pacing instead. This reframes the entire "20ms rule" discussion.

### 2. VR Streaming Underreports Latency by 30–50%
ALVR #334: a researcher found ~33.6ms of unaccounted latency in a VR streaming stack. Current VR streaming optimizations target the wrong metric — the true perceptual latency is 30–50% higher than what monitoring tools report. This means the industry has been optimizing against a phantom number.

### 3. Spatial Audio IsArchitecturally Absent from WebXR
WebXR #390 (open since 2018, 30+ comments): the spec has no spatial-audio element. The API surface was designed for visual XR — sound is bolted on, not built in. Combined with Omnitone #2 (mobile gap, 10+ years unresolved) and Hubs #5057 (doesn't scale past 20 users), spatial audio is the XR field's most neglected dimension.

### 4. MR Registration ≠ MR Acceptance
MRC #221 (18 comments): even geometrically correct hologram placement is rejected by the brain if it drifts, sticks to camera, or fails to stay anchored. The open question: what turns geometric alignment into perceptual acceptance? Is it temporal stability, haptic feedback, audio anchoring, or something deeper in the perceptual hierarchy?

### 5. The WebXR Spec Is Visually Blind
Issues #815 (41 comments) and #992 (36 comments): the WebXR specification literally precludes non-visual uses. Wayfinding in immersive sessions is broken (users don't know where they are). DOM overlays in canvas (#1414) and dynamic foveation (#1420) are being bolted on at the edges — but the core spec assumes eyes-only.

### 6. Input Fragmentation: Convergence Without Abstraction
MRTK #914 (MX Ink stylus on Meta Quest): hardware platforms are converging (HoloLens, Quest 3, Vision Pro, XREAL), but software abstraction layers haven't. Developers still write platform-specific input code. MRTK #511 asks the architectural question that will shape MR development for a decade: should vendor RealityProviders live in core MRTK or as plugins?

### 7. Neuroadaptive MR: Brain-Controlled Experiences
OpenGalea (Team Syncer) — MIT Reality Hack Meta winner — fuses an 8-channel EEG with a Quest 3 for brain-controlled, colocated multiplayer MR. The question: should interfaces respond to attention/relaxation (EEG-derived) rather than (or in addition to) physical input? This blurs the line between perception and control.

### 8. Scalability: Can Spatial Audio Work for 20+ People?
Hubs issues #1853 and #5057 prove that spatial audio quality degrades under CPU load and user count. No engine today ships a real-time spatial-audio renderer that works for 20+ simultaneous listeners. This is the barrier to social XR at scale.
