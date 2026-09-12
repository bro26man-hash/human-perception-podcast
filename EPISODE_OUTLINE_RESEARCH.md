# The Future of Human Perception — Episode Outline (Research-Enriched)

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **canonical episode outline** for the series, enriched with live GitHub issue analysis (September 2026).
> Companion research lives in `COMMUNITY-RESEARCH.md` and `RESEARCH-DATABASE.md`.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two speakers? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR repos and the researchers pushing them forward.

**Research backbone** (most active GitHub communities surveyed):
`microsoft/MixedRealityToolkit-Unity` (6,076⭐, MRTK v2/v3 for HoloLens & MR)
`ultralytics/ultralytics` (61,534⭐, YOLO pose & hand-tracking)
`GoogleChrome/omnitone` (web spatial audio)
`KhronosGroup/OpenXR-SDK` (cross-platform XR API)
`immersive-web/webxr` (W3C standard)
`leomccormack/Spatial_Audio_Framework` (C spatial audio)
`freeman-jiang/beatsync` (multi-device spatial audio)
`jeromeetienne/AR.js` (15,789⭐ web-AR)
`hiukim/mind-ar-js` (on-device AR)
`Microsoft/MixedRealityCompanionKit` (MR calibration)
`Microsoft/OpenXR-MixedReality` (HoloLens performance)
`IvanCampos/visionOS-examples` (Apple Vision Pro spatial UI)
`Mach1Studios/m1-spatialaudioserver` (binaural rendering)
`WiVRn/WiVRn` (OpenXR streaming latency)
`StereoKit/StereoKit` (XR engine)

---

## Episode 1: "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver, even when raw pipeline numbers look good.

### 🔬 Key Topics
1. **Motion-to-photon pipeline deep-dive:** sensor → predict → render → encode → transport → decode → display — where do the milliseconds actually vanish?
2. **The "20 ms rule" and vestibular-visual conflict:** why a few milliseconds of lag translate directly into motion sickness and presence collapse
3. **Temporal irregularity vs. average latency:** the WiVRn community debate (issues #282, #234) — users report visible stutter when reception-time variability exceeds ~10 ms, even when mean latency is acceptable. The brain detects jitter, not just delay.
4. **"Missing" system latency in VR streaming stacks:** ALVR #334 finding that stock Qt-based profilers underreport total system latency by 30–50% — what does this mean for optimization priorities?
5. **HoloLens 2 performance & frame-timestamp precision:** Microsoft/OpenXR-MixedReality #131, #132 — Direct3D 11 vs. D3D12, viewfinder reliability, and the cost of mixed-reality passthrough compositing
6. **Spatial computing on Apple Vision Pro:** imclab/Apple-Vision-PRO-AR-VR-XR-AI — SE(3) anchor stability, foveated rendering overhead, and the perceptual cost of compositor stalls (WiVRn #741 passthrough lockup)
7. **Pose estimation & hand-tracking latency:** ultralytics/ultralytics #1915 (YOLOv8 Pose Models, 106 comments): real-time keypoint inference on-device vs. cloud, and the perceptual difference between a 2 ms detection lag and a 20 ms one
8. **Calibration instability in MR:** MixedRealityCompanionKit #228 — SpectatorView calibration that works once and never twice; what does calibration drift do to presence?

### 🎤 Guest Candidates
- **leinardi** — SteamVR-for-Linux maintainer; on-the-ground motion-to-photon latency debugging
- **jd-3d** — ALVR developer; first-hand investigation into "missing" latency in VR streaming stacks
- **xytovl** — WiVRn maintainer; OpenXR streaming, latency pacing & packet-timing forensics
- **AaronMillward** — WiVRn contributor; field reports of perceptual stutter & motion sickness
- **brycehutchings** — Microsoft OpenXR contributor; MR performance & the D3D12 path
- **emaschino** — Microsoft MRC; HoloLens 2 performance & viewfinder reliability
- **fredemmott** — Microsoft XR Advocate; HoloLens platform & mixed-reality advocacy
- **fieldsJacksonG** — Microsoft MRC; hologram registration & calibration issues
- **Maluoi** — StereoKit maintainer; XR engine performance & OpenXR backend

### 📚 Key GitHub Issues to Reference
- [WiVRn #282 — Stuttering Headset/Controller Position](https://github.com/WiVRn/WiVRn/issues/282) (40 comments)
- [WiVRn #234 — Unstable feeling controller tracking](https://github.com/WiVRn/WiVRn/issues/234) (20 comments)
- [ALVR #334 — Latency measurement methodology](https://github.com/polygraphene/ALVR/issues/334)
- [Ultralytics #1915 — YOLOv8 Pose Models](https://github.com/ultralytics/ultralytics/issues/1915) (106 comments)
- [MixedRealityCompanionKit #228 — Calibration instability](https://github.com/microsoft/MixedRealityCompanionKit/issues/228)

---

## Episode 2: "Spatial Sound and the Third Dimension"

**Focus:** How spatial-audio algorithms trick the brain into hearing sound in 3D space — and why a one-size-fits-all HRTF still isn't good enough for convincing virtual presence.

### 🔬 Key Topics
1. **HRTF personalization problem:** generic HRTFs work for ~30% of listeners; what does the remaining 70% experience? Discussion from Spatial_Audio_Framework and audio-ai-hub research
2. **Vector Base Amplitude Panning (VBAP) and Higher-Order Ambisonics (HOA):** the trade-off between computational cost and spatial accuracy; Ambisonics as a "universal" spatial encoding
3. **Real-time binaural rendering on the web:** Google Chrome's omnitone project: FOA/HOA renderers via Web Audio API, and the perceptual challenge of rendering spatial audio inside a browser
4. **Multi-device spatial audio synchronization:** freeman-jiang/beatsync (3,158⭐): how precise do clock sync need to be before the brain fuses two channels into one image, and what happens when they drift?
5. **Audio-visual integration in VR:** vision dominates when cues conflict (the ventriloquism effect and its XR implications) — does bad spatial audio poison the visual experience?
6. **Room acoustics modeling (ISM reverberation):** how simulated room tone and early reflections shape the "presence" of a virtual space; omnitone room modeling
7. **Spatial audio for accessibility:** using spatial audio to help visually impaired users identify and navigate to indoor objects — research from ameliaeckard/spatial-audio-research-arvr and Apple Vision Pro spatial audio experiments
8. **Machine-learning HRTF interpolation:** emerging work on neural HRTF prediction from ear photos — how close are we to personalized spatial audio at scale?
9. **Binaural rendering performance:** Mach1Studios/m1-spatialaudioserver — real-time binaural rendering on resource-constrained devices

### 🎤 Guest Candidates
- **leomccormack** — creator of Spatial_Audio_Framework; ambisonics, HRTFs & temporal rendering
- **crlandsc, ali-vosoughi, jacobhollebon** — Spatial_Audio_Framework contributors (spatialization algorithms)
- **BinWang28** — audio-ai-hub; HRTF research & spatial speech perception
- **edurnebernal** — audio-visual spatial perception in VR
- **TheBarmaEffect** — perception-first spatial audio engine design
- **Boris Smus / Brandon Jones** — omnitone / Google spatial audio team
- **Tim Fain** — Jaunt VR; spatial content & rendering
- **freeman-jiang** — beatsync creator; multi-device spatial synchronization
- **Amelia Eckard** — spatial audio accessibility research (Apple Vision Pro)
- **Avnerus** — Mach1 Studios; binaural rendering server architecture

### 📚 Key GitHub Issues to Reference
- [ASH-Toolset #22 — Microsoft Spatial Sound API request](https://github.com/ShanonPearce/ASH-Toolset/issues/22) (20 comments)
- [Spatial_Audio_Framework — repo](https://github.com/leomccormack/Spatial_Audio_Framework)
- [GoogleChrome/omnitone — Web Spatial Audio](https://github.com/GoogleChrome/omnitone)
- [Mach1Studios/m1-spatialaudioserver — binaural rendering](https://github.com/Mach1Studios/m1-spatialaudioserver)
- [beatsync — multi-device spatial audio](https://github.com/freeman-jiang/beatsync)

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**Focus:** The design of mixed-reality interfaces — optical passthrough quality, boundary systems, hologram registration, hand/eye/gaze interaction, and how MR interfaces compete for our attention in ways 2D screens never could.

### 🔬 Key Topics
1. **Hologram registration & drift:** MixedRealityCompanionKit #221: "holograms sticking to camera," reprojection drift across network stacks (18 comments); what does persistent misalignment do to the sense of presence?
2. **Optical passthrough quality and the resolution/contrast race:** Apple Vision Pro (μLED, 23M pixels), Meta Quest 3 (color passthrough), XREAL — where is the perceptual threshold for "transparent digital"?
3. **Plane detection & spatial mapping limitations in dynamic environments:** how does the system handle moving people, sliding furniture, rain on windows? Vision OS examples and AR.js markerless challenges
4. **WebXR layers & projection-layer scaling:** cut-off artifacts and visual glitches (webxr-samples #228, #231, #235) and DOM overlays in canvas (webxr #1414): the perceptual cost of imperfect compositing layers
5. **Dynamic foveation and visibility masking:** can we hide rendering cost where the user isn't looking, and does the brain notice? (webxr #1420, #1396)
6. **The attention economy of persistent holographic UIs:** how do persistent digital objects in physical space hijack focus differently than phone notifications? What are the ethical design implications?
7. **Hand tracking keypoint accuracy for interface interaction:** Ultralytics #1915 pose estimation, #1429 multi-object tracking — how accurate does hand keypoint detection need to be for reliable pinch/select gestures in mid-air?
8. **Voice + gaze + gesture multimodal interaction:** MRTK's input system (eye tracking, hand tracking, voice, articulated hand support) — designing for the "no controller" paradigm
9. **Spatial anchors & persistence:** Azure Spatial Anchors: how does persistent digital content in the real world change our relationship with spaces?

### 🎤 Guest Candidates
- **jeromeetienne** — creator, AR.js (15,789⭐); web AR godfather; marker-based & geospatial AR
- **hiukim** — creator, MindAR (2,725⭐); on-device image/face tracking with TensorFlow.js
- **maluoi** — StereoKit maintainer; XR engine & OpenXR backend architecture
- **cabanier** — W3C Immersive Web Working Group; WebXR DOM overlays & visibility
- **AdaRoseCannon** — W3C Immersive Web; dynamic foveation & accessibility
- **himorin** — WebXR contributor; security/privacy of spatial mapping data
- **chrisdavidmills** — WebXR visibility-mask events & rendering layers
- **danrossi** — WebXR layers & projection-layer compositor work
- **aphillia** — XR input profiles & internationalization for spatial interaction
- **Ivan Campos** — visionOS-examples (405⭐); Apple Vision Pro spatial UI patterns
- **dongyoonpark** — Microsoft MRDL; Periodic Table of the Elements (HoloLens 2)
- **richardinerickson** — Microsoft MRDL; Surfaces MR tactile experience

### 📚 Key GitHub Issues to Reference
- [MixedRealityCompanionKit #221 — Hologram registration drift](https://github.com/microsoft/MixedRealityCompanionKit/issues/221)
- [webxr-samples #228 — Layers & projection-layer artifacts](https://github.com/immersive-web/webxr-samples/issues/228)
- [webxr #1414 — DOM overlays in canvas](https://github.com/immersive-web/webxr/issues/1414)
- [webxr #1420 — Dynamic foveation](https://github.com/immersive-web/webxr/issues/1420)
- [mind-ar-js #556 — Unstable AR Content & Tracking](https://github.com/hiukim/mind-ar-js/issues/556) (5 comments)
- [AR.js #833 — Markerless AR across a city](https://github.com/jeromeetienne/AR.js/issues/833)

---

## The Hot Debate Table

| Debate | Where It's Live (GitHub) | Why It Matters for Perception |
|--------|--------------------------|-------------------------------|
| Temporal jitter vs. average latency | WiVRn #282, #234 | Brain detects frame irregularity, not just delay — redefines optimization targets |
| "Missing" system latency in streaming | ALVR #334 | Stock profilers underreport by 30-50%; optimization may be chasing ghosts |
| MR calibration fragility | MixedRealityCompanionKit #228 | Blocks reproducibility; drift destroys presence |
| HRTF personalization vs. generic | Spatial_Audio_Framework, audio-ai-hub | 70% of listeners get poor spatial audio — realism ceiling |
| Hologram drift / "stick to camera" | MixedRealityCompanionKit #221 | Core MR presence problem — broken anchoring = broken immersion |
| WebXR layers & passthrough artifacts | webxr-samples #228-235 | Visual comfort vs. fidelity trade-off |
| Visibility masking & foveation | webxr #1420, #1396 | Can we hide perf cost from perception? |
| Hand tracking keypoint accuracy | Ultralytics #1915, #1429 | Mid-air gesture reliability for MR interfaces |
| Multi-device audio sync precision | beatsync | Clock sync threshold for spatial fusion |

---

## Contributor Quick-Reference

| Name | Domain | Key Repo / Role |
|------|--------|-----------------|
| leinardi | VR latency | SteamVR-for-Linux maintainer |
| jd-3d | VR streaming | ALVR developer |
| xytovl | OpenXR streaming | WiVRn maintainer |
| AaronMillward | VR latency | WiVRn contributor |
| brycehutchings | MR performance | Microsoft OpenXR contributor |
| emaschino | HoloLens perf | Microsoft MRC |
| fredemmott | XR advocacy | Microsoft XR Advocate |
| leomccormack | Spatial audio | Spatial_Audio_Framework creator |
| Boris Smus | Web audio | omnitone / Google |
| jeromeetienne | Web AR | AR.js creator (15.8k⭐) |
| hiukim | On-device AR | MindAR creator (2.7k⭐) |
| maluoi | XR engines | StereoKit maintainer |
| Ivan Campos | visionOS | visionOS-examples (405⭐) |
| AdaRoseCannon | WebXR standards | W3C Immersive Web |
| Amelia Eckard | Audio accessibility | Vision Pro spatial audio research |
| dongyoonpark | MR UI design | Microsoft MRDL |
| richardinerickson | MR tactile | Microsoft MRDL |

---

*Last updated with research from GitHub issue analysis, repo commits, and community contributor mapping — September 2026.*
