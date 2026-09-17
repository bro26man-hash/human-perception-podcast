# GitHub Research Addendum — September 2026

> Live audit of GitHub issues, contributors, and hot debates across AR/MR/Spatial Computing repos. Updated 2026-09-17.

---

## Most Active Repositories (Research Backbone)

| Repo | Stars | Language | Focus | Last Updated |
|---|---|---|---|---|
| `mrdoob/three.js` | 115.6k | JS | 3D engine / WebXR | 2026-09-17 |
| `playcanvas/engine` | 16.9k | JS | Web 3D / WebXR / glTF | 2026-09-17 |
| `AR-js-org/AR.js` | 15.8k | JS | Web AR (marker + geolocation) | Active |
| `google-ar/arcore-android-sdk` | 5.2k | Java | Android AR SDK | Active |
| `microsoft/MixedRealityToolkit-Unity` | 6.1k | C# | MR toolkit | Active |
| `olucurious/Awesome-ARkit` | 8.0k | — | ARKit resource list | Active |
| `Unity-Technologies/arfoundation-samples` | 3.4k | C# | AR Foundation samples | Active |
| `google/spatial-media` | 2.1k | — | Spatial media format | Active |
| `freeman-jiang/beatsync` | 3.2k | — | Multi-device audio sync | Active |
| `jeeliz/jeelizFaceFilter` | 2.9k | JS | Web face tracking AR | 2026-09-13 |
| `hiukim/mind-ar-js` | 2.7k | JS | Web AR (image/face tracking) | 2026-09-16 |
| `google-ar/arcore-unity-sdk` | 1.4k | C# | ARCore Unity SDK | Active |
| `StereoKit/StereoKit` | 1.1k | C# | XR engine (OpenXR + WebXR) | Active |
| `KhronosGroup/OpenXR-SDK` | 1.1k | C | OpenXR standard | Active |
| `GoogleChrome/omnitone` | 911 | JS | Spatial audio (FOA/HOA) | Active |
| `microsoft/MixedReality-WebRTC` | 944 | C# | MR communication stack | Active |
| `leomccormack/Spatial_Audio_Framework` | 748 | C | Spatial audio algorithms | Active |
| `maxxfrazer/RealityUI` | 700 | Swift | RealityKit UI components | 2026-09-01 |
| `sceneview/sceneview` | 1.3k | Kotlin | 3D & AR SDK (Android/iOS/Web) | 2026-09-17 |
| `microsoft/xr-development-for-beginners` | 564 | — | XR dev tutorials | Active |
| `IvanCampos/visionOS-examples` | 405 | Swift | visionOS spatial UI examples | Active |
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | 550 | C# | MRTK community fork | Active |
| `Hubs-Foundation/hubs` | 2.2k | JS | Social VR / A-Frame | Active |
| `immersive-web/webxr` | 3.1k | — | WebXR spec | Active |
| `immersive-web/webxr-ar-module` | — | — | WebXR AR module | Active |
| `immersive-web/webxr-samples` | — | — | WebXR samples | Active |
| `immersive-web/plane-detection` | — | — | WebXR plane detection | Active |
| `KhronosGroup/glTF` | 10k+ | — | 3D asset format (audio extensions) | Active |
| `dolphin-emu/dolphin` | — | C++ | Game emulator (spatial audio) | Active |

---

## Top Contributors & Potential Guests by Domain

### Episode 1: Latency & Perceptual Threshold

| Name | GitHub | Repo / Role | Key Issues |
|---|---|---|---|
| **xytovl** | @xytovl | WiVRn maintainer | #1099 (passthrough freeze), #282 (stutter/irregularity), #1078 (high refresh rate) |
| **leinardi** | @leinardi | SteamVR-for-Linux maintainer | #21 (tracking lag, 97+ comments) |
| **jd-3d** | @jd-3d | ALVR developer | #334 (missing latency underreporting) |
| **IceyMint** | @IceyMint | WiVRn reporter | #1099 (found the freeze bug) |
| **maxkojju** | @maxkojju | WiVRn reporter | Pico GPU frame scheduling issues |
| **zoeleu** | @zoeleu | WiVRn reporter | #1078 (Quest 3 high refresh rate) |
| **brycehutchings** | @brycehutchings | Microsoft OpenXR-MR | #131, #132 (D3D12 frame timestamps) |
| **emaschino** | @emaschino | Microsoft MRC | HoloLens 2 performance |
| **fredemmott** | @fredemmott | Microsoft XR Advocate | Platform strategy |
| **fieldsJacksonG** | @fieldsJacksonG | Microsoft MRC | #228, #221 (calibration instability) |
| **chrisfromwork** | @chrisfromwork | Microsoft MRC | #221 (hologram camera sticking) |
| **Daniel4144** | @Daniel4144 | MixedReality-WebRTC | locatable camera & projection matrix |
| **fiban-havok** | @fiban-havok | MixedReality-WebRTC reporter | H.264 encoder blockiness |
| **jameszhong2008** | @jameszhong2008 | MixedReality-WebRTC | #157 (AEC failure) |
| **Maluoi** | @Maluoi | StereoKit maintainer | OpenXR backend, performance |
| **AndrewJDR** | @AndrewJDR | immersive-web/webxr-ar-module | #44 (camera feed delay) |
| **tangobravo** | @tangobravo | immersive-web/webxr-ar-module | #78, #77 (AR module gaps) |

### Episode 2: Spatial Audio

| Name | GitHub | Repo / Role | Key Issues |
|---|---|---|---|
| **leomccormack** | @leomccormack | Spatial_Audio_Framework creator | #58 (ISM bug), #55 (SONIMO bugs), #66 (HOA) |
| **crlandsc** | @crlandsc | Spatial_Audio_Framework contributor | Spatialization algorithms |
| **ali-vosoughi** | @ali-vosoughi | Spatial_Audio_Framework contributor | Ambisonic processing |
| **jacobhollebon** | @jacobhollebon | Spatial_Audio_Framework contributor | Architecture & design |
| **BinWang28** | @BinWang28 | audio-ai-hub maintainer | HRTF research, spatial speech |
| **edurnebernal** | @edurnebernal | Audio-visual perception researcher | Ventriloquism effect, AV integration |
| **TheBarmaEffect** | @TheBarmaEffect | Spatial audio engine designer | Perception-first design |
| **orighst (Boris Smus)** | @orighst | Google/omnitone | FOA/HOA, binaural rendering |
| **brandonpjones** | @brandonpjones | Google/omnitone | Web Audio API spatial rendering |
| **jkarmer** | @jkarmer | Google/omnitone | Real-time web spatial audio |
| **timfain** | @timfain | Jaunt VR | Spatial content creation |
| **freeman-jiang** | @freeman-jiang | beatsync creator | Multi-device clock sync |
| **ameliaeckard** | @ameliaeckard | Apple Vision Pro spatial audio | Accessibility, navigation for visually impaired |
| **Avnerus** | @Avnerus | Mach1 Studios | Real-time binaural on constrained devices |
| **rudybear** | @rudybear | glTF audio extension author | #2561 (layered audio architecture) |
| **robertlong** | @robertlong | glTF KHR_audio_emitter | Spatial audio emitter extension |
| **Ben Erwin (powersimple)** | @powersimple | glTF immersive media | #2506 (synchronized AV in glTF) |
| **najadojo** | @najadojo | MSFT_glTF_audio_emitter | Microsoft's proprietary audio emitter |
| **pmlt** | @pmlt | WebAudio/web-audio-api | #2386 (Multi-channel PannerNode) |
| **mastr-ch13f** | @mastr-ch13f | easyeffects | #2783 (HRIR support for Convolver) |

### Episode 3: MR Interfaces & Non-Visual XR

| Name | GitHub | Repo / Role | Key Issues |
|---|---|---|---|
| **jeromeetienne** | @jeromeetienne | AR.js creator (15.8k⭐) | Web AR pioneer |
| **hiukim** | @hiukim | MindAR creator (2.7k⭐) | On-device AR tracking |
| **maluoi** | @Maluoi | StereoKit maintainer | OpenXR + WebXR dual backend |
| **davidjscott** | @davidjscott | StereoKit contributor | MR interaction patterns |
| **bkonyves** | @bkonyves | Google AR/VR | Spatial computing platform vision |
| **ricardmarco** | @ricardmarco | MR interaction researcher | Hand tracking ergonomics |
| **Oliver** | @Oliver | Apple visionOS | VisionOS spatial UI |
| **SimonScholl** | @SimonScholl | ARCore pointcloud advocate | #120 (dense depth pointcloud) |
| **inio** | @inio | ARCore device support tracker | #89 (device fragmentation, 589 comments) |
| **jpeltone** | @jpeltone | ARCore | #714 (rear-camera augmented faces) |
| **ROBYER1** | @ROBYER1 | ARCore | #1275 (body pose tracking) |
| **hbmartin** | @hbmartin | Bricky | AR + VLM for LEGO building |
| **AdaRoseCannon** | @AdaRoseCannon | W3C Foveated Rendering CG | #1420 (dynamic foveation) |
| **cabanier** | @cabanier | W3C Immersive Web | WebXR DOM overlays |
| **himorin** | @himorin | WebXR contributor | Security/privacy of spatial mapping |
| **chrisdavidmills** | @chrisdavidmills | WebXR editor | Visibility-mask events |
| **danrossi** | @danrossi | WebXR layers work | Projection-layer rendering |
| **aphillia** | @aphillia | WebXR input profiles | i18n for spatial interaction |
| **IvanCampos** | @IvanCampos | visionOS-examples (405⭐) | Vision Pro passthrough, SE(3) drift |
| **dongyoonpark** | @dongyoonpark | Microsoft MRDL | MR interaction design |
| **richardinerickson** | @richardinerickson | Microsoft MRDL | Surfaces MR, multi-modal feedback |

---

## Hottest Open Debates — Ranked by Engagement

### 🔥 Tier 1: Paradigm-Shifting (10+ comments, high reactions)

1. **WiVRn #1099** — Quest 3 passthrough refocus freeze (47 min!). Perceptual vs. measured latency. @xytovl
2. **ARCore #89** — Device support requests (589 comments, 8+ years). Perceptual accessibility crisis.
3. **ARCore #120** — Dense pointcloud from depth (357 comments, 6 years). MR surface anchoring foundation.
4. **webxr #815** — Spec language precludes non-visual uses (41 comments). Visual-centric spec gap.
5. **webxr #992** — Wayfinding crisis in immersive sessions (36 comments). Spatial navigation breakdown.
6. **SteamVR-for-Linux #21** — Tracking lag (97+ comments). Foundational VR latency report.
7. **MRC #221** — Holograms sticking to camera (18 comments). Fundamental MR registration failure.
8. **MRC #228** — SpectatorView calibration instability (19 comments). Research reproducibility blocker.

### 🔥 Tier 2: Important & Active (3-10 comments)

9. **Hubs #1853** — Spatial audio degrades with users (30 comments). Social XR audio collapse.
10. **Hubs #2643** — User audio broken (30 comments). Social XR audio collapse.
11. **Hubs #5057** — Audio at scale (24 comments). Social XR audio collapse.
12. **MRC #157** — Acoustic echo cancellation broken (17 comments). AEC = spatial audio collapse.
13. **webxr #1414** — HTML-in-canvas integration. DOM overlay rendering.
14. **ARCore #153** — Camera control (flashlight/auto-exposure). Lighting-aware AR perception.
15. **MRC #153** — Blocky H.264 on HoloLens 2 (32 comments). Perceptual quality vs. latency.
16. **glTF #2137** — KHR_audio_emitter PR (58 comments). Spatial audio source standard.
17. **MRTK #914** — MX Ink MR stylus for Meta Quest. Platform convergence without abstraction.
18. **MRTK #511** — Vendor plugin architecture. Cross-platform MR interface design.
19. **webxr #1420** — Dynamic foveation & visibility masking. Perceptual performance lever.
20. **glTF #2561** — Layered audio architecture proposal. Full spatial audio stack in glTF.

### 🟡 Tier 3: Long-Standing & Unresolved

21. **Omnitone #2** — Mobile browser support (23 comments, 10 years). 🔥 Oldest unresolved audio gap.
22. **webxr #390** — CSS/HTML spatial audio (8 years). Spec gap for audio in WebXR.
23. **ARCore #1779** — Camera↔IMU clock offset 13–35ms. Invisible perceptual lag.
24. **ALVR #334** — Latency measurements missing info. Industry underreporting by 30-50%.

---

## Cross-Cutting Research Themes

| Theme | Evidence | Episode |
|---|---|---|
| **Perceptual ≠ Measured** | WiVRn #1099, ALVR #334, ARCore #1779 | E1 |
| **Spatial Audio Has No Standard** | webxr #390 (8 yrs), omnitone #2 (10 yrs) | E2 |
| **MR Registration Fragility** | MRC #228, MRC #221 | E3 |
| **Social XR Audio Collapse** | Hubs #1853/#2643/#5057 | E2 |
| **Spec Accessibility Gap** | webxr #815 (41 comments) | E2 & E3 |
| **Research Reproducibility Crisis** | MRC #228, ISM bug (SAF #58), SONIMO bugs (SAF #55) | E1 & E2 |
| **Perceptual Accessibility** | ARCore #89 (589 comments) | E3 |
| **Standards Convergence (glTF ↔ WebXR)** | KHR_audio_emitter, KHR_audio_graph, KHR_audio_environment | E2 & E3 |
| **Platform Convergence Without Abstraction** | MRTK #914, MRTK #511 | E3 |
| **Frame Irregularity > Average Latency** | WiVRn #282, #1099 | E1 |

---

*Last updated: 2026-09-17 | Maintainer: podcast research team | Contribute: add issue links, new findings, or guest suggestions as PRs or comments*
