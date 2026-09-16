# Research Supplement — Episode Deep Dives (2026-09-16)

> Supplementary research findings discovered during the "Future of Human Perception" podcast planning,
> covering repos and debates not present in the original research addendum.

---

## 1. WiVRn — OpenXR Streaming & Perceptual Jitter

| Field | Detail |
|---|---|
| **Repo** | [WiVRn/WiVRn](https://github.com/WiVRn/WiVRn) (1,675 ⭐, C++) |
| **Focus** | Linux OpenXR streaming to standalone headsets (Quest, etc.) |
| **Key Issues** | |
| `#282` | "Stuttering Headset/Controller Position" — 40 comments. Maintainer `xytovl` traced stutter to >10 ms of reception-time variability; each spike causes a dropped/mangled frame. Debate: Is measured pipeline latency or temporal irregularity what the brain actually detects? |
| `#234` | "Unstable feeling controller tracking" — 20 comments. Low-frequency jitter that feels "wrong" even when point-to-point accuracy looks fine — textbook perceptual-vs-measured discrepancy. |
| `#741` | Passthrough activation / 72 Hz lockup when passthrough triggers or headset reconnects (15 comments). |
| `#873` | Compositor changes causing severe performance drops on NVIDIA GPUs (16 comments). |
| **Maintainer** | `xytovl` — latency pacing, packet-timing forensics |
| **Notable Contributor** | `AaronMillward` — field reports of perceptual stutter & motion sickness |

**Podcast Angle (Episode 1):** The WiVRn debates expose a new dimension of the latency problem: it's not just *how fast* you render, but *how consistently*. Temporal irregularity may be perceptually more disruptive than absolute latency — reframing the entire "sub-20ms" optimization narrative.

---

## 2. StereoKit — XR Engine & Input Profiles

| Field | Detail |
|---|---|
| **Repo** | [StereoKit/StereoKit](https://github.com/StereoKit/StereoKit) (1,077 ⭐, C#) |
| **Focus** | Easy-to-use XR engine (WebXR + OpenXR backend) |
| **Key Issues** | |
| `#345` | WebXR backend display issues |
| `#1209` | WebXR backend display issues |
| `#1329` | OpenXR 1.1 spec implications |
| `#511` | Vendor plugin architecture — should vendor-specific RealityProviders live in the core MRTK? |
| **Maintainer** | `maluoi` |

**Podcast Angle (Episode 3):** StereoKit's input profiles for WebXR and OpenXR reveal a platform convergence problem: the spec is visual-centric (#815, 41 comments) but developers need non-visual spatial interaction paradigms. The engine-level abstraction layer (StereoKit) may be more important than toolkit-level.

---

## 3. ZED SDK — Hardware-Accelerated Spatial Perception

| Field | Detail |
|---|---|
| **Repo** | [stereolabs/zed-sdk](https://github.com/stereolabs/zed-sdk) (1,235 ⭐, C++) |
| **Focus** | Cross-platform depth sensing, spatial mapping, body tracking |
| **Key Features (v5.4)** | |
| NEURAL depth inference | 20% faster on Jetson Thor, ~15% lower GPU load |
| `DEPTH_MODE::CUSTOM` | Feed external stereo networks into the SDK each frame |
| `MONOTONIC_RAW_CLOCK` | Timestamps immune to NTP/PTP step/frequency adjustments |
| `LENS_DISTORTION_MODEL` | Per-camera lens distortion model exposed via API |
| SLAM GEN_3 | Per-pose confidence reporting |
| | **Limitation**: Requires NVIDIA GPU (Compute Capability > 5) |

**Podcast Angle (Episode 3):** The ZED SDK forces a hardware-vs-software perception debate. NVIDIA-only depth sensing vs. open-source marker tracking (artoolkitX, AR.js) — which actually serves the *perceptual* needs of MR? Does real understanding of physical space matter more than convincing the brain it's real?

---

## 4. artoolkitX — Cross-Platform AR Tracking

| Field | Detail |
|---|---|
| **Repo** | [artoolkitx/artoolkitx](https://github.com/artoolkitx/artoolkitx) (511 ⭐, C) |
| **Focus** | High-performance video acquisition, marker & texture tracking |
| **Platforms** | macOS, iOS, Android, Windows, Linux, Emscripten (WebAssembly) |
| **License** | LGPL v3.0 |
| **Build Matrix** | ✅ macOS ✅ iOS ✅ Android ✅ Linux ✅ Windows ✅ Emscripten |
| **Community** | [forums.artoolkitx.org](https://forums.artoolkitx.org) |

**Podcast Angle (Episode 3):** artoolkitX's 6-platform build matrix makes it uniquely positioned for cross-platform AR research. Its focus on native-code performance plus experimental WebAssembly support bridges the gap between mobile AR and web AR — directly relevant to the perceptual latency discussion in Episode 1.

---

## 5. Perceptual Similarity — Measuring What We Perceive

| Field | Detail |
|---|---|
| **Repo** | [richzhang/PerceptualSimilarity](https://github.com/richzhang/PerceptualSimilarity) (4,276 ⭐, Python) |
| **Focus** | LPIPS (Learned Perceptual Image Patch Similarity) metric |
| **Use Case** | How to objectively measure whether two images *look* the same to a human, not just whether they differ pixel-by-pixel |

**Podcast Angle (Episode 2 & 3):** The LPIPS metric revolutionizes how we measure perceptual quality — but it's images only. What's the equivalent for spatial audio? For hologram registration? For motion-to-photon latency? The "perceptual measurement gap" is a fundamental research challenge.

---

## 6. OpenGalea — Neuroadaptive Mixed Reality

| Field | Detail |
|---|---|
| **Project** | [Caerii/OpenGalea](https://github.com/Caerii/OpenGalea) — Team Syncer |
| **Award** | MIT Reality Hack Meta 2025 Winner |
| **Focus** | 8-channel EEG fused with Meta Quest 3 for brain-controlled colocated multiplayer MR |
| **Key Features** | |
| EEG integration | Attention/relaxation-derived interface triggers |
| Colocated multiplayer | Spatially-anchored shared experiences |
| Brain-controlled UI | User responds to neuro-adaptive cues, not just hand gestures |

**Podcast Angle (Episode 3):** The neuroadaptive MR frontier. If OpenGalea proves that brain-derived attention signals can drive spatial UI, the entire input paradigm shifts from "hands and controllers" to "attention and intention." This is the next 10 years of spatial computing.

---

## Enhanced Contributor Directory

| Contributor | Repos | Expertise | Appears In |
|---|---|---|---|
| **jeromeetienne** | AR.js (15.8k ⭐) | Web AR tracking, markerless AR | Ep. 1, Ep. 3 |
| **nicolocarpignoli** | AR-js-org/AR.js | Web AR maintainer | Ep. 1 |
| **hiukim** | MindAR (2.7k ⭐) | TensorFlow.js AR tracking | Ep. 1, Ep. 3 |
| **leomccormack** | Spatial_Audio_Framework, SPARTA | HRTF, ambisonics, temporal rendering | Ep. 2 |
| **freeman-jiang** | beatsync (3.2k ⭐) | Multi-device spatial audio | Ep. 2 |
| **leomccormack** | Spatial_Audio_Framework | Spatial audio algorithms | Ep. 2 |
| **hoch** | omnitone | Web spatial audio rendering | Ep. 2 |
| **xytovl** | WiVRn | OpenXR streaming, latency pacing | Ep. 1 |
| **leinardi** | SteamVR-for-Linux | Motion-to-photon latency | Ep. 1 |
| **jd-3d** | ALVR | VR streaming latency | Ep. 1 |
| **maluoi** | StereoKit | XR engine, OpenXR backend | Ep. 1, Ep. 3 |
| **keveleigh** | MRTK-Unity, OpenXR-MR | MR performance, vendor plugins | Ep. 1, Ep. 3 |
| **brycehutchings** | OpenXR-MixedReality | MR performance, Direct3D 12 | Ep. 1 |
| **fredemmott** | Microsoft XR | HoloLens platform advocacy | Ep. 1, Ep. 3 |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration | Ep. 1, Ep. 3 |
| **cabanier** | W3C Immersive Web | WebXR DOM overlays, visibility | Ep. 3 |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation, accessibility | Ep. 3 |
| **himorin** | WebXR | Security/privacy of spatial mapping | Ep. 3 |
| **chrisdavidmills** | WebXR | Visibility-mask events | Ep. 3 |
| **danrossi** | WebXR | Layers & projection rendering | Ep. 3 |
| **richzhang** | PerceptualSimilarity | Perceptual quality metrics | Ep. 2, Ep. 3 |
| **stechyo** | godot-steam-audio | Cross-engine spatial audio | Ep. 2 |
| **Team Syncer** | OpenGalea | Neuroadaptive (EEG + Quest 3) MR | Ep. 3 |
| **AaronMillward** | WiVRn | Field reports of perceptual stutter | Ep. 1 |
| **Ivan Campos** | visionOS-examples (405 ⭐) | Apple Vision Pro spatial UI | Ep. 3 |
| **BinWang28** | audio-ai-hub | HRTF research & spatial speech | Ep. 2 |
| **edurnebernal** | — | Audio-visual spatial perception in VR | Ep. 2 |
| **ameliaeckard** | spatial-audio-research-arvr | Spatial audio for visual impairment | Ep. 2 |
| **alextawes19** | SYNC-MR | Colocated MR + Velnet spatial audio | Ep. 2, Ep. 3 |
| **TheBarmaEffect** | echo engine | Perception-first spatial audio engine | Ep. 2 |

---

## Cross-Episode Debate Summary

| Debate | Ep # | Key GitHub Issues |
|---|---|---|
| Perceptual vs. measured latency | 1 | SteamVR-for-Linux #21, ALVR #334, WiVRn #282, WiVRn #234 |
| Temporal irregularity vs. absolute latency | 1 | WiVRn #282 (new angle!) |
| "Missing" system latency in VR streaming | 1 | ALVR #334 |
| Web AR tracking failure on mobile | 1 | AR.js #826, AR.js #825, MindAR #556, MindAR #526 |
| Audio before vision (reflexive perception) | 2 | omnitone #2, Spatial_Audio_Framework issues |
| HRTF personalization vs. generic | 2 | Spatial_Audio_Framework #55, audio-ai-hub research |
| Mobile spatial audio gap | 2 | omnitone #2 (23 comments!) |
| Hologram drift / "stick to camera" | 3 | MixedRealityCompanionKit #221 |
| MR input fragmentation | 3 | MRTK-Unity #914, StereoKit #345, webxr #815 |
| Hardware vs. software spatial perception | 3 | ZED SDK vs. artoolkitX vs. AR.js |
| Neuroadaptive MR (EEG-driven interfaces) | 3 | OpenGalea (Team Syncer) |
| WebXR accessibility gap | 3 | webxr #815 (41 comments), webxr-samples artifacts |
