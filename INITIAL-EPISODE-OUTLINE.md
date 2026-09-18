# 🎙️ The Future of Human Perception — Initial Episode Outline

> **Research sync: 2026-09-18** — GitHub-sourced hot debates from WiVRn, ARCore, MixedReality-WebRTC, WebXR, glTF, AR.js, OmniTone, and Spatial_Audio_Framework repositories.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos |
|---|---|
| Web 3D / WebXR | `mrdoob/three.js` (115.6k ⭐), `playcanvas/engine` (16.9k ⭐), `immersive-web/webxr` (3.1k ⭐), `Hubs-Foundation/hubs` (2.2k ⭐) |
| Web AR | `AR-js-org/AR.js` (15.8k ⭐), `hiukim/mind-ar-js` (2.7k ⭐), `jeeliz/jeelizFaceFilter` (2.9k ⭐) |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity` (6.1k ⭐), `microsoft/MixedReality-WebRTC` (944 ⭐) |
| Spatial Computing | `StereoKit/StereoKit` (1.1k ⭐), `KhronosGroup/OpenXR-SDK` (1.1k ⭐), `microsoft/xr-development-for-beginners` (564 ⭐) |
| Spatial Audio | `GoogleChrome/omnitone` (911 ⭐), `leomccormack/Spatial_Audio_Framework` (748 ⭐), `google/spatial-media` (2.1k ⭐) |
| AR SDKs | `google-ar/arcore-android-sdk` (5.2k ⭐), `google-ar/arcore-unity-sdk` (1.4k ⭐), `Unity-Technologies/arfoundation-samples` (3.4k ⭐) |
| 3D Assets & Standards | `KhronosGroup/glTF` (10k+ ⭐) — audio emitter extensions, spatial video proposals |
| Open Source VR | `WiVRn/WiVRn`, `ValveSoftware/openvr`, `polygraphene/ALVR`, `ValveSoftware/SteamVR-for-Linux` |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### 🔥 Confirmed GitHub-Sourced Hot Debates

| Debate | Source | Signal | Key Insight |
|---|---|---|---|
| **Per-client scheduled frames stall xrEndFrame** — WiVRn #1099 | [WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) | 🔴 15 comments, 2026 | After Quest 3 passthrough refocus, `wait_for_scheduled_free()` holds per-client frame slots scheduled **47 minutes in the future**. Compositor stays healthy at 80 FPS — this is a per-client scheduling bug, not global. The brain's vestibular system certainly notices. |
| **Temporal irregularity vs. average latency** — WiVRn #282 | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) | 🔴 40 comments | Paradigm shift: stutter = irregularity, not depth. The brain detects frame pacing irregularity, not absolute latency. |
| **"Missing" latency in VR streaming** — ALVR #334 | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) | 🔴 33.6ms unaccounted | 30–50% underreporting. If we're optimizing against the wrong number, the "20ms rule" may be unreachable even when reported numbers look fine. |
| **Camera↔IMU clock offset 13–35ms** — ARCore #1779 | [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | 🔴 Active, 2026 | On Xiaomi/OPPO devices, hardware clock sync between camera and IMU introduces 13–35ms offsets. ARCore logs: "Camera to IMU clock offset (34.86ms) exceeds threshold (5ms)." Rotation integrated as translation — phantom 100m path from in-place rotation. Invisible to devs, catastrophic for perception. |
| **Acoustic echo cancellation broken in MR** — MixedReality-WebRTC #157 | [MR-WebRTC #157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | 🔴 17 comments, open since 2019 | AEC failure = spatial audio collapse. Without echo cancellation, room acoustics contaminate the spatial audio model. Not an audio quality issue — a perceptual calibration failure. |
| **No standardized latency benchmark** — OpenVR #249 | [OpenVR #249](https://github.com/ValveSoftware/openvr/issues/249) | 🔴 Metrology crisis | Industry uses different methodologies — comparisons meaningless. We can't even agree on how to measure latency. |
| **Reprojection error in timewarp** — OpenVR #659 | [OpenVR #659](https://github.com/ValveSoftware/openvr/issues/659) | 🔴 Mechanical last line of defense | When predicted head pose is wrong, the warped frame causes visceral discomfort. Reprojection is the last line of defense, and it's failing. |
| **ARCore session crash on Samsung** — ARCore #1762 | [ARCore #1762](https://github.com/google-ar/arcore-android-sdk/issues/1762) | 🟡 Perceptual trust destroyed | Session resume crash after Play Services update — the brain's spatial model is violently interrupted. |
| **Web AR tracking failure** — AR.js #826, #825 | [AR.js #826](https://github.com/AR-js-org/AR.js/issues/826) | 🟡 First perceptual bottleneck on the web | Real-time tracking as the first perceptual bottleneck on the web platform. |
| **AR.js maintainers needed** — AR.js #609 | [AR.js #609](https://github.com/AR-js-org/AR.js/issues/609) | 🟡 Stale maintenance = stale perceptual techniques | Web AR's ceiling is held back by maintenance gaps. |

### Key Topics
1. The motion-to-photon pipeline — sensor → predict → render → encode → transport → decode → display. Every stage injects latency.
2. The "20 ms rule" and vestibular-visual conflict — why a few milliseconds of lag translate directly into motion sickness.
3. **Temporal irregularity vs. average latency** — the WiVRn #282 paradigm shift.
4. **"Missing" latency in VR streaming** — ALVR #334's 33.6ms underreporting finding.
5. **Per-client scheduled frame stalls** — WiVRn #1099: the compositor is healthy but the client freezes for 47+ minutes.
6. **Camera↔IMU clock offset** — ARCore #1779: 13–35ms hardware sync gap on mid-range Android.
7. **Acoustic echo cancellation failure** — MR-WebRTC #157: AEC broken in OpenXR MR stacks.
8. **No standardized latency benchmark** — OpenVR #249: the metrology crisis.
9. **Reprojection error** — OpenVR #659: the mechanical last line of defense that's breaking.
10. Session crashes as perceptual events — ARCore #1762.

### 👤 Guest Targets

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **xytovl** | Maintainer, WiVRn | Temporal irregularity finding (#282); per-client scheduled frame stalls (#1099, 47-min freeze); packet-timing & pacing algorithms |
| **IceyMint** | Reporter, WiVRn #1099 | Instrumented measurement of per-client frame-queue behavior; AI-drafted bug report with live process/thread stacks |
| **msclecram** | OpenVR contributor | Reprojection error deep-dive (#659); timewarp pipeline mechanics |
| **echuber2** | OpenVR latency advocate | Standardized motion-to-photon latency measurement methodology (#249) |
| **jn-3d** | Developer, ALVR | VR streaming stack forensics; "missing" 33.6ms latency discovery (#334) |
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR evolution; architecture decisions affecting perceptual latency |
| **nicolocarpignoli** | Maintainer, AR.js | iOS/Safari AR challenges (#302); community-driven rebuild (#609); geospatial AR accuracy (#288) |
| **kalwalt** | Author, AR.js-next ECS | ECS architecture and frame budget predictability (#681) |
| **brycehutchings** | Microsoft OpenXR-MR | HoloLens 2 D3D12 frame-timestamp precision; OpenXR-MR #131/#132 |
| **Daniel4144** | Contributor, MixedReality-WebRTC | Locatable camera & projection-matrix tracking (#83); MR audio-visual pipeline coupling |
| **jameszhong2008** | Issue author, MR-WebRTC #157 | First-hand AEC failure experience on MixedReality-WebRTC |
| **rutmir** | Issue author, ARCore #1779 | Camera↔IMU clock offset measurement on Xiaomi; VIO fault analysis |

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets are wrong — we need to stabilize frame delivery instead.

> **🔥 Per-client scheduled frame stalls are the ultimate "perceptual vs. measured" bug.** WiVRn #1099 reveals that after passthrough refocus, `wait_for_scheduled_free()` holds frame slots scheduled 47 minutes in the future. The compositor reports 80 FPS, but the user experiences minute-long freezes. The brain's vestibular system doesn't care about compositor health — it cares about when the next frame arrives.

> **🔥 Camera↔IMU clock offset is invisible but catastrophic.** ARCore #1779 shows 13–35ms offsets between camera and IMU on mid-range Android. ARCore's own diagnostics say "exceeds threshold (5ms)" — but the user never sees this. Rotation becomes translation. The brain's spatial model is silently corrupted.

> **🔥 Acoustic echo cancellation is a spatial-perception problem.** MixedReality-WebRTC #157 reveals that AEC — critical for spatial audio presence — is fundamentally broken in current MR stacks. Without echo cancellation, room acoustics contaminate the spatial audio model. This isn't an audio quality issue; it's a *perceptual calibration* failure.

> **🔥 The industry can't even measure latency consistently.** OpenVR #249: no standardized motion-to-photon latency benchmark exists. Different methodologies make comparisons meaningless. This is a metrology crisis — we're optimizing phantom numbers.

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### Core Question
Why is the WebXR spec visual-only for spatial audio? What does HRTF mean for presence?

### 🔥 Confirmed GitHub-Sourced Hot Debates

| Debate | Source | Signal | Key Insight |
|---|---|---|---|
| **WebXR has no spatial audio API** — #390 | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) | 🔴 Open since 2018, 30+ comments | The spec has no spatial-audio element. Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. Native platforms ship proprietary spatial audio developers can't access. |
| **Spec language precludes non-visual uses** — #815 | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | 🔴 41 comments, assigned to @toji | The spec literally assumes eyes-only perception. "A state of visible indicates that imagery rendered by the XRSession can be seen by the user…" — no room for audio-only XR. |
| **KHR_audio_emitter PR** — glTF #2137 | [glTF #2137](https://github.com/KhronosGroup/glTF/pull/2137) | 🔴 58 comments | How sound sources are positioned in 3D glTF scenes. The most active spatial audio standardization effort. |
| **Layered audio architecture** — glTF #2561 | [glTF #2561](https://github.com/KhronosGroup/glTF/issues/2561) | 🔴 rudybear's proposal | emitter + graph + environment = complete spatial audio stack in glTF. |
| **KHR_audio_graph PR** — glTF #2632 | [glTF #2632](https://github.com/KhronosGroup/glTF/pull/2632) | 🟡 Audio graph standard | Formal audio graph specification for spatial audio pipelines. |
| **KHR_audio_environment PR** — glTF #2631 | [glTF #2631](https://github.com/KhronosGroup/glTF/pull/2631) | 🟡 Acoustic environment standard | Reverb, occlusion, attenuation — the acoustic environment model. |
| **Synchronized immersive video+audio** — glTF #2506 | [glTF #2506](https://github.com/KhronosGroup/glTF/issues/2506) | 🟡 AV sync for XR | Timeline metadata, volumetric video, AV sync — Ben Erwin (powersimple). |
| **Mumble physics-accurate spatial audio** — #6597 | [Mumble #6597](https://github.com/mumble-voip/mumble/issues/6597) | 🔴 22 comments | Krzmbrzl proposes replacing simplistic spatial audio with proper HRTFs + Doppler + environmental effects via OpenAL-Soft. Cites IEEE paper on sound localization. |
| **Mach1 binaural rendering** — #2 | [Mach1 Studios #2](https://github.com/Mach1Studios/m1-spatialaudioserver/issues/2) | 🟡 Server-side binaural | Can convolvers achieve binaural rendering on top of the basic layer? References Omnitone's HOA convolver approach. |
| **SONIMO HRTF dataset loading bugs** — SAF #55 | [Spatial_Audio_Framework #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55) | 🟡 Reproducibility crisis | Even dataset loading is broken — researchers can't reproduce spatial audio results. |
| **ISM RIR incorrect summing** — SAF #58 | [Spatial_Audio_Framework #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) | 🟡 Fundamental bug | Image Source Method room acoustics bug invalidates perceptual room-acoustics research. |
| **Hubs audio doesn't scale past 20 users** — #5057 | [Hubs #5057](https://github.com/Hubs-Foundation/hubs/issues/5057) | 🟡 Social-scale audio | Spatial audio quality collapses under CPU load at social scale. |
| **Omnitone mobile gap** — #2 | [Omnitone #2](https://github.com/GoogleChrome/omnitone/issues/2) | 🔴 Open since 2016, 23 comments | Billion mobile users can't experience 3D audio. The mobile spatial audio gap is a decade old. |

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
11. **Two competing philosophies**: server-side binaural (Mach1/Avnerus) vs. client-side physics-accurate (Mumble/Krzmbrzl).
12. **Research reproducibility crisis** — ISM bugs (#58) and HRTF dataset loading failures (#55) undermine spatial audio science.

### 👤 Guest Targets

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **Krzmbrzl** | Maintainer, Mumble VoIP | Most ambitious open-source spatial audio upgrade: HRTF + Doppler + environmental effects via OpenAL-Soft (#6597). 22-comment deep technical engagement. |
| **Avnerus** | Developer, Mach1 Studios | Real-time binaural rendering on constrained devices (#2). Can contrast "good enough" vs. physics-accurate approaches. |
| **leomccormack** | Creator, Spatial_Audio_Framework & SPARTA | Ambisonics, HRTFs, ISM room modeling. Bridge between academic research and implementation. Also facing reproducibility bugs (#55, #58). |
| **rudybear** | glTF audio extension author | KHR_audio_graph + KHR_audio_environment — the layered spatial audio architecture (#2561) |
| **robertlong** | Hubs-Foundation | Audio reliability engineering; spatial audio at social scale (#1853, #5057) |
| **hoch** | Maintainer, Omnitone | Has lived with the mobile spatial audio gap for a decade (#2). Can speak to political/technical barriers. |
| **orighst (Boris Smus)** | Google, Omnitone | Browser-based binaural rendering; FOA/HOA; the Chrome spatial audio team perspective |
| **brandonpjones** | Web audio engineer, Google | Web Audio API spatial rendering; ambisonic codecs |
| **jkarmer (Julius Kammerl)** | Web audio engineer, Google | Real-time spatial audio in web browsers |
| **ameliaeckard** | Researcher, Apple Vision Pro | Spatial audio for visual impairment; accessibility via spatial navigation |
| **freeman-jiang** | Creator, beatsync | Multi-device spatial audio synchronization; clock sync precision |
| **edurnebernal** | Researcher, audio-visual perception | Audio-visual integration in VR; ventriloquism effect |
| **cwilso** | WebXR spec contributor | Author of #390 (spatial audio in WebXR); understands the spec gap from the inside |
| **ddorwin** | WebXR contributor, #815 author | Non-visual XR use cases; spec language barrier analysis |

### The Hot Debate

> **The WebXR spec is visually blind — and spatial audio is the biggest casualty.** WebXR #390 has been open since 2018 (30+ comments): the spec has no spatial-audio element. Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. Native platforms (Apple, Meta) ship proprietary spatial audio that developers can't access or extend. The web is the only platform that should be truly open for spatial audio — and it's falling behind.

> **🔥 glTF is becoming the accidental spatial audio standard.** With three concurrent audio extension proposals (`KHR_audio_emitter` #2137, `KHR_audio_graph` #2632, `KHR_audio_environment` #2631), glTF is closer than WebXR to defining a complete spatial audio pipeline. The question is whether W3C Immersive Web will collaborate with Khronos or let glTF become the de facto standard.

> **🔥 Two competing philosophies for web spatial audio are emerging.** Server-side binaural rendering (Mach1 / @Avnerus) — real-time HRTF on constrained devices via convolvers. vs. Client-side physics-accurate rendering (Mumble / @Krzmbrzl) — replace simplistic spatial audio with proper HRTFs + Doppler + environmental effects via OpenAL-Soft.

> **🔥 Spatial audio can't be separated from spatial rendering.** MR-WebRTC issues #83, #153, #157 form a pattern: the audio pipeline is constrained by the visual rendering pipeline. You can't fix spatial audio without fixing the entire MR compositor.

> **🔥 Research reproducibility is broken at the foundation.** SONIMO HRTF dataset loading bugs (#55) and ISM RIR incorrect summing (#58) mean that even the researchers can't reproduce each other's results. How can we build a science of spatial audio when the basic data pipelines are broken?

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### Core Question
Is the WebXR spec blind to non-visual perception? Can MR interfaces survive without depth, camera control, and device parity?

### 🔥 Confirmed GitHub-Sourced Hot Debates

| Debate | Source | Signal | Key Insight |
|---|---|---|---|
| **Dense pointcloud from depth sensors** — ARCore #120 | [ARCore #120](https://github.com/google-ar/arcore-android-sdk/issues/120) | 🔴 357 comments, 25 👍, 6 years old | The dominant Android AR platform still can't deliver dense depth pointclouds. Without surface geometry, MR holograms float in mid-air with no physical grounding. |
| **Device support requests (8+ years!)** — ARCore #89 | [ARCore #89](https://github.com/google-ar/arcore-android-sdk/issues/89) | 🔴 589 comments! | Perceptual accessibility crisis. If your AR app only works on 5 devices, you exclude the majority. |
| **Camera control (flashlight/auto-exposure)** — ARCore #153 | [ARCore #153](https://github.com/google-ar/arcore-android-sdk/issues/153) | 🔴 76 comments | Camera = perceptual bottleneck. No flashlight/auto-exposure API. AR is at the mercy of the OS camera app. |
| **Spec language precludes non-visual uses** — WebXR #815 | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | 🔴 41 comments, assigned to @toji | The spec literally assumes eyes-only perception. "A state of visible indicates that imagery rendered by the XRSession can be seen by the user…" |
| **Wayfinding crisis in immersive sessions** — WebXR #992 | [WebXR #992](https://github.com/immersive-web/webxr/issues/992) | 🔴 36 comments | Users don't know where they are in XR — fundamental spatial-awareness gap. Core human abilities that XR interfaces break. |
| **Dynamic foveation & visibility masking** — WebXR #1420 | [WebXR #1420](https://github.com/immersive-web/webxr/issues/1420) | 🟡 Rendering asymmetry as perceptual-performance lever | @AdaRoseCannon (W3C): high-res center, low-res periphery as a perceptual optimization. |
| **SpectatorView calibration instability** — MRC #228 | [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | 🟡 19 comments | HoloLens ↔ phone calibration that works once and never again. Fundamental research reproducibility blocker. |
| **Holograms sticking to camera** — MRC #221 | [MRC #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) | 🟡 18 comments | Even geometrically correct placement is rejected if it drifts. The #1 MR registration failure. |
| **AR.js architecture debates** — #681, #26, #58 | [AR.js #681](https://github.com/AR-js-org/AR.js/issues/681) | 🟡 ECS architecture proposal | Kalwalt's component-based architecture → pluggable tracking/rendering/interaction systems for MR. |
| **Multi-camera AR support** — AR.js #26 | [AR.js #26](https://github.com/AR-js-org/AR.js/issues/26) | 22 comments | No API to choose camera on multi-camera devices. Front vs. back cameras have different FOV, distortion, latency. |
| **MX Ink stylus for Meta Quest** — MRTK #914 | [MRTK #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) | 🟡 Platform convergence without interface abstraction | Quest user wants HoloLens tools. Input fragmentation breaks MR presence. |

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
10. **Non-visual XR interfaces** — WebXR spec treats haptics, spatial audio, and biometrics as afterthoughts. #815 proves the spec is visually blind.
11. Hand tracking vs. controllers — the missing middle ground.
12. **WebXR wayfinding crisis** — #992: spatial memory and navigation, core human abilities that XR interfaces break.
13. **Dynamic foveation as perceptual lever** — #1420: rendering asymmetry (high-res center, low-res periphery) as a performance optimization.
14. **Input fragmentation** — MRTK #914 (MX Ink on Quest) and #511 (vendor plugins) mean spatial interface designers must choose between ecosystems.

### 👤 Guest Targets

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k⭐) | Web AR pioneer; evolution from marker-based to image/geospatial tracking; AR.js 2→3 community rebuild |
| **hiukim** | Creator, MindAR (2.7k⭐) | On-device image/face tracking; production-ready AR on mobile |
| **nicolocarpignoli** | Maintainer, AR.js | Community-driven rebuild; iOS/Safari AR challenges (#302); geospatial AR accuracy (#288); maintainer recruitment (#609) |
| **kalwalt** | Author, AR.js-new ECS proposal | Component-based architecture for MR; pluggable tracking/rendering/interaction systems (#681) |
| **maluoi** | Maintainer, StereoKit (1.1k⭐) | XR engine architecture; OpenXR + WebXR dual-backend design; MR interface patterns |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration assignee (#221, #228); SpectatorView fragility |
| **bkonyves** | Google, AR/VR engineering | Google's spatial computing platform vision; reference space design; ARCore depth & camera control gaps |
| **SimonScholl** | ARCore pointcloud advocate (#120) | Depth sensing for AR; Tango-to-ARCore transition; dense surface mapping challenges |
| **inio** | ARCore device support tracker (#89) | Longest-running ARCore issue — device fragmentation & perceptual access |
| **jpeltone** | ARCore rear-camera faces (#714) | Augmented Faces on rear cameras; new camera paradigms |
| **ROBYER1** | ARCore body pose tracking (#1275) | Human body pose tracking for MR interfaces |
| **Andrew Hart** | ARKit-CoreLocation (5.5k⭐) | AR + GPS-scale spatial data; indoor-outdoor navigation bridge |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation & visibility masking (#1420); accessibility; spec language for non-visual XR (#815) |
| **toffan** | WebXR contributor | DOM overlays in XR (#1414); compositing layers; visibility-mask events |
| **keveleigh** | Microsoft MRTK maintainer | Vendor plugin architecture (#511); MRTK documentation gaps (#987); input abstraction strategy |

### The Hot Debate

> **Is the WebXR spec blind to non-visual perception?** Issues #815 (41 comments) and #992 (36 comments): the spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. You can "see" a virtual object in WebXR but you cannot reliably "hear" it or "feel" it. For MR — where the physical world is the backdrop — this is a fundamental architectural gap.

> **🔥 ARCore's depth-sensing gap is a perceptual crisis.** Issue #120 (357 comments, 6 years old) reveals that the dominant Android AR platform still can't deliver dense depth pointclouds from consumer hardware. Without accurate surface geometry, MR holograms float in mid-air with no physical grounding. This isn't a feature request — it's the missing foundation of spatial computing on the most widely deployed AR platform.

> **🔥 Device fragmentation is a perceptual accessibility issue.** ARCore #89 (589 comments!) isn't just about adding support — it's about whether spatial computing is available to everyone or only flagship device owners. The brain's perceptual system expects to interact with digital content in the physical world. If the hardware can't track the world, the perceptual contract is broken.

> **🔥 The camera is the perceptual bottleneck.** ARCore #153 (no flashlight/auto-exposure API) reveals that the camera subsystem limits perceptual quality. Without programmatic camera control, AR is at the mercy of the OS camera app. The brain's visual system adapts to lighting conditions automatically — AR can't.

> **🔥 AR.js 2→3 is an architectural perceptible shift.** Kalwalt's ECS proposal (#681) isn't just a refactoring — it's a paradigm change from monolithic to component-based. Component architecture means pluggable tracking, rendering, and interaction systems — exactly what MR needs for adaptive perceptual pipelines.

---

## Cross-Episode Themes

| Theme | Episode 1 | Episode 2 | Episode 3 |
|---|---|---|---|
| The brain as final arbiter of reality | ✅ (temporal vs. average latency) | ✅ (audio presence paradox) | ✅ (visual-centric spec gap) |
| Open-source vs. proprietary stacks | ✅ (open VR latency tools) | ✅ (open spatial audio frameworks) | ✅ (open MR toolkits) |
| The web platform as the egalitarian frontier | ✅ (Web AR, AR.js) | ✅ (Omnitone vs. native) | ✅ (WebXR spec gap + ARCore fragmentation) |
| Regulatory & ethics (FDA, accessibility) | ✅ (motion sickness liability) | ✅ (accessibility for impaired) | ✅ (device fragmentation = access gap) |
| Perceptual access & fragmentation | ✅ (device latency variability) | ✅ (HRTF personalization gap) | ✅ (ARCore #89, 589 comments) |
| Standards convergence (glTF ↔ WebXR) | — | ✅ (KHR_audio_* extensions) | ✅ (WebXR spec gaps) |
| Camera-as-bottleneck | ✅ (session stability) | ✅ (audio-visual coupling) | ✅ (flashlight/auto-exposure gap) |
| Reproducibility crisis | ✅ (latency measurement crisis) | ✅ (ISM/HRTF data bugs) | ✅ (calibration that works once) |

---

## Repository Contributions Guide

1. **Pick an episode issue** — see the open issues for Episode 1, 2, or 3 for research & outreach tasks.
2. **Add issue links** from the GitHub repos above as comments on the relevant issue.
3. **Tag potential guests** — see `GUEST_DIRECTORY.md` for full contact and research context.
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates.

---

*Last research sync: 2026-09-18. See `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md` for the full continuously updated audit.*