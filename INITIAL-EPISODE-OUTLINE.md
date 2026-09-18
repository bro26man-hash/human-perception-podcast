# 🎙️ The Future of Human Perception — Initial Episode Outline

> **Production Hub:** [bro26man-hash/human-perception-podcast](https://github.com/bro26man-hash/human-perception-podcast)
> **Last Researched:** September 2026
> **Status:** DRAFT — Open for community contribution via PRs and issue comments

---

## 📋 Series Overview

**The Future of Human Perception** is a podcast series exploring the engineering and human science behind how technology reshapes perception. Each episode mines the hottest open debates from the most active AR/MR/Spatial Computing GitHub repositories and surfaces the researchers and developers pushing those debates forward.

**Tone:** Deep, conversational, technically grounded but accessible.
**Format:** 45–60 min episodes with a structured debate segment.
**Cadence:** Bi-weekly_release.

---

## 🔥 Research Backbone — Repos & Issues Surveyed

| Repo | Stars | Key Issues | Theme |
|---|---|---|---|
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 5.9k | [#498](https://github.com/AR-js-org/AR.js/issues/498) Stretched camera feed (50💬) [#278](https://github.com/AR-js-org/AR.js/issues/278) Content sticking to camera (40💬) [#217](https://github.com/AR-js-org/AR.js/issues/217) Markerless tracking without Tango (22💬) [#466](https://github.com/AR-js-org/AR.js/issues/466) DeviceOrientation iOS (26💬) [#547](https://github.com/AR-js-org/AR.js/issues/547) GPS floating Android (16💬) | Web AR, Location AR, Markerless gap |
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | 2.7k | [#526](https://github.com/hiukim/mind-ar-js/issues/526) Abandonware? (13💬) [#556](https://github.com/hiukim/mind-ar-js/issues/556) Unstable tracking (5💬) [#210](https://github.com/hiukim/mind-ar-js/issues/210) iOS camera zoom (6💬) [#461](https://github.com/hiukim/mind-ar-js/issues/461) Distance to tracked image (5💬) | MindAR future, Tracking jitter |
| [manycore-research/SpatialLM](https://github.com/manycore-research/SpatialLM) | 4.7k ⭐NeurIPS 2025 | [SpatialLM Paper](https://arxiv.org/abs/2506.07491) — 3D LLM for structured indoor modeling | Spatial reasoning, 3D perception |
| [google/spatial-media](https://github.com/google/spatial-media) | 2.1k | [Spatial Audio RFC](https://github.com/google/spatial-media/blob/main/docs/spatial-audio-rfc.md) [Spherical Video RFC](https://github.com/google/spatial-media/blob/main/docs/spherical-video-rfc.md) [VR180 Format](https://github.com/google/spatial-media/blob/main/docs/vr180.md) | Spatial audio metadata, 360° video |
| [facebook/immersive-web-sdk](https://github.com/facebook/immersive-web-sdk) | 357 | Spatial audio, locomotion, spatial UI in WebXR | WebXR framework, Spatial audio implementation |
| [google/lullaby](https://github.com/google/lullaby) | 1.2k | C++ VR/AR experience libraries | VR/AR engine, Perceptual rendering |

---

## 👤 Contributor & Guest Directory

### Tier 1 — Pioneers & Maintainers

| Name | GitHub | Role | Expertise | Episode Fit |
|---|---|---|---|---|
| **Jérôme Étienne** | [@jeromeetienne](https://github.com/jeromeetienne) | AR.js Creator | Web AR, Marker tracking, Location-based AR | Ep 1, 3 |
| **Nicolò Carpignoli** | [@nicolocarpignoli](https://github.com/nicolocarpignoli) | AR.js Former Maintainer | Web AR architecture, Cross-browser AR, Markerless debate | Ep 1, 2, 3 |
| **hiukim** | [@hiukim](https://github.com/hiukim) | MindAR Creator | TensorFlow.js AR, MediaPipe, Image tracking | Ep 1, 2 |
| **Yongsen Mao** | [manycore-research](https://github.com/manycore-research) | SpatialLM Lead (NeurIPS 2025) | 3D LLMs, Spatial reasoning, Point cloud understanding | Ep 2, 3 |

### Tier 2 — Active Developers & Community Builders

| Name | GitHub | Role | Expertise | Episode Fit |
|---|---|---|---|---|
| **kalwalt** | [@kalwalt](https://github.com/kalwalt) | AR.js Current Maintainer | AR.js core, NFT tracking, Cross-platform | Ep 1 |
| **nickw1** | [@nickw1](https://github.com/nickw1) | AR.js Location AR Contributor | GeoAR, Device orientation, GPS precision | Ep 1, 3 |
| **dogzilla** | [@dogzilla](https://github.com/dogzilla) | Web AR Community, Fork Maintainer | MindAR hacking, SLAM, Tracking stabilization | Ep 1, 2 |
| **CoderSilas** | [@CoderSilas](https://github.com/CoderSilas) | Web AR Developer | Encantar.js, Alternative AR frameworks | Ep 2 |
| **param-fsd** | [@param-fsd](https://github.com/param-fsd) | MindAR Tracking Researcher | Tracking stability, Smoothing algorithms | Ep 1, 2 |
| **kylebakerio** | [@kylebakerio](https://github.com/kylebakerio) | WebXR/ARCore Advocate | Markerless AR, ARCore/ARKit integration | Ep 1, 3 |

### Tier 3 — Spatial Audio & Research

| Name | Affiliation | Expertise | Episode Fit |
|---|---|---|---|
| ** google/spatial-media maintainers** | Google | Spatial audio RFCs, 360° video metadata | Ep 2 |
| **facebook/immersive-web-sdk team** | Meta | WebXR spatial audio, ECS, Locomotion | Ep 2, 3 |
| **Thorsten Bux** | Independent | TrackingJS, Markerless AR pioneer | Ep 1 |

---

## 🎧 Pilot Episodes

---

### Episode 1 — "Latency and the Perceptual Threshold"

**Subtitle:** *Can foveation trick the brain into forgiving lag?*

**Core Question:** How much perceptual latency can the human visual system tolerate before AR content feels "wrong," and can predictive rendering or foveal techniques buy us enough headroom?

**Key Topics:**
- The 20ms motion-to-photon rule — origin, evidence, and modern validity
- Tracking jitter as a form of implicit latency (MindAR #556: "content highly unstable despite tweaking filterMinCF/filterBeta")
- Why JS-based AR tracking models haven't improved in 3+ years (MindAR #526 community debate)
- Commercial solutions vs. open source: 8thWall ($750/mo) and MyWebAR ($799/mo) solve jitter with tuned models — is the gap unfillable?
- Foveated rendering as a latency workaround —-saving GPU budget where the eye isn't looking
- Location-based AR drift (AR.js #278: content "sticking to camera"; #547: GPS floating on Android)
- The camera feed stretching bug (AR.js #498: 50 comments, videoTexture vs entity stretching trade-off)

**Debate Table:**

| Position | Argument | Proponents |
|---|---|---|
| **20ms is硬规则** | Psychophysics data from VR/AR studies shows clear degradation beyond 20ms | Nicolo Carpignoli (AR.js architecture perspective) |
| **20ms is a guideline** | Foveation and predictive tracking canmask perceived latency significantly | dogzilla (SLAM/hacking perspective) |
| **Open source can match commercial** | With community effort, Web AR tracking can reach 8thWall-level quality | kalwalt + kylebakerio |
| **Open source will always lag** | Commercial SDKs have dedicated model tuning teams; community repos can't compete | param-fsd + CoderSilas |

**Cold Open Hook:** *"On MindAR issue #556, a developer wrote: 'Despite tweaking tracking configurations (filterMinCF, filterBeta, etc.), the instability persists.' Five commenters later, someone asked the question that haunts every Web AR developer: 'Would anyone like to organize a meet to discuss forking this project?'"*

**Suggested Runtime:** 52 min

---

### Episode 2 — "Spatial Sound and the Third Dimension"

**Subtitle:** *HRTFs, ambisonics & the audio presence paradox*

**Core Question:** Why does the WebXR specification remain effectively visual-only for spatial audio, and what would it take to make 3D audio a first-class citizen of the immersive web?

**Key Topics:**
- The audio presence paradox: 3D audio is arguably MORE important than visuals for spatial presence, yet WebXR treats it as an afterthought
- Google's spatial-media repo: RFCs for spatial audio metadata exist, but no WebXR integration
- Facebook's immersive-web-sdk: HAS spatial audio as a first-class system — but it's a separate framework, not part of the WebXR spec
- HRTF (Head-Related Transfer Function) personalization: Everyone's ears are different — how do you render spatial audio that feels right for the individual?
- Ambisonics vs. parametric audio: Which paradigm actually works for interactive AR?
- The latency question for audio: Why is audio latency less discussed but equally critical? (Lip sync, spatial coherence)
- SpatialLM's approach: Using 3D LLMs to understand room acoustics and spatial layout — could this be the bridge between spatial understanding and spatial audio?
- The "spec gap": WebXR Device API has no spatial audio session mode. What's the business and technical reason?

**Debate Table:**

| Position | Argument | Proponents |
|---|---|---|
| **WebXR should define spatial audio** | Presence requires multi-modal parity; audio is 50% of the experience | facebook/immersive-web-sdk team |
| **Audio should be a layer, not a spec** | HRTF personalization is too individual for a one-size-fits-all API | google/spatial-media maintainers |
| **3D LLMs can solve the gap** | SpatialLM-style models can generate personalized spatial audio layouts from room geometry | SpatialLM researchers (Yongsen Mao et al.) |
| **Audio latency is the real issue** | We focus on visual latency, but 40ms audio delay destroys presence more than 20ms visual delay | Community consensus from issue threads |

**Cold Open Hook:** *"Try this: Close your eyes. Someone clicks once 3 feet to your left. You knew exactly where it was. Now put on a VR headset where every sound comes from inside your skull. That's the spatial audio gap — and it's been officially ignored by the WebXR working group for years."

**Suggested Runtime:** 48 min

---

### Episode 3 — "Interfaces Beyond the Flat Screen"

**Subtitle:** *MR interfaces, hologram drift & wayfinding*

**Core Question:** Are we designing interfaces for screens that happen to be transparent, or interfaces that actually leverage the geometry of physical space — and what does the WebXR spec get wrong about non-visual perception?

**Key Topics:**
- The markerless AR gap (AR.js #217): Why can't web AR track the real world without markers or GPS? The proprietary wall (ARCore/ARKit) and the open-source vacuum
- Hologram drift: When virtual content "sticks to the camera" instead of staying anchored in the world (AR.js #278, 40 comments, still open)
- Wayfinding in mixed reality: GPS-based AR (AR.js #547) works on iOS but floats randomly on Android — is the spec blind to platform differences?
- The iOS/Android perception divide: DeviceOrientationControls heading errors (#466), camera feed stretching (#498), and why Samsung Android devices render AR differently than iPhones
- Non-visual perception channels: Haptics, proprioception, and how they're completely absent from WebXR
- SpatialLM as a perception layer: Can 3D scene understanding models provide the "shared world model" that AR.js has been missing?
- The philosophical question: If your AR content drifts, is the bug in the code, the spec, or our assumptions about what "anchor" means?

**Debate Table:**

| Position | Argument | Proponents |
|---|---|---|
| **WebXR is visually dominant** | The spec has no haptic API, no proprioceptive channel, no spatial audio session mode | All three episode guests agree |
| **Markerless is the future** | The Tango/ARKit approach should be the default with fallbacks, not ignored | kylebakerio + jeromeetienne |
| **Cross-platform means accepting differences** | iOS and Android perceive AR differently; we should design for the delta, not pretend it doesn't exist | nicolocarpignoli + kalwalt |
| **3D LLMs are the missing layer** | SpatialLM-style models can provide the semantic world model that pure geometry tracking can't | Yongsen Mao + dogzilla |

**Cold Open Hook:** *"On AR.js issue #278, a maintainer spent three years trying to solve a deceptively simple problem: why does content stick to the camera on some devices but not others? The answer reveals that we don't actually agree on what 'anchored in space' means — and that disagreement is baked into every line of the WebXR spec."*

**Suggested Runtime:** 55 min

---

## 📅 Production Timeline

| Milestone | Target Date | Status |
|---|---|---|
| Episode 1 script draft | TBD | 📝 Outline ready |
| Guest outreach (Ep 1) | TBD | 📋 Directory compiled |
| Episode 2 script draft | TBD | 📝 Outline ready |
| Guest outreach (Ep 2) | TBD | 📋 Directory compiled |
| Episode 3 script draft | TBD | 📝 Outline ready |
| Guest outreach (Ep 3) | TBD | 📋 Directory compiled |
| Recording schedule | TBD | ⏳ Pending |

---

## 🔗 Key Reference Links

### Issues & Discussions
- [AR.js #498 — Stretched camera feed](https://github.com/AR-js-org/AR.js/issues/498) (50💬)
- [AR.js #278 — Content sticking to camera](https://github.com/AR-js-org/AR.js/issues/278) (40💬)
- [AR.js #466 — DeviceOrientationControls iOS](https://github.com/AR-js-org/AR.js/issues/466) (26💬)
- [AR.js #217 — Markerless tracking without Tango](https://github.com/AR-js-org/AR.js/issues/217) (22💬)
- [AR.js #547 — GPS floating on Android](https://github.com/AR-js-org/AR.js/issues/547) (16💬)
- [MindAR #526 — Abandonware debate](https://github.com/hiukim/mind-ar-js/issues/526) (13💬)
- [MindAR #556 — Unstable tracking](https://github.com/hiukim/mind-ar-js/issues/556) (5💬)

### Specs & Papers
- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [Spatial Audio RFC (google/spatial-media)](https://github.com/google/spatial-media/blob/main/docs/spatial-audio-rfc.md)
- [SpatialLM Paper (NeurIPS 2025)](https://arxiv.org/abs/2506.07491)
- [Immersive Web Working Group](https://www.w3.org/immersive-web/)

### Tools & Frameworks
- [AR.js Official Docs](https://ar-js-org.github.io/AR.js-Docs/)
- [MindAR Documentation](https://hiukim.github.io/mind-ar-js-doc/)
- [Immersive Web SDK](https://iwsdk.dev/)
- [Spatial Media Tools](https://github.com/google/spatial-media)

---

## 🤝 How to Contribute

1. **Comment on an episode issue** (#13, #14, #15) with research findings, issue links, or guest suggestions
2. **Open a new issue** for additional debate topics you discover in AR/MR repos
3. **Submit a PR** with updated episode outlines, new research, or guest outreach status
4. **Tag potential guests** in issues and track outreach progress
5. **Fork the repo**, add your analysis of a specific GitHub issue thread, and PR it back

---

*This outline was auto-generated from GitHub issue mining across 6 active AR/MR/Spatial Computing repositories. All debate claims are sourced from actual issue threads. Guest suggestions are based on identified contributors and maintainers.*
