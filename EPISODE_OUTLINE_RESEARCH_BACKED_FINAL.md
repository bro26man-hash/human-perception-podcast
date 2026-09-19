# 🎙️ The Future of Human Perception — Episode Outline (Research-Backed Final)

## Series Overview

A podcast exploring the engineering and human science behind how technology reshapes perception. Each episode is grounded in live GitHub research from the most active AR/MR/Spatial Computing repositories, and each is seeded with potential guests drawn from those communities.

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency & the 20ms rule
**Key Debate:** Can foveation trick the brain into forgiving lag — or is it sensory deception?

### Core Topics
- Motion-to-photon (MTP) latency: what it is, how it's measured, and why 20ms is the magic number
- The neuroscience of perceptual latency: visual persistence, phi phenomenon, and the brain's prediction engine
- Foveated rendering as a latency-hiding trick — is it cheating or clever engineering?
- **NEW from GitHub research:** Camera↔IMU clock offsets of 13–35ms on mid-range Android devices (ARCore #1779) — invisible to developers but catastrophic for perceptual stability
- **NEW:** WiVRn #1099 — Per-client scheduled frames stalling `xrEndFrame` for up to 47 minutes after Quest 3 refocus; the compositor reports 80 FPS but users experience minutes-long freezes
- **NEW:** ALVR #334 — VR streaming stacks underreport total system latency by 30–50%, meaning the "20ms rule" may be unreachable even when numbers look fine
- Tetherless vs. tethered rendering pipelines and their latency profiles
- Predictive tracking and the head-mounted display != display problem

### GitHub Sources & Hot Issues
- [google-ar/arcore-android-sdk#1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) — Camera↔IMU Clock Offset 13–35ms on Xiaomi/OPPO
- [WiVRn/WiVRn#1099](https://github.com/WiVRn/WiVRn/issues/1099) — Future Per-Client Scheduled Frames Stall xrEndFrame (40+ comments, 15+ reactions)
- [polygraphene/ALVR#334](https://github.com/polygraphene/ALVR/issues/334) — Latency Measurements Are Missing Info / Incorrect
- [ValveSoftware/SteamVR-for-Linux#21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) — Tracking Not Smooth and a Little Delayed (97+ comments)
- [immersive-web/webxr#1420](https://github.com/immersive-web/webxr/issues/1420) — Dynamic Foveation & Visibility Masking
- [microsoft/OpenXR-MixedReality#131](https://github.com/microsoft/OpenXR-MixedReality/issues/131) — Frame Timestamp Precision on HoloLens 2

### Potential Guests
- **jeromeetienne** — Creator of AR.js (15.8k ⭐), pioneer of Web AR at 60fps; perspective on latency from the web AR frontier
- **hiukim** — Creator of MindAR (2.7k ⭐), TensorFlow.js-based Web AR; can speak to tracking-vs-latency tradeoffs in open-source AR
- **xytovl** — WiVRn creator; deep expertise in OpenXR runtime latency and compositor scheduling
- **Nicolò Carpignoli** — AR.js former maintainer; architectural perspective on how AR.js handles vs. hides latency
- **param-fsd** — MindAR tracking stability researcher; hands-on experience with the gap between open-source and commercial tracking quality
- **yongsen_mao** — SpatialLM lead researcher (NeurIPS 2025); can bridge the discussion to how 3D LLMs might predict and compensate for perceptual latency

### Debate Arena
**Motion smoothing vs. perceptual honesty:** Should developers be ethically required to disclose when they're "hiding" latency via reprojection? Is foveated rendering a feature or a deception? The ALVR #334 finding that we underreport latency by 30–50% suggests the entire industry may be optimizing against fictionally low numbers.

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics & the audio presence paradox
**Key Debate:** Why is the WebXR spec still visual-only for spatial audio — and what would it take to fix it?

### Core Topics
- Head-Related Transfer Functions (HRTFs): how your ears shape what you hear
- Ambisonics vs. binaural: which paradigm wins for presence?
- **The audio presence paradox:** perfect spatial audio can feel *less* real than imperfect audio because the brain detects the artifact
- **NEW from GitHub research:** WebXR has zero first-class spatial audio spec — Issue #390 has been open for 8 years with 30 comments and no resolution
- **NEW:** GoogleChrome/omnitone#2 — Chrome's spatial audio library doesn't work on mobile browsers (10 years, 23 comments, still unresolved)
- **NEW:** microsoft/MixedReality-WebRTC#573 — ADM2 audio pipeline breaks with multiple output devices, meaning spatial audio fails precisely during social XR
- **NEW:** leomccormack/Spatial_Audio_Framework#58 — ISM room acoustics modeling has a band-summing bug that invalidates perceptual research
- **NEW:** Hubs-Foundation/hubs#1853/#2643/#5057 — Spatial audio degrades catastrophically with more users (30+ comments per issue)
- Audio-only devices and accessibility: Issue #892 — is WebXR ignoring a whole class of user?
- Dynamic HRTF personalization vs. generic kernels
- The resolution asymmetry: 8K HEVC on Quest 2 for visuals, 48kHz mono audio as "good enough"

### GitHub Sources & Hot Issues
- [immersive-web/webxr#390](https://github.com/immersive-web/webxr/issues/390) — "Consider hooking up sound source nodes in the API somehow" (30 comments, open since 2018)
- [GoogleChrome/omnitone#2](https://github.com/GoogleChrome/omnitone/issues/2) — Support for Mobile Browsers (23 comments, 10 years open)
- [immersive-web/webxr#892](https://github.com/immersive-web/webxr/issues/892) — Audio-only devices accessibility (a11y-tracker label)
- [microsoft/MixedReality-WebRTC#573](https://github.com/microsoft/MixedReality-WebRTC/issues/573) — ADM2 Does Not Play Sound with Multiple Audio Outputs
- [leomccormack/Spatial_Audio_Framework#58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) — ISM RIR Incorrect Summing of Bands
- [Hubs-Foundation/hubs#1853](https://github.com/Hubs-Foundation/hubs/issues/1853) — Spatial Audio Quality Degrades with Users
- [microsoft/MixedRealityToolkit-Unity PR#2775](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/2775) — Port audio influencers and effects from HTK (spatial sound PR by david-c-kline)

### Potential Guests
- **cwilso** — WebXR spec editor, authored the spatial audio integration issue (#390); can speak to why the spec lagged
- **toji** — WebXR accessibility advocate, authored Issue #892 on audio-only devices
- **ddorwin** — WebXR spec co-editor, co-authored Issue #815 on non-visual perception
- **david-c-kline** — MRTK spatial audio PR author; built the audio influencers system for HoloLens
- **misslivirose** — Hubs spatial audio & accessibility lead; dealing with the scaling problem daily
- **robertlong** — Hubs audio reliability maintainer
- **Yongsen Mao** — SpatialLM researcher; could bridge spatial audio with 3D scene understanding

### Debate Arena
**The spec gap as perceptual discrimination:** If the WebXR spec has no spatial audio channel, is that scope management or a form of sensory exclusion? The omnitone#2 finding that mobile browsers — where billions of users are — can't run spatial audio at all suggests the "visual-first" bias isn't just an oversight; it's a structural perceptual inequality.\n
---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift & wayfinding
**Key Debate:** Is the WebXR spec blind to non-visual perception — and are we still designing MR for 2D?

### Core Topics
- Hologram drift: why virtual objects in MR slowly "slide" and how registration error erodes trust
- **NEW from GitHub research:** MRC#228 — SpectatorView calibration works once and never twice; fundamental research reproducibility blocker for MR
- **NEW:** MRC#221 — Holograms that "stick to camera" instead of staying anchored break the core promise of mixed reality
- Hand tracking fidelity: from 21-jointed skeletal hands to fine diaphragmatic gesture
- Wayfinding in mixed reality: cognitive maps, landmarks, and the 3D navigation UX problem
- **NEW:** webxr#992 — Users in immersive XR sessions can't find content that wasn't visible when they entered (36 comments)
- **NEW:** webxr#815 — Spec language precludes non-visual uses (41 comments, 8 years open)
- The WebXR spec's visual bias: non-visual modalities are extensions, not primitives
- MR interface design patterns: platelets, menus-at-arm's-length, and the "air tap" standardization problem
- Eye tracking as the next input layer: foveated rendering + intent detection
- **NEW:** MRTK#914 — MX Ink MR Stylus for Meta Quest; platform convergence without interface abstraction
- **NEW:** MRTK#511 — Vendor Plugin Architecture: should vendor-specific RealityProviders live inside MRTK core?
- **NEW:** AR.js #833/#834 — City-scale markerless AR breaks because local SLAM doesn't scale to global reference frames; geospatial AR needs earth-centered coordinates
- The "cognitive load" crisis: when every surface is a UI, what do you look at?

### GitHub Sources & Hot Issues
- [immersive-web/webxr#815](https://github.com/immersive-web/webxr/issues/815) — Spec Language Precludes Non-Visual Uses (41 comments)
- [immersive-web/webxr#992](https://github.com/immersive-web/webxr/issues/992) — Content in Immersive Session Search Around (36 comments)
- [microsoft/MixedRealityCompanionKit#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — SpectatorView Calibration Instability (19 comments)
- [microsoft/MixedRealityCompanionKit#221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — Holograms Sticking to Camera (18 comments)
- [MixedRealityToolkit/MixedRealityToolkit-Unity#914](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914) — MX Ink MR Stylus for Meta Quest
- [MixedRealityToolkit/MixedRealityToolkit-Unity#511](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/511) — Vendor Plugin Architecture
- [AR-js-org/AR.js#833](https://github.com/AR-js-org/AR.js/issues/833) — Markerless location-based AR, more realistic placement
- [AR-js-org/AR.js#681](https://github.com/AR-js-org/AR.js/issues/681) — AR.js-next: ECS architecture & roadmap
- [microsoft/MixedRealityToolkit-Unity PR#2795](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/2795) — Alternate Solver Handler Scene Object attachment (instability in spatial tracking)

### Potential Guests
- **jeromeetienne** — AR.js creator; the philosophical rebel who gave up on markerless and why
- **nickw1** — AR.js location-based AR contributor; created arjs-peakfinder POI browser; deepest knowledge of AR drift and GPS-based challenges
- **kalwalt** — AR.js current maintainer; holds the keys to AR.js's architectural future
- **dogzilla** — Web AR community, MindAR fork maintainer; represents the for-the-people voice
- **CoderSilas** — Web AR developer who found encantar.js as a successor; the canary in the coal mine
- **kylebakerio** — WebXR/ARCore integration advocate; pragmatic position on markerless AR
- **Yongsen Mao** — SpatialLM researcher; could discuss how 3D LLMs might enable "true" spatial understanding vs. local SLAM
- **ddorwin** — WebXR co-editor; the spec's own voice on non-visual perception

### Debate Arena
**The Interface Paradigm Trap:** Despite being "spatial" computing, XR interfaces are still designed around 2D paradigms — gamepads flattened into Gamepad API (#993), 2D input devices traversing 3D space. Are we building "3D interfaces with 2D constraints" or "truly spatial interfaces"? The MRTK#511 vendor plugin decision and the webxr#815 spec language both suggest the answer is: we're still trapped in 2D, and the "3D" part is mostly visual.

---

## Cross-Episode Themes

| Theme | Episodes | GitHub Anchor |
|---|---|---|
| **Perceptual ≠ Measured** | Ep 1, Ep 3 | ARCore #1779, WiVRn #1099, ALVR #334, MRC #228 |
| **The Spec Gap as Discrimination** | Ep 2, Ep 3 | webxr #390 (8yr), webxr #815 (41c), omnitone #2 (10yr) |
| **Presence vs. Fidelity** | Ep 1, Ep 2 | Foveated rendering, HRTF personalization, ISM bug |
| **Open Source as the Battleground** | All | AR.js, MindAR, MRTK, WebXR spec repos |
| **Accessibility as Design Driver** | Ep 2, Ep 3 | webxr #892 (audio-only), MRC #221 (registration) |
| **The 20ms Rule** | Ep 1, Ep 3 | ARCore #1779, SteamVR #21, OpenXR #131 |
| **Spatial Audio Has No Standard** | Ep 2 | webxr #390, omnitone #2, MRTK-WebRTC #573 |
| **Registration Fragility** | Ep 3 | MRC #228, MRC #221, AR.js #833 |

---

## Production Notes

- **Recording format:** Interview + live GitHub issue walkthrough
- **Segment structure:** 20 min research deep-dive → 15 min guest interview → 10 min "Debate Arena" (hosted discussion of the week's hottest issue)
- **GitHub integration:** Each episode links to 3–5 real open issues; listeners can join the discussion
- **Editorial cadence:** Bi-weekly release, with "mid-week briefs" on breaking issues
- **New:** Each episode should include a "Source Audit" segment linking directly to the GitHub issues that surfaced the topic

---

## Guest Outreach Tracker

| Guest | Episode | Status | Notes |
|---|---|---|---|
| jeromeetienne | Ep 1, Ep 3 | ☐ Not contacted | AR.js creator, 15.8k ⭐ |
| hiukim | Ep 1 | ☐ Not contacted | MindAR creator, 2.7k ⭐ |url=https://github.com/hiukim/mind-ar-js/issues/526</a> |
| Nicolò Carpignoli | Ep 1 | ☐ Not contacted | AR.js former maintainer; markerless AR authority |
| xytovl | Ep 1 | ☐ Not contacted | WiVRn creator; OpenXR latency expert |
| param-fsd | Ep 1 | ☐ Not contacted | MindAR tracking stability researcher |
| cwilso | Ep 1, Ep 2 | ☐ Not contacted | WebXR spec editor; spatial audio #390 |
| toji | Ep 2 | ☐ Not contacted | WebXR a11y advocate; #892 |
| ddorwin | Ep 2, Ep 3 | ☐ Not contacted | WebXR co-editor; non-visual perception |
| david-c-kline | Ep 2 | ☐ Not contacted | MRTK spatial audio PR author |
| misslivirose | Ep 2 | ☐ Not contacted | Hubs spatial audio & accessibility lead |
| yongsen_mao | Ep 1, Ep 2, Ep 3 | ☐ Not contacted | SpatialLM lead (NeurIPS 2025) |
| nickw1 | Ep 3 | ☐ Not contacted | AR.js location-based AR; arjs-peakfinder |
| kalwalt | Ep 3 | ☐ Not contacted | AR.js current maintainer |
| dogzilla | Ep 3 | ☐ Not contacted | Web AR community; MindAR fork |
| CoderSilas | Ep 3 | ☐ Not contacted | Web AR developer; encantar.js explorer |
| kylebakerio | Ep 3 | ☐ Not contacted | WebXR/ARCore integration advocate |

*Last updated: September 2026 — GitHub-research backed from live issue audit*
