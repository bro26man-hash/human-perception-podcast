# 🎙️ The Future of Human Perception — Canonical Episode Outline

> Collaborative production document for the podcast series exploring AR, spatial computing, perceptual latency, mixed reality interfaces, and spatial audio.

---

## How to Use This Outline

- **Each episode** has its own dedicated GitHub Issue with pinned research links, debate topics, and contributor suggestions.
- **Guest outreach** is tracked in `GUEST_DIRECTORY.md`.
- **Live GitHub issue audits** are maintained in `GITHUB-RESEARCH-ADDENDUM.md`.
- Contributions (research, links, guest ideas) go in through PRs or issue comments.

---

## Episode 1: **Latency and the Perceptual Threshold**

**Core Question:** Can foveation and reprojection trick the brain into forgiving lag — or is the 20 ms motion-to-photon rule a hard physiological limit?

| Topic | Detail | GitHub Evidence |
|---|---|---|
| Motion-to-photon latency | The 20 ms threshold for VR comfort vs. what's achievable on mobile AR | MRTK-Unity #88 (Vision Pro pass-through latency), godotengine/godot PR #106221 (pacing/latency) |
| Foveated rendering | Rendering at full resolution only where the eye is looking — psychological trade-offs | Lullaby spatial audio + rendering pipeline, OpenXR foveation specs |
| Reprojection & timewarp | Techniques to hide latency by warping the last frame — do they cause perceptual artifacts? | OVR (Oculus) reprojection docs, SteamVR reprojection discussion |
| Perceptual inconsistency | Color/clipping bugs that break presence — w3c/csswg-drafts #9449 (219 comments!) | CSS Color 4 perceptive uniformity debate |
| WebAR 60fps target | AR.js 60fps on mobile — how close is the perceptual threshold? | jeromeetienne/AR.js (15.8k ⭐), hiukim/mind-ar-js (2.7k ⭐) |

**Potential Guests:**
- **Jerome Etienne** (@jeromeetienne) — Creator of AR.js, pioneer of Web AR
- **Nicolò Carpignoli** (@nicolocarpignoli) — AR.js maintainer
- **wbeert** — MRTK maintainer, spatial interaction architect
- **Seb Lague** (@SebLague) — Unity VR/AR educator & developer
- **keijiro** — Unity graphics programmer, Boids/Perception GT project
- **David Kline** (@david-c-kline) — MRTK audio lead

**Key Debate to Chair:** *Is the 20ms rule a hard limit or a soft guideline that context-aware rendering can bend?*

---

## Episode 2: **Spatial Sound and the Third Dimension**

**Core Question:** Why is spatial audio the forgotten dimension in XR — and can HRTF personalization finally solve the "presence paradox"?

| Topic | Detail | GitHub Evidence |
|---|---|---|
| HRTF personalization | Generic HRTFs vs. personalized scans — does it matter for presence? | Hubs-Foundation/hubs #1853 (30 comments, Epic bug on audio spatialization) |
| Ambisonics & WebXR | WebXR spec is visual-only for spatial audio — what's the roadmap? | MRTK-Unity #663 (docs for spatializer plugins), #181 (Spatializer mixer integration) |
| Steam Audio & physics-based acoustics | Real-time acoustic simulation in VR — too heavy for headset? | ValveSoftware/steam-audio #362 (spatializer bug, 13 comments) |
| Binaural rendering on the Web | Can WebAudio + HRTF compete with dedicated spatializers? | mumble-voip/mumble #6597 (positional audio, 22 comments) |
| The "Presence Paradox" | Perfect visuals + wrong audio = no presence. Why is audio treated as an afterthought? | Lullaby README (spatial audio as core feature), Moonlight spatial audio PRs |

**Potential Guests:**
- **Haroon Qureshi** — Lead contributor, Google Lullaby (spatial audio + ECS architecture)
- **Krzmbrzl** — Mumble positional audio maintainer
- **denis-sm** — Steam Audio developer
- **elliot Paris** — Spatial audio researcher & developer
- **Cuong M. Le** — Ambisonics & 3D audio engineer
- **david-c-kline** (@david-c-kline) — MRTK audio lead, Microsoft

**Key Debate to Chair:** *Is the WebXR spec's silence on spatial audio a bug or a deliberate design choice — and who should own it?*

---

## Episode 3: **Interfaces Beyond the Flat Screen**

**Core Question:** Are current MR interfaces just shrunken desktop paradigms — or can hologram drift, gaze interaction, and spatial UI finally liberate us from the 2D prison?

| Topic | Detail | GitHub Evidence |
|---|---|---|
| Vision Pro / Apple spatial UI | MRTK Vision Pro support (#88, 28 comments) — is Apple's spatial UI philosophy compatible with open standards? | MRTK-Unity #88, IvanCampos/visionOS-examples (405 ⭐) |
| Hand tracking & gesture UX | Direct hand manipulation vs. controller — which feels more "real"? | MRTK-Unity #113 (MetaXR hand tracking bug), #82 (trigger sensitivity) |
| Hologram drift & calibration | Why do virtual objects "slide" when you move your head — and can perception.modeling fix it? | MRTK-Unity #553 (OpenXR reinit visual bug), Lullaby entity tracking |
| Spatial wayfinding & anchors | Persistent spatial anchors — how does the brain build a cognitive map in MR? | MRTK spatial manipulation package, Azure Spatial Anchors |
| The "Flat Screen Prison" | Are we just making a 2D monitor that floats in space, or is a truly spatial UI emerging? | MRTK-Unity #261 (mobile AR support), design labs experiments |

**Potential Guests:**
- **wbeert** (@whebertML) — MRTK spatial interaction & object manipulation lead
- **AMollis** — MRTK UX architect, doubtfully的设计研究
- **shaynie** — MRTK contributor, audio & spatializer docs
- **Ivan Campose** — visionOS developer & spatial computing educator
- **Fabio Z.?** — RealityMixer author, iOS MR
- **keijiro** — Unity graphics, Boids perception project

**Key Debate to Chair:** *Is "spatial UI" just a buzzword for repositioning 2D panels — or is a genuinely new interaction paradigm emerging from XR research?*

---

## Research Backbone: Most Active AR/MR/Spatial Computing Repos

| Repo | Stars | Focus | Link |
|---|---|---|---|
| jeromeetienne/AR.js | 15,891 | Web AR (60fps mobile) | [github.com/AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) |
| microsoft/MixedRealityToolkit-Unity | 6,076 | Legacy MRTK v2 | [github.com/microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) |
| MixedRealityToolkit/MixedRealityToolkit-Unity | 550 | MRTK3 (OpenXR, Unity) | [github.com/MixedRealityToolkit/MixedRealityToolkit-Unity](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity) |
| google/lullaby | 1,197 | VR/AR C++ ECS engine | [github.com/google/lullaby](https://github.com/google/lullaby) |
| microsoft/MixedReality-WebRTC | 944 | MR audio/video comms | [github.com/microsoft/MixedReality-WebRTC](https://github.com/microsoft/MixedReality-WebRTC) |
| jeeliz/jeelizFaceFilter | 2,938 | WebGL AR face filters | [github.com/jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) |
| hiukim/mind-ar-js | 2,731 | Web AR (TensorFlow) | [github.com/hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) |
| IvanCampos/visionOS-examples | 405 | Apple Vision Pro spatial computing | [github.com/IvanCampos/visionOS-examples](https://github.com/IvanCampos/visionOS-examples) |

---

## Hottest Open Debates (GitHub-Issue Sourced)

1. **Perceptual Latency** — Motion-to-photon vs. foveation vs. reprojection (MRTK, godot, OVR docs)
2. **Spatial Audio Neglect** — WebXR visual-only spec, HRTF personalization, presence paradox (Hubs #1853, Mumble #6597, Steam Audio #362)
3. **MR Interface Paradigm** — Vision Pro support, hand tracking UX, hologram drift (MRTK #88, #113, #82)
4. **Color Perceptual Uniformity** — CSS Color 4 clipping issues (w3c/csswg-drafts #9449, 219 comments)
5. **Mobile AR Performance** — 60fps threshold on AR.js, MRTK3 mobile AR support (#261)

---

*Last updated: 2026-09-16 | Research sources: GitHub Issues, PRs, and repository audits across AR/MR/Spatial Computing communities.*
