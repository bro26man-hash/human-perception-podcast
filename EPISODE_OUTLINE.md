# 🎙️ The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **canonical episode outline** for the series.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos |
|---|---|
| Web 3D / WebXR | `mrdoob/three.js` (115.6k ⭐), `playcanvas/engine` (16.7k ⭐), `immersive-web/webxr` (3.1k ⭐) |
| Web AR | `jeromeetienne/AR.js` / `AR-js-org/AR.js` (15.8k ⭐), `hiukim/mind-ar-js` (2.7k ⭐), `jeeliz/jeelizFaceFilter` (2.9k ⭐) |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity` (6.1k ⭐), `MixedRealityToolkit/MixedRealityToolkit-Unity` (550 ⭐), `microsoft/MixedRealityCompanionKit` (594 ⭐), `microsoft/MixedReality-WebRTC` (944 ⭐) |
| Spatial Computing | `StereoKit/StereoKit` (1.1k ⭐), `KhronosGroup/OpenXR-SDK` (1.1k ⭐), `IvanCampos/visionOS-examples` (405 ⭐), `MIT-SPARK/Kimera-VIO` (1.9k ⭐) |
| Spatial Audio | `GoogleChrome/omnitone` (911 ⭐), `leomccormack/Spatial_Audio_Framework` (748 ⭐), `google/spatial-media` (2.1k ⭐), `resonance-audio/resonance-audio-web-sdk` |
| AI Perception | `vladmandic/human` (3.3k ⭐) — face/body/hand/gesture tracking |
| VR Streaming | `WiVRn/WiVRn` (1.6k ⭐), `polygraphene/ALVR` |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Key Topics

1. **The motion-to-photon pipeline** — sensor → predict → render → encode → transport → decode → display. Every stage injects latency; the sum is what the brain judges.
2. **The "20 ms rule" and vestibular-visual conflict** — why a few milliseconds of lag translate directly into motion sickness. The brain's vestibular system expects sensory congruence; lag breaks it.
3. **Temporal irregularity vs. average latency** — WiVRn #282 (40 comments): maintainer `xytovl` traced stutter to >10 ms of reception-time variability, not raw pipeline depth. Is the brain detecting frame irregularity rather than average ms? This reframes the entire optimization target.
4. **"Missing" latency in VR streaming** — ALVR #334: ~33.6 ms of unaccounted latency; VR stacks underreport total system latency by 30–50%. The industry may be optimizing against a phantom number.
5. **Web AR tracking failure on mobile** — AR.js #826 (broken image tracking), AR.js #825 (location-based AR failing), AR.js #815 (3D model "stuck above" origin — a latency symptom between tracking update and display refresh), AR.js #818 (iOS device orientation drift — sensor lag causing misaligned AR content).
6. **Hologram calibration instability** — MixedRealityCompanionKit #228: SpectatorView calibration that works once and never twice (19 comments). Blocks research reproducibility.
7. **Direct3D 12 & frame-timestamp precision** — HoloLens 2 performance and viewfinder reliability (OpenXR-MixedReality #131, #132).
8. **VIO pipeline timing** — Kimera-VIO frontend at ~60Hz, backend at ~20Hz; queue depths reveal where perceptual lag hides in SLAM pipelines.

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets (reduce average ms) are wrong — we need to stabilize frame delivery instead. This reframes the entire 20 ms discussion.

### Potential Guest Contributors

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leinardi** | SteamVR-for-Linux maintainer | Open-source VR motion-to-photon latency debugging |
| **xytovl** | WiVRn maintainer | Packet-timing & pacing algorithm design; traced stutter to temporal irregularity |
| **jd-3d** | ALVR developer & latency researcher | "Missing latency" in VR streaming stacks |
| **jeromeetienne** | AR.js creator | Web AR latency constraints — can't control the hardware |
| **nicolocarpignoli** | AR.js maintainer | Sees every tracking bug report from the community |
| **antoni rosinol** | Kimera-VIO lead author | VIO/SLAM timing, frontend/backend pipeline gaps |
| **luca carlone** | Kimera team / MIT | Real-time state estimation, factor graphs |
| **vlad mandić** | Human library creator | Face/body/hand tracking latency, WebGPU/WebGL pipelines |
| **brycehutchings** | Microsoft OpenXR contributor | MR performance, Direct3D 12 path |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How do spatial-audio algorithms trick the brain into hearing sound in 3D space — and why does a one-size-fits-all HRTF still fall short of "real"?

### Key Topics

1. **Head-Related Transfer Functions (HRTFs)** and the personalization challenge
2. **VBAP** and higher-order ambisonics (HOA)
3. **Real-time binaural/ambisonic rendering on the web** — GoogleChrome/omnitone (FOA/HOA renderers, Web Audio API)
4. **HRTF augmentation effects on spatial release from masking**
5. **Audio–visual integration** in VR: vision dominates when cues conflict
6. **Room-acoustics modeling** (ISM reverberation) and perceptual quality
7. **Accessibility:** spatial audio as a navigation cue for visually impaired users
8. **Mobile browser spatial audio is broken** — Omnitone #2: 23 comments, the longest-running debate. Mobile browsers can't decode multichannel audio properly. This is the #1 blocker for web spatial audio.
9. **Ambisonics → video export pipeline is fragile** — Omnitone #84: FOA→HOA conversion produces unplayable video output. Spatial audio rendering → delivery pipeline has fundamental codec/container issues.
10. **Three.js + spatial audio are siloed** — Omnitone #90: no unified scene graph integrating audio sources with 3D rendering. Spatial audio and 3D graphics live in separate worlds.
11. **The project seems stalled** — Omnitone #109: contributors ask "is this project still alive?" — spatial audio on the web has lost momentum.
12. **MR audio-visual integration gaps** — MixedReality-WebRTC brings audio/video to MR apps, but spatial audio positioning is an afterthought in MRTK.

### The Hot Debate

> **The WebXR spec is visual-only for spatial audio.** While the spec defines immersive-session rendering for visuals, spatial audio rendering is left to implementation-specific extensions. Omnitone proved it's technically possible on the web — but mobile browser codec limitations, lack of HRTF personalization APIs, and the absence of an AudioNode-based spatial rendering graph in WebXR make it a research project, not a shipping feature. The result: the most important sense for presence in MR is the one the web platform ignores.

### Potential Guest Contributors

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leomccormack** | Spatial_Audio_Framework creator | Ambisonics, HRTFs & temporal rendering |
| **crlandsc / ali-vosoughi / jacobhollebon** | Spatial_Audio_Framework contributors | Spatialization algorithms |
| **BinWang28** | audio-ai-hub | HRTF research & spatial speech perception |
| **edurnebernal** | — | Audio-visual spatial perception in VR |
| **TheBarmaEffect** | — | Perception-first spatial audio engine |
| **Boris Smus** | Omnitone / Google audio team | Web binaural rendering, FOA/HOA codec design |
| **hoch** | Omnitone maintainer | 7+ years of spatial audio pain points on the web |
| **Tim Fain** | Jaunt VR | Spatial content & rendering for VR music |
| **Dillon Cower** | Former Google spatial audio | Resonance Audio SDK, bridging ambisonics and web |
| **luca carlone** | Kimera team | 3D spatial perception — can bridge visual and auditory mapping |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** In mixed reality, holograms drift, stick to the camera, and fail to stay where you placed them. What are the fundamental limits of registering digital content to the physical world — and how close are we to solving them?

### Key Topics

1. **Hologram registration errors:** "holograms sticking to camera," reprojection drift across network stacks
2. **Optical passthrough quality:** the resolution/contrast race (visionOS, Quest 3, XREAL)
3. **Plane detection & spatial mapping** limitations in dynamic environments
4. **WebXR layers & projection-layer scaling** — cut-off and visual artifacts, and DOM overlays in canvas
5. **Dynamic foveation** and visibility masking as perceptual/performance levers
6. **The attention economy:** how persistent holographic UIs compete for — and hijack — focus
7. **Markerless city-scale AR is still unsolved** — AR.js #833: "How to create AR visible across an entire city?" The holy grail of spatial computing, still a research question on the web. GPS + IMU + visual fusion can't yet achieve persistent, cm-accurate world-locked content at city scale.
8. **Holographic remoting is fragile** — MRTK #11845: Unity + Chinese keyword recognition + holographic remoting = crash. MR interaction stacks break in unpredictable ways when you push them past their design envelopes.
9. **Hand tracking reliability gaps** — human #530: WASM backend initialization failures affect hand/finger tracking. The core MR interaction modality (hand tracking) has backend stability issues that break the illusion of natural interaction.
10. **VIO-driven 3D mesh generation** — Kimera-VIO generates 3D meshes from VIO pipelines, bridging the gap between "where am I?" and "what's around me?" — the foundation of true spatial computing.
11. **MRTK Spatial Awareness** creates mesh representations of the environment, but the perceptual fidelity is questionable — how "real" does a spatial mesh need to be for the brain to accept it?

### The Hot Debate

> **Is the WebXR spec perception-blind?** The spec optimizes for visual output (layers, projection, visibility) but gives auditory and haptic channels short shrift. AR.js proves you can build marker-based AR that works on any phone — but city-scale markerless AR (#833) remains unsolved because the web platform doesn't expose the sensor fusion, SLAM, or spatial mapping APIs that native MR stacks (MRTK, ARKit, ARCore) take for granted. We're building interfaces on a platform that doesn't fully understand what "spatial" means.

### Potential Guest Contributors

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **jeromeetienne** | AR.js creator | City-scale AR ambition vs. web constraints |
| **maluoi** | StereoKit maintainer | XR engine & OpenXR backend — raw interface performance |
| **cabanier** | W3C Immersive Web | WebXR DOM overlays & visibility |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation & accessibility |
| **himorin** | WebXR contributor | Security/privacy of spatial mapping |
| **chrisdavidmills** | WebXR editor | Visibility-mask events |
| **danrossi** | WebXR layers work | Projection-layer rendering |
| **aphillia** | WebXR input profiles | i18n for XR |
| **vlad mandić** | Human library creator | Hand/face/gesture tracking — the interfaces of tomorrow |
| **antoni rosinol** | Kimera-VIO author | Metric-semantic mapping, 3D dynamic scene graphs |
| **microsoft MRTK team** | Mixed Reality Toolkit | Building the abstractions between hardware and perception |

---

## Cross-Episode Themes

| Theme | Episodes | Debate |
|---|---|---|
| **The 20ms Rule & Beyond** | 1, 3 | Is perceptual latency a hard limit or a soft target? Does it differ across senses (visual vs. auditory vs. vestibular)? |
| **Web vs. Native** | 1, 2, 3 | Web AR (AR.js) vs. native MR (MRTK/ARKit/ARCore) — what do we lose in the abstraction layer? Can the web ever catch up? |
| **Multimodal Perception** | 1, 2, 3 | Latency isn't just visual — audio presence, haptic feedback, and vestibular sense all have different thresholds and failure modes |
| **Open Source vs. Industry** | 1, 2, 3 | Open-source repos (AR.js, Omnitone, Kimera-VIO) track real pain points; industry tools (MRTK, Resonance Audio) paper over them with closed binaries |
| **The "Presence" Gap** | 1, 2, 3 | We can track body, render visuals, and play spatial audio — but why doesn't it *feel* real yet? What's missing beyond technology? |

---

## GitHub Issue Watchlist

These are the hottest issue threads to monitor for new episode material:

| Repo | Issue | Topic | Comments |
|---|---|---|---|
| WiVRn/WiVRn | #282 | Temporal irregularity & stutter | 40+ |
| polygraphene/ALVR | #334 | "Missing" latency in VR streaming | 30+ |
| googlechrome/omnitone | #2 | Mobile browser spatial audio support | 23 |
| microsoft/MixedRealityCompanionKit | #228 | Hologram calibration instability | 19 |
| microsoft/MixedRealityCompanionKit | #221 | Holograms sticking to camera | 18 |
| googlechrome/omnitone | #84 | Ambisonics→video export broken | 12 |
| jeromeetienne/AR.js | #833 | City-scale markerless AR | 1 |
| vladmandic/human | #530 | WASM backend init failure (hand tracking) | 0 |
| microsoft/MixedRealityToolkit-Unity | #11845 | Holographic remoting crash | 0 |
| immersive-web/webxr | #1420 | Dynamic foveation | — |

## Resources

- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [MRTK Documentation](https://aka.ms/mrtkdocs)
- [AR.js (new org)](https://github.com/AR-js-org/AR.js)
- [Omnitone Spatial Audio](https://googlechrome.github.io/omnitone/)
- [Kimera-VIO Papers](https://arxiv.org/abs/1910.02490)
- [W3C Immersive Web Working Group](https://www.w3.org/immersive-web/)
- [Spatial Media Specification](https://github.com/google/spatial-media)