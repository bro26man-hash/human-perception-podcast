# 🎙️ The Future of Human Perception — Initial Episode Outline

> **A podcast series exploring the engineering and human science behind how technology reshapes perception.**
> Every episode is grounded in real open debates from the most active GitHub repositories in AR, spatial computing, and perceptual science.

---

## 📋 Series Overview

| Detail | Info |
|---|---|
| **Format** | Conversational — 2 hosts + 1 guest per episode |
| **Length** | 45–60 minutes |
| **Pre-production** | 2 weeks of GitHub issue research + guest outreach |
| **GitHub Hub** | This repository — issues for community input, PRs for revisions |
| **Research Methodology** | Mine hottest open issues → extract debate topics → identify active contributors → invite as guests |

---

## 🎧 Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency and the 20ms rule  
**Core Question:** Can foveation and reprojection trick the brain into forgiving lag — or is the 20ms threshold a hard physical limit?

### Key Topics

1. **Motion-to-Photon (MTP) Latency:** What it is, why 20ms is the magic number, and why the brain's vestibular system makes it non-negotiable
2. **Foveated Rendering as a Latency Cheat:** Trading peripheral detail for speed — is it a crutch or the future?
3. **Async Reprojection vs. Direct Rendering:** The SteamVR-for-Linux debate ([#21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) — 97+ comments, "Tracking not smooth and a little delayed")
4. **Temporal Irregularity > Average Latency:** WiVRn #[282](https://github.com/WiVRn/WiVRn/issues/282) — maintainer @xytovl traced stutter to >10ms reception-time variability, not raw pipeline latency. The brain may detect *pacing irregularity*, not just delay.
5. **The "Missing Latency" Crisis:** ALVR #[334](https://github.com/polygraphene/ALVR/issues/334) — VR streaming stacks underreport total system latency by 30–50%. The industry has been optimizing against a phantom number.
6. **Camera↔IMU Clock Offset:** ARCore #[1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) — 13–35ms hardware clock skew on mid-range Android. Invisible to developers, catastrophic for perceptual stability.
7. **The Vestibular-Ocular Reflex:** Why latency makes you nauseous, not just annoyed

### 🔥 GitHub Debate Table

| Position | Argument | Source |
|---|---|---|
| **Foveation is enough** | Rendering only 2° of high-res detail saves 60-70% GPU time, easily hitting 20ms for most users | WiVRn #1420, WebXR foveation proposal |
| **Foveation is a crutch** | It masks the problem for static gaze but fails during fast head movements — the exact moments that matter | WiVRn #282 (stutter during motion)
| **17ms is the real limit** | Vestibular-visual conflict becomes unbearable below 17ms; 20ms is polite, not physiological | ALVR #334 (33.6ms unaccounted)
| **Reprojection IS the future** | AI-driven frame generation (DLSS-style) will make 20ms irrelevant within 3 years | SteamVR-for-Linux #21 community |
| **Temporal stability > average latency** | The brain detects frame-to-frame jitter, not just mean pipeline depth | WiVRn #282 (xytovl's findings) |

### 🎤 Potential Guests

| Name | GitHub | Expertise | Episode Angle |
|---|---|---|---|
| **xytovl** | [@xytovl](https://github.com/xytovl) | WiVRn maintainer; OpenXR streaming; packet-timing algorithms | The frame-stuttering discovery that changes the latency debate |
| **jeromeetienne** | [@jeromeetienne](https://github.com/jeromeetienne) | AR.js creator (15.8k ⭐); Web AR pioneer | Tracking pipeline latency stories from the Web AR wars |
| **leinardi** | [@leinardi](https://github.com/leinardi) | SteamVR-for-Linux community | 97-comment saga of "tracking not smooth" — the user perspective |
| **jd-3d** | [@jd-3d](https://github.com/jd-3d) | ALVR developer | VR streaming latency forensics — discovering the "missing 33ms" |
| **reduz (Juan Linietsky)** | [@reduz](https://github.com/reduz) | Godot Engine co-creator | How 3D engines handle frame timing; perceptual impact of rendering latency |
| **jaygullapalli** | [@jaygullapalli](https://github.com/jaygullapalli) | Azure Kinect SDK lead | Sensor latency engineering — 0.2s vs 0.006s camera latency gap |
| **maluoi** | [@maluoi](https://github.com/maluoi) | StereoKit maintainer | XR engine architecture; OpenXR backend performance optimization |

### 📎 Essential GitHub Issues to Review Before Recording

- [WiVRn/WiVRn #282](https://github.com/WiVRn/WiVRn/issues/282) — Stuttering headset/controller position (40 comments)
- [WiVRn/WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) — Quest 3 passthrough freeze (40+ comments, 15+ reactions)
- [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) — Tracking not smooth (97+ comments)
- [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334) — Latency measurements missing info
- [google-ar/arcore-android-sdk #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) — Camera↔IMU clock offset
- [microsoft/Azure-Kinect-Sensor-SDK #816](https://github.com/microsoft/Azure-Kinect-Sensor-SDK/issues/816) — 0.2s vs 0.006s latency comparison (47 comments)

---

## 🎧 Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics, and the audio presence paradox  
**Core Question:** Why is the WebXR spec still visual-only for spatial audio — and can a flexible HRTF Resource type finally fix it?

### Key Topics

1. **The WebXR Audio Gap:** The spec has no spatial-audio element. Sound is bolted on, not built in. ([#390](https://github.com/immersive-web/webxr/issues/390) — open since 2018, 30+ comments)
2. **The Mobile Dead Zone:** Omnitone #[2](https://github.com/GoogleChrome/omnitone/issues/2) — binaural rendering doesn't work on mobile browsers. 10+ years unresolved. Billion users excluded.
3. **HRTF Personalization:** Your HRTF is as unique as your fingerprint. Shipping a default dataset means nobody gets accurate spatial audio.
4. **The Audio Presence Paradox:** Visual AR overlays are accepted as "real." Spatial audio that doesn't match visual origin feels "fake." Cross-modal binding failure.
5. **Scalability Crisis:** Hubs #[1853](https://github.com/Hubs-Foundation/hubs/issues/1853) and #[5057](https://github.com/Hubs-Foundation/hubs/issues/5057) — spatial audio degrades with >20 users. The cocktail party problem is unsolved at the engine level.
6. **Fundamental DSP Bugs:** Spatial_Audio_Framework #[58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) — Image Source Method RIR summing is incorrect, invalidating perceptual room-acoustics research.
7. **Cross-Modal Perception:** Auditory processing is faster than visual. The brain uses sound as a pre-attentive spatial anchor — when audio fails, the whole MR illusion collapses.

### 🔥 GitHub Debate Table

| Position | Argument | Source |
|---|---|---|
| **HRTFs belong in user assets** | Head shapes vary too much; one dataset fits nobody. Let users download their own sprigs. | Godot #4377 (SpatialAudioModel proposal) |
| **Ship a default HRTF** | Users won't download anything. Without a default, SpatialAudioModel is just an empty shell. | Godot #4377 counter-argument |
| **Ambisonics is the universal format** | 1st-order is enough for presence; higher orders are overkill. Decode once, render everywhere. | WebAudio #2386 debate |
| **WebAudio is the missing piece** | WebXR is visual-only. The W3C needs a PannerNode that accepts ambisonic inputs directly. | WebAudio #2386, webxr #390 |
| **HRTF = personal identity** | Your HRTF is unique. "Perceptual latency" in audio is about mismatch, not delay. | SAF #55, #58 research findings |
| **Spatial audio must scale to 20+ users** | Current engines collapse under social XR load. The cocktail party problem is unsolved. | Hubs #1853, #5057 |

### 🎤 Potential Guests

| Name | GitHub | Expertise | Episode Angle |
|---|---|---|---|
| **cwilso** | [@cwilso](https://github.com/cwilso) | W3C Immersive Web; authored sound source node proposal (#390) | Why the spec has no spatial audio — and what it would take to add it |
| **leomccormack** | [@leomccormack](https://github.com/leomccormack) | Creator, Spatial_Audio_Framework (748 ⭐) | Ambisonics, HRTF datasets, ISM room modeling bug — and the reproducibility crisis |
| **orsipper** / **orighst** (Boris Smus) | [@orighst](https://github.com/orighst) | Omnitone maintainer; Google Chrome audio team | Mobile spatial audio gap — 10 years of frustration |
| **pmlt** | [@pmlt](https://github.com/pmlt) | WebAudio Multi-channel PannerNode proposal | Ambisonic binauralization needs a new Node type — spec-level change |
| **alex-schroedsen** | [@alex-schroedsen](https://github.com/alex-schroedsen) | FAudio spatial audio; XAudio2 legacy | Ambisonic signal path: JACK → IEM ALLRAD → ASIO; does FAudio handle 5.1.2? |
| **rudybear** | [@rudybear](https://github.com/rudybear) | glTF KHR_audio extension architecture | Layered audio: emitter + graph + environment; TypeScript reference impl |
| **alankila** | [@alankila](https://github.com/alankila) | EasyEffects; Localization Cue Correction DSP | Crossfeed reduction — expanding stereo image from forward angles to 180° arc |
| **ThreeDeeJay** | [@ThreeDeeJay](https://github.com/ThreeDeeJay) | OpenAL Soft; HRTF proximity simulation | Near-field control; NFC degrades HRTF; multi-field SOFA improves it |
| **misslivirose** | [@misslivirose](https://github.com/misslivirose) | Hubs-Foundation; audio spatialization & accessibility | The social XR audio problem from the inside |
| **ameliaeckard** | [@ameliaeckard](https://github.com/ameliaeckard) | Apple Vision Pro; spatial audio for visual impairment | Using spatial audio as a sensory substitute for navigation |

### 📎 Essential GitHub Issues to Review Before Recording

- [immersive-web/webxr #390](https://github.com/immersive-web/webxr/issues/390) — Hook up CSS/HTML spatial audio (open since 2018)
- [GoogleChrome/omnitone #2](https://github.com/GoogleChrome/omnitone/issues/2) — Mobile browser support (10+ years, 23 comments)
- [Hubs-Foundation/hubs #1853](https://github.com/Hubs-Foundation/hubs/issues/1853) — Spatial audio quality (30 comments)
- [Hubs-Foundation/hubs #5057](https://github.com/Hubs-Foundation/hubs/issues/5057) — Audio at scale (24 comments)
- [leomccormack/Spatial_Audio_Framework #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) — ISM RIR incorrect summing
- [WebAudio/web-audio-api #2386](https://github.com/WebAudio/web-audio-api/issues/2386) — Multi-channel PannerNode
- [godotengine/godot-proposals #4377](https://github.com/godotengine/godot-proposals/issues/4377) — SpatialAudioModel Resource type
- [microsoft/MixedReality-WebRTC #573](https://github.com/microsoft/MixedReality-WebRTC/issues/573) — ADM2 doesn't play sound with multiple outputs

---

## 🎧 Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift, and wayfinding  
**Core Question:** Is the WebXR spec blind to non-visual perception — and what does that mean for mixed reality interfaces that feel like home?

### Key Topics

1. **The WebXR Visual Primacy Gap:** The spec defines `XRReferenceSpace` and `XRPose` but nothing for auditory or haptic reference frames. ([#815](https://github.com/immersive-web/webxr/issues/815) — 41 comments; spec language precludes non-visual uses)
2. **MR Registration ≠ MR Acceptance:** Holograms that are geometrically correct but drift, stick to camera, or fail to anchor are rejected by the brain. ([MRC #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — 18 comments; [MRC #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — 19 comments)
3. **Wayfinding Crisis:** Users in immersive XR can't find content that wasn't visible when they entered. ([webxr #992](https://github.com/immersive-web/webxr/issues/992) — 36 comments)
4. **Hand Tracking vs. Controllers:** The "pinch gap" — hand tracking flickers, jitters, and fails in bright light. Controllers are deterministic but battery-dependent. Is the Rubber Hand Illusion strong enough to make the brain "own" any input?
5. **The 2D-Orbit Problem:** Rotating a 3D object with a 2D input device is like using a TV remote to sculpt clay.
6. **Dynamic Foveation as Interface Design:** Reducing peripheral resolution to cheat the brain — more performance, same presence. ([webxr #1420](https://github.com/immersive-web/webxr/issues/1420) — @AdaRoseCannon)
7. **Input Fragmentation:** Platforms are converging (HoloLens, Quest 3, Vision Pro, XREAL) but software abstraction hasn't. ([MRTK #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) — MX Ink stylus on Meta Quest)
8. **AR.js ECS Architecture Decision:** Monolithic engines can optimize end-to-end latency (sensor-to-display in one pass). ECS introduces message-passing overhead that may push latency above perceptual thresholds. ([AR.js #681](https://github.com/AR-js-org/AR.js/issues/681))

### 🔥 GitHub Debate Table

| Position | Argument | Source |
|---|---|---|
| **Hand tracking is the future** | No controllers to lose, no batteries, no precision trade-offs. Just hands. | MRTK interaction trends |
| **Controllers are safer** | Hand tracking flickers, jitters, and fails in bright light. Determinism matters. | MRTK #914 (MX Ink request) |
| **The 2D-orbit problem is unsolved** | Rotating 3D objects with 2D input is like sculpting with a TV remote. | General MR design consensus |
| **WebXR is visual-centric by design** | The spec defines visual reference frames but nothing for haptic or auditory. | webxr #815 (41 comments) |
| **Spatial anchors need drift correction** | GPS-level accuracy (1m) is not enough for MR. Centimeter-level persistence is unsolved. | MRC #221, #228 |
| **The Rubber Hand Illusion applies to MR** | If visuo-motor correlation is strong enough, the brain will "own" any input — even a laser pointer. | Cognitive science + MR evidence |
| **ECS is the right architecture for Web AR** | Modularity, plugin systems, and maintainability outweigh latency overhead. | AR.js #681 (kalwalt) |
| **ECS introduces perceptible latency** | Message-passing overhead may push latency above perceptual thresholds. Monolithic engines win on latency. | AR.js #681 counter-argument |
| **Wayfinding is a first-class MR problem** | Spatial memory and navigation are core human abilities; XR that breaks them violates perceptual expectations. | webxr #992 (36 comments) |

### 🎤 Potential Guests

| Name | GitHub | Expertise | Episode Angle |
|---|---|---|---|
| **jeromeetienne** | [@jeromeetienne](https://github.com/jeromeetienne) | AR.js creator; Web AR pioneer | AR.js 2→3 transition; markerless tracking reliability; the ECS decision |
| **kalwalt** | [@kalwalt](https://github.com/kalwalt) | AR.js org lead; AR.js-next ECS architect | Why the monolithic→ECS shift is a *perceptual* design decision, not just code refactoring |
| **donrmccurdy** | [@donrmccurdy](https://github.com/donrmccurdy) | A-Frame co-maintainer; hand tracking & controller systems | MR input models; hand-controls misalignment bugs (#5305) |
| **kevin-ngo** | [@andgokevin](https://github.com/andgokevin) | A-Frame co-maintainer; VR UI design | "Building UIs in VR" — why MR interface design docs are still incomplete |
| **reduz (Juan Linietsky)** | [@reduz](https://github.com/reduz) | Godot Engine co-creator | Why 3D interfaces are harder than 3D rendering; the 2D-first design trap |
| **punto- (Ariel Manzur)** | [@punto-](https://github.com/punto-) | Godot Engine co-creator | How 2D-first philosophy shapes (and limits) 3D interface paradigms |
| **AdaRoseCannon** | [@AdaRoseCannon](https://github.com/AdaRoseCannon) | W3C Immersive Web; dynamic foveation; accessibility | Can the renderer cheat the brain by reducing peripheral resolution? |
| **cwilso** | [@cwilso](https://github.com/cwilso) | W3C Immersive Web; sound source nodes | The spec's visual bias — from audio to input profiles |
| **toji** | [@toji](https://github.com/toji) | WebXR spec editor | Overall spec direction; why non-visual uses are afterthoughts |
| **cabanier** | [@cabanier](https://github.com/cabanier) | W3C Immersive Web | DOM overlays & visibility specification for MR interfaces |
| **fieldsJacksonG** | [@fieldsJacksonG](https://github.com/fieldsJacksonG) | Microsoft MRC; hologram registration | Calibration that works once and never twice — the MR reproducibility blocker |
| **bradleylab** | [@bradleylab](https://github.com/bradleylab) | XR Geoxplorer; hand tracking + XRI 3.x | MR interaction design; hand tracking reliability |

### 📎 Essential GitHub Issues to Review Before Recording

- [immersive-web/webxr #815](https://github.com/immersive-web/webxr/issues/815) — Spec language precludes non-visual uses (41 comments)
- [immersive-web/webxr #992](https://github.com/immersive-web/webxr/issues/992) — Content search around in immersive sessions (36 comments)
- [immersive-web/webxr #1420](https://github.com/immersive-web/webxr/issues/1420) — Dynamic foveation & visibility masking
- [microsoft/MixedRealityCompanionKit #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — Holograms sticking to camera (18 comments)
- [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — SpectatorView calibration instability (19 comments)
- [MixedRealityToolkit/MixedRealityToolkit-Unity #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) — MX Ink MR stylus for Meta Quest
- [MixedRealityToolkit/MixedRealityToolkit-Unity #511](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/511) — Vendor plugin architecture
- [AR-js-org/AR.js #681](https://github.com/AR-js-org/AR.js/issues/681) — AR.js-next ECS architecture
- [aframevr/aframe #5305](https://github.com/aframevr/aframe/issues/5305) — Hand-controls misaligned (20 comments)
- [aframevr/aframe #2281](https://github.com/aframevr/aframe/issues/2281) — UI in VR docs incomplete (23 comments)

---

## 🔥 Cross-Cutting Themes (All Episodes)

| Pattern | Evidence | Episode |
|---|---|---|
| **Perceptual ≠ Measured** | ALVR #334 (33ms missing), WiVRn #1099 (47-min freeze), ARCore #1779 (13-35ms clock skew) | Ep. 1 |
| **Spatial Audio Has No Standard** | webxr #390 (8 yrs), omnitone #2 (10 yrs, 23 comments) | Ep. 2 |
| **MR Registration Fragility** | MRC #228, MRC #221 — calibration that works once, never twice | Ep. 3 |
| **Spec Accessibility Gap** | webxr #815 (41 comments) — the spec assumes eyes-only | Ep. 2 & 3 |
| **Performance Breaks Presence** | Hubs #1853/#5057 (audio collapses under load), D3D12 #131 | Ep. 1 & 2 |
| **Platform Convergence ≠ Abstraction** | MRTK #914 (MX Ink on Quest), MRTK #511 (vendor architecture) | Ep. 3 |
| **Cross-Modal Perception** | Auditory faster than visual; SONIMO HRTF research; rubber hand illusion in MR | Ep. 2 & 3 |
| **Research Reproducibility Crisis** | SpectatorView calibration, ISM summing bug, HRTF dataset loading | Ep. 1 & 2 |
| **Temporal Irregularity > Average Latency** | WiVRn #282 — the brain detects jitter, not just delay | Ep. 1 |

---

## 📺 Production Pipeline

### Per Episode Workflow

1. **Week 1 — Deep Research**
   - Review all linked GitHub issues (minimum 30 comments each)
   - Read guest GitHub contributions (PRs, issues, discussions)
   - Draft debate table with sourced arguments
   - Post research notes as issue comments on the episode GitHub issue

2. **Week 2 — Guest Outreach & Rehearsal**
   - Send personalized interview requests referencing their specific GitHub work
   - Schedule 30-min tech check / dry run
   - Finalize debate positions and talking points

3. **Recording Day**
   - 45–60 min conversational recording
   - Screenshare key GitHub issues during recording (for video version)
   - Capture B-roll of issue threads for social media

4. **Post-Production**
   - Publish episode transcript as GitHub issue comment
   - Update this outline with episode-specific insights
   - Open follow-up issue for community Q&A

### Community Engagement

- Each episode has a companion GitHub issue for listener questions
- Listeners can submit PRs with additional research, issue links, or guest suggestions
- Quarterly "Git Hack" episodes: live-review the hottest new issues in AR/MR repos

---

## 🔗 Key Repositories Referenced

| Repository | Stars | Role in Podcast |
|---|---|---|
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 15.8k ⭐ | Web AR tracking pipelines; ECS architecture debate |
| [playcanvas/engine](https://github.com/playcanvas/engine) | 16.7k ⭐ | WebXR runtime; WebGL/WebGPU rendering |
| [mrdoob/three.js](https://github.com/mrdoob/three.js) | 115k ⭐ | Foundational 3D library for Web AR/VR |
| [immersive-web/webxr](https://github.com/immersive-web/webxr) | 3.1k ⭐ | The WebXR spec — visual primacy gap, foveation, wayfinding |
| [WiVRn/WiVRn](https://github.com/WiVRn/WiVRn) | 1.6k ⭐ | OpenXR streaming; latency & frame pacing forensics |
| [Hubs-Foundation/hubs](https://github.com/Hubs-Foundation/hubs) | 2.2k ⭐ | Social VR; spatial audio scalability crisis |
| [microsoft/MixedRealityCompanionKit](https://github.com/microsoft/MixedRealityCompanionKit) | 594 ⭐ | MR calibration & hologram registration |
| [MixedRealityToolkit/MixedRealityToolkit-Unity](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity) | 550 ⭐ | MR interaction design; input abstraction architecture |
| [google-lullaby](https://github.com/google/lullaby) | 1.2k ⭐ | Google's internal VR/AR engine; spatial audio dead end |
| [GoogleChrome/omnitone](https://github.com/GoogleChrome/omnitone) | 911 ⭐ | Web spatial audio; mobile gap (10+ years unresolved) |
| [leomccormack/Spatial_Audio_Framework](https://github.com/leomccormack/Spatial_Audio_Framework) | 748 ⭐ | Ambisonics & HRTF research; ISM bug |
| [polygraphene/ALVR](https://github.com/polygraphene/ALVR) | — | VR streaming; "missing latency" discovery |
| [StereoKit/StereoKit](https://github.com/StereoKit/StereoKit) | 1.1k ⭐ | XR engine; OpenXR backend performance |
| [IvanCampos/visionOS-examples](https://github.com/IvanCampos/visionOS-examples) | 405 ⭐ | Apple Vision Pro; passthrough quality & anchor drift |
| [google-ar/arcore-android-sdk](https://github.com/google-ar/arcore-android-sdk) | — | Mobile AR; camera↔IMU clock synchronization |
| [Microsoft/Azure-Kinect-Sensor-SDK](https://github.com/microsoft/Azure-Kinect-Sensor-SDK) | — | Sensor latency; 0.2s vs 0.006 comparison |

---

## ✅ Status

| Phase | Status | Notes |
|---|---|---|
| Repo Survey | ✅ Complete | 15+ repositories audited |
| Issue Mining | ✅ Complete | 40+ issues analyzed across 3 topics |
| Guest Identification | ✅ Complete | 25+ contributors tier-ranked |
| Episode 1 Outline | ✅ This File | Latency & the Perceptual Threshold |
| Episode 2 Outline | ✅ This File | Spatial Sound & the Third Dimension |
| Episode 3 Outline | ✅ This File | Interfaces Beyond the Flat Screen |
| Issue #1 (Ep 1) | 🔜 Create | Seeded with topics + guests |
| Issue #2 (Ep 2) | 🔜 Create | Seeded with topics + guests |
| Issue #3 (Ep 3) | 🔜 Create | Seeded with topics + guests |
| Guest Outreach | 🔜 Pending | Personalized requests referencing GitHub work |
| Pilot Recording | 🔜 Pending | Target: next 30 days |

---

*Research compiled September 2026 from GitHub issue analysis across 15+ active AR/MR/Spatial Computing repositories. This is a living document — submit PRs to update as new issues emerge and new contributors join the space.*
