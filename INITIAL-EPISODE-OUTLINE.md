# 🎙️ The Future of Human Perception — Initial Episode Outline

> **Research sync: 2026-09-18** — Consolidated from GitHub issue audits across WiVRn, AR.js, WebXR, MixedReality-WebRTC, ARCore, glTF, Omnitone, and Spatial_Audio_Framework repositories.

---

## Series Vision

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos | Stars |
|---|---|---|
| Web 3D / WebXR | `mrdoob/three.js`, `playcanvas/engine`, `immersive-web/webxr`, `Hubs-Foundation/hubs` | 115k–2k |
| Web AR | `AR-js-org/AR.js`, `hiukim/mind-ar-js`, `jeeliz/jeelizFaceFilter` | 15.8k–2.7k |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity`, `microsoft/MixedReality-WebRTC`, `microsoft/MixedRealityCompanionKit` | 6.1k–18 |
| Spatial Computing | `StereoKit/StereoKit`, `KhronosGroup/OpenXR-SDK`, `IvanCampos/visionOS-examples` | 1.1k–405 |
| Spatial Audio | `GoogleChrome/omnitone`, `leomccormack/Spatial_Audio_Framework`, `google/spatial-media`, `freeman-jiang/beatsync` | 911–748 |
| AR SDKs | `google-ar/arcore-android-sdk`, `google-ar/arcore-unity-sdk`, `Unity-Technologies/arfoundation-samples` | 5.2k–3.4k |
| 3D Assets & Standards | `KhronosGroup/glTF` (audio emitter extensions, spatial video proposals) | 10k+ |
| Open Source VR | `WiVRn/WiVRn`, `ValveSoftware/openvr`, `polygraphene/ALVR`, `ValveSoftware/SteamVR-for-Linux` | Active |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### 🔥 Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### 🔥 Confirmed GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Key Insight |
|---|---|---|---|---|
| 1 | **Per-client scheduled frames stall xrEndFrame** | [WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) | 🔴 15 comments, 2026 | After Quest 3 passthrough refocus, `wait_for_scheduled_free()` holds per-client frame slots scheduled **47 minutes in the future**. Compositor stays healthy at 80 FPS — this is a per-client scheduling bug, not global. The brain's vestibular system certainly notices. |
| 2 | **Temporal irregularity vs. average latency** | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) | 🔴 40 comments |Paradigm shift: stutter = irregularity, not depth. The brain detects frame pacing irregularity, not absolute latency. |
| 3 | **"Missing" latency in VR streaming** | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) | 🔴 33.6ms unaccounted | 30–50% underreporting. If we're optimizing against the wrong number, the "20ms rule" may be unreachable even when reported numbers look fine. |
| 4 | **Camera↔IMU clock offset 13–35ms** | [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | 🔴 Active, 2026 | On Xiaomi/OPPO devices, hardware clock sync between camera and IMU introduces 13–35ms offsets. ARCore logs: "Camera to IMU clock offset (34.86ms) exceeds threshold (5ms)." Rotation integrated as translation — phantom 100m path from in-place rotation. Invisible to devs, catastrophic for perception. |
| 5 | **Acoustic echo cancellation broken in MR** | [MixedReality-WebRTC #157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | 🔴 17 comments, open since 2019 | AEC failure = spatial audio collapse. Without echo cancellation, room acoustics contaminate the spatial audio model. Not an audio quality issue — a perceptual calibration failure. |
| 6 | **No standardized latency benchmark** | [OpenVR #249](https://github.com/ValveSoftware/openvr/issues/249) | 🔴 Metrology crisis | Industry uses different methodologies — comparisons meaningless. We can't even agree on how to measure latency. |
| 7 | **Reprojection error in timewarp** | [OpenVR #659](https://github.com/ValveSoftware/openvr/issues/659) | 🔴 Mechanical last line of defense | When predicted head pose is wrong, the warped frame causes visceral discomfort. Reprojection is the last line of defense, and it's failing. |
| 8 | **ARCore session crash on Samsung** | [ARCore #1762](https://github.com/google-ar/arcore-android-sdk/issues/1762) | 🟡 Perceptual trust destroyed | Session resume crash after Play Services update — the brain's spatial model is violently interrupted. |
| 9 | **Web AR tracking failure** | [AR.js #826, #825](https://github.com/AR-js-org/AR.js/issues/826) | 🟡 First perceptual bottleneck on the web | Real-time tracking as the first perceptual bottleneck on the web platform. |
| 10 | **AR.js maintainers needed** | [AR.js #609](https://github.com/AR-js-org/AR.js/issues/609) | 🟡 Stale maintenance = stale perceptual techniques | Web AR's ceiling is held back by maintenance gaps. |

### 👤 Guest Targets — Episode 1

| Name | Repo / Role | What They'll Bring | Status |
|---|---|---|---|
| **xytovl** | Maintainer, WiVRn | Temporal irregularity finding (#282); per-client scheduled frame stalls (#1099, 47-min freeze); packet-timing & pacing algorithms | ⬜ Not contacted |
| **IceyMint** | Reporter, WiVRn #1099 | Instrumented measurement of per-client frame-queue behavior; AI-drafted bug report with live process/thread stacks | ⬜ Not contacted |
| **msclecram** | OpenVR contributor | Reprojection error deep-dive (#659); timewarp pipeline mechanics | ⬜ Not contacted |
| **echuber2** | OpenVR latency advocate | Standardized motion-to-photon latency measurement methodology (#249) | ⬜ Not contacted |
| **jn-3d** | Developer, ALVR | VR streaming stack forensics; "missing" 33.6ms latency discovery (#334) | ⬜ Not contacted |
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR evolution; architecture decisions affecting perceptual latency; AR.js 2→3 transition | ⬜ Not contacted |
| **nicolocarpignoli** | Maintainer, AR.js | iOS/Safari AR challenges (#302); community-driven rebuild (#609); geospatial AR accuracy (#288) | ⬜ Not contacted |
| **kalwalt** | Author, AR.js-next ECS | ECS architecture and frame budget predictability (#681) | ⬜ Not contacted |
| **brycehutchings** | Microsoft OpenXR-MR | HoloLens 2 D3D12 frame-timestamp precision; OpenXR-MR #131/#132 | ⬜ Not contacted |
| **Daniel4144** | Contributor, MixedReality-WebRTC | Locatable camera & projection-matrix tracking (#83); MR audio-visual pipeline coupling | ⬜ Not contacted |
| **jameszhong2008** | Issue author, MR-WebRTC #157 | First-hand AEC failure experience on MixedReality-WebRTC | ⬜ Not contacted |
| **rutmir** | Issue author, ARCore #1779 | Camera↔IMU clock offset measurement on Xiaomi; VIO fault analysis | ⬜ Not contacted |
| **leinardi** | Maintainer, SteamVR-for-Linux | Open-source VR motion-to-photon latency; community-reported lag (#21, 97+ comments) | ⬜ Not contacted |
| **jemunch1997** | Maintainer, ALVR | VR streaming latency underreporting; encoding optimization | ⬜ Not contacted |
| **AaronMillward** | Contributor, WiVRn | Field reports of perceptual stutter & motion sickness from real users | ⬜ Not contacted |
| **maxkojju** | Reporter, WiVRn #1102 | Pico GPU issues; let me know if a game is dermatologically healthy (#1102) | ⬜ Not contacted |

### 🎯 Episode 1 Goals

1. **Establish that perceptual latency ≠ pipeline latency** — WiVRn #282's temporal irregularity finding is paradigm-shifting
2. **Expose the "missing latency" problem** — ALVR #334 shows 30-50% underreporting; the 20ms rule may be unreachable
3. **Reveal invisible perceptual bugs** — ARCore #1779 (clock offset) and WiVRn #1099 (47-min freeze) show systems that report healthy metrics while breaking perception
4. **Frame the metrology crisis** — OpenVR #249: no standardized benchmark means we're optimizing phantom numbers
5. **Make the case for AEC as a spatial-perception issue** — MR-WebRTC #157: echo cancellation failure is not audio quality, it's perceptual calibration

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### 🔥 Core Question
Why is the WebXR spec visual-only for spatial audio? What does HRTF mean for presence?

### 🔥 Confirmed GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Key Insight |
|---|---|---|---|---|
| 1 | **WebXR has no spatial audio API** | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) | 🔴 Open since 2018, 30+ comments | The spec has no spatial-audio element. Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. Native platforms ship proprietary spatial audio developers can't access. |
| 2 | **Spec language precludes non-visual uses** | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | 🔴 41 comments, assigned to @toji | The spec literally assumes eyes-only perception. "A state of visible indicates that imagery rendered by the XRSession can be seen by the user…" — no room for audio-only XR. |
| 3 | **KHR_audio_emitter PR** | [glTF #2137](https://github.com/KhronosGroup/glTF/pull/2137) | 🔴 58 comments | How sound sources are positioned in 3D glTF scenes. The most active spatial audio standardization effort. |
| 4 | **Layered audio architecture** | [glTF #2561](https://github.com/KhronosGroup/glTF/issues/2561) | 🔴 rudybear's proposal | emitter + graph + environment = complete spatial audio stack in glTF. |
| 5 | **KHR_audio_graph PR** | [glTF #2632](https://github.com/KhronosGroup/glTF/pull/2632) | 🟡 Audio graph standard | Formal audio graph specification for spatial audio pipelines. |
| 6 | **KHR_audio_environment PR** | [glTF #2631](https://github.com/KhronosGroup/glTF/pull/2631) | 🟡 Acoustic environment standard | Reverb, occlusion, attenuation — the acoustic environment model. |
| 7 | **Synchronized immersive video+audio** | [glTF #2506](https://github.com/KhronosGroup/glTF/issues/2506) | 🟡 AV sync for XR | Timeline metadata, volumetric video, AV sync — Ben Erwin (powersimple). |
| 8 | **Mumble physics-accurate spatial audio** | [Mumble #6597](https://github.com/mumble-voip/mumble/issues/6597) | 🔴 22 comments | Krzmbrzl proposes replacing simplistic spatial audio with proper HRTFs + Doppler + environmental effects via OpenAL-Soft. Cites IEEE paper on sound localization. |
| 9 | **Mach1 binaural rendering** | [Mach1 Studios #2](https://github.com/Mach1Studios/m1-spatialaudioserver/issues/2) | 🟡 Server-side binaural | Can convolvers achieve binaural rendering on top of the basic layer? References Omnitone's HOA convolver approach. |
| 10 | **SONIMO HRTF dataset loading bugs** | [SAF #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55) | 🟡 Reproducibility crisis | Even dataset loading is broken — researchers can't reproduce spatial audio results. |
| 11 | **ISM RIR incorrect summing** | [SAF #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) | 🟡 Fundamental bug | Image Source Method room acoustics bug invalidates perceptual room-acoustics research. |
| 12 | **Hubs audio doesn't scale past 20 users** | [Hubs #5057](https://github.com/Hubs-Foundation/hubs/issues/5057) | 🟡 Social-scale audio | Spatial audio quality collapses under CPU load at social scale. |
| 13 | **Omnitone mobile gap** | [Omnitone #2](https://github.com/GoogleChrome/omnitone/issues/2) | 🔴 Open since 2016, 23 comments | Billion mobile users can't experience 3D audio. The mobile spatial audio gap is a decade old. |
| 14 | **ADM2 does not play sound with multiple audio outputs** | [MR-WebRTC #573](https://github.com/microsoft/MixedReality-WebRTC/issues/573) | 🟢 ACTIVE | When mixing spatial audio with communication stacks (WebRTC), the ADM2 audio pipeline breaks with multiple output devices. |

### 👤 Guest Targets — Episode 2

| Name | Repo / Role | What They'll Bring | Status |
|---|---|---|---|
| **Krzmbrzl** | Maintainer, Mumble VoIP | Most ambitious open-source spatial audio upgrade: HRTF + Doppler + environmental effects via OpenAL-Soft (#6597). 22-comment deep technical engagement. | ⬜ Not contacted |
| **Avnerus** | Developer, Mach1 Studios | Real-time binaural rendering on constrained devices (#2). Can contrast "good enough" vs. physics-accurate approaches. | ⬜ Not contacted |
| **leomccormack** | Creator, Spatial_Audio_Framework & SPARTA | Ambisonics, HRTFs, ISM room modeling. Bridge between academic research and implementation. Also facing reproducibility bugs (#55, #58). | ⬜ Not contacted |
| **rudybear** | glTF audio extension author | KHR_audio_graph + KHR_audio_environment — the layered spatial audio architecture (#2561) | ⬜ Not contacted |
| **robertlong** | Hubs-Foundation | Audio reliability engineering; spatial audio at social scale (#1853, #5057) | ⬜ Not contacted |
| **hoch** | Maintainer, Omnitone | Has lived with the mobile spatial audio gap for a decade (#2). Can speak to political/technical barriers. | ⬜ Not contacted |
| **orighst (Boris Smus)** | Google, Omnitone | Browser-based binaural rendering; FOA/HOA; the Chrome spatial audio team perspective | ⬜ Not contacted |
| **brandonpjones** | Web audio engineer, Google | Web Audio API spatial rendering; ambisonic codecs | ⬜ Not contacted |
| **jkarmer (Julius Kammerl)** | Web audio engineer, Google | Real-time spatial audio in web browsers | ⬜ Not contacted |
| **ameliaeckard** | Researcher, Apple Vision Pro | Spatial audio for visual impairment; accessibility via spatial navigation | ⬜ Not contacted |
| **freeman-jiang** | Creator, beatsync | Multi-device spatial audio synchronization; clock sync precision | ⬜ Not contacted |
| **edurnebernal** | Researcher, audio-visual perception | Audio-visual integration in VR; ventriloquism effect | ⬜ Not contacted |
| **cwilso** | WebXR spec contributor | Author of #390 (spatial audio in WebXR); understands the spec gap from the inside | ⬜ Not contacted |
| **ddorwin** | WebXR contributor, #815 author | Non-visual XR use cases; spec language barrier analysis | ⬜ Not contacted |
| **crlandsc** | Contributor, Spatial_Audio_Framework | Spatialization algorithms; real-time rendering | ⬜ Not contacted |
| **ali-vosoughi** | Contributor, Spatial_Audio_Framework | Ambisonic processing & signal flow | ⬜ Not contacted |
| **jacobhollebon** | Contributor, Spatial_Audio_Framework | Spatial audio architecture & design | ⬜ Not contacted |
| **BinWang28** | Maintainer, audio-ai-hub | HRTF research; spatial speech perception; personalized HRTFs | ⬜ Not contacted |
| **TheBarmaEffect** | Spatial audio engine designer | Perception-first spatial audio engine design | ⬜ Not contacted |
| **timfain** | Jaunt VR | Spatial content creation & rendering pipelines | ⬜ Not contacted |
| **Ben-Esquivel** | Java DAW spatial audio | HRTF/binaural rendering in Java DAW pipelines | ⬜ Not contacted |
| **riccardobl** | jmePhonon | Ambisonics performance optimization in Godot | ⬜ Not contacted |

### 🎯 Episode 2 Goals

1. **Argue that WebXR is spatially blind** — #390 (8 years, 30+ comments) and #815 (41 comments): the spec has no spatial audio API and assumes eyes-only perception
2. **Establish glTF as the accidental spatial audio standard** — Three concurrent proposals (KHR_audio_emitter #2137, KHR_audio_graph #2632, KHR_audio_environment #2631) are closer to a complete spatial audio pipeline than WebXR
3. **Contrast two competing philosophies** — Server-side binaural (Mach1/Avnerus) vs. client-side physics-accurate (Mumble/Krzmbrzl)
4. **Expose the mobile spatial audio gap** — Omnitone #2: billion mobile users can't experience 3D audio; open for a decade
5. **Flag the reproducibility crisis** — ISM bugs (#58) and HRTF dataset loading failures (#55) undermine spatial audio science

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### 🔥 Core Question
Is the WebXR spec blind to non-visual perception? Can MR interfaces survive without depth, camera control, and device parity?

### 🔥 Confirmed GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Key Insight |
|---|---|---|---|---|
| 1 | **Dense pointcloud from depth sensors** | [ARCore #120](https://github.com/google-ar/arcore-android-sdk/issues/120) | 🔴 357 comments, 25 👍, 6 years old | The dominant Android AR platform still can't deliver dense depth pointclouds. Without surface geometry, MR holograms float in mid-air with no physical grounding. |
| 2 | **Device support requests (8+ years!)** | [ARCore #89](https://github.com/google-ar/arcore-android-sdk/issues/89) | 🔴 589 comments! | Perceptual accessibility crisis. If your AR app only works on 5 devices, you exclude the majority. |
| 3 | **Camera control (flashlight/auto-exposure)** | [ARCore #153](https://github.com/google-ar/arcore-android-sdk/issues/153) | 🔴 76 comments | Camera = perceptual bottleneck. No flashlight/auto-exposure API. AR is at the mercy of the OS camera app. |
| 4 | **Spec language precludes non-visual uses** | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) | 🔴 41 comments, assigned to @toji | The spec literally assumes eyes-only perception. |
| 5 | **Wayfinding crisis in immersive sessions** | [WebXR #992](https://github.com/immersive-web/webxr/issues/992) | 🔴 36 comments | Users don't know where they are in XR — fundamental spatial-awareness gap. Core human abilities that XR interfaces break. |
| 6 | **Dynamic foveation & visibility masking** | [WebXR #1420](https://github.com/immersive-web/webxr/issues/1420) | 🟡 Rendering asymmetry as perceptual-performance lever | @AdaRoseCannon (W3C): high-res center, low-res periphery as a perceptual optimization. |
| 7 | **SpectatorView calibration instability** | [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | 🟡 19 comments | HoloLens ↔ phone calibration that works once and never again. Fundamental research reproducibility blocker. |
| 8 | **Holograms sticking to camera** | [MRC #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) | 🟡 18 comments | Even geometrically correct placement is rejected if it drifts. The #1 MR registration failure. |
| 9 | **AR.js architecture debates** | [AR.js #681](https://github.com/AR-js-org/AR.js/issues/681) | 🟡 ECS architecture proposal | Kalwalt's component-based architecture → pluggable tracking/rendering/interaction systems for MR. |
| 10 | **Multi-camera AR support** | [AR.js #26](https://github.com/AR-js-org/AR.js/issues/26) | 22 comments | No API to choose camera on multi-camera devices. Front vs. back cameras have different FOV, distortion, latency. |
| 11 | **MX Ink stylus for Meta Quest** | [MRTK #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) | 🟡 Platform convergence without interface abstraction | Quest user wants HoloLens tools. Input fragmentation breaks MR presence. |
| 12 | **ARCore body pose tracking** | [ARCore #1275](https://github.com/google-ar/arcore-android-sdk/issues/1275) | 21 comments | Full-body pose tracking for MR interfaces still unsupported. |
| 13 | **ARKit rear camera faces** | [ARKit-CoreLocation #714](https://github.com/olucurious/Awesome-ARkit/issues/714) | 🟡 New camera paradigms | Augmented Faces on rear cameras — the visual system adapts to lighting conditions automatically; AR can't. |
| 14 | **Vendor plugin architecture in MRTK** | [MRTK #511](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/511) | 🟡 Architectural | Should vendor RealityProviders live inside MRTK core? High-priority architectural decision. |
| 15 | **Passthrough quality & SE(3) anchor drift** | [IvanCampos/visionOS-examples](https://github.com/IvanCampos/visionOS-examples) | 🟡 Frequently updated | Apple Vision Pro passthrough contrast/resolution limits and SE(3) anchor instability in dynamic environments. |

### 👤 Guest Targets — Episode 3

| Name | Repo / Role | What They'll Bring | Status |
|---|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k⭐) | Web AR pioneer; evolution from marker-based to image/geospatial tracking; AR.js 2→3 community rebuild | ⬜ Not contacted |
| **hiukim** | Creator, MindAR (2.7k⭐) | On-device image/face tracking with TensorFlow.js; production-ready AR | ⬜ Not contacted |
| **nicolocarpignoli** | Maintainer, AR.js | Community-driven rebuild; iOS/Safari AR challenges (#302); geospatial AR accuracy (#288); maintainer recruitment (#609) | ⬜ Not contacted |
| **kalwalt** | Author, AR.js-new ECS proposal | Component-based architecture for MR; pluggable tracking/rendering/interaction systems (#681) | ⬜ Not contacted |
| **maluoi** | Maintainer, StereoKit (1.1k⭐) | XR engine architecture; OpenXR + WebXR dual-backend design; MR interface patterns | ⬜ Not contacted |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration assignee (#221, #228); SpectatorView fragility | ⬜ Not contacted |
| **bkonyves** | Google, AR/VR engineering | Google's spatial computing platform vision; reference space design; ARCore depth & camera control gaps | ⬜ Not contacted |
| **SimonScholl** | ARCore pointcloud advocate (#120) | Depth sensing for AR; Tango-to-ARCore transition; dense surface mapping challenges | ⬜ Not contacted |
| **inio** | ARCore device support tracker (#89) | Longest-running ARCore issue — device fragmentation & perceptual access | ⬜ Not contacted |
| **jpeltone** | ARCore rear-camera faces (#714) | Augmented Faces on rear cameras; new camera paradigms | ⬜ Not contacted |
| **ROBYER1** | ARCore body pose tracking (#1275) | Human body pose tracking for MR interfaces | ⬜ Not contacted |
| **Andrew Hart** | ARKit-CoreLocation (5.5k⭐) | AR + GPS-scale spatial data; indoor-outdoor navigation bridge | ⬜ Not contacted |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation & visibility masking (#1420); accessibility; spec language for non-visual XR (#815) | ⬜ Not contacted |
| **cwilso** | WebXR spec contributor | Author of #390 and #815; understands the spec's visual bias from the inside | ⬜ Not contacted |
| **toffan** | WebXR contributor | DOM overlays in XR (#1414); compositing layers; visibility-mask events | ⬜ Not contacted |
| **keveleigh** | Microsoft MRTK maintainer | Vendor plugin architecture (#511); MRTK documentation gaps (#987); input abstraction strategy | ⬜ Not contacted |
| **chrisfromwork** | Microsoft MRC | SpectatorView calibration; hologram registration | ⬜ Not contacted |
| **Ivan Campos** | Creator, visionOS-examples (405⭐) | Apple Vision Pro spatial UI patterns; SE(3) anchor stability; passthrough quality | ⬜ Not contacted |
| **dongyoonpark** | Microsoft MRDL | Periodic Table of the Elements on HoloLens 2; MR interaction design | ⬜ Not contacted |
| **richardinerickson** | Microsoft MRDL | Surfaces MR app; tactile sensation via visual/audio/hand tracking | ⬜ Not contacted |
| **cabanier** | W3C Immersive Web Working Group | WebXR DOM overlays; visibility & rendering layers specification | ⬜ Not contacted |
| **himorin** | WebXR contributor | Security & privacy of spatial mapping data; WebXR API design | ⬜ Not contacted |
| **chrisdavidmills** | WebXR contributor | Visibility-mask events; projection-layer compositing | ⬜ Not contacted |
| **danrossi** | WebXR contributor | WebXR layers & projection-layer work; rendering pipeline | ⬜ Not contacted |
| **aphillia** | WebXR contributor | XR input profiles; internationalization for spatial interaction | ⬜ Not contacted |

### 🎯 Episode 3 Goals

1. **Argue that WebXR is architecturally visually blind** — #815 (41 comments) and #992 (36 comments) prove the spec assumes eyes-only perception
2. **Expose ARCore's depth-sensing gap as a perceptual crisis** — 357 comments over 6 years; without surface geometry, MR holograms are untethered
3. **Frame AR.js 2→3 as a perceptible architectural shift** — ECS modularity enables adaptive perceptual pipelines that monolithic architecture cannot
4. **Connect input fragmentation to presence collapse** — MRTK #914 (MX Ink on Quest) and #511 (vendor plugins) mean spatial interface designers must choose between ecosystems
5. **Make the case for maintenance as perceptual accessibility** — ARCore #89 (589 comments!) is a standing indictment of prioritizing new hardware over perceptual inclusivity

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
| **Perceptual ≠ Measured** | ✅ (ALVR #334, WiVRn #1099) | — | ✅ (SpectatorView calibration) |
| **Cross-modal perception** | ✅ (vestibular-visual conflict) | ✅ (auditory faster than visual) | ✅ (haptics as afterthought) |

---

## Repository Structure Guide

```
human-perception-podcast/
├── INITIAL-EPISODE-OUTLINE.md          ← You are here
├── EPISODE_OUTLINE.md                   ← Consolidated canonical outline
├── HOT-DEBATES-AUDIT.md                 ← Live audit of GitHub issue debates
├── GUEST_DIRECTORY.md                   ← Structured guest directory
├── GITHUB-RESEARCH-ADDENDUM.md          ← Continuously updated research addendum
├── RESEARCH-Database.md                 ← Annotated bibliography
├── episodes/
│   ├── episode-1-draft.md              ← Episode 1 recording materials
│   ├── episode-2-draft.md              ← Episode 2 recording materials
│   └── episode-3-draft.md              ← Episode 3 recording materials
└── README.md
```

## How to Contribute

1. **Pick an episode issue** — [#13](https://github.com/bro26man-hash/human-perception-podcast/issues/13) (E1), [#14](https://github.com/bro26man-hash/human-perception-podcast/issues/14) (E2), or [#54](https://github.com/bro26man-hash/human-perception-podcast/issues/54) (E3)
2. **Add issue links** from the GitHub repos above as comments on the relevant issue
3. **Tag potential guests** — see `GUEST_DIRECTORY.md` for full contact and research context
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates

---

*Last research sync: 2026-09-18. See `HOT-DEBATES-AUDIT.md` and `GITHUB-RESEARCH-ADDENDUM.md` for the full continuously updated audit.*
