# 🎙️ The Future of Human Perception — Episode Outline

> Collaborative production document for the podcast series exploring the engineering and human science behind how technology reshapes perception.

---

## Episode 1: Latency and the Perceptual Threshold

**Focus:** Motion-to-photon latency, the 20ms rule, and whether foveation tricks the brain into forgiving lag.

### Core Questions
- What is the perceptual threshold for visual latency? Why is ~20ms the magic number?
- How do modern AR stacks (AR.js, MindAR, SceneView) handle — and fail at — sub-frame tracking?
- Can foveated rendering genuinely reduce perceived latency, or is it a placebo?
- What does HoloLens 2's hand/eye tracking pipeline teach us about multi-modal latency cancellation?

### GitHub Debate Sources
| Debate | Repo | Issue | Key Insight |
|---|---|---|---|
| Unstable AR content & tracking configs | hiukim/mind-ar-js | [#556](https://github.com/hiukim/mind-ar-js/issues/556) | Users report jitter and drift when tracking configurations are suboptimal — the perceptual cost of unstable anchors |
| Phone orientation breaks detection | hiukim/mind-ar-js | [#428](https://github.com/hiukim/mind-ar-js/issues/428) | Switching orientation degrades marker detection — sensor fusion latency exposed |
| EIS re-registers placed models | sceneview/sceneview | [#2728](https://github.com/sceneview/sceneview/issues/2728) | Image stabilization visibly shifts AR content — a real-world example of perceptual misregistration |
| Location-based AR broken | jeromeetienne/AR.js | [#825](https://github.com/jeromeetienne/AR.js/issues/825) | Geospatial AR fails in practice — GPS + IMU fusion latency at the perceptual boundary |
| Device orientation on iOS | jeromeetienne/AR.js | [#818](https://github.com/jeromeetienne/AR.js/issues/818) | Safari's sensor API limitations create latency ceiling for web AR |
| H.264 encoder blockiness | microsoft/MixedReality-WebRTC | [#153](https://github.com/microsoft/MixedReality-WebRTC/issues/153) | Hardware video encoding latency creates perceptual breakup in MR compositing |
| Acoustic echo cancellation failure | microsoft/MixedReality-WebRTC | [#157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | Audio latency and echo break the illusion of presence in collaborative MR |

### Potential Guests
- **Jerome Etienne** (`jeromeetienne`) — Creator of AR.js; pioneer of web-based marker tracking and location AR
- **Hui Kim** (`hiukim`) — Creator of MindAR.js; built image/face tracking for the mobile web
- **Thomas Gorisse** (`ThomasGorisse`) — Creator of SceneView; solving cross-platform 3D/AR rendering at scale

### Key Reading
- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- MRTK v2 documentation: [Performance and Optimization](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/experimental/feature-performance)
- SceneView AR recording & replay: [AR Debug with Rerun.io](https://github.com/sceneview/sceneview/blob/main/docs/docs/ar-recording.md)

---

## Episode 2: Spatial Sound and the Third Dimension

**Focus:** HRTFs, ambisonics, spatial audio presence, and why the WebXR spec is still visual-only for spatial audio.

### Core Questions
- How do Head-Related Transfer Functions (HRTFs) create the illusion of 3D audio space?
- Why is the WebXR spec silent on spatial audio rendering?
- What can Google Lullary's spatial audio engine teach us about ambisonics for VR/AR?
- How does the absence of spatial audio in current AR SDKs break the perceptual illusion?

### GitHub Debate Sources
| Debate | Repo | Issue | Key Insight |
|---|---|---|---|
| WebRTC projection matrix for spatial audio | microsoft/MixedReality-WebRTC | [#83](https://github.com/microsoft/MixedReality-WebRTC/issues/83) | Transform/projection of spatial audio frames is an open enhancement — MR audio positioning is unsolved |
| Spatialized audio AR for blind users | SeitaKayukawa/Blind_Accessibility_Papers | [#184](https://github.com/SeitaKayukawa/Blind_Accessibility_Papers/issues/184) | "What's around Me?" — spatialized audio AR as an accessibility tool, proving the perceptual power of 3D sound |
| Audio-tactile drawings with spatial AR | SeitaKayukawa/Blind_Accessibility_Papers | [#509](https://github.com/SeitaKayukawa/Blind_Accessibility_Papers/issues/509) | Combining spatial audio with tactile feedback for multi-modal perception |
| Lullaby's spatial audio engine | google/lullaby | [README](https://github.com/google/lullaby) | Google's internal VR audio framework — used by VR Home, Play Store, YouTube, Earth — never fully open-sourced |
| MixedReality-WebRTC AEC failure | microsoft/MixedReality-WebRTC | [#157](https://github.com/microsoft/MixedReality-WebRTC/issues/157) | Acoustic echo cancellation not working — without it, collaborative MR audio is unusable |

### Potential Guests
- **Andra Connect** (`AndraConnect`) — Spatial audio researcher and 3D audio developer
- **Jerome Etienne** (`jeromeetienne`) — AR.js creator; has explored location-based and spatial audio AR
- **Prof. Edgar Choueiri** — Princeton professor, 3D audio/audio spatialization researcher (external referral)

### Key Reading
- [WebXR Stage Stereo spec](https://immersive-web.github.io/webxr-stage-stereo/) (visual-only — the gap)
- [Google Lullaby GitHub](https://github.com/google/lullaby) — spatial audio source
- [6DoF Audio in WebXR — W3C Workshop Paper](https://www.w3.org/2021/12/16-audio-in-xr-eval/)

---

## Episode 3: Interfaces Beyond the Flat Screen

**Focus:** MR interfaces, hologram drift, wayfinding, and whether the WebXR spec is blind to non-visual perception.

### Core Questions
- What are the perceptual challenges of MR interfaces that coexist with the real world?
- How does "hologram drift" (pose accumulation error over time) break the illusion of persistence?
- Are current MR UI paradigms (gaze + gesture + voice) the right ones — or are they visual-centric?
- What role does spatial audio, haptics, and proprioception play in next-gen MR interfaces?
- Google's Sceneform was archived — what does SceneView's rise tell us about the future of MR interfaces?

### GitHub Debate Sources
| Debate | Repo | Issue | Key Insight |
|---|---|---|---|
| AR wall-placement like Amazon AR View | sceneview/sceneview | [#2740](https://github.com/sceneview/sceneview/issues/2740) | Floor↔wall edge alignment + contextual shadows — the perceptual craft of MR placement |
| "Point & Ask" — Gemini Nano in AR | sceneview/sceneview | [#2648](https://github.com/sceneview/sceneview/issues/2648) | On-device LLM explains what the AR camera sees, anchored in world space — a new MR interface paradigm |
| iOS parity epic for AR features | sceneview/sceneview | [#894](https://github.com/sceneview/sceneview/issues/894) | 52 demo apps, only 21 implemented — the platform gap in MR interface parity |
| Sceneform archived, no replacement | sceneview/sceneview | [README](https://github.com/sceneview/sceneview) | Google archived Sceneform in 2021; no first-party declarative AR renderer remains |
| Cloud anchors & persistent MR | sceneview/sceneview | [`CloudAnchorNode`](https://github.com/sceneview/sceneview/blob/main/sceneview/src/main/java/io/github/sceneview/ar/node/CloudAnchorNode.kt) | Cross-device persistent anchors — the foundation of shared MR experiences |
| Hand tracking & holographic remoting | microsoft/MixedRealityToolkit-Unity | [#11845](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11845) | MRTK3 keyword recognition crashes with holographic remoting — gesture interfaces still fragile |
| Eye tracking target selection | microsoft/MixedRealityToolkit-Unity | [Eye Tracking docs](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/eye-tracking) | Gaze + hand + voice = tri-modal interaction — but is it enough for spatial computing? |
| Geospatial urban mesh | sceneview/sceneview | [`StreetscapeGeometryNode`](https://github.com/sceneview/sceneview/blob/main/sceneview/src/main/java/io/github/sceneview/ar/node/StreetscapeGeometryNode.kt) | Semantic city mesh for AR — perceptual wayfinding at urban scale |

### Potential Guests
- **Thomas Gorisse** (`ThomasGorisse`) — SceneView creator; solving the Sceneform vacuum with a cross-platform composable-native AR SDK
- **Jerome Etienne** (`jeromeetienne`) — AR.js pioneer; from marker-based to geospatial AR on the web
- **Microsoft MRTK team** (via HoloDevelopers Slack) — The architects of HoloLens 2's interaction paradigm
- **Prof. Hiroshi Ishii** — MIT Media Lab, Tangible Media Group; brass tacks research on physical-digital interfaces (external referral)

### Key Reading
- [Mixed Reality Toolkit Architecture](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/architecture/overview)
- [WebXR Immersive Session spec](https://immersive-web.github.io/webxr/)
- [SceneView vs Sceneform: the void Google left behind](https://github.com/sceneview/sceneview/blob/main/README.md)
- [Azure Spatial Anchors — cross-platform persistence](https://docs.microsoft.com/azure/spatial-anchors/)

---

## GitHub Research Addendum

> Live audit of the most active AR/MR/Spatial Computing repositories and their open debates as of September 2026.

### Repository Registry

| Repository | Stars | Language | Focus | Activity |
|---|---|---|---|---|
| [jeromeetienne/AR.js](https://github.com/AR-js-org/AR.js) | 15,791 | HTML/JS | Web AR (marker + location) | Moved to AR-js-org org; active |
| [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | 6,076 | C# | MRTK v2 for Unity | Legacy — MRTK v3 at MixedRealityToolkit org |
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | 2,731 | JS | Web AR image/face tracking | Active issue tracker |
| [jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) | 2,938 | JS | WebGL face tracking AR | Maintenance mode |
| [viromedia/viro](https://github.com/viromedia/viro) | 2,400 | JS | AR/VR via React Native | Active |
| [sceneview/sceneview](https://github.com/sceneview/sceneview) | 1,321 | Kotlin/Swift | Cross-platform 3D/AR SDK | Very active (Sept 2026 commits) |
| [google/lullaby](https://github.com/google/lullaby) | 1,197 | C++ | VR/AR C++ framework | WIP, not fully open |
| [microsoft/MixedReality-WebRTC](https://github.com/microsoft/MixedReality-WebRTC) | 944 | C# | MR audio/video comms | Maintenance mode |
| [kzampog/cilantro](https://github.com/kzampog/cilantro) | 1,137 | C++ | Point cloud processing | Active |

### Top Open Debate Themes

1. **Perceptual Latency & Tracking Stability** — The #1 pain point across all AR SDKs. From MindAR's orientation tracking failures to SceneView's EIS re-registration bug, the gap between technical tracking and perceptual stability is where the podcast lives.

2. **Spatial Audio Absence in WebXR** — The WebXR spec defines visual rendering but has no spatial audio rendering API. Google Lullaby's closed-source spatial audio engine and the WebRTC AEC failures highlight that MR audio is the most under-explored perceptual dimension.

3. **MR Interface Paradigms** — The shift from "gaze + gesture" to voice-first, LLM-anchored, multi-modal interfaces. SceneView's "Point & Ask" issue (#2648) is a perfect case study: an on-device Gemini Nano explaining the AR camera's view, anchored in world space.

4. **Platform Fragmentation** — SceneView's iOS parity epic (#894: 52 demos, 21 implemented) and AR.js's iOS orientation bugs reveal that cross-platform AR is still a perceptual promise, not a delivery.

5. **Gaussian Splatting & Neural Rendering** — SceneView's SplatNode (#2646) signals that neural rendering is entering the AR mainstream. The perceptual implications of real-time neural radiance fields for AR are wide open.

### Key Contributors to Follow

| Contributor | Repos | Expertise |
|---|---|---|
| `jeromeetienne` | AR.js, ghosthistoric assets | Web AR, marker/location tracking, geospatial AR |
| `hiukim` | MindAR.js | TensorFlow.js, image/face tracking, sensor fusion |
| `ThomasGorisse` | SceneView | Cross-platform 3D/AR, Filament, RealityKit, Kotlin Multiplatform |
| `AndraConnect` | Spatial audio research | HRTF, ambisonics, 3D audio rendering |
| `nicholocarpignoli` | AR.js (co-maintainer) | Web AR community building |

---

*Last updated: September 2026 with GitHub research audit across 9 repositories.*
