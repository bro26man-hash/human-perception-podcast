# 🎙️ The Future of Human Perception

Collaborative production hub for **The Future of Human Perception** podcast series — managing episodes, guest research, and discussion around AR, spatial computing, and perceptual science.

## What Is This?

This repo is the production hub for a podcast series exploring the engineering and human science behind how technology reshapes perception. We track the **hottest open debates** in the most active AR/MR/Spatial Computing GitHub repositories and surface the researchers and developers pushing those debates forward.

## 🔬 Research Backbone

Our research is sourced from live GitHub analysis. See the full audit below:

| Document | Scope |
|---|---|
| [`RESEARCH-SOURCE-INDEX.md`](./RESEARCH-SOURCE-INDEX.md) | Complete index of all surveyed repos, key issues, community members, and debate topics |
[`EPISODE-OUTLINE-RESEARCH-BACKED.md`](./EPISODE-OUTLINE-RESEARCH-BACKED.md) `EPISODE-OUTLINE-RESEARCH-BACKED.md` | Full episode outlines with GitHub-sourced debates, guests, and segment drafts |

### Top Repositories Surveyed

| Repo | Stars | Domain | Key Podcast Relevance |
|---|---|---|---|
| [AR-js-org/AR.js](https://github.com/AR-js-org/AR.js) | 15.8k ⭐ | Web AR | Tracking latency, perceptual continuity (#639, #680, #621) |
| [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | 6.1k ⭐ | Mixed Reality | Spatial audio (#11271, #2775, #7730), MR capture UX (#11844) |
| [microsoft/MixedReality-WebRTC](https://github.com/microsoft/MixedReality-WebRTC) | 944 ⭐ | MR Audio/Video | Audio pipeline, multitrack spatial audio (#92, #99) |
| [google/lullaby](https://github.com/google/lullaby) | 1.2k ⭐ | VR/AR C++ | Spatial audio engine, perceptual rendering |
| [MixedRealityToolkit/MixedRealityToolkit-Unity](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity) | 550 ⭐ | MRTK v3 | Current-gen MR UX, hand tracking, eye tracking |

## The Three Pilot Episodes

| # | Issue | Title | Focus | Key Debate |
|---|---|---|---|---|
| 1 | [**#142**](https://github.com/bro26man-hash/human-perception-podcast/issues/142) | **Latency and the Perceptual Threshold** | Motion-to-photon latency & the 20ms rule | Can foveation trick the brain into forgiving lag? |
| 2 | [**#143**](https://github.com/bro26man-hash/human-perception-podcast/issues/143) | **Spatial Sound and the Third Dimension** | HRTFs, ambisonics & the audio presence paradox | Why is the WebXR spec still visual-only for spatial audio? |
| 3 | [**#144**](https://github.com/bro26man-hash/human-perception-podcast/issues/144) | **Interfaces Beyond the Flat Screen** | MR interfaces, hologram drift & wayfinding | Is the WebXR spec blind to non-visual perception? |

### Potential Guest Bench

| Name | Handle | Expertise | Episodes |
|---|---|---|---|
| **Jerome Etienne** | @jeromeetienne | Web AR (AR.js creator) | Ep. 1 |
| **Nicolò Carpignoli** | @nicolocarpignoli | Web AR maintainer | Ep. 1 |
| **kalwalt** | @kalwalt | AR.js-next ECS architect | Ep. 1, 3 |
| **David C. Kline** | @david-c-kline | MRTK spatial audio lead | Ep. 2 |
| **Fabian Hildebrand** | @fiban-havok | MR-WebRTC audio pipeline | Ep. 2 |
| **ActiveNick** | @ActiveNick | Mixed Reality UX advocacy | Ep. 2, 3 |
| **Miya** | @miykael | Computer vision / AR research | Ep. 3 |

### Hot Debate Topics (GitHub-Sourced)

1. **Perceptual Latency** — Can foveated rendering hide latency? Is 20ms a hard threshold or a myth?
2. **Spatial Audio Presence** — Why don't spatial audio algorithms create true "outside-the-head" presence?
3. **Hologram Drift** — Is sub-centimeter anchor drift (AR.js #639) a UX deal-breaker?
4. **Hand Tracking vs Controllers** — Proprioceptive conflict in MR interaction
5. **WebXR Spec Gaps** — Is the WebXR spec blind to non-visual perceptual modalities?
6. **Resolution vs Latency** — Can AR.js track at higher resolutions without perceptible lag?
7. **Audio Spatializer Auto-Configuration** — Should the system choose your spatializer, or should the user?

## Repository Structure

| File | Purpose |
|---|---|
| `EPISODE-OUTLINE-RESEARCH-BACKED.md` | Full episode outlines with GitHub-sourced debates, guests, and segment drafts |
| `RESEARCH-SOURCE-INDEX.md` | Complete index of all surveyed repos, issues, and community members |
| `episodes/` | Episode drafts, show notes, and recording materials |
| **Issues #142–144** | Individual episode pipelines with research backlog and guest outreach tracking |

## How to Contribute

1. **Pick an episode issue** ([#142](https://github.com/bro26man-hash/human-perception-podcast/issues/142), [#143](https://github.com/bro26man-hash/human-perception-podcast/issues/143), or [#144](https://github.com/bro26man-hash/human-perception-podcast/issues/144))
2. Add research findings, GitHub issue links, or potential guest suggestions as comments on the issue
3. Submit a PR with updated episode outlines or new research
4. Tag potential guests and track outreach status
5. Every open issue is a potential episode segment — join the discussion!

## Bonus Episode Pipeline (Pre-Research)

| # | Title | Trigger |
|---|---|---|
| 4 | "The Body in the Loop: Haptics and Proprioception" | MRTK Hand Physics Service experimental features |
| 5 | "Eye Tracking: The Invisible Interface" | MRTK eye tracking: target selection, navigation, heat maps |
| 6 | "From 60fps to 120: The Next Latency Arms Race" | Apple Vision Pro, Quest 3, and the refresh-rate arms race |
| 7 | "WebXR's Perceptual Blind Spots" | immersive-web/webxr spec gaps (visual-first design) |
| 8 | "Spatial Anchors and the Geography of Memory" | Azure Spatial Anchors, persistent mixed reality |

## Links & Resources

- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [Immersive Web Working Group](https://www.w3.org/immersive-web/)
- [Mixed Reality Toolkit](https://aka.ms/mrtkdocs)
- [AR.js (new org)](https://github.com/AR-js-org/AR.js)
- [Google Lullaby](https://github.com/google/lullaby)
- [Mixed Reality WebRTC](https://github.com/microsoft/MixedReality-WebRTC)
