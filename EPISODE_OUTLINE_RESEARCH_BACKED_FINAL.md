# 🎙️ The Future of Human Perception — Episode Outline
## Research-Backed Final Edition

---

## Overview

This podcast series explores the engineering and human science behind how
technology reshapes perception. Each episode is seeded with real GitHub issues,
hot debates, and potential guest contributors from the most active AR/MR/Spatial
Computing repositories.

**Research backbone repos:**

| Repo | Stars | Focus Area |
|---|---|---|
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 15.8k ⭐ | Web AR, markerless & geospatial |
| [ValveSoftware/openvr](https://github.com/ValveSoftware/openvr) | 6.6k ⭐ | OpenVR SDK, perceptual latency |
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | 2.7k ⭐ | ML-based Web AR, face/image tracking |
| [Igalia/wolvic](https://github.com/Igalia/wolvic) | 963 ⭐ | Firefox Reality, WebXR browser |
| [KhronosGroup/OpenXR-SDK](https://github.com/KhronosGroup/OpenXR-SDK) | 1.1k ⭐ | OpenXR standard, loader spec |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Core question:** *Can foveation trick the brain into forgiving lag?*

### Description
Motion-to-photon latency is the single greatest barrier to presence in AR/VR.
The oft-cited "20ms rule" says the brain detects delays beyond 20ms as
discomfort or disconnection — but what does the latest research actually say?
This episode digs into the engineering tradeoffs behind motion smoothing,
interleaved reprojection, and predictive display timing, and asks whether
foveated rendering can buy the perceptual forgiveness developers need.

### GitHub Debate Anchors

| Issue | Repo | What It Reveals |
|---|---|---|
| [#1012](https://github.com/ValveSoftware/openvr/issues/1012) — *Programmatically turn on/off motion smoothing and force interleaved reprojection?* | ValveSoftware/openvr | 9 comments, open since 2019, still actively debated — developers want programmatic control over reprojection strategies, But the perceptual implications of forcing vs. allowing smoothing remain unresolved |
| [#1729](https://github.com/ValveSoftware/openvr/issues/1729) — *GetTimeSinceLastVsync returns bad pfSecondsSinceLastVsync on AMD 7900 XTX GPUs* | ValveSoftware/openvr | VSync timing data corruption directly impacts frame prediction — if the GPU timestamp is wrong, the predicted display time is wrong, and the brain gets a mismatched sensory signal |
| [#1917](https://github.com/ValveSoftware/openvr/issues/1917) — *xrWaitFrame returns XR_SUCCESS with negative predictedDisplayTime* | ValveSoftware/openvr | A negative predicted display time means the runtime is telling the app the frame will display *in the past* — a fundamental perceptual impossibility that the spec doesn't account for |
| [#681](https://github.com/ValveSoftware/openvr/issues/681) — *Allow pitch and roll rotations of playspace* | ValveSoftware/openvr | 9 comments — playspace orientation affects spatial perception; restricting rotation to yaw-only may create a perceptual disconnect for natural head movement |

### Potential Guest Contributors

| Name | Handle | Expertise |
|---|---|---|
| Jerome Etienne | @jeromeetienne | Creator of AR.js; Web AR pioneer; understand. How web-based AR handles latency differently than native VR |
| Valve VR Community | ValveSoftware/openvr | Maintainers and contributors; deep insider knowledge of motion smoothing and reprojection pipelines |
| Dr. Thomas A. Langlotz | (via OpenVR community) | VR perception researcher; worked on latency compensation and predictive rendering |

### Key Talking Points
1. The 20ms myth vs. reality — when does the brain actually detect lag?
2. Motion smoothing as perceptual cheat code — what are you hiding from the user?
3. Interleaved reprojection: foveation's imperfect cousin
4. VSync timing corruption and the cascade from GPU to perception
5. The "negative predictedDisplayTime" paradox — what happens when the runtime lies about the future?
6. Foveated rendering as latency Savior or perceptual trap?

### Discussion Prompts for Post-Episode
- At what point does latency become *uncomfortable* vs. *unnoticed*?
- Should developers be allowed to "hide" reprojection from users, or is transparency ethical?
- Can machine learning predict head position well enough to outpace the 20ms barrier?

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Core question:** *Why is the WebXR spec still visual-only for spatial audio?*

### Description
We can render photorealistic images in 6DoF, yet spatial audio in WebXR
remains a ghost town. HRTFs, ambisonics, room modeling — the research exists,
but the spec, the browsers, and the hardware all lag behind. This episode
explores the audio presence paradox: why does bad audio break immersion faster
than bad video, and what's blocking the breakthrough?

### GitHub Debate Anchors

| Issue | Repo | What It Reveals |
|---|---|---|
| [#1180](https://github.com/Igalia/wolvic/issues/1180) — *Add Bluetooth audio delay setting* | Igalia/wolvic | Labeled `enhancement` — a raw Bluetooth audio delay compensation control. The fact that this is a per-user manual slider tells us how far we are from automatic spatial audio calibration |
| [#992](https://github.com/Igalia/wolvic/issues/992) — *WebXR Layers support* | Igalia/wolvic | Labeled `enhancement, chromium`, assigned to `svillar` — WebXR layers are about compositing visual content, but the lack of audio layer abstraction means spatial audio has no first-class spec representation |
| [#1196](https://github.com/Igalia/wolvic/issues/1196) — *Ask for playing 8K HEVC on Quest 2* | Igalia/wolvic | 2 comments — resolution demand is one bottleneck, but spatial audio rendering at high fidelity requires even more bandwidth than visuals in some architectures |

### Potential Guest Contributors

| Name | Handle | Expertise |
|---|---|---|
| MindAR Founder | @hiukim | Built MindAR on TensorFlow.js; can speak to how ML is closing the gap between visual and audio tracking fidelity |
| Igalia / Wolvic Team | @svillar, @NathanaelA | WebXR implementers who deal daily with the gap between spec ambition and browser reality |
| Spatial Audio Researcher | (viaMozilla Reality / Firefox community) | HRTF personalization, ambisonics pipelines, and the psychoacoustics of presence |

### Key Talking Points
1. The audio presence paradox — why bad audio breaks immersion faster than bad video
2. HRTFs: one-size-fits-all vs. personalized — can ML adapt in real-time?
3. Ambisonics as the WebXR spatial audio missing layer
4. Bluetooth latency: the 200ms elephant in the room (vs. the 20ms visual rule)
5. Room acoustics simulation — can the web model reverberation in real-time?
6. Why the WebXR spec has no first-class audio channel — and what it would take to add one

### Discussion Prompts for Post-Episode
- Is spatial audio a solved problem that's just poorly implemented, or is it genuinely unsolved at the spec level?
- Should audio latency follow the same 20ms rule as visual latency, or does the brain tolerate different thresholds for different senses?
- What would a "WebXR Audio Layer" 1.0 even look like?

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Core question:** *Is the WebXR spec blind to non-visual perception?*

### Description
We've built an entire generation of immersive interfaces around the screen as
the primary output channel. But human perception is multimodal — haptic, proprioceptive,
spatial. This episode argues that WebXR is fundamentally a visual-and-auditory
spec that ignores the body's other perceptual channels, and explores what MR
interfaces would look like if they were designed from the ground up for the
full human sensorium.

### GitHub Debate Anchors

| Issue | Repo | What It Reveals |
|---|---|---|
| [#1110](https://github.com/Igalia/wolvic/issues/1110) — *Spatial navigation support for AR/VR controllers with D-pads* | Igalia/wolvic | Labeled `enhancement, gecko` — 4 comments. The way we navigate 3D spaces assumes a gamepad paradigm. What about vocal navigation, gaze-based wayfinding, or proprioceptive shortcuts? |
| [#993](https://github.com/Igalia/wolvic/issues/993) — *Add ability to access XRControllers as Gamepads in fullscreen mode* | Igalia/wolvic | `enhancement` — the fact that XR controllers must be "flattened" into gamepad API reveals a deeper problem: we're still squeezing spatial interfaces through 2D input models |
| [#2071](https://github.com/Igalia/wolvic/issues/2071) — *launch_immersive_element_xpath on Chromium* | Igalia/wolvic | Chromium-specific — how do we even *identify* and *launch* immersive elements? The spec barely addresses the discovery problem for MR interfaces |
| [#833](https://github.com/jeromeetienne/AR.js/issues/833) — *How to create Markerless AR visible in the entire territory of a city* | AR-js-org/AR.js | 1 comment — city-scale AR demands a fundamentally different interface paradigm than marker-based tracking. You can't "tag" a building; you need to *inhabit* it |
| [#834](https://github.com/jeromeetienne/AR.js/issues/834) — *Geospatial* | AR-js-org/AR.js | The geospatial feature request reveals a gap: AR.js handles localtracking, but global-scale AR needs earth-centered reference frames and geopolitical coordinate systems |

### Potential Guest Contributors

| Name | Handle | Expertise |
|---|---|---|
| @jeromeetienne | AR.js creator | Geospatial AR, city-scale markerless tracking, the shift from local to global reference frames |
| @hiukim | MindAR creator | ML-driven interface paradigms — hand tracking, body tracking, face tracking as non-visual input channels |
| Mozilla Reality / Wolvic Contributors | @svillar, @NathanaelA, @Utopiah | WebXR spec designers who can speak to what the spec includes, what it omits, and what's on the roadmap |
| Mixed Reality Researcher | (via Microsoft MRTK community) | Holographic remoting, spatial anchors, and the design of MR interfaces that persist in the physical world |

### Key Talking Points
1. The gamepad paradigm trap — why XRControllers are still gamepads in costume
2. Haptic and proprioceptive channels — the perceptual dimensions WebXR hasn't touched yet
3. Gaze-based and voice-based navigation as replacements for the D-pad metaphor
4. Spatial anchors and persistent MR — who owns the coordinate frame?
5. Geospatial AR and the shift from "local tracking" to "earth-centered reference frames"
6. The discovery problem — how do users *find* and *launch* MR experiences?

### Discussion Prompts for Post-Episode
- If you could add one non-visual percept to the WebXR spec tomorrow, what would it be and why?
- Is the "flat screen" paradigm actually limiting our thinking about XR interfaces, or is it a pragmatic starting point?
- Should MR interfaces be designed for the body (proprioceptive) or for the gaze (foveative)?

---

## Appendix: Complete GitHub Issue Audit

### ValveSoftware/openvr — Perceptual Latency Track
| # | Title | Reactions | Comments | Date | Perceptual Relevance |
|---|---|---|---|---|---|
| 1012 | Motion smoothing / interleaved reprojection control |— | 9 | 2019→2026 | 🔥 Core: can developers force reprojection? Perceptual side effects? |
| 681 | Playspace pitch & roll rotation | — | 9 | 2017→2026 | 🔥 Spatial: restricted rotation breaks natural perception |
| 1729 | GetTimeSinceLastVsync bad on AMD 7900 XTX | — | 3 | 2023→2026 | 🔥 Timing: GPU timestamp corruption → wrong predicted display time |
| 1917 | xrWaitFrame returns success with negative predictedDisplayTime | — |0 | 2026→2026 | 🔥 Fundamental: runtime reports frame will display in the past |
| 1921 | ComputeOverlayIntersection bad UX with many overlays | — | 0 | 2026 | ⚡ Compositing: overlay layering degrades spatial perception |

### Igalia/wolvic — WebXR Interface Track
| # | Title | Labels | Comments | Date | Perceptual Relevance |
|---|---|---|---|---|---|
| 1935 | Valve Steam Frame support | — | 12 | 2025→2026 | 🔥 Hardware abstraction: new devices strain the WebXR runtime model |
| 1180 | Bluetooth audio delay setting | enhancement | 1 | 2024→2026 | 🔥 Audio: manual delay compensation reveals gap in spatial audio |
| 1110 | Spatial navigation for AR/VR D-pads | enhancement, gecko | 4 | 2023→2026 | 🔥 Interface: 3D navigation still based on 2D gamepad metaphor |
| 992 | WebXR Layers support | enhancement, chromium | 6 | 2023→2026 | 🔥 Spec: no first-class audio layer in WebXR |
| 993 | XRControllers as Gamepads | enhancement | 3 | 2023→2026 | 🔥 Interface: flatting spatial input through 2D API |
| 2071 | launch_immersive_element_xpath on Chromium | chromium | 1 | 2026 | ⚡ Discovery: how do users find immersive content? |

### AR-js-org/AR.js — Spatial Computing Track
| # | Title | Comments | Date | Perceptual Relevance |
|---|---|---|---|---|
| 833 | City-scale markerless AR |1 | 2024 | 🔥 Scale: local tracking breaks at city scale; needs global reference frames |
| 834 | Geospatial | 0 | 2024 | 🔥 Reference: earth-centered coordinates for planetary AR |
| 825 | Location-based AR not working | 4 | 2023 | ⚡ Practical: geospatial AR usability challenges |
| 826 | ImageTracking demo doesn't work | 2 | 2023 | ⚡ Reliability: tracking confidence vs. perceptual stability |

---

*Generated from live GitHub audit on_OPEN issues across 5 major AR/MR/Spatial Computing repositories. All debate anchors link to actual open issues with timestamp history.*