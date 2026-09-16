# 🎙️ The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.
> This is the **canonical episode outline** for the series.

---

## Series Overview

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Repos |
|---|---|
| Web 3D / WebXR | `mrdoob/three.js` (115.6k ⭐), `playcanvas/engine` (16.7k ⭐), `immersive-web/webxr` (3.1k ⭐) |
| Web AR | `jeromeetienne/AR.js` / `AR-js-org/AR.js` (15.8k ⭐), `hiukim/mind-ar-js` (2.7k ⭐), `jeeliz/jeelizFaceFilter` (2.9k ⭐) |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity` (6.1k ⭐), `MixedRealityToolkit/MixedRealityToolkit-Unity` (550 ⭐), `microsoft/MixedRealityCompanionKit` (594 ⭐) |
| Spatial Computing | `StereoKit/StereoKit` (1.1k ⭐), `KhronosGroup/OpenXR-SDK` (1.1k ⭐), `IvanCampos/visionOS-examples` (405 ⭐) |
| Spatial Audio | `GoogleChrome/omnitone` (911 ⭐), `leomccormack/Spatial_Audio_Framework` (748 ⭐), `google/spatial-media` (2.1k ⭐), `freeman-jiang/beatsync` (3.2k ⭐) |
| VR Streaming | `WiVRn/WiVRn` (1.6k ⭐), `polygraphene/ALVR` |

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

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets (reduce average ms) are wrong — we need to stabilize frame delivery instead. This reframes the entire 20 ms discussion.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leinardi** | Maintainer, SteamVR-for-Linux | Open-source VR latency debugging; first-hand motion-to-photon pipeline experience |
| **jd-3d** | Developer, ALVR | VR streaming stack forensics; discovered the "missing" 30–50% latency underreporting |
| **xytovl** | Maintainer, WiVRn | OpenXR streaming; packet-timing & pacing algorithm design; traced stutter to temporal irregularity |
| **AaronMillward** | Contributor, WiVRn | Field reports of perceptual stutter & motion sickness from real users |
| **brycehutchings** | Microsoft OpenXR (MRTK3) | HoloLens 2 Direct3D 12 path; frame-timestamp precision; viewfinder reliability |
| **emaschino** | Microsoft MRC | HoloLens 2 performance; mixed-reality compositor calibration |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform strategy; mixed-reality advocacy & developer ecosystem |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration; MixedRealityCompanionKit #228 |
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR tracking & latency on mobile |
| **maluoi** | Maintainer, StereoKit | XR engine architecture; OpenXR backend; performance optimization |

### Source Repos

- `WiVRn/WiVRn` — OpenXR streaming; stutter & temporal irregularity (#282, #234, #741, #873)
- `polygraphene/ALVR` — The "missing latency" finding (#334)
- `microsoft/MixedRealityCompanionKit` — Calibration instability & hologram drift (#228, #221)
- `jeromeetienne/AR.js` / `AR-js-org/AR.js` — Web AR tracking latency (#826, #825)
- `google-ar/arcore-unity-sdk` — Camera feed drop, Instant Preview workflow latency (#206, #277)
- `Unity-Technologies/arfoundation-samples` — AR Foundation frame drops & depth sensor latency (#1113, #615)

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How spatial-audio algorithms trick the brain into hearing sound in 3D space — and why a one-size-fits-all HRTF still isn't good enough.

### Key Topics

1. **Head-Related Transfer Functions (HRTFs) and the personalization challenge** — the brain localizes sound through subtle interaural time and level differences; current HRTF databases are built on average ear shapes, not yours.
2. **Vector Base Amplitude Panning (VBAP) and higher-order ambisonics (HOA)** — the mathematical foundations of 3D audio rendering.
3. **Real-time binaural/ambisonic rendering on the web** — GoogleChrome/omnitone's FOA/HOA renderer using the Web Audio API.
4. **The mobile spatial audio gap** — omnitone #2 (23 comments, open since 2016): a billion mobile browser users cannot experience 3D audio at all.
5. **HRTF augmentation and spatial release from masking** — cross-modal hearing research.
6. **Audio–visual integration in VR** — vision dominates when cues conflict (the ventriloquism effect).
7. **Room acoustics modeling (ISM reverberation) and perceptual quality** — fundamental bugs in room-model algorithms undermine perceptual realism.
8. **Scalability: spatial audio for 20+ people** — Hubs #5057: no engine today ships a spatial-audio renderer that works for 20+ simultaneous listeners.

### The Hot Debate

> **Spatial audio is architecturally absent from WebXR.** WebXR #390 (open since 2018, 30+ comments): the spec has no spatial-audio element. The API surface was designed for visual XR — sound is bolted on, not built in. Combined with Omnitone #2 (mobile gap, 10+ years unresolved) and Hubs #5057 (doesn't scale past 20 users), spatial audio is the XR field's most neglected dimension. The question isn't just technical — it's a specification-level decision about whether sound gets first-class status in immersive computing.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **leomccormack** | Creator, Spatial_Audio_Framework & SPARTA | Ambisonics, HRTFs, ISM room modeling, cross-platform C algorithms |
| **crlandsc** | Contributor, Spatial_Audio_Framework | Spatialization algorithms; real-time rendering |
| **ali-vosoughi** | Contributor, Spatial_Audio_Framework | Ambisonic processing & signal flow |
| **jacobhollebon** | Contributor, Spatial_Audio_Framework | Spatial audio architecture & design |
| **hoch** | Maintainer, Omnitone | Mobile browser spatial audio gap; FOA/HOA rendering |
| **Boris Smus** | Google / Omnitone | Web binaural rendering; FOA/HOA |
| **Brandon Jones** | Google / Omnitone | Web Audio API spatial rendering; ambisonic codecs |
| **Julius Kammerl** | Google / Omnitone | Real-time spatial audio in web browsers |
| **freeman-jiang** | Creator, beatsync (3.2k ⭐) | High-precision multi-device spatial audio; clock sync |
| **BinWang28** | Maintainer, audio-ai-hub | HRTF research; spatial speech perception; personalized HRTFs |
| **edurnebernal** | Researcher | Audio-visual spatial perception in VR; ventriloquism effect |
| **misslivirose** | Hubs-Foundation | Audio spatialization & accessibility in social VR |
| **ameliaeckard** | Researcher, Apple Vision Pro | Spatial audio for visual impairment; indoor navigation |
| **TheBarmaEffect** | Spatial audio engine designer | Perception-first spatial audio engine design |

### Source Repos

- `GoogleChrome/omnitone` — Web spatial audio rendering (mobile gap, #2)
- `microsoft/MixedReality-WebRTC` — MR audio/video communication stacks (ADM2 failure, #573)
- `leomccormack/Spatial_Audio_Framework` — C/C++ spatial audio algorithms (ISM bug, #58; HRTF bugs, #55)
- `leomccormack/SPARTA` — JUCE-based spatial audio plugins
- `google/spatial-media` — 360° video & spatial audio metadata
- `freeman-jiang/beatsync` — High-precision multi-device spatial audio
- `Hubs-Foundation/hubs` — Social VR spatial audio (&1853, #5057)
- `immersive-web/webxr` — Spec-level spatial audio absence (#390, #815)

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** The design of mixed-reality interfaces — optical passthrough quality, boundary systems, hologram registration, and how MR competes for our attention.

### Key Topics

1. **Hologram registration errors & drift** — MixedRealityCompanionKit #221: holograms that "stick to camera" instead of staying anchored to the physical world. 18 comments. Core presence failure.
2. **Optical passthrough quality** — resolution, contrast, and the race between visionOS, Quest 3, and XREAL.
3. **Boundary systems & wayfinding** — WebXR #992 (36 comments): users don't know where they are in immersive sessions. A fundamental spatial-awareness gap.
4. **WebXR layers & projection-layer scaling** — webxr-samples #228/#231/#235: cut-off and visual artifacts when rendering 2D layers into 3D space.
5. **Dynamic foveation & visibility masking** — WebXR #1420, #1396: rendering asymmetry (high-res center, low-res periphery) as a perceptual-performance lever.
6. **MR input fragmentation** — MRTK #914: MX Ink MR Stylus on Meta Quest. Platform convergence without interface abstraction.
7. **Documentation gaps** — MRTK #987: even Microsoft's own toolkit can't document how to turn on mixed reality capture for HoloLens 2.
8. **Vendor plugin architecture** — MRTK #511: should vendor RealityProviders live in core MRTK? High-priority, architectural.
9. **Neural interfaces & neuroadaptive MR** — OpenGalea (Team Syncer): 8-channel EEG fused with Quest 3 for brain-controlled experiences. MIT Reality Hack Meta winner.

### The Hot Debate

> **MR registration is not MR acceptance.** Even geometrically correct hologram placement is rejected by the brain if it drifts, sticks to camera, or fails to stay anchored (MRC #221). The open question: what turns geometric alignment into perceptual acceptance? Is it temporal stability, haptic feedback, audio anchoring, or something deeper in the perceptual hierarchy? This is the fundamental unsolved problem of mixed reality.

### Potential Guests

| Name | Repo / Role | What They'll Bring |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | Web AR pioneer; the AR.js 2→3 transition; geospatial AR vision |
| **hiukim** | Creator, MindAR (2.7k ⭐) | On-device image/face tracking with TensorFlow.js |
| **maluoi** | Maintainer, StereoKit (1.1k ⭐) | XR engine architecture; OpenXR backend |
| **cabanier** | W3C Immersive Web | WebXR DOM overlays; visibility & rendering layers |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation; accessibility in XR; spec language for non-visual XR |
| **chrisdavidmills** | WebXR editor | Visibility-mask events; compositing layers |
| **danrossi** | WebXR contributor | WebXR layers & projection-layer work |
| **keveleigh** | Microsoft MRTK maintainer | MRTK #511 vendor architecture; #987 documentation |
| **dongyoonpark** | Microsoft MRDL | Periodic Table on HoloLens 2; tactile MR interaction design |
| **richardinerickson** | Microsoft MRDL | Surfaces MR app; tactile sensation via audiovisual/hand tracking |
| **IvanCampos** | Creator, visionOS-examples (405 ⭐) | Apple Vision Pro spatial UI patterns; SE(3) anchor stability |
| **Team Syncer (OpenGalea)** | MIT Reality Hack Meta winner | Neuroadaptive MR — 8-channel EEG + Quest 3 for brain-controlled experiences |

### Source Repos

- `MixedRealityToolkit/MixedRealityToolkit-Unity` — MRTK v3; stylus input (#914), capture docs (#987), vendor plugins (#511)
- `microsoft/MixedRealityCompanionKit` — Hologram registration & calibration (#221, #228)
- `immersive-web/webxr` — Wayfinding (#992), DOM overlays (#1414), foveation (#1420, #1396), non-visual spec (#815)
- `immersive-web/webxr-samples` — Projection-layer scaling artifacts (#228, #231, #235)
- `StereoKit/StereoKit` — XR engine & input profiles
- `XuanJi-ISA/Isaac-Sim-Addons` — Sonic Palette: color-hearing for the blind (#62)

---

## Cross-Episode — The Hottest Open Debates

| Debate | Where It's Live | Perception Implication |
|---|---|---|
| Temporal irregularity vs. average latency | WiVRn #282, #234 | Is the brain detecting frame pacing, not raw ms? Reframes optimization targets. |
| VR streaming underreporting by 30–50% | ALVR #334 | Industry has been optimizing against a phantom number. |
| Spatial audio is architecturally absent from WebXR | webxr #390, omnitone #2 | Sound is an afterthought in immersive computing specs. |
| MR registration ≠ MR acceptance | MRC #221 | Geometric correctness ≠ perceptual acceptance. |
| WebXR spec is visually blind | webxr #815, #992 | Spec precludes non-visual uses; wayfinding broken. |
| Input fragmentation | MRTK #914 | Convergence without abstraction; platform-specific code persists. |
| Scalable spatial audio for 20+ users | Hubs #1853, #5057 | Cocktail-party problem unsolved at engine level. |
| Neuroadaptive interfaces | OpenGalea / Team Syncer | Brain-controlled MR blurs perception and control. |
