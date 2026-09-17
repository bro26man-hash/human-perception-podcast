# 🔬 GitHub Research Supplement — September 17, 2026

> Fresh audit of AR/MR/Spatial Computing repos, issue debates, and contributor profiles. Complements `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md`.

---

## 🆕 Repositories Discovered This Session

| Repository | Stars | Focus | Why It Matters |
|---|---|---|---|
| `AR-js-org/AR.js` | 15,789 | Web AR (marker + location + image tracking) | Hot topic: AR.js 2→3 transition with ECS architecture. Community-driven rebuild. |
| `google/lullaby` | 1,197 | C++ VR/AR libraries | Google's VR/AR C++ toolkit; less active but architecturally interesting. |
| `microsoft/xr-development-for-beginners` | 564 | Spatial computing curriculum | Best onboarding resource for MR developers; Vue-based learning modules. |
| `hiukim/mind-ar-js` | 2,731 | Web AR with TF.js | Image + face tracking on the web; production-ready AR filters. |
| `jeeliz/jeelizFaceFilter` | 2,938 | Multi-face AR WebGL filters | Real-time face tracking for AR filters; lightweight and fast. |
| `exyte/ARTetris` | 1,524 | ARKit + SceneKit AR game | Demonstrates ARKit placement and interaction patterns. |
| `thomwolf/Magic-Sand` | 1,018 | AR sandbox software | Educational AR sandtable; shows occlusion & placement challenges. |

---

## 🆕 Hottest Open Issues — Deep Dive

### Episode 1 — Perceptual Latency

#### 🔥 ValveSoftware/openvr #659 — Reprojection Error (4 comments)
- **Author:** msclecram
- **Core problem:** Reprojection error in OpenVR's timewarp systems — when the predicted head pose is wrong, the warped frame doesn't match what the user expects, causing visceral discomfort.
- **Perception angle:** Reprojection is the last line of defense against motion-to-photon latency. When it fails, the brain gets conflicting motion/position signals. This is the *mechanical* manifestation of perceptual latency.
- **Debate:** Can ML-based pose prediction (neural networks instead of linear extrapolation) reduce reprojection error below perceptual threshold?
- **Guest candidate:** @msclecram — deep reprojection pipeline expertise

#### 🔥 ValveSoftware/openvr #249 — "Motion to Photon Latency" Measurement (2 comments)
- **Author:** echuber2
- **Core problem:** No standardized way to measure motion-to-photon latency in VR hardware. The industry uses different methodologies, making comparisons meaningless.
- **Perception angle:** If we can't measure it consistently, how can we claim to have solved the latency problem? This is a metrology crisis.
- **Debate:** Should there be an industry-standard latency benchmark (like SPEC for CPUs)?

#### 🆕 AR-js-org/AR.js #681 — AR.js-next: ECS Architecture & Roadmap (3 comments)
- **Author:** kalwalt
- **Core problem:** AR.js 2.x is monolithic and hard to extend. AR.js-next proposes an Entity-Component-System architecture for modularity, better Three.js r152+ integration, and a clearer roadmap.
- **Perception angle:** Architecture decisions affect update loop timing. An ECS approach could enable more predictable frame budgets → lower temporal jitter → better perceptual latency.
- **Debate:** Does refactoring for maintainability indirectly improve perceptual performance?

#### 🆕 AR-js-org/AR.js #288 — Markerless Location-Based AR: Realistic Object Placement (11 comments)
- **Author:** nickw1 (maintainer)
- **Core problem:** Geolocation-based AR places objects inaccurately (meters off), breaking the perceptual illusion of virtual objects coexisting with the real world.
- **Perception angle:** If a virtual chair appears 2 meters from where you expect it, your brain rejects the "realness" of the AR scene. Precision matters for presence.

#### 🆕 AR-js-org/AR.js #609 — AR.js Maintainers Needed (9 comments)
- **Author:** nickw1
- **Core problem:** The AR.js project is critically under-maintained. The original creator (jeromeetienne) moved on; the community needs more contributors.
- **Perception angle:** Stale AR libraries mean stale perceptual techniques. Web AR's perceptual ceiling is held back by maintenance gaps.

#### 🆕 AR-js-org/AR.js #302 — iOS/Safari Device Orientation Reimplementation (14 comments)
- **Author:** nickw1
- **Core problem:** AR.js's device orientation tracking breaks on Safari/iOS due to Apple's permission model and sensor API changes.
- **Perception angle:** Platform-specific perceptual failures. The iPhone is the most common AR device — if orientation tracking breaks, the entire spatial illusion collapses.

### Episode 2 — Spatial Audio

#### 🔥 mumble-voip/mumble #6597 — Proper Physical Treatment of Sound Waves for Spatial Audio (22 comments)
- **Author:** Krzmbrzl (Mumble maintainer)
- **Core proposal:** Replace Mumble's simplistic spatial audio with:
  1. **Proper HRTFs** (Head-Related Transfer Functions) — modeling how sound waves interact with the head, pinna, and torso
  2. **Doppler shift** — frequency shifts from relative motion of source and listener
  3. **Environmental effects** — reverb, occlusion, attenuation based on 3D world geometry
- **Suggested implementation:** OpenAL-Soft (LGPL licensed) as the audio backend, with Qt Spatial Audio as a potential alternative
- **Perception angle:** This is the most serious open-source proposal to bring physics-accurate spatial audio to a production audio engine. Current Mumble spatial audio is "simplistic" — it doesn't simulate how real sound behaves.
- **Key references cited:**
  - IEEE Paper: "Sound Localization" (ieeexplore.ieee.org/document/5661988)
  - OpenAL Soft: github.com/kcat/openal-soft
  - Spatial Audio Framework: github.com/leomccormack/Spatial_Audio_Framework
  - Qt Spatial Audio: doc.qt.io/qt-6/qtspatialaudio-index.html
  - EAX 5.0: historical Hi-Fi environmental audio standard
- **🆕 Guest candidate:** @Krzmbrzl — Mumble maintainer, proposing the most ambitious open-source spatial audio upgrade

#### 🔥 Mach1Studios/m1-spatialaudioserver #2 — Binaural Rendering (8 comments)
- **Author:** Avnerus
- **Core question:** Does Mach1's spatial audio server support binaural rendering? Can convolvers be used on top of the basic layer (referencing Google Chrome's Omnitone HOA convolver approach)?
- **Perception angle:** Binaural rendering is the only way to deliver 3D audio over headphones — the dominant XR audio delivery method. Without it, spatial audio is limited to speaker-based setups (which don't work for most users).
- **🆕 Guest candidate:** @Avnerus — building real-time binaural rendering on constrained devices

#### 🆕 GoogleChrome/omnitone — Mobile Gap (referenced in HOT-DEBATES-AUDIT)
- **Status:** Still open since 2016, 23 comments
- **🆕 Context:** The Mach1 binaural approach and the Mumble HRTF proposal represent two different philosophies: (1) server-side binaural rendering for constrained devices vs. (2) client-side HRTF via OpenAL for desktop quality. Which path will dominate?

### Episode 3 — Mixed Reality Interfaces

#### 🔥 AR-js-org/AR.js #681 — ECS Architecture (also relevant to E3)
- The shift from monolithic AR.js to modular ECS directly affects how MR interfaces are built. Component-based architecture means pluggable tracking, rendering, and interaction systems — exactly what MR needs.

#### 🆕 AR-js-org/AR.js #26 — Multi-Camera AR Support (22 comments)
- **Author:** nicolocarpignoli (maintainer)
- **Core problem:** No API to choose which camera to use for AR on multi-camera devices (e.g., front + back on smartphones).
- **Perception angle:** MR interfaces that use the wrong camera (front vs. back) fundamentally misalign the mixed-reality experience. Front cameras have different FOV, distortion, and latency characteristics.

#### 🆕 AR-js-org/AR.js #58 — A-Frame-AR + Physics Integration (4 comments)
- **Author:** yannklein
- **Core problem:** A-Frame's AR module doesn't work with A-Frame's physics engine. Virtual objects in AR can't interact with physical surfaces realistically.
- **Perception angle:** Physics-accurate object behavior (gravity, collision, occlusion) is essential for the brain to accept virtual objects as "real" in a spatial context.

#### 🔥 MixedRealityCompanionKit #221 — Holograms Sticking to Camera (18 comments)
- Referenced in HOT-DEBATES-AUDIT but worth re-emphasizing: this is the #1 MR registration failure. When holograms stick to camera instead of staying anchored to the real world, the brain's spatial processing is fundamentally confused.

#### 🆕 ARCore Depth Gap (google-ar/arcore-android-sdk #120) + Camera Control #153
- Referenced in existing EPISODE_OUTLINE.md. The depth-sensing gap and lack of camera API control are the two most fundamental MR interface problems on Android.

---

## 🆕 Prominent Developers & Researchers — New Identifications

### AR.js / Web AR Community
| Name | Repo / Role | Why They'd Be Great on the Podcast |
|---|---|---|
| **jeromeetienne** | Creator, AR.js (15.8k ⭐) | The godfather of web AR. Can speak to the evolution from marker-based to image/geospatial tracking, and why the 2→3 rewrite matters. |
| **nicolocarpignoli** | Maintainer, AR.js | Led the community-driven rebuild. Deep expertise in WebXR tracking, geospatial AR, and Safari/iOS AR challenges. |
| **kalwalt** | Author, AR.js-next ECS proposal | Architect thinking about the future of web AR modularity. Can bridge the gap between game engine architecture and AR. |
| **nickw1** | Maintainer, AR.js (geospatial) | Deep expertise in location-based AR accuracy, iOS sensor API, and the practical limits of GPS-based spatial placement. |
| **hiukim** | Creator, MindAR (2.7k ⭐) | Production-ready on-device image/face tracking with TensorFlow.js. Can speak to the gap between research demos and real products. |

### Spatial Audio Deep-Dive
| Name | Repo / Role | Why They'd Be Great on the Podcast |
|---|---|---|
| **Krzmbrzl** | Maintainer, Mumble VoIP | The most ambitious open-source proposal for physics-accurate spatial audio (HRTF + Doppler + environmental effects). 22-comment issue showing deep technical engagement. |
| **Avnerus** | Developer, Mach1 Studios | Building real-time binaural rendering for constrained devices. Can speak to the philosophy of "good enough" spatial audio vs. physics-accurate rendering. |
| **leomccormack** | Creator, Spatial_Audio_Framework & SPARTA | Ambisonics, HRTFs, ISM room modeling. The bridge between academic spatial audio research and implementation. |
| **hoch** | Maintainer, Omnitone | Has lived with the mobile spatial audio gap for a decade. Can speak to the political and technical barriers to standardizing web spatial audio. |

### Latency & OpenVR
| Name | Repo / Role | Why They'd Be Great on the Podcast |
|---|---|---|
| **msclecram** | OpenVR contributor, reprojection expert | Deep expertise in timewarp/reprojection — the mechanical last line of defense against perceptual latency. |
| **echuber2** | OpenVR latency measurement advocate | Championed the need for standardized motion-to-photon latency benchmarks. |
| **xytovl** | Maintainer, WiVRn | Already well-documented. The temporal irregularity finding was paradigm-shifting. |

---

## 🆕 Cross-Cutting Insights

### The "Three L's" of Perceptual Failure
From this research session, three recurring failure modes emerge across all three episodes:

1. **Latency** (Ep 1): The system responds too slowly or inconsistently → vestibular-visual conflict → sickness
2. **Localization** (Ep 2): The audio doesn't seem to come from the right place → presence collapse → "it's just headphones"
3. **Anchoring** (Ep 3): The virtual object doesn't stay where you put it → cognitive rejection → "it's fake"

### The WebXR Spec's Three Blind Spots
1. **No spatial audio API** (webxr #390, 8 years open)
2. **No haptic specification** (afterthought in input profiles)
3. **No biometric/sensor abstraction** (eye tracking, EEG — emerging but unstandardized)

### The Maintenance Gap as Perceptual Ceiling
Multiple repos (AR.js #609, OpenVR #249, Omnitone #2) show that **stale maintenance directly caps perceptual quality**. When libraries aren't updated, they lag behind hardware capability and perceptual science. This is an under-discussed systemic issue.

---

## 📋 Tracking Checklist

- [ ] Contact **jeromeetienne** for Episode 1 or 3 (AR.js history + architecture)
- [ ] Contact **nicolocarpignoli** for Episode 3 (AR.js 3.0 roadmap + iOS challenges)
- [ ] Contact **Krzmbrzl** for Episode 2 (HRTF + Doppler + environmental audio)
- [ ] Contact **Avnerus** for Episode 2 (binaural rendering on mobile)
- [ ] Contact **msclecram** for Episode 1 (reprojection error + latency)
- [ ] Contact **xytovl** for Episode 1 (temporal irregularity + WiVRn #1099)
- [ ] Verify AR.js #681 ECS proposal status before Episode 3 recording
- [ ] Test Mach1 binaural rendering demo for Episode 2 sound clip
- [ ] Re-audit OpenVR reprojection issues before Episode 1 final script

---

*Supplement to `GITHUB-RESEARCH-ADDENDUM.md` and `HOT-DEBATES-AUDIT.md`. Last updated: 2026-09-17.*
