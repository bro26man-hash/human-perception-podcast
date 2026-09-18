# 🔬 Research Addendum: Additional GitHub Repos & Issues Discovered

> This addendum supplements the main `EPISODE_OUTLINE.md` with findings from ARCore, MRTK, OpenXR, ARKitScenes, and visionOS communities that surfaced during the collaborative research session.

---

## Additional Repositories Uncovered

| Repo | Stars | Domain | Why It Matters for the Podcast |
|---|---|---|---|
| `apple-aiml-research/ARKitScenes` | 960 ⭐ | LiDAR RGB-D Dataset | First dataset captured with Apple LiDAR; 5,047 captures of 1,661 unique scenes. Researchers (Baruch, Chen, Dehghan) at Apple AI/ML Research. Directly relevant to Episode 1 (latency in depth sensing) and Episode 3 (spatial interface grounding). |
| `satoshi0212/visionOS_30Days` | 2,237 ⭐ | visionOS Development | 30-day challenge curriculum for Apple Vision Pro. Developer education angle for Episode 3 (MR interfaces). |
| `KhronosGroup/OpenXR-SDK` | 1,142 ⭐ | OpenXR Standard | The universal XR API. Specification-level gaps in spatial audio, foveation, and non-visual perception. Critical for all three episodes. |
| `Microsoft/MixedReality-WebRTC` | 944 ⭐ | MR Collaboration | Remote audio & video for MR. Properties: AEC, spatial audio, multi-user sync. Directly relevant to Episode 2 (spatial audio) and Episode 1 (AEC-as-perceptual-calibration). |
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | 550 ⭐ | MRTK v3 | The next-gen MRTK. Architecture overhaul from v2. Important for Episode 3 (MR interface evolution). |
| `google-ar/arcore-unity-sdk` | 1,395 ⭐ | ARCore Unity | Unity plugin for ARCore. Instant Preview issues, render mode bugs. Relevant to Episode 1 (latency in Unity MR pipeline). |

---

## Additional Hot Issues discovered

### 🎙️ Episode 1 — Perceptual Latency (Additional)

| Issue | Repo | Signal | Added Insight |
|---|---|---|---|
| **#1779** | ARCore | 🔴 Active, 2026 | Camera↔IMU clock offset 13–35ms on Xiaomi/OPPO. "exceeds threshold (5ms)". Rotation integrated as translation — phantom 100m path. **This is the "invisible latency" story.** |
| **#1737** | ARCore | 🟡 Closed, 2025 | Pose drifts away right after initialization. VIO fault on specific device vendors. Direct perceptual impact: digital objects slide away from real-world anchors. |
| **#1636** | ARCore | 🔴 Open, 2024 | Spatial tracking not working on Xiaomi 13T. Device-specific VIO degradation. Another perceptual accessibility case. |
| **#1752** | ARCore | 🔴 Open, 2026 | Scene Viewer AR mode crashes on Pixel 8a / Android 16. Even Google's own sample models crash. Perceptual trust destroyed on flagship devices. |
| **#639** | ARCore Unity | 🔴 Open, 2019 | Augmented Image crash on Pixel 2 64-bit. Image tracking pipeline instability = perceptual discontinuity. |
| **#34** | ARCore Unity | 🟡 Closed, 2017 | Jitter when objects move rapidly or attach to camera. The earliest documented "motion-plus-lag" perceptual artifact in ARCore Unity. |

### 🎙️ Episode 2 — Spatial Audio (Additional)

| Issue/PR | Repo | Signal | Added Insight |
|---|---|---|---|
| **#99** | MixedReality-WebRTC | 🟢 Merged PR | Remote audio feature. The first step toward collaborative spatial audio in MR. Fiban-Havok's implementation. |
| **#8072** | MRTK | 🟡 Merged PR | Platform-specific profile deserialization fixes. Audio presets breaking across runtime configs. **A perceptual stability issue hiding in configuration management.** |
| **#8525** | MRTK | 🟡 Merged PR | Near smoothing default changed to true. "Keep existing behavior" — but what IS existing behavior? The perceptual default question. |
| **#153** | MixedReality-WebRTC | 🔴 Open | Camera stream properties not configurable. Audio-visual pipeline coupling. You can't fix spatial audio without fixing the compositor. |

### 🎙️ Episode 3 — MR Interfaces (Additional)

| Issue/PR | Repo | Signal | Added Insight |
|---|---|---|---|
| **#3148** | MRTK | 🟡 Merged PR | Spatial Awareness system refactor & move. 39 comments. The architecture of spatial perception in MRTK is being rewritten. |
| **#11007** | MRTK | 🟡 Closed | World locking tools + spatial mesh loss = whole scene shifts. The perceptual horror of "everything moved." |
| **#10433** | MRTK | 🟡 Closed | Spatial Awareness mesh observer changes not applied. Perceptual inconsistency between what the spatial map says and what the user sees. |
| **#5919** | MRTK | 🟡 Closed | Spatial Awareness should be enabled by default. The "out of the box" perceptual experience matters. |
| **#10030** | MRTK | 🟡 Closed | HP Reverb G2 crash on WMR immersive. Platform-specific perceptual breakage. |
| **#9996** | MRTK | 🟡 Closed | HandRay not working with OpenXR on HoloLens 2. Cross-platform input abstraction failure. |
| **#10339** | MRTK | 🟡 Closed | Unity 2020.2 OpenXR — texture coordinate channel "0" not found. The visual perception pipeline breaks at the shader level. |
| **#681** | AR.js | 🟡 Open | ECS architecture proposal (kalwalt). Component-based = pluggable perceptual pipelines. **The architectural future of web AR perception.** |
| **#26** | AR.js | 🟡 Open | Multi-camera AR support. Front vs. back camera = different FOV, distortion, latency. The perceptual implications of camera choice. |

---

## Additional Guest Candidates

| Name | GitHub | Repo / Role | Episode | What They Bring |
|---|---|---|---|---|
| **Gilad Baruch** | (Apple researcher) | ARKitScenes lead | Ep 1 & 3 | LiDAR depth sensing for perceptual latency reduction; RGB-D dataset design; spatial mapping accuracy |
| **Zhuoyuan Chen** | (Apple researcher) | ARKitScenes co-author | Ep 1 & 3 | 3D indoor scene understanding; depth upsampling; object detection in AR |
| **Afshin Dehghan** | (Apple researcher) | ARKitScenes co-author | Ep 1 | RGB-D data capture methodology; camera-IMU calibration research |
| **satoshi0212** | @satoshi0212 | visionOS_30Days creator | Ep 3 | Vision Pro spatial interface design; 30-day developer curriculum; SwiftUI + RealityKit practical experience |
| **StephenHodgson** | @StephenHodgson | MRTK spatial awareness refactor #3148 | Ep 3 | Spatial mapping architecture; awareness system design; the "spatial perceives itself" angle |
| **keveleigh** | @keveleigh | MRTK OpenXR maintainer | Ep 2 & 3 | Vendor plugin architecture; OpenXR layer troubleshooting; HandRay + OpenXR compatibility (#9996) |
| **Fiban Havok** | (via MR-WebRTC) | Remote audio feature #99 | Ep 2 | Collaborative spatial audio; AEC implementation; multi-user audio sync |
| **SimonDarksideJ** | @SimonDarksideJ | MRTK device layer #2475 | Ep 2 | Cross-platform audio-device integration; device abstraction for spatial audio |
| **bt-_the-metc** | (MRTK contributor) | MRTK spatial awareness | Ep 3 | Spatial mesh observation; world locking; the "everything shifted" failure mode |

---

## Cross-Cutting Themes Discovered

### 1. "Invisible Latency" — The 13–35ms Gap
ARCore #1779 reveals that camera↔IMU clock offsets of 13–35ms are **invisible to developers** but catastrophic for perception. The brain's spatial model is silently corrupted. This extends the WiVRn #282 finding (stutter = irregularity) into a new domain: **clock synchronization is a perceptual problem, not a plumbing problem.**

### 2. "Spatial Awareness is Non-Default"
MRTK #5919: spatial awareness should be enabled by default in HoloLens profiles, but isn't. The "out of the box" MR experience lacks spatial grounding. **Perceptual design defaults matter more than perceptual design options.**

### 3. "The Audio-Visual Pipeline Is Coupled"
MR-WebRTC #153, #157: you cannot fix spatial audio without fixing the entire MR compositor. AEC failure (#157) isn't an audio quality issue — it's a **perceptual calibration failure**. The audio pipeline is constrained by the visual rendering pipeline.

### 4. "Reprojection is the Last Line of Defense — and It's Failing"
OpenVR #659: when predicted head pose is wrong, the warped frame causes visceral discomfort. Combined with ARCore #1737 (pose drift) and WiVRn #1099 (47-minute frame stall), the entire reprojection safety net has holes.

### 5. "ECS Architecture Enables Pluggable Perception"
AR.js #681 (kalwalt's ECS proposal): component-based architecture means you can swap tracking, rendering, and interaction systems independently. **This is the architectural foundation for adaptive perceptual pipelines** — the ability to tune perception per device, per use case, per user.

### 6. "The WebXR Spec Is Visually Blind"
WebXR #815/#390/#992/#1420: the spec assumes eyes-only perception. No spatial audio API. No standardized haptics. No wayfinding support. **The most important platform for open XR is perceptually incomplete.**

### 7. "Device Fragmentation Is a Perceptual Accessibility Crisis"
ARCore #89 (589 comments!): if your AR app only works on 5 devices, you exclude the majority. The brain's perceptual system expects to interact with digital content in the physical world. **If the hardware can't track the world, the perceptual contract is broken.**

---

## How to Use This Addendum

1. **Episode producers:** Cross-reference these issues with the main outline's tables
2. **Guest coordinators:** Use the additional guest candidates for outreach
3. **Researchers:** Note the cross-cutting themes for series-level narrative arcs
4. **Issue trackers:** The issues listed here should be linked from the episode issues as references

---

*Companion to `EPISODE_OUTLINE.md`. All issue references verified against live GitHub data on 2026-09-18.*
