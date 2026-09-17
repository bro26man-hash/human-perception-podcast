# 🎙️ The Future of Human Perception — Episode Outline (Enhanced Sept 2026)

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **enhanced episode outline** incorporating fresh GitHub research from September 2026.
> For the canonical outline, see `EPISODE_OUTLINE.md`. For the live audit, see `GITHUB-RESEARCH-ADDENDUM.md`.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos |
|---|---|
| Web 3D / WebXR | `mrdoob/three.js` (115.6k ⭐), `playcanvas/engine` (16.9k ⭐), `immersive-web/webxr` (3.1k ⭐), `Hubs-Foundation/hubs` (2.2k ⭐) |
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
9. **🔥 NEW: Android camera-IMU clock offsets** — ARCore #1779: 13–35ms hardware clock skew between camera and IMU on mid-range Xiaomi/OPPO devices. The visual feed lags behind vestibular input by up to 35ms — invisible to developers but catastrophic for perceptual stability.
10. **🔥 NEW: WiVRn #1099 — Quest 3 passthrough refocus freeze** — After entering system passthrough and regaining focus, VRChat and other apps freeze for up to 47 minutes. `wait_for_scheduled_free()` holds per-client frame slots scheduled *days* in the future. The compositor reports healthy 80 FPS while the user experiences minutes-long freezes. This is the ultimate "perceptual vs. measured" latency bug.

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets (reduce average ms) are wrong — we need to stabilize frame delivery instead.

> **🔥 NEW: Acoustic echo cancellation is a spatial-perception problem.** The MixedReality-WebRTC #157 thread reveals that AEC — critical for spatial audio presence — is fundamentally broken in current MR stacks. Without echo cancellation, the room's acoustics contaminate the spatial audio model, making it impossible to determine whether a sound is "outside" the headset or "inside" the room. This isn't an audio quality issue; it's a *perceptual calibration* failure.

> **🔥 NEW: The brain may detect frame irregularity, not average latency.** WiVRn #1099's 47-minute freeze after passthrough refocus, combined with ALVR #334's "missing latency" findings, suggests the perceptual system is far more sensitive to timing jitter and delivery inconsistencies than to raw pipeline depth. This reframes optimization from "reduce ms" to "stabilize delivery."

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
| **🆕 SimonScholl** | ARCore pointcloud advocate (#120) | Depth sensing for AR; Tango-to-ARCore transition; dense surface mapping |
| **🆕 inio** | ARCore device support tracker (#89) | Longest-running ARCore issue — device fragmentation & perceptual access |
| **🆕 IceyMint** | WiVRn reporter | Found the Quest 3 passthrough refocus freeze (#1099) |
| **🆕 maxkojju** | WiVRn reporter | Pico GPU frame scheduling issues |
| **🆕 zoeleu** | WiVRn reporter | Quest 3 high refresh rate support (#1078) |
| **🆕 AndrewJDR** | webxr-ar-module contributor | #44 — camera feed delay in AR sessions |
| **🆕 tangobravo** | webxr-ar-module contributor | #78, #77 — AR module gaps for handheld AR |

### Key GitHub Issues to Track

| Repo | Issue | Topic | Comments | Relevance |
|---|---|---|---|---|
| `WiVRn/WiVRn` | [#1099](https://github.com/WiVRn/WiVRn/issues/1099) | Quest 3 passthrough refocus freeze | 40+ | 🔥 Perceptual vs. measured latency |
| `WiVRn/WiVRn` | [#1078](https://github.com/WiVRn/WiVRn/issues/1078) | 144/207/240Hz support for Quest 3 | 1 | Refresh rate → latency reduction |
| `ValveSoftware/SteamVR-for-Linux` | [#21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) | Tracking not smooth and a little delayed | 97+ | Foundational VR latency report |
| `polygraphene/ALVR` | [#334](https://github.com/polygraphene/ALVR/issues/334) | Latency measurements missing info / incorrect | — | Industry underreporting by 30–50% |
| `microsoft/MixedReality-WebRTC` | [#157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | Acoustic echo cancellation broken | 17 | AEC failure = spatial audio collapse |
| `google-ar/arcore-android-sdk` | [#1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | Camera↔IMU clock offset 13–35ms | — | Invisible but catastrophic perceptual lag |
| `microsoft/OpenXR-MixedReality` | [#131](https://github.com/microsoft/OpenXR-MixedReality/issues/131) | Frame timestamp precision & D3D12 | — | HoloLens 2 performance |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How does spatial audio create the illusion of a 3D world from two ears — and why does the WebXR spec still lack a spatial audio API?

### Key Topics

1. **Head-Related Transfer Functions (HRTFs)** — how the shape of your ears filters sound to give you elevation and front-back cues. Why generic HRTFs don't work for everyone.
2. **Ambisonics & Higher-Order Ambisonics (HOA)** — the mathematics of encoding 3D sound fields. FOA vs. HOA tradeoffs for real-time rendering.
3. **🔥 NEW: The glTF audio extension frontier** — KhronosGroup/glTF now has *three* active audio extension proposals: `KHR_audio_emitter` (#2137, 58 comments), `KHR_audio_graph` (#2632), and `KHR_audio_environment` (#2631). These would define how spatial audio sources, audio graphs, and acoustic environments are encoded in 3D asset pipelines. This is the closest thing to a spatial audio standard for the web.
4. **🔥 NEW: Layered audio architecture proposal** — Issue #2561 (rudybear): proposes a composing architecture where `KHR_audio_emitter` + `KHR_audio_graph` + `KHR_audio_environment` form a complete spatial audio stack inside glTF. This is the most serious attempt to standardize spatial audio for 3D content delivery.
5. **🔥 NEW: Synchronized immersive video + audio in glTF** — Issue #2506 (Ben Erwin / powersimple): calls for timeline metadata, stereo/volumetric video types, and AV sync in glTF. This bridges spatial audio and spatial video — the "immersive media" standard we've been waiting for.
6. **🔥 NEW: WebXR #390 — 8-year-old spec gap** — The WebXR Device API has no built-in spatial audio specification. CSS/HTML spatial audio for WebXR has been debated since 2018 with no spec progress.
7. **🔥 NEW: Omnitone #2 — 10-year-old mobile gap** — Chrome's Omnitone spatial audio library doesn't work on mobile browsers. 23 comments across a decade, no resolution. Billion mobile users excluded from 3D audio.
8. **🔥 NEW: Hubs spatial audio scaling failures** — #1853 (30 comments), #2643 (30 comments), #5057 (24 comments): spatial audio degrades with more users. CPU load collapses spatial quality exactly when social presence matters most.
9. **Personalized HRTFs** — modeling individual ear geometry. The Iowa auditory dataset, NIIP dual-ridge method, and the unsolved problem of real-time personalization on consumer hardware.
10. **Spatial presence vs. localization** — can you feel "present" in a space without accurate externalization? The ventriloquism effect and its XR implications.
11. **Multi-device synchronization** — freeman-jiang/beatsync: clock sync precision across correlated haptic, audio, and visual events for presence maintenance.
12. **Accessibility & spatial audio** — Sound of Vision, leading SMEs and researches for individuals with low vision / blindness, and Amelia Eckard's Apple Vision Pro research.
13. **Spatial audio rendering on constrained devices** — avnerus's Mach1 Studios approach: real-time binaural rendering on mobile/standalone hardware.
14. **🔥 NEW: ISM reverberation modeling bug** — Spatial_Audio_Framework #58: Image Source Method bands are summed incorrectly, invalidating perceptual room-acoustics research built on this library.
15. **🔥 NEW: SONIMO HRTF dataset loading bugs** — Spatial_Audio_Framework #55: loading bugs affect perceptual accuracy of spatial audio rendering.

### The Hot Debate

> **The WebXR spec is visual-only for spatial audio — and that's a design failure.** Chrome's Omnitone implements FOA but not full HRTF-based binaural rendering. The immersive-web working group has debated spatial audio extensions for years with no consensus. Meanwhile, native platforms (Apple, Meta) ship proprietary spatial audio that developers can't access or extend. The web is the only platform that should be truly open for spatial audio — and it's falling behind.

> **🔥 NEW: glTF is becoming the accidental spatial audio standard.** With three concurrent audio extension proposals (`KHR_audio_emitter`, `KHR_audio_graph`, `KHR_audio_environment`), glTF is closer than WebXR to defining a complete spatial audio pipeline for 3D content. The question is whether the W3C Immersive Web group will collaborate with Khronos or let glTF become the de facto standard while WebXR remains visual-only.

> **🔥 NEW: Spatial audio fundamentally breaks under social load.** Hubs #1853/#2643/#5057 show that spatial audio quality collapses under CPU load exactly when social presence matters most. This isn't a rendering bug — it's a perceptual architecture problem. Current spatial audio engines weren't designed for multi-user social XR.

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
| **🆕 pmlt** | WebAudio/web-audio-api | #2386 — Multi-channel PannerNode support |
| **🆕 mastr-ch13f** | easyeffects | #2783 — HRIR support for Convolver Effect |

### Key GitHub Issues to Track

| Repo | Issue | Topic | Comments | Relevance |
|---|---|---|---|---|
| `KhronosGroup/glTF` | [#2137](https://github.com/KhronosGroup/glTF/pull/2137) | KHR_audio_emitter PR | 58 | Spatial audio source standard |
| `KhronosGroup/glTF` | [#2561](https://github.com/KhronosGroup/glTF/issues/2561) | Layered audio architecture proposal | 2 | Full spatial audio stack in glTF |
| `KhronosGroup/glTF` | [#2632](https://github.com/KhronosGroup/glTF/pull/2632) | KHR_audio_graph PR | 2 | Audio graph standard |
| `KhronosGroup/glTF` | [#2631](https://github.com/KhronosGroup/glTF/pull/2631) | KHR_audio_environment PR | 1 | Acoustic environment standard |
| `KhronosGroup/glTF` | [#2506](https://github.com/KhronosGroup/glTF/issues/2506) | Synchronized immersive video+audio | 2 | AV sync for XR |
| `immersive-web/webxr` | [#390](https://github.com/immersive-web/webxr/issues/390) | Hook up CSS/HTML spatial audio | — | 🔥 8-year spec gap |
| `GoogleChrome/omnitone` | [#2](https://github.com/GoogleChrome/omnitone/issues/2) | Support for mobile browsers | 23 | 🔥 10-year unresolved gap |
| `Hubs-Foundation/hubs` | [#1853](https://github.com/Hubs-Foundation/hubs/issues/1853) | Spatial audio quality degradation | 30 | Social XR audio breaks |
| `Hubs-Foundation/hubs` | [#2643](https://github.com/Hubs-Foundation/hubs/issues/2643) | User audio broken | 30 | Social XR audio breaks |
| `Hubs-Foundation/hubs` | [#5057](https://github.com/Hubs-Foundation/hubs/issues/5057) | Audio at scale | 24 | Social XR audio breaks |
| `leomccormack/Spatial_Audio_Framework` | [#58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) | ISM RIR incorrect summing | — | Research reproducibility crisis |
| `leomccormack/Spatial_Audio_Framework` | [#55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55) | SONIMO dataset loading bugs | — | Perceptual accuracy compromised |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** Mixed reality interfaces, hologram drift, and wayfinding — and whether the WebXR spec is blind to non-visual perception.

### Key Topics

1. **The MR interface stack** — from hand tracking (Metric Theory, Ultraleap) to gaze anchoring, temporal stabilization, and the illusion of a stable cursor in mid-air.
2. **Hologram drift & registration** — MixedRealityCompanionKit #228: SpectatorView calibration that works once and never again. Why persistent hologram registration is unsolved outside lab conditions.
3. **🔥 NEW: Holograms sticking to camera** — MRC #221 (18 comments): Holograms that "stick to camera" instead of staying anchored reproduce reprojection drift across network stacks. This breaks the fundamental promise of mixed reality — digital content that stays where you put it.
4. **🔥 NEW: ARCore depth sensing & pointcloud** — google-ar/arcore-android-sdk #120 (357 comments, 25 👍): a 6-year-old feature request for dense pointcloud from depth sensors. This is fundamental to MR — you can't anchor holograms to real surfaces without accurate depth. The Tango-to-ARCore transition left a gap in depth-first AR.
5. **🔥 NEW: ARCore device support fragmentation** — ARCore #89 (589 comments!): the longest-running open issue in the repo. Device support requests span 8+ years. This isn't just a feature request — it's a *perceptual accessibility* problem. If your AR app only works on 5 devices, you're excluding the majority of users from spatial computing.
6. **🔥 NEW: ARCore camera control** — ARCore #153 (76 comments): no API for flashlight, auto-exposure, or torch control. For AR to work in varied lighting, you need programmatic camera control. Without it, the perceptual experience is at the mercy of the OS camera app.
7. **🔥 NEW: WebXR #815 — Spec language precludes non-visual uses** — 41 comments. The WebXR spec is heavily vision-centric, leaving accessibility gaps for non-visual XR experiences.
8. **🔥 NEW: WebXR #992 — Wayfinding crisis** — 36 comments. Users in immersive XR sessions can't find content that wasn't visible when they entered — fundamental wayfinding problem. Spatial memory and navigation are core human abilities; XR interfaces that break them violate basic perceptual expectations.
9. **🔥 NEW: WebXR #1420 — Dynamic foveation** — Dynamic foveation and visibility masking as tools to reduce rendering cost while preserving perceptual quality. @AdaRoseCannon (W3C, Foveated Rendering CG) leading this work.
10. **🔥 NEW: WebXR #1414 — DOM overlays in canvas** — WebXR integration with HTML-in-canvas rendering challenges.
11. **Wayfinding in MR** — cognitive load of spatial navigation when the display medium is yourself. Audio-based wayfinding as a complementary channel.
12. **Non-visual XR interfaces** — the WebXR Device API defines `viewer` and `local` reference spaces but treats haptics, spatial audio, and biometric sensors as afterthoughts. The spec is fundamentally visual-centric.
13. **The "posure" problem** — if your virtual body is wrong, your spatial judgment is wrong. Avatar fidelity and its downstream effects on presence and spatial reasoning.
14. **Hand tracking vs. controllers** — ergonomic research on pinch, grab, and pointing interactions. The missing middle ground between raw hand tracking and 6-DoF controllers.
15. **Architectural implications** — StereoKit's OpenXR + WebXR dual backend, and what it means for cross-platform MR interface design.
16. **AR.js 2→3 transition** — the creator `jeromeetienne` discusses the community-driven rebuild and what it means for the future of web-based spatial interfaces.
17. **🔥 NEW: MX Ink MR stylus for Meta Quest** — MRTK #914: Platform convergence without interface abstraction. Input fragmentation means spatial interface designers must choose between ecosystems.
18. **🔥 NEW: Vendor plugin architecture** — MRTK #511: Should vendor-specific RealityProviders live inside the MRTK core? High-priority architectural decision with 2 active commenters. The answer determines whether MR interfaces can be truly cross-platform.

### The Hot Debate

> **Is the WebXR spec blind to non-visual perception?** The spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. You can "see" a virtual object in WebXR but you cannot reliably "hear" it or "feel" it. For MR — where the physical world is the backdrop — this is a fundamental architectural gap that no working group has seriously addressed.

> **🔥 NEW: ARCore's depth-sensing gap is a perceptual crisis.** Issue #120 (357 comments, 6 years old) reveals that the dominant Android AR platform still can't deliver dense depth pointclouds from consumer hardware. Without accurate surface geometry, MR holograms float in mid-air with no physical grounding. This isn't a feature request — it's the missing foundation of spatial computing on the most widely deployed AR platform.

> **🔥 NEW: Device fragmentation is a perceptual accessibility issue.** ARCore #89 (589 comments!) isn't just about adding support — it's about whether spatial computing is available to everyone or only to owners of the latest flagship devices. The 8-year-old open issue is a standing indictment of the industry's prioritization of new hardware over perceptual inclusivity.

> **🔥 NEW: WebXR's wayfinding crisis.** Issue #992 (36 comments) reveals that users in immersive XR can't find content that wasn't visible on entry. This breaks fundamental human spatial memory and navigation abilities — core perceptual capacities that XR interfaces should support, not undermine.

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
| **🆕 fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration (#228, #221); SpectatorView |
| **🆕 chrisfromwork** | Microsoft MRC | Hologram camera sticking (#221); MR calibration |
| **🆕 AdaRoseCannon** | W3C, Foveated Rendering CG | #1420 (dynamic foveation); accessibility in XR; inclusive spatial design |
| **🆕 cabanier** | W3C Immersive Web | WebXR DOM overlays; visibility & rendering layers |
| **🆕 himorin** | WebXR contributor | Security & privacy of spatial mapping data |
| **🆕 chrisdavidmills** | WebXR editor | Visibility-mask events; projection-layer compositing |
| **🆕 danrossi** | WebXR layers work | Projection-layer rendering pipeline |
| **🆕 aphillia** | WebXR input profiles | i18n for spatial interaction |
| **🆕 Ivan Campos** | visionOS-examples (405⭐) | Apple Vision Pro passthrough quality & SE(3) anchor drift |
| **🆕 dongyoonpark** | Microsoft MRDL | Periodic Table on HoloLens 2; MR interaction design |
| **🆕 richardinerickson** | Microsoft MRDL | Surfaces MR app; tactile sensation via multi-modal feedback |

### Key GitHub Issues to Track

| Repo | Issue | Topic | Comments | Relevance |
|---|---|---|---|---|
| `microsoft/MixedRealityCompanionKit` | [#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | Calibration instability | 19 | Hologram registration reproducibility |
| `microsoft/MixedRealityCompanionKit` | [#221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) | Holograms sticking to camera | 18 | 🔥 Fundamental MR registration failure |
| `google-ar/arcore-android-sdk` | [#89](https://github.com/google-ar/arcore-android-sdk/issues/89) | Device support requests | 589 | 🔥 Perceptual accessibility crisis |
| `google-ar/arcore-android-sdk` | [#120](https://github.com/google-ar/arcore-android-sdk/issues/120) | Dense pointcloud from depth | 357 (25👍) | 🔥 MR surface anchoring foundation |
| `google-ar/arcore-android-sdk` | [#153](https://github.com/google-ar/arcore-android-sdk/issues/153) | Camera control (flashlight/auto-exposure) | 76 | Lighting-aware AR perception |
| `google-ar/arcore-android-sdk` | [#1275](https://github.com/google-ar/arcore-android-sdk/issues/1275) | Body pose tracking request | 21 | Full-body MR interfaces |
| `immersive-web/webxr` | [#815](https://github.com/immersive-web/webxr/issues/815) | Spec language precludes non-visual uses | 41 | 🔥 Visual-centric spec gap |
| `immersive-web/webxr` | [#992](https://github.com/immersive-web/webxr/issues/992) | Wayfinding crisis | 36 | 🔥 Spatial navigation breakdown |
| `immersive-web/webxr` | [#1420](https://github.com/immersive-web/webxr/issues/1420) | Dynamic foveation | — | Perceptual performance lever |
| `immersive-web/webxr` | [#1414](https://github.com/immersive-web/webxr/issues/1414) | HTML-in-canvas integration | — | DOM overlay rendering |
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | [#914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) | MX Ink for Meta Quest | — | Platform convergence w/o abstraction |
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | [#511](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/511) | Vendor plugin architecture | 2 | Cross-platform MR interface design |
| `IvanCampos/visionOS-examples` | — | Passthrough quality & SE(3) drift | — | Vision Pro MR fidelity |

---

## Cross-Episode Themes

| Theme | Episode 1 | Episode 2 | Episode 3 |
|---|---|---|---|
| The brain as final arbiter of reality | ✅ (temporal vs. average latency) | ✅ (audio presence paradox) | ✅ (visual-centric spec gap) |
| Open-source vs. proprietary stacks | ✅ (open VR latency tools) | ✅ (open spatial audio frameworks) | ✅ (open MR toolkits) |
| The web platform as the egalitarian frontier | ✅ (Web AR, AR.js) | ✅ (Omnitone vs. native) | ✅ (WebXR spec gap) |
| Perceptual access & fragmentation | ✅ (device latency variability) | ✅ (HRTF personalization gap) | ✅ (ARCore device support, 589 comments) |
| Standards convergence (glTF ↔ WebXR) | — | ✅ (KHR_audio_* extensions) | ✅ (WebXR spec gaps) |
| 🆕 Social XR auditory collapse | — | ✅ (Hubs #1853/#2643/#5057) | — |
| 🆕 Research reproducibility crisis | ✅ (calibration instability) | ✅ (ISM bug, SONIMO bugs) | ✅ (SpectatorView) |
| 🆕 Platform convergence without abstraction | — | — | ✅ (MRTK #914, #511) |

---

## Repository Contributions Guide

1. **Pick an episode issue** — #13 (E1), #14 (E2), or #15 (E3) for research & outreach.
2. **Add issue links** from the GitHub repos above as comments on the relevant issue.
3. **Tag potential guests** — see `GUEST_DIRECTORY.md` for full contact and research context.
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates.

---

*Last research sync: 2026-09-17. See `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md` for the full continuously updated audit.*
