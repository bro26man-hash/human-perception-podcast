# 🎙️ The Future of Human Perception — Canonical Episode Outline

> **Research sync: 2026-09-18** — Consolidated from GitHub issue audits across AR.js, MRTK, Lullaby, MindAR, WiVRn, ALVR, OpenVR, Spatial_Audio_Framework, and glTF repositories.

---

## Series Vision

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality? This podcast tracks the fiercest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Key Repos | Stars |
|---|---|---|
| Web AR | `AR-js-org/AR.js`, `hiukim/mind-ar-js`, `jeeliz/jeelizFaceFilter` | 15.8k / 2.7k / 2.9k |
| WebXR & 3D | `mrdoob/three.js`, `playcanvas/engine`, `immersive-web/webxr` | 115k / 16.7k / 3.1k |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity`, `microsoft/MixedReality-WebRTC` | 6.1k / 944 |
| Open-source VR | `WiVRn/WiVRn`, `polygraphene/ALVR`, `ValveSoftware/openvr`, `ValveSoftware/SteamVR-for-Linux` | Active |
| AR SDKs | `google-ar/arcore-android-sdk`, `google-ar/arcore-unity-sdk`, `Unity-Technologies/arfoundation-samples` | 5.2k / 1.4k / 3.4k |
| Spatial Audio | `leomccormack/Spatial_Audio_Framework`, `GoogleChrome/omnitone`, `google/spatial-media` | 748 / 911 / 2.1k |
| Standards | `KhronosGroup/glTF`, `KhronosGroup/OpenXR-SDK`, `StereoKit/StereoKit` | 10k+ / 1.1k / 1.1k |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** How fast must a system respond before the human brain perceives it as real — and why sub-20 ms motion-to-photon latency remains so hard to deliver.

### Core Question
Can foveation trick the brain into forgiving lag? What is the true motion-to-photon budget for comfort?

### 🔥 GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Perception Impact |
|---|---|---|---|---|
| 1 | Per-client scheduled frames stall xrEndFrame | WiVRn #1099 | 🔴 15+ comments, 2026 | 47-min freeze after Quest 3 refocus; brain's vestibular system notices |
| 2 | Temporal irregularity vs. average latency | WiVRn #282 | 🔴 40 comments | Stutter = irregularity, not depth; brain detects pacing, not absolute ms |
| 3 | "Missing" 30-50% latency in VR streaming | ALVR #334 | 🔴 Active | Optimizing against wrong number; 20ms rule may be unreachable |
| 4 | Camera↔IMU clock offset 13-35ms | ARCore #1779 | 🔴 Active, 2026 | Invisible to devs; phantom 100m path from in-place rotation |
| 5 | Acoustic echo cancellation broken in MR | MixedReality-WebRTC #157 | 🔴 17 comments | AEC failure = spatial audio collapse; perceptual calibration failure |
| 6 | No standardized latency benchmark | OpenVR #249 | 🔴 Metrology crisis | Comparisons meaningless; industry uses different methodologies |
| 7 | Reprojection error in timewarp | OpenVR #659 | 🔴 Active | Wrong predicted pose → visceral discomfort; last line of defense failing |
| 8 | ARCore session crash on Samsung | ARCore #1762 | 🟡 Active | Session resume crash; spatial model violently interrupted |
| 9 | Web AR tracking failure | AR.js #826, #825 | 🟡 First bottleneck | Real-time tracking as first perceptual bottleneck on web |
| 10 | AR.js maintainers needed | AR.js #609 | 🟡 Stale = stale techniques | Web AR's ceiling held back by maintenance gaps |

### 🎤 Potential Guests

| Name | Role | GitHub | What They Bring |
|---|---|---|---|
| xytovl | Maintainer, WiVRn | @xytovl | OpenXR streaming; packet-timing & pacing; stutter analysis |
| jd-3d | Developer, ALVR | @jd-3d | VR streaming forensics; discovered 30-50% latency underreporting |
| leinardi | Maintainer, SteamVR-for-Linux | @leinardi | Open-source VR latency debugging; motion-to-photon pipeline |
| AaronMillward | Contributor, WiVRn | @AaronMillward | Field reports of perceptual stutter & motion sickness |
| brycehutchings | Microsoft OpenXR-MR | @brycehutchings | HoloLens 2 D3D12 path; frame-timestamp precision |
| emaschino | Microsoft MRC | @emaschino | HoloLens 2 performance; mixed-reality compositor calibration |
| Maluoi | Maintainer, StereoKit | @maluoi | XR engine architecture; OpenXR backend; performance optimization |

### Key Topics to Cover
1. The motion-to-photon pipeline — sensor → predict → render → encode → transport → decode → display. Every stage injects latency.
2. The 20ms rule — where it came from, why it's debated, and whether it's even measurable.
3. Foveated rendering — can eye tracking + selective resolution fool the brain?
4. Reprojection & timewarp — the last line of defense and when it fails.
5. Clock sync — camera↔IMU offsets that destroy AR presence silently.
6. Streaming latency — why WiFi 6E and 7 aren't enough.
7. The metrology crisis — we can't even agree on how to measure latency.

### Debate Table
| Position | Argument |
|---|---|
| **The 20ms rule is dead** | ALVR #334 shows 30-50% underreporting; the real budget is 30ms+ |
| **Foveation saves us** | Cognitive science shows the fovea processes 20x faster; latein peripheral is tolerable |
| **Irregularity > absolute latency** | WiVRn #282: the brain detects jitter, not depth; 20ms steady is better than 10ms stutter |
| **Web AR is the future** | AR.js + MindAR make perceptual research accessible; maintainers are the bottleneck |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics, and the audio presence paradox — why spatial audio is both the most trust-building and most neglected modality in XR.

### Core Question
Why is the WebXR spec still visual-only for spatial audio? Can you have presence without a soundscape?

### 🔥 GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Perception Impact |
|---|---|---|---|---|
| 1 | Acoustic echo cancellation broken in MR | MixedReality-WebRTC #157 | 🔴 17 comments | Room acoustics contaminate spatial model; not audio quality — perceptual calibration failure |
| 2 | Audio emitter extension for glTF | KhronosGroup/glTF PR #1400 | 🔴 Active | MSFT_audio_emitter extension; spatial audio standards gap in 3D asset pipelines |
| 3 | KHR_gaussian_splatting + audio | KhronosGroup/glTF PR #2490 | 🔴 225 comments | Neural rendering meets spatial audio; new paradigm for acoustic field modeling |
| 4 | Spatial_Audio_Framework maintenance | leomccormack/SAF issues | 🟡 Active | Community contributions stalled; ambisonic processing needs modern audio API |
| 5 | Web Audio API spatial rendering gaps | omnitone issues | 🟡 HRTF database quality | Browser-based binaural rendering limited by HRTF accuracy |
| 6 | Multi-device spatial audio sync | beatsync issues | 🟡 Clock precision | freeman-jiang's research on multi-device sync; perceptual coherence across speakers |

### 🎤 Potential Guests

| Name | Role | GitHub | What They Bring |
|---|---|---|---|
| leomccormack | Creator, Spatial_Audio_Framework | @leomccormack | Ambisonics, HRTFs, cross-platform spatial audio in C |
| crlandsc | Contributor, SAF | @crlandsc | Spatialization algorithms; real-time rendering |
| BinWang28 | HRTF research | @BinWang28 | Personalized HRTFs; spatial speech perception |
| edurnebernal | Audio-visual perception | @edurnebernal | Ventriloquism effect; audio-visual integration in VR |
| Boris Smus | Web audio, Google/omnitone | @orighst | Browser-based binaural rendering; FOA/HOA |
| Brandon Jones | Web audio, Google/omnitone | @brandonpjones | Web Audio API spatial rendering; ambisonic codecs |
| freeman-jiang | Creator, beatsync | @freeman-jiang | Multi-device spatial audio synchronization; clock sync precision |
| Amelia Eckard | Apple Vision Pro spatial audio | @ameliaeckard | Accessibility via spatial audio; indoor navigation for visually impaired |

### Key Topics to Cover
1. HRTF fundamentals — why personalized head-related transfer functions matter.
2. Ambisonics vs. binaural — the technical tradeoffs and perceptual differences.
3. The WebXR gap — spatial audio is specified but not implemented in browsers.
4. Echo cancellation as perceptual calibration — MR-WebRTC #157.
5. glTF audio emitter extensions — the standards gap in 3D asset pipelines.
6. Neural acoustic fields — Gaussian splatting meets spatial audio (glTF #2490).
7. Multi-device sync — clock precision and perceptual coherence.

### Debate Table
| Position | Argument |
|---|---|
| **Presence requires audio** | Vision alone creates a fragile illusion; sound is the ontological anchor |
| **WebXR is blind to audio** | The spec defers to Web Audio API, which has no spatial standard |
| **Personalized HRTFs are essential** | Generic HRTFs work for 60%; the other 40% get poor presence |
| **Ambisonics is the future** | Higher-order ambisonics + Ambisonic codec = hierarchical, scalable |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift, and wayfinding — the design space of interaction when the screen disappears.

### Core Question
Is the WebXR spec blind to non-visual perception? What does a hologram need to do to feel "real"?

### 🔥 GitHub-Sourced Hot Debates

| # | Debate | Source | Signal | Perception Impact |
|---|---|---|---|---|
| 1 | HoloLens 2 handshake stability | microsoft/MixedRealityToolkit-Unity issues | 🟡 Tracking calibration drift | Hologram drift over time destroys the "it's really there" feeling |
| 2| MR interface design patterns | MRTK UX building blocks | 🟡 Active | Bounds Control, Object Manipulator, Solvers — the grammar of MR interaction |
| 3 | Spatial awareness & mesh understanding | MRTK Spatial Awareness | 🟡 Active | How well does the device understand the physical room? |
| 4 | WebXR input sources | immersive-web/webxr | 🟡 Spec gap | Gamepad vs. hand tracking vs. eye tracking — no unified interaction model |
| 5 | AR.js markerless AR limitations | AR.js #833 | 🟡 City-scale AR | GPS + visual-inertial odometry; drift over large spaces |
| 6 | MindAR tracking stability | MindAR #556 | 🟡 Active | Unstable AR content; ineffective tracking configurations |
| 7 | Lullaby spatial audio + spatial UI | google/lullaby | 🟡 WIP | Entity-Component-System for VR; spatial audio integration |

### 🎤 Potential Guests

| Name | Role | GitHub | What They Bring |
|---|---|---|---|
| jeromeetienne | Creator, AR.js (15.8k⭐) | @jeromeetienne | Web AR pioneer; marker-based & geospatial AR; AR.js 2→3 transition |
| hiukim | Creator, MindAR (2.7k⭐) | @hiukim | On-device image/face tracking with TF.js; production-ready AR |
| fredemmott | Microsoft XR Advocate | @fredemmott | HoloLens platform strategy; mixed-reality advocacy & ecosystem |
| fieldsJacksonG | Microsoft MRC | @fieldsJacksonG | Hologram registration & calibration; MixedRealityCompanionKit |
| Maluoi | Maintainer, StereoKit | @maluoi | XR engine architecture; spatial interaction design |
| spscan | StereoKit contributor | @spscan | Hand tracking + eye tracking integration in XR |

### Key Topics to Cover
1. The interaction grammar — Bounds Control, Object Manipulator, Solvers, and what they teach us about MR UX.
2. Hologram drift — why registration degrades and how to compensate.
3. Spatial awareness — mesh understanding, plane detection, and room mapping.
4. The WebXR input gap — no unified model for hand/eye/voice/gesture.
5. Wayfinding in MR — how users navigate when the screen is gone.
6. City-scale AR — AR.js #833 and the dream of persistent, location-based AR.
7. Non-visual perception — haptics, proprioception, and the missing modalities.

### Debate Table
| Position | Argument |
|---|---|
| **The screen is the enemy** | Flat-screen UX destroys presence; MR needs a new interaction grammar |
| **WebXR is incomplete** | Input sources, spatial audio, and haptics are afterthoughts in the spec |
| **Registration is everything** | A hologram that drifts 2° after 10 minutes is not a hologram — it's a hallucination |
| **Web AR is ready for primetime** | AR.js + MindAR = 18k stars; the web is the most accessible XR platform |

---

## How to Contribute

1. Pick an episode issue (`#76`, `#77`, or `#78`)
2. Add research findings, issue links, or potential guest suggestions as comments
3. Submit a PR with updated outlines or new research
4. Tag potential guests and track outreach status

## Links & Resources

- [Immersive Web Working Group](https://www.w3.org/immersive-web/)
- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [Mixed Reality Toolkit](https://aka.ms/mrtkdocs)
- [AR.js (new org)](https://github.com/AR-js-org/AR.js)
- [Spatial_Audio_Framework](https://github.com/leomccormack/Spatial_Audio_Framework)
- [glTF Audio Extensions](https://github.com/KhronosGroup/glTF)

## Cross-References

| File | Purpose |
|---|---|
| `HOT-DEBATES-AUDIT.md` | Live audit of GitHub issues across AR/MR repos |
| `GUEST_DIRECTORY.md` | Structured directory of potential guests by episode |
| `RESEARCH-Database.md` | Annotated bibliography and research notes |
| `episodes/` | Episode drafts, show notes, and recording materials |
