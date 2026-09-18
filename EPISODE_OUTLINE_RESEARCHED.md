# 🎙️ The Future of Human Perception — Episode Outline (Research-Backed)

> **Production Hub:** [bro26man-hash/human-perception-podcast](https://github.com/bro26man-hash/human-perception-podcast)
> **Last Researched:** September 2026 | **Source Repos:** AR.js, Unity AR Foundation, Meta Quest Unity-Discover, Google Lullaby, mind-ar-js

---

## 📡 Season 1: The Perceptual Stack

This season traces the full perceptual pipeline — from the sensors that capture the world, through the pipelines that compute our place in it, to the displays and speakers that deliver synthesized reality back to our brains.

---

### 🎧 Episode 1 — "Latency and the Perceptual Threshold"

**Premise:** What is the hardest engineering limit in spatial computing, and why is the human brain the final judge?

**Core Debate:** *Can foveation and predictive rendering trick the brain into forgiving lag — or is the 20ms motion-to-photon ceiling a hard biological wall?*

| Slot | Topic | Detail |
|---|---|---|
| Cold Open | The Dubai AR Sandbox | Why AR.js location-based AR still fails at city scale (Issue #833) |
| Segment 1 | The 20ms Rule | Motion-to-photon latency, vestibulo-ocular reflex, and cybersickness thresholds |
| Segment 2 | Foveated Rendering | Eye-tracking + variable rate shading: can we render less and feel more? |
| Segment 3 | Predictive Tracking | Kalman filters and neural prediction — is the future pre-rendered? |
| Deep Dive | iOS AsyncOperation Slowdown | Unity AR Foundation Issue #1113 — 16+ comments on frame drops that break presence |
| Guest Bench | **Jerome Etienne** (AR.js creator), **Unity XR Team**, **Meta Quest Engineers**, **Salman Khan** (Spatial Computing) |
| Closing Angle | The Brain as the Final Heresy | Every optimization is ultimately a negotiation with neurons that evolved for a different world |

**GitHub Evidence:**
- [Unity AR Foundation #1113 — iOS massive slowdown with AsyncOperation](https://github.com/Unity-Technologies/arfoundation-samples/issues/1113) (16 comments — performance/perceptual latency)
- [Unity AR Foundation #1206 — Camera feed extreme lag after 6.0→6.1 upgrade](https://github.com/Unity-Technologies/arfoundation-samples/issues/1206) (9 comments — pipeline regression impact on presence)
- [Unity AR Foundation #615 — ARKit TrueDepth front-facing depth map](https://github.com/Unity-Technologies/arfoundation-samples/issues/615) (21 comments — face tracking latency for MR avatars)
- [AR.js #833 — Markerless AR for entire city territory](https://github.com/jeromeetienne/AR.js/issues/833) (GPS + visual simultanetic localization limits)

**Topic Clusters:**
- Motion-to-photon latency budgets and the 20ms myth
- Foveated rendering: technical feasibility and perceptual有效性
- Predictive tracking and the "brain cheat" hypothesis
- Frame drops as presence killers — empirical evidence from AR Foundation bugs
- WebXR latency: can the browser ever be fast enough?

**Open Questions for Show Notes:**
1. Is 20ms truly a hard limit, or do studies show adaptation over time?
2. Does foveated rendering add latency that cancels out its bandwidth savings?
3. How doQuest 3's passthrough latency compare to optical see-through?

---

### 🔊 Episode 2 — "Spatial Sound and the Third Dimension"

**Premise:** We can render worlds visually, but why does spatial audio still feel like a miracle — and a failure?

**Core Debate:** *Why is the WebXR specification still visual-only for spatial audio, and can HRTFs ever be personalized enough to fool the human auditory cortex?*

| Slot | Topic | Detail |
|---|---|---|
| Cold Open | The Missing Frequency | Why your headphones can't tell a bird is 2 meters above you |
| Segment 1 | HRTF Science | Head-related transfer functions, spectral cues, and the sonic fingerprint of your head |
| Segment 2 | Ambisonics & Object-Based Audio | Higher-order ambisonics vs. point-based rendering in MR |
| Segment 3 | The WebXR Audio Gap | Why `<embed>` Type: "immersive" considers only visual modes |
| Deep Dive | Meta Quest Spatial Audio | How Oculus rebuilt audio for passthroughMR — and what WebXR should borrow |
| Guest Bench | **Spatial Audio Researchers (Meta/Disney)**, **Immersive Web WG Members**, **Google Resonance Audio Team**, **Aalto University Psychoacoustics Lab** |
| Closing Angle | Hearing is Believing | Vision dominates, but spatial audio is the subconscious trust layer — and we barely have it |

**GitHub Evidence:**
- [WebXR Spec](https://github.com/immersive-web/webxr) — No spatial audio API in current specification (visual-only `immersive-vr` / `immersed-ar` modes)
- [Unity AR Foundation #992 — ARKit environment probes wrong rotation](https://github.com/Unity-Technologies/arfoundation-samples/issues/992) (Spatial mapping errors that break audio anchoring)
- [Meta Quest Unity-Discover samples](https://github.com/oculus-samples/Unity-Discover) — Passthrough + Spatial Anchors API (audio anchoring challenges)
- [Google Lullaby #13 — Build system issues](https://github.com/google/lullaby/issues/13) (VR/audio build complexities flagging maintenance gaps)

**Topic Clusters:**
- HRTF personalization: why one-size-fits-all spatial audio sounds wrong
- Ambisonics vs. audio objects in mixed reality
- The WebXR音频盲区: why spatial audio is missing from the spec
- Acoustic environment modeling (room size, materials, occlusion)
- The "presence paradox": convincing visuals + bad audio = uncanny valley?

**Open Questions for Show Notes:**
1. Can personalized HRTFs be generated from a single photo?
2. Will neural audio codecs replace HRTFs entirely?
3. Is silence the most powerful spatial audio tool (avalanche audio)?

---

### 🕶️ Episode 3 — "Interfaces Beyond the Flat Screen"

**Premise:** We've spent 30 years optimizing for 2D pointers. What happens when the interface is the world itself?

**Core Debate:** *Is the WebXR spec blind to non-visual perception — and are MR interfaces doomed to suffer from hologram drift and wayfinding failures?*

| Slot | Topic | Detail |
|---|---|---|
| Cold Open | The Hand That Failed | Why hand tracking in AR still feels like talking to a broken waiter |
| Segment 1 | Hologram Drift | When virtual objects slowly migrate — and why your brain notices before you do |
| Segment 2 | Wayfinding in MR | Spatial anchors, geo-localized content, and the cognitive load of "where am I?" |
| Segment 3 | Non-Visual Interfaces | Haptic feedback, proprioceptive design, and the forgotten senses |
| Deep Dive | MRTK vs. AR Foundation | Microsoft's Mixed Reality Toolkit vs. Unity's cross-platform approach |
| Guest Bench | **Microsoft MRTK Team**, **Apple Vision Pro Engineers (backchannel)**, **Oculus/Meta UX Researchers**, **Evan Stewart (Vision Pro spatial UI)** |
| Closing Angle | The World Is the Interface | The screen was always a crutch — and its removal is both liberation and terror |

**GitHub Evidence:**
- [Microsoft MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) (6.1k ⭐ — avatar systems, hand tracking,Chelsea eye tracking)
- [Unity AR Foundation #1107 — Need to destroy or restart ARTrackedImageManager?](https://github.com/Unity-Technologies/arfoundation-samples/issues/1107) (11 comments — anchor persistence and image tracking lifecycle)
- [Unity AR Foundation #1213 — Meta Quest 3 SceneCapture black background](https://github.com/Unity-Technologies/arfoundation-samples/issues/1213) (MR compositing pipelines)
- [Unity AR Foundation #1033 — Image tracking fails on iOS built on Windows](https://github.com/Unity-Technologies/arfoundation-samples/issues/1033) (Cross-platform MR interface fragility)

**Topic Clusters:**
- Hologram drift: physics vs. perception in persistent content
- Wayfinding: GPS vs. visual-inertial odometry vs. spatial anchors
- Hand tracking fidelity: 21-DoF vs. what the brain expects
- The "co-presence" problem: seeing others' hands in MR
- Non-visual MR: haptics, hearing, proprioception as interface channels
- Cross-platform MR: why ARKit + ARCore + OpenXR still can't agree on anchors

**Open Questions for Show Notes:**
1. Should MR interfaces have "persistence budgets" — how long can an anchor live before it feels wrong?
2. Can brain-computer interfaces bypass the hand entirely?
3. What does "spatial UI" mean for people who've never seen a screen?

---

## 🗺️ Bonus Episodes (Season 1 Considerations)

| # | Title | Trigger |
|---|---|---|
| B1 | "The WebXR Spec: A Love Letter to Incompleteness" | If WebXR community debates heat up |
| B2 | "Phone AR Is the Real AR: Why 2 Billion Devices Matter More Than Quest" | If AR.js mobile studies produce new data |
| B3 | "Sensory Substitution: Seeing with Sound, Hearing with Vibrations" | If neurodiversity perception research expands |

---

## 👤 Contributor & Guest Roster (Research-Backed)

| Name | Role | Repo Connection | Episode Fit |
|---|---|---|---|
| **Jerome Etienne** | Creator of AR.js | AR.js maintainer (@jeromeetienne) | Ep 1, Ep 3 — Web AR latency & city-scale anchoring |
| **Unity XR Team** | AR Foundation leads | arfoundation-samples maintainers | Ep 1, Ep 2 — Perceptual latency & spatial audio in engine |
| **Salman Khan** (salmanmkc) | Spatial Computing Developer | Prominent MR follower | Ep 1, Ep 3 — Cross-platform MR interfaces |
| **Meta Quest Engineering** | Passthrough & MR API leads | Unity-Discover samples | Ep 1, Ep 2 — Quest 3 perceptual pipeline |
| **Microsoft MRTK Team** | Mixed Reality Toolkit | MixedRealityToolkit-Unity | Ep 3 — Hologram drift & wayfinding |
| **Google AR Core Team** | ArCore SDK leads | google-ar/arcore-unity-sdk | Ep 2, Ep 3 — Spatial audio anchors & cross-platform |
| **Immersive Web WG** | WebXR spec editors | immersive-web/webxr | Ep 2 — Why spatial audio is missing from spec |
| **Aalto Psychoacoustics Lab** | HRTF research | Academic — no repo, but citations | Ep 2 — Personalized spatial audio |

---

## 🔥 Live Debate Tracker

| Debate | Source Repo | Open Issue | Sentiment |
|---|---|---|---|
| Is 20ms achievable on phone AR? | Unity AR Foundation | [#1113](https://github.com/Unity-Technologies/arfoundation-samples/issues/1113) — iOS frame drops | 🔴 Heated — 16 devs confirming perception-breaking lag |
| Does foveated rendering add net latency? | Meta Quest | #1213 — Quest 3 SceneCapture black screen | 🟡 Unresolved — engineering tradeoff community split |
| Should WebXR include spatial audio? | immersive-web/webxr | Spec has no audio input/output modes | 🔴 Active exclusion debate in WG |
| Can city-scale markerless AR work? | AR.js | [#833](https://github.com/jeromeetienne/AR.js/issues/833) — "entire territory of a city" | 🟡 GPS + VSLAM limits — no published solution |
| Are environment probes trustworthy? | Unity AR Foundation | [#992](https://Unity-Technologies/arfoundation-samples/issues/992) — Wrong rotation probes | 🔴 Confirmed bug — breaks spatial audio anchoring |
| Should anchors have expiration dates? | MRTK / AR Foundation | #1107 — ARTrackedImageManager lifecycle | 🟡 Persistent vs. fresh debate — no consensus |

---

## 📋 Production Checklist

- [ ] Confirm Episode 1 guest(s) —优先 Jerome Etienne or Unity XR leads
- [ ] Record Episode 1 raw audio (target: 45 min)
- [ ] Edit and add GitHub issue timestamps for listeners to click through
- [ ] Publish episode page with links to all cited GitHub issues
- [ ] Open GitHub Discussion for each episode's "Next Episode Vote"
- [ ] Tag contributors in issues for ongoing collaborative research

---

*This outline is living documentation. Pull requests welcome. Issues are the thread.*
*Last synthesized from GitHub research on AR.js, Unity AR Foundation, Meta Quest, Google Lullaby, and WebXR communities.*