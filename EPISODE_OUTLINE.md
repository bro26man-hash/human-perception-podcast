# The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **canonical episode outline** for the series. Companion research lives in `RESEARCH-DATABASE.md` and `COMMUNITY-RESEARCH.md`.

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two speakers? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR repos and the researchers pushing them forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos |
|---|---|
| Web AR | `jeromeetienne/AR.js` (15.8k ⭐), `hiukim/mind-ar-js` (2.7k ⭐), `jeeliz/jeelizFaceFilter` (2.9k ⭐) |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity` (6.1k ⭐), `MixedRealityToolkit/MixedRealityToolkit-Unity` (550 ⭐), `microsoft/MixedReality-WebRTC` (944 ⭐), `microsoft/MixedRealityCompanionKit` (594 ⭐) |
| Spatial Computing | `microsoft/xr-development-for-beginners` (564 ⭐), `google/lullaby` (1.2k ⭐) |
| Spatial Audio | `google/spatial-media` (2.1k ⭐), `freeman-jiang/beatsync` (3.2k ⭐), `GoogleChrome/omnitone` (911 ⭐), `leomccormack/Spatial_Audio_Framework` (748 ⭐), `leomccormack/SPARTA` (777 ⭐), `ashawkey/RAD-NeRF` (925 ⭐) |
| AR Frameworks | `StereoKit/StereoKit`, `KhronosGroup/OpenXR-SDK`, `google-ar/arcore-android-sdk` |

---

## Episode 1: "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

**Key Topics**
- Motion-to-photon pipeline: sensor → predict → render → encode → transport → decode → display
- The "20 ms rule" and vestibular-visual conflict: why a few milliseconds of lag translate directly into motion sickness
- Tracking not feeling smooth: the [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) threaded discussion (97+ comments from users reporting nausea-inducing lag)
- "Missing" latency: the [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334) finding that VR streaming stacks underreport total system latency by 30–50%
- Calibration instability in MR: [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — SpectatorView calibration that works once and never twice (19 comments)
- HoloLens 2 Direct3D 12 performance and frame-timestamp precision (microsoft/OpenXR-MixedReality #131, #132)
- WebAR latency on mobile: [jeromeetienne/AR.js #826](https://github.com/jeromeetienne/AR.js/issues/826) (image tracking breaking) and [#825](https://github.com/jeromeetienne/AR.js/issues/825) (location-based AR failing) — real-time tracking is the first perceptual bottleneck on the web

**Hot Debate — Perceptual Latency**
The most active debate in the AR/MR space is about where latency measurement actually begins. ALVR's finding that streaming stacks underreport total latency by 30–50% means the industry may be optimizing against the wrong number. Combined with AR.js tracking failures on mobile, the gap between "technical latency" and "perceptual latency" is widening — and users are paying the price in motion sickness and broken presence.

**Potential Guests**
- **leinardi** — SteamVR-for-Linux maintainer; on the ground with motion-to-photon latency on open-source VR
- **jd-3d** — ALVR developer; first-hand investigation into "missing" latency in VR streaming
- **brycehutchings** — Microsoft OpenXR contributor; MR performance & the Direct3D 12 path
- **fredemmott** — Microsoft XR Advocate; HoloLens platform
- **emaschino** — active MR performance researcher
- **fieldsJacksonG** — Microsoft MRC; assignee on hologram registration & calibration
- **jeromeetienne** (Jérôme Etienne) — AR.js creator; web AR tracking & latency on mobile
- **hiukim** — mind-ar-js maintainer; TensorFlow.js-based AR tracking for the web

**Source Repos for Episode 1**
- `microsoft/MixedRealityCompanionKit` — calibration & hologram registration issues
- `ValveSoftware/SteamVR-for-Linux` — motion-to-photon latency community debate
- `polygraphene/ALVR` — underreporting latency in VR streaming
- `jeromeetienne/AR.js` — web AR tracking latency
- `hiukim/mind-ar-js` — ML-based AR tracking pipelines

---

## Episode 2: "Spatial Sound and the Third Dimension"

**Focus:** How spatial-audio algorithms trick the brain into hearing sound in 3D space — and why a one-size-fits-all HRTF still isn't good enough.

**Key Topics**
- Head-Related Transfer Functions (HRTFs) and the personalization challenge
- Vector Base Amplitude Panning (VBAP) and higher-order ambisonics (HOA)
- Real-time binaural/ambisonic rendering on the web — the [GoogleChrome/omnitone](https://github.com/GoogleChrome/omnitone) approach (FOA/HOA renderers, Web Audio API)
- HRTF augmentation effects on spatial release from masking (see community HFSP work)
- Audio–visual integration in VR: vision dominates when cues conflict
- Room acoustics modeling (ISM reverberation) and perceptual quality
- Accessibility: spatial audio as navigation for visually impaired users

**Hot Debate — Spatial Audio Rendering**
Three open issues frame the current crisis in spatial audio:
1. **[omnitone #2](https://github.com/GoogleChrome/omnitone/issues/2)** — Support for mobile browsers (23 comments, still open since 2016): the most-watched spatial audio issue on GitHub, debated across desktop and mobile rendering pipelines
2. **[MixedReality-WebRTC #573](https://github.com/microsoft/MixedReality-WebRTC/issues/573)** — ADM2 does not play any sound with multiple audio outputs: when mixing spatial audio with communication stacks, the rendering pipeline breaks
3. **[Spatial_Audio_Framework #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58)** — ISM RIR incorrect summing of bands: a fundamental bug in room acoustics modeling that undermines perceptual realism

The thread: humans localize sound through subtle interaural cues, and current HRTF databases are built on average ear shapes. Personalized HRTFs improve localization accuracy dramatically, but we lack scalable measurement tools. Mobile browsers can't yet render spatial audio at all — 23 comments deep, this issue remains unfixed.

**Potential Guests**
- **leomccormack** (Leon McCormack) — creator of Spatial_Audio_Framework & SPARTA; ambisonics, HRTFs & temporal rendering
- **crlandsc**, **ali-vosoughi**, **jacobhollebon** — Spatial_Audio_Framework contributors (spatialization algorithms)
- **BinWang28** — audio-ai-hub; HRTF research & spatial speech perception
- **edurnebernal** — audio-visual spatial perception in VR
- **TheBarmaEffect** — perception-first spatial audio engine design
- **Boris Smus / Brandon Jones / Julius Kammerl** — omnitone / Google spatial audio team
- **Tim Fain** — Jaunt VR; spatial content & rendering
- **freeman-jiang** (Freeman Jiang) — beatsync creator; high-precision multi-device spatial audio (3.2k ⭐)
- **ashawkey** — RAD-NeRF; audio-spatial decomposition for talking portraits
- **hoch** — omnitone maintainer (assignee on the mobile browser issue)

**Source Repos for Episode 2**
- `GoogleChrome/omnitone` — web spatial audio rendering (mobile gap)
- `microsoft/MixedReality-WebRTC` — MR audio/video communication stacks
- `leomccormack/Spatial_Audio_Framework` — C/C++ spatial audio algorithms
- `leomccormack/SPARTA` — JUCE-based spatial audio plugins
- `google/spatial-media` — 360° video & spatial audio metadata
- `freeman-jiang/beatsync` — web-based spatial audio player
- `ashawkey/RAD-NeRF` — Neural radiance + spatial audio decomposition

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**Focus:** The design of mixed-reality interfaces — optical passthrough quality, boundary systems, hologram registration, and how MR competes for our attention.

**Key Topics**
- Hologram registration errors: [microsoft/MixedRealityCompanionKit #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — "holograms sticking to camera," reprojection drift across network stacks (18 comments)
- Optical passthrough quality and the resolution/contrast race (visionOS, Quest 3, XREAL)
- Plane detection & spatial mapping limitations in dynamic environments (visionOS-examples)
- WebXR layers & projection-layer scaling — cut-off and visual artifacts ([webxr-samples #228, #231, #235](https://github.com/immersive-web/webxr-samples)), and DOM overlays in canvas ([webxr #1414](https://github.com/immersive-web/webxr/issues/1414))
- Dynamic foveation and visibility masking as perceptual-performance levers ([webxr #1420](https://github.com/immersive-web/webxr/issues/1420), [webxr #1396](https://github.com/immersive-web/webxr/issues/1396))
- MR stylus input: [MRTK-Unity #914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) — MX Ink MR Stylus for Meta Quest feature request (platform convergence debate)
- MR capture & documentation: [MRTK-Unity #987](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/987) — missing docs on HoloLens 2 mixed reality capture (4 comments, triage needed)
- Vendor plugin architecture: [MRTK-Unity #511](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/511) — should vendor-specific plugins be in the core MRTK repo? (High priority, 2 comments)

**Hot Debate — Mixed Reality Interfaces**
The MRTK issue tracker is a microcosm of the MR interface crisis:
- **Registration drift** (#221): Holograms that "stick to camera" instead of staying anchored to the physical world break the fundamental promise of mixed reality. 18 people have weighed in — this is a core presence problem.
- **Input fragmentation** (#914): A Meta Quest user requesting Microsoft's MX Ink stylus support reveals that the ecosystem is converging, but toolkits haven't caught up. Platform boundaries are dissolving; interface abstraction layers haven't.
- **Documentation gaps** (#987): Even Microsoft's own MRTK can't document how to turn on mixed reality capture for HoloLens 2 — meaning researchers can't reliably reproduce MR experiments.
- **Architecture tension** (#511): Should vendor-specific RealityProviders live inside the MRTK core? High-priority question with 2 active commenters.

**Potential Guests**
- **maluoi** — StereoKit maintainer; XR engine & OpenXR backend
- **cabanier** — W3C Immersive Web; WebXR DOM overlays & visibility
- **AdaRoseCannon** — W3C Immersive Web; dynamic foveation & accessibility
- **himorin** — WebXR contributor; security/privacy of spatial mapping
- **chrisdavidmills** — WebXR visibility-mask events
- **danrossi** — WebXR layers & projection-layer work
- **aphillia** — input profiles & i18n for XR
- **keveleigh** — Microsoft MRTK lead (assignee on #511, #987)
- **Ali-Can-Keskin** — MX Ink MR Stylus requester (#914)
- **RPRX** — HoloLens developer with significant MR interaction expertise

**Source Repos for Episode 3**
- `MixedRealityToolkit/MixedRealityToolkit-Unity` — MRTK v3, stylus input, capture, vendor plugins
- `microsoft/MixedRealityCompanionKit` — hologram registration & calibration
- `immersive-web/webxr` — layers, foveation, visibility, DOM overlays
- `immersive-web/webxr-samples` — projection-layer scaling artifacts
- `StereoKit/StereoKit` — XR engine & input profiles
- `microsoft/xr-development-for-beginners` — spatial computing education

---

## Community Research Contributors

These GitHub users are actively shaping the AR/MR/spatial-audio ecosystems and make ideal podcast guests:

| Contributor | Primary Repos | Expertise |
|---|---|---|
| **jeromeetienne** | AR.js (15.8k ⭐) | Web AR tracking, markerless AR |
| **leomccormack** | Spatial_Audio_Framework, SPARTA | Spatial audio algorithms, HRTFs, ambisonics |
| **freeman-jiang** | beatsync (3.2k ⭐) | High-precision spatial audio playback |
| **hoch** | omnitone | Web spatial audio rendering (Google Chrome) |
| **ashawkey** | RAD-NeRF | Neural radiance fields + spatial audio |
| **keveleigh** | MRTK-Unity | Mixed reality toolkit, HoloLens |
| **cabanier** | webxr | WebXR DOM overlays, visibility |
| **AdaRoseCannon** | webxr | Dynamic foveation, accessibility |
| **brycehutchings** | OpenXR-MixedReality | MR performance, Direct3D 12 |
| **fredemmott** | Microsoft XR | HoloLens platform advocacy |
| **leinardi** | SteamVR-for-Linux | Motion-to-photon latency, open VR |
| **jd-3d** | ALVR | VR streaming latency analysis |
| **maluoi** | StereoKit | XR engine, OpenXR backend |

---

## Behind the Episodes: The Hot Debates (from open issues)

| Debate | Where it's live | Why it matters for perception |
|---|---|---|
| Vestibular-visual conflict & motion sickness | SteamVR-for-Linux #21, ALVR #334 | Defines the acceptable latency ceiling |
| "Missing" system latency in VR streaming | ALVR #334 | Misleads optimization efforts by 30–50% |
| Web AR tracking failure on mobile | AR.js #826, #825 | Breaks the promise of accessible AR |
| HRTF personalization vs. generic | Spatial_Audio_Framework, audio-ai-hub | Determines whether virtual sound feels "real" |
| Mobile spatial audio gap | omnitone #2 (23 comments!) | Billion mobile users can't experience 3D audio |
| ADM2 audio output failures | MixedReality-WebRTC #573 | Spatial audio breaks when communication stacks mix |
| ISM room model bug | Spatial_Audio_Framework #58 | Invalidates perceptual room-acoustics research |
| Hologram drift / "stick to camera" | MixedRealityCompanionKit #221 | Core MR presence problem |
| MR input fragmentation | MRTK-Unity #914 | Platform convergence without abstraction |
| MR capture documentation gap | MRTK-Unity #987 | Blocks research reproducibility |
| MRTK vendor plugin architecture | MRTK-Unity #511 | High-priority architectural decision |
| WebXR layers & passthrough artifacts | webxr-samples #228/#231/#235 | Visual comfort vs. fidelity trade-off |
| Visibility masking & foveation | webxr #1420, #1396 | Perceptual dilution of performance cost |
