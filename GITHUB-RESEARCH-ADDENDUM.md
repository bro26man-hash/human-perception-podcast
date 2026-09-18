# 🔬 GitHub Research Addendum — Hot Debates & Contributors

*Last audited: September 2026*

## Methodology

We searched across GitHub for the most active repositories in augmented reality, spatial computing, and 3D audio. We then surfaced open issues with the highest community engagement (reactions, comments) related to perceptual latency, mixed reality interfaces, and spatial audio. Contributor names were extracted from issue authors, proposal authors, and maintainers.

---

## Section 1 — Most Active AR / Spatial Computing Repositories

### Tier 1: Mega-Stellar (50k+)
| Repo | Stars | Language | Focus |
|---|---|---|---|
| [godotengine/godot](https://github.com/godotengine/godot) | 117,396 | C++ | Full 3D engine with active XR modules (ARVRServer, XRBodyTracker) |

### Tier 2: High-Impact (5k–10k)
| Repo | Stars | Language | Focus |
|---|---|---|---|
| [ValveSoftware/openvr](https://github.com/ValveSoftware/openvr) | 6,661 | C++ | OpenVR SDK — basis of SteamVR, compositor timing, reprojection |
| [google-ar/arcore-android-sdk](https://github.com/google-ar/arcore-android-sdk) | 5,237 | C++ | ARCore — motion tracking, environmental understanding, light estimation |

### Tier 3: Active Discussion (1k–5k)
| Repo | Stars | Language | Focus |
|---|---|---|---|
| [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | 6,100+ | C#/Unity | MRTK — hand tracking, spatial anchors, holographic rendering |
| [godotengine/godot-proposals](https://github.com/godotengine/godot-proposals) | Active | GDScript/C++ | Community proposals including SpatialAudioModel (HRTF) and audio spatialization |

### Tier 4: Spec & Standards
| Repo | Stars | Language | Focus |
|---|---|---|---|
| [WebAudio/web-audio-api](https://github.com/WebAudio/web-audio-api) | Active | JavaScript | Web Audio API spec — Multi-channel PannerNode for spatial audio |
| [immersive-web/webxr](https://github.com/immersive-web/webxr) | Active | IDL/JS | WebXR Device API — MR input/output profiles |

### Tier 5: Desktop Spatial Audio
| Repo | Stars | Language | Focus |
|---|---|---|---|
| [wwmm/easyeffects](https://github.com/wwmm/easyeffects) | Active | C | PipeWire effects — HRIR/HRTF convolution for desktop |
| [FNA-XNA/FAudio](https://github.com/FNA-XNA/FAudio) | Active | C | XAudio2/OpenAL/DirectSound3D reimplementation — ambisonic mixing |

---

## Section 2 — Hottest Open Debates (by reactions + comments)

### 🔥 Debate 1: Perceptual Latency — The 20ms Rule

**Primary source:** [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21)
- **Title:** "Tracking not smooth and a little delayed"
- **Engagement:** 97 comments, 24 👍 reactions, open since Feb 2017
- **Core complaint:** HMD tracking is delayed and unsmooth on Linux even with AsyncReprojection enabled; controllers are "interpolated/approximated"
- **Perceptual angle:** User reports nausea after extended use — vestibular-visual conflict

**Secondary source:** [opentrack/opentrack #2030](https://github.com/opentrack/opentrack/issues/2030)
- **Title:** "opentrack 2025.1 release process"
- **Engagement:** 174 comments, 9 👍, open since May 2025
- **Core issue:** Tracking pipeline architecture debt — Qt 5→6 migration, camera open bugs, MSVC++ build failures
- **Perceptual angle:** Even if tracking works, the software architecture introduces frame pipeline delays that violate the perceptual threshold

**Key contributors:** leinardi (reporter), sthalik (maintainer, 174-comment discussion driver)

### 🔥 Debate 2: Spatial Audio — HRTFs and the WebXR Gap

**Primary source:** [godotengine/godot-proposals #4377](https://github.com/godotengine/godot-proposals/issues/4377)
- **Title:** "Create a Resource type for audio spatialization models"
- **Engagement:** 16 👍 reactions, milestone 4.x, open since Aug 2021
- **Core proposal:** A `SpatialAudioModel` Resource type that manages HRTF sets dynamically — SHOULDN'T ship a fixed HRTF dataset in core, should let users download from Asset Library
- **Key technical constraint:** Can't allow script callbacks into audio thread (buffer underruns); can't overhaul audio architecture without more contributors
- **Debate:** HRTFs in core vs. user-downloaded assets; surround sound (SPCAP) compatibility vs. ambisonic decoding; frequency-domain dense convolution vs. time-domain IIR

**Secondary source:** [WebAudio/web-audio-api #2386](https://github.com/WebAudio/web-audio-api/issues/2386)
- **Title:** "Support Multi-channel PannerNode"
- **Engagement:** Labeled "Needs Discussion" + "category: new feature"
- **Core problem:** Game engines produce ambisonic mixes (7.1.4, 3rd-5th order) that need binauralization — currently requires simulating many PannerNodes; needs ONE PannerNode that accepts ambisonic input
- **Referenced libraries:** Omnitone (Google Chrome), Resonance Audio (Web SDK)

**Tertiary source:** [wwmm/easyeffects #2783](https://github.com/wwmm/easyeffects/issues/2783)
- **Title:** "[Feature Request] Implement HRIR support for the Convolver Effect"
- **Engagement:** 17 comments, open since Nov 2023
- **Core request:** Up-mix 2-ch → 5.1/7.1 → process through 8-ch IR → down-mix to stereo, all inside one Convolver using zita-convolver (64-ch support)

**Quaternary source:** [FNA-XNA/FAudio #345](https://github.com/FNA-XNA/FAudio/issues/345)
- **Title:** "(Question) Implementing Spatial Audio"
- **Engagement:** 2 comments, open since May 2024
- **Core question:** Does FAudio support 5.1.2 channel mixing, ambisonic encoding/decoding, JACK API? User describes a JACK → IEM ALLRAD → ASIO chain for 3rd-order ambisonics

**Key contributors:** ellenhp (Godot proposal), pmlt (WebAudio spec), mastr-ch13f (easyeffects), alex-schroedsen (FAudio), Calinou (Godot Foundation)

### 🔥 Debate 3: Mixed Reality Interfaces — Beyond the Visual Channel

**Primary sources:**
- [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) — hand tracking reliability, hologram drift, spatial anchor persistence
- [immersive-web/webxr](https://github.com/immersive-web/webxr) — spec gap: no non-visual input/output profiles

**Key discussion points (sourced from community):**
1. **Hand tracking vs. controllers:** Tracking flickers in bright light; controllers are deterministic but lose the "natural" feeling
2. **The 2D-orbit problem:** Rotating 3D objects with 2D input is fundamentally limiting
3. **Hologram drift:** Spatial anchors at GPS accuracy (1m) are insufficient for MR; centimeter-level persistence needed
4. **Rubber Hand Illusion in MR:** Cross-modal plasticity — if visuo-motor correlation is strong, brain "owns" any device
5. **WebXR spec blindness:** `XRReferenceSpace` and `XRPose` exist, but nothing for auditory or haptic reference frames

**Key contributors:** reduz (Juan Linietsky, Godot), punto- (Ariel Manzur, Godot), Calinou (Godot Foundation), ellenhp (spatial audio)

---

## Section 3 — Contributor Directory

| GitHub Handle | Repos | Expertise | Guest Potential |
|---|---|---|---|
| **sthalik** | opentrack (maintainer) | Tracking pipelines, Qt architecture, firmware | ⭐⭐⭐⭐⭐ — Episode 1 core guest |
| **leinardi** | SteamVR-for-Linux | Linux VR, reprojection, user experience | ⭐⭐⭐⭐ — Episode 1 user perspective |
| **ellenhp** | godot-proposals (author) | HRTF spatial audio, Godot audio architecture | ⭐⭐⭐⭐⭐ — Episode 2 core guest |
| **pmlt** | web-audio-api (author) | W3C audio spec, multichannel spatialization | ⭐⭐⭐⭐⭐ — Episode 2 spec perspective |
| **mastr-ch13f** | easyeffects | Desktop spatial audio, HRIR convolution | ⭐⭐⭐⭐ — Episode 2 practical perspective |
| **alex-schroedsen** | FAudio | XAudio2, OpenAL, ambisonic signal chains | ⭐⭐⭐⭐ — Episode 2 implementation perspective |
| **reduz (Juan Linietsky)** | godot (co-creator) | 3D engine architecture, frame timing, XR | ⭐⭐⭐⭐⭐ — Episodes 1 & 3 |
| **punto- (Ariel Manzur)** | godot (co-creator) | 2D-first design philosophy, 3D interfaces | ⭐⭐⭐⭐ — Episode 3 design perspective |
| **Calinou** | godot-proposals (maintainer) | Godot 4.x milestones, audio architecture | ⭐⭐⭐⭐ — Episodes 2 & 3 |

---

## Section 4 — Cross-Cutting Themes

| Theme | Episodes | Key Insight |
|---|---|---|
| **The 20ms rule is physiological, not engineering** | 1, 3 | Vestibular-visual conflict makes latency a medical issue, not a performance metric |
| **HRTFs are identity, not settings** | 2 | Your head shape determines your HRTF; one-size-fits-all is perceptually wrong |
| **WebXR is visually biased** | 2, 3 | The spec defines visual reference spaces but ignores auditory/haptic frames |
| **Architecture debt kills perception** | 1, 2 | OpenTrack's Qt 5 debt and Godot's audio thread constraints both trace back to architectural choices |
| **Cross-modal binding is the real presence test** | 2, 3 | If audio doesn't match visual origin, or if hand tracking lags by 50ms, presence collapses |

---

## Appendix: Search Queries Used

- `augmented reality mixed reality stars:>1000`
- `spatial computing LiDAR 3D reconstruction stars:>500`
- `ARCore ARKit spatial anchors stars:>2000`
- `virtual reality steam openvr stars:>1000`
- `godot 3D engine stars:>5000`
- `webxr immersive reality stars:>300`
- `steamvr openvr stars:>5000`
- `perceptual latency is:open sort:reactions-desc`
- `mixed reality interface hand tracking is:open sort:reactions-desc`
- `spatial audio HRTF ambisonics is:open sort:reactions-desc`
- `latency OR "time warp" OR "reprojection" repo:NianticLargeWorlds`
- `code: "perceptual" "latency" language:cpp extension:cpp`
