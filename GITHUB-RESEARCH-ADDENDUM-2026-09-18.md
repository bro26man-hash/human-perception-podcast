# 🔬 GitHub Research Addendum — September 18, 2026

## Summary of New Findings

This addendum captures research gathered on September 18, 2026, surveying the most active AR, spatial computing, and perceptual science repositories on GitHub. It supplements the existing episode outlines with live issue data, newly identified contributors, and cross-repo thematic connections.

---

## Active Repositories Surveyed

### 1. jeromeetienne/AR.js → AR-js-org/AR.js (15,791 ⭐)
- **Language:** HTML/JavaScript | **License:** MIT
- The foundational Web AR library. Marker-based and geolocation-based AR for the browser.
- **Key development:** AR.js has migrated to an organization account (AR-js-org) and is undergoing a major architectural transition.
- **Repo URL:** https://github.com/AR-js-org/AR.js

### 2. microsoft/MixedReality-WebRTC (944 ⭐)
- **Language:** C#/C++ | **License:** MIT
- Real-time audio/video/data communication for mixed reality apps. Supports HoloLens 2.
- **Status:** Deprecated — no longer accepting commits. The community must fork and maintain it.
- **Key issues:** #130 (Spatial mesh streaming throughput), #157 (AEC failure), #74 (H.264 encoding quality)
- **Repo URL:** https://github.com/microsoft/MixedReality-WebRTC

### 3. google/lullaby (1,197 ⭐)
- **Language:** C++ | **License:** Apache-2.0
- Google's internal VR/AR engine. ECS architecture. Full 3D environments with spatial audio.
- **Used by:** VR Home, Play Store, YouTube, Play Movies, Earth
- **Status:** No external PRs accepted. The open-source spatial audio story has a "dead end" problem.
- **Repo URL:** https://github.com/google/lullaby

### 4. microsoft/MixedRealityCompanionKit (594 ⭐)
- **Language:** C# | **License:** MIT
- Components that pair with HoloLens for Windows Mixed Reality experiences.
- **Key features:** Holographic Remoting, Kinect IPD, SpectatorView, RealtimeStreaming
- **Key issues:** #221 (Holograms sticking to camera), #228 (Calibration instability)
- **Repo URL:** https://github.com/microsoft/MixedRealityCompanionKit

### 5. immersive-web/webxr (3.1k ⭐)
- **The WebXR Device API specification.** The defining standard for immersive web experiences.
- **Key issues #390:** Sound source nodes — proposed by W3C member @cwilso in 2018. Open, 30 comments. The core question: should WebXR provide HRTF-based spatial audio?
- **Key issue #892:** Audio-only devices — how should WebXR interact with non-visual XR devices?
- **Key issue #815:** Spec language precludes non-visual uses — accessibility tracker concern.
- **Key issue #1420:** Dynamic foveation — proposed by @AdaRoseCannon. Can the renderer reduce peripheral resolution to cheat the brain?
- **Key issue #1396:** Actual vs. internal visibility — fundamental MR rendering question.
- **Key issue #1414:** HTML-in-canvas integration — DOM overlay in XR.
- **Repo URL:** https://github.com/immersive-web/webxr

---

## Hottest GitHub Issues Found

### 🔥 Perceptual Latency

| Issue | Repo | Reactions | Comments | Key Insight |
|-------|------|-----------|----------|-------------|
| [#816](https://github.com/microsoft/Azure-Kinect-Sensor-SDK/issues/816) | Azure-Kinect-Sensor-SDK | 8 👍 | 47 | 0.2s camera latency vs. 0.02s Rift S and 0.006s RealSense. The modern standard is far higher than current MR hardware. |
| [#1099](https://github.com/WiVRn/WiVRn/issues/1099) | WiVRn | 15+ | 40+ | After Quest 3 passthrough reacquisition, VRChat freezes for 47 minutes. Frame scheduling bug, not global stall. Brain may detect *pacing irregularity*, not absolute latency. |
| [#334](https://github.com/polygraphene/ALVR/issues/334) | ALVR | — | — | ~33.6ms of unaccounted latency. VR stacks underreport total system latency by 30-50%. Industry optimizing against phantom numbers. |
| [#1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | arcore-android-sdk | — | — | 13-35ms camera↔IMU clock offset on mid-range Android. Invisible to developers, catastrophic for perceptual stability. |

### 🔥 Spatial Audio

| Issue | Repo | Reactions | Comments | Key Insight |
|-------|------|-----------|----------|-------------|
| [#390](https://github.com/immersive-web/webxr/issues/390) | webxr | 1 👍 | 30 | @cwilso (W3C member): Should WebXR hook up sound source nodes with HRTF? Problem: keeping headpose updated at audio-thread frequency. |
| [#2561](https://github.com/KhronosGroup/glTF/issues/2561) | glTF | 1 👍 | 2 | @rudybear: Layered audio extension architecture — KHR_audio_emitter + KHR_audio_graph + KHR_audio_environment. Full reference implementation in TypeScript. |
| [#1113](https://github.com/kcat/openal-soft/issues/1113) | openal-soft | 1 👍 | 6 | @ThreeDeeJay: Convincing proximity simulation remains unsolved. NFC degrades HRTF; multi-field SOFA improves it but requires specialized HRTFs. 3DTI sets gold standard. |
| [#3816](https://github.com/wwmm/easyeffects/issues/3816) | easyeffects | 3 👍 | 10 | @alankila: Localization Cue Correction — crossfeed reduction plugin that expands stereo image from forward angles to 180° arc. Filter curves still tuned by ear. |
| [#2](https://github.com/GoogleChrome/omnitone/issues/2) | omnitone | — | 23 | Mobile browser support still unresolved after 8+ years. Binaural rendering remains desktop-only. The WebXR spatial audio gap is real. |

### 🔥 Mixed Reality Interfaces

| Issue | Repo | Reactions | Comments | Key Insight |
|-------|------|-----------|----------|-------------|
| [#221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) | MixedRealityCompanionKit | — | 18 | Holograms sticking to camera — fundamental registration failure in optical passthrough. |
| [#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | MixedRealityCompanionKit | — | 19 | Calibration that works once and never twice. Blocks research reproducibility. |
| [#1420](https://github.com/immersive-web/webxr/issues/1420) | webxr | — | 3 | @AdaRoseCannon: Dynamic foveation — can the renderer cheat the brain by reducing peripheral resolution? |
| [#1396](https://github.com/immersive-web/webxr/issues/1396) | webxr | — | — | Actual vs. internal visibility confusion — fundamental MR rendering question. |

### 🔥 Web AR Architecture

| Issue | Repo | Reactions | Comments | Key Insight |
|-------|------|-----------|----------|-------------|
| [#681](https://github.com/AR-js-org/AR.js/issues/681) | AR.js | 4 (3 🚀) | 3 | @kalwalt (org member): AR.js-next introduces ECS architecture for modularity, flexibility, maintainability. Retrocompatibility with parameters but not legacy class APIs. Plugin system for Three.js and ARToolKit. |

---

## Newly Identified Contributors

### Perceptual Latency Experts

| Name | GitHub | Repo | Why They Matter for the Podcast |
|------|--------|------|--------------------------------|
| @xytovl | xytovl | WiVRn maintainer | OpenXR streaming; packet-timing & pacing algorithm design; stutter analysis. Direct experience with the WiVRn #1099 frame scheduling crisis. |
| @leinardi | leinardi | SteamVR-for-Linux | Open-source VR latency debugging; first-hand motion-to-photon pipeline experience. |
| @jd-3d | jd-3d | ALVR developer | VR streaming stack forensics; discovered the "missing latency" in ALVR #334. |
| @fieldsJacksonG | fieldsJacksonG | Microsoft MRC | Hologram registration & calibration; MixedRealityCompanionKit maintainer. |
| @emaschino | emaschino | Microsoft MRC | HoloLens 2 performance; mixed-reality compositor calibration. |
| @fredemmott | fredemmott | Microsoft XR Advocate | HoloLens platform strategy; MR advocacy & developer ecosystem. |
| @jaygullapalli | jaygullapalli | Azure Kinect SDK lead | Sensor latency engineering; assigned to Azure Kinect #816. |
| @maluoi | maluoi | StereoKit maintainer | XR engine architecture; OpenXR backend; performance optimization. |

### Spatial Audio Experts

| Name | GitHub | Repo | Why They Matter for the Podcast |
|------|--------|------|--------------------------------|
| @leomccormack | leomccormack | Spatial_Audio_Framework | Creator of SAF. Ambisonics, HRTFs & temporal rendering in C. Cross-platform spatial audio. |
| @crlandsc | crlandsc | SAF contributor | Spatialization algorithms; real-time rendering. |
| @ali-vosoughi | ali-vosoughi | SAF contributor | Ambisonic processing & signal flow. |
| @jacobhollebon | jacobhollebon | SAF contributor | Spatial audio architecture & design. |
| @BinWang28 | BinWang28 | audio-ai-hub | HRTF research; spatial speech perception; personalized HRTFs. |
| @edurnebernal | edurnebernal | Audio-visual perception | Audio-visual integration in VR; ventriloquism effect research. |
| @TheBarmaEffect | TheBarmaEffect | Spatial audio engine | Perception-first spatial audio engine design. |
| @orighst (Boris Smus) | orighst | omnitone / Google | Browser-based binaural rendering; FOA/HOA. |
| @brandonpjones | brandonpjones | omnitone / Google | Web Audio API spatial rendering; ambisonic codecs. |
| @jkarmer (Julius Kammerl) | jkarmer | omnitone / Google | Real-time spatial audio in web browsers. |
| @timfain | timfain | Jaunt VR | Spatial content creation & rendering pipelines. |
| @freeman-jiang | freeman-jiang | beatsync | Multi-device spatial audio synchronization; clock sync precision. |
| @ameliaeckard | ameliaeckard | Apple Vision Pro | Accessibility via spatial audio; indoor navigation for visually impaired. |
| @cwilso | cwilso | W3C Immersive Web | WebXR audio design; authored sound source node proposal (#390). |
| @toji | toji | W3C Immersive Web | WebXR spec editor; accessibility & non-visual uses (#892, #815). |
| @rudybear | rudybear | glTF audio extension | KHR_audio layered architecture; TypeScript reference implementation. |
| @alankila | alankila | EasyEffects | Localization Cue Correction DSP; crossfeed research. |
| @ThreeDeeJay | ThreeDeeJay | OpenAL Soft | HRTF proximity; near-field control research. |
| @kcat | kcat | OpenAL Soft | Open-source spatial audio; HRTF database. |

### MR Interface / Web AR Experts

| Name | GitHub | Repo | Why They Matter for the Podcast |
|------|--------|------|--------------------------------|
| @jeromeetienne | jeromeetienne | AR.js creator (15.8k ⭐) | Web AR pioneer; marker-based & geospatial AR; the AR.js 2→3 transition. |
| @hiukim | hiukim | MindAR creator (2.7k ⭐) | On-device image/face tracking with TF.js; production-ready MR. |
| @kalwalt | kalwalt | AR.js org / AR.js-next lead | ECS architecture; plugin system; retrocompatibility design. |
| @cabanier | cabanier | W3C Immersive Web | WebXR DOM overlays & visibility specification. |
| @AdaRoseCannon | AdaRoseCannon | W3C Immersive Web | Dynamic foveation & accessibility; authored #1420. |
| @chrisdavidmills | chrisdavidmills | WebXR editor | Visibility-mask events; WebXR spec evolution. |
| @danrossi | danrossi | WebXR layers work | Projection-layer rendering; layer composition. |
| @himorin | himorin | WebXR contributor | Security/privacy of spatial mapping; permission models. |
| @bradleylab | bradleylab | XR Geoxplorer | Hand tracking + XRI 3.x interaction wiring; MR interaction design. |
| @yacuzo | yacuzo | MixedReality-WebRTC | Spatial mesh streaming; data channel throughput (#130). |

---

## Cross-Repo Thematic Connections

### 1. The "Invisible Pipeline" Problem
Every repo in this survey deals with latency that users never notice — until it's there. Azure Kinect #816 (0.2s vs 0.006s), WiVRn #1099 (47-minute freeze), ALVR #334 (33.6ms missing). The best perceptual systems are the ones you never feel.

### 2. The WebXR Visual Primacy Gap
WebXR #390 (sound source nodes, open since 2018), #892 (audio-only devices), #815 (non-visual uses precluded), #1420 (dynamic foveation). The spec was designed for visual rendering. Spatial audio, non-visual accessibility, and perceptual calibration are afterthoughts. This gap is the show's through-line.

### 3. The Open-Source Audio Dead End
google/lullaby accepted no external contributions. omnitone has been desktop-only for 8+ years. MixedReality-WebRTC is deprecated. The open-source spatial audio ecosystem has a series of "dead end" problems — projects that start with promise but stall before solving the hard problems.

### 4. The Modular vs. Monolithic Debate (AR.js ECS)
AR.js #681: The move from monolithic classes to ECS architecture is not just a code refactor — it's a perceptual design decision. A monolithic engine can optimize end-to-end latency (sensor-to-display in one pass). An ECS introduces message-passing overhead that may push latency above perceptual thresholds. The AR.js-next decision will shape how millions of Web AR experiences handle perception.

### 5. Calibration as a Perceptual Problem
MixedRealityCompanionKit #228 (calibration that works once, never twice) and #221 (holograms sticking to camera) are not just bugs — they're perceptual failures. When calibration drifts, the brain's spatial model breaks. The brain expects digital content to stay where you placed it. Calibration instability is a perception problem, not a rendering problem.

---

## Research Action Items

- [ ] Reach out to @xytovl for Episode 1 — WiVRn maintainer perspective on frame pacing
- [ ] Contact @cwilso for Episode 2 — W3C member who proposed WebXR sound source nodes
- [ ] Interview @kalwalt for Episode 3 — AR.js-next ECS architecture decision rationale
- [ ] Connect @leomccormack for Episode 2 — SAF creator on HRTF personalization gap
- [ ] Reach out to @AdaRoseCannon for Episode 3 — dynamic foveation perception research
- [ ] Contact @alankila for Episode 2 — Localization Cue Correction DSP experiment
- [ ] Interview @rudybear for Episode 2 — glTF layered audio architecture proposal
- [ ] Investigate @ThreeDeeJay's proximity simulation findings for Episode 2
- [ ] Connect @jeromeetienne for Episode 3 — AR.js 2→3 transition and Web AR tracking reliability
- [ ] Review @fieldsJacksonG's calibration work for Episodes 1 & 3

---

*Research compiled September 18, 2026 from GitHub issue analysis across 10+ active AR/MR/Spatial Computing repositories.*