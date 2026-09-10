# Supplementary Community Research — The Future of Human Perception

> Companion research gathered from live, active GitHub communities (last updated 2026).
> This file supplements `RESEARCH-Database.md` and the episode outline files with
> additional repos, on-the-ground debates, and potential guest contributors.

## Active Repositories (by subdomain)

### Web / Standalone AR
| Repo | Stars | Note |
|------|-------|------|
| `jeromeetienne/AR.js` | 15,789 | Largest web-AR repo; marker-based + location-based AR |
| `hiukim/mind-ar-js` | 2,725 | Image/face tracking with TensorFlow.js |
| `MozillaReality/FirefoxReality` | 773 | (INACTIVE) Immersive headset browser |

### Spatial Audio
| Repo | Stars | Note |
|------|-------|------|
| `freeman-jiang/beatsync` | 3,158 | High-precision multi-device spatial audio player |
| `google/spatial-media` | 2,116 | 360° video + spatial audio tooling |
| `GoogleChrome/omnitone` | 911 | Web spatial audio rendering |
| `leomccormack/Spatial_Audio_Framework` | 748 | Cross-platform C spatial audio algos |
| `stechyo/godot-steam-audio` | 679 | Immersive spatial audio for Godot (SteamAudio) |

### Spatial Computing / OpenXR / MR
| Repo | Stars | Note |
|------|-------|------|
| `WiVRn/WiVRn` | 1,639 | Linux OpenXR streaming to standalone headsets |
| `KhronosGroup/OpenXR-SDK` | 1,139 | OpenXR loader headers |
| `KhronosGroup/OpenXR-SDK-Source` | 824 | OpenXR loader source & layers |
| `mbucchia/OpenXR-Toolkit` | 442 | Features to improve OpenXR apps |
| `microsoft/OpenXR-MixedReality` | 360 | OpenXR samples for HoloLens / Windows MR |
| `microsoft/xr-development-for-beginners` | 564 | Spatial computing learning curriculum |
| `IvanCampos/visionOS-examples` | 405 | visionOS / Apple Vision Pro spatial examples |

---

## Hottest Live Debates (from open issues)

### 1. Perceptual Latency & Motion-to-Photon Jitter
- **WiVRn #282 — "Stuttering Headset/Controller Position"** (40 comments): Players report visible stutter correlated to network/received-packet timing. Maintainer `xytovl` traced it to **>10 ms of reception-time variability**, each spike causing a dropped/mangled frame, and debated tweaking the pacing algorithm at the cost of higher base latency. Community debate: Is the measured pipeline latency or the *temporal irregularity* what the brain actually detects?
  - https://github.com/WiVRn/WiVRn/issues/282
- **WiVRn #234 — "Unstable' feeling controller tracking"** (20 comments): Describes low-frequency jitter that feels "wrong" even when point-to-point accuracy looks fine — a textbook perceptual-vs-measured discrepancy.
  - https://github.com/WiVRn/WiVRn/issues/234
- **WiVRn #741 — Passthrough activation / 72 Hz lockup** when passthrough mode triggers or the headset reconnects (15 comments).
  - https://github.com/WiVRn/WiVRn/issues/741
- **WiVRn #873 — Compositor changes causing severe performance drops on NVIDIA GPUs** (16 comments).
  - https://github.com/WiVRn/WiVRn/issues/873

### 2. Mixed Reality Interfaces & Tracking Fidelity
- **mind-ar-js #556 — "Unstable AR Content and Ineffective Tracking Configurations"** (5 comments): Practitioners debate whether markerless tracking is production-ready.
  - https://github.com/hiukim/mind-ar-js/issues/556
- **mind-ar-js #526 — "Is this repo abandonware? Should I switch to ar.js?"** (13 comments): Community weighing maintenance health and framework choice.
  - https://github.com/hiukim/mind-ar-js/issues/526
- **AR.js #833 — "Markerless AR visible across an entire city"**: Aspirational markerless / geospatial AR use-case.
  - https://github.com/jeromeetienne/AR.js/issues/833
- **AR.js #822 — THREE.math rename breaking location-based logic**: How upstream library churn breaks spatial-map stability.
  - https://github.com/jeromeetienne/AR.js/issues/822

### 3. Spatial Audio
- Source repos with active spatial-audio pipelines: `leomccormack/Spatial_Audio_Framework`, `google/spatial-media` (360° sync), `GoogleChrome/omnitone` (web binaural), `beatsync` (multi-device).
- Cross-modal design theme: auditory spatial cues are processed faster and more reflexively than visual — what this means for MR/audio-first interface design (see episode outline files).

---

## Potential Guest Candidates

| Name | Repo / Role | Relevance |
|------|-------------|-----------|
| **jeromeetienne** | Creator, AR.js (15.8k⭐) | Web AR godfather; marker-based & geospatial AR |
| **hiukim** | Creator, MindAR (2.7k⭐) | On-device image/face tracking, TF.js |
| **xytovl** | WiVRn maintainer | OpenXR streaming, latency pacing & packet-timing forensics |
| **AaronMillward** | WiVRn contributor | Field reports of perceptual stutter & motion sickness |
| **mbucchia** | OpenXR-Toolkit author | Improving OpenXR app latency/quality |
| **Ivan Campos** | visionOS-examples (405⭐) | Apple Vision Pro spatial UI patterns |
| **leomccormack** | Spatial_Audio_Framework creator | Ambisonics, HRTFs, cross-platform spatial audio |
| **emaschino** | Microsoft OpenXR-MR | HoloLens 2 performance & viewfinder reliability |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform & mixed-reality advocacy |
| **GoogleChrome/omnitone** team | Web spatial audio rendering | Browser-based binaural rendering |

---

## Suggested Episode Seeding (for issues #1, #2, #3)
- **Episode 1 (Latency):** Reference WiVRn #282/#234 debate; guests leomccormack (temporal rendering), xytovl/AaronMillward (streaming latency), maluoi (StereoKit).
- **Episode 2 (Spatial Audio):** Pull from google/spatial-media, omnitone, Spatial_Audio_Framework; guests leomccormack, beatsync/god, ameliaeckard (accessibility angle).
- **Episode 3 (MR Interfaces):** Web-AR frontier (AR.js, mind-ar-js) + visionOS (Ivan Campos) + OpenXR standardization (KhronosGroup); guests jeromeetienne, hiukim, Ivan Campos, emaschino.
