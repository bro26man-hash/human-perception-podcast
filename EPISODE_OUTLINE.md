# 🎙️ The Future of Human Perception — Episode Outline

## Series Overview

A podcast exploring the engineering and human science behind how technology reshapes perception. Each episode is grounded in live GitHub research from the most active AR/MR/Spatial Computing repositories, and each is seeded with potential guests drawn from those communities.

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency & the 20ms rule
**Key Debate:** Can foveation trick the brain into forgiving lag?

### Topics
- Motion-to-photon (MTP) latency: what it is, how it's measured, and why 20ms is the magic number
- The neuroscience of perceptual latency: visual persistence, phi phenomenon, and the brain's prediction engine
- Foveated rendering as a latency-hiding trick — is it cheating or clever engineering?
- Rollout scan simulation in RetroArch (#16373) and its implications for perceived latency
- Tetherless vs. tethered rendering pipelines and their latency profiles
- The role of predictive tracking (Head-mounted display != display)

### GitHub Sources
- [immersive-web/webxr#390](https://github.com/immersive-web/webxr/issues/390) — "Consider hooking up sound source nodes in the API somehow" (30 comments — spatial audio latency)
- [immersive-web/webxr#815](https://github.com/immersive-web/webxr/issues/815) — "Spec language precludes non-visual uses" (41 comments)
- [libretro/RetroArch#16373](https://github.com/libretro/RetroArch/issues/16373) — Rolling Scanline Simulation (99 comments)
- [playcanvas/engine](https://github.com/playcanvas/engine) — Active WebXR & Gaussian Splatting development (16.8k ⭐)

### Potential Guests
- **jeromeetienne** — Creator of AR.js (15.8k ⭐), pioneer of Web AR at 60fps
- **Martin Valigursky** — Active PlayCanvas engine contributor (WebXR rendering pipeline)
- **cwilso** — WebXR spec contributor, authored spatial audio integration issues

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics & the audio presence paradox
**Key Debate:** Why is the WebXR spec still visual-only for spatial audio?

### Topics
- Head-Related Transfer Functions (HRTFs): how your ears shape what you hear
- Ambisonics vs. binaural: which paradigm wins for presence?
- The **audio presence paradox**: perfect spatial audio can feel *less* real than imperfect audio because the brain detects the artifact
- WebXR's systemic neglect of spatial audio — Issue #390 (30 comments, still open after 6 years)
- Audio-only devices and accessibility: Issue #892 — is WebXR ignoring a whole class of user?
- University of Utah's Audio Mentoring Project and open HRTF datasets
- Dynamic HRTF personalization vs. generic kernels

### GitHub Sources
- [immersive-web/webxr#390](https://github.com/immersive-web/webxr/issues/390) — "Consider hooking up sound source nodes in the API somehow" (30 comments, open since 2018)
- [immersive-web/webxr#892](https://github.com/immersive-web/webxr/issues/892) — "Evaluate how/if WebXR should interact with audio-only devices" (a11y-tracker label)
- [immersive-web/webxr#815](https://github.com/immersive-web/webxr/issues/815) — "Spec language precludes non-visual uses" (41 comments)
- [playcanvas/engine](https://github.com/playcanvas/engine) — 3D positional sounds built on Web Audio API

### Potential Guests
- **cwilso** — WebXR spec editor, authored the spatial audio integration issue
- **toji** — WebXR accessibility advocate, authored Issue #892
- **ddorwin** — Co-authored Issue #815 on non-visual perception in WebXR spec

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift & wayfinding
**Key Debate:** Is the WebXR spec blind to non-visual perception?

### Topics
- Hologram drift: why virtual objects in MR slowly "slide" and how registration error erodes trust
- Hand tracking fidelity: from 21-jointed skeletal hands to fine diaphragmatic gesture
- Wayfinding in mixed reality: cognitive maps,地标 (landmarks), and the 3D navigation UX problem
- The WebXR spec's visual bias: Issue #815 (41 comments) — spec language that excludes non-visual modalities
- MR interface design patterns: platelets, menus-at-arm's-length, and the"air tap" standardization problem
- Eye tracking as the next input layer: foveated rendering + intent detection
- The "cognitive load" crisis: when every surface is a UI, what do you look at?

### GitHub Sources
- [immersive-web/webxr#815](https://github.com/immersive-web/webxr/issues/815) — "Spec language precludes non-visual uses" (41 comments)
- [AR-js-org/AR.js#288](https://github.com/AR-js-org/AR.js/issues/288) — Markerless location-based AR, more realistic placement (11 comments)
- [AR-js-org/AR.js#681](https://github.com/AR-js-org/AR.js/issues/681) — AR.js-next: ECS architecture & roadmap (kalwalt)
- [playcanvas/engine](https://github.com/playcanvas/engine) — Built-in WebXR support, Gaussian Splatting for MR
- [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) — MRTK hand tracking & wayfinding systems (6.1k ⭐)

### Potential Guests
- **jeromeetienne** — AR.js creator, pioneer of markerless & image-tracked AR on the web
- **nickw1** — AR.js maintainer, authored markerless placement issue #288
- **kalwalt** — AR.js-next (ECS architecture) proposal author
- **ddorwin** — WebXR spec co editor, accessibility & non-visual perception advocate

---

## Cross-Episode Themes

| Theme | Episodes | GitHub Anchor |
|---|---|---|
| **The 20ms rule** | Ep 1, Ep 3 | WebXR #390, RetroArch #16373 |
| **Non-visual perception** | Ep 2, Ep 3 | WebXR #815, #892 |
| **Presence vs. fidelity** | Ep 1, Ep 2 | Foveated rendering, HRTF personalization |
| **Open-source as the battleground** | All | AR.js, PlayCanvas, WebXR spec repos |
| **Accessibility as a design driver** | Ep 2, Ep 3 | WebXR #892 (audio-only devices) |

---

## Production Notes

- **Recording format:** Interview + live GitHub issue walkthrough
- **Segment structure:** 20 min research deep-dive → 15 min guest interview → 10 min "Debate Arena" (hosted discussion of the week's hottest issue)
- **GitHub integration:** Each episode links to 3–5 real open issues; listeners can join the discussion
- **Editorial cadence:** Bi-weekly release, with "mid-week briefs" on breaking issues

---

## Guest Outreach Tracker

| Guest | Episode | Status | Notes |
|---|---|---|---|
| jeromeetienne | Ep 1, Ep 3 | ☐ Not contacted | AR.js creator, 15.8k ⭐ |
| Martin Valigursky | Ep 1 | ☐ Not contacted | PlayCanvas lead contributor |
| cwilso | Ep 1, Ep 2 | ☐ Not contacted | WebXR spec editor |
| toji | Ep 2 | ☐ Not contacted | WebXR a11y advocate |
| ddorwin | Ep 2, Ep 3 | ☐ Not contacted | WebXR co-editor, non-visual perception |
| nickw1 | Ep 3 | ☐ Not contacted | AR.js maintainer |
| kalwalt | Ep 3 | ☐ Not contacted | AR.js-next architect |

*Last updated: September 2026 — GitHub-research backed*