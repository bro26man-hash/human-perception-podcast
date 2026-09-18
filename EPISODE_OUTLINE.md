# 🎙️ The Future of Human Perception — Episode Outline

## Podcast Mission
Exploring the engineering and human science behind how technology reshapes perception — through deep-dive conversations with the developers and researchers building the future of AR, spatial computing, and mixed reality.

---

## Episode 1 — "Latency and the Perceptual Threshold"
**Status:** 🟡 Planned  
**Duration Target:** 45 min  
**Key Debate:** *Can foveation trick the brain into forgiving lag?*

### Core Topics
1. **Motion-to-Photon Latency & the 20ms Rule**
   - The neuroscience: why 20ms is the perceptual cliff for VR sickness
   - How AR.js and MindAR handle (or fail) real-time tracking latency on mobile
   - Google Lullaby's ECS architecture for sub-frame rendering pipelines

2. **Foveated Rendering as a Latency Hack**
   - fovea-based rendering pipelines (Tobii, Meta Quest Pro)
   - Can the brain's perceptual compression forgive inconsistent frame timing?
   - The trade-off: visual fidelity vs. subjective presence

3. **Tracking Latency in Web AR**
   - MindAR issue #428: *"switching phone orientation makes detection terrible"* — a real-world case study in perceptual lag (https://github.com/hiukim/mind-ar-js/issues/428)
   - AR.js NFT tracking (issue #544): 27-comment debate on natural feature tracking latency vs. marker-based approaches
   - The gap between promising specs and on-device reality

4. **The Future: Predictive Tracking & Neural Rendering**
   - Machine-learning-assisted motion prediction (MediaPipe, TrueDepth)
   - How will the next-gen WebXR API address latency at the protocol level?

### 🎤 Potential Guests
- **Jerome Etienne** (@jeromeetienne) — Creator of AR.js, pioneer of Web AR  
- **Nicolò Carpignoli** (@nicolocarpignoli) — AR.js maintainer, community organizer  
- **Hiukim** (@hiukim) — MindAR creator, solo developer fighting for open Web AR  
- **Google Lullaby team** — C++ VR/AR engineers behind spatial audio + rendering stacks  
- **Tobii Spatial Computing team** — foveated rendering experts  

### 📚 GitHub Research Backbone
- [AR.js Issue #469 — "Ensure the future of AR.js"](https://github.com/jeromeetienne/AR.js/issues/469) (94 comments, 22 👀, labeled `critical`) — The sustainability debate that underpins all open-source AR latency improvement
- [AR.js Issue #544 — "NFT (Natural Feature Tracking) on AR.js"](https://github.com/jeromeetienne/AR.js/issues/544) (27 comments) — Tracking accuracy vs. latency tradeoffs
- [MindAR Issue #428 — "switching phone orientation makes detection terrible"](https://github.com/hiukim/mind-ar-js/issues/428) (3 comments, 2 👀) — Real user experiencing perceptual latency in orientation tracking
- [MindAR Issue #537 — "Render the rest of the A-Frame Scene outside the MindAR Target"](https://github.com/hiukim/mind-ar-js/issues/537) — MR compositing and latency in mixed environments
- [Google Lullaby README](https://github.com/google/lullaby) — Spatial audio + ECS architecture documentation

### 🎬 Segment Structure
| Segment | Time | Focus |
|---|---|---|
| Cold Open | 3 min | "Have you ever felt nauseous in VR? That's 20ms failing you." |
| The Neuroscience of Latency | 10 min | How the brain constructs presence — and where it breaks |
| The Engineering Reality | 15 min | What AR.js, MindAR, and Lullaby actually achieve on-device |
| The Debate: Foveation vs. Full Rendering | 10 min | Is the brain the final renderer? |
| Future Gazing | 7 min | Neural rendering, predictive tracking, WebXR next-gen |
| Checkout | 3 min | Links, credits, next episode teaser |

### 📝 Pre-Recording Tasks
- [ ] Interview Jerome Etienne on AR.js origins and the 60fps promise
- [ ] Review MindAR's KnownIssues.md for documented latency caveats
- [ ] Pull Google Lullaby's spatial audio design docs
- [ ] Reference WebXR spec's latency-relevant sections
- [ ] Prepare foveated rendering demo clips

---

## Episode 2 — "Spatial Sound and the Third Dimension"
**Status:** 🟡 Planned  
**Duration Target:** 45 min  
**Key Debate:** *Why is the WebXR spec still visual-only for spatial audio?*

### Core Topics
1. **HRTFs and the Head-Related Transfer Function Mystery**
   - How HRTFs create the illusion of 3D sound from 2D drivers
   - Personalized vs. generic HRTFs — does your ear shape matter?
   - The "precultural" problem: most HRTF research uses Western candidates

2. **Ambisonics & Spatial Audio Rendering**
   - B-format ambisonics as the standard for VR/AR
   - Real-time ambisonic decoding on mobile (GPU constraints)
   - The gap between cinematic spatial audio and interactive AR audio

3. **The WebXR Audio Gap**
   - WebXR spec focuses on visual rendering; spatial audio is left to implementation
   - Google Lullaby fills this gap internally (used by VR Home, YouTube, Play Movies)
   - But the open-source community has no consensus spatial audio API for the web

4. **The Audio Presence Paradox**
   - Why do we trust what we hear more than what we see in VR?
   - Auditory illusions that break presence faster than visual ones
   - Cognitive science of sound-based spatial orientation

### 🎤 Potential Guests
- **Google Lullary audio engineers** — Spatial audio architects behind Material VR
- **Josh McDermott (MIT)** — Auditory perception researcher, computational acoustics  
- **Andreas Sabelfeld (KTH)** — HRTF personalization and spatial audio rendering  
- **WebXR working group members** — Spec authors who can speak to the audio gap  
- **Resonance Audio / SLAM engineers** — Google's spatial audio SDK team  

### 📚 GitHub Research Backbone
- [Google Lullaby — Spatial Audio in ECS Architecture](https://github.com/google/lullaby) (C++ spatial audio support, used across Google VR products)
- [WebXR Immersive Web Working Group](https://www.w3.org/immersive-web/) — Spec gaps in spatial audio rendering
- MindAR's lack of any spatial audio integration (source of the "visual-only" critique)

### 🎬 Segment Structure
| Segment | Time | Focus |
|---|---|---|
| Cold Open | 3 min | Close your eyes. You can"t navigate a room you can"t hear. |
| The Science of HRTF | 12 min | How your head shapes sound — and why one size doesn"t fit all |
| The Engineering Challenge | 12 min | Real-time ambisonics on a phone — brutal constraints |
| The WebXR Gap | 10 min | Why the spec left audio behind — and who's fixing it |
| The Presence Paradox | 8 min | When sound lies more than sight |
| Checkout | 3 min | Next episode teaser |

### 📝 Pre-Recording Tasks
- [ ] Request comment from WebXR working group on audio spec status
- [ ] Study Lullaby's spatial audio module source code
- [ ] Prepare HRTF demo clips (personalized vs. generic)
- [ ] Interview a cognitive scientist on auditory dominance in VR

---

## Episode 3 — "Interfaces Beyond the Flat Screen"
**Status:** 🟡 Planned  
**Duration Target:** 50 min  
**Key Debate:** *Is the WebXR spec blind to non-visual perception?*

### Core Topics
1. **MR Interface Design & the Compositing Problem**
   - How do you blend virtual content with the real world seamlessly?
   - MindAR issue #537: "Render the rest of the A-Frame Scene outside the MindAR Target" — a microcosm of the MR compositing challenge
   - Passthrough vs. content-first: two philosophies that can't agree

2. **Hologram Drift & Registration Error**
   - Why do virtual objects "slide" when you move your head?
   - 6DoF tracking vs. 3DoF: the perceptual difference that matters
   - Cement drift and anchor persistence in AR spaces

3. **Hand Tracking & Natural Interfaces**
   - The illusion of hands: how pinch gestures fool (and fail) the brain
   - MindAR issue #527: "Can track multiple faces on face-tracking?" — multi-user MR interface challenges
   - The gap between "quarterly demo" hand tracking and daily-use reliability

4. **Wayfinding & Spatial Cognition in MR**
   - How do humans navigate mixed environments?
   - Cognitive load of AR wayfinding prompts
   - The "annotated world" paradox: more info can mean less understanding

5. **The WebXR Blind Spot: Non-Visual Channels**
   - Haptics, proprioception, and the forgotten senses in XR specs
   - Material VR's widget system — visual-only UI in spatial environments
   - What would a truly multi-sensory WebXR look like?

### 🎤 Potential Guests
- **Microsoft MRTK team** — Mixed Reality Toolkit architects  
- **Hiukim** (@hiukim) — On MR compositing challenges and front-camera AR limitations (MindAR issue #539)  
- **Marco6ocram** — MindAR contributor working on scene compositing outside tracking targets  
- **Blitzy** — MindAR contributor who decoupled ThreeJS from the AR engine (issue #104)  
- **Spatial computing researchers from Meta Reality Labs** — Point cloud tracking and holographic display teams  

### 📚 GitHub Research Backbone
- [MindAR Issue #526 — "Is this repo abandonware?"](https://github.com/hiukim/mind-ar-js/issues/526) (13 comments, 3 👀) — The sustainability question that mirrors the industry's MR interface standardization gap
- [MindAR Issue #537 — "Render the rest of the A-Frame Scene outside the MindAR Target"](https://github.com/hiukim/mind-ar-js/issues/537) — MR compositing design challenge
- [MindAR Issue #527 — "Can track multiple faces on face-tracking?"](https://github.com/hiukim/mind-ar-js/issues/527) — Multi-user MR interface scalability
- [MindAR Issue #539 — "Front camera image tracking"](https://github.com/hiukim/mind-ar-js/issues/539) — Environmental occlusion and MR realism
- [MindAR Issue #104 — "Decouple ThreeJS from MindAR"](https://github.com/hiukim/mind-ar-js/issues/104) (18 comments) — Architecture choices affecting MR interface flexibility
- [Microsoft MRTK-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) (6.1k ⭐) — Enterprise MR interface patterns

### 🎬 Segment Structure
| Segment | Time | Focus |
|---|---|---|
| Cold Open | 4 min | "Your AR app knows where your face is. Does it know where you are?" |
| The Compositing Crisis | 12 min | Why mixing real and virtual is harder than it looks |
| Hologram Drift | 10 min | The uncanny feeling of things that won't stay put |
| Hands That Aren't There | 10 min | Hand tracking's perception problem |
| Wayfinding in the Blend | 8 min | Lost in the augmented world |
| Beyond Vision | 9 min | What about sound, touch, and balance in XR? |
| Checkout | 4 min | Series outlook + community call-for-guests |

### 📝 Pre-Recording Tasks
- [ ] Comment on MindAR issue #537 to connect with marco6ocram
- [ ] Reach out to Blitzy about MR interface architecture decisions
- [ ] Review MRTK-Unity's spatial UX guidelines
- [ ] Prepare side-by-side clips: passthrough vs. content-first MR demos
- [ ] Draft a "non-visual WebXR" manifesto snippet for the episode

---

## 🗓️ Episode Production Calendar

| Milestone | Episode 1 | Episode 2 | Episode 3 |
|---|---|---|---|
| Research Complete | ✅ | 🔲 | 🔲 |
| Guest Confirmed | 🔲 | 🔲 | 🔲 |
| Script Draft | 🔲 | 🔲 | 🔲 |
| Demo Clips Ready | 🔲 | 🔲 | 🔲 |
| Recording | 🔲 | 🔲 | 🔲 |
| Edit & Master | 🔲 | 🔲 | 🔲 |
| Publish | 🔲 | 🔲 | 🔲 |

## 🤝 How to Contribute

1. **Pick an episode issue** (see Issues #113, #114, #115 in this repo)
2. **Add research findings, issue links, or guest suggestions** as comments on the issue
3. **Submit a PR** with updated outlines, demos, or transcripts
4. **Tag potential guests** and track outreach status in the issue comments
5. **Flag new GitHub debates** — when you find a hot issue in AR.js, MindAR, or Lullaby, add it to the research audit

## 📡 Repository Audit — Live GitHub Tracker

See [`GITHUB-RESEARCH-ADDENDUM.md`](./GITHUB-RESEARCH-ADDENDUM.md) for the full, continuously updated audit of:
- Top AR/MR/Spatial Computing repos (stars, activity, maintenance status)
- Key contributors and maintainers to potentially invite
- Hottest open issues organized by perceptual theme
- Debate threads with direct links and comment cherry-picks
