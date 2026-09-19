# 🔬 Research Source Index

> Indexed repository of all GitHub sources referenced in 'The Future of Human Perception' podcast research.

---

## Primary Repositories

### 1. AR.js (AR-js-org/AR.js)
- **Stars:** 15,791 | **License:** MIT | **Language:** HTML/JS
- **Focus:** Web-based AR with marker and location-based tracking
- **Key maintainers:** @jeromeetienne (creator), @nicolocarpignoli (maintainer), @kalwalt (AR.js-next lead)
- **URL:** https://github.com/AR-js-org/AR.js

### 2. MixedRealityToolkit-Unity (microsoft/MixedRealityToolkit-Unity)
- **Stars:** 6,076 | **License:** MIT | **Language:** C#
- **Focus:** Cross-platform MR app development in Unity
- **Key contributors:** @david-c-kline (spatial audio), @fiban-havok (WebRTC), @danielescudero
- **URL:** https://github.com/microsoft/MixedRealityToolkit-Unity
- **Status:** ⚠️ Legacy v2 — MRTK3 has moved to MixedRealityToolkit org

### 3. Google Lullaby (google/lullaby)
- **Stars:** 1,197 | **License:** Apache-2.0 | **Language:** C++
- **Focus:** VR/AR C++ libraries — spatial audio, rendering, UI
- **Internal Google usage:** VR Home, Play Store, YouTube, Play Movies, Earth
- **URL:** https://github.com/google/lullaby

### 4. MixedReality-WebRTC (microsoft/MixedReality-WebRTC)
- **Stars:** 944 | **License:** MIT | **Language:** C#/C++
- **Focus:** Real-time audio/video/data for MR apps
- **Key contributors:** @fiban-havok, @jehumb-havok, @stkenned-havok
- **URL:** https://github.com/microsoft/MixedReality-WebRTC
- **Status:** ⚠️ Deprecated — no longer receiving commits

### 5. MindAR.js (hiukim/mind-ar-js)
- **Stars:** 2,733 | **License:** MIT | **Language:** JS
- **Focus:** Web AR with image and face tracking via TensorFlow.js
- **URL:** https://github.com/hiukim/mind-ar-js

### 6. jeelizFaceFilter (jeeliz/jeelizFaceFilter)
- **Stars:** 2,938 | **License:** MIT | **Language:** JS
- **Focus:** Lightweight WebGL face detection/tracking/AR filters
- **URL:** https://github.com/jeeliz/jeelizFaceFilter

### 7. AR.js v3 / MRTK-Unity (MixedRealityToolkit/MixedRealityToolkit-Unity)
- **Stars:** 550 | **License:** MIT | **Language:** C#
- **Focus:** Third-gen MRTK for Unity (community-owned)
- **URL:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity

### 8. XR Development for Beginners (microsoft/xr-development-for-beginners)
- **Stars:** 564 | **License:** MIT | **Language:** Vue
- **Focus:** Spatial computing curriculum for cloud advocacy
- **URL:** https://github.com/microsoft/xr-development-for-beginners

---

## Key GitHub Issues Mapped to Podcast Themes

### Perceptual Latency
| Issue | Repo | Description |
|---|---|---|
| [#639](https://github.com/AR-js-org/AR.js/issues/639) | AR.js | 3D object moving/disappearing randomly — location-based AR drift |
| [#680](https://github.com/AR-js-org/AR.js/issues/680) | AR.js | Tracking distance worsens at higher resolution — resolution/latency tradeoff |
| [#11848](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11848) | MRTK | MicStream never set to True — audio pipeline timing |
| [#11845](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11845) | MRTK | Holographic remoting crash with Chinese keywords — multimodal perception gap |

### Spatial Audio
| Issue | Repo | Description |
|---|---|---|
| [#11271](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/11271) | MRTK | Audio spatializer configuration script and update (part 1) |
| [#2775](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/2775) | MRTK | Port audio influencers and effects from HTK — conv reverb for spatial fidelity |
| [#7730](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7730) | MRTK | Auto-detect appropriate audio spatializer — user intent vs system default |
| [#92](https://github.com/microsoft/MixedReality-WebRTC/issues/92) | MR-WebRTC | WebRTC audio track → Unity AudioSource bridge for spatial rendering |
| [#99](https://github.com/microsoft/MixedReality-WebRTC/pull/99) | MR-WebRTC | Remote audio feature — multitrack spatial audio for MR collab |

### Mixed Reality Interfaces
| Issue | Repo | Description |
|---|---|---|
| [#1884](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/1884) | MRTK | SpectatorView integration — third-person vs first-person MR perception |
| [#35](https://github.com/microsoft/MixedReality-WebRTC/issues/35) | MR-WebRTC | Custom local video source (RenderTexture) — MR compositing pipelines |
| [#11844](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11844) | MRTK | MRC documentation gap — MR capture UX is undocumented |
| [#621](https://github.com/AR-js-org/AR.js/issues/621) | AR.js | Browser reloads with large glTF — perceptual continuity broken |
| [#221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) | MRC | Holograms sticking — anchor stability in mixed reality |

---

## Community Members Identified

| Person | GitHub Handle | Area of Expertise | Relevance |
|---|---|---|---|
| Jerome Etienne | @jeromeetienne | Web AR (AR.js creator) | ⭐⭐⭐ — Creator of the leading Web AR library; deep WebXR performance expertise |
| Nicolò Carpignoli | @nicolocarpignoli | Web AR maintainer | ⭐⭐⭐ — Maintains AR.js org, performance optimization focus |
| kalwalt | @kalwalt | Web AR architecture | ⭐⭐⭐ — Lead of AR.js-next ECS rewrite for AR.js v3 |
| David C. Kline | @david-c-kline | Spatial audio (MRTK) | ⭐⭐⭐ — PR author on MRTK spatial audio system (#11271, #2775, #7730) |
| Fabian Hildebrand | @fiban-havok | MR WebRTC/audio | ⭐⭐⭐ — Key MR-WebRTC contributor, spatial audio pipeline |
| ActiveNick | @ActiveNick | Mixed Reality UX | ⭐⭐ — MR community leader (100+ followers) |
| Miya | @miykael | Computer vision / AR | ⭐⭐ — Research-level CV/AR work (200+ followers) |
| Armando Genis | @armando-genis | Computer vision / AR | ⭐⭐ — AR researcher with spatial interests |

---

## Hot Debate Topics (from GitHub issue analysis)

1. **Perceptual Latency** — Can foveated rendering hide latency? Is 20ms a hard threshold or a myth?
2. **Spatial Audio Presence** — Why don't spatial audio algorithms create true "outside-the-head" presence?
3. **Hologram Drift** — Is sub-centimeter anchor drift (AR.js #639) a UX deal-breaker for MR collaboration?
4. **Hand Tracking vs Controllers** — Proprioceptive conflict: does hand tracking feel more "real" or more "wrong"?
5. **WebXR Spec Gaps** — Is the WebXR spec blind to non-visual perceptual modalities?
6. **Resolution vs Latency** — Can AR.js track at higher resolutions without perceptible lag (#680)?
7. **Audio Spatializer Auto-Configuration** — Should the system choose your spatializer, or should the user (#7730)?

---

## Repository Cross-Reference Matrix

| Research Area | AR.js | MRTK-Unity | Lullaby | MR-WebRTC |
|---|---|---|---|---|
| Tracking & Latency | ★★★ | ★★ | ★ | — |
| Spatial Audio | — | ★★★ | ★★★ | ★★ |
| Interaction Design | ★★ | ★★★ | ★ | ★ |
| Performance/Rendering | ★★★ | ★★ | ★★★ | — |
| Multimodal Fusion | — | ★★ | — | ★★★ |

---

## Last Updated

September 2026 — Generated from GitHub API search and repository analysis.