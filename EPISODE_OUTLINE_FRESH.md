# 🎙️ The Future of Human Perception — Fresh Episode Outline

> **Research sync: 2026-09-18** — Consolidated from GitHub audit of 15+ active AR/MR/Spatial Computing repositories, 20+ open issues, and 15+ identified contributor/guest targets.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

### Research Backbone — Most Active GitHub Communities

| Domain | Repo | Stars | Key Detail |
|---|---|---|---|
| Web AR | `AR-js-org/AR.js` | 15.8k ⭐ | Marker + Location + Image tracking; MIT; now community-governed org |
| Web AR | `hiukim/mind-ar-js` | 2.7k ⭐ | Image + Face tracking via TensorFlow.js/WebGL; pure JS; actively maintained by 1 person |
| Web AR | `jeeliz/jeelizFaceFilter` | 2.9k ⭐ | Lightweight WebGL face tracking + AR face filters |
| VR/AR Engine | `google/lullaby` | 1.2k ⭐ | C++ ECS architecture; spatial audio; used by Google VR Home, YouTube, Earth |
| 3D Standard | `KhronosGroup/glTF` | 10k ⭐+ | **Three concurrent spatial audio extension proposals** (KHR_audio_emitter, KHR_audio_graph, KHR_audio_environment) |
| WebXR Spec | `immersive-web/webxr` | 3.1k ⭐ | **Issue #815**: "Spec language precludes non-visual uses" — 41 comments, a11y-tracker label |
| WebXR Samples | `immersive-web/model-element` | — | **Issue #55**: "Is it time for browsers to standardize 3D rendering?" — 11 comments |
| MR Toolkit | `microsoft/MixedRealityToolkit-Unity` | 6.1k ⭐ | HoloLens 2 + OpenXR;.audio + haptics stacks |
| MR WebRTC | `microsoft/MixedReality-WebRTC` | 944 ⭐ | **Issue #157**: AEC broken in MR; **Issue #83**: locatable camera projection; **Issue #153**: H.264 blockiness on HoloLens 2 |
| MR Companion | `microsoft/MixedRealityCompanionKit` | — | **Issue #228**: SpectatorView calibration instability — hologram drift |
| AR SDK | `google-ar/arcore-android-sdk` | 5.2k ⭐ | **Issue #89**: 589 comments, 8+ year device support battle; **#120**: dense pointcloud (357 comments, 6 yrs); **#153**: camera control; **#1762**: Samsung crash; **#1636**: Xiaomi tracking fail |
| AR Kit | `olucurious/Awesome-ARkit` | 8.0k ⭐ | Curated ARKit resource list |
| AR+GPS | `AndrewHartAR/ARKit-CoreLocation` | 5.5k ⭐ | Bridges indoor AR and outdoor navigation — spatial scale problem |
| Spatial Audio | `GoogleChrome/omnitone` | 911 ⭐ | Browser binaural rendering; FOA-based; no full HRTF in WebXR spec |
| Spatial Audio | `leomccormack/Spatial_Audio_Framework` | 748 ⭐ | Ambisonics + HRTF cross-platform; open-source spatialization |
| Spatial Audio | `google/spatial-media` | 2.1k ⭐ | Spatial video + audio capture/reference |
| Spatial Audio | `freeman-jiang/beatsync` | 3.2k ⭐ | Multi-device clock sync for spatial presence |
| MR App | `fabio914/RealityMixer` | 807 ⭐ | Mixed Reality app for iOS; spatial compositing |
| 3D Engine | `mrdoob/three.js` | 115.6k ⭐ | WebXR rendering backbone; AR.js & MindAR both build on it |
| Web 3D | `playcanvas/engine` | 16.7k ⭐ | Open-source 3D engine with WebXR support |
| Web 3D | `hubs-foundation/hubs` | 2.2k ⭐ | Collaborative spatial experiences platform |
| XR Standard | `KhronosGroup/OpenXR-SDK` | 1.1k ⭐ | Open standard for XR access; spatial audio extensions pending |
| XR Dev | `microsoft/xr-development-for-beginners` | 564 ⭐ | MR development learning path |
| VisionOS | `IvanCampos/visionos-examples` | 405 ⭐ | Apple visionOS spatial interface patterns |
| Spatial Computing | `StereoKit/StereoKit` | 1.1k ⭐ | C# XR engine; OpenXR + WebXR dual-backend; spatial UI primitives |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **Temporal irregularity vs. average latency** — WiVRn #282 (40 comments) | `xytovl/wivrn` | 🔴 Paradigm shift: stutter = irregularity, not depth |
| **"Missing" latency in VR streaming** — ALVR #334 | `beautiesamongus/ALVR` | 🔴 33.6ms unaccounted; 30-50% underreporting |
| **Acoustic echo cancellation broken in MR** — MR-WebRTC #157 | `microsoft/MixedReality-WebRTC` | 🔴 AEC failure = spatial audio collapse |
| **ARCore session crash on Samsung** — ARCore #1762 | `google-ar/arcore-android-sdk` | 🟡 Perceptual trust destroyed by session resume crash |
| **Spatial tracking failure on Xiaomi** — ARCore #1636 | `google-ar/arcore-android-sdk` | 🟡 Real-world tracking reliability gap |
| **Hologram calibration instability** — MRC #228 | `microsoft/MixedRealityCompanionKit` | 🟡 SpectatorView calibration that works once never again |
| **Web AR tracking failure** — AR.js #826, #825 | `AR-js-org/AR.js` | 🟡 First perceptual bottleneck on the web |
| **MindAR KnownIssues — tracking accuracy** — MindAR #KnownIssues | `hiukim/mind-ar-js` | 🟡 CPU-intensive tracking; WebGL perf constraints on mobile |
| **Lullaby spatial audio + rendering pipeline** — google/lullaby | `google/lullaby` | 🟡 ECS architecture for spatial audio + 3D rendering coherence |

### Key Topics
1. The motion-to-photon pipeline — sensor → predict → render → encode → transport → decode → display. Every stage injects latency.
2. The "20 ms rule" and vestibular-visual conflict — why a few milliseconds of lag translate directly into motion sickness.
3. **Temporal irregularity vs. average latency** — WiVRn #282 paradigm shift: stutter is caused by frame pacing irregularity, not pipeline depth.
4. **"Missing" latency in VR streaming** — ALVR #334's 33.6ms underreporting finding.
5. **Acoustic echo cancellation failure** — MR-WebRTC #157: AEC broken in OpenXR MR stacks.
6. ARCore session stability & crash latency — #1762: Samsung SM-X520 crash after Play Services update.
7. Spatial tracking failure on devices — #1636: Xiaomi 13T tracking failure.
8. Hologram calibration instability — MRC #228: SpectatorView calibration drift.
9. Web AR tracking failure — AR.js #826, #825: real-time tracking as first perceptual bottleneck.
10. MindAR tracking accuracy — contribution plea from hiukim: CPU-intensive tracking; WebGL perf on mobile.
11. Lullaby's spatial audio + rendering coherence — ECS architecture ensuring audio-visual sync in Google's VR apps.

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
| **🆕 Daniel4144** | Contributor, MixedReality-WebRTC | Locatable camera & projection-matrix tracking; MR-WebRTC #83, #157 |
| **🆕 fiban-havok** | Reporter, MixedReality-WebRTC | H.264 blockiness on HoloLens 2; perceptual quality vs. latency |
| **🆕 jameszhong2008** | Issue author, MR-WebRTC #157 | First-hand AEC failure experience |
| **🆕 inio** | ARCore issue #1762 reporter | Samsung session crash & fragmentation |
| **🆕 Bastel-Bodo** | ARCore issue #1636 reporter | Xiaomi spatial tracking failure |
| **🆕 hiukim** | Creator, MindAR (2.7k ⭐) | Web AR tracking accuracy; TensorFlow.js WebGL perf on mobile |
| **🆕 jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR pioneer; AR.js 2→3 transition; community governance model |

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets are wrong — we need to stabilize frame delivery instead.

> **🔥 Acoustic echo cancellation is a spatial-perception problem.** MR-WebRTC #157 reveals that AEC — critical for spatial audio presence — is fundamentally broken in current MR stacks. Without echo cancellation, room acoustics contaminate the spatial audio model. This isn't an audio quality issue; it's a *perceptual calibration* failure.

> **🔥 Session crashes are perceptual events.** ARCore #1762 and #1636 aren't just bugs — they're *perceptual access* failures. When the system crashes or can't track, the brain's spatial model is violently interrupted.

> **🔥 Web AR is the first perceptual bottleneck for millions.** AR.js #826/#825 and MindAR's KnownIssues reveal that mobile web AR tracking — the most accessible MR platform — is the least reliable. The egalitarian frontier of spatial computing is also the most fragmented.

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### Core Question
Why is the WebXR spec visual-only for spatial audio? What does HRTF mean for presence?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **KHR_audio_emitter PR** — glTF #2137 (58 comments) | `KhronosGroup/glTF` | 🔴 Spatial audio source standard for 3D assets |
| **Layered audio architecture** — glTF #2561 (rudybear) | `KhronosGroup/glTF` | 🔴 Full spatial audio stack in glTF |
| **KHR_audio_graph PR** — glTF #2632 | `KhronosGroup/glTF` | 🟡 Audio graph standard |
| **KHR_audio_environment PR** — glTF #2631 | `KhronosGroup/glTF` | 🟡 Acoustic environment standard |
| **Synchronized immersive video+audio** — glTF #2506 | `KhronosGroup/glTF` | 🟡 AV sync for XR |
| **Locatable camera projection matrix** — MR-WebRTC #83 (37 comments) | `microsoft/MixedReality-WebRTC` | 🔴 MR rendering pipeline constraint; Daniel4144 |
| **Blocky H.264 on HoloLens 2** — MR-WebRTC #153 (32 comments) | `microsoft/MixedReality-WebRTC` | 🔴 Perceptual quality vs. latency; fiban-havok |
| **WebXR spec: visual-only for spatial audio** — Issue #815 | `immersive-web/webxr` | 🔴 "Spec language precludes non-visual uses" — a11y-tracker; 41 comments |
| **Browser 3D rendering standardization** — Issue #55 | `immersive-web/model-element` | 🟡 Is it time for browsers to standardize 3D rendering? |
| **glTF audio extensions: three competing proposals** | `KhronosGroup/glTF` #2137 + #2632 + #2631 | 🔴 Will Khronos unify or let glTF become de facto spatial audio standard? |

### Key Topics
1. Head-Related Transfer Functions (HRTFs) — how ear shape filters sound for elevation and front-back cues.
2. Ambisonics & Higher-Order Ambisonics (HOA) — mathematics of encoding 3D sound fields.
3. **The glTF audio extension frontier** — three concurrent proposals: KHR_audio_emitter (robertlong), KHR_audio_graph (rudybear), KHR_audio_environment (rudybear). Will Khronos unify them?
4. **Layered audio architecture** — rudybear's proposal for a complete spatial audio stack inside glTF.
5. **Synchronized immersive video + audio** — glTF #2506: timeline metadata, volumetric video, AV sync.
6. **The WebXR gap** — no spatial audio API in the spec. Issue #815: "Spec language precludes non-visual uses." Chrome's Omnitone vs. native HRTF pipelines.
7. Personalized HRTFs — modeling individual ear geometry; unsolved on consumer hardware.
8. Spatial presence vs. localization — ventriloquism effect and XR implications.
9. Multi-device synchronization — freeman-jiang/beatsync: clock sync for presence.
10. ARKit spatial audio & environment mapping — ARKit-CoreLocation (5.5k ⭐).
11. **Spatial audio can't be separated from spatial rendering** — MR-WebRTC #83, #153, #157 pattern: the audio pipeline is constrained by the visual rendering pipeline.
12. Lullaby's spatial audio engine — Google's internal C++ spatial audio system used in VR Home, YouTube VR, and Earth.

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
| **🆕 rudybear** | glTF audio extension author | KHR_audio_graph + KHR_audio_environment; layered audio architecture |
| **🆕 robertlong** | glTF KHR_audio_emitter PR author | Spatial audio emitter extension; 3D sound source standard |
| **🆕 Ben Erwin (powersimple)** | glTF immersive media advocate | Synchronized video+audio; SIGGRAPH roadmap |
| **🆕 najadojo** | MSFT_glTF_audio_emitter author | Microsoft's proprietary audio emitter approach |
| **🆕 Daniel4144** | MixedReality-WebRTC | MR audio-visual pipeline coupling; locatable camera |
| **🆕 Andrew Hart** | ARKit-CoreLocation (5.5k ⭐) | AR + GPS-scale spatial data; indoor-outdoor audio bridging |

### The Hot Debate

> **The WebXR spec is visual-only for spatial audio — and that's a design failure.** Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. The immersive-web working group has debated spatial audio extensions for years with no consensus (Issue #815, 41 comments, a11y-tracker label). Meanwhile, native platforms ship proprietary spatial audio developers can't access.

> **🔥 glTF is becoming the accidental spatial audio standard.** With three concurrent audio extension proposals (KHR_audio_emitter #2137 with 58 comments, KHR_audio_graph #2632, KHR_audio_environment #2631), glTF is closer than WebXR to defining a complete spatial audio pipeline. Will the W3C collaborate with Khronos, or let glTF become de facto while WebXR remains visual-only?

> **🔥 Spatial audio can't be separated from spatial rendering.** MR-WebRTC issues #83, #153, #157 form an unmistakable pattern: the audio pipeline is constrained by the visual rendering pipeline. You can't fix spatial audio without fixing the entire MR compositor. Daniel4144's locatable camera projection matrix work (#83, 37 comments) and fiban-havok's H.264 blockiness reports (#153, 32 comments) are two sides of the same coin.

> **🔥 The WebXR a11y gap is a perception problem.** Issue #815 ("Spec language precludes non-visual uses") isn't just about convenience — it's about whether the web platform can deliver *full sensory* XR. Without spatial audio APIs, WebXR is visually-rich but perceptually empty for audio-only or audio-primary experiences.

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### Core Question
Is the WebXR spec blind to non-visual perception? Can MR interfaces survive without depth, camera control, and device parity?

### GitHub-Sourced Hot Debates

| Debate | Source | Signal |
|---|---|---|
| **Dense pointcloud from depth sensors** — ARCore #120 (357 comments, 25 👍) | `google-ar/arcore-android-sdk` | 🔴 6-year-old request; MR surface anchoring foundation missing |
| **Device support requests (8+ years!)** — ARCore #89 (589 comments) | `google-ar/arcore-android-sdk` | 🔴 Perceptual accessibility crisis |
| **Camera control (flashlight/auto-exposure)** — ARCore #153 (76 comments) | `google-ar/arcore-android-sdk` | 🔴 Camera = perceptual bottleneck |
| **Body pose tracking request** — ARCore #1275 | `google-ar/arcore-android-sdk` | 🟡 Full-body MR interfaces |
| **Augmented Faces on rear camera** — ARCore #714 | `google-ar/arcore-android-sdk` | 🟡 New camera paradigms |
| **ARKit-CoreLocation spatial scale** — 5.5k ⭐ | `AndrewHartAR/ARKit-CoreLocation` | 🟡 Indoor-outdoor navigation bridge |
| **SpectatorView calibration instability** — MRC #228 | `microsoft/MixedRealityCompanionKit` | 🟡 Hologram drift & registration |
| **WebXR: spec blind to non-visual perception** — Issue #815 | `immersive-web/webxr` | 🔴 a11y-tracker label; 41 comments |
| **Browser 3D rendering standardization** — Issue #55 | `immersive-web/model-element` | 🟡 3D rendering as browser platform question |
| **MindAR KnownIssues — hand/body/plane tracking** — MindAR Roadmap | `hiukim/mind-ar-js` | 🟡 Individual dev asking: "Do DPUs let phones do plane tracking?" |
| **Lullaby: spatial UI widgets + animation system** — google/lullaby | `google/lullaby` | 🟡 Reticle, images, labels, buttons — MR UI primitives in C++ ECS |

### Key Topics
1. The MR interface stack — hand tracking, gaze anchoring, temporal stabilization.
2. **Hologram drift & registration** — MRC #228: calibration that works once and never again. Mixed reality fails when the virtual-world anchor loses its physical-world correspondence.
3. **ARCore depth sensing & pointcloud** — #120: 6-year-old request still unfilled (357 comments, 25 👍). Without surface geometry, MR holograms float in mid-air with no physical grounding.
4. **ARCore device support fragmentation** — #89 (589 comments!): perceptual accessibility crisis. 8+ years of device support requests.
5. **ARCore camera control** — #153: no flashlight/auto-exposure API. Camera is the perceptual bottleneck.
6. **ARCore body pose tracking** — #1275: full-body MR interfaces still unsupported.
7. **ARKit front & rear camera paradigms** — #714: rear-facing AR faces; jpeltone's proposal.
8. **ARKit-CoreLocation & spatial scale** — Andrew Hart's 5.5k ⭐ repo bridges indoor AR and outdoor navigation. ROBYER1's body pose tracking request is the human-body counterpart.
9. **Wayfinding in MR** — cognitive load of spatial navigation when the display medium is yourself.
10. **Non-visual XR interfaces** — WebXR spec treats haptics, spatial audio, and biometrics as afterthoughts. Issue #815: "Spec language precludes non-visual uses."
11. **Hand tracking vs. controllers** — the missing middle ground. MR interfaces need both precision and expressiveness.
12. **MR Speaker Viewfinder reliability** — H.264 blockiness on HoloLens 2 impacts spectator experience (fiban-havok's #153 experience).
13. **Lullaby's MR UI primitives** — reticle, images, labels, buttons, animation system. Google's internal C++ ECS provides spatial UI building blocks, but they're not publicly available.
14. **MindAR's roadmap gap** — hand tracking, body tracking, plane tracking all in roadmap but blocked by DPU/compiler constraints. The individual-dev bottleneck.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR pioneer; AR.js 2→3 transition; community governance model |
| **hiukim** | Creator, MindAR (2.7k ⭐) | On-device image/face tracking; DPU/compiler bottleneck experience; roadmap transparency |
| **maluoi** | Maintainer, StereoKit | XR engine architecture; OpenXR + WebXR dual-backend; spatial UI primitives |
| **davidjscott** | StereoKit contributor | MR interaction patterns; spatial UI design |
| **bkonyves** | Google, AR/VR engineering | Google's spatial computing platform vision |
| **ricardmarco** | MR interaction researcher | Hand tracking ergonomics; gesture taxonomy |
| **Oliver** | Apple visionOS | visionOS spatial interface paradigms |
| **🆕 SimonScholl** | ARCore pointcloud advocate (#120) | Depth sensing; Tango-to-ARCore transition; 357-comment battle |
| **🆕 inio** | ARCore device support tracker (#89) | 8-year fragmentation battle; 589-comment perceptual accessibility crisis |
| **🆕 jpeltone** | ARCore rear-camera faces (#714) | Augmented Faces on rear cameras; new camera paradigms |
| **🆕 ROBYER1** | ARCore body pose tracking (#1275) | Human body pose tracking for MR interfaces |
| **🆕 Andrew Hart** | ARKit-CoreLocation (5.5k ⭐) | AR + GPS-scale spatial data; indoor-outdoor bridging |
| **🆕 fabio914** | RealityMixer (807 ⭐) | Mixed Reality app for iOS; spatial compositing UX |
| **🆕 Daniel4144** | MixedReality-WebRTC | MR rendering pipeline; locatable camera; audio-visual coupling |
| **🆕 fiban-havok** | MR-WebRTC #153 reporter | H.264 blockiness on HoloLens 2; perceptual quality vs. latency |

### The Hot Debate

> **Is the WebXR spec blind to non-visual perception?** The spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. You can "see" a virtual object in WebXR but you cannot reliably "hear" it or "feel" it. For MR, this is a fundamental architectural gap. Issue #815 (a11y-tracker label, 41 comments) makes this explicit: "Spec language precludes non-visual uses."

> **🔥 ARCore's depth-sensing gap is a perceptual crisis.** Issue #120 (357 comments, 6 years old, 25 👍) reveals the dominant Android AR platform still can't deliver dense depth pointclouds. Without surface geometry, MR holograms float in mid-air with no physical grounding. SimonScholl's Tango-to-ARCore transition experience is the cautionary tale.

> **🔥 Device fragmentation is a perceptual accessibility issue.** ARCore #89 (589 comments!) isn't just about adding support — it's about whether spatial computing is available to everyone or only flagship device owners. inio's 8-year tracking of this issue reveals a systemic exclusion.

> **🔥 The camera is the perceptual bottleneck.** ARCore #153 (no flashlight/auto-exposure API) reveals that the camera subsystem limits perceptual quality. Without programmatic camera control, AR is at the mercy of the OS camera app. This is a *design* failure, not an oversight.

> **🔥 The individual-dev bottleneck in open-source MR.** hiukim's MindAR is the only actively maintained web AR SDK with commercial-grade features — and it's maintained by one person who explicitly says "I personally don't come from a strong computer vision background." The DPU/compiler bottleneck for hand/body/plane tracking isn't just a technical problem — it's a sustainability problem for open-source MR.

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
| 🆔 Individual-dev sustainability | ✅ (ipherlering ecosystem) | ✅ (MindAR roadmap) | ✅ (AR.js org transition) |

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
| `microsoft/MixedRealityCompanionKit` | [#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | SpectatorView calibration instability | 19 | E1/E3 — hologram drift & registration |
| `KhronosGroup/glTF` | [#2137](https://github.com/KhronosGroup/glTF/pull/2137) | KHR_audio_emitter PR | 58 | E2 — spatial audio source standard |
| `KhronosGroup/glTF` | [#2561](https://github.com/KhronosGroup/glTF/issues/2561) | Layered audio architecture proposal | 2 | E2 — full spatial audio stack in glTF |
| `KhronosGroup/glTF` | [#2632](https://github.com/KhronosGroup/glTF/pull/2632) | KHR_audio_graph PR | 2 | E2 — audio graph standard |
| `KhronosGroup/glTF` | [#2631](https://github.com/KhronosGroup/glTF/pull/2631) | KHR_audio_environment PR | 1 | E2 — acoustic environment standard |
| `KhronosGroup/glTF` | [#2506](https://github.com/KhronosGroup/glTF/issues/2506) | Synchronized immersive video+audio | 2 | E2 — AV sync for XR |
| `immersive-web/webxr` | [#815](https://github.com/immersive-web/webxr/issues/815) | Spec language precludes non-visual uses | 41 | E2/E3 — a11y + spatial audio gap |
| `immersive-web/model-element` | [#55](https://github.com/immersive-web/model-element/issues/55) | Is it time for browsers to standardize 3D rendering? | 11 | E2/E3 — browser platform question |
| `AR-js-org/AR.js` | [#826](https://github.com/AR-js-org/AR.js/issues/826) | Broken image tracking | — | E1 — Web AR tracking bottleneck |
| `AR-js-org/AR.js` | [#825](https://github.com/AR-js-org/AR.js/issues/825) | Location-based AR failing | — | E1 — Web AR geospatial failure |
| `hiukim/mind-ar-js` | KnownIssues | Tracking accuracy; CPU perf; roadmap gaps | — | E1/E3 — individual-dev bottleneck |
| `google/lullaby` | (internal) | Spatial audio + ECS architecture | — | E1/E2 — Google's spatial pipeline |

---

## How to Contribute

1. **Pick an episode issue** — #55 (E1), #53 (E2), or #54 (E3) for research & outreach.
2. **Add GitHub issue links** from the audit table above as comments on the relevant episode issue.
3. **Tag potential guests** — see `GUEST_DIRECTORY.md` for full contact and research context.
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates.

---

*Last research sync: 2026-09-18. See `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md` for the full continuously updated audit.*