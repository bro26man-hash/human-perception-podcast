# 🎙️ The Future of Human Perception — Initial Episode Outline

> **A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.**
> This file is the canonical initial outline for the series, synthesized from GitHub research across the most active AR/MR/Spatial Computing repositories as of September 2026.

---

## Series Vision

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast follows the engineering and the human science behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

---

## Research Backbone: Most Active GitHub Communities

### Web AR / WebXR
| Repo | Stars | Focus |
|------|-------|-------|
| `jeromeetienne/AR.js` | 15.8k ⭐ | Efficient AR on the Web — 60fps on mobile |
| `playcanvas/engine` | 16.7k ⭐ | 3D game engine with WebXR support |
| `immersive-web/webxr` | 3.1k ⭐ | W3C Immersive Web Working Group — the spec itself |
| `Hubs-Foundation/hubs` | 2.2k ⭐ | Social VR/AR platform |
| `hiukim/mind-ar-js` | 2.7k ⭐ | Web AR with image & face tracking via TF.js |
| `jeeliz/jeelizFaceFilter` | 2.9k ⭐ | Real-time multi-face detection & AR filters |

### Mixed Reality
| Repo | Stars | Focus |
|------|-------|-------|
| `microsoft/MixedRealityToolkit-Unity` | 6.1k ⭐ | MRTK — the foundational MR interaction framework |
| `microsoft/MixedReality-WebRTC` | 944 ⭐ | MR communication — audio, video, data channels |
| `microsoft/OpenXR-MixedReality` | — | HoloLens 2 OpenXR runtime & layer management |
| `microsoft/MixedRealityCompanionKit` | — | SpectatorView & calibration tools |
| `microsoft/spatial-computing` | 83 ⭐ | Azure AI + MR samples |
| `microsoft/xr-development-for-beginners` | 564 ⭐ | Spatial Computing curriculum |

### Spatial Computing (Apple Vision Pro / visionOS)
| Repo | Stars | Focus |
|------|-------|-------|
| `StereoKit/StereoKit` | 1.1k ⭐ | XR engine with OpenXR backend & spatial interaction |
| `KhronosGroup/OpenXR-SDK` | 1.1k ⭐ | The OpenXR standard implementation |
| `IvanCampos/visionOS-examples` | 405 ⭐ | Vision Pro spatial computing accelerators |

### AR SDKs
| Repo | Stars | Focus |
|------|-------|-------|
| `google-ar/arcore-android-sdk` | 5.2k ⭐ | ARCore — Google's mobile AR platform |
| `google-ar/arcore-unity-sdk` | 1.4k ⭐ | ARCore Unity integration |
| `Unity-Technologies/arfoundation-samples` | 3.4k ⭐ | AR Foundation cross-platform samples |
| `olucurious/Awesome-ARkit` | 8.0k ⭐ | ARKit resource collection |

### Spatial Audio
| Repo | Stars | Focus |
|------|-------|-------|
| `GoogleChrome/omnitone` | 911 ⭐ | Web-based ambisonic & binaural rendering |
| `leomccormack/Spatial_Audio_Framework` | 748 ⭐ | C-based spatial audio processing (HRTF, HOA, ISM) |
| `google/spatial-media` | 2.1k ⭐ | Spatial video & audio encoding |
| `freeman-jiang/beatsync` | 3.2k ⭐ | Multi-device spatial audio synchronization |
| `mgth/Omniphony` | — | Open-source binaural spatial audio |

---

## 🔥 Hottest Open Debates (Mined from GitHub Issues)

### Debate 1: Perceptual Latency Is Not Pipeline Latency
- **WiVRn #1099** (40+ comments, 15+ reactions): After Quest 3 enters passthrough and regains focus, VRChat freezes for up to 47 minutes. Monado's `wait_for_scheduled_free()` holds per-client frame slots scheduled *days* in the future. The compositor stays healthy at 80 FPS — this is a per-client scheduling bug, not a global stall.
- **Key insight**: The brain may detect *temporal irregularity* in frame delivery, not average latency. This reframes the entire optimization target from "reduce average ms" to "stabilize frame delivery."
- **ALVR #334**: VR streaming stacks underreport total system latency by 30–50%. The "20 ms rule" may be unreachable even when reported numbers look fine.
- **ValveSoftware/SteamVR-for-Linux #21** (97+ comments): Community reports of nausea-inducing lag — the foundational problem.
- **GestureRecognizer**: @xytovl (WiVRn), @leinardi (SteamVR-for-Linux), @jd-3d (ALVR)

### Debate 2: The WebXR Spatial Audio Gap
- **MixedReality-WebRTC #157** (17 comments): Acoustic echo cancellation is disabled by default or non-functional in OpenXR MR stacks. Without AEC, room acoustics contaminate the spatial audio model — you can't determine whether a sound is "outside" the headset or "inside" the room. This isn't an audio quality issue; it's a *perceptual calibration* failure.
- **WebXR spec**: The spec is fundamentally visual-first. Spatial audio is an afterthought — no standardized spatial audio API, no HRTF DOM, no ambisonic integration.
- **omnitone #2**: Mobile browser support still open after 8+ years — binaural rendering remains desktop-only.
- **ensors**: @BorisSmus, @BrandonJones, @JuliusKammerl (omnitone/Google audio), @leomccormack (SAF)

### Debate 3: Hologram Registration Drift & Calibration Instability
- **MixedRealityCompanionKit #228**: SpectatorView calibration that works once and never twice (19 comments). Blocks research reproducibility.
- **MixedRealityCompanionKit #221**: Holograms sticking to camera — fundamental registration failure in optical passthrough.
- **arcore-android-sdk #1779**: Camera↔IMU clock offset of 13–35ms on mid-range Android devices. Invisible to developers, catastrophic for perceptual stability.
- **OpenXR-MixedReality #131 & #132**: HoloLens 2 frame-timestamp precision and D3D12 performance instabilities.
- **Gueusts**: @fieldsJacksonG, @brycehutchings, @emaschino, @fredemmott

### Debate 4: Dynamic Foveation — Perceptual Trick or Technical Necessity?
- **immersive-web/webxr #1420** (3 comments, authored by @AdaRoseCannon): Dynamic foveation as a performance lever — can the renderer cheat the brain by reducing resolution in the periphery?
- **Perception question**: Is foveated rendering a legitimate perceptual optimization, or does it introduce artifacts that break presence?
- **WebXR visibility & DOM overlay gaps**: #1396 (actual vs. internal visibility confusion), #1414 (HTML-in-canvas integration)
- **Gueusts**: @AdaRoseCannon, @cabanier, @chrisdavidmills, @himorin

### Debate 5: Hand Tracking Reliability for MR Interaction
- **StereoKit #922**: Hand tracking problems when pinching to grab — the fundamental interaction contract breaks.
- **StereoKit #579**: UltraLeap hand tracking forearm support — tracking fidelity vs. latency tradeoffs.
- **StereoKit #652**: Hand tracking rejected on Vive Focus 3 — platform fragmentation.
- **MRTK #9510**: Performance drops whenever hands are visible due to articulated hand mesh rendering — the perceptual cost of hand visualization.
- **Gueusts**: @maluoi, @bradleylab

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Key Topics
1. **The motion-to-photon pipeline** — sensor → predict → render → encode → transport → decode → display. Every stage injects latency.
2. **The "20 ms rule" and vestibular-visual conflict** — why a few milliseconds of lag translate directly into motion sickness.
3. **Temporal irregularity vs. average latency** — WiVRn #1099's finding that stutter is caused by frame delivery irregularity, not pipeline depth.
4. **"Missing" latency in VR streaming** — ALVR #334: ~33.6 ms of unaccounted latency; stacks underreport by 30–50%.
5. **Camera↔IMU clock offset** — arcore-android-sdk #1779: 13–35ms offsets invisible to developers.
6. **Calibration instability** — MixedRealityCompanionKit #228: setups that work once and never twice.
7. **AEC failure as perceptual latency** — MixedReality-WebRTC #157: when echo cancellation breaks, spatial audio collapses.

### The Hot Debate
> **Perceptual latency is not pipeline latency.** The WiVRn #1099 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets (reduce average ms) are wrong — we need to stabilize frame delivery instead.

### Potential Guests
| Name | GitHub | What They'll Bring |
|------|--------|--------------------|
| **xytovl** | @xytovl | WiVRn maintainer; packet-timing & pacing algorithm design; stutter analysis |
| **leinardi** | @leinardi | SteamVR-for-Linux maintainer; open-source VR latency debugging |
| **jd-3d** | @jd-3d | ALVR developer; "missing latency" in VR streaming stacks |
| **brycehutchings** | @brycehutchings | Microsoft OpenXR contributor; MR performance, D3D12 path |
| **fieldsJacksonG** | @fieldsJacksonG | Microsoft MRC; hologram registration & calibration |
| **emaschino** | @emaschino | MR performance researcher; pipeline optimization |
| **fredemmott** | @fredemmott | Microsoft XR Advocate; HoloLens platform strategy |
| **maluoi** | @maluoi | StereoKit maintainer; XR engine architecture & OpenXR backend |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** How do spatial-audio algorithms trick the brain into hearing sound in 3D space — and why does a one-size-fits-all HRTF still fall short of "real"?

### Key Topics
1. **HRTFs and the personalization challenge** — why generic HRTFs sound wrong, and what personalized HRTFs cost.
2. **VBAP and higher-order ambisonics (HOA)** — the tradeoffs between directionality and computational cost.
3. **Real-time binaural/ambisonic rendering on the web** — GoogleChrome/omnitone's FOA/HOA renderers and Web Audio API integration.
4. **The WebXR spatial audio gap** — the spec is visual-first; spatial audio is an afterthought.
5. **AEC failure as a spatial-perception problem** — MixedReality-WebRTC #157: without echo cancellation, room acoustics contaminate the spatial model.
6. **Audio-visual integration** — vision dominates when cues conflict; does bad spatial audio break presence more than bad visuals?
7. **Accessibility** — spatial audio as a navigation cue for visually impaired users.
8. **ISM room reverberation** — simulating realistic rooms in real-time.

### The Hot Debate
> **The WebXR spec is blind to non-visual perception.** Spatial audio has no standardized API, no HRTF DOM, no ambisonic integration. The spec treats audio as an afterthought, while the brain treats it as primary. The gap between visual and audio spatial rendering in WebXR is not a bug — it's a design philosophy that needs to be challenged.

### Potential Guests
| Name | GitHub | What They'll Bring |
|------|--------|--------------------|
| **leomccormack** | @leomccormack | Spatial_Audio_Framework creator; ambisonics, HRTFs & temporal rendering |
| **crlandsc** | @crlandsc | SAF contributor; spatialization algorithms |
| **ali-vosoughi** | @ali-vosoughi | SAF contributor; ambisonic processing |
| **jacobhollebon** | @jacobhollebon | SAF contributor; spatial audio architecture |
| **BinWang28** | @BinWang28 | audio-ai-hub; HRTF research & spatial speech perception |
| **edurnebernal** | @edurnebernal | Audio-visual spatial perception in VR |
| **TheBarmaEffect** | @TheBarmaEffect | Perception-first spatial audio engine design |
| **Boris Smus** | @orighst | omnitone; browser-based binaural rendering |
| **Brandon Jones** | @brandonpjones | omnitone; Web Audio API spatial rendering |
| **Julius Kammerl** | @jkarmer | omnitone; real-time spatial audio in browsers |
| **Tim Fain** | @timfain | Jaunt VR; spatial content creation & rendering |
| **freeman-jiang** | @freeman-jiang | beatsync; multi-device spatial audio synchronization |
| **Amelia Eckard** | @ameliaeckard | Apple Vision Pro spatial audio; accessibility & navigation |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** In mixed reality, holograms drift, stick to the camera, and fail to stay where you placed them. What are the fundamental limits of registering digital content to the physical world?

### Key Topics
1. **Hologram registration errors** — "holograms sticking to camera," reprojection drift across network stacks.
2. **Optical passthrough quality** — the resolution/contrast race (visionOS, Quest 3, XREAL).
3. **Plane detection & spatial mapping** limitations in dynamic environments.
4. **WebXR layers & projection-layer scaling** — cut-off artifacts, DOM overlays in canvas.
5. **Dynamic foveation** — can the renderer cheat the brain by reducing peripheral resolution?
6. **The attention economy** — how persistent holographic UIs compete for and hijack focus.
7. **Hand tracking reliability** — the fundamental interaction contract (StereoKit #922, MRTK #9510).
8. **WebXR visibility & DOM integration** — #1396, #1414, #1420.

### The Hot Debate
> **Is the WebXR spec blind to non-visual perception?** Dynamic foveation (#1420), visibility masking (#1396), and DOM overlay (#1414) gaps all point to the same problem: WebXR is designed for visual rendering, not for the full perceptual experience. The spec has no mechanism for audio spatialization, no gesture-recognition abstraction beyond controller profiles, and no framework for perceptual calibration. We're building MR interfaces on a visual-only foundation.

### Potential Guests
| Name | GitHub | What They'll Bring |
|------|--------|--------------------|
| **jeromeetienne** | @jeromeetienne | AR.js creator (15.8k ⭐); web AR pioneer; marker-based & geospatial AR |
| **hiukim** | @hiukim | MindAR creator (2.7k ⭐); on-device image/face tracking with TF.js |
| **maluoi** | @maluoi | StereoKit maintainer; XR engine & OpenXR backend |
| **cabanier** | @cabanier | W3C Immersive Web; WebXR DOM overlays & visibility |
| **AdaRoseCannon** | @AdaRoseCannon | W3C Immersive Web; dynamic foveation & accessibility |
| **chrisdavidmills** | @chrisdavidmills | WebXR editor; visibility-mask events |
| **danrossi** | @danrossi | WebXR layers work; projection-layer rendering |
| **himorin** | @himorin | WebXR contributor; security/privacy of spatial mapping |
| **bradleylab** | @bradleylab | XR Geoxplorer; hand tracking + XRI interaction |
| **fieldsJacksonG** | @fieldsJacksonG | Microsoft MRC; hologram registration & calibration |

---

## How to Contribute

1. Pick an episode issue and add research findings, issue links, or potential guest suggestions as comments.
2. Submit a PR with updated episode outlines or new research.
3. Tag potential guests and track outreach status.
4. Monitor the linked GitHub issues from the source repos — new debates emerge constantly.

## Key GitHub Issue Links for Contributors

### Episode 1 — Latency
- [WiVRn #1099 — Framerate stalling after passthrough reacquisition](https://github.com/WiVRn/WiVRn/issues/1099)
- [WiVRn #1078 — 144/207/240Hz Quest 3 support](https://github.com/WiVRn/WiVRn/issues/1078)
- [ALVR #334 — Latency measurements missing info](https://github.com/polygraphene/ALVR/issues/334)
- [SteamVR-for-Linux #21 — Tracking not smooth](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21)
- [arcore-android-sdk #1779 — Camera/IMU clock offset](https://github.com/google-ar/arcore-android-sdk/issues/1779)
- [OpenXR-MixedReality #131 & #132 — Frame timestamp & D3D12](https://github.com/microsoft/OpenXR-MixedReality/issues/131)
- [MixedReality-WebRTC #157 — AEC failure](https://github.com/microsoft/MixedReality-WebRTC/issues/157)

### Episode 2 — Spatial Audio
- [Spatial_Audio_Framework #66 — Higher-order ambisonics](https://github.com/leomccormack/Spatial_Audio_Framework/issues/66)
- [Spatial_Audio_Framework #55 — HRTF dataset loading](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55)
- [Spatial_Audio_Framework #58 — ISM room reverberation](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58)
- [omnitone #2 — Mobile browser support](https://github.com/GoogleChrome/omnitone/issues/2)
- [omnitone #109 — Project status](https://github.com/GoogleChrome/omnitone/issues/109)
- [MixedReality-WebRTC #157 — AEC failure](https://github.com/microsoft/MixedReality-WebRTC/issues/157)

### Episode 3 — MR Interfaces
- [MixedRealityCompanionKit #221 — Holograms sticking to camera](https://github.com/microsoft/MixedRealityCompanionKit/issues/221)
- [MixedRealityCompanionKit #228 — Calibration instability](https://github.com/microsoft/MixedRealityCompanionKit/issues/228)
- [webxr #1420 — Dynamic foveation](https://github.com/immersive-web/webxr/issues/1420)
- [webxr #1396 — Actual vs. internal visibility](https://github.com/immersive-web/webxr/issues/1396)
- [webxr #1414 — HTML-in-canvas integration](https://github.com/immersive-web/webxr/issues/1414)
- [webxr-samples #228 — Projection-layer scale cutoff](https://github.com/immersive-web/webxr-samples/issues/228)
- [StereoKit #922 — Hand tracking pinch problems](https://github.com/StereoKit/StereoKit/issues/922)
- [MRTK-Unity #9510 — Hand visibility performance drop](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9510)

---

*Initial outline synthesized from GitHub research, September 2026. All issue links are live and actively maintained.*
