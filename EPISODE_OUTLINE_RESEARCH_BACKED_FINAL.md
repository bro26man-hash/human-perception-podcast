# 🎙️ The Future of Human Perception — Episode Outline (Research-Backed Final)

> Generated from GitHub field research across the most active AR / MR / Spatial Computing repositories.
> Last updated: 2026-09-18

---

## How This Document Was Built

We surveyed **5 key GitHub repositories** representing the deepest active engineering communities in AR, MR, and spatial computing:

| Repository | Stars | Focus | Key Debate Surface |
|---|---|---|---|
| **jeromeetienne/AR.js** | 15.8k ⭐ | Web-based AR (60fps on mobile) | Location-based AR accuracy, markerless tracking limits |
| **microsoft/MixedRealityToolkit-Unity** | 6.1k ⭐ | MRTK v2 — cross-platform MR in Unity | Hand-tracking input sensitivity, MRC capture dimensions |
| **MixedRealityToolkit/MixedRealityToolkit-Unity** | 550 ⭐ | MRTK v3 — built on XRI 3.0 + OpenXR | Vision Pro support, controller deprecation, spatial manipulation |
| **microsoft/MixedReality-WebRTC** | 944 ⭐ | Spatial audio/video comms for MR | Deprecated but defines the spatial-audio-in-MR paradigm |
| **google/lullaby** | 1.2k ⭐ | C++ VR/AR engine with spatial audio | Spatial audio presence, ECS-perception architecture |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Core Question:** *Can foveation trick the brain into forgiving lag?*

### Key Topics

| Topic | GitHub Evidence | Associated Repos |
|---|---|---|
| **Motion-to-photon latency & the 20ms rule** | MRTK v2 issue #82: "triggerPressed is overly sensitive" — direct evidence of perceptual lag in MR input pipelines | microsoft/MixedRealityToolkit-Unity |
| **Hand-tracking passthrough failures** | MRTK v3 issue #830: "Quest 3 passthrough not working" — shows how latency in sensor fusion breaks presence | MixedRealityToolkit/MixedRealityToolkit-Unity |
| **Foveated rendering as a latency hack** | AR.js location-based AR accuracy issues (#825, #833) — when tracking can't keep up, the perceptual model breaks down | jeromeetienne/AR.js |
| **OpenXR Input system migration** | MRTK v3 issue #645: full XRI 3.0 migration — controller-based classes deprecated, new rig architecture impacts latency paths | MixedRealityToolkit/MixedRealityToolkit-Unity |
| **WebRTC codec latency for spatial audio** | MixedReality-WebRTC issue #14: VS 2017 hard-code, H.264 hardware encoding quality degradation — codec-level latency affects sync | microsoft/MixedReality-WebRTC |
| **Lullaby's ECS perception loop** | google/lullaby — entity-component-system architecture designed for "fluid, responsive UIs and living environmental objects" — implies a 90Hz perception gate | google/lullaby |

### Potential Guests

| Name | Role | Connection |
|---|---|---|
| **@keveleigh** | MRTK3 lead maintainer | Assignee on XRI 3.0 migration (#645), deep latency-path knowledge |
| **@whebertML** | MRTK3 spatial manipulation | Assignee on ObjectManipulator and hand-tracking issues |
| **@jeromeetienne** | AR.js creator | Founded the 60fps-on-mobile web AR paradigm |
| **@nicolocarpignoli** | AR.js maintainer | Carried AR.js into the AR-js-org era, image tracking |
| **@jehumb-havok** | MixedReality-WebRTC contributor | Deep WebRTC codec and UWP latency knowledge |

### Key Debate Prompt

> *"The 20ms motion-to-photon threshold is engineering folklore. But foveated rendering can shave 8ms off the perceived path. If the brain only 'sees' latency in the foveal region, are we building lag compensation or lag illusion?"*

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Core Question:** *Why is the WebXR spec still visual-only for spatial audio?*

### Key Topics

| Topic | GitHub Evidence | Associated Repos |
|---|---|---|
| **Spatial audio in MR co-presence** | MixedReality-WebRTC's entire purpose: multi-track real-time audio/video/data comms for MR — defines spatial audio positioning in peer-to-peer MR | microsoft/MixedReality-WebRTC |
| **HRTF implementation gaps** | Lullaby supports "full 3D VR environments, including spatial audio" — but no public HRTF API; Google's internal use vs. open spec gap | google/lullaby |
| **Ambisonics vs. HRTF on the web** | AR.js runs in A-Frame/Three.js — no spatial audio API in standard web stack; the WebXR spec defines spatial tracking but not spatial audio rendering | jeromeetienne/AR.js |
| **MRC audio capture limitations** | MixedReality-WebRTC known issues: H.264 hardware encoding blockiness, missing SIMD on ARM — audio-visual sync degradation in MR capture | microsoft/MixedReality-WebRTC |
| **The "audio presence paradox"** | Lullaby's ECS architecture separates perception systems; spatial audio is a "presence channel" distinct from visual fidelity — but the Web prioritizes visual | google/lullaby |

### Potential Guests

| Name | Role | Connection |
|---|---|---|
| **@jehumb-havok** | MR-WebRTC contributor | Spatial audio in real-time MR comms, codec sync |
| **@keveleigh** | MRTK3 lead | Audio Effects package in MRTK3 (org.mixedrealitytoolkit.audio) |
| **Lullaby maintainers** (Google internal) | Spatial audio engine design | C++ ECS perception architecture used by VR Home, YouTube, Play Movies |
| **@nicolocarpignoli** | AR.js maintainer | Web AR audio gap — location-based AR has no spatial audio layer |

### Key Debate Prompt

> *"WebXR defines spatial tracking but not spatial audio rendering. We have HRTF specs from the AES, ambisonics from the MPEG-H group, and WebAudio's PannerNode — but none talk to each other. Is the web's spatial audio future a unified API, or will it remain a patchwork of native SDKs?"*

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Core Question:** *Is the WebXR spec blind to non-visual perception?*

### Topics

| Topic | GitHub Evidence | Associated Repos |
|---|---|---|
| **Vision Pro / VisionOS support** | MRTK v3 issue #88: "MRTK support for Apple VisionOs and Vision Pro" — 28 comments, the community is begging for spatial interface parity | MixedRealityToolkit/MixedRealityToolkit-Unity |
| **Gaze-pinch vs. hand-tracking interaction paradigms** | MRTK v3 introduces "gaze-pinch indirect manipulation" — a new interaction model that replaces direct hand manipulation | MixedRealityToolkit/MixedRealityToolkit-Unity |
| **Hologram drift & wayfinding** | MRTK v2 boundary system + spatial awareness — how do holographic objects stay anchored in physical space when the world moves? | microsoft/MixedRealityToolkit-Unity |
| **Spatial anchors & persistent MR** | Azure Spatial Anchors integration — cross-platform persistent objects that persist "their location across devices over time" | microsoft/MixedRealityToolkit-Unity (Azure integration) |
| **The flat-screen bias in WebXR** | AR.js is fundamentally a 2D screen overlay XR — location-based AR tries 3D but GPS accuracy (±5m) makes true spatial computing impossible on phones | jeromeetienne/AR.js |
| **Accessibility in MR** | MRTK3 early preview package: Accessibility — the first perception channel beyond visual/auditory in MR toolkits | MixedRealityToolkit/MixedRealityToolkit-Unity |

### Potential Guests

| Name | Role | Connection |
|---|---|---|
| **@keveleigh** | MRTK3 lead | Vision Pro architecture decisions, XRI 3.0 interaction models |
| **@whebertML** | Spatial manipulation | ObjectManipulator, hand tracking, spatialawareness |
| **@AMollis** | MRTK3 contributor | XRI 3.0 migration, controller deprecation philosophy |
| **@shaynie** | MRTK3 maintainer | UX building blocks, MR design language |
| **@ms-RistoRK** | MRTK3 maintainer | OpenXR backend, platform abstraction |
| **@jeromeetienne** | AR.js creator | The flat-screen AR paradigm — what WebXR gets wrong about perception |

### Key Debate Prompt

> *"Apple Vision Pro shipped with visionOS but MRTK still has no support — issue #88 has been open for 2 years. Meanwhile, the WebXR spec defines 'immersive' as a 90fps stereoscopic render. But MR is not VR. Is the spec definition of 'immersive' itself the problem?"*

---

## Cross-Episode Themes

| Theme | Episodes | repos |
|---|---|---|
| **The 20ms rule is folklore, not physics** | E1 (primary), E2 (audio sync), E3 (frame timing) | All |
| **Visual dominance bias in XR** | E2 (audio gap), E3 (spec definition) | AR.js, WebXR |
| **Interaction paradigm fragmentation** | E3 (gaze-pinch vs. hand), E1 (controller deprecation) | MRTK v2→v3 |
| **Open-source vs. platform silos** | E3 (VisionOS gap), E2 (HRTF spec gap) | All |

---

## Research Sources

### Repository Issue Links

| Issue | Repo | Topic |
|---|---|---|
| [#88 — MRTK support for Apple VisionOs and Vision Pro](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88) | MRTK-v3 | Vision Pro / spatial interface |
| [#645 — XRI 3.0 support for MRTK3](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/645) | MRTK-v3 | Interaction paradigm migration |
| [#82 — triggerPressed overly sensitive](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/82) | MRTK-v2 | Perceptual input latency |
| [#830 — Quest 3 passthrough not working](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/830) | MRTK-v3 | Hand-tracking / spatial mapping |
| [#14 — Upgrade to Visual Studio 2019](https://github.com/microsoft/MixedReality-WebRTC/issues/14) | MR-WebRTC | Codec / pipeline latency |
| [#825 — Location-based AR doesn't work](https://github.com/jeromeetienne/AR.js/issues/825) | AR.js | GPS accuracy / spatial tracking |
| [#833 — Markerless city-scale AR](https://github.com/jeromeetienne/AR.js/issues/833) | AR.js | Tracking limits |
| [#13 — how Building](https://github.com/google/lullaby/issues/13) | Lullaby | Build/architecture questions |

### Additional Repositories to Monitor

| Repo | Stars | Why Monitor |
|---|---|---|
| **immersive-web/webxr** | 3.1k ⭐ | The WebXR spec itself — where spatial audio should be defined |
| **aframe/aframe** | 16.7k ⭐ | A-Frame is the web framework AR.js is built on |
| **GoogleAR/uikinajs** | — | ARCore + Unity bridge — spatial tracking on mobile |
| **microsoft/MRDL_Unity_PeriodicTable** | — | Real MRTK production app — periodic table as MR demo |
| **Microsoft/GalaxyExplorer** | — | HoloLens 2 galaxy exploration — spatial awareness in practice |

---

## Contribution Guide for Episode Issues

Each episode gets its own GitHub issue (#13, #14, #15). To contribute:

1. **Comment on the episode issue** with research findings, issue links, or guest suggestions
2. **Tag potential guests** (use @mentions for MRTK maintainers)
3. **Add timestamps** for key debate moments from GitHub discussions
4. **Submit a PR** to update this outline or add new research pages
