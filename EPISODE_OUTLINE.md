# 🎙️ The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **canonical episode outline** for the series. Updated 2026-09-17.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos |
|---|---|
| Web 3D / WebXR | `mrdoob/three.js` (115.6k ⭐), `playcanvas/engine` (16.7k ⭐), `immersive-web/webxr` (3.1k ⭐), `Hubs-Foundation/hubs` (2.2k ⭐) |
| Web AR | `AR-js-org/AR.js` (15.8k ⭐), `hiukim/mind-ar-js` (2.7k ⭐), `jeeliz/jeelizFaceFilter` (2.9k ⭐) |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity` (6.1k ⭐), `MixedRealityToolkit/MixedRealityToolkit-Unity` (550 ⭐), `microsoft/MixedReality-WebRTC` (944 ⭐) |
| Spatial Computing | `StereoKit/StereoKit` (1.1k ⭐), `KhronosGroup/OpenXR-SDK` (1.1k ⭐), `IvanCampos/visionOS-examples` (405 ⭐), `microsoft/xr-development-for-beginners` (564 ⭐) |
| Spatial Audio | `GoogleChrome/omnitone` (911 ⭐), `leomccormack/Spatial_Audio_Framework` (748 ⭐), `google/spatial-media` (2.1k ⭐), `freeman-jiang/beatsync` (3.2k ⭐) |
| AR SDKs | `google-ar/arcore-android-sdk` (5.2k ⭐), `google-ar/arcore-unity-sdk` (1.4k ⭐), `Unity-Technologies/arfoundation-samples` (3.4k ⭐), `olucurious/Awesome-ARkit` (8.0k ⭐) |
| 3D Assets & Standards | `KhronosGroup/glTF` (10k ⭐+) — audio emitter extensions, spatial video proposals |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Key Topics

1. **The motion-to-photon pipeline** — sensor → predict → render → encode → transport → decode → display. Every stage injects latency; the sum is what the brain judges.
2. **The "20 ms rule" and vestibular-visual conflict** — why a few milliseconds of lag translate directly into motion sickness. The brain's vestibular system expects sensory congruence; lag breaks it.
3. **Temporal irregularity vs. average latency** — WiVRn #282 (40 comments): maintainer `xytovl` traced stutter to >10 ms of reception-time variability, not raw pipeline depth. Is the brain detecting frame irregularity rather than average ms? This reframes the entire optimization target.
4. **"Missing" latency in VR streaming** — ALVR #334: ~33.6 ms of unaccounted latency; VR stacks underreport total system latency by 30–50%. The industry may be optimizing against a phantom number.
5. **Web AR tracking failure on mobile** — AR.js #826 (broken image tracking), AR.js #825 (location-based AR failing) — real-time tracking is the first perceptual bottleneck on the web.
6. **Hologram calibration instability** — MixedRealityCompanionKit #228: SpectatorView calibration that works once and never twice (19 comments). Blocks research reproducibility.
7. **Direct3D 12 & frame-timestamp precision** — HoloLens 2 performance and viewfinder reliability (OpenXR-MixedReality #131, #132).
8. **🔥 NEW: Acoustic echo cancellation failure in MR** — MixedReality-WebRTC #157 (17 comments): AEC disabled by default or non-functional in OpenXR MR stacks. When your headset can't cancel echo, the spatial audio model collapses — you can't localize sound in a room that's echoing. This is a *perceptual* latency problem, not just an audio bug.

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets (reduce average ms) are wrong — we need to stabilize frame delivery instead.

> **🔥 NEW: Acoustic echo cancellation is a spatial-perception problem.** The MixedReality-WebRTC #157 thread reveals that AEC — critical for spatial audio presence — is fundamentally broken in current MR stacks. Without echo cancellation, the room's acoustics contaminate the spatial audio model, making it impossible to determine whether a sound is "outside" the headset or "inside" the room. This isn't an audio quality issue; it's a *perceptual calibration* failure.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leinardi** | Maintainer, SteamVR-for-Linux | Open-source VR latency debugging; first-hand motion-to-photon pipeline experience |
| **jd-3d** | Developer, ALVR | VR streaming stack forensics; discovered the "missing" 30–50% latency underreporting |
| **xytovl** | Maintainer, WiVRn | OpenXR streaming; packet-timing & pacing algorithm design; stutter analysis |
| **AaronMillward** | Contributor, WiVRn | Field reports of perceptual stutter & motion sickness from real users |
| **brycehutchings** | Contributor, Microsoft OpenXR-MR | HoloLens 2 Direct3D 12 path; frame-timestamp precision; viewfinder reliability |
| **emaschino** | Microsoft MRC | HoloLens 2 performance; mixed-reality compositor calibration |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform strategy; mixed-reality advocacy & developer ecosystem |
| **Maluoi** | Maintainer, StereoKit | XR engine architecture; OpenXR backend; performance optimization |
| **🆕 Daniel4144** | Contributor, MixedReality-WebRTC | Locatable camera & projection-matrix tracking; MR rendering pipelines |
| **🆕 fiban-havok** | Reporter, MixedReality-WebRTC | H.264 encoder blockiness on HoloLens 2 — perceptual quality vs. latency tradeoffs |
| **🆕 jameszhong2008** | Issue author, MixedReality-WebRTC #157 | First-hand AEC failure in MR — acoustic presence breakdown |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### Key Topics

1. **Head-Related Transfer Functions (HRTFs)** — how the shape of your ears filters sound to give you elevation and front-back cues. Why generic HRTFs don't work for everyone.
2. **Ambisonics & Higher-Order Ambisonics (HOA)** — the mathematics of encoding 3D sound fields. FOA vs. HOA tradeoffs for real-time rendering.
3. **🔥 NEW: The glTF audio extension frontier** — KhronosGroup/glTF now has *three* active audio extension proposals: `KHR_audio_emitter` (#2137, 58 comments), `KHR_audio_graph` (#2632), and `KHR_audio_environment` (#2631). These would define how spatial audio sources, audio graphs, and acoustic environments are encoded in 3D asset pipelines. This is the closest thing to a spatial audio standard for the web.
4. **🔥 NEW: Layered audio architecture proposal** — Issue #2561 (rudybear): proposes a composing architecture where `KHR_audio_emitter` + `KHR_audio_graph` + `KHR_audio_environment` form a complete spatial audio stack inside glTF. This is the most serious attempt to standardize spatial audio for 3D content delivery.
5. **🔥 NEW: Synchronized immersive video + audio in glTF** — Issue #2506 (Ben Erwin / powersimple): calls for timeline metadata, stereo/volumetric video types, and AV sync in glTF. This bridges spatial audio and spatial video — the "immersive media" standard we've been waiting for.
6. **The WebXR gap** — the WebXR Device API spec defines visual immersion but has **no spatial audio API**. Spaces sound like a hack. Chrome's Omnitone partial implementation vs. full native HRTF pipelines.
7. **Personalized HRTFs** — modeling individual ear geometry. The Iowa auditory dataset, NIIP dual-ridge method, and the unsolved problem of real-time personalization on consumer hardware.
8. **Spatial presence vs. localization** — can you feel "present" in a space without accurate externalization? The ventriloquism effect and its XR implications.
9. **Multi-device synchronization** — freeman-jiang/beatsync: clock sync precision across correlated haptic, audio, and visual events for presence maintenance.
10. **Accessibility & spatial audio** — Sound of Vision, leading SMEs and researches for individuals with low vision / blindness, and Amelia Eckard's Apple Vision Pro research.
11. **Spatial audio rendering on constrained devices** — avnerus's Mach1 Studios approach: real-time binaural rendering on mobile/standalone hardware.

### The Hot Debate

> **The WebXR spec is visual-only for spatial audio — and that's a design failure.** Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. The immersive-web working group has debated spatial audio extensions for years with no consensus. Meanwhile, native platforms (Apple, Meta) ship proprietary spatial audio that developers can't access or extend. The web is the only platform that should be truly open for spatial audio — and it's falling behind.

> **🔥 NEW: glTF is becoming the accidental spatial audio standard.** With three concurrent audio extension proposals (`KHR_audio_emitter`, `KHR_audio_graph`, `KHR_audio_environment`), glTF is closer than WebXR to defining a complete spatial audio pipeline for 3D content. The question is whether the W3C Immersive Web group will collaborate with Khronos or let glTF become the de facto standard while WebXR remains visual-only.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leomccormack** | Creator, Spatial_Audio_Framework | Ambisonics, HRTFs, cross-platform spatial audio algorithms in C |
| **crlandsc** | Contributor, Spatial_Audio_Framework | Spatialization algorithms; real-time rendering |
| **ali-vosoughi** | Contributor, Spatial_Audio_Framework | Ambisonic processing & signal flow |
| **jacobhollebon** | Contributor, Spatial_Audio_Framework | Spatial audio architecture & design |
| **BinWang28** | Maintainer, audio-ai-hub | HRTF research; spatial speech perception; personalized HRTFs |
| **edurnebernal** | Researcher, audio-visual perception | Audio-visual integration in VR; ventriloquism effect |
| **orighst (Boris Smus)** | Web audio engineer, Google/omnitone | Browser-based binaural rendering; FOA/HOA |
| **brandonpjones (Brandon Jones)** | Web audio engineer, Google/omnitone | Web Audio API spatial rendering; ambisonic codecs |
| **jkarmer (Julius Kammerl)** | Web audio engineer, Google/omnitone | Real-time spatial audio in web browsers |
| **freeman-jiang** | Creator, beatsync | Multi-device spatial audio synchronization; clock sync precision |
| **ameliaeckard** | Researcher, Apple Vision Pro spatial audio | Accessibility via spatial audio; indoor navigation for visually impaired |
| **Avnerus** | Developer, Mach1 Studios | Binaural rendering server; real-time HRTF on constrained devices |
| **🆕 rudybear** | glTF audio extension author | `KHR_audio_graph` + `KHR_audio_environment` — the layered spatial audio architecture |
| **🆕 robertlong** | glTF KHR_audio_emitter PR author | Spatial audio emitter extension — how sound sources are positioned in 3D glTF scenes |
| **🆕 Ben Erwin (powersimple)** | glTF immersive media advocate | Synchronized video+audio in glTF; SIGGRAPH 2025/2026 roadmap |
| **🆕 najadojo** | MSFT_glTF_audio_emitter author | Microsoft's proprietary audio emitter extension — competing with Khronos |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### Key Topics

1. **The MR interface stack** — from hand tracking (Metric Theory, Ultraleap) to gaze anchoring, temporal stabilization, and the illusion of a stable cursor in mid-air.
2. **Hologram drift & registration** — MixedRealityCompanionKit #228: SpectatorView calibration that works once and never again. Why persistent hologram registration is unsolved outside lab conditions.
3. **🔥 NEW: ARCore depth sensing & pointcloud** — google-ar/arcore-android-sdk #120 (357 comments, 25 👍): a 6-year-old feature request for dense pointcloud from depth sensors. This is fundamental to MR — you can't anchor holograms to real surfaces without accurate depth. The Tango-to-ARCore transition left a gap in depth-first AR.
4. **🔥 NEW: ARCore device support fragmentation** — ARCore #89 (589 comments!): the longest-running open issue in the repo. Device support requests span 8+ years. This isn't just a feature request — it's a *perceptual accessibility* problem. If your AR app only works on 5 devices, you're excluding the majority of users from spatial computing.
5. **🔥 NEW: ARCore camera control** — ARCore #153 (76 comments): no API for flashlight, auto-exposure, or torch control. For AR to work in varied lighting, you need programmatic camera control. Without it, the perceptual experience is at the mercy of the OS camera app.
6. **Wayfinding in MR** — cognitive load of spatial navigation when the display medium is yourself. Audio-based wayfinding as a complementary channel.
7. **Non-visual XR interfaces** — the WebXR Device API defines `viewer` and `local` reference spaces but treats haptics, spatial audio, and biometric sensors as afterthoughts. The spec is fundamentally visual-centric.
8. **The "posure" problem** — if your virtual body is wrong, your spatial judgment is wrong. Avatar fidelity and its downstream effects on presence and spatial reasoning.
9. **Hand tracking vs. controllers** — ergonomic research on pinch, grab, and pointing interactions. The missing middle ground between raw hand tracking and 6-DoF controllers.
10. **Architectural implications** — StereoKit's OpenXR + WebXR dual backend, and what it means for cross-platform MR interface design.
11. **AR.js 2→3 transition** — the creator `jeromeetienne` discusses the community-driven rebuild and what it means for the future of web-based spatial interfaces.

### The Hot Debate

> **Is the WebXR spec blind to non-visual perception?** The spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. You can "see" a virtual object in WebXR but you cannot reliably "hear" it or "feel" it. For MR — where the physical world is the backdrop — this is a fundamental architectural gap that no working group has seriously addressed.

> **🔥 NEW: ARCore's depth-sensing gap is a perceptual crisis.** Issue #120 (357 comments, 6 years old) reveals that the dominant Android AR platform still can't deliver dense depth pointclouds from consumer hardware. Without accurate surface geometry, MR holograms float in mid-air with no physical grounding. This isn't a feature request — it's the missing foundation of spatial computing on the most widely deployed AR platform.

> **🔥 NEW: Device fragmentation is a perceptual accessibility issue.** ARCore #89 (589 comments!) isn't just about adding support — it's about whether spatial computing is available to everyone or only to owners of the latest flagship devices. The 8-year-old open issue is a standing indictment of the industry's prioritization of new hardware over perceptual inclusivity.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k⭐) | Web AR pioneer; marker-based & geospatial AR; the AR.js 2→3 transition |
| **hiukim** | Creator, MindAR (2.7k⭐) | On-device image/face tracking with TensorFlow.js; production-ready AR |
| **maluoi** | Maintainer, StereoKit | XR engine architecture; OpenXR + WebXR dual-backend design |
| **davidjscott** | StereoKit contributor | MR interaction patterns; spatial UI design systems |
| **bkonyves** | Google, AR/VR engineering | Google's spatial computing platform vision; reference space design |
| **ricardmarco** | MR interaction researcher | Hand tracking ergonomics; gesture taxonomy for MR |
| **Oliver** | Apple visionOS | visionOS spatial interface paradigms; Optic ID & biometric XR |
| **🆕 SimonScholl** | ARCore pointcloud advocate (#120) | Depth sensing for AR; Tango-to-ARCore transition; dense surface mapping |
| **🆕 inio** | ARCore device support tracker (#89) | Longest-running ARCore issue — device fragmentation & perceptual access |
| **🆕 jpeltone** | ARCore rear-camera faces (#714) | Augmented Faces on rear-facing cameras — new interaction paradigms |
| **🆕 ROBYER1** | ARCore body pose tracking (#1275) | Human body pose tracking for MR interfaces |

---

## Cross-Episode Themes

| Theme | Episode 1 | Episode 2 | Episode 3 |
|---|---|---|---|
| The brain as final arbiter of reality | ✅ (temporal vs. average latency) | ✅ (audio presence paradox) | ✅ (visual-centric spec gap) |
| Open-source vs. proprietary stacks | ✅ (open VR latency tools) | ✅ (open spatial audio frameworks) | ✅ (open MR toolkits) |
| The web platform as the egalitarian frontier | ✅ (Web AR, AR.js) | ✅ (Omnitone vs. native) | ✅ (WebXR spec gap) |
| Regulatory & ethics (FDA, accessibility) | ✅ (motion sickness liability) | ✅ (accessibility for impaired) | ✅ (biometric data in XR) |
| 🆕 Perceptual access & fragmentation | ✅ (device latency variability) | ✅ (HRTF personalization gap) | ✅ (ARCore device support, 589 comments) |
| 🆕 Standards convergence (glTF ↔ WebXR) | — | ✅ (KHR_audio_* extensions) | ✅ (WebXR spec gaps) |

---

## Repository Contributions Guide

1. **Pick an episode issue** — #13 (E1), #14 (E2), or #15 (E3) for research & outreach.
2. **Add issue links** from the GitHub repos above as comments on the relevant issue.
3. **Tag potential guests** — see `GUEST_DIRECTORY.md` for full contact and research context.
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates.

---

## Key GitHub Issues to Track (Live Audit)

| Repo | Issue | Topic | Comments | Relevance |
|---|---|---|---|---|
| `google-ar/arcore-android-sdk` | [#89](https://github.com/google-ar/arcore-android-sdk/issues/89) | Device support requests | 589 | E3 — fragmentation = perceptual inaccessibility |
| `google-ar/arcore-android-sdk` | [#120](https://github.com/google-ar/arcore-android-sdk/issues/120) | Dense pointcloud from depth | 357 (25👍) | E3 — MR surface anchoring foundation |
| `google-ar/arcore-android-sdk` | [#153](https://github.com/google-ar/arcore-android-sdk/issues/153) | Camera control (flashlight/auto-exposure) | 76 | E3 — lighting-aware AR perception |
| `google-ar/arcore-android-sdk` | [#1275](https://github.com/google-ar/arcore-android-sdk/issues/1275) | Body pose tracking request | 21 | E3 — full-body MR interfaces |
| `microsoft/MixedReality-WebRTC` | [#157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | Acoustic echo cancellation broken | 17 | E1 — AEC failure = spatial audio collapse |
| `microsoft/MixedReality-WebRTC` | [#83](https://github.com/microsoft/MixedReality-WebRTC/issues/83) | Locatable camera projection matrix | 37 | E1 — MR rendering pipeline |
| `microsoft/MixedReality-WebRTC` | [#153](https://github.com/microsoft/MixedReality-WebRTC/issues/153) | Blocky H.264 on HoloLens 2 | 32 | E1 — perceptual quality vs. latency |
| `KhronosGroup/glTF` | [#2137](https://github.com/KhronosGroup/glTF/pull/2137) | KHR_audio_emitter PR | 58 | E2 — spatial audio source standard |
| `KhronosGroup/glTF` | [#2561](https://github.com/KhronosGroup/glTF/issues/2561) | Layered audio architecture proposal | 2 | E2 — full spatial audio stack in glTF |
| `KhronosGroup/glTF` | [#2632](https://github.com/KhronosGroup/glTF/pull/2632) | KHR_audio_graph PR | 2 | E2 — audio graph standard |
| `KhronosGroup/glTF` | [#2631](https://github.com/KhronosGroup/glTF/pull/2631) | KHR_audio_environment PR | 1 | E2 — acoustic environment standard |
| `KhronosGroup/glTF` | [#2506](https://github.com/KhronosGroup/glTF/issues/2506) | Synchronized immersive video+audio | 2 | E2 — AV sync for XR |
| `microsoft/MixedRealityToolkit-Unity` | [#11848](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11848) | Microphone stream bug | 0 | E1 — audio input for MR |

---

*Last research sync: 2026-09-17. See `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md` for the full continuously updated audit.*
