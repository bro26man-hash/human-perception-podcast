# 🎙️ The Future of Human Perception — Episode Outline

> **Production hub for podcast episodes**, seeded with GitHub research from the most active AR / Spatial Computing / Perceptual Science repositories.

---

## 📋 Research Sources

This outline is grounded in live analysis of GitHub open issues, PRs, and contributor activity across the following repositories:

| Repository | Stars | Relevance |
|---|---|---|
| [jeromeetienne/AR.js](https://github.com/jeromeetienne/AR.js) | ⭐ 15,791 | Web AR — 60 fps on mobile, marker & location tracking |
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | ⭐ 5,988 | Image & location-based AR on the web (maintained fork) |
| [mrdoob/three.js](https://github.com/mrdoob/three.js) | ⭐ 115,636 | Foundational 3D library underpinning all WebXR/AR experiences |
| [ValveSoftware/openvr](https://github.com/ValveSoftware/openvr) | ⭐ 6,661 | OpenVR SDK — motion-to-photon latency, tracker pipelines |
| [google-ar/three.ar.js](https://github.com/google-ar/three.ar.js) | ⭐ 2,914 | ARCore + Cardboard helper for three.js |
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | ⭐ 2,733 | Web AR with TensorFlow.js — face & image tracking |
| [fholger/openvr_fsr](https://github.com/fholger/openvr_fsr) | ⭐ 1,809 | Foveated rendering via AMD FidelityFX SR in SteamVR |
| [polygraphene/ALVR](https://github.com/polygraphene/ALVR) | ⭐ 1,844 | Air Link VR — wireless PC VR streaming for standalone headsets |
| [facebook/immersive-web-sdk](https://github.com/facebook/immersive-web-sdk) | ⭐ 357 | WebXR framework — locomotion, spatial UI, hit-test APIs |
| [google/model-viewer](https://github.com/google/model-viewer) | ⭐ 8,248 | 3D model viewer with AR support — render fidelity & lazy loading |
| [Microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | ⭐ 6,076 | MRTK v2 — spatial audio, hand tracking, HoloLens SDK |
| [Microsoft/MixedReality-WebRTC](https://github.com/Microsoft/MixedReality-WebRTC) | ⭐ 944 | MR audio/video comms — spatial audio in WebRTC (deprecated but historically significant) |
| [Microsoft/MixedRealityToolkit](https://github.com/microsoft/MixedRealityToolkit) | ⭐ 867 | MRTK C++ — foundation for managed MRTK |
| [MixedRealityToolkit/MixedRealityToolkit-Unity](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity) | ⭐ 550 | MRTK3 — third-generation Unity toolkit |
| [google/lullaby](https://github.com/google/lullaby) | ⭐ 1,197 | C++ libraries for VR/AR experience development |
| [ekmett/openvr](https://github.com/ekmett/openvr) | ⭐ — | Latency research fork by rendering architect ekmett |

---

## 🎧 Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency, the 20 ms rule, and whether foveation can trick the brain into forgiving lag.

**Key Debate:** Can foveated rendering shave enough time off the pipeline to stay under the perceptual threshold, or do we need fundamental architectural changes?

### Hot Topics from GitHub

- **Motion-to-photon latency measurement** — [ValveSoftware/openvr#249](https://github.com/ValveSoftware/openvr/issues/249): *"Equivalent of motion-to-photon latency? Measuring latency incurred by sensor hardware"* — still open after 9 years; the problem is unsolved.
- **Display pipeline latency** — [ValveSoftware/openvr#258](https://github.com/ValveSoftware/openvr/issues/258): *"Displaying old data, avoiding glFinish() and latency spikes"* by **ekmett** (a rendering architect) — the fundamental tension between frame completion and display refresh.
- **Periodic lag spikes** — [ValveSoftware/openvr#374](https://github.com/ValveSoftware/openvr/issues/374): *"Massive lag spike every 8 seconds — reproducible"* — suggests driver/compositor-level timing issues.
- **Tracker pipeline delay** — [ValveSoftware/openvr#1704](https://github.com/ValveSoftware/openvr/issues/1704): *"Tracker data from OVR is very delayed compared to SteamVR"* — shows that even within Valve's ecosystem, latency varies by API path.
- **Foveated rendering as mitigation** — [fholger/openvr_fsr](https://github.com/fholger/openvr_fsr): AMD FidelityFX SuperResolution applied to VR to render at lower resolution in periphery, potentially reducing per-pixel processing time.
- **Model-viewer render performance** — [google/model-viewer#930](https://github.com/google/model-viewer/issues/930): *"Enable rendering to be moved to a worker"* — offloading rendering to a separate thread is a latency mitigation strategy for web-based 3D.

### Potential Guests

| Name | Handle | Why They're Perfect |
|---|---|---|
| **Jerome Etienne** | [@jeromeetienne](https://github.com/jeromeetienne) | Creator of AR.js; experienced first-hand how tracking latency breaks immersion in Web AR. |
| **ekmett** | [@ekmett](https://github.com/ekmett) | Rendering engineer who filed the foundational OpenVR latency issue #258; knows the display pipeline inside out. |
| **fholger** | [@fholger](https://github.com/fholger) | Built openvr_fsr — the foveated rendering bridge between VR and SuperResolution tech. |
| **polygraphene** | [@polygraphene](https://github.com/polygraphene) | Created ALVR (Air Link VR); wireless streaming introduces its own latency calculus. |
| **cdata** | [@cdata](https://github.com/cdata) | Google model-viewer lead; can speak to web-based rendering latency challenges and worker-threading solutions. |

### Key Questions for the Episode
1. What exactly is motion-to-photon latency, and why is 20 ms the magic number?
2. How do foveated rendering techniques (FSR, eye-tracking) reduce effective latency?
3. Can Web AR platforms (AR.js) achieve the same latency budgets as native VR SDKs?
4. Is the OpenVR driver model fundamentally limited, or can architectural changes fix the 8-second spike problem?
5. What can web-based 3D (model-viewer, three.js) learn from VR SDK latency engineering?

### GitHub Issues to Reference
- [ValveSoftware/openvr#249](https://github.com/ValveSoftware/openvr/issues/249)
- [ValveSoftware/openvr#258](https://github.com/ValveSoftware/openvr/issues/258)
- [ValveSoftware/openvr#374](https://github.com/ValveSoftware/openvr/issues/374)
- [ValveSoftware/openvr#1704](https://github.com/ValveSoftware/openvr/issues/1704)
- [fholger/openvr_fsr](https://github.com/fholger/openvr_fsr)
- [google/model-viewer#930](https://github.com/google/model-viewer/issues/930)

---

## 🔊 Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics, and the audio presence paradox — why spatial audio matters more than graphics for immersion.

**Key Debate:** Why is the WebXR specification still effectively visual-only for spatial audio, and can glTF's new audio extension architecture fix it?

### Hot Topics from GitHub

- **Layered audio extension architecture** — [KhronosGroup/glTF#2561](https://github.com/KhronosGroup/glTF/issues/2561): *"Proposal: Layered Audio Extension Architecture — KHR_audio_emitter + KHR_audio_graph + KHR_audio_environment"* by **rudybear** — a comprehensive framework for spatial audio in glTF.
- **KHR_audio_emitter** — [KhronosGroup/glTF PR#2137](https://github.com/KhronosGroup/glTF/pull/2137) by **robertlong** — 58 comments, very active discussion; the base emitter extension.
- **KHR_audio_environment** — [KhronosGroup/glTF PR#2631](https://github.com/KhronosGroup/glTF/pull/2631) by **rudybear** — acoustic environment modeling (reverb, occlusion).
- **KHR_audio_graph** — [KhronosGroup/glTF PR#2632](https://github.com/KhronosGroup/glTF/pull/2632) by **rudybear** — audio signal routing graph for complex scenes.
- **Synchronized immersive video + audio** — [KhronosGroup/glTF#2506](https://github.com/KhronosGroup/glTF/issues/2506): *"Extending glTF for Synchronized Immersive Video and Audio"* — the broader synchronization question.
- **MRTK Spatializer** — [Microsoft/MixedRealityToolkit-Unity#6897](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6897): *"MRTK should use the new Microsoft Spatializer with hardware offload support"* — hardware-accelerated spatial audio is a game-changer for MR.
- **Spatialized audio inaudibility bug** — [Microsoft/MixedRealityToolkit-Unity#11176](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11176): *"Spatialized audio is inaudible"* — a real-world bug that exposes how fragile spatial audio implementation still is.
- **WebRTC spatial audio gap** — [Microsoft/MixedReality-WebRTC#92](https://github.com/Microsoft/MixedReality-WebRTC/issues/92): *"Support for connecting a WebRTC audio track to a Unity AudioSource"* — bridging real-time comms spatial audio with engine audio.
- **WebXR's audio gap** — The WebXR Device API spec defines spatial audio sources but the browser implementation landscape is fragmented; the W3C Immersive Web Working Group has no working group draft for spatial audio rendering.

### Potential Guests

| Name | Handle | Why They're Perfect |
|---|---|---|
| **rudybear** | [@rudybear](https://github.com/rudybear) | Authored the complete glTF spatial audio extension architecture proposal; deep knowledge of spatial audio in 3D formats. |
| **robertlong** | [@robertlong](https://github.com/robertlong) | Submitted the foundational KHR_audio_emitter PR; experienced in glTF extension development. |
| **najadojo** | [@najadojo](https://github.com/najadojo) | Authored the MSFT_audio_emitter extension; Microsoft's perspective on spatial audio in glTF. |
| **marlenaklein-msft** | [@marlenaklein-msft](https://github.com/marlenaklein-msft) | MRTK spatial audio lead; filed the Spatializer hardware offload issue and the spatial audio documentation issue. |
| **Jerome Etienne** | [@jeromeetienne](https://github.com/jeromeetienne) | AR.js creator; can speak to how audio is currently handled (or ignored) in web AR experiences. |

### Key Questions for the Episode
1. What is the difference between HRTF-based spatial audio and simpler stereo panning, and why does it matter for presence?
2. Why does WebXR lack a spatial audio rendering spec, and what's blocking it?
3. Can glTF's KHR_audio_emitter / KHR_audio_graph / KHR_audio_environment triple become the standard for spatial audio in 3D?
4. How do ambisonics compare to HRTF approaches for the web?
5. What's the "audio presence paradox" — why do we forgive visual imperfections but reject audio ones faster?
6. How does hardware-accelerated spatial audio (Microsoft Spatializer) change the MR audio landscape?

### GitHub Issues to Reference
- [KhronosGroup/glTF#2561](https://github.com/KhronosGroup/glTF/issues/2561)
- [KhronosGroup/glTF PR#2137](https://github.com/KhronosGroup/glTF/pull/2137)
- [KhronosGroup/glTF PR#2631](https://github.com/KhronosGroup/glTF/pull/2631)
- [KhronosGroup/glTF PR#2632](https://github.com/KhronosGroup/glTF/pull/2632)
- [KhronosGroup/glTF#2506](https://github.com/KhronosGroup/glTF/issues/2506)
- [Microsoft/MixedRealityToolkit-Unity#6897](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6897)
- [Microsoft/MixedRealityToolkit-Unity#11176](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11176)
- [Microsoft/MixedReality-WebRTC#92](https://github.com/Microsoft/MixedReality-WebRTC/issues/92)

---

## 🖐️ Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hand tracking, hologram drift, and wayfinding.

**Key Debate:** Is the WebXR specification blind to non-visual perception — and what does MR interface design look like when the screen is the world?

### Hot Topics from GitHub

- **WebXR Hit-Test & Depth APIs** — [facebook/immersive-web-sdk#13](https://github.com/facebook/immersive-web-sdk/issues/13): *"Feature Request: Expose WebXR Hit-Test & Depth APIs to Userland (XRFrame / XRSession Access)"* by **aribornstein** — MR interfaces need spatial understanding APIs beyond what the spec currently exposes.
- **Locomotion precision** — [facebook/immersive-web-sdk#11](https://github.com/facebook/immersive-web-sdk/issues/11): *"Locomotion Example — Falling through the floor"* — even basic movement in MR/VR is unstable.
- **Spatial UI interaction model** — [facebook/immersive-web-sdk#41](https://github.com/facebook/immersive-web-sdk/issues/41): *"Spatial UI forwarded touch/click events lose iOS Safari user activation"* — the interaction model breaks on the dominant mobile platform.
- **Cursor-surface alignment** — [facebook/immersive-web-sdk#53](https://github.com/facebook/immersive-web-sdk/issues/53): *"Cursor sinks into the surface after the player turns"* — fundamental MR interface problem.
- **AR.js tracking reliability** — [jeromeetienne/AR.js#826](https://github.com/jeromeetienne/AR.js/issues/826): *"ImageTracking demo doesn't work"* and [#825](https://github.com/jeromeetienne/AR.js/issues/825): *"Location-based example doesn't work"* — GPS drift and image tracking failures are the MR interface problem at the web scale.
- **glTF audio under viewer scale** — [KhronosGroup/glTF#2162](https://github.com/KhronosGroup/glTF/issues/2162): *"Undefined behaviour of light (and audio) under viewer scale"* — even the spec doesn't fully define how sensory inputs behave at different scales.
- **MRTK hand tracking** — [Microsoft/MixedRealityToolkit-Unity#6974](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6974): *"Hand tracking not correctly notified of coordinate space resets"* — hand tracking is a core MR interface input but is plagued by coordinate system bugs.
- **MRTK WebXR support** — [Microsoft/MixedRealityToolkit-Unity#8472](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8472): *"Feature Request: Support for WebXR"* (Won't Fix) — Microsoft's MRTK is moving away from WebXR support, creating a gap in the MR interface tooling landscape.

### Potential Guests

| Name | Handle | Why They're Perfect |
|---|---|---|
| **aribornstein** | [@aribornstein](https://github.com/aribornstein) | Submitted the critical WebXR Hit-Test & Depth API feature request; lives in the MR interface gap between spec and reality. |
| **Jerome Etienne** | [@jeromeetienne](https://github.com/jeromeetienne) | AR.js creator; faced tracking reliability and location-based GPS drift challenges firsthand. |
| **hiukim** | [@hiukim](https://github.com/hiukim) | mind-ar-js creator; TensorFlow.js-based face & image tracking — a different approach to MR interface input. |
| **mrdoob** | [@mrdoob](https://github.com/mrdoob) | three.js creator; the foundational 3D engine that all MR interfaces are built on. |
| **david-c-kline** | [@david-c-kline](https://github.com/david-c-kline) | MRTK lead at Microsoft; can speak to the strategic decisions around WebXR support and MR interface architecture. |

### Key Questions for the Episode
1. What's the difference between a "MR interface" and a "VR interface" in terms of perceptual design?
2. Why does the WebXR spec expose locomotion and rendering but not spatial audio rendering or spatial understanding?
3. How do hand tracking vs. controller input change the perceived interface paradigm?
4. What is "hologram drift" and why do AR.js tracking failures (#825, #826) exemplify it?
5. Can hit-test and depth APIs (Issue #13) bridge the gap between what WebXR offers and what MR interfaces need?
6. What does it mean that Microsoft's MRTK is deprecating WebXR support (#8472)?

### GitHub Issues to Reference
- [facebook/immersive-web-sdk#13](https://github.com/facebook/immersive-web-sdk/issues/13)
- [facebook/immersive-web-sdk#11](https://github.com/facebook/immersive-web-sdk/issues/11)
- [facebook/immersive-web-sdk#41](https://github.com/facebook/immersive-web-sdk/issues/41)
- [facebook/immersive-web-sdk#53](https://github.com/facebook/immersive-web-sdk/issues/53)
- [jeromeetienne/AR.js#826](https://github.com/jeromeetienne/AR.js/issues/826)
- [jeromeetienne/AR.js#825](https://github.com/jeromeetienne/AR.js/issues/825)
- [KhronosGroup/glTF#2162](https://github.com/KhronosGroup/glTF/issues/2162)
- [Microsoft/MixedRealityToolkit-Unity#6974](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6974)
- [Microsoft/MixedRealityToolkit-Unity#8472](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8472)

---

## 🗺️ Future Episodes (Brainstorm)

| # | Title | Focus |
|---|---|---|
| 4 | **The Body Owns the Avatar** | Proprioception, full-body tracking, and the uncanny valley of embodied VR |
| 5 | **Multi-Sensory Fusion** | How the brain combines visual, auditory, and haptic signals — and what happens when they conflict |
| 6 | **Perception at Scale** | Urban-scale AR, geo-anchored experiences, and the psychology of shared spatial awareness |
| 7 | **The Ethics of Perceptual Hacking** | When latency tricks and sensory manipulation stop being features and become weaponized |

---

## 📌 How to Use This Outline

1. **Each episode issue** (#139, #140, #141) is seeded with the topics, GitHub issue links, and potential guests from this outline.
2. Contributors: add research findings, additional issue links, or guest suggestions as **comments** on the episode issues.
3. When an issue is resolved (guest confirmed, topics locked), update the issue labels and move to `episodes/` for drafting.
4. Cross-reference the `GITHUB-RESEARCH-ADDENDUM.md` for the full audit of issues and contributors across all surveyed repos.

---

*Last updated: September 2026 · Research sourced from live GitHub issue analysis across 15+ AR/MR/Spatial Computing repositories.*