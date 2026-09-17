# 🎙️ The Future of Human Perception — Podcast Production Outline

> **Production hub for episode planning, guest research, and GitHub-sourced hot debates.**
> Last updated: September 2026

---

## Series Vision

Why does AR/VR still feel "not quite real"? What does UX design mean when the interface is the entire room? And if vision is half the battle, why is hearing the whole war?

This podcast explores the engineering and human science behind how technology reshapes perception — through deep-dive interviews with the researchers and developers pushing the boundaries, and by surfacing the hottest open debates from the most active GitHub repositories.

---

## Research Backbone — Most Active AR / Spatial Computing Repos

| Repo | Stars | Focus | Key Issues |
|---|---|---|---|
| [immersive-web/webxr](https://github.com/immersive-web/webxr) | 3.1k | WebXR Device API spec | #1420 Foveation, #1414 HTML-in-canvas, #1423 Haptics, #1400 Event-loop races, #390 Spatial Audio, #815 Non-visual, #992 Wayfinding |
| [Unity-Technologies/arfoundation-samples](https://github.com/Unity-Technologies/arfoundation-samples) | 3.4k | AR Foundation samples | Camera feed lag (#1206), plane detection |
| [playcanvas/engine](https://github.com/playcanvas/engine) | 16.7k | Real-time 3D engine for web XR | Render pipeline, foveation |
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 15.8k | Web-based AR in the browser | Tracking stability, markerless AR, maintainer recruitment |
| [Hubs-Foundation/hubs](https://github.com/Hubs-Foundation/hubs) | 2.2k | Social VR/AR platforms | Presence, spatial audio scaling |
| [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | 6.1k | MRTK for HoloLens & Windows MR | Spatial mapping, hand tracking, MX Ink on Quest |
| [microsoft/MixedReality-WebRTC](https://github.com/microsoft/MixedReality-WebRTC) | 944 | WebRTC for mixed reality | Photon capture, AEC failure, spatial audio |
| [GoogleChrome/omnitone](https://github.com/GoogleChrome/omnitone) | 911 | Binaural rendering for the web | Mobile spatial audio gap (#2, open since 2016) |
| [leomccormack/Spatial_Audio_Framework](https://github.com/leomccormack/Spatial_Audio_Framework) | 748 | Ambisonics & HRTF research | ISM bugs (#58), HRTF dataset loading (#55) |
| [KhronosGroup/glTF](https://github.com/KhronosGroup/glTF) | 10k+ | 3D asset standard | KHR_audio_emitter (#2137), KHR_audio_graph (#2632), KHR_audio_environment (#2631) |
| [WiVRn/WiVRn](https://github.com/WiVRn/WiVRn) | — | Open-source VR runtime | Temporal irregularity (#282), per-client frame stalls (#1099) |
| [ValveSoftware/openvr](https://github.com/ValveSoftware/openvr) | — | OpenVR runtime | Reprojection error (#659), latency benchmark crisis (#249) |
| [polygraphene/ALVR](https://github.com/polygraphene/ALVR) | — | PC VR streaming | "Missing" 33.6ms latency (#334) |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Target Release:** Q4 2026  
**Status:** 🔍 Research Complete & Guest Outreach Initiated  
**GitHub Issue:** [#67](https://github.com/bro26man-hash/human-perception-podcast/issues/67)

### Core Question
*Why does AR/VR still feel "not quite real," and how close are we to closing the perceptual gap?*

### 🔥 Hottest GitHub-Sourced Debates

| Debate | Source | Key Insight |
|---|---|---|
| **Temporal irregularity vs. average latency** | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) (40 comments) | Stutter = irregularity, not depth. The brain detects frame pacing irregularity, not absolute latency. Paradigm shift. |
| **Per-client scheduled frame stalls (47-min freeze)** | [WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) | Compositor reports 80 FPS, but the client freezes for 47+ minutes. The brain's vestibular system doesn't care about compositor health. |
| **"Missing" 33.6ms latency in VR streaming** | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) | 30-50% underreporting. If optimizing against the wrong number, the "20ms rule" may be unreachable even when reported numbers look fine. |
| **Camera↔IMU clock offset 13-35ms** | [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | Hardware clock sync gap on mid-range Android. Rotation becomes translation. Invisible to devs, catastrophic for perception. |
| **Acoustic echo cancellation broken in MR** | [MR-WebRTC #157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | AEC failure = spatial audio collapse. Not an audio quality issue — a perceptual calibration failure. |
| **No standardized latency benchmark** | [OpenVR #249](https://github.com/ValveSoftware/openvr/issues/249) | Metrology crisis. Industry uses different methodologies — comparisons are meaningless. |
| **Reprojection error in timewarp** | [OpenVR #659](https://github.com/ValveSoftware/openvr/issues/659) | When predicted head pose is wrong, the warped frame causes visceral discomfort. Last line of defense, and it's failing. |
| **Dynamic Foveation privacy** | [WebXR #1420](https://github.com/immersive-web/webxr/issues/1420) | AdaRoseCannon (Google): gaze data must never reach web content; WebXR should handle foveation at the browser level. |

### 🎤 Potential Guests — Episode 1

| Name | Affiliation | Expertise | Key Issue |
|---|---|---|---|
| **AdaRoseCannon** | Google (W3C) | Dynamic Foveation spec; gaze-based rendering; cross-sensory perception | [webxr #1420](https://github.com/immersive-web/webxr/issues/1420) |
| **Rik Cabanier** | Immersive Web Inc. | Inline stereo; haptics policy; HTML-in-canvas prototype | [webxr #1414](https://github.com/immersive-web/webxr/issues/1414) |
| **xytovl** | WiVRn maintainer | Temporal irregularity finding (#282); per-client frame stalls (#1099) | [WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) |
| **jn-3d** | ALVR developer | VR streaming stack forensics; "missing" 33.6ms latency discovery | [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) |
| **rutmir** | ARCore issue reporter | Camera↔IMU clock offset measurement on Xiaomi | [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) |
| **chrisdavidmills** | WebXR Spec Editor | Session lifecycle & visibility; spec governance | webxr spec discussions |
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR evolution; architecture decisions affecting perceptual latency | [AR.js #609](https://github.com/AR-js-org/AR.js/issues/609) |

### 📋 Episode Structure (45-60 min)

1. **Cold Open** (3 min) — "The moment presence broke": listener-submitted stories
2. **The Science of Latency** (10 min) — Motion-to-photon pipeline, the 20ms rule, how the brain detects timing errors
3. **The Foveation Revolution** (12 min) — Eye-tracked rendering, GPU savings, privacy implications (AdaRoseCannon interview)
4. **When the Spec Breaks** (8 min) — Event-loop race conditions, camera feed lag in production
5. **The Future: 7ms and Beyond** (10 min) — Hardware foveation, reprojection, what's next
6. **CTA & Preview** (2 min) — Next episode teaser: spatial audio and the 50ms binding window

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Target Release:** Q1 2027  
**Status:** 🔍 Research Complete & Guest Outreach Initiated  
**GitHub Issue:** [#68](https://github.com/bro26man-hash/human-perception-podcast/issues/68)

### Core Question
*If vision is half the battle, hearing is the whole war — how does spatial audio create (or break) presence?*

### 🔥 Hottest GitHub-Sourced Debates

| Debate | Source | Key Insight |
|---|---|---|
| **WebXR has no spatial audio API** | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) (30+ comments, open since 2018) | The spec has no spatial-audio element. Chrome's Omnitone implements FOA but not full HRTF. Native platforms ship proprietary audio devs can't access. |
| **Spec language precludes non-visual uses** | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) (41 comments) | The spec literally assumes eyes-only perception. "A state of visible indicates that imagery rendered by the XRSession can be seen by the user…" — no room for audio-only XR. |
| **glTF audio extensions — Emitter + Graph + Environment** | [glTF #2137](https://github.com/KhronosGroup/glTF/pull/2137), [#2632](https://github.com/KhronosGroup/glTF/pull/2632), [#2631](https://github.com/KhronosGroup/glTF/pull/2631) | Three concurrent proposals forming a complete spatial audio stack inside glTF. Is glTF becoming the accidental spatial audio standard? |
| **50ms haptic-audio binding window** | Cross-sensory perception research | When a virtual ball hits the floor, sound and haptic vibration must arrive within ~50ms or the brain flags them as "wrong." |
| **Mumble: physics-accurate spatial audio** | [Mumble #6597](https://github.com/mumble-voip/mumble/issues/6597) (22 comments) | Replacing simplistic spatial audio with proper HRTFs + Doppler + environmental effects via OpenAL-Soft. Cites IEEE paper on sound localization. |
| **Server-side vs. client-side binaural** | Mach1 Studios (#2) vs. Mumble (#6597) | "Good enough" server-side convolvers vs. client-side physics-accurate rendering — two competing philosophies for web spatial audio. |
| **Spatial audio can't scale past 20 users** | [Hubs #5057](https://github.com/Hubs-Foundation/hubs/issues/5057) | Social-scale audio: spatial audio quality collapses under CPU load. |
| **Omnitone mobile gap — decade old** | [Omnitone #2](https://github.com/GoogleChrome/omnitone/issues/2) (23 comments, open since 2016) | Billion mobile users can't experience 3D audio. The mobile spatial audio gap is a decade old. |
| **Research reproducibility crisis** | [SAF #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55), [#58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) | ISM RIR incorrect summing and HRTF dataset loading bugs — even researchers can't reproduce each other's results. |

### 🎤 Potential Guests — Episode 2

| Name | Affiliation | Expertise | Key Work |
|---|---|---|---|
| **Krzmbrzl** | Mumble VoIP maintainer | Physics-accurate spatial audio: HRTF + Doppler + environmental effects via OpenAL-Soft | [Mumble #6597](https://github.com/mumble-voip/mumble/issues/6597) |
| **Avnerus** | Mach1 Studios | Real-time binaural rendering on constrained devices via convolvers | Mach1 Studios #2 |
| **leomccormack** | Creator, Spatial_Audio_Framework | Ambisonics, HRTFs, ISM room modeling; facing reproducibility bugs | [SAF #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55) |
| **rudybear** | glTF audio extension author | KHR_audio_graph + KHR_audio_environment — layered spatial audio architecture | [glTF #2561](https://github.com/KhronosGroup/glTF/issues/2561) |
| **cwilso** | WebXR spec contributor | Author of #390 (spatial audio in WebXR); understands the spec gap from the inside | [WebXR #390](https://github.com/immersive-web/webxr/issues/390) |
| **ddorwin** | WebXR contributor | Non-visual XR use cases; spec language barrier analysis | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) |
| **alextawes19** | SYNCMR creator | Mixed reality percussion & spatialized audio; real-time audio-visual sync | [SYNC-MR](https://github.com/alextawes19/SYNC-MR) |
| **Angelos-Kard** | MR Accessibility Researcher | HoloLens 2 spatial audio for visually impaired navigation; Microsoft Spatializer | [thesis-project](https://github.com/Angelos-Kard/thesis-project) |

### 📋 Episode Structure (45-60 min)

1. **Cold Open** (3 min) — "Can you hear the shape of the room?" — binaural audio demonstrations
2. **The Missing Standard** (10 min) — Why WebXR spatial audio lags behind perceptual science; the platform lock-in problem
3. **The 50ms Binding Window** (10 min) — Cross-sensory integration; haptic-audio sync; the SYNCMR approach
4. **Sound as Wayfinding** (12 min) — MR spatial audio for accessibility; Angelos-Kard's HoloLens 2 thesis
5. **Ambisonics vs. Parametric / Server vs. Client** (8 min) — Technical deep-dive on spatial audio rendering
6. **CTA & Preview** (2 min) — Next episode teaser: interfaces beyond the flat screen

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Target Release:** Q2 2027  
**Status:** 🔍 Research Complete & Guest Outreach Initiated  
**GitHub Issue:** [#69](https://github.com/bro26man-hash/human-perception-podcast/issues/69)

### Core Question
*If the interface is the entire room, what does UX design even mean? Is the WebXR spec blind to non-visual perception?*

### 🔥 Hottest GitHub-Sourced Debates

| Debate | Source | Key Insight |
|---|---|---|
| **Is the WebXR spec blind to non-visual perception?** | [WebXR #815](https://github.com/immersive-web/webxr/issues/815) (41 comments) + [WebXR #992](https://github.com/immersive-web/webxr/issues/992) (36 comments) | The spec defines visual and input reference spaces but has no standardized spatial audio, haptic, or biometric APIs. You can "see" a virtual object but you cannot reliably "hear" it or "feel" it. |
| **HTML-in-canvas: DOM in 3D space** | [WebXR #1414](https://github.com/immersive-web/webxr/issues/1414) (14 👍) | Rik Cabanier's Three.js demo renders DOM as 3D textures. Strong community interest. Hit testing remains the open question. |
| **ARCore depth sensing gap (6 years old!)** | [ARCore #120](https://github.com/google-ar/arcore-android-sdk/issues/120) (357 comments, 25 👍) | The dominant Android AR platform still can't deliver dense depth pointclouds. Without surface geometry, MR holograms float with no physical grounding. |
| **ARCore device fragmentation (589 comments!)** | [ARCore #89](https://github.com/google-ar/arcore-android-sdk/issues/89) | Perceptual accessibility crisis. If your AR app only works on 5 devices, you exclude the majority. |
| **Camera control gap — no flashlight/auto-exposure** | [ARCore #153](https://github.com/google-ar/arcore-android-sdk/issues/153) (76 comments) | Camera = perceptual bottleneck. AR is at the mercy of the OS camera app. The brain's visual system adapts to lighting automatically — AR can't. |
| **Hologram drift & calibration fragility** | [MRC #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221), [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | Even geometrically correct placement is rejected if it drifts. Calibration that works once and never again. Fundamental reproducibility blocker. |
| **Haptics in WebXR — now or never?** | [WebXR #1423](https://github.com/immersive-web/webxr/issues/1423) | "We've been waiting for years for better haptics support. Maybe we should just implement this in WebXR?" — cabanier |
| **Wayfinding crisis in immersive sessions** | [WebXR #992](https://github.com/immersive-web/webxr/issues/992) | Users don't know where they are in XR — fundamental spatial-awareness gap. Core human abilities that XR interfaces break. |
| **Input fragmentation — MX Ink on Quest** | [MRTK #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) | Quest users want HoloLens tools. Input fragmentation breaks MR presence. |
| **AR.js 2→3: ECS architecture shift** | [AR.js #681](https://github.com/AR-js-org/AR.js/issues/681) | Component-based architecture → pluggable tracking/rendering/interaction systems for adaptive perceptual pipelines. |

### 🎤 Potential Guests — Episode 3

| Name | Affiliation | Expertise | Key Work |
|---|---|---|---|
| **Rik Cabanier** | Immersive Web Inc. | HTML-in-canvas prototype; haptics policy; inline stereo | [WebXR #1414](https://github.com/immersive-web/webxr/issues/1414) (14 👍) |
| **AdaRoseCannon** | Google (W3C) | Dynamic foveation; HTML-in-canvas; non-visual XR accessibility | [WebXR #1420](https://github.com/immersive-web/webxr/issues/1420), [WebXR #815](https://github.com/immersive-web/webxr/issues/815) |
| **SimoScholl** | ARCore depth advocate | Dense pointcloud sensing for AR; Tango-to-ARCore transition | [ARCore #120](https://github.com/google-ar/arcore-android-sdk/issues/120) |
| **bkonyves** | Google AR/VR | Spatial computing platform vision; reference space design | ARCore depth & camera control gaps |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration | [MRC #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221), [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) |
| **keveleigh** | Microsoft MRTK maintainer | Vendor plugin architecture; input abstraction strategy | [MRTK #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) |
| **Angelos-Kard** | MR Accessibility | HoloLens 2 spatial navigation; voice-first interaction; spatial mapping | [thesis-project](https://github.com/Angelos-Kard/thesis-project) |
| **s0i37** | 6DoF samples | Six-degrees-of-freedom tracking; spatial interaction | WebXR samples |

### 📋 Episode Structure (45-60 min)

1. **Cold Open** (3 min) — "Draw a circle in the air" — the challenge of spatial UI without screens
2. **HTML-in-Canvas: The Web Bridge** (10 min) — How DOM content enters 3D space; Rik Cabanier's prototype; hit testing in WebGL
3. **Haptics: The Forgotten Sense** (10 min) — Why haptics is years behind visual in WebXR; the "just implement it" debate
4. **Spatial Mapping & Wayfinding** (12 min) — MRTK vs. AR Foundation; HoloLens 2 accessibility navigation; voice-first interaction
5. **The Future Interface: Gaze + Gesture + Voice** (8 min) — Convergence of foveated rendering, hand tracking, and spatial audio
6. **CTA & Season Wrap-Up** (2 min) — Where do we go from here? The 3-year roadmap for spatial computing

---

## Cross-Episode Themes

| Theme | Episode 1 | Episode 2 | Episode 3 |
|---|---|---|---|
| **The brain as final arbiter of reality** | ✅ Temporal irregularity vs. average latency | ✅ Audio presence paradox | ✅ Visual-centric spec gap |
| **Perceptual access & fragmentation** | ✅ Device latency variability | ✅ HRTF personalization gap | ✅ ARCore #89, 589 comments |
| **Open web vs. platform lock-in** | ✅ Open VR latency tools | ✅ Omnitone vs. native spatial audio | ✅ WebXR spec gap + ARCore fragmentation |
| **Camera-as-perceptual-bottleneck** | ✅ Session stability & clock offset | ✅ Audio-visual coupling (AEC) | ✅ Flashlight/auto-exposure gap |
| **Reproducibility crisis** | ✅ Latency measurement crisis | ✅ ISM/HRTF data bugs | ✅ Calibration that works once |
| **Privacy vs. immersion** | ✅ Foveation requires gaze data | — | ✅ Visibility masking |
| **Standards convergence** | — | ✅ glTF KHR_audio_* extensions | ✅ WebXR spec gaps |

---

## Production Checklist

- [ ] Research phase complete for all 3 episodes
- [ ] Guest outreach initiated (see individual issue trackers)
- [ ] Demo recordings planned
- [ ] Listener story collection launched
- [ ] Episode 1 script draft
- [ ] Episode 2 script draft
- [ ] Episode 3 script draft
- [ ] Post-production workflow established
- [ ] Distribution strategy defined

---

## How to Contribute

1. **Pick an episode issue** — [#67](https://github.com/bro26man-hash/human-perception-podcast/issues/67) (E1), [#68](https://github.com/bro26man-hash/human-perception-podcast/issues/68) (E2), or [#69](https://github.com/bro26man-hash/human-perception-podcast/issues/69) (E3)
2. **Add GitHub issue links** as comments on the relevant episode issue
3. **Tag potential guests** and track outreach status in the issue tables
4. **Submit a PR** with updated outlines, new research findings, or additional hot debates

---

*Research sourced from GitHub issues across immersive-web/webxr, Unity-Technologies/arfoundation-samples, WiVRn/WiVRn, VG,刘洋openvr, polygraphene/ALVR, GoogleChrome/omnitone, leomccormack/Spatial_Audio_Framework, KhronosGroup/glTF, Microsoft/MixedReality-WebRTC, Microsoft/MixedRealityToolkit-Unity, and related AR/MR repositories. Last updated: September 2026.*