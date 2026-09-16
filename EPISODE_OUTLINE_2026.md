# 🎙️ The Future of Human Perception — Episode Outlines (2026-09-16)

> Canonical episode outlines with topics, debates, guest candidates, and GitHub issue references.
> Last updated: September 16, 2026

---

## Episode 1: "Latency and the Perceptual Threshold"

**GitHub Issue:** [#13](https://github.com/bro26man-hash/human-perception-podcast/issues/13)  
**Target Release:** Q4 2026  
**Focus:** Why AR/VR still feels "not quite real," and how close we are to closing the perceptual gap.

### Core Question
*Why does AR/VR still feel "not quite real," and how close are we to closing the perceptual gap?*

### Topics
1. **Motion-to-Photon Latency** — The 20ms threshold and why every millisecond matters for presence
2. **Frame Timing & Judder** — The perceptual consequences of dropped frames; the new debate: temporal irregularity vs. average latency
3. **Dynamic Foveation** — Eye-tracked rendering; rendering only where you look to save 50–70% GPU cost
4. **VR Streaming Underreporting** — ALVR discovered ~33.6ms of unaccounted latency; stacks underreport by 30–50%
5. **Camera Feed Lag in AR** — AR Foundation issues (#1113, #1206, #1220); TrueDepth depth map latency (#615)
6. **Foveated Rendering Hardware** — Meta Quest Pro, Apple Vision Pro, XR2 Gen 2 implementations

### 🔥 Hottest Debate
> **Is the brain detecting average pipeline latency, or temporal frame irregularity?**
> WiVRn #282: maintainer `xytovl` traced headset stutter to >10ms of reception-time variability. If the brain detects irregularity, not raw latency, the entire XR industry is optimizing the wrong metric.

### 🔥 Key Issues Surfaced
| Issue | Repo | Why It Matters |
|-------|------|----------------|
| #282 | WiVRn/WiVRn | Stutter traced to temporal irregularity, not pipeline latency (40 comments) |
| #334 | polygraphene/ALVR | VR streaming underreports latency by 30–50% |
| #277 | google-ar/arcore-unity-sdk | Camera feed drop breaks perceptual continuity (25 comments) |
| #228 | microsoft/MixedRealityCompanionKit | "Works once, never twice" calibration fragility (19 comments) |
| #221 | microsoft/MixedRealityCompanionKit | Holograms stick to camera — presence failure (18 comments) |
| #1113 | Unity-Technologies/arfoundation-samples | AsyncOperation iOS slowdown violates 20ms threshold (16 comments) |

### 🎤 Suggested Guests
| Name | GitHub | Expertise |
|------|--------|-----------|
| **xytovl** | @xytovl | WiVRn maintainer; temporal irregularity discovery |
| **AaronMillward** | @AaronMillward | Field reports of perceptual stutter & motion sickness |
| **jd-3d** | @jd-3d | ALVR forensics; 33.6ms latency finding |
| **leinardi** | @leinardi | SteamVR-for-Linux; motion-to-photon pipeline |
| **fieldsJacksonG** | @fieldsJacksonG | MRC hologram registration; MRTK |

---

## Episode 2: "Spatial Sound and the Third Dimension"

**GitHub Issue:** [#14](https://github.com/bro26man-hash/human-perception-podcast/issues/14)  
**Target Release:** Q1 2027  
**Focus:** HRTFs, ambisonics, and why spatial audio is the most architecturally neglected dimension of XR.

### Core Question
*If vision is half the battle, hearing is the whole war — how does spatial audio create (or break) presence?*

### Topics
1. **The WebXR Audio Gap** — The spec has zero spatial-audio element (issue #390, open since 2018; #815, 41 comments)
2. **The Mobile Browser Gap** — Omnitone #2: 10 years unresolved; a billion users can't experience 3D audio
3. **Scalability** — Hubs #5057 & #1853: spatial audio doesn't scale past 20 simultaneous listeners
4. **Ambisonics & ISM Room Modeling** — Even foundational libraries have bugs (#58 band summing; #55 dataset loading)
5. **HRTF Personalization** — Generic HRTFs work for ~50% of listeners; can ML (DeepHRTF, NTF-HRTF) democratize this?
6. **Audio as Accessibility** — Sonic Palette (#62): using sound to substitute for vision in navigation

### 🔥 Hottest Debate
> **The browser can render 8K VR visuals at 90fps, but it can't deliver binaural 3D audio to your phone. Why has the richest sensory channel in VR/AR been the last one onboard?**

### 🔥 Key Issues Surfaced
| Issue | Repo | Why It Matters |
|-------|------|----------------|
| #390 | immersive-web/webxr | No spatial audio API in WebXR spec (30+ comments, open since 2018) |
| #2 | GoogleChrome/omnitone | Mobile browser 3D audio gap (10 years unresolved) |
| #5057 | Hubs-Foundation/hubs | Spatial audio doesn't scale past 20 users (24 comments) |
| #1853 | Hubs-Foundation/hubs | Top UX complaint: spatial audio quality (30 comments) |
| #58 | leomccormack/Spatial_Audio_Framework | ISM room modeling bug |
| #55 | leomccormack/Spatial_Audio_Framework | HRTF dataset loading broken |
| #62 | XuanJi-ISA | Sonic Palette — color-hearing for the blind |

### 🎤 Suggested Guests
| Name | GitHub | Expertise |
|------|--------|-----------|
| **leomccormack** | @leomccormack | Spatial_Audio_Framework creator; ambisonics, HRTFs, SPARTA |
| **hoch** | @hoch | Omnitone maintainer; 10-year mobile gap |
| **BinWang28** | @BinWang28 | HRTF research & personalized spatial audio |
| **edurnebernal** | @edurnebernal | Audio-visual spatial perception in VR |
| **ameliaeckard** | @ameliaeckard | Spatial audio for visual impairment |
| **Boris Smus / Brandon Jones / Julius Kammerl** | @orighst / @brandonpjones / @jkarmer | Google / Omnitone; web binaural rendering |
| **fabiangiovagnoli** | @fabiangiovagnoli | beatsync (3.2k ⭐); multi-device spatial audio |
| **misslivirose** | @misslivirose | Hubs-Foundation; audio spatialization & accessibility |

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**GitHub Issue:** [#15](https://github.com/bro26man-hash/human-perception-podcast/issues/15)  
**Target Release:** Q2 2027  
**Focus:** MR interfaces, spatial UI, wayfinding, and the WebXR spec's visual-first bias.

### Core Question
*If the interface is the entire room, what does UX design even mean?*

### Topics
1. **DOM Overlays in XR Canvas** — webxr #1414: rendering 2D UI into 3D worlds without performance collapse
2. **Wayfinding is Broken** — webxr #992: users don't know where they are in immersive sessions (36 comments)
3. **The Spec Is Visually Blind** — webxr #815 (41 comments): the spec precludes non-visual uses
4. **Dynamic Foveation & Privacy** — webxr #1420: hiding gaze data while reducing periphery rendering
5. **Input Fragmentation** — MRTK #914: MX Ink on Quest; MRTK #511: vendor RealityProviders architecture
6. **WebAR: Markerless Not Ready** — mind-ar-js #556 & #526: markerless tracking aspirational not operational
7. **Neuroadaptive MR** — Team Syncer (OpenGalea): 8-channel EEG + Quest 3 for brain-controlled experiences

### 🔥 Hottest Debate
> **If AR/VR hardware has converged across platforms (HoloLens, Quest 3, Vision Pro, XREAL), why do developers still write platform-specific input code?**
> MRTK #914: hardware convergence without software abstraction. MRTK #511: should vendor RealityProviders live in core MRTK or as plugins? This shapes MR development for the next decade.

### 🔥 Key Issues Surfaced
| Issue | Repo | Why It Matters |
|-------|------|----------------|
| #221 | microsoft/MixedRealityCompanionKit | Holograms stick to camera — the core MR presence failure (18 comments) |
| #228 | microsoft/MixedRealityCompanionKit | Calibration fragility blocks research reproducibility (19 comments) |
| #992 | immersive-web/webxr | Wayfinding broken in immersive sessions (36 comments) |
| #815 | immersive-web/webxr | Spec precludes non-visual uses (41 comments) |
| #914 | MixedRealityToolkit/MixedRealityToolkit-Unity | Convergence without abstraction: MX Ink on Quest |
| #511 | MixedRealityToolkit/MixedRealityToolkit-Unity | Vendor RealityProviders architecture question |
| #1414 | immersive-web/webxr | DOM overlays in XR canvas |
| #1420 | immersive-web/webxr | Dynamic foveation spec direction |
| #556 | hiukim/mind-ar-js | Markerless AR: production-ready or aspirational? |
| #526 | hiukim/mind-ar-js | MindAR abandonware question (13 comments) |

### 🎤 Suggested Guests
| Name | GitHub | Expertise |
|------|--------|-----------|
| **jeromeetienne** | @jeromeetienne | Creator, AR.js (15.8k ⭐); web AR pioneer |
| **hiukim** | @hiukim | Creator, MindAR (2.7k ⭐); on-device TF.js tracking |
| **cabanier** | @cabanier | W3C Immersive Web; DOM overlays & visibility spec |
| **AdaRoseCannon** | @AdaRoseCannon | Google & W3C; dynamic foveation; accessibility |
| **himorin** | @himorin | WebXR security & spatial mapping privacy |
| **chrisdavidmills** | @chrisdavidmills | WebXR editor; visibility-mask events |
| **keveleigh** | @keveleigh | Microsoft MRTK maintainer; vendor architecture |
| **Ivan Campos** | @IvanCampos | visionOS-examples (405 ⭐); Vision Pro spatial UI |
| **dongyoonpark** | @dongyoonpark | Microsoft MRDL; HoloLens 2 interaction design |
| **richardinerickson** | @richardinerickson | Microsoft MRDL; Surfaces MR app; tactile sensation |
| **Team Syncer** | OpenGalea | Neuroadaptive MR: EEG + Quest 3 brain-controlled experiences |

---

## Active Repos Survey Summary

| Category | Top Repos | Stars |
|----------|-----------|-------|
| **3D / Web Graphics** | `mrdoob/three.js`, `playcanvas/engine` | 115k / 16.7k |
| **Web AR** | `AR-js-org/AR.js`, `hiukim/mind-ar-js` | 15.8k / 2.7k |
| **WebXR Spec** | `immersive-web/webxr` | 3.1k |
| **Social VR** | `Hubs-Foundation/hubs` | 2.2k |
| **OpenXR Streaming** | `WiVRn/WiVRn` | 1.6k |
| **MR Toolkit** | `microsoft/MixedRealityToolkit-Unity` | 6.1k |
| **Spatial Audio** | `freeman-jiang/beatsync`, `leomccormack/Spatial_Audio_Framework` | 3.2k / 748 |
| **360° Media** | `google/spatial-media` | 2.1k |
| **Web Audio** | `GoogleChrome/omnitone` | 911 |
| **XR Engine** | `StereoKit/StereoKit`, `godotengine/godot` | 1k+ |
| **AR SDK** | `google-ar/arcore-unity-sdk`, `Unity-Technologies/arfoundation-samples` | Various |
| **visionOS** | `IvanCampos/visionOS-examples` | 405 |
