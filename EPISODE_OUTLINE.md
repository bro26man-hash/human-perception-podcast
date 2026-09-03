# The Future of Human Perception — Episode Outline

## Series Overview

This podcast explores the cutting edge of how humans perceive and interact with digital environments — from augmented reality and spatial computing to spatial audio and mixed reality interfaces. Each episode dives into a different dimension of perceptual technology, featuring insights from leading researchers, developers, and practitioners.

---

## Episode 1: "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as "real"?

**Key Topics:**
- Motion-to-photon latency in AR/MR headsets
- HoloLens 2 Direct3D 12 performance considerations (see [microsoft/OpenXR-MixedReality #132](https://github.com/microsoft/OpenXR-MixedReality/issues/132))
- Frame timestamp precision and temporal synchronization (see [microsoft/OpenXR-MixedReality #131](https://github.com/microsoft/OpenXR-MixedReality/issues/131))
- The perceptual clock: How the brain processes temporal discrepancies
- Camera feed latency vs. render latency in passthrough AR

**Potential Guests:**
- **leomccormack** (Spatial Audio Framework creator — temporal rendering expertise)
- **brycehutchings** (Microsoft OpenXR contributor — MR performance)
- **thetuvix** (OpenXR-MixedReality contributor — HRTF & spatialization)
- **fredemmott** (Microsoft XR Advocate — HoloLens platform)
- **emaschino** (Active MR performance researcher)

---

## Episode 2: "Spatial Sound and the Third Dimension"

**Focus:** How spatial audio algorithms trick the brain into hearing sound in 3D space.

**Key Topics:**
- Head-Related Transfer Functions (HRTFs) and personalization challenges
- Vector Base Amplitude Panning (VBAP) and higher-order ambisonics (see [leomccormack/Spatial_Audio_Framework #66](https://github.com/leomccormack/Spatial_Audio_Framework/issues/66))
- HRTF dataset issues — SONICOM loading bugs and perceptual accuracy (see [leomccormack/Spatial_Audio_Framework #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55))
- Room acoustics simulation: ISM reverberation and perceptual quality (see [leomccormack/Spatial_Audio_Framework #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58))
- Real-time spatial audio rendering on the web (Google/Chrome Omnitone, beatsync)
- 360° video spatial audio sync (Google/spatial-media)

**Potential Guests:**
- **leomccormack** (Spatial_Audio_Framework creator — ambisonics & HRTFs)
- **crlandsc**, **ali-vosoughi**, **jacobhollebon** (Spatial_Audio_Framework contributors — spatialization algorithms)
- **mormegil6**, **egerdem** (Spatial_Audio_Framework — acoustic modeling)
- **sanillevi**, **jdemuynke** (Spatial_Audio_Framework — real-time rendering)

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**Focus:** How mixed reality collapses the boundary between digital UI and physical space.

**Key Topics:**
- Gaze, gesture, and speech: The holy trinity of XR interaction
- Hand tracking & hand controller simulation roadmap (see [XRTK/com.xrtk.core #645](https://github.com/XRTK/com.xrtk.core/issues/645))
- Pointer/Gaze interaction breakdown during fast motion (see [XRTK/com.xrtk.core #902](https://github.com/XRTK/com.xrtk.core/issues/902))
- Scriptable Render Pipeline support for MR visual fidelity (see [XRTK/com.xrtk.core #407](https://github.com/XRTK/com.xrtk.core/issues/407))
- visionOS spatial UI patterns on Apple Vision Pro (see [IvanCampos/visionOS-examples](https://github.com/IvanCampos/visionOS-examples))
- Record & replay frameworks for UI testing in XR (see [XRTK/com.xrtk.core #652](https://github.com/XRTK/com.xrtk.core/issues/652))
- Spatial graph node spaces and reference frame semantics (see [microsoft/OpenXR-MixedReality #115](https://github.com/microsoft/OpenXR-MixedReality/issues/115))

**Potential Guests:**
- **StephenHodgson** (XRTK core contributor — MR interaction design)
- **FejZa** (XRTK maintainer — rendering & input systems)
- **jdwalker** (XRTK — record/replay & frameworks)
- **jasongraham** (visionOS spatial UI)
- **crlandsc** (Spatial_Audio_Framework — cross-modal perception)
- **anasnap** (project lead)

---

## Production Notes

- **Repo:** https://github.com/bro26man-hash/human-perception-podcast
- **License:** MIT (open collaboration)
- **Format:** Audio interview + live demo segments
- **Cadence:** Bi-weekly
- **Status:** Planning — Episode outlines and contributor outreach in progress