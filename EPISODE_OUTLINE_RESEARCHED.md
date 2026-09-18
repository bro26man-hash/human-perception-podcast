# 🎙️ The Future of Human Perception — Researched Episode Outline

> **Research sync: 2026-09-18** — GitHub-sourced hot debates from WebXR, AR.js, WiVRn, ALVR, OpenVR, MixedReality-WebRTC, glTF, Omnitone, Spatial_Audio_Framework, and Mumble repositories.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

### Most Active GitHub Communities Surveyed

| Domain | Repos | Stars |
|---|---|---|
| **Web 3D / WebXR** | `mrdoob/three.js`, `playcanvas/engine`, `immersive-web/webxr`, `Hubs-Foundation/hubs` | 115k+ / 16.9k / 3.1k / 2.2k |
| **Web AR** | `AR-js-org/AR.js`, `hiukim/mind-ar-js`, `jeeliz/jeelizFaceFilter` | 15.8k / 2.7k / 2.9k |
| **Mixed Reality** | `microsoft/MixedRealityToolkit-Unity`, `microsoft/MixedReality-WebRTC` | 6.1k / 944 |
| **Spatial Computing** | `StereoKit/StereoKit`, `KhronosGroup/OpenXR-SDK` | 1.1k / 1.1k |
| **Spatial Audio** | `GoogleChrome/omnitone`, `leomccormack/Spatial_Audio_Framework`, `google/spatial-media` | 911 / 748 / 2.1k |
| **AR SDKs** | `google-ar/arcore-android-sdk`, `google-ar/arcore-unity-sdk`, `Unity-Technologies/arfoundation-samples` | 5.2k / 1.4k / 3.4k |
| **Open Source VR** | `WiVRn/WiVRn`, `polygraphene/ALVR`, `ValveSoftware/openvr` | Active |
| **3D Assets & Standards** | `KhronosGroup/glTF` (audio emitter extensions, spatial video proposals) | 10k+ |

---

## 🔥 Hottest GitHub-Sourced Debates Across All Episodes

| # | Debate | Source | Signal | Why It Matters |
|---|---|---|---|---|
| 1 | **Spec language precludes non-visual uses** | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | 🔴 41 comments, open since 2019, assigned to @toji | The spec literally assumes eyes-only perception. "A state of visible indicates that imagery rendered by the XRSession can be seen by the user…" — no room for audio-only XR. |
| 2 | **No spatial audio API in WebXR** | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) | 🔴 30 comments, open since 2018 | Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. Native platforms ship proprietary spatial audio developers can't access. |
| 3 | **Better haptics support needed** | [WebXR #1423](https://github.com/immersive-web/webxr/issues/1423) | 🔴 Open since 2025, @cabanier | We've been waiting for years for haptics. Only immersive devices care — maybe we should just implement it in WebXR. |
| 4 | **Temporal irregularity vs. average latency** | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) | 🔴 40 comments | Paradigm shift: stutter = irregularity, not depth. The brain detects frame pacing irregularity, not absolute latency. |
| 5 | **Per-client scheduled frame stalls** | [WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) | 🔴 15 comments, 2026 | `wait_for_scheduled_free()` holds frame slots scheduled 47 minutes in the future. Compositor reports 80 FPS — user experiences minute-long freezes. |
| 6 | **"Missing" latency in VR streaming** | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) | 🔴 33.6ms unaccounted | 30–50% underreporting. If we're optimizing against the wrong number, the "20ms rule" may be unreachable even when reported numbers look fine. |
| 7 | **Camera↔IMU clock offset 13–35ms** | [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | 🔴 Active, 2026 | "Camera to IMU clock offset (34.86ms) exceeds threshold (5ms)." Rotation integrated as translation — phantom 100m path from in-place rotation. |
| 8 | **Acoustic echo cancellation broken in MR** | [MixedReality-WebRTC #157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | 🔴 17 comments, open since 2019 | AEC failure = spatial audio collapse. Without echo cancellation, room acoustics contaminate the spatial audio model. |
| 9 | **No standardized latency benchmark** | [OpenVR #249](https://github.com/ValveSoftware/openvr/issues/249) | 🔴 Metrology crisis | Industry uses different methodologies — comparisons meaningless. We can't even agree on how to measure latency. |
| 10 | **Reprojection error in timewarp** | [OpenVR #659](https://github.com/ValveSoftware/openvr/issues/659) | 🔴 Mechanical last line of defense | When predicted head pose is wrong, the warped frame causes visceral discomfort. Reprojection is failing. |
| 11 | **WebXR has no spatial audio API** | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) | 🔴 Open since 2018, 30+ comments | The spec has no spatial-audio element. FOA only, no HRTF. Web is the only platform that should be truly open for spatial audio — and it's falling behind. |
| 12 | **glTF audio extensions — 3 concurrent proposals** | [glTF #2137](https://github.com/KhronosGroup/glTF/pull/2137), [#2561](https://github.com/KhronosGroup/glTF/issues/2561), [#2632](https://github.com/KhronosGroup/glTF/pull/2632), [#2631](https://github.com/KhronosGroup/glTF/pull/2631) | 🔴 58 comments on #2137 | KHR_audio_emitter + KHR_audio_graph + KHR_audio_environment = accidental spatial audio standard. glTF is closer than WebXR to defining a complete spatial audio pipeline. |
| 13 | **Mumble physics-accurate spatial audio** | [Mumble #6597](https://github.com/mumble-voip/mumble/issues/6597) | 🔴 22 comments | Krzmbrzl proposes replacing simplistic spatial audio with proper HRTFs + Doppler + environmental effects via OpenAL-Soft. |
| 14 | **Omnitone mobile gap** | [Omnitone #2](https://github.com/GoogleChrome/omnitone/issues/2) | 🔴 Open since 2016, 23 comments | Billion mobile users can't experience 3D audio. The mobile spatial audio gap is a decade old. |
| 15 | **SONIMO HRTF dataset loading bugs** | [SAF #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55) | 🟡 Reproducibility crisis | Even dataset loading is broken — researchers can't reproduce spatial audio results. |
| 16 | **ISM RIR incorrect summing** | [SAF #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) | 🟡 Fundamental bug | Image Source Method room acoustics bug invalidates perceptual room-acoustics research. |
| 17 | **Dense pointcloud from depth sensors** | [ARCore #120](https://github.com/google-ar/arcore-android-sdk/issues/120) | 🔴 357 comments, 6 years old | The dominant Android AR platform still can't deliver dense depth pointclouds. MR holograms float in mid-air with no physical grounding. |
| 18 | **Device support requests (8+ years!)** | [ARCore #89](https://github.com/google-ar/arcore-android-sdk/issues/89) | 🔴 589 comments! | Perceptual accessibility crisis. If your AR app only works on 5 devices, you exclude the majority. |
| 19 | **Camera control (flashlight/auto-exposure)** | [ARCore #153](https://github.com/google-ar/arcore-android-sdk/issues/153) | 🔴 76 comments | Camera = perceptual bottleneck. No flashlight/auto-exposure API. AR is at the mercy of the OS camera app. |
| 20 | **Wayfinding crisis in immersive sessions** | [WebXR #992](https://github.com/immersive-web/webxr/issues/992) | 🔴 36 comments | Users don't know where they are in XR — fundamental spatial-awareness gap. Core human abilities that XR interfaces break. |
| 21 | **Dynamic foveation & visibility masking** | [WebXR #1420](https://github.com/immersive-web/webxr/issues/1420) | 🟡 Rendering asymmetry as perceptual-performance lever | @AdaRoseCannon (W3C): high-res center, low-res periphery as a perceptual optimization. |
| 22 | **Hologram drift & calibration instability** | [MRC #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221), [#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | 🟡 18–19 comments | Holograms sticking to camera + SpectatorView calibration instability. Registration is the #1 MR failure. |
| 23 | **Markerless tracking without Tango** | [AR.js #217](https://github.com/AR-js-org/AR.js/issues/217) | 🟡 22 comments | Web AR still can't do markerless AR on regular phones without specialized hardware. WebXR polyfill does it — why can't AR.js? |
| 24 | **AR.js maintainers needed** | [AR.js #609](https://github.com/AR-js-org/AR.js/issues/609) | 🟡 Stale maintenance = stale perceptual techniques | Web AR's ceiling is held back by maintenance gaps. |
| 25 | **Hubs audio doesn't scale past 20 users** | [Hubs #5057](https://github.com/Hubs-Foundation/hubs/issues/5057) | 🟡 Social-scale audio | Spatial audio quality collapses under CPU load at social scale. |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### 🔥 Key Debates for This Episode

| Debate | Source | Key Insight |
|---|---|---|
| **Temporal irregularity vs. average latency** | WiVRn #282 | Stutter = irregularity, not depth. The brain detects frame pacing irregularity, not absolute latency. |
| **Per-client scheduled frame stalls** | WiVRn #1099 | Compositor reports 80 FPS, but user experiences minute-long freezes. Brain's vestibular system doesn't care about compositor health. |
| **"Missing" latency in VR streaming** | ALVR #334 | 33.6ms unaccounted. 30–50% underreporting. The "20ms rule" may be unreachable even when reported numbers look fine. |
| **Camera↔IMU clock offset 13–35ms** | ARCore #1779 | "exceeds threshold (5ms)" — but user never sees this. Rotation becomes translation. Brain's spatial model silently corrupted. |
| **No standardized latency benchmark** | OpenVR #249 | Metrology crisis. Different methodologies make comparisons meaningless. |
| **Reprojection error in timewarp** | OpenVR #659 | Mechanical last line of defense that's breaking. |

### 👤 Guest Targets — Episode 1

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

> **🔥 Per-client scheduled frame stalls are the ultimate "perceptual vs. measured" bug.** WiVRn #1099 reveals that after passthrough refocus, `wait_for_scheduled_free()` holds frame slots scheduled 47 minutes in the future. The compositor reports 80 FPS, but the user experiences minute-long freezes.

> **🔥 Camera↔IMU clock offset is invisible but catastrophic.** ARCore #1779 shows 13–35ms offsets between camera and IMU on mid-range Android. ARCore's own diagnostics say "exceeds threshold (5ms)" — but the user never sees this.

> **🔥 Acoustic echo cancellation is a spatial-perception problem.** MixedReality-WebRTC #157 reveals that AEC is fundamentally broken in current MR stacks. Without echo cancellation, room acoustics contaminate the spatial audio model. This isn't an audio quality issue; it's a *perceptual calibration* failure.

> **🔥 The industry can't even measure latency consistently.** OpenVR #249: no standardized motion-to-photon latency benchmark exists. This is a metrology crisis — we're optimizing phantom numbers.

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### Core Question
Why is the WebXR spec visual-only for spatial audio? What does HRTF mean for presence?

### 🔥 Key Debates for This Episode

| Debate | Source | Key Insight |
|---|---|---|
| **WebXR has no spatial audio API** | WebXR #390 | Open since 2018, 30+ comments. The spec has no spatial-audio element. FOA only, no HRTF. |
| **Spec language precludes non-visual uses** | WebXR #815 | 41 comments, assigned to @toji. The spec literally assumes eyes-only perception. |
| **glTF audio extensions — 3 concurrent proposals** | glTF #2137, #2561, #2632, #2631 | KHR_audio_emitter + KHR_audio_graph + KHR_audio_environment. glTF is becoming the accidental spatial audio standard. |
| **Mumble physics-accurate spatial audio** | Mumble #6597 | Krzmbrzl: replace simplistic spatial audio with proper HRTFs + Doppler + environmental effects via OpenAL-Soft. |
| **Omnitone mobile gap** | Omnitone #2 | Open since 2016, 23 comments. Billion mobile users can't experience 3D audio. |
| **SONIMO HRTF dataset loading bugs** | SAF #55 | Reproducibility crisis — even dataset loading is broken. |
| **ISM RIR incorrect summing** | SAF #58 | Fundamental bug invalidates perceptual room-acoustics research. |
| **Hubs audio doesn't scale past 20 users** | Hubs #5057 | Spatial audio quality collapses under CPU load at social scale. |

### 👤 Guest Targets — Episode 2

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **Krzmbrzl** | Maintainer, Mumble VoIP | Most ambitious open-source spatial audio upgrade: HRTF + Doppler + environmental effects via OpenAL-Soft (#6597). 22-comment deep engagement. |
| **Avnerus** | Developer, Mach1 Studios | Real-time binaural rendering on constrained devices (#2). "Good enough" vs. physics-accurate approaches. |
| **leomccormack** | Creator, Spatial_Audio_Framework & SPARTA | Ambisonics, HRTFs, ISM room modeling. Bridge between academic research and implementation. Also facing reproducibility bugs (#55, #58). |
| **rudybear** | glTF audio extension author | KHR_audio_graph + KHR_audio_environment — the layered spatial audio architecture (#2561) |
| **robertlong** | Hubs-Foundation | Audio reliability engineering; spatial audio at social scale (#1853, #5057) |
| **hoch** | Maintainer, Omnitone | Has lived with the mobile spatial audio gap for a decade (#2). Political/technical barriers. |
| **orighst (Boris Smus)** | Google, Omnitone | Browser-based binaural rendering; FOA/HOA; the Chrome spatial audio team perspective |
| **brandonpjones** | Web audio engineer, Google | Web Audio API spatial rendering; ambisonic codecs |
| **jkarmer (Julius Kammerl)** | Web audio engineer, Google | Real-time spatial audio in web browsers |
| **ameliaeckard** | Researcher, Apple Vision Pro | Spatial audio for visual impairment; accessibility via spatial navigation |
| **freeman-jiang** | Creator, beatsync | Multi-device spatial audio synchronization; clock sync precision |
| **edurnebernal** | Researcher, audio-visual perception | Audio-visual integration in VR; ventriloquism effect |
| **cwilso** | WebXR spec contributor | Author of #390 (spatial audio in WebXR); understands the spec gap from the inside |
| **ddorwin** | WebXR contributor, #815 author | Non-visual XR use cases; spec language barrier analysis |

### The Hot Debate

> **The WebXR spec is visually blind — and spatial audio is the biggest casualty.** WebXR #390 has been open since 2018 (30+ comments): the spec has no spatial-audio element. Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. Native platforms (Apple, Meta) ship proprietary spatial audio that developers can't access or extend.

> **🔥 glTF is becoming the accidental spatial audio standard.** With three concurrent audio extension proposals (`KHR_audio_emitter` #2137, `KHR_audio_graph` #2632, `KHR_audio_environment` #2631), glTF is closer than WebXR to defining a complete spatial audio pipeline. The question is whether W3C Immersive Web will collaborate with Khronos or let glTF become the de facto standard.

> **🔥 Two competing philosophies for web spatial audio are emerging.** Server-side binaural rendering (Mach1 / @Avnerus) vs. Client-side physics-accurate rendering (Mumble / @Krzmbrzl).

> **🔥 Spatial audio can't be separated from spatial rendering.** MR-WebRTC issues #83, #153, #157 form a pattern: the audio pipeline is constrained by the visual rendering pipeline.

> **🔥 Research reproducibility is broken at the foundation.** SONIMO HRTF dataset loading bugs (#55) and ISM RIR incorrect summing (#58) mean that even the researchers can't reproduce each other's results.

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### Core Question
Is the WebXR spec blind to non-visual perception? Can MR interfaces survive without depth, camera control, and device parity?

### 🔥 Key Debates for This Episode

| Debate | Source | Key Insight |
|---|---|---|
| **Spec language precludes non-visual uses** | WebXR #815 | 41 comments, assigned to @toji. The spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. |
| **Wayfinding crisis in immersive sessions** | WebXR #992 | 36 comments. Users don't know where they are in XR — fundamental spatial-awareness gap. Core human abilities that XR interfaces break. |
| **Dynamic foveation & visibility masking** | WebXR #1420 | @AdaRoseCannon (W3C): high-res center, low-res periphery as a perceptual optimization. |
| **Better haptics support needed** | WebXR #1423 | @cabanier: We've been waiting for years. Only immersive devices care. Maybe we should just implement it in WebXR. |
| **Dense pointcloud from depth sensors** | ARCore #120 | 357 comments, 6 years old. Dominant Android AR platform still can't deliver dense depth pointclouds. MR holograms float without surface geometry. |
| **Device support requests (8+ years!)** | ARCore #89 | 589 comments! Perceptual accessibility crisis. If your AR app only works on 5 devices, you exclude the majority. |
| **Camera control (flashlight/auto-exposure)** | ARCore #153 | 76 comments. Camera = perceptual bottleneck. No flashlight/auto-exposure API. |
| **Hologram drift & calibration instability** | MRC #221, #228 | 18–19 comments. Even geometrically correct placement is rejected if it drifts. The #1 MR registration failure. |
| **Markerless tracking without Tango** | AR.js #217 | 22 comments. Web AR still can't do markerless AR on regular phones without specialized hardware. |
| **AR.js architecture debates** | AR.js #681 | Kalwalt's ECS architecture proposal → pluggable tracking/rendering/interaction systems for MR. |
| **MX Ink stylus for Meta Quest** | MRTK #914 | Platform convergence without interface abstraction. Quest user wants HoloLens tools. Input fragmentation breaks MR presence. |

### 👤 Guest Targets — Episode 3

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

> **🔥 ARCore's depth-sensing gap is a perceptual crisis.** Issue #120 (357 comments, 6 years old) reveals that the dominant Android AR platform still can't deliver dense depth pointclouds from consumer hardware. Without accurate surface geometry, MR holograms float in mid-air with no physical grounding.

> **🔥 Device fragmentation is a perceptual accessibility issue.** ARCore #89 (589 comments!) isn't just about adding support — it's about whether spatial computing is available to everyone or only flagship device owners.

> **🔥 The camera is the perceptual bottleneck.** ARCore #153 (no flashlight/auto-exposure API) reveals that the camera subsystem limits perceptual quality. The brain's visual system adapts to lighting conditions automatically — AR can't.

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