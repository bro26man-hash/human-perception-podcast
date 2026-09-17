# 🎙️ The Future of Human Perception — Episode Outline
## Research-Backed Edition (GitHub-Sourced)

> This outline is grounded in live analysis of the most active AR/MR/Spatial Computing GitHub repositories and their open issues, debates, and contributor communities.

---

## 📋 Research Methodology

**Repositories surveyed:**
- `microsoft/MixedRealityToolkit-Unity` (6,076 ⭐) — Legacy MRTK v2, still actively patched
- `MixedRealityToolkit/MixedRealityToolkit-Unity` (550 ⭐) — MRTK v3, current generation
- `meta-quest/immersive-web-emulator` (463 ⭐) — WebXR runtime for desktop browser testing
- `needle-mirror/com.unity.xr.openxr` — OpenXR Unity plugin (Khronos standard)
- `needle-mirror/com.unity.xr.interaction.toolkit` — Unity XR Interaction Toolkit
- Vision Pro / spatial computing community repos (Swift, RealityKit, ARKit)

**Key contributors identified across repos:**
| Name | Role | Repos | Expertise |
|---|---|---|---|
| Kurtis | MRTK Maintainer | MRTK v2 & v3 | Core architecture, input system, debugging |
| Adam Mollis | MRTK Tech Lead (Microsoft) | MRTK v2 | Project management, XR integration, bug triage |
| David C. Kline | MRTK Audio Lead | MRTK v2 & v3 | Spatial audio, audio mixer, MS Spatializer plugin |
| Marlena Klein | MRTK Audio Engineer | MRTK v2 & v3 | Spatialization bugs, audio UX fixing |
| whebertML | MRTK3 Spatial Manipulation | MRTK v3 | Object manipulation, hand interaction, MR UX |
| keveleigh | MRTK3 Core/Input | MRTK v3 | Input system, XRI 3.0 migration, profiles |
| Felix Zhang (fe1ix) | Meta Immersive Web Lead | immersive-web-emulator | WebXR runtime, Quest emulation, AR module |

---

## 🎧 Episode 1 — "Latency and the Perceptual Threshold"

**Focus:** Motion-to-photon latency, the 20ms rule, and whether foveation rendering can trick the brain into forgiving lag.

**GitHub-Sourced Debate Topics:**

### 🔥 Hot Issues from MRTK Repos
1. **MRTK2 #8897** — *"MRTK.update() takes 10-15 ms using HoloLens 2 default profile while a hand is in view"*
   - Labels: Performance, Bug, Won't Fix
   - 9 comments; reported by `darax`
   - Core question: Is the per-frame iteration cost of MRTK's update loop pushing past the perceptual latency budget?

2. **MRTK2 #11256** — *"[2021 + URP Perf] Facing Performance issue after upgrading MRTK SDK to 2.8.2 with Unity OpenXR"*
   - Labels: Performance, Blocking, Platform - OpenXR, MRTK3, MRTK2
   - 9 comments; reported by `AmitBagada118`
   - Core question: Does the OpenXR pipeline introduce hidden latency overhead compared to the legacy Windows XR plugin?

3. **MRTK3 #304** — *"Very low performance after publishing with MRTK3 default configuration"*
   - Labels: Bug, Performance
   - Assigned to `david-c-kline`; 6 comments
   - Core question: Are MRTK3's zero-allocation claims holding up in real-world builds, or is there hidden GC pressure?

4. **MRTK3 #284** — *"Refactor smoothing to be less 'bad'"* (OPEN)
   - Labels: Feature Request
   - 6 comments
   - Core question: Is the current interpolation/smoothing algorithm in MRTK3 introducing perceptible judder that violates the 20ms motion-to-photon rule?

5. **MRTK2 #5097** — *"Make hand mesh rendering more performant"*
   - Labels: Feature Request, Performance, Won't Fix
   - Assigned to `Troy-Ferrell`; 3 comments
   - Core question: Hand mesh rendering cost — is it eating into the frame budget and causing perceptible latency?

### 🔬 Perceptual Science Topics for Discussion
- The 20ms motion-to-photon threshold: origins and validity
- Foveated rendering as a latency mitigation strategy
- Latency vs. jitter: which matters more for presence?
- The "vestibular-visual conflict" and motion sickness
- How does the human perceptual system compensate for latency?
-。人 Conflict between predicted and actual sensory feedback

### 🎤 Potential Guests
- **Kurtis** (MRTK Maintainer) — On the engineering challenge of hitting 20ms in MRTK's update loop
- **david-c-kline** (MRTK Audio Lead) — On the hidden latency introduced by spatial audio processing
- **Felix Zhang** (Meta IWE Lead) — On how WebXR emulation reveals latency problems invisible on-device
- **Adam Mollis** (MRTK Tech Lead) — On the Windows XR vs. OpenXR latency trade-offs

### 📚 Reading List (from GitHub issues & linked resources)
- MRTK Diagnostics system (for frame timing analysis)
- Unity Profiler + MRTK Optimize Window workflow
- "Motion-to-Photon Latency in VR" — OSTI report
- MRTK2 #8897 issue thread on hand-tracking frame budget

---

## 🎧 Episode 2 — "Spatial Sound and the Third Dimension"

**Focus:** HRTFs, ambisonics, the audio presence paradox, and why WebXR's spatial audio support is still incomplete.

**GitHub-Sourced Debate Topics:**

### 🔥 Hot Issues from MRTK Repos
1. **MRTK2 #11176 / MRTK3 #237** — *"Spatialized audio is inaudible"*
   - Labels: Bug, Spatial Sound / Audio, MRTK3
   - Assigned to `marlenaklein-msft`; 3 comments
   - Core question: Is MRTK's spatial audio pipeline broken by design, or are users misconfiguring the spatializer?

2. **MRTK2 #11349 / MRTK3 #197** — *"Default spatialization audio mixer throws errors when Microsoft Spatializer package is not installed"*
   - Labels: Bug, Spatial Sound / Audio
   - Assigned to `david-c-kline`; 1 comment
   - Core question: Should spatial audio fail gracefully, or is the dependence on the MS Spatializer plugin a design flaw?

3. **MRTK3 #181** (OPEN) — *"Update MRTK3 buttons and interactables to gracefully handle Spatializer Plugins that require an audio mixer"*
   - Labels: Feature Request
   - 1 comment
   - Core question: How do you design spatial audio UX when the underlying audio mixer architecture is fragmented across platforms?

4. **MRTK2 #8090** — *"AudioPluginMicrosoftSpatializer & Build Exceptions (dll's unloaded)"*
   - Labels: External
   - 5 comments; reported by `jasonhbartlett`
   - Core question: Platform-specific spatializer DLL conflicts — is spatial audio too Windows-centric for cross-platform MR?

5. **MRTK3 PR #11271** — *"Audio spatializer support part 1: configuration script and update spatializer"*
   - Author: `david-c-kline`; merged Dec 2022
   - Core question: What does a proper spatial audio configuration abstraction look like in MRTK3?

6. **MRTK3 PR #11681** — *"Removing MRTK3's SpatializationMixer property until usage is properly defined"*
   - Author: `AMollis`; merged Jul 2023
   - Core question: Is the spatial audio API surface too immature for MRTK3, and should it be hidden until ready?

### 🔬 Spatial Audio Science Topics for Discussion
- HRTF personalization: why one-size-fits-all spatial audio fails
- The "precedence effect" and how the brain localizes sound in space
- Ambisonics vs. HRTF: which paradigm better creates presence?
- The audio presence paradox: why bad spatial audio breaks immersion more than bad visuals
- WebXR's silence on spatial audio: is the spec ignoring the most important sense for presence?
- Sports venue audio: how spatial sound design shapes emotional perception
- Atmospheric acoustics: how reverb and early reflections create room presence

### 🎤 Potential Guests
- **david-c-kline** (MRTK Audio Lead) — On the engineering of spatial audio in MRTK3, and why the SpatializerMixer was removed
- **marlenaklein-msft** (MRTK Audio Engineer) — On fixing the "spatialized audio inaudible" bug and what it reveals about audio UX
- **Felix Zhang** (Meta IWE Lead) — On how WebXR's audio emulation gaps expose spec limitations
- Potential external researcher on HRTF personalization science

### 📚 Reading List (from GitHub issues & linked resources)
- MRTK3 `org.mixedrealitytoolkit.audio` package changelog
- Microsoft Spatializer plugin documentation
- MRTK2 #11176 issue thread on spatial audio inaudibility
- WebXR Audio Positioning spec draft (immersive-web working group)
- "The Missing Sense: Spatial Audio in MR" — research paper

---

## 🎧 Episode 3 — "Interfaces Beyond the Flat Screen"

**Focus:** MR interfaces, hologram drift, wayfinding, hand tracking, gaze interaction, and whether the WebXR spec is blind to non-visual perception.

**GitHub-Sourced Debate Topics:**

### 🔥 Hot Issues from MRTK Repos
1. **MRTK3 #88** (OPEN, 28 comments) — *"MRTK support for Apple VisionOS and Vision Pro"*
   - Labels: Type: Feature Request, Platform: Apple Vision Pro
   - 28 comments — **the most-commented open issue in MRTK3**
   - Core question: Can MRTK's cross-platform abstraction survive the Apple Vision Pro paradigm shift?

2. **MRTK3 #621** (OPEN, 19 comments) — *"[XRI3] ObjectManipulator support for XRSocketInteractor parameters 'Hover Socket Snapping' and 'Socket Scale Mode'"*
   - Labels: Feature Request, Package: Spatial Manipulation
   - Assignee: `whebertML`; 19 comments
   - Core question: Are current MR manipulation paradigms (grab, pinch, drag) sufficient, or do we need socket-based attachment for true spatial interaction?

3. **MRTK3 #82** (OPEN, 12 comments) — *"MRTK3 triggerPressed is overly sensitive"*
   - Labels: Type: Bug
   - 12 comments; reported by `IssueSyncBot`
   - Core question: Is the trigger pressure threshold calibrated for perceptual comfort, or is it causing "phantom grip" sensations?

4. **MRTK3 #645** (OPEN, 11 comments, Priority: High) — *"[XRI3] Update MRTK3 to support XRI 3.0"*
   - Labels: Feature Request, Package: Core, Package: Input
   - Assignees: `keveleigh`, `shaynie`, `david-c-kline`, `whebertML`, `ghazen-ml`, `ms-RistoRK`
   - Core question: Does the migration from MRTK's custom input system to Unity's XRI 3.0 introduce perceptual regressions?

5. **MRTK2 #9358** — *"ObjectManipulator should use a smoothing function that's better for noisy hand input"*
   - Labels: Bug, Won't Fix, UX Controls - ObjectManipulator
   - 2 comments; reported by `krampster`
   - Core question: How does hand-tracking noise affect the perception of object "physicality" in MR?

6. **MRTK2 #4311** — *"MRTK/Standard Shader Updates + Lightweight Scriptable Render Pipeline Support"*
   - 4 comments; by `Cameron-Micka`
   - Core question: Does the LWP/HDRP rendering pipeline choice affect how holograms are perceived as "real" vs. "virtual"?

7. **MRTK3 #41** (OPEN, 12 comments) — *"UI not usable while moving root transform (UI inside a moving vehicle)"*
   - Labels: Type: Bug
   - Core question: How does self-motion (vection) affect the usability and perception of MR interfaces?

### 🔬 MR Interface Science Topics for Discussion
- Hologram drift: why virtual objects "wander" and how it destroys presence
- Wayfinding in mixed reality: cognitive maps vs. arrow-based navigation
- Hand tracking fidelity: how much detail does the brain need to accept a virtual hand as "yours"?
- gaze-based interaction: the uncanny effect of being watched by an avatar
- MR interface design for accessibility: how spatial computing can include (or exclude) users with perceptual differences
- The " screen door effect" and how it perceived quality differs across displays
- Chromatic aberration and how it affects the perception of virtual object boundaries

### 🎤 Potential Guests
- **whebertML** (MRTK3 Spatial Manipulation) — On socket-based interaction and the future of MR manipulation UX
- **keveleigh** (MRTK3 Core/Input) — On the XRI 3.0 migration and its perceptual implications
- **Felix Zhang** (Meta IWE Lead) — On how the immersive-web emulator reveals Vision Pro vs. Quest interaction paradigm differences
- **Adam Mollis** (MRTK Tech Lead) — On the Apple Vision Pro challenge: can one toolkit serve all MR platforms?
- Potential external researcher on MR interface perception and vection

### 📚 Reading List (from GitHub issues & linked resources)
- MRTK3 Spatial Awareness system documentation
- Unity XR Interaction Toolkit 3.0 migration guide
- MRTK3 #88 issue thread on Vision Pro support (28 comments of rich debate)
- "Hologram Drift and Presence in Mixed Reality" — research literature
- Apple Vision Pro spatial computing design guidelines

---

## 🗺️ Future Episode Pipeline (Research-Backed)

| # | Working Title | Primary Repos to Monitor | Key Debates to Track |
|---|---|---|---|
| 4 | "The Social Body in Virtual Space" | Hubs-Foundation/hubs, meta-quest/immersive-web-emulator | Avatar embodiment, proxy perception, social presence metrics |
| 5 | "Architectural Acoustics for the Digital World" | webaudio/web-audio-api, AudioKit/AudioKit | Room simulation, early reflections, perceptual quality of algorithmic reverb |
| 6 | "Foveated Rendering and the Brain's Budget" | nreal/nreal-light, PimaxReality | Variational foveation, flicker fusion threshold, peripheral awareness |
| 7 | "The Ethics of Perceptual Manipulation" | W3C/immersive-web, KhronosGroup/OpenXR | Dark patterns in XR, consent for sensory modification, accessibility as a design constraint |

---

## 📌 How to Use This Outline

1. **Pick an episode issue** (#1, #2, or #3) — each is pre-seeded with the GitHub research below
2. **Add findings** as comments on the issue — link specific issues, PRs, and contributors
3. **Propose guests** — tag contributors found in the research and track outreach status
4. **Submit PRs** to update the outline when new GitHub debates emerge

## 🔗 Key GitHub Links

- [MRTK v2 Issues](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)
- [MRTK v3 Issues](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues)
- [MRTK v3 #88: Vision Pro Support (28 comments)](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/88)
- [MRTK v3 #284: Refactor smoothing (OPEN)](https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/284)
- [MRTK v2 #8897: MRTK.update() 10-15ms (Performance)](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8897)
- [MRTK v2 #11176: Spatialized audio inaudible](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11176)
- [immersive-web-emulator (Meta Quest WebXR)](https://github.com/meta-quest/immersive-web-emulator)
- [WebXR Device API Spec](https://immersive-web.github.io/webxr/)
- [Unity XR Interaction Toolkit](https://github.com/Unity-Technologies/XR-Interaction-Toolkit)
- [OpenXR Standard (Khronos)](https://www.khronos.org/openxr/)
