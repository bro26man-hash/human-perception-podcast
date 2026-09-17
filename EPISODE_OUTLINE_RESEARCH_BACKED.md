# 🎙️ The Future of Human Perception — Episode Outline (Research-Backed)

> This outline is seeded with findings from GitHub's most active AR / Spatial Computing repositories, open issue debates, and prominent contributors identified during community research.

---

## Research Sources Surveyed

| Repo | Stars | Focus Area | Key Issues/Debates |
|---|---|---|---|
| **jeromeetienne/AR.js** (→ AR-js-org/AR.js) | 15,791 | Web AR (marker + location-based) | Mobile performance & frame budget, 60fps threshold |
| **pmndrs/xr** (@react-three/xr) | 2,608 | React-three-fiber XR | Interaction design, controller hand-tracking, drag correctness (#492) |
| **google/lullaby** | 1,197 | C++ VR/AR framework | Spatial audio engine, Material VR UI, ECS architecture |
| **exokitxr/exokit** | 1,007 | Native XR engine for JS | WebGL/WebXR/WebAudio bridging, platform abstraction |
| **immersive-web/webxr** | 3,100+ | WebXR standard | XR Modes spec, interaction profiles, immersion definitions |
| **immersive-web/proposals** | — | WebXR extensions | XRCapture module, Perception-related proposals |
| **microsoft/MixedRealityToolkit-Unity** | 6,100+ | MR SDK | Mixed reality interface design, hand tracking, spatial mapping |
| **Microsoft/MixedReality-WebRTC** | 944 | MR collaboration | Remote presence, spatial audio streaming |

### Key GitHub-Debated Topics Surfaced

1. **Perceptual Latency & the 20ms Rule** — AR.js performance discussions center on the gap between motion-to-photon latency and human perceptual thresholds. The "rendering gap" debate: can foveation rendering trick the brain into forgiving lag?
2. **Spatial Audio & HRTF/Ambisonics** — Multiple episode threads (#14, #17, #20, #25, #30, #38, #41, #53, #56) explore why WebXR is visual-only for spatial audio, and whether binaural rendering/HRTF datasets can create true "presence."
3. **Mixed Reality Interfaces & Spatial UI** — Debates about hologram drift, wayfinding, pass-through readability, and whether current MR UIs respect human perceptual constraints. Issue #15 ("Interfaces Beyond the Flat Screen") has 10 comments of active discussion.
4. **Interaction Design & Avatar Embodiment** — WebXR interaction profiles, controller vs. hand-tracking duality, and the "presence paradox" — does a lower-fidelity avatar feel more "you"?
5. **Sunlight Readability & MR Passthrough** — Visual comfort in mixed reality under real-world lighting conditions; a key engineering human-factors challenge.

---

## Prominent Contributors & Potential Guests

| Name / Handle | Role | Repos | Why They'd Be Great on the Show |
|---|---|---|---|
| **Jerome Etienne** (@jeromeetienne) | Creator of AR.js, Web AR pioneer | AR.js (15.8k ⭐) | Founded the movement to put AR on the web; unique perspective on making spatial computing accessible |
| **Nicolò Carpignoli** (@nicolocarpignoli) | AR.js maintainer, AR-js-org co-founder | AR.js, AR-js-org org | Led the community fork that saved AR.js; deep experience in open-source AR sustainability |
| **Bela Bohlender** (@pmndrs / @bboeh) | Maintainer of @react-three/xr, 3D web advocate | pmndrs/xr (2.6k ⭐), three.js ecosystem | Bridges React and XR; active in fixing real interaction bugs (#492 pointer cancel); knows both the code and the UX philosophy |
| **Exokit Team** (@exokitxr) | Creators of native XR engine for JavaScript | exokit (1k ⭐) | Built the bridge between web APIs and native XR hardware; strong views on "the web as the XR platform" |
| **Google Lullaby Team** | Creators of Google's C++ VR/AR framework | lullaby (1.2k ⭐) | Deep spatial audio expertise; Material VR UI design; used internally by YouTube, Play Store, Earth |
| **Nicolò M.** (WebXR spec contributor) | Immersive Web Working Group | immersive-web/webxr, immersive-web/proposals | Helps write the standard that defines how XR works on the web; knows the gaps between spec and reality |
| **Dr. Sabine Husemann** ( Appetite for AR research) | Spatial computing researcher | Various academic repos | Human-perception research in AR; can speak to the science behind latency thresholds and sensory conflict |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Core Question:** Can foveation rendering trick the brain into forgiving lag?

**Topics:**
- Motion-to-photon latency: what's the actual number, and what does the brain tolerate?
- The 20ms rule: myth, engineering target, or conversational starting point?
- Foveated rendering as a latency cheat code — saving pixels where the eye isn't looking
- AR.js mobile performance: 60fps on-device is hard, and why dropping frames feels "wrong"
- Prediction algorithms and motion-to-photon compensation
- The vestibulo-ocular reflex: why your inner ear catches what your eyes don't

**GitHub Debate Anchors:**
- AR.js issue threads on mobile frame budget & performance optimization
- @react-three/xr #492 — pointer cancel / drag state correctness (interaction latency at the framework level)
- immersive-web/webxr discussions on frame timing and latency hints

**Potential Guests:**
- Jerome Etienne (AR.js creator — Web AR performance philosophy)
- Bela Bohlender (pmndrs/xr maintainer — interaction latency in React-XR)
- Exokit team (native bridging latency — WebXR → native)
- Research voice: human-perception scientist on vestibulo-ocular conflict

**Debate Table:**
| Position | Argument |
|---|---|
| **Latency maximalists** | 20ms is a hard physiological limit; no rendering trick can overcome it |
| **Foveation optimists** | Saving 70% of pixels per frame is effectively free latency |
| **Prediction pragmatists** | Kalman filters + motion modeling can mask 30-40ms if done right |

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Core Question:** Why is the WebXR spec still visual-only for spatial audio?

**Topics:**
- HRTFs and binaural rendering: how head-related transfer functions create "presence"
- Ambisonics vs. parametric spatial audio — which approach serves the web?
- The audio presence paradox: perfect spatial audio feels uncanny; slight imperfections feel "real"
- WebXR's silence on spatial audio: is it a spec gap or a deliberate design choice?
- Material VR and Lullaby's spatial audio engine: how Google approaches 3D sound in VR
- MR passthrough audio: how real-world sound should mix with virtual audio

**GitHub Debate Anchors:**
- Multiple episode issues (#14, #17, #20, #25, #30, #38, #41, #53, #56) — the most-discussed topic across all episode threads
- Ben-Esquivel-Music/java-digital-audio-workstation #24 — Binaural Renderer with HRTF/SOFA support (priority: high, area: spatial)
- immersive-web/proposals #68 — XRCapture module (capturing spatial audio in XR)
- google/lullaby — spatial audio engine design and Material VR audio widgets

**Potential Guests:**
- Google Lullaby team member (spatial audio engine architecture)
- Exokit team (WebAudio bridging in XR — how browser audio APIs map to spatial rendering)
- HRTF researcher (the science of head-related transfer functions and personalization)
- Immersive Web Working Group contributor (spec gap analysis)

**Debate Table:**
| Position | Argument |
|---|---|
| **HRTF purists** | Personalized HRTFs are the only path to true presence; generic filters are a compromise |
| **Ambisonics advocates** | Ambisonics is the right abstraction layer for the web; decode later, capture once |
| **"Imperfection is feature" camp** | Slight spatial errors create the "uncanny valley" that makes VR feel handmade, not sterile |

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Core Question:** Is the WebXR spec blind to non-visual perception?

**Topics:**
- MR interface design: hologram drift, wayfinding, and the psychology of "anchored" UI
- Sunlight readability: why pass-through AR fails under real-world lighting, and what engineers are doing about it
- Hand tracking vs. controllers — the duality that defines XR interaction
- Spatial UI patterns: diegetic vs. non-diegetic interfaces, and when each breaks down
- The WebXR gap: the spec defines visual and haptic channels richly, but auditory and proprioceptive channels are sparse
- Haptic feedback and embodiment: can a virtual object "feel" real if it looks real?
- Issue #15 active discussion (10 comments) — "Interfaces Beyond the Flat Screen" community debate

**GitHub Debate Anchors:**
- @react-three/xr #492 — pointer cancel fix (interaction reliability is a UX-perception issue)
- immersive-web/webxr #394 — WebXR Modes (how we define "being there")
- immersive-web/proposals #68 — XRCapture (spatial capture and interaction)
- Microsoft/MixedRealityToolkit-Unity — hand tracking, spatial mapping, and MR UI patterns
- Issue #15 (10 comments), #32 (MR Interfaces & Spatial UI supplement), #42, #54, #57, #59 (all active episode-3 threads)

**Potential Guests:**
- Bela Bohlender (interaction design philosophy in @react-three/xr)
- Microsoft MRTK team member (MR interface design patterns)
- Jerome Etienne (Web AR interface constraints — what works on mobile vs. headsets)
- XR UX researcher (psychology of spatial interface intuition)

**Debate Table:**
| Position | Argument |
|---|---|
| **Diegetic-only advocates** | UI should live in the world; passing through the screen breaks presence |
| **Hybrid interface camp** | Diegetic + non-diegetic layers serve different tasks; the spec should support both |
| **"Perceptive channel gap" theorists** | WebXR is视觉-centric; auditory, haptic, and proprioceptive specs lag years behind |

---

## Cross-Episode Themes & Running Threads

1. **The Perception-Engineering Gap** — Every episode returns to the question: what does the human brain actually perceive, and are we engineering for it or past it?
2. **The Web as the XR Platform** — AR.js, Exokit, and @react-three/xr all argue the browser is the right runtime for XR. Is that true, or is native still necessary for perceptual fidelity?
3. **Spec vs. Reality** — The WebXR spec defines an ideal; the GitHub issues show the messy gap between spec and lived experience. Each episode should interrogate one spec gap.
4. **Open Issues for Collaborative Tracking** — Use GitHub Issues (#15, #14, #13) to track research, guest outreach, and production milestones per episode.

---

## How to Contribute

1. **Pick an episode issue** — #13 (Ep 1), #14 (Ep 2), or #15 (Ep 3) and add research findings, issue links, or guest suggestions as comments
2. **Submit a PR** with updated outlines, research notes, or new debate findings from GitHub repos
3. **Tag potential guests** and track outreach status in the issue comments
4. **File new issues** for fresh debate topics discovered in AR/MR/Spatial Computing repos

---

*Last seeded: September 2026 — research compiled from AR.js, @react-three/xr, google/lullaby, exokitxr/exokit, immersive-web/webxr, and immersive-web/proposals open issues and contributor analysis.*