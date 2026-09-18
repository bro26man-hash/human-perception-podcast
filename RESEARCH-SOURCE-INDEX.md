# 📡 Research Source Index

> Live index of all GitHub repositories, issues, and contributors surveyed for 'The Future of Human Perception' podcast.
> Last updated: September 18, 2026.

---

## Repositories Surveyed

| Repo | Stars | Last Active | Focus Areas |
|---|---|---|---|
| `AR-js-org/AR.js` | 15,791 | Sept 2026 | Web AR, markerless tracking, location-based AR |
| `mrdoob/three.js` | 115,600+ | Active | 3D rendering, WebXR backend |
| `playcanvas/engine` | 16,900+ | Active | 3D engine, WebXR sound |
| `HiukKim/mind-ar-js` | 2,733 | Sept 2026 | Web AR, face tracking, image tracking |
| `jeeliz/jeelizFaceFilter` | 2,938 | Sept 2026 | Face tracking, AR face filters |
| `microsoft/MixedRealityToolkit-Unity` | 6,100+ | Active | MR toolkit, hand tracking, controllers |
| `microsoft/MixedReality-WebRTC` | 944 | Active | MR communication, AEC, spatial audio |
| `microsoft/spatial-computing` | 83 | June 2026 | Azure AI + MR samples |
| `microsoft/OpenXR-MixedReality` | Active | Active | OpenXR MR, D3D12, frame timestamps |
| `microsoft/MixedRealityCompanionKit` | Active | Active | MR calibration, hologram registration |
| `immersive-web/webxr` | 3,100+ | Active | WebXR spec, foveation, visibility |
| `immersive-web/webxr-samples` | Active | Active | WebXR samples, projection layers |
| `google-ar/arcore-android-sdk` | 5,200+ | Active | ARCore, camera-IMU calibration |
| `google-ar/arcore-unity-sdk` | 1,400+ | Active | ARCore Unity, plane detection |
| `Unity-Technologies/arfoundation-samples` | 3,400+ | Active | AR Foundation samples |
| `google/omnitone` | 911 | Active | WebXR spatial audio emitters |
| `google/spatial-media` | 2,100+ | Active | Spatial media, 360° video |
| `leomccormack/Spatial_Audio_Framework` | 748 | Active | Measured HRTFs, room modeling |
| `IvanCampos/visionOS-examples` | 405 | Active | visionOS, Apple Vision Pro demos |
| `StereoKit/StereoKit` | 1,100+ | Active | XR engine, OpenXR backend |
| `KhronosGroup/OpenXR-SDK` | 1,100+ | Active | OpenXR specification & SDK |
| `KhronosGroup/glTF` | 10,000+ | Active | 3D assets, audio emitter extensions |
| `ValveSoftware/openvr` | Active | Active | OpenVR runtime, tracking |
| `ValveSoftware/SteamVR-for-Linux` | Active | Active | Linux VR, latency, tracking smoothness |
| `polygraphene/ALVR` | Active | Active | Air Link VR, latency measurement |
| `Igalia/wolvic` | Active | Active | WebXR browser, spatial audio, HRTF |
| `Hubs-Foundation/hubs` | 2,200+ | Active | Social VR, Spatial Audio |
| `freeman-jiang/beatsync` | 3,200+ | Active | Spatial audio + music |

## Key Issues Surfaced

### Perceptual Latency
| Issue | Repo | Comments | Key Finding |
|---|---|---|---|
| #282 | WiVRn/godot-xr | 40 | Temporal irregularity, not pipeline depth, causes stutter |
| #1099 | WiVRn/godot-xr | — | 47-min freeze after passthrough refocus; compositor lies about FPS |
| #334 | polygraphene/ALVR | — | ~33.6ms unaccounted latency; VR stacks underreport by 30-50% |
| #21 | ValveSoftware/SteamVR-for-Linux | 97+ | "Tracking not smooth and a little delayed" |
| #1779 | google-ar/arcore-android-sdk | — | 13-35ms camera-IMU clock skew on mid-range devices |
| #157 | microsoft/MixedReality-WebRTC | 17 | AEC disabled/broken in OpenXR MR stacks |
| #131 | microsoft/OpenXR-MixedReality | — | Frame timestamp & D3D12 performance |
| #132 | microsoft/OpenXR-MixedReality | — | D3D12 performance (cont.) |
| #228 | microsoft/MixedRealityCompanionKit | 19 | Calibration instability: works once, never twice |
| #826 | AR-js-org/AR.js | 2 | Image tracking demo broken |
| #825 | AR-js-org/AR.js | 4 | Location-based AR not working |

### Spatial Audio
| Issue | Repo | Comments | Key Finding |
|---|---|---|---|
| #1180 | Igalia/wolvic | 17 | Bluetooth audio delay: manual slider, no auto-calibration |
| #992 | Igalia/wolvic | — | WebXR spatial audio gap |
| #1196 | Igalia/wolvic | — | Audio rendering & presence paradox |

### Mixed Reality Interfaces
| Issue | Repo | Comments | Key Finding |
|---|---|---|---|
| #221 | microsoft/MixedRealityCompanionKit | 18 | Holograms sticking to camera |
| #228 | microsoft/MixedRealityCompanionKit | 19 | Calibration instability |
| #228 | immersive-web/webxr-samples | — | XRGPUBinding projection-layer scale cutoff |
| #231 | immersive-web/webxr-samples | — | Media binding video quad layer scaling |
| #235 | immersive-web/webxr-samples | — | xrGPUBinding preferred color format |
| #1414 | immersive-web/webxr | — | WebXR integration with HTML-in-canvas |
| #1420 | immersive-web/webxr | — | Dynamic foveation |
| #1396 | immersive-web/webxr | — | Confusion around actual vs. internal visibility |
| #5305 | A-Frame/A-Frame | 20 | Hand controls misalignment |
| #2281 | A-Frame/A-Frame | 23 | "Building UIs in VR" still incomplete after 9 years |
| #4709 | A-Frame/A-Frame | 106 | WebXR-on-Chrome (most-commented A-Frame issue) |
| #5658 | A-Frame/A-Frame | — | 3D Gaussian splats PR — cutting edge |

## Contributors Identified

### Tier 1 — Deep Technical Leaders
| GitHub Handle | Repos | Expertise | Episode Fit |
|---|---|---|---|
| @jeromeetienne | AR.js | Web AR, markerless tracking | Ep 1 |
| @dmarcos | A-Frame, WebXR | WebXR runtime, performance | Ep 1, 2 |
| @donrmccurdy | A-Frame | Hand tracking, MR input | Ep 1, 3 |
| @hiukim | mind-ar-js | Web AR, face tracking | Ep 1 |
| @jnalpha | StereoKit | XR engine, spatial audio | Ep 3 |
| @xytovl | WiVRn | VR latency, temporal irregularity | Ep 1 |
| @leinardi | SteamVR-for-Linux | Linux VR, tracking latency | Ep 1 |
| @jd-3d | ALVR | VR streaming, latency measurement | Ep 1 |

### Tier 2 — Standards & Browser Engineers
| GitHub Handle | Repos | Expertise | Episode Fit |
|---|---|---|---|
| @cabanier | W3C Immersive Web | WebXR DOM overlays, visibility | Ep 3 |
| @AdaRoseCannon | W3C Immersive Web | Dynamic foveation, accessibility | Ep 3 |
| @chrisdavidmills | W3C Immersive Web | Visibility-mask events | Ep 3 |
| @himorin | WebXR | Security/privacy of spatial mapping | Ep 3 |
| @danrossi | WebXR layers | Projection-layer rendering | Ep 3 |
| @aphillia | WebXR input profiles | i18n, input device diversity | Ep 3 |
| @Ben_Tudor | Igalia/wolvic | HRTF, Bluetooth audio delay | Ep 2 |

### Tier 3 — Platform & Tooling
| GitHub Handle | Repos | Expertise | Episode Fit |
|---|---|---|---|
| @brycehutchings | Microsoft OpenXR | D3D12, MR performance | Ep 1, 3 |
| @fredemmott | Microsoft XR | HoloLens platform | Ep 1 |
| @emaschino | MR performance | Pipeline optimization | Ep 1 |
| @fieldsJacksonG | Microsoft MRC | Hologram registration, calibration | Ep 1, 3 |
| @nicolocarpignoli | AR.js maintainer | Web AR ecosystem, community | Ep 1 |
| @andgokevin | A-Frame co-maintainer | VR UI design | Ep 3 |
| @leomccormack | Spatial_Audio_Framework | Measured HRTFs, room modeling | Ep 2 |

---

*This index is a living document. Add new issues, repos, and contributors as research continues.*