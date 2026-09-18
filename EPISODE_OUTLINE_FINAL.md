# 🎙️ The Future of Human Perception — Episode Outline

> **Collaborative production document** for the podcast series exploring how technology reshapes human perception through AR, spatial computing, and mixed reality.

---

## 📌 Series Overview

**Mission:** Explore the engineering and human science behind how technology reshapes perception — by digging into the *actual open debates* happening in the most active GitHub repositories across the AR/MR/Spatial Computing ecosystem.

**Format:** 45–60 min episodes, each anchored to a live GitHub issue or debate, with guest contributors who are actively writing the code.

**Production Repo:** [bro26man-hash/human-perception-podcast](https://github.com/bro26man-hash/human-perception-podcast)

---

## 🎧 Episode 1 — "The Web AR Revolution & the 20ms Gap"

**Core Question:** Can the web deliver AR experiences fast enough to trick the brain, and where does the perceptual threshold actually lie?

| Field | Detail |
|---|---|
| **Focus Topics** | Motion-to-photon latency, foveated rendering, WebXR performance budgets, AR.js tracking pipeline latency |
| **Anchor Debate** | AR.js issue #822 (THREE.math rename breaks location-based logic) & #826 (ImageTracking demo doesn't work) — how do tracking pipeline breaks erode perceptual presence? |
| **Guest Pros** | **Jerome Etienne** (@jeromeetienne) — Creator of AR.js; **Nicolò Carpignoli** (@nicolocarp) — AR.js org maintainer; **Hiukim** (@hiukim) — MindAR creator (TensorFlow.js-based tracking) |
| **Related Repos** | AR-js-org/AR.js (5.9k ⭐), hiukim/mind-ar-js (2.7k ⭐), jeromeetienne/AR.js (15.8k ⭐, archived) |
| **Reading List** | AR.js docs: https://ar-js-org.github.io/AR.js-Docs/; MindAR repo; WebXR Device API spec — `depth-sensing` & `light-estimate` sections |
| **Key Talking Points** | ① Why marker-based tracking has different latency profiles than markerless/NFT tracking ② How the 20ms motion-to-photon rule applies (or doesn't) to AR vs VR ③ What foveated rendering could mean for mobile WebAR ④ The philosophical question: if tracking jitters by 50ms, does the brain "snap" to it or reject it? |

---

## 🎧 Episode 2 — "Gaussian Splatting & the New Spatial Data Format"

**Core Question:** Is 3D Gaussian Splatting the future of perceptual fidelity in AR — or just a pretty shortcut that collapses under real-world conditions?

**Anchor Debate:** KhronosGroup/glTF KHR_gaussian_splatting extension (#2490, 225 comments; #2531 compression; #2563 log-space scale debate, 56 comments; #2564 anti-aliasing filter proposal)

| Field | Detail |
|---|---|
| **Focus Topics** | NeRF vs Gaussian Splatting, point-cloud vs splat rendering, perceptual compression trade-offs, log-space scale encoding, anti-aliasing in splat pipelines |
| **Anchor Debate** | glTF KHR_gaussian_splatting — Should scale be stored in log-space? (#2563) Should an anti-aliasing filter be specified? (#2564) Compression schema SPZ_2 (#2531) — 16 comments on bandwidth vs quality |
| **Guest Pros** | **Weegeekps** (@weegeekps) — glTF Gaussian Splatting extension author; **NorbertNopper-Huawei** — scale-space debate contributor; **tomas2211** — anti-aliasing filter proposer; **javagl** — glTF spec maintainer |
| **Related Repos** | KhronosGroup/glTF, google/lullaby (1.2k ⭐, spatial audio + ECS VR), facebook/immersive-web-sdk (357 ⭐, spatial UI) |
| **Reading List** | KHR_gaussian_splatting spec draft; Lullaby's spatial audio architecture; SplatForge reference implementation (#2580) |
| **Key Talking Points** | ① Why splatting is winning over NeRF for real-time AR (and where it loses) ② The log-space scale debate: is it a math choice or a perceptual one? ③ How compression affects perceived quality — can you "hear" the difference in a splat? ④ What anti-aliasing means when your "pixels" are probabilistic distributions ⑤ Will the glTF spec become the .jpg of 3D perception? |

---

## 🎧 Episode 3 — "Spatial Audio, Immersive Interfaces & the Missing Senses"

**Core Question:** If the WebXR spec is still visual-first, how do we build spatial audio and multi-sensory interfaces that feel *real* rather than *retrofitted*?

| Field | Detail |
|---|---|
| **Focus Topics** | HRTF implementation in browsers, ambisonics vs parametric spatial audio, ECS-driven audio (Lullaby), spatial UI interaction patterns, haptic-audio coupling |
| **Anchor Debate** | Facebook immersive-web-sdk exposes spatial audio as a core system — but the WebXR spec has no mandatory spatial audio depth-sensing; Google Lullaby's spatial audio architecture (used by YouTube VR, Earth, Play Store) — how do production teams bridge the gap? |
| **Guest Pros** | **Alan Popp** (Alan Blizzard / Alan Popp — spatial audio architect); **Theodore Ast** — Hubs/Meta spatial interfaces; **Simon Poulter** (@viralinfo) — mind-ar & A-Frame AR contributor; Lullaby sparse audio team |
| **Related Repos** | google/lullaby (1.2k ⭐ — spatial audio + ECS), facebook/immersive-web-sdk (357 ⭐ — spatial UI + locomotion), A-Frame/aframevr (WebXR baseline) |
| **Reading List** | Lullaby spatial audio docs; IWSDK spatial audio implementation; WebXR spec — ` Wallace` section on audio; HRTF personalisation research |
| **Key Talking Points** | ① The "audio presence paradox" — why poor spatial audio breaks presence faster than poor visuals ② Why the WebXR spec treats spatial audio as optional, and what that means for developers ③ Lullaby's ECS architecture: how entity-component systems can model auditory scenes ④ Haptic-audio coupling: can you "hear" a texture? ⑤ What does 6DoF audio mean for AR vs VR differently? ⑥ The perceivable latency difference between visual and auditory spatial updates — is audio more forgiving or less? |

---

## 🔬 Ongoing GitHub Research Audit

Each episode should reference **live issues and PRs** from the tracked repos. See `GITHUB-RESEARCH-ADDENDUM.md` for the full audit.

| Repo | Stars | Hottest Open Issues | Perceptual Angle |
|---|---|---|---|
| **AR-js-org/AR.js** | 5.9k | #833 (city-scale markerless AR), #826 (image tracking broken), #822 (THREE.math break) | Tracking latency & perceptual continuity |
| **google/lullaby** | 1.2k | #13 (build system), #14 (VectorPacked data) | Spatial audio architecture & ECS perception |
| **facebook/immersive-web-sdk** | 357 | Active PR pipeline, spatial UI <!-- --> | Interaction latency & spatial interface design |
| **KhronosGroup/glTF** | — | #2454 (Gaussian Splatting in glTF), #2563 (log-space scale), #2564 (anti-aliasing) | Splat fidelity & perceptual compression |
| **hiukim/mind-ar-js** | 2.7k | Feature requests for multi-face & face mesh | Face tracking as perceptual interface |

---

## 👥 Guest Contributor Pool

| Name | Handle | Expertise | Episode Fit |
|---|---|---|---|
| Jerome Etienne | @jeromeetienne | Web AR pioneer, AR.js creator | Ep 1, Ep 3 |
| Nicolò Carpignoli | @nicolocarp | AR.js maintainer, WebXR engineer | Ep 1 |
| Hiukim | @hiukim | MindAR creator, TensorFlow.js tracking | Ep 1 |
| Weegeekps | @weegeekps | glTF spec, Gaussian Splatting | Ep 2 |
| Simon Poulter | @viralinfo | A-Frame AR, mind-ar UI | Ep 1, Ep 3 |
| Alan Popp | (spatial audio architect) | HRTF, ambisonics, spatial mixing | Ep 3 |
| Theodore Ast | (spatial interfaces) | MR UI, Hubs, spatial design systems | Ep 3 |

---

## 📋 Episode Production Workflow

1. **Research Sprint** — Review live GitHub issues for the anchor repo; quote actual discussion threads
2. **Guest Outreach** — Tag prospective guests in issues or DM via Twitter/X
3. **Pre-Record** — Share episode outline with guest for comment
4. **Record** — 45–60 min, with screen-shared GitHub issue walkthroughs
5. **Post-Release** — Update this outline with timestamps, key quotes, and follow-up issue links

---

## 🔗 Key External Resources

- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [Immersive Web Working Group (W3C)](https://www.w3.org/immersive-web/)
- [AR.js Official Docs](https://ar-js-org.github.io/AR.js-Docs/)
- [glTF KHR_gaussian_splatting Draft](https://github.com/KhronosGroup/glTF/pull/2490)
- [Google Lullaby Documentation](https://github.com/google/lullaby/blob/master/g3doc/index.md)
- [Immersive Web SDK Docs](https://iwsdk.dev)
- [Mixed Reality Toolkit](https://aka.ms/mrtkdocs)

---

*Last updated: 2026-09-18 | Research backbone: GitHub issue audit of AR.js, Lullaby, IWSDK, glTF, MindAR*