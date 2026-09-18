# 🎙️ The Future of Human Perception — Initial Episode Outline

> **A collaborative podcast series exploring the bleeding edge of augmented reality, spatial computing, and perceptual science.**
> 
> Each episode targets a core question about how humans perceive and interact with digital environments — grounded in real open-source debates and active XR communities.
>
> **Repo:** https://github.com/bro26man-hash/human-perception-podcast  
> **Format:** Audio interview + live demo segments  |  **Cadence:** Bi-weekly  |  **License:** MIT

---

## 📡 Season 1 — Three Pilot Episodes

---

### Episode 1: "The Latency Gap — When Perception Meets Processing"

**Core Question:** If a headset introduces just 20 ms of motion-to-photon delay, the vestibular system detects it. What does that *feel* like, and what's happening in the pipeline that makes it so hard to eliminate?

**Key Topics:**
- **Perceptual latency thresholds:** the ~20 ms rule, vestibular-visual conflict, motion-sickness onset, and the "perceptual clock"
- **Motion-to-photon pipeline:** Sensor → Predict → Render → Encode → Transport → Decode → Display
- **Camera↔IMU hardware clock synchronization:** Xiaomi/OPPO 13–35 ms offsets (google-ar/arcore-android-sdk #1779)
- **Tracking & floor-plane drift:** "Tracking not smooth and a little delayed" — 97 comments (ValveSoftware/SteamVR-for-Linux #21); ARCore floor plane drift that is metrically correct then incorrectly updated (#1781)
- **"Missing" latency:** A researcher found ~33.6 ms of unaccounted latency in a VR streaming stack (polygraphene/ALVR #334)
- **Depth-map noise on mid-range devices** (google-ar/arcore-android-sdk #1723)
- **Calibration instability:** SpectatorView calibration that works once but never twice (microsoft/MixedRealityCompanionKit #228)
- **HoloLens / OpenXR timing:** Direct3D 12 performance, frame timestamp precision, and temporal synchronization (microsoft/OpenXR-MixedReality #131, #132)
- **Web / mobile AR pipeline:** How AR.js (markerless & location-based, 15.8k★) and MindAR (TensorFlow.js image/face tracking, 2.7k★) handle the camera→render loop
- **Foveated rendering as a latency cheat:** Can reducing render resolution in the periphery trick the brain into forgiving lag?

**🔥 Hot Debates to Surface:**
- *Perceptual vs. measured latency:* Is the latency our instruments measure the same as what the brain detects?
- *Where does latency "live"?* Sensor fusion, prediction, encode/transport, decode, display — which stage is least optimized?
- *Is the 20ms rule a hard physical limit or a soft cultural norm?*
- *Should developers be ethically required to disclose when they're "hiding" latency via reprojection?*

**🎤 Primary Guest Contributors:**
| Name | Handle | Relevance |
|------|--------|----------|
| hiukim | @hiukim | Creator of MindAR; on tracking jitter and why Web AR lags behind commercial |
| Nicolò Carpignoli | @nicolocarpignoli | AR.js former maintainer; deepest knowledge of Web AR architecture |

**🎤 Secondary Guest Contributors:**
| Name | Handle | Relevance |
|------|--------|----------|
| kalwalt | @kalwalt | AR.js current maintainer; holds keys to ARCore/WebXR integration decisions |
| dogzilla | @dogzilla | MindAR fork maintainer; community voice on open-source vs. commercial tracking |
| param-fsd | @param-fsd | MindAR tracking stability researcher; documents gap between open-source and commercial quality |
| leinardi | @leinardi | SteamVR for Linux maintainer; motion-to-photon latency on open-source VR |
| jd-3d / polygraphene | — | ALVR developer; first-hand investigation into "missing" pipeline latency |

**📎 Source Issues:**
- [ValveSoftware/openvr #1012](https://github.com/ValveSoftware/openvr/issues/1012) — Reprojection control
- [ValveSoftware/openvr #1729](https://github.com/ValveSoftware/openvr/issues/1729) — GPU timestamp corruption
- [ValveSoftware/openvr #1917](https://github.com/ValveSoftware/openvr/issues/1917) — `xrWaitFrame` negative predictedDisplayTime
- [google-ar/arcore-android-sdk #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) — Camera-IMU clock offset
- [google-ar/arcore-android-sdk #1781](https://github.com/google-ar/arcore-android-sdk/issues/1781) — Floor plane drift
- [google-ar/arcore-android-sdk #1723](https://github.com/google-ar/arcore-android-sdk/issues/1723) — Depth-map noise
- [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — Calibration instability
- [microsoft/OpenXR-MixedReality #131](https://github.com/microsoft/OpenXR-MixedReality/issues/131) — HoloLens timing
- [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334) — Missing latency
- [AR-js-org/AR.js #288](https://github.com/AR-js-org/AR.js/issues/288) — Markerless location-based AR
- [AR-js-org/AR.js #609](https://github.com/AR-js-org/AR.js/issues/609) — Maintainers needed
- [AR-js-org/AR.js #681](https://github.com/AR-js-org/AR.js/issues/681) — AR.js-next ECS roadmap
- [hiukim/mind-ar-js #526](https://github.com/hiukim/mind-ar-js/issues/526) — "Is this repo abandonware?"
- [hiukim/mind-ar-js #556](https://github.com/hiukim/mind-ar-js/issues/556) — Tracking instability

---

### Episode 2: "Spatial Sound & the Third Dimension — Sound as the Ultimate Spatial Sense"

**Core Question:** WebXR has no first-class spatial audio channel. HRTFs, ambisonics, and room modeling are either absent from the spec or relegated to extensions that browsers implement inconsistently. Why is the most important sense for presence the one the spec ignores?

**Key Topics:**
- **The WebXR audio gap:** No `XRSoundLayer`, no HRTF API, no ambisonic encoding built into the spec
- **Bluetooth audio delay as a per-user manual slider** (Igalia/wolvic #1180) — no automatic calibration, no HRTF adaptation, no room modeling
- **WebXR Layers (#992):** Visual compositing only — spatial audio has no spec representation whatsoever
- **8K HEVC on Quest 2 (#1196):** The resolution arms race for visuals has no parallel in audio
- **HRTF personalization:** How individualized head-related transfer functions change presence — and why default HRTFs feel "off"
- **Ambisonics as a workaround:** How projects like facebook/immersive-web-sdk implement spatial audio at the SDK level when the spec doesn't support it
- **The spatial audio metadata gap:** Google's spatial-media RFC exists, but there's no WebXR integration path
- **Room modeling and reflections:** How acoustic modeling affects perceived presence in MR environments
- **The "presence paradox":** Visual immersion without spatial audio creates an uncanny valley — you *see* the world but can't *hear* your way around it

**🔥 Hot Debates to Surface:**
- *Is spatial audio a "nice to have" or a "must have" for true presence?*
- *If we can't get the spec to represent spatial audio as a first-class concept, are we building associative or architectural solutions?*
- *Should there be a "WebXR Audio Layer 1.0" requirement?*
- *Does the visual-first bias in XR spec development reflect a deeper perceptual hierarchy — or just a market assumption?*

**🎤 Primary Guest Contributors:**
| Name | Handle | Relevance |
|------|--------|----------|
| Yongsen Mao | @manycore-research | Lead researcher, SpatialLM (NeurIPS 2025); 3D LLMs for spatial perception — could bridge geometric tracking and semantic audio understanding |

**🎤 Secondary Guest Contributors:**
| Name | Handle | Relevance |
|------|--------|----------|
| facebook/immersive-web-sdk team | — | Built spatial audio as a first-class system when the spec didn't have it |
| google/spatial-media maintainers | — | Maintain spatial audio RFC; know the gap between spec and implementation |
| Nicolò Carpignoli | @nicolocarpignoli | Can speak to why AR.js/WebAR has no audio pipeline |

**📎 Source Issues:**
- [Igalia/wolvic #1180](https://github.com/Igalia/wolvic/issues/1180) — Bluetooth audio delay manual slider
- [Igalia/wolvic #992](https://github.com/Igalia/wolvic/issues/992) — WebXR Layers visual-only
- [Igalia/wolvic #1196](https://github.com/Igalia/wolvic/issues/1196) — 8K HEVC vs. audio quality
- [google/spatial-media spatial-audio-rfc](https://github.com/google/spatial-media/blob/main/docs/spatial-audio-rfc.md) — Spatial audio RFC
- [facebook/immersive-web-sdk](https://github.com/facebook/immersive-web-sdk) — SDK-level spatial audio implementation
- [hiukim/mind-ar-js #526](https://github.com/hiukim/mind-ar-js/issues/526) — Web AR abandonware question (no audio path either)

---

### Episode 3: "Interfaces Beyond the Flat Screen — MR Interfaces, Hologram Drift & the WebXR Blind Spot"

**Core Question:** Despite being "spatial" computing, XR interfaces are still designed around 2D paradigms — gamepads, flat screens, and 2D input APIs. The "three-dimensional" part of 3D interfaces is mostly visual, not interactive. Are we building "3D interfaces with 2D constraints" or "truly spatial interfaces"?

**Key Topics:**
- **The 2D input trap:** XRControllers must be "flattened" into Gamepad API (#993) — spatial input is reduced to 2D axes before the app ever sees it
- **Spatial navigation for D-pads (#1110):** Assumes a 3D space traversed by a 2D input device — the mismatch is acknowledged but unsolved
- **Content discovery & launching immersive elements (#2071):** The discovery problem for MR content is barely addressed in the spec
- **Markerless AR at city scale (#833):** Local SLAM doesn't scale to global reference frames; tracking paradigm breaks at geographic scope
- **Geospatial AR (#834):** Needs earth-centered coordinates but AR.js only handles local tracking
- **Hologram drift & registration:** MR content that drifts, wobbles, or loses tracking breaks the illusion more decisively than visual glitches
- **Hand tracking vs. controller paradigms:** Which paradigm better supports "natural" interaction — and is either truly spatial?
- **Wayfinding in MR:** How do you navigate a spatial interface when the interface itself is the space?
- **Proprioceptive and haptic interfaces:** The next frontier beyond gaze, voice, and gesture

**🔥 Hot Debates to Surface:**
- *Are we building "3D interfaces with 2D constraints" or "truly spatial interfaces"? What would the latter even feel like?*
- *Is the WebXR spec blind to non-visual perception?*
- *The Perceptual Transparency Problem: When technology hides perceptual realities from users, is that a feature or a betrayal?*
- *Can 3D LLMs (SpatialLM) finally provide the semantic world understanding that tracking-only approaches lack?*

**🎤 Primary Guest Contributors:**
| Name | Handle | Relevance |
|------|--------|----------|
| Jérôme Étienne | @jeromeetienne | Creator of AR.js; his vision of `tracking: best` and why markerless was never built |

**🎤 Secondary Guest Contributors:**
| Name | Handle | Relevance |
|------|--------|----------|
| kylebakerio | @kylebakerio | WebXR/ARCore integration advocate; argues AR.js must adopt ARCore/ARKit or lose relevance |
| nickw1 | @nickw1 | AR.js location-based AR contributor; understands GPS-AR drift better than anyone |
| dogzilla | @dogzilla | Community fork maintainer; perspective on what comes after AR.js/MindAR |
| CoderSilas | @CoderSilas | Found encantar.js as a replacement; the canary in the coal mine for "what comes next" |
| Yongsen Mao | @manycore-research | SpatialLM — 3D LLMs that could finally provide semantic world understanding for MR interfaces |

**📎 Source Issues:**
- [Igalia/wolvic #1110](https://github.com/Igalia/wolvic/issues/1110) — Spatial navigation for D-pads
- [Igalia/wolvic #993](https://github.com/Igalia/wolvic/issues/993) — XRControllers flattened to Gamepad API
- [Igalia/wolvic #2071](https://github.com/Igalia/wolvic/issues/2071) — Launching immersive elements
- [AR-js-org/AR.js #833](https://github.com/AR-js-org/AR.js/issues/833) — City-scale markerless AR
- [AR-js-org/AR.js #834](https://github.com/AR-js-org/AR.js/issues/834) — Geospatial AR
- [AR-js-org/AR.js #217](https://github.com/AR-js-org/AR.js/issues/217) — Markerless debate (Jerome's vision)
- [hiukim/mind-ar-js #526](https://github.com/hiukim/mind-ar-js/issues/526) — Abandonware & fork discussion
- [SpatialLM Paper](https://arxiv.org/abs/2506.07491) — 3D LLMs for spatial perception

---

## 🔁 Cross-Cutting Theme: The Perceptual Transparency Problem

All three episodes surface a deeper question that should frame each season's closing reflection:

**When technology hides perceptual realities from users, is that a feature or a betrayal?**

- Motion smoothing hides latency → is that "immersion enhancement" or "sensory deception"?
- Spatial audio omission hides the third dimension → is that "spec scope management" or "perceptual discrimination"?
- 2D input masking hides the spatial nature of interaction → is that "ergonomic pragmatism" or "paradigm capture"?

---

## 🗓️ Production Timeline

| Milestone | Target | Status |
|-----------|--------|--------|
| Outline finalization | Week 1 | ✅ This document |
| Guest outreach | Weeks 1–2 | 🔜 In progress |
| Episode 1 recording | Weeks 2–3 | ⏳ Pending |
| Episode 1 edit & publish | Week 4 | ⏳ Pending |
| Episode 2 recording | Weeks 5–6 | ⏳ Pending |
| Episode 2 edit & publish | Week 7 | ⏳ Pending |
| Episode 3 recording | Weeks 8–9 | ⏳ Pending |
| Episode 3 edit & publish | Week 10 | ⏳ Pending |

---

## 🤝 How to Contribute

1. **Pick an episode issue** (see open issues labeled `episode-1`, `episode-2`, `episode-3`)
2. **Add research findings, issue links, or potential guest suggestions** as comments on the issue
3. **Submit a PR** with updated episode outlines or new research
4. **Tag potential guests** and track outreach status in the Guest Directory

---

## 📚 Research Backbone — Key GitHub Repos Surveyed

| Repo | Stars | Focus | Key Issues |
|------|-------|-------|------------|
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 5,988 | Web AR (marker, image, location) | #288, #609, #681, #833, #834 |
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | 2,733 | Web AR (TensorFlow.js image/face) | #526, #556 |
| [ValveSoftware/openvr](https://github.com/ValveSoftware/openvr) | — | OpenVR runtime & spec | #1012, #1729, #1917 |
| [google-ar/arcore-android-sdk](https://github.com/google-ar/arcore-android-sdk) | — | ARCore mobile SDK | #1723, #1779, #1781 |
| [microsoft/MixedRealityCompanionKit](https://github.com/microsoft/MixedRealityCompanionKit) | — | MR calibration & tools | #228 |
| [microsoft/OpenXR-MixedReality](https://github.com/microsoft/OpenXR-MixedReality) | — | OpenXR MR extension | #131, #132 |
| [Igalia/wolvic](https://github.com/Igalia/wolvic) | — | WebXR browser implementation | #992, #993, #1110, #1180, #1196, #2071 |
| [facebook/immersive-web-sdk](https://github.com/facebook/immersive-web-sdk) | 357 | WebXR framework (spatial audio) | SDK-level innovation |
| [google/spatial-media](https://github.com/google/spatial-media) | — | Spatial audio & 360° video RFCs | spatial-audio-rfc |
| [polygraphene/ALVR](https://github.com/polygraphene/ALVR) | — | VR streaming (latency research) | #334 |
| [manycore-research/SpatialLM](https://github.com/manycore-research/SpatialLM) | 4,700+ | 3D LLM for spatial perception | NeurIPS 2025 paper |

---

*This outline was compiled from GitHub issue analysis across 10+ active AR/MR/Spatial Computing repositories. All issue references link to real, open discussions in the community.*