# 🎙️ The Future of Human Perception — Episode Outline

## Overview

This podcast explores the engineering and human science behind how technology reshapes perception. Each episode is grounded in real open debates from the most active GitHub repositories in AR, spatial computing, and perceptual science.

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency and the 20ms rule

**Core Question:** Can foveation and reprojection trick the brain into forgiving lag — or is the 20ms threshold a hard physical limit?

### Key Topics
- Motion-to-photon (MTP) latency: what it is, why 20ms is the magic number
- Foveated rendering as a latency cheat — trading peripheral detail for speed
- Async reprojection vs. direct rendering — the SteamVR-for-Linux debate (issue #21: "Tracking not smooth and a little delayed," 97 comments, 24 👍)
- OpenTrack's 2025.1 release saga (issue #2030: 174 comments) — Qt 6 migration, camera bugs, and the architecture debt behind perceptual lag
- The vestibular-ocular reflex: why latency makes you nauseous, not just annoyed

### GitHub Evidence
| Repo | Issue | Debate |
|---|---|---|
| ValveSoftware/SteamVR-for-Linux | [#21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) | HMD tracking delayed & unsmooth despite AsyncReprojection |
| opentrack/opentrack | [#2030](https://github.com/opentrack/opentrack/issues/2030) | Release process, Qt 6 port, architectural debt in tracking pipeline |
| ValveSoftware/openvr | [General](https://github.com/ValveSoftware/openvr) | OpenVR SDK reproduction timing and compositor settings |

### Potential Guests
- **sthalik** — OpenTrack maintainer (issue author, community member). Deep knowledge of tracking pipeline architecture and the Qt 6 migration saga.
- **leinardi** — SteamVR-for-Linux issue reporter (97 comments on tracking latency). Passionate about the Linux VR experience and reprojection timing.
- **reduz (Juan Linietsky)** — Godot Engine co-creator. Can speak to how 3D engines handle frame timing and the perceptual impact of rendering latency.

### Debate Table
| Position | Argument |
|---|---|
| **Foveation is enough** |渲染 only 2° of high-res detail saves 60-70% GPU time, easily hitting 20ms for the majority of users |
| **Foveation is a crutch** | It masks the problem for static gaze but fails during fast head movements — the exact moments that matter |
| **17ms is the real limit** | Vestibular-visual conflict becomes unbearable below 17ms; 20ms is polite, not physiological |
| **Reprojection IS the future** | AI-driven frame generation (DLSS Frame Generation, similar) will make 20ms irrelevant within 3 years |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics, and the audio presence paradox

**Core Question:** Why is the WebXR spec still visual-only for spatial audio, and can a flexible HRTF Resource type finally fix it?

### Key Topics
- The SpatialAudioModel proposal in Godot (issue [#4377](https://github.com/godotengine/godot-proposals/issues/4377) — 16 👍, milestone 4.x) — a Resource type for HRTF loading without shipping a fixed dataset
- WebAudio's Multi-channel PannerNode (issue [#2386](https://github.com/WebAudio/web-audio-api/issues/2386)) — why binauralizing ambisonic mixes needs spec-level support, not just library hacks
- HRIR/HRTF in desktop audio: easyeffects issue [#2783](https://github.com/wwmm/easyeffects/issues/2783) — up-mixing to 5.1/7.1, 8-channel IR convolution, down-mixing back to stereo
- FAudio issue [#345](https://github.com/FNA-XNA/FAudio/issues/345) — 3rd-order ambisonic signal chain via JACK → IEM ALLRAD → ASIO output; does FAudio support ambisonic mixing?
- The "audio presence paradox": visual AR overlays are accepted as "real"; spatial audio that doesn't match visual origin feels "fake" — cross-modal binding failure

### GitHub Evidence
| Repo | Issue | Debate |
|---|---|---|
| godotengine/godot-proposals | [#4377](https://github.com/godotengine/godot-proposals/issues/4377) | SpatialAudioModel Resource type — HRTFs belong in core or in user-downloadable assets? |
| WebAudio/web-audio-api | [#2386](https://github.com/WebAudio/web-audio-api/issues/2386) | Multi-channel PannerNode — ambisonic binauralization needs a new Node type |
| wwmm/easyeffects | [#2783](https://github.com/wwmm/easyeffects/issues/2783) | HRIR convolution: up-mix → 8-ch IR → down-mix pipeline for desktop spatialization |
| FNA-XNA/FAudio | [#345](https://github.com/FNA-XNA/FAudio/issues/345) | Ambisonic signal path: JACK → IEM ALLRAD → ASIO; does FAudio handle 5.1.2? |

### Potential Guests
- **ellenhp** — Godot SpatialAudioModel proposal author. Deep expertise in HRTF datasets, PCA compression, and why shipping fixed HRTFs in core is a mistake.
- **pmlt** — WebAudio Multi-channel PannerNode proposal author. Works at the intersection of W3C standards and practical 3D audio implementation.
- **mastr-ch13f** — easyeffects HRIR feature requester. Passional about making desktop spatial audio accessible to non-gamers.
- **alex-schroedsen** — FAudio spatial audio implementer. Bridge between XAudio2 legacy and modern ambisonic pipelines.
- **Calinou** — Godot Foundation 4.x milestone maintainer. Can speak to why the audio spatialization proposal is slated for 4.x but blocked by architectural constraints.

### Debate Table
| Position | Argument |
|---|---|
| **HRTFs belong in user assets, not core** | Head shapes vary too much; one dataset fits nobody. Let users download their own HRTF sprigs from the Asset Library. |
| **Ship a default HRTF** | Users won't download anything. Without a default, SpatialAudioModel is just an empty shell. |
| **Ambisonics is the universal interchange format** | 1st-order is enough for presence; higher orders are overkill. Decode once, render everywhere. |
| **WebAudio is the missing piece** | WebXR is visual-only for spatial audio. The W3C needs a PannerNode that accepts ambisonic inputs directly. |
| **HRTF = personal identity** | Your HRTF is as unique as your fingerprint. "Perceptual latency" in audio is about mismatch, not delay. |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift, and wayfinding

**Core Question:** Is the WebXR spec blind to non-visual perception — and what does that mean for mixed reality interfaces that feel like home?

### Key Topics
- MR interface design: hologram drift, fixed-foveated rendering, and the 2D-orbit problem
- Wayfinding in spatial computing: how do you navigate a 3D desktop? The "air mouse" vs. laser pointer debate
- Hand tracking as the primary MR input: reliability, latency, and the "pinch gap"
- The WebXR spec gap: no standardized input profiles for non-visual modalities (haptic, proprioceptive, vestibular)
- Cross-modal perception: if your virtual hand moves 50ms behind your real hand, does your brain "own" it? (Rubber Hand Illusion in MR)
- MR overlay persistence: anchoring content to real-world surfaces vs. letting it float — the "spatial anchor drift" problem

### GitHub Evidence
| Repo | Issue | Debate |
|---|---|---|
| microsoft/MixedRealityToolkit-Unity | [General](https://github.com/microsoft/MixedRealityToolkit-Unity) | Hand tracking reliability, hologram stability, spatial anchor management |
| microsoft/MixedReality-WebRTC | [General](https://github.com/microsoft/MixedReality-WebRTC) | WebRTC for MR: low-latency streaming vs. interactive perception |
| immersive-web/webxr | [General](https://github.com/immersive-web/webxr) | Spec gap: no non-visual input/output profiles; hand tracking vs. controller paradigm |
| godotengine/godot | [XR modules](https://github.com/godotengine/godot/tree/master/modules) | Godot's XR architecture: ARVRServer, XRBodyTracker, and the 3D interface framework |

### Potential Guests
- **reduz (Juan Linietsky)** — Godot co-creator. Can speak to the architectural decisions behind Godot's XR support and why 3D interfaces are harder than 3D rendering.
- **punto- (Ariel Manzur)** — Godot co-creator. Perspective on how 2D-first design philosophy shapes (and limits) 3D interface paradigms.
- **Calinou** — Godot Foundation. Maintains the milestone that includes XR audio and input improvements.
- **ellenhp** — Spatial audio in Godot. Cross-modal perception: if audio doesn't match visual origin, does the brain reject the whole MR experience?

### Debate Table
| Position | Argument |
|---|---|
| **Hand tracking is the future** | No controllers to lose, no batteries, no精度高 — just hands. The pinch gesture is universal. |
| **Controllers are safer** | Hand tracking flickers, jitters, and fails in bright light. Controllers are deterministic. |
| **The 2D-orbit problem is unsolved** | Rotating a 3D object with a 2D input device is like using a TV remote to sculpt clay. |
| **WebXR is visual-centric by design** | The spec defines `XRReferenceSpace` and `XRPose` but nothing for auditory or haptic reference frames. |
| **Spatial anchors need drift correction** | GPS-level accuracy (1m) is not enough for MR. Centimeter-level anchor persistence is the unsolved problem. |
| **The Rubber Hand Illusion applies to MR** | If visuo-motor correlation is strong enough, the brain will "own" any input device — even a laser pointer. |

---

## Production Notes

- **Recording format:** Conversational, two hosts + one guest per episode
- **Length target:** 45–60 minutes
- **Pre-production:** Each episode requires 2 weeks of GitHub issue research and guest outreach
- **Open issues link:** Each episode has a companion GitHub issue (see below) for community input

## Companion Issues

- 🎙️ **Episode 1:** "Latency and the Perceptual Threshold" — [Issue #1](https://github.com/bro26man-hash/human-perception-podcast/issues/1)
- 🎙️ **Episode 2:** "Spatial Sound and the Third Dimension" — [Issue #2](https://github.com/bro26man-hash/human-perception-podcast/issues/2)
- 🎙️ **Episode 3:** "Interfaces Beyond the Flat Screen" — [Issue #3](https://github.com/bro26man-hash/human-perception-podcast/issues/3)
