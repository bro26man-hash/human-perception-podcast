# 🎙️ The Future of Human Perception — Definitive Episode Outline

> Synthesized from GitHub issue analysis across **AR.js** (15.8k ★), **MixedRealityToolkit-Unity** (6.1k ★), **Google Lullaby** (1.2k ★), and **Microsoft XR Development Curriculum** (564 ★).

---

## Episode 1: "Latency and the Perceptual Threshold"

**Core Question:** *Can foveation and predictive rendering trick the brain into forgiving lag — or is the 20ms motion-to-photon rule a hard biological limit?*

### Key Topics
| Topic | Source Repo | Relevant Issue | Status |
|---|---|---|---|
| Motion-to-photon latency & the 20ms rule | MRTK-Unity | #9358 — ObjectManipulator smoothing for noisy hand input | Open debate |
| Holographic remoting latency in VMs | MRTK-Unity | #9920 — Remoting fails under virtualization | Bug |
| Perceptual threshold research | Cross-repo | Academic literature onica-20ms rule | Research phase |
| Foveated rendering as latency mask | AR.js | Community discussions on mobile 60fps budget | Emerging |
| Frame budget management on mobile | AR.js | 60fps promise on resource-constrained devices | Core challenge |

### Hot Debate Snippets (from GitHub Issues)
- **MRTK #9358**: *ObjectManipulator should use a smoothing function that's better for noisy hand input* — Krampster flags that raw hand-tracking data introduces jitter that the brain perceives as "unreal" even at low latency.
- **MRTK #9920**: *Holographic Remoting with WindowsMR fails in virtual machines* — NoTuxNoBux surfaces a fundamental tension: cloud-rendered MR introduces_latency that the perceptual system rejects.
- **AR.js**: The 60fps-on-mobile promise creates a frame budget of ~16.7ms — leaving almost no room for sensor fusion, pose prediction, and compositing before the next frame is due.

### Suggested Guests
| Name | Role | Connection |
|---|---|---|
| **Jerome Etienne** (@jeromeetienne) | AR.js creator, Web AR pioneer | Built the 60fps-on-mobile AR engine; deep insight into latency budgets |
| **Nicolò Carpignoli** (@nicolocarpignoli) | AR.js maintainer | Current steward of Web AR performance optimization |
| **Darcy Wilson** | VR/AR researcher, perceptual science | Expert on motion-to-photon thresholds and foveated rendering |
| **Szendeffy Balint** | Spatial computing engineer | Works on latency compensation in MR contexts |

### Talking Points
1. What is the "20ms rule" and where does it come from in the neuroscience literature?
2. How does AR.js achieve 60fps on mobile — and what perceptual trade-offs are made?
3. Is foveated rendering a genuine latency solution or a perceptual sleight-of-hand?
4. Cloud rendering vs. on-device: when does latency become "unacceptable" to the brain?
5. The difference between *latency* and *jitter* — and why the brain cares about both.

---

## Episode 2: "Spatial Sound and the Third Dimension"

**Core Question:** *Why is the WebXR spec still visual-only for spatial audio, and can HRTF-based 3D sound ever match the presence of real-world acoustic cues?*

### Key Topics
| Topic | Source Repo | Relevant Issue | Status |
|---|---|---|---|
| Spatialized audio inaudibility | MRTK-Unity | #11176 — Spatialized audio is inaudible | Bug, Rabbit Hole |
| audio spatializer on UX buttons | MRTK-Unity | #11177 — Spatialized audio inaudible after repeated presses | Bug |
| Microsoft Spatializer integration | MRTK-Unity | #6897 — Should use new Microsoft Spatializer with hardware offload | Feature Request |
| Default spatialization mixer errors | MRTK-Unity | #11349 — Throws errors when Spatializer package not installed | Bug |
| Spatial audio documentation gap | MRTK-Unity | #11433 — Documentation For Spatial Audio | Documentation Need |
| Spatial Sound / Audio mixer updates | MRTK-Unity | #10744 — Update audio demos and spatializer settings | Feature Request |
| Google Lullaby spatial audio | Lullaby | Core feature: "Support for full 3D VR environments, including spatial audio" | Architectural |

### Hot Debate Snippets (from GitHub Issues)
- **MRTK #11176**: *Spatialized audio is inaudible* — User Zee2 reports that spatialized audio on HoloLens 2 produces no perceptible output, raising the question: **is spatial audio a real perceptual channel or a visual proxy?**
- **MRTK #11177**: *Spatialized audio on UX buttons eventually is inaudible after several presses* — Depressing pattern: the audio system degrades with interaction, suggesting a perceptual fatigue or mixer deprecation bug.
- **MRTK #6897**: *MRTK should use the new Microsoft Spatializer with hardware offload support* — ashtat argues that hardware-accelerated spatialization is the only path to convincing 3D audio presence.
- **MRTK #11433**: *Documentation For Spatial Audio* — Even the maintainers (marlenaklein-msft) admit: **nobody knows how spatial audio should work in MR because the spec is silent.**

### Suggested Guests
| Name | Role | Connection |
|---|---|---|
| **Marlena Klein** (@marlenaklein-msft) | MRTK Spatial Audio lead | Directly responsible for spatial audio in MRTK3; heard every bug report |
| **David C. Kline** (@david-c-kline) | MRTK Audio/Spatialization engineer | Fixed the default mixer errors; deep SIP knowledge |
| **Acoustic/algorithmic specialist** | HRTF researcher | Can explain why head-related transfer functions challenge the brain |

### Talking Points
1. Why does the WebXR device API spec have **zero normative requirements** for spatial audio?
2. The "audio presence paradox": if spatialized sound is inaudible, does the brain "give up" on it?
3. Hardware offload vs. software spatialization — can the CPU truly compete with the ear?
4. Why do UX spatial audio bugs (#11177) manifest only *after repeated presses*? Perceptual adaptation?
5. Google Lullaby's ECS architecture treats spatial audio as first-class — is that the right model?

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**Core Question:** *Are hand tracking, eye tracking, and gaze-based interaction truly perceptually natural — or is the WebXR spec blind to non-visual perception?*

### Key Topics
| Topic | Source Repo | Relevant Issue | Status |
|---|---|---|---|
| WebXR support request | MRTK-Unity | #8472 — Feature Request for WebXR support | Closed (Won't Fix) |
| Hand tracking smoothing | MRTK-Unity | #9358 — ObjectManipulator smoothing for noisy hand input | Open debate |
| Eye tracking & gaze selection | MRTK-Unity | Feature: Eye Tracking Target Selection, Navigation, Heat Maps | Shipped feature |
| Spatial awareness & environmental understanding | MRTK-Unity | Core MRTK feature for hologram-world interaction | Architectural |
| Hand/gesture interaction design | XR Curriculum | Unit 4: Hands, Motion Controllers, Hands-Free, Gaze & Commit | Curriculum-based |
| Markerless AR at city scale | AR.js | #833 — "How to create Markerless AR visible across an entire city?" | Open question |
| Geospatial AR | AR.js | #834 — Geospatial tracking discussion | Open |

### Hot Debate Snippets (from GitHub Issues)
- **MRTK #8472**: *Support for WebXR — closed as Won't Fix* — The MRTK team decided against WebXR integration, but the underlying question persists: **is the MR interface paradigm fundamentally incompatible with the browser sandbox?**
- **AR.js #833**: *Markerless AR for an entire city* — User Tedesqui asks the existential question: **can Web AR scale to city-level geospatial tracking without losing the perceptual thread?**
- **MRTK #9358**: *ObjectManipulator smoothing for noisy hand input* — The deeper issue: **hand tracking data is inherently noisy, and the smoothing function determines whether the interface feels "wet" or "ghostly."**
- **XR Curriculum Unit 4**: The gaze-and-commit model raises a philosophical issue: **if your eyes select and your hands confirm, where does "intention" live in the perceptual loop?**

### Suggested Guests
| Name | Role | Connection |
|---|---|---|
| **April Speight** | XR Curriculum co-author, Azure Advocate | Designed the gaze-and-commit interaction pedagogy |
| **Gustavo Cordido** | XR Curriculum co-author | Co-authored comfort & coordinate system lessons |
| **Htet Htet June Han** | XR Curriculum co-author | Contributed to spatial design unit |
| **Marco** (HoloLens MRTK PM) | Microsoft MR program management | Can speak to the WebXR decision and why |

### Talking Points
1. The WebXR "Won't Fix" decision — is MR too complex for the browser, or is the browser too limited for MR?
2. Hand tracking noise and the "uncanny valley of interaction": when does smoothing feel fake?
3. Eye tracking as a perceptual proxy: does gaze selection change *how* we perceive content, not just *what* we select?
4. City-scale markerless AR (#833, #834): what does it do to spatial perception when the world itself becomes the display?
5. The gaze-and-commit model: is intention a perceptual event or a motor event?

---

## Cross-Episode Themes

| Theme | Episodes | Core Tension |
|---|---|---|
| **The Brain as Bottleneck** | 1, 2, 3 | Every technical limit is ultimately a perceptual limit — the brain's frame budget, audio processing, and intention modeling are the real constraints |
| **Spec vs. Reality** | 1, 2, 3 | WebXR is visual-first; MRTK targets HoloLens; AR.js promises 60fps — none of these specs account for how humans actually perceive |
| **The "Elf" Question** | 1, 2 | Latency and spatial audio are both "invisible" when they work and "catastrophic" when they fail — perception is a razor-thin margin |
| **Ghostliness & Uncanny Valley** | 1, 3 | Both latency-induced ghosting and hand-tracking jitter produce the same perceptual result: "this isn't real" |

## Repository Cross-Reference Map

| Repo | Stars | License | Primary Language | Perceptual Relevance |
|---|---|---|---|---|
| **jeromeetienne/AR.js** | 15,791 | MIT | HTML/JS | Mobile 60fps latency budget; markerless scaling |
| **microsoft/MixedRealityToolkit-Unity** | 6,076 | MIT | C# | Hand/eye/gaze tracking; spatial audio; spatial awareness |
| **google/lullaby** | 1,197 | Apache-2.0 | C++ | ECS architecture; spatial audio as first-class; VR environments |
| **microsoft/xr-development-for-beginners** | 564 | MIT | Vue | XR curriculum covering comfort, coordinate systems, interactions |

## Contributing

1. **Pick an episode issue** — each episode has an open GitHub Issue with this outline linked
2. **Add research findings** — comment on the issue with new GitHub issue links, papers, or demo references
3. **Propose guests** — add to the `GUEST_DIRECTORY.md` and tag the episode issue
4. **Submit PRs** — update this outline, add show notes, or link external resources
