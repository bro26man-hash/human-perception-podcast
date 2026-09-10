# The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **canonical episode outline** for the series. Companion research lives in `RESEARCH-DATABASE.md`.

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two speakers? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR repos and the researchers pushing them forward.

**Research backbone** (most active GitHub communities surveyed): `mrdoob/three.js`, `immersive-web/webxr` (+ `webxr-samples`, `proposals`, `depth-sensing`, `layers`, `anchors`, `real-world-geometry`), `GoogleChrome/omnitone`, `google-ar/arcore-android-sdk`, `KhronosGroup/OpenXR-SDK`, `StereoKit/StereoKit`, `Microsoft/MixedRealityToolkit`, and the W3C Immersive Web Working Group.

---

## Episode 1: "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

**Key Topics**
- Motion-to-photon pipeline: sensor → predict → render → encode → transport → decode → display
- The "20 ms rule" and vestibular-visual conflict: why a few milliseconds of lag translate directly into motion sickness
- Tracking not feeling smooth: the [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) threaded discussion (97+ comments from users reporting nausea-inducing lag)
- "Missing" latency: the [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334) finding that VR streaming stacks underreport total system latency by 30–50%
- Calibration instability in MR: [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — SpectatorView calibration that works once and never twice (19 comments)
- HoloLens 2 Direct3D 12 performance and frame-timestamp precision (microsoft/OpenXR-MixedReality #131, #132)

**Potential Guests**
- **leinardi** — SteamVR-for-Linux maintainer; on the ground with motion-to-photon latency on open-source VR
- **jd-3d** — ALVR developer; first-hand investigation into "missing" latency in VR streaming
- **brycehutchings** — Microsoft OpenXR contributor; MR performance & the Direct3D 12 path
- **fredemmott** — Microsoft XR Advocate; HoloLens platform
- **emaschino** — active MR performance researcher
- **fieldsJacksonG** — Microsoft MRC; assignee on hologram registration & calibration

---

## Episode 2: "Spatial Sound and the Third Dimension"

**Focus:** How spatial-audio algorithms trick the brain into hearing sound in 3D space — and why a one-size-fits-all HRTF still isn't good enough.

**Key Topics**
- Head-Related Transfer Functions (HRTFs) and the personalization challenge
- Vector Base Amplitude Panning (VBAP) and higher-order ambisonics (HOA)
- Real-time binaural/ambisonic rendering on the web — the [GoogleChrome/omnitone](https://github.com/GoogleChrome/omnitone) approach (FOA/HOA renderers, Web Audio API)
- HRTF augmentation effects on spatial release from masking (see community HFSP work)
- Audio–visual integration in VR: vision dominates when cues conflict
- Room acoustics modeling (ISM reverberation) and perceptual quality
- Accessibility: spatial audio as navigation for visually impaired users

**Potential Guests**
- **leomccormack** — creator of Spatial_Audio_Framework; ambisonics, HRTFs & temporal rendering
- **crlandsc**, **ali-vosoughi**, **jacobhollebon** — Spatial_Audio_Framework contributors (spatialization algorithms)
- **BinWang28** — audio-ai-hub; HRTF research & spatial speech perception
- **edurnebernal** — audio-visual spatial perception in VR
- **TheBarmaEffect** — perception-first spatial audio engine design
- **Boris Smus / Brandon Jones / Julius Kammerl** — omnitone / Google spatial audio team
- **Tim Fain** — Jaunt VR; spatial content & rendering

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**Focus:** The design of mixed-reality interfaces — optical passthrough quality, boundary systems, hologram registration, and how MR competes for our attention.

**Key Topics**
- Hologram registration errors: [microsoft/MixedRealityCompanionKit #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — "holograms sticking to camera," reprojection drift across network stacks (18 comments)
- Optical passthrough quality and the resolution/contrast race (visionOS, Quest 3, XREAL)
- Plane detection & spatial mapping limitations in dynamic environments (visionOS-examples)
- WebXR layers & projection-layer scaling — cut-off and visual artifacts ([webxr-samples #228, #231, #235](https://github.com/immersive-web/webxr-samples)), and DOM overlays in canvas ([webxr #1414](https://github.com/immersive-web/webxr/issues/1414))
- Dynamic foveation and visibility masking as perceptual-performance levers ([webxr #1420](https://github.com/immersive-web/webxr/issues/1420), [webxr #1396](https://github.com/immersive-web/webxr/issues/1396))
- The attention economy: how persistent holographic UIs hijack focus

**Potential Guests**
- **maluoi** — StereoKit maintainer; XR engine & OpenXR backend
- **cabanier** — W3C Immersive Web; WebXR DOM overlays & visibility
- **AdaRoseCannon** — W3C Immersive Web; dynamic foveation & accessibility
- **himorin** — WebXR contributor; security/privacy of spatial mapping
- **chrisdavidmills** — WebXR visibility-mask events
- **danrossi** — WebXR layers & projection-layer work
- **aphillia** — input profiles & i18n for XR

---

## Behind the Episodes: The Hot Debates (from open issues)

| Debate | Where it's live | Why it matters for perception |
|---|---|---|
| Vestibular-visual conflict & motion sickness | SteamVR-for-Linux #21, ALVR #334 | Defines the acceptable latency ceiling |
| "Missing" system latency | ALVR #334 | Misleads optimization efforts |
| MR calibration fragility | MixedRealityCompanionKit #228 | Blocks research reproducibility |
| HRTF personalization vs. generic | audio-ai-hub, Spatial_Audio_Framework | Determines whether virtual sound feels "real" |
| Hologram drift / "stick to camera" | MixedRealityCompanionKit #221 | Core MR presence problem |
| WebXR layers & passthrough artifacts | webxr-samples #228/#231/#235 | Visual comfort vs. fidelity trade-off |
| Visibility masking & foveation | webxr #1420, #1396 | Perceptual dilution of performance cost |
