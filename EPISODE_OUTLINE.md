# 🎙️ The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> **Research sync: 2026-09-18** — Updated with fresh GitHub audit findings from ARCore, MixedReality-WebRTC, glTF, and ARKit-CoreLocation.

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
| AR SDKs | `google-ar/arcore-android-sdk` (5.2k ⭐), `google-ar/arcore-unity-sdk` (1.4k ⭐), `Unity-Technologies/arfoundation-samples` (3.4k ⭐), `olucurious/Awesome-ARkit` (8.0k ⭐), `AndrewHartAR/ARKit-CoreLocation` (5.5k ⭐) |
| 3D Assets & Standards | `KhronosGroup/glTF` (10k ⭐+) — audio emitter extensions, spatial video proposals |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **Temporal irregularity vs. average latency** — WiVRn #282 (40 comments) | [WiVRn #282](https://github.com/xytovl/wivrn/issues/282) | 🔴 Paradigm shift: stutter = irregularity, not depth |
| **"Missing" latency in VR streaming** — ALVR #334 | [ALVR #334](https://github.com/ beautiesamongus/ALVR/issues/334) | 🔴 33.6ms unaccounted; 30-50% underreporting |
| **Acoustic echo cancellation broken in MR** — MixedReality-WebRTC #157 | [MR-WebRTC #157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | 🔴 AEC failure = spatial audio collapse |
| **ARCore session crash on Samsung** — ARCore #1762 | [ARCore #1762](https://github.com/google-ar/arcore-android-sdk/issues/1762) | 🟡 Perceptual trust destroyed by session resume crash |
| **Spatial tracking failure on Xiaomi** — ARCore #1636 | [ARCore #1636](https://github.com/google-ar/arcore-android-sdk/issues/1636) | 🟡 Real-world tracking reliability gap |
| **Hologram calibration instability** — MixedRealityCompanionKit #228 | [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | 🟡 SpectatorView calibration that works once never again |
| **Web AR tracking failure** — AR.js #826, #825 | [AR.js #826](https://github.com/AR-js-org/AR.js/issues/826) | 🟡 First perceptual bottleneck on the web |

### Key Topics
1. The motion-to-photon pipeline — sensor → predict → render → encode → transport → decode → display. Every stage injects latency.
2. The "20 ms rule" and vestibular-visual conflict — why a few milliseconds of lag translate directly into motion sickness.
3. Temporal irregularity vs. average latency — the WiVRn #282 paradigm shift.
4. "Missing" latency in VR streaming — ALVR #334's 33.6ms underreporting finding.
5. Acoustic echo cancellation failure — MixedReality-WebRTC #157: AEC broken in OpenXR MR stacks.
6. ARCore session stability & crash latency — ARCore #1762: Samsung SM-X520 crash after Play Services update.
7. Spatial tracking failure on devices — ARCore #1636: Xiaomi 13T tracking failure.
8. Hologram calibration instability — MixedRealityCompanionKit #228: SpectatorView calibration drift.
9. Web AR tracking failure — AR.js #826, #825: real-time tracking as first perceptual bottleneck.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leinardi** | Maintainer, SteamVR-for-Linux | Open-source VR latency debugging |
| **jd-3d** | Developer, ALVR | VR streaming stack forensics; "missing latency" discovery |
| **xytovl** | Maintainer, WiVRn | OpenXR streaming; packet-timing & pacing |
| **AaronMillward** | Contributor, WiVRn | Field reports of perceptual stutter & sickness |
| **brycehutchings** | Contributor, Microsoft OpenXR-MR | HoloLens 2 Direct3D 12; frame-timestamp precision |
| **emaschino** | Microsoft MRC | HoloLens 2 performance; compositor calibration |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform strategy |
| **Maluoi** | Maintainer, StereoKit | XR engine architecture; OpenXR backend |
| **🆕 Daniel4144** | Contributor, MixedReality-WebRTC | Locatable camera & projection-matrix tracking |
| **🆕 fiban-havok** | Reporter, MixedReality-WebRTC | H.264 blockiness on HoloLens 2 |
| **🆕 jameszhong2008** | Issue author, MixedReality-WebRTC #157 | First-hand AEC failure experience |
| **🆕 inio** | ARCore issue #1762 reporter | Samsung session crash & fragmentation |
| **🆕 Bastel-Bodo** | ARCore issue #1636 reporter | Xiaomi spatial tracking failure |

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets are wrong — we need to stabilize frame delivery instead.

> **🔥 Acoustic echo cancellation is a spatial-perception problem.** MixedReality-WebRTC #157 reveals that AEC — critical for spatial audio presence — is fundamentally broken in current MR stacks. Without echo cancellation, room acoustics contaminate the spatial audio model. This isn't an audio quality issue; it's a *perceptual calibration* failure.

> **🔥 Session crashes are perceptual events.** ARCore #1762 and #1636 aren't just bugs — they're *perceptual access* failures. When the system crashes or can't track, the brain's spatial model is violently interrupted.

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### Core Question
Why is the WebXR spec visual-only for spatial audio? What does HRTF mean for presence?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **KHR_audio_emitter PR** — glTF #2137 (58 comments) | [glTF #2137](https://github.com/KhronosGroup/glTF/pull/2137) | 🔴 Spatial audio source standard for 3D assets |
| **Layered audio architecture** — glTF #2561 (rudybear) | [glTF #2561](https://github.com/KhronosGroup/glTF/issues/2561) | 🔴 Full spatial audio stack in glTF |
| **KHR_audio_graph PR** — glTF #2632 | [glTF #2632](https://github.com/KhronosGroup/glTF/pull/2632) | 🟡 Audio graph standard |
| **KHR_audio_environment PR** — glTF #2631 | [glTF #2631](https://github.com/KhronosGroup/glTF/pull/2631) | 🟡 Acoustic environment standard |
| **Synchronized immersive video+audio** — glTF #2506 | [glTF #2506](https://github.com/KhronosGroup/glTF/issues/2506) | 🟡 AV sync for XR |
| **Locatable camera projection matrix** — MR-WebRTC #83 (37 comments) | [MR-WebRTC #83](https://github.com/microsoft/MixedReality-WebRTC/issues/83) | 🔴 MR rendering pipeline constraint |
| **Blocky H.264 on HoloLens 2** — MR-WebRTC #153 (32 comments) | [MR-WebRTC #153](https://github.com/microsoft/MixedReality-WebRTC/issues/153) | 🔴 Perceptual quality vs. latency |
| **MR Speaker Viewfinder reliability** — MRTK / MixedRealityCompanionKit | MRC #228 | 🟡 Spectator view compositor quality |

### Key Topics
1. Head-Related Transfer Functions (HRTFs) — how ear shape filters sound for elevation and front-back cues.
2. Ambisonics & Higher-Order Ambisonics (HOA) — mathematics of encoding 3D sound fields.
3. The glTF audio extension frontier — three concurrent proposals: KHR_audio_emitter, KHR_audio_graph, KHR_audio_environment.
4. Layered audio architecture — rudybear's proposal for a complete spatial audio stack inside glTF.
5. Synchronized immersive video + audio — glTF #2506: timeline metadata, volumetric video, AV sync.
6. The WebXR gap — no spatial audio API in the spec. Chrome's Omnitone vs. native HRTF pipelines.
7. Personalized HRTFs — modeling individual ear geometry; unsolved on consumer hardware.
8. Spatial presence vs. localization — ventriloquism effect and XR implications.
9. Multi-device synchronization — freeman-jiang/beatsync: clock sync for presence.
10. ARKit spatial audio & environment mapping — ARKit-CoreLocation (5.5k ⭐).
11. Spatial audio can't be separated from spatial rendering — MR-WebRTC #83, #153, #157 pattern.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leomccormack** | Creator, Spatial_Audio_Framework | Ambisonics, HRTFs, cross-platform algorithms |
| **crlandsc** | Contributor, Spatial_Audio_Framework | Spatialization algorithms; real-time rendering |
| **ali-vosoughi** | Contributor, Spatial_Audio_Framework | Ambisonic processing & signal flow |
| **jacobhollebon** | Contributor, Spatial_Audio_Framework | Spatial audio architecture & design |
| **BinWang28** | Maintainer, audio-ai-hub | HRTF research; personalized HRTFs |
| **edurnebernal** | Researcher, audio-visual perception | Audio-visual integration; ventriloquism effect |
| **orighst (Boris Smus)** | Web audio engineer, Google/omnitone | Browser-based binaural rendering |
| **brandonpjones** | Web audio engineer, Google/omnitone | Web Audio API spatial rendering |
| **freeman-jiang** | Creator, beatsync | Multi-device spatial audio sync |
| **ameliaeckard** | Researcher, Apple Vision Pro spatial audio | Accessibility via spatial audio |
| **Avnerus** | Developer, Mach1 Studios | Binaural rendering on constrained devices |
| **🆕 rudybear** | glTF audio extension author | KHR_audio_graph + KHR_audio_environment |
| **🆕 robertlong** | glTF KHR_audio_emitter PR author | Spatial audio emitter extension |
| **🆕 Ben Erwin (powersimple)** | glTF immersive media advocate | Synchronized video+audio; SIGGRAPH roadmap |
| **🆕 najadojo** | MSFT_glTF_audio_emitter author | Microsoft's proprietary audio emitter |
| **🆕 Andrew Hart** | ARKit-CoreLocation (5.5k ⭐) | AR + GPS-scale spatial data |
| **🆕 Daniel4144** | MixedReality-WebRTC | MR audio-visual pipeline coupling |

### The Hot Debate

> **The WebXR spec is visual-only for spatial audio — and that's a design failure.** Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. The immersive-web working group has debated spatial audio extensions for years with no consensus. Meanwhile, native platforms ship proprietary spatial audio developers can't access.

> **🔥 glTF is becoming the accidental spatial audio standard.** With three concurrent audio extension proposals, glTF is closer than WebXR to defining a complete spatial audio pipeline. Will the W3C collaborate with Khronos, or let glTF become de facto while WebXR remains visual-only?

> **🔥 Spatial audio can't be separated from spatial rendering.** MR-WebRTC issues #83, #153, #157 form a pattern: the audio pipeline is constrained by the visual rendering pipeline. You can't fix spatial audio without fixing the entire MR compositor.

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### Core Question
Is the WebXR spec blind to non-visual perception? Can MR interfaces survive without depth, camera control, and device parity?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **Dense pointcloud from depth sensors** — ARCore #120 (357 comments, 25 👍) | [ARCore #120](https://github.com/google-ar/arcore-android-sdk/issues/120) | 🔴 6-year-old request; MR surface anchoring foundation missing |
| **Device support requests (8+ years!)** — ARCore #89 (589 comments) | [ARCore #89](https://github.com/google-ar/arcore-android-sdk/issues/89) | 🔴 Perceptual accessibility crisis |
| **Camera control (flashlight/auto-exposure)** — ARCore #153 (76 comments) | [ARCore #153](https://github.com/google-ar/arcore-android-sdk/issues/153) | 🔴 Camera = perceptual bottleneck |
| **Body pose tracking request** — ARCore #1275 | [ARCore #1275](https://github.com/google-ar/arcore-android-sdk/issues/1275) | 🟡 Full-body MR interfaces |
| **Augmented Faces on rear camera** — ARCore #714 | [ARCore #714](https://github.com/google-ar/arcore-android-sdk/issues/714) | 🟡 New camera paradigms |
| **ARKit-CoreLocation spatial scale** — 5.5k ⭐ | [ARKit-CoreLocation](https://github.com/AndrewHartAR/ARKit-CoreLocation) | 🟡 Indoor-outdoor navigation bridge |
| **SpectatorView calibration instability** — MRC #228 | [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | 🟡 Hologram drift & registration |

### Key Topics
1. The MR interface stack — hand tracking, gaze anchoring, temporal stabilization.
2. Hologram drift & registration — MixedRealityCompanionKit #228: calibration that works once and never again.
3. ARCore depth sensing & pointcloud — #120: 6-year-old request still unfilled. MR holograms float without surface geometry.
4. ARCore device support fragmentation — #89 (589 comments!): perceptual accessibility crisis.
5. ARCore camera control — #153: no flashlight/auto-exposure API. Camera is the perceptual bottleneck.
6. ARCore body pose tracking — #1275: full-body MR interfaces still unsupported.
7. ARKit front & rear camera paradigms — #714: rear-facing AR faces.
8. ARKit-CoreLocation & spatial scale — Andrew Hart's 5.5k ⭐ repo bridges indoor AR and outdoor navigation.
9. Wayfinding in MR — cognitive load of spatial navigation when the display medium is yourself.
10. Non-visual XR interfaces — WebXR spec treats haptics, spatial audio, and biometrics as afterthoughts.
11. Hand tracking vs. controllers — the missing middle ground.
12. MR Speaker Viewfinder reliability — H.264 blockiness on HoloLens 2 impacts spectator experience.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k⭐) | Web AR pioneer; AR.js 2→3 transition |
| **hiukim** | Creator, MindAR (2.7k⭐) | On-device image/face tracking |
| **maluoi** | Maintainer, StereoKit | XR engine architecture; OpenXR + WebXR dual-backend |
| **davidjscott** | StereoKit contributor | MR interaction patterns; spatial UI design |
| **bkonyves** | Google, AR/VR engineering | Google's spatial computing platform vision |
| **ricardmarco** | MR interaction researcher | Hand tracking ergonomics; gesture taxonomy |
| **Oliver** | Apple visionOS | visionOS spatial interface paradigms |
| **🆕 SimonScholl** | ARCore pointcloud advocate (#120) | Depth sensing; Tango-to-ARCore transition |
| **🆕 inio** | ARCore device support tracker (#89) | 8-year fragmentation battle |
| **🆕 jpeltone** | ARCore rear-camera faces (#714) | Augmented Faces on rear cameras |
| **🆕 ROBYER1** | ARCore body pose tracking (#1275) | Human body pose tracking for MR |
| **🆕 Andrew Hart** | ARKit-CoreLocation (5.5k ⭐) | AR + GPS-scale spatial data |
| **🆕 fabio914** | RealityMixer (807 ⭐) | Mixed Reality app for iOS |

### The Hot Debate

> **Is the WebXR spec blind to non-visual perception?** The spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. You can "see" a virtual object in WebXR but you cannot reliably "hear" it or "feel" it. For MR, this is a fundamental architectural gap.

> **🔥 ARCore's depth-sensing gap is a perceptual crisis.** Issue #120 (357 comments, 6 years old) reveals the dominant Android AR platform still can't deliver dense depth pointclouds. Without surface geometry, MR holograms float in mid-air with no physical grounding.

> **🔥 Device fragmentation is a perceptual accessibility issue.** ARCore #89 (589 comments!) isn't just about adding support — it's about whether spatial computing is available to everyone or only flagship device owners.

> **🔥 The camera is the perceptual bottleneck.** ARCore #153 (no flashlight/auto-exposure API) reveals that the camera subsystem limits perceptual quality. Without programmatic camera control, AR is at the mercy of the OS camera app.

---

## Cross-Episode Themes

| Theme | Episode 1 | Episode 2 | Episode 3 |
|---|---|---|---|
| The brain as final arbiter of reality | ✅ (temporal vs. average latency) | ✅ (audio presence paradox) | ✅ (visual-centric spec gap) |
| Open-source vs. proprietary stacks | ✅ (open VR latency tools) | ✅ (open spatial audio frameworks) | ✅ (open MR toolkits) |
| The web platform as the egalitarian frontier | ✅ (Web AR, AR.js) | ✅ (Omnitone vs. native) | ✅ (WebXR spec gap + ARCore fragmentation) |
| Regulatory & ethics (FDA, accessibility) | ✅ (motion sickness liability) | ✅ (accessibility for impaired) | ✅ (device fragmentation = access gap) |
| 🆕 Perceptual access & fragmentation | ✅ (device latency variability) | ✅ (HRTF personalization gap) | ✅ (ARCore #89, 589 comments) |
| 🆕 Standards convergence (glTF ↔ WebXR) | — | ✅ (KHR_audio_* extensions) | ✅ (WebXR spec gaps) |
| 🆕 Camera-as-bottleneck | ✅ (session stability) | ✅ (audio-visual coupling) | ✅ (flashlight/auto-exposure gap) |

---

## GitHub Issue Audit — Live Hot Debates (2026-09-18)

| Repo | Issue | Topic | Comments | Episode |
|---|---|---|---|---|
| `google-ar/arcore-android-sdk` | [#89](https://github.com/google-ar/arcore-android-sdk/issues/89) | Device support requests (8+ years!) | 589 | E3 — fragmentation = perceptual inaccessibility |
| `google-ar/arcore-android-sdk` | [#120](https://github.com/google-ar/arcore-android-sdk/issues/120) | Dense pointcloud from depth sensors | 357 (25👍) | E3 — MR surface anchoring foundation |
| `google-ar/arcore-android-sdk` | [#153](https://github.com/google-ar/arcore-android-sdk/issues/153) | Camera control (flashlight/auto-exposure) | 76 | E3 — lighting-aware AR perception |
| `google-ar/arcore-android-sdk` | [#1275](https://github.com/google-ar/arcore-android-sdk/issues/1275) | Body pose tracking request | 21 | E3 — full-body MR interfaces |
| `google-ar/arcore-android-sdk` | [#714](https://github.com/google-ar/arcore-android-sdk/issues/714) | Augmented Faces on rear camera | 25 | E3 — new camera paradigms |
| `google-ar/arcore-android-sdk` | [#1762](https://github.com/google-ar/arcore-android-sdk/issues/1762) | Session crash on Samsung after update | 20 | E1 — session stability = perceptual trust |
| `google-ar/arcore-android-sdk` | [#1636](https://github.com/google-ar/arcore-android-sdk/issues/1636) | Spatial tracking failure on Xiaomi | 15 | E1 — real-world tracking reliability |
| `microsoft/MixedReality-WebRTC` | [#157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | Acoustic echo cancellation broken | 17 | E1 — AEC failure = spatial audio collapse |
| `microsoft/MixedReality-WebRTC` | [#83](https://github.com/microsoft/MixedReality-WebRTC/issues/83) | Locatable camera projection matrix | 37 | E1/E2 — MR rendering pipeline |
| `microsoft/MixedReality-WebRTC` | [#153](https://github.com/microsoft/MixedReality-WebRTC/issues/153) | Blocky H.264 on HoloLens 2 | 32 | E1/E3 — perceptual quality vs. latency |
| `microsoft/MixedRealityToolkit-Unity` | [#11848](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11848) | Microphone stream bug | 0 | E1 — audio input for MR |
| `microsoft/MixedRealityCompanionKit` | [#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | SpectatorView calibration instability | 19 | E1/E3 — hologram drift & registration |
| `KhronosGroup/glTF` | [#2137](https://github.com/KhronosGroup/glTF/pull/2137) | KHR_audio_emitter PR | 58 | E2 — spatial audio source standard |
| `KhronosGroup/glTF` | [#2561](https://github.com/KhronosGroup/glTF/issues/2561) | Layered audio architecture proposal | 2 | E2 — full spatial audio stack in glTF |
| `KhronosGroup/glTF` | [#2632](https://github.com/KhronosGroup/glTF/pull/2632) | KHR_audio_graph PR | 2 | E2 — audio graph standard |
| `KhronosGroup/glTF` | [#2631](https://github.com/KhronosGroup/glTF/pull/2631) | KHR_audio_environment PR | 1 | E2 — acoustic environment standard |
| `KhronosGroup/glTF` | [#2506](https://github.com/KhronosGroup/glTF/issues/2506) | Synchronized immersive video+audio | 2 | E2 — AV sync for XR |
| `AR-js-org/AR.js` | [#826](https://github.com/AR-js-org/AR.js/issues/826) | Broken image tracking | — | E1 — Web AR tracking bottleneck |
| `AR-js-org/AR.js` | [#825](https://github.com/AR-js-org/AR.js/issues/825) | Location-based AR failing | — | E1 — Web AR geospatial failure |

---

## Repository Contributions Guide

1. **Pick an episode issue** — #52 (E1), #53 (E2), or #54 (E3) for research & outreach.
2. **Add issue links** from the GitHub repos above as comments on the relevant issue.
3. **Tag potential guests** — see `GUEST_DIRECTORY.md` for full contact and research context.
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates.

---

*Last research sync: 2026-09-18. See `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md` for the full continuously updated audit.*
