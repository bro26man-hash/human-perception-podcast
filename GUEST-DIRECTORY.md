# 👤 Guest Directory — The Future of Human Perception

> Compiled from GitHub issue analysis, repository contributors, and community discussion threads.
> Last updated: September 2026

---

## Tier 1 — Pioneers & Maintainers

### Jérôme Étienne — `@jeromeetienne`
- **Role:** Creator of AR.js (now 5.9k ⭐)
- **Background:** French developer and AR pioneer. Created AR.js as a lightweight Web AR library that brought marker tracking, image tracking, and location-based AR to the browser.
- **Why he's a guest:** He's the person who made Web AR possible. His decision to transfer maintenance to the AR.js org and his thoughts on where Web AR should go next are essential history.
- **Key threads:** AR.js README, issue #217 (markerless debate — his original vision of `tracking: best`)
- **Topics:** The birth of Web AR, why markerless was never built, what he'd do differently

### Nicolò Carpignoli — `@nicolocarpignoli`
- **Role:** AR.js Former Maintainer (after Jerome Etienne)
- **Background:** Took over AR.js maintenance, drove the Three.js build, NFT image tracking, and architectural decisions.
- **Why he's a guest:** He's the most knowledgeable person about AR.js's internal architecture AND the philosophical debates about markerless AR, cross-platform strategy, and WebXR's future.
- **Key threads:** [Issue #217 comment thread](https://github.com/AR-js-org/AR.js/issues/217#issuecomment-849888943) — his comprehensive answer about the state of markerless Web AR; [Issue #498](https://github.com/AR-js-org/AR.js/issues/498) — camera feed stretching debugging
- **Topics:** "We are in between where there is no OSS markerless cross-browser Web AR" — the gap that may last "another couple of years"

### hiukim — `@hiukim`
- **Role:** Creator of MindAR (2.7k ⭐)
- **Background:** Built MindAR as a TensorFlow.js-based Web AR library with image tracking and face tracking. Last commit: January 2024 (v1.2.5).
- **Why he's a guest:** MindAR is the spiritual successor to AR.js, but the community is questioning whether it's abandonware. His perspective on why development slowed and what the future holds is crucial.
- **Key threads:** [Issue #526](https://github.com/hiukim/mind-ar-js/issues/526) — "Is this repo abandonware?" (13 comments, 3 👀 reactions)
- **Topics:** Why MindAR's tracking models haven't been updated, the relationship between AR.js and MindAR, what he's working on next

### Yongsen Mao — `manycore-research`
- **Role:** Lead Researcher, SpatialLM (NeurIPS 2025, 4.7k ⭐)
- **Background:** Led the SpatialLM project — a 3D large language model that processes point cloud data to generate structured 3D scene understanding (walls, doors, windows, objects). Accepted at NeurIPS 2025.
- **Why he's a guest:** SpatialLM represents a completely new paradigm: using LLMs for spatial perception. This could be the bridge between geometric tracking and semantic world understanding that AR.js has been missing.
- **Key threads:** [SpatialLM Paper](https://arxiv.org/abs/2506.07491), [SpatialLM Dataset on HuggingFace](https://huggingface.co/datasets/manycore-research/SpatialLM-Dataset)
- **Topics:** Can 3D LLMs replace traditional SLAM? How close are we to machines that truly "understand" space?

---

## Tier 2 — Active Developers & Community Builders

### kalwalt — `@kalwalt`
- **Role:** AR.js Current Maintainer
- **Background:** Active maintainer of AR.js, assigned to multiple critical issues (#46, #40, #515).
- **Why he's a guest:** He holds the keys to AR.js's future. His perspective on whether to integrate ARCore/WebXR directly, and how to handle the markerless gap, is decision-making.
- **Key threads:** [Issue #498](https://github.com/AR-js-org/AR.js/issues/498) — confirmed the stretched camera feed bug, implemented fix on `stretched-video-fix` branch
- **Topics:** Maintenance burden, release strategy, the ARCore integration question

### nickw1 — `@nickw1`
- **Role:** AR.js Location-Based AR Contributor
- **Background:** Deep contributor to AR.js's location-based AR features. Also created [arjs-peakfinder](https://github.com/nickw1/arjs-peakfinder), a POI (point-of-interest) AR browser.
- **Why he's a guest:** He's the person who understands GPS-based AR better than anyone. He's spent years debugging the exact problems listeners experience.
- **Key threads:** [Issue #278](https://github.com/AR-js-org/AR.js/issues/278) — "Content sticking to camera" (40 comments, he's the reporter); [Issue #466](https://github.com/AR-js-org/AR.js/issues/466) — iOS heading correction; [Issue #302](https://github.com/AR-js-org/AR.js/issues/302) — Reimplementation of device orientation code; [Issue #547](https://github.com/AR-js-org/AR.js/issues/547) — GPS floating on Android
- **Topics:** Why location-based AR drifts, the iOS vs Android perception gap, combining AR.js with AlvaAR (SLAM library)

### dogzilla — `@dogzilla`
- **Role:** Web AR Community Member, MindAR Fork Maintainer
- **Background:** Extremely active in both MindAR and AR.js issue threads. Continues to hack on MindAR despite its perceived abandonment. Led the community effort to discuss forking.
- **Why he's a guest:** He represents the voice of the for-the-people Web AR community — the developers who are stuck with imperfect tools and are choosing to fix them themselves.
- **Key threads:** [Issue #526](https://github.com/hiukim/mind-ar-js/issues/526) — started the "abandonware?" debate, organized community meetup discussion; [Issue #556](https://github.com/hiukim/mind-ar-js/issues/556) — tracking stability debugging; [Issue #498](https://github.com/AR-js-org/AR.js/issues/498) — compared MindAR vs AR.js camera behavior
- **Topics:** "We just forked it and started hacking on it" — the open-source fork trend, commercial vs free AR pricing, SLAM integration ambitions

### CoderSilas — `@CoderSilas`
- **Role:** Web AR Developer, Alternative Framework Explorer
- **Background:** Testing and reviewing alternative Web AR frameworks. Found encantar.js as a replacement for MindAR/AR.js. Active in community discussion threads.
- **Why he's a guest:** He's the canary in the coal mine — a developer actively looking for what comes AFTER MindAR and AR.js, and finding that it doesn't exist.
- **Key threads:** [Issue #526](https://github.com/hiukim/mind-ar-js/issues/526) — recommended encantar.js, noted "AR.js is definitively dead if you dig around a bit"
- **Topics:** The gap in the Web AR ecosystem, what a maintained successor would need, Google/Mozilla's responsibility

### param-fsd — `@param-fsd`
- **Role:** MindAR Tracking Stability Researcher
- **Background:** Developer struggling with MindAR's jitter issues. Applied custom smoothing approaches and documented the gap between open source and commercial tracking quality.
- **Why he's a guest:** He's the person doing the actual experimental work on tracking stabilization — the engineering that would make or break an open-source AR future.
- **Key threads:** [Issue #556](https://github.com/hiukim/mind-ar-js/issues/556) — "Unstable AR Content and Ineffective Tracking Configurations" — documented that 8thWall and MyWebAR apply smoothing that MindAR doesn't
- **Topics:** Custom smoothing algorithms, hybrid tracking approaches, the $750/month question

### kylebakerio — `@kylebakerio`
- **Role:** WebXR/ARCore Integration Advocate
- **Background:** WebXR developer who wants AR.js to integrate ARCore/ARKit as the default with fallbacks. Built 3Dof AR proof of concept and multiplayer WebXR VR apps.
- **Why he's a guest:** He represents the pragmatic position: ARCore/ARKit are the reality today, and pretending they don't exist doesn't help anyone.
- **Key threads:** [Issue #217](https://github.com/AR-js-org/AR.js/issues/217) — argued for markerless AR with ARCore/ARKit support
- **Topics:** "AR.js is going to lose relevance if an open source library supports that tech and AR.js doesn't"

---

## Tier 3 — Spatial Audio & Research

### google/spatial-media Maintainers
- **Role:** Specifications and tools for 360° video and spatial audio
- **Background:** Google team maintaining the spatial audio RFC, spherical video RFC, and VR180 format specifications.
- **Why they're a guest:** They hold the keys to the spatial audio metadata standard — but there's no WebXR integration. The gap between "documented" and "implemented" is the episode.
- **Key threads:** [Spatial Audio RFC](https://github.com/google/spatial-media/blob/main/docs/spatial-audio-rfc.md)
- **Topics:** Why spatial audio isn't in WebXR, what would it take to bridge the spec gap

### facebook/immersive-web-sdk Team
- **Role:** WebXR Framework (357 ⭐, TypeScript)
- **Background:** Meta team building a complete WebXR framework with spatial audio, locomotion, interactions, and scene understanding. Has spatial audio as a first-class system.
- **Why they're a guest:** They've BUILT what the WebXR spec doesn't have — and their experience shows what's possible when you stop waiting for the spec.
- **Key threads:** [Immersive Web SDK](https://github.com/facebook/immersive-web-sdk), [iwsdk.dev](https://iwsdk.dev/)
- **Topics:** "Same code, two experiences" — how SDK-level innovation can outpace spec-level stagnation

---

## 📊 Guest Selection Matrix

| Episode | Primary Guests | Secondary Guests | Debate Positions |
|---|---|---|---|
| **Ep 1: Latency** | hiukim, Nicolò Carpignoli | kalwalt, dogzilla, param-fsd | Open source vs commercial / 20ms rule / Fork or wait |
| **Ep 2: Spatial Audio** | google/spatial-media team | facebook/immersive-web-sdk team, Yongsen Mao | Spec vs SDK / HRTF personalization / 3D LLM bridge |
| **Ep 3: Interfaces** | jeromeetienne, kylebakerio | nickw1, Yongsen Mao | Markerless gap / Cross-platform reality / 3D world model |

---

*This directory was compiled from GitHub issue analysis, repository contributor lists, and community discussion thread mining. All descriptions are based on actual contributions and public statements.*
