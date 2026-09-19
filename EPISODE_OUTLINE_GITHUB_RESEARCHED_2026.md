# 🎙️ The Future of Human Perception — Episode Outline (GitHub-Researched, 2026)

> **Generated from live audit of active AR/MR/Spatial Computing GitHub repositories and issue debates.**
> Research sources: `immersive-web/webxr`, `mrdoob/three.js`, `hiukim/mind-ar-js`, `jeeliz/jeelizFaceFilter`, `De-Panther/unity-webxr-export`, `immersive-web/webxr-samples`

---

## Episode 1 — "The Latency Frontier: Motion-to-Photon & the Perceptual Cliff"

**Core Question:** Can the human brain forgive latency if we trick it with prediction, foveation, and frame timing?

| Field | Detail |
|---|---|
| **Runtime** | ~45 min |
| **Key Topics** | Motion-to-photon latency, the 20ms perceptual rule, foveated rendering, reprojection/ASW, phase-sync frame timing, OffscreenCanvas workers, framebuffer scaling, dynamic frame rate |
| **GitHub Debate Anchors** | [webxr#1203](https://github.com/immersive-web/webxr/issues/1203) — "Provide statistics to help guide performance" (open, 12 comments) · [webxr#1233](https://github.com/immersive-web/webxr/issues/1233) — "Allow dynamic frame timing" (resolved, phase-sync) · [webxr#368](https://github.com/immersive-web/webxr/issues/368) — "Encouraging apps to avoid mid-frame flushes" · [webxr#1102](https://github.com/immersive-web/webxr/issues/1102) — "OffscreenCanvas in a Worker support" (open, 13 👍) |
| **Potential Guests** | **toji** (WebXR spec lead, W3C Immersive Web WG) · **cabanier** (WebXR spec contributor, performance & frame timing) · **mrdoob** (three.js creator, PositionalAudio & 3D rendering pioneer) · **ranbuch** (OffscreenCanvas/WebXR worker work) |
| **Guest Outreach Status** | 🔬 Researched — outreach not yet attempted |

### Episode 1 — Segment Outline

1. **Cold Open:** The 20ms rule — why does VR queasiness spike past 20ms motion-to-photon?
2. **Segment A — The Science of Latency Perception:** How the brain constructs time; the vestibulo-ocular reflex; why 20ms is the cliff, not a guideline
3. **Segment B — Engineering Solutions:** Reprojection (ASW/Space Warp), foveated rendering, phase sync, dynamic frame timing — what the WebXR spec says and what it still misses
4. **Segment C — The Open Debate:** webxr#1203 — should the spec expose performance statistics to developers? Should we have a "compute pressure" API for XR?
5. **Closing:** What's the next perceptual frontier beyond latency?

---

## Episode 2 — "Spatial Sound and the Third Dimension: HRTF, Presence & the WebXR Blind Spot"

**Core Question:** Why does the WebXR spec still treat spatial audio as an afterthought when it's half of the presence equation?

| Field | Detail |
|---|---|
| **Runtime** | ~40 min |
| **Key Topics** | HRTF (Head-Related Transfer Function), Web Audio PannerNode, PositionalAudio, spatial presence paradox, ambisonics, audio-vision alignment, multi-speaker setups, head pose synchronization |
| **GitHub Debate Anchors** | [webxr#390](https://github.com/immersive-web/webxr/issues/390) — "Consider hooking up sound source nodes in the API somehow" (open, 30 comments, 1 👍) — the single most-discussed open audio issue in the WebXR repo |
| **Potential Guests** | **cwilso** (WebXR spec contributor, authored #390 on spatial audio) · **mrdoob** (THREE.PositionalAudio pioneer) · **toji** (WebXR spec lead) |
| **Guest Outreach Status** | 🔬 Researched — outreach not yet attempted |

### Episode 2 — Segment Outline

1. **Cold Open:** Close your eyes. A sound moves behind you. Now open your eyes. Is the virtual object where you heard it? The spatial presence paradox.
2. **Segment A — How HRTF Works:** Pinna filtering, interaural time differences, the personalized HRTF problem, why generic HRTFs feel "off"
3. **Segment B — The WebXR Gap:** webxr#390 — why can't developers easily position sound sources in the virtual space? The PannerNode bridge and its limitations.
4. **Segment C — The Presence Equation:** Vision dominates, but audition anchors confidence. When audio lags or misaligns, presence collapses. What's the perceptual cost?
5. **Closing:** Can WebXR ever truly support spatial audio, or do we need a new API layer?

---

## Episode 3 — "Interfaces Beyond the Flat Screen: MR Pass-Through, Hologram Drift & Wayfinding"

**Core Question:** When the screen is the world, how do you design an interface that doesn't fight human perception?

| Field | Detail |
|---|---|
| **Runtime** | ~45 min |
| **Key Topics** | MR pass-through/passthrough API, opaque vs. see-through device distinction, hologram drift, world locking, wayfinding in mixed reality, spatial mapping, depth sensing, multi-sensory interfaces (haptic) |
| **GitHub Debate Anchors** | [webxr#145](https://github.com/immersive-web/webxr/issues/145) — "Should we distinguish between opaque and see-through devices?" (24 comments) · [webxr#254](https://github.com/immersive-web/webxr/issues/254) — "AR extensions and modifications" (26 comments) · [webxr#894](https://github.com/immersive-web/webxr/issues/894) — "Projection matrices differ between WebGL and WebGPU" (open) · [webxr#1228](https://github.com/immersive-web/webxr/issues/1228) — "Communicate earlier that the UA doesn't need a depth texture" |
| **Potential Guests** | **dmarcos** (AR extensions/spec contributor) · **ssylvan** (opaque vs. transparent device distinction, #145) · **magcius** (WebGL vs. WebGPU projection matrices, #894) · **cabanier** (tracked sources PR #1361) · **hiukim** (mind-ar-js creator, Web AR tracking) · **NehaXR** (AR/MR researcher) |
| **Guest Outreach Status** | 🔬 Researched — outreach not yet attempted |

### Episode 3 — Segment Outline

1. **Cold Open:** You're in a kitchen. A hologram recipe floats above the counter. But every time you move your head, the text drifts. Why does hologram drift break presence more than latency?
2. **Segment A — The Pass-Through Problem:** webxr#145 — should the spec distinguish opaque (VR头显) from see-through (MR眼镜) devices? What does the current spec say, and what's missing?
3. **Segment B — World Locking & Hologram Drift:** Why do virtual objects "wander"? Spatial mapping, depth sensing (webxr#1228), and the fight between tracking accuracy and rendering latency.
4. **Segment C — Beyond Vision:** Haptics, spatial audio, and multi-sensory MR interfaces. Can you "feel" a hologram? What does the research say?
5. **Closing:** The MR interface challenge is fundamentally a perception challenge — and we're barely starting.

---

## Research Addendum: Key GitHub Repositories Surveyed

| Repo | Stars | Relevance |
|---|---|---|
| [immersive-web/webxr](https://github.com/immersive-web/webxr) | 3,152 | WebXR Device API spec — the core standard for web AR/VR |
| [mrdoob/three.js](https://github.com/mrdoob/three.js) | 115,636 | Dominant 3D library; foundation of WebXR rendering & PositionalAudio |
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | 2,733 | Web AR with image/face tracking via TensorFlow.js |
| [jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) | 2,938 | WebGL face tracking AR filters |
| [De-Panther/unity-webxr-export](https://github.com/De-Panther/unity-webxr-export) | 1,257 | Unity WebGL → WebXR export pipeline |
| [immersive-web/webxr-samples](https://github.com/immersive-web/webxr-samples) | 1,160 | WebXR reference implementations |

## Research Addendum: Key Contributors Identified

| GitHub User | Role | Expertise | Relevant Issues |
|---|---|---|---|
| **toji** | WebXR spec lead | Spec architecture, VR/AR modes | #394, #222, #368, #185 |
| **cabanier** | WebXR spec contributor | Performance, frame timing, dynamic timing | #1203, #1233, #1228, #1361 |
| **cwilso** | WebXR spec contributor | Spatial audio, HRTF integration | #390 |
| **ranbuch** | WebXR contributor | OffscreenCanvas, worker rendering | #1102 |
| **mrdoob** | three.js creator | 3D rendering, PositionalAudio | (foundational code) |
| **dmarcos** | AR spec contributor | AR extensions, passthrough | #254 |
| **ssylvan** | WebXR contributor | Transparent/opaque device distinction | #145 |
| **magcius** | WebXR contributor | Projection matrix, WebGL/WebGPU | #894 |
| **hiukim** | mind-ar-js creator | Web AR tracking, TensorFlow.js AR | (mind-ar-js repo) |
| **NehaXR** | AR/MR researcher | Mixed reality perception | (user profile) |

---

*This outline was auto-generated from a GitHub Issues audit sorted byReactions across the immersive-web/webxr, mrdoob/three.js, and related AR/MR repositories. All issue links are live.*
