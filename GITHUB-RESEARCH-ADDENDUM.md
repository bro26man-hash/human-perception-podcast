# 📡 GitHub Research Addendum — Live Audit of AR/MR/Perception Repos

> Comprehensive audit of open issues, active PRs, and key contributors across the most active augmented reality, spatial computing, and perceptual science repositories on GitHub.

---

## Repositories Surveyed

### 1. jeromeetienne/AR.js — ⭐ 15,791
**Description:** Efficient Augmented Reality for the Web — 60fps on mobile.
**Language:** HTML/JavaScript
**Last updated:** September 2026

**Open Issues (Hot):**
| # | Title | Author | Comments | Relevance |
|---|---|---|---|---|
| #826 | ImageTracking demo doesn't work | tlecoz | 2 | Tracking reliability — core to MR interface trust |
| #825 | Location-based example doesn't work | jiajia-tao | 4 | GPS drift in location AR — hologram drift problem |

**Key Concept:** Web AR must solve tracking reliability at the browser level; these issues represent the gap between "AR works in demo" and "AR works for everyone."

### 2. ValveSoftware/openvr — ⭐ 6,661
**Description:** OpenVR SDK.
**Language:** C++
**Last updated:** September 2026

**Open Issues (Hot — Latency Focus):**
| # | Title | Author | Comments | Relevance |
|---|---|---|---|---|
| #249 | Equivalent of motion-to-photon latency? Measuring latency incurred by sensor hardware | echuber2 | 2 | **Foundational question** — how do we even measure the thing we're trying to fix? |
| #258 | Displaying old data, avoiding glFinish() and latency spikes | ekmett | 2 | Rendering architect shows the fundamental tension: frame completion vs. display refresh |
| #374 | Massive lag spike every 8 seconds — reproducible | craigspree | 5 | Systematic timing issue in driver/compositor pipeline |
| #1704 | Tracker data from OVR is very delayed compared to tracker data from SteamVR | guiglass | 5 | Latency varies by API path even within Valve's own ecosystem |
| #1808 | Steam Link: Features request for OpenVR SDK | sergioberg | 0 | Feature gaps in the SDK |
| #308 | Support for reformatted output to HMD | david-clement | 9 | Display output pipeline |

**Key Concept:** The motion-to-photon latency problem is unsolved after 9+ years. Multiple developers are hitting different points of the same fundamental bottleneck.

### 3. fholger/openvr_fsr — ⭐ 1,809
**Description:** Add Image Upscaling via AMD FidelityFX SuperResolution or NVIDIA Image Scaling to SteamVR games.
**Language:** C++
**Last updated:** September 2026

**Key Concept:** Foveated rendering via SuperResolution — rendering at lower peripheral resolution to free GPU budget, potentially reducing per-frame processing time and thus effective latency. This is the leading practical mitigation for the latency problem.

### 4. KhronosGroup/glTF — (Active audio extension development)
**Description:** The glTF 2.0 specification — the "JPEG of 3D" — now expanding into spatial audio.

**Open PRs/Issues (Spatial Audio):**
| # | Title | Author | Comments | Relevance |
|---|---|---|---|---|
| #2561 | Proposal: Layered Audio Extension Architecture | rudybear | 2 | **Comprehensive framework** for spatial audio in glTF |
| PR #2137 | KHR_audio_emitter | robertlong | 58 | **Most active** — base emitter extension, heavy discussion |
| PR #2631 | KHR_audio_environment | rudybear | 1 | Acoustic environment modeling |
| PR #2632 | KHR_audio_graph | rudybear | 2 | Audio signal routing graph |
| #2506 | Extending glTF for Synchronized Immersive Video and Audio | powersimple | 2 | Broader sync question |
| #2162 | Undefined behaviour of light (and audio) under viewer scale | hybridherbst | 1 | Spec gap at different scales |

**Key Concept:** glTF is evolving from visual-only to multi-sensory. The audio extension architecture (emitter + graph + environment) could become the web standard for spatial audio.

### 5. facebook/immersive-web-sdk — ⭐ 357
**Description:** WebXR made simple. Full-featured framework with interactions, locomotion, and spatial UI.
**Language:** TypeScript

**Open Issues (Interface Focus):**
| # | Title | Author | Comments | Relevance |
|---|---|---|---|---|
| #13 | Expose WebXR Hit-Test & Depth APIs to Userland | aribornstein | 4 | **Critical MR gap** — spec doesn't expose spatial understanding |
| #11 | Locomotion Example — Falling through the floor | epreglej | 4 | Locomotion instability even in official examples |
| #41 | Spatial UI forwarded touch/click events lose iOS Safari user activation | felixtrz | 0 | Interaction model breaks on dominant mobile platform |
| #53 | Cursor sinks into the surface after the player turns | xrbookstore | 0 | Fundamental MR interface alignment problem |
| #7 | Guidance Needed: Post processing | huwprosser | 4 | Visual quality still an afterthought |
| #51 | three.js R181 broken | Sythos | 1 | Dependency fragility |

**Key Concept:** WebXR's spec gap extends beyond audio to spatial understanding (hit-test, depth) — the interfaces we need for MR don't exist in the standard yet.

### 6. google-ar/three.ar.js — ⭐ 2,914
**Description:** A helper three.js library for building AR web experiences that run in WebARonARKit and WebARonARCore.

**Open Issues:**
| # | Title | Author | Comments | Relevance |
|---|---|---|---|---|
| #128 | [feature request] AR+VR (ArCore + Cardboard) + CamaradaVR | jumpjack | 2 | AR/VR convergence — the line is blurring |

### 7. hiukim/mind-ar-js — ⭐ 2,733
**Description:** Web Augmented Reality. Image Tracking, Face Tracking. Tensorflow.js.
**Language:** JavaScript

**Key Concept:** Alternative approach to web AR using ML-based tracking instead of marker-based. More flexible but potentially less precise — a different perceptual trade-off.

### 8. polygraphene/ALVR — ⭐ 1,844
**Description:** Air Link VR — wireless remote display for Gear VR and Oculus Go.
**Language:** C++

**Key Concept:** Wireless VR streaming introduces a different latency calculus: you're compressing, transmitting, and decompressing video frames. The "optimal" latency budget changes when the pipeline includes a network hop.

### 9. mrdoob/three.js — ⭐ 115,636
**Description:** JavaScript 3D Library.
**Language:** JavaScript

**Key Concept:** The foundational engine. Every AR/VR/MR experience on the web eventually touches three.js. Changes to three.js ripple through the entire ecosystem.

---

## 👥 Key Contributors Identified (Potential Podcast Guests)

| Name | GitHub Handle | Repos Contributed To | Expertise |
|---|---|---|---|
| **Jerome Etienne** | @jeromeetienne | AR.js | Web AR pioneer; tracking & geolocation AR; firsthand experience with the latency-perception gap in AR |
| **hiukim** | @hiukim | mind-ar-js | Web AR + TensorFlow.js; ML-based tracking approaches; alternative to marker-based AR |
| **ekmett** | @ekmett | ValveSoftware/openvr | Rendering engineer; deep knowledge of display pipelines and latency; authored the foundational latency issue |
| **fholger** | @fholger | openvr_fsr | Foveated rendering researcher; bridges SuperResolution tech and VR latency mitigation |
| **polygraphene** | @polygraphene | ALVR | Wireless VR streaming architect; understands latency in compressed-transmitted pipelines |
| **rudybear** | @rudybear | KhronosGroup/glTF | Spatial audio extension architect; proposed the full KHR_audio_emitter/graph/environment framework |
| **robertlong** | @robertlong | KhronosGroup/glTF | Submitted the foundational KHR_audio_emitter PR; glTF extension development expert |
| **najadojo** | @najadojo | KhronosGroup/glTF | Microsoft's glTF audio emitter extension; cross-platform spatial audio perspective |
| **aribornstein** | @aribornstein | facebook/immersive-web-sdk | WebXR interface advocate; hit-test & depth API feature request author |
| **mrdoob** | @mrdoob | three.js | Creator of three.js; foundational 3D web technology architect |
| **jumpjack** | @jumpjack | google-ar/three.ar.js | ARCore + Cardboard VR; AR/VR convergence experiments |

---

## 🔥 Cross-Cutting Debate Themes

### Theme 1: The Latency Problem is Unsolved
Both OpenVR issues (#249, #258) and AR.js issues (#825, #826) show that the fundamental perceptual latency problem persists across platforms. VR has foveated rendering (FSR); AR has no equivalent mitigation. Web AR is especially vulnerable because browser budgets are tighter.

### Theme 2: WebXR's Spec Gap
The WebXR Device API spec covers visual rendering and locomotion but is effectively **silent on spatial audio rendering** and **sparse on spatial understanding** (hit-test, depth). The glTF audio extension PRs may be filling this gap from the content side, but the runtime/browser side has no equivalent.

### Theme 3: The Interface Is the Perception
MR interface problems (cursor sinking, locomotion falling through floors, tracking failures) aren't bugs — they're **perceptual events**. Each one breaks the illusion and reminds the user they're wearing a device. The interface IS the perception.

### Theme 4: Audio Presence Paradox
Users forgive visual imperfections far faster than audio ones. A slightly blurry hologram is "cool"; a slightly off spatial audio cue is "creepy." This paradox means that spatial audio quality may be the make-or-break factor for MR adoption.

---

*This addendum is a living document. Contributors should update it as new issues surface or new repos are surveyed.*