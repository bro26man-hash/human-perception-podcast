# Episode Scripts — Draft 1 (September 2026)

> Working draft scripts for the first three episodes. Each script follows a
> research-backed structure built around real GitHub issues and contributor expertise.
> **Status:** 🔬 DRAFT — contributors welcome to improve, add sources, and fact-check.

---

## Episode 1 Script — "Latency and the Perceptual Threshold"

**Duration:** 45–60 min | **Format:** Interview + live demo segments

### Cold Open (2 min)
> *"Your inner ear tells you you're moving. Your eyes tell you you're still. Your brain does not know which to trust — and when the gap between those two signals exceeds ~20 milliseconds, the result is nausea, disorientation, and the collapse of presence. In this episode, we trace the motion-to-photon pipeline from IMU sensor to display pixel and ask the people building the pipelines: where does the latency actually live, and why can't we find it?"*

### Segments

**1. The 20 ms Rule — Why Your Brain Has a Deadline (8 min)**
- The vestibular-visual conflict: why 19 ms feels real but 21 ms makes you sick
- Reference: [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) — 97+ comments of users describing the exact feeling
- Guest talking points: @leinardi (SteamVR-for-Linux maintainer) on what latency looks like from the open-source VR side

**2. Where Latency Lives — The Motion-to-Photon Pipeline (12 min)**
- Sensor → Predict → Render → Encode → Transport → Decode → Display
- Each stage: what the instruments measure vs. what the brain detects
- Reference: [ALVR #334](https://github.com/polygraphene/ALVR/issues/334) — "missing" latency underreporting by 30–50%
- Reference: [ARCore #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) — 13–35ms camera↔IMU clock offset on mid-range Androids
- Guest talking points: @jd-3d (ALVR) on the "missing latency" discovery; @brycehutchings (Microsoft OpenXR) on D3D12 vs D3D11 latency on HoloLens

**3. The Jitter Problem — Why Average Latency is the Wrong Metric (10 min)**
- WiVRn #282 and #234 — temporal irregularity vs. mean latency
- The brain detects frame-to-frame jitter (~10 ms variability), not just average delay
- Reference: [WiVRn #1099](https://github.com/WiVRn/WiVRn/issues/1099) — frames scheduled *days* in the future after passthrough refocus
- Guest talking points: @xytovl (WiVRn maintainer) on pacing algorithms and the stutter debate

**4. Web AR Latency — Why Smartphone AR Feels "Off" (8 min)**
- AR.js and MindAR face the same perceptual bottleneck: real-time camera→render on mobile GPUs
- Reference: [AR.js #826](https://github.com/jeromeetienne/AR.js/issues/826), [AR.js #825](https://github.com/jeromeetienne/AR.js/issues/825)
- Reference: [Ultralytics #1915](https://github.com/ultralytics/ultralytics/issues/1915) — YOLOv8 pose model consistency (106 comments)
- Guest talking points: @jeromeetienne (AR.js creator) on why web AR tracking can't match native; @hiukim (MindAR creator) on TensorFlow.js inference latency

**5. Closing — The Unanswerable Question (5 min)**
- If we can't even measure total system latency correctly, how do we optimize for the brain's perception?
- Call to action: listeners share their own latency war stories on GitHub Issues

### Pre-Recording Checklist
- [x] Review WiVRn #1099, #282, #234, #1078
- [x] Review ALVR #334
- [x] Review ARCore #1779, AR.js #826/#825
- [x] Reach out to leinardi, jd-3d, xytovl, jeromeetienne, hiukim
- [ ] Confirm guest availability for 2-hour recording window
- [ ] Prepare Visual: motion-to-photon pipeline diagram
- [ ] Prepare demo: side-by-side latency comparison (WebXR latencies tool)

---

## Episode 2 Script — "Spatial Sound and the Third Dimension"

**Duration:** 50–65 min | **Format:** Interview + spatial audio demonstration

### Cold Open (2 min)
> *"Close your eyes. A voice says your name from behind your left shoulder. You turn left — and there it is. Three speakers, two channels, no headset. Your brain located a sound in 3D space using nothing but time delays and spectral shaping. How do we replicate that in a virtual world —and why, after 10 years of trying, is the WebXR specification still blind to spatial audio?"*

### Segments

**1. The HRTF Problem — Why Generic Head-Related Transfer Functions Fail 20% of Listeners (10 min)**
- How HRTFs work: interaural time difference (ITD), interaural level difference (ILD), spectral shaping
- Why generic HRTFs work for ~80% but leave ~20% with persistent front-back confusion
- Reference: [Spatial_Audio_Framework #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55) — SONIMO dataset loading bugs affecting perceptual accuracy
- Guest talking points: @leomccormack on why personalized HRTFs remain impractical at scale; @BinWang28 on HRTF augmentation and spatial speech perception

**2. The Billion-User Gap — Why Mobile Browsers Can't Do Spatial Audio (10 min)**
- GoogleChrome/omnitone #2 — open since 2016, 23 comments, still unresolved
- Why mobile browsers lack the audio processing power and API access
- What this means for the "spatial" in WebXR
- Guest talking points: @brandonpjones and @jkarmer (omnitone team at Google Chrome) on the mobile rendering challenge and plans

**3. The Spec Gap — WebXR Has No Spatial Audio API (8 min)**
- immersive-web/webxr #390 — open since 2018, still no spec progress
- Web developers are forced into proprietary extensions (Omnitone, Resonance Audio)
- The W3C Immersive Web Working Group's stance and what it would take
- Guest talking points: @cabanier (WebXR DOM overlays, visibility events)

**4. Spatial Audio at Scale — Why It Breaks Under Social Load (8 min)**
- Hubs-Foundation/hubs #1853 (30 comments), #2643 (30 comments), #5057 (24 comments)
- Spatial audio degrades under CPU load precisely when social presence matters
- Reference: [MixedReality-WebRTC #573](https://github.com/microsoft/MixedReality-WebRTC/issues/573) — ADM2 breaks with multiple audio outputs
- Guest talking points: @misslivirose (Hubs audio spatialization & accessibility lead)

**5. The Room That Doesn't Exist — ISM Reverberation and Perceptual Bugs (5 min)**
- [Spatial_Audio_Framework #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) — ISM RIR incorrect summing of bands
- A fundamental bug that invalidates room acoustics research built on this library
- Guest talking points: @crlandsc and @ali-vosoughi on spatialization algorithms

**6. Cross-Modal Perception — When Hearing Guides Seeing (5 min)**
- Auditory spatial cues processed faster and more reflexively than visual
- Implications for MR design priority: audio-first interfaces
- Reference: echolocation studies, spatial hearing research
- Guest talking points: @TheBarmaEffect on perception-first spatial audio engine design

**7. Closing — The 10-Year Wait (5 min)**
- omnitone #2 has been open for a decade. What does it tell us about the state of spatial audio on the web?
- Call to action: lobby the W3C Immersive Web WG for a spatial audio spec

### Pre-Recording Checklist
- [x] Review omnitone #2, webxr #390, hubs #1853/#2643/#5057
- [x] Review MixedReality-WebRTC #573, Spatial_Audio_Framework #55/#58
- [x] Reach out to leomccormack, Brandon Jones, jkarmer, BinWang28, misslivirose, TheBarmaEffect
- [ ] Confirm omnitone team member availability
- [ ] Prepare demo: binaural rendering comparison (with headphones!)
- [ ] Prepare Visual: HRTF performance diagram

---

## Episode 3 Script — "Interfaces Beyond the Flat Screen"

**Duration:** 50–65 min | **Format:** Interview + spatial UI walkthroughs

### Cold Open (2 min)
> *"A hologram appears in front of you. You reach out to touch it. Your fingers pass through. The hologram drifts. It sticks to your camera instead of staying where you placed it. Four years after the HoloLens launched, the fundamental problem of mixed reality — registration — remains unsolved. What are the limits of registering digital content to the physical world — and are they engineering problems or perceptual ones?"*

### Segments

**1. Registration ≠ Acceptance — Why Geometric Alignment Isn't Enough (10 min)**
- "Holograms sticking to camera" is not a rendering bug — it's a perceptual failure
- Reference: [MixedRealityCompanionKit #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — 18 comments on reprojection drift across network stacks
- Reference: [MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — SpectatorView calibration that works once and never twice (19 comments)
- Guest talking points: @fieldsJacksonG (Microsoft MRC assignee on both issues) on why calibration is fundamentally fragile

**2. The WebXR Wayfinding Crisis — Getting Lost in Immersive Space (8 min)**
- [webxr #992](https://github.com/immersive-web/webxr/issues/992) — 36 comments on content discoverability in immersive sessions
- [webxr #815](https://github.com/immersive-web/webxr/issues/815) — 41 comments on spec language precluding non-visual uses
- Both are fundamental to how humans navigate and orient in space
- Guest talking points: @ddorwin (XR accessibility contributor)

**3. Input Fragmentation — Controller, Gaze, Hand, or Stylus? (8 min)**
- MixedRealityToolkit #914 — a Meta Quest user requesting Microsoft's MX Ink stylus
- The ecosystem is converging at the hardware level without converging at the interface level
- Reference: MRTK #511 (vendor plugin architecture debate — high priority)
- Guest talking points: @keveleigh (MRTK lead) on the platform convergence vs. abstraction tension

**4. The VisionOS Revolution — Passthrough Quality as the New Fidelity Metric (10 min)**
- Apple Vision Pro passthrough: contrast, resolution, and latency limits
- SE(3) anchor stability in dynamic environments
- Reference: [IvanCampos/visionOS-examples](https://github.com/IvanCampos/visionOS-examples) (405★) — the most comprehensive visual record of spatial UI patterns
- Guest talking points: @IvanCampos on visionOS plane detection, hand tracking, and RealityKit shaders

**5. Perceptual Performance — Dynamic Foveation and Visibility Masking (8 min)**
- The brain's foveal resolution is much higher than peripheral — why render what you don't see?
- Reference: [webxr #1420](https://github.com/immersive-web/webxr/issues/1420) — dynamic foveation (AdaRoseCannon, W3C Foveated Rendering CG)
- WebXR samples #228/#231/#235 — projection-layer rendering artifacts
- Guest talking points: @AdaRoseCannon on foveation as a perceptual-performance lever

**6. Neuroadaptive MR — When Interfaces Read Your Brain (5 min)**
- OpenGalea (MIT Reality Hack Meta winner): 8-channel EEG + Quest 3 for brain-controlled MR
- Attention/relaxation-driven spatial interfaces — the next frontier?
- Reference: [Caerii/OpenGalea](https://github.com/Caerii/OpenGalea) — Team Syncer
- Guest talking points: S. Hussain Ather (Team Syncer) on neuroadaptive interfaces

**7. The MR Documentation Gap — We Can't Reproduce What We Can't Document (4 min)**
- MRTK #987 — even Microsoft can't document HoloLens 2 mixed reality capture
- If researchers can't reproduce experiments, how do we build on previous work?
- Guest talking points: @chrisfromwork (Microsoft MRC)

### Pre-Recording Checklist
- [x] Review MRC #221, MRC #228, webxr #815/#992
- [x] Review MRTK #914, #987, #511, webxr #1420
- [x] Reach out to fieldsJacksonG, keveleigh, IvanCampos, AdaRoseCannon, Team Syncer, chrisfromwork
- [ ] Confirm MRTK maintainer and Ivan Campos availability
- [ ] Prepare demo: webxr-samples projection-layer artifacts
- [ ] Prepare Visual: registration drift diagram (before/after correction)

---

## Guest Outreach Tracker — September 2026

| Guest | Episode | Contact Method | Status | Notes |
|-------|---------|---------------|--------|-------|
| @leinardi | 1 | GitHub DM / email | 🟡 Contacted | SteamVR-for-Linux maintainer; latency expert |
| @jd-3d | 1 | GitHub DM | 🟡 Contacted | ALVR developer; "missing latency" researcher |
| @xytovl | 1 | GitHub DM | 🟢 To contact | WiVRn maintainer; OpenXR streaming |
| @jeromeetienne | 1, 3 | GitHub DM | 🟢 To contact | AR.js creator; web AR pioneer |
| @hiukim | 1, 3 | GitHub DM | 🟢 To contact | MindAR creator; TensorFlow.js AR |
| @leomccormack | 2 | Email | 🟢 To contact | Spatial_Audio_Framework creator; HRTF expert |
| @brandonpjones | 2 | GitHub DM | 🟢 To contact | omnitone team (Google Chrome) |
| @jkarmer | 2 | GitHub DM | 🟢 To contact | omnitone team (Google Chrome) |
| @Binwang28 | 2 | GitHub DM | 🟢 To contact | audio-ai-hub; HRTF research |
| @adacannon | 3 | W3C contact | 🟢 To contact | Dynamic foveation expert |
| @ikevovo | 1 | GitHub DM | 🟢 To contact | WebXR spec editor |
| @IvanCampos | 3 | Twitter/X | 🟢 To contact | visionOS-examples creator |
| @keveleigh | 3 | GitHub DM | 🟢 To contact | MRTK lead |
| @fieldsjacksong | 3 | Microsoft DM | 🟢 To contact | MRC hologram registration |
| @team-syncer | 3 | GitHub DM | 🟢 To contact | OpenGalea neuroadaptive MR |
| @misslivirose | 2 | GitHub DM | 🟢 To contact | Hubs-Foundation audio spatialization |
| @thebarmaeffect | 2 | Twitter/X | 🟢 To contact | Perception-first spatial audio engine |
| @edurnebernal | 2 | Email | 🟢 To contact | Audio-visual spatial perception |
| @ameliaeckard | 2 | Twitter/X | 🟢 To contact | Spatial audio for visual impairment