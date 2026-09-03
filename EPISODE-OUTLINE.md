# The Future of Human Perception — Episode Outline

> A collaborative podcast series exploring the bleeding edge of augmented reality, spatial computing, and perceptual science.

---

## Episode 1: "The Latency Problem — Why Your Brain Knows When Reality Lags"

**Status:** 🔬 Research & Guest Recruitment

### Core Question
If a VR/AR headset introduces just 20ms of motion-to-photon latency, your vestibular system detects it. What does that *feel* like — and what's happening in the pipeline that makes it so hard to eliminate?

### Key Topics
- **Perceptual latency thresholds**: The 20ms rule, vestibular-visual conflict, and motion sickness onset
- **SteamVR tracking latency** (Issue #21 — ValveSoftware/SteamVR-for-Linux): "Tracking not smooth and a little delayed" — 97 comments from users reporting nausea-inducing lag on Linux
- **ALVR latency accounting mystery** (Issue #334 — polygraphene/ALVR): A researcher found 33.6ms of "missing" latency in the total pipeline — where does it go?
- **Motion-to-photon pipeline breakdown**: Sensor → Predict → Render → Encode → Transport → Decode → Display
- **Calibration instability** (Issue #228 — microsoft/MixedRealityCompanionKit): SpectatorView calibration that works once but never twice — what does this tell us about reproducibility in spatial tracking?

### Research Notes
- The SteamVR-for-Linux tracking issue reveals that even UX-style "smoothing" and interpolation can't hide the gap between head movement and rendered frame delivery
- The ALVR latency mystery shows that current VR streaming stacks may underreport total system latency by 30–50%, making optimization efforts misdirected
- Calibration instability in SpectatorView (19 comments, still unresolved) highlights that real-world MR setups are fragile — a major barrier to research reproducibility

### Potential Guest Contributors
| Name | Role | Relevance |
|------|------|-----------|
| **leinardi** | SteamVR for Linux maintainer | Direct experience with motion-to-photon latency on open-source VR |
| **jd-3d** | ALVR developer & latency researcher | First-hand investigation into missing latency in VR streaming pipelines |
| **fieldsJacksonG** | Microsoft MRC contributor | Assignee on hologram registration & calibration issues |
| **BrettSheleski** | SpectatorViewCalibration reporter | Real-world MR calibration struggles |

### Open Issues to Reference
- [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21): Tracking not smooth and a little delayed (97 comments)
- [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334): Latency calculations are missing info / incorrect (6 comments)
- [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228): Calibration Instability with elgato HD60S (19 comments)

---

## Episode 2: "Where Does the Digital End and the Physical Begin?"

**Status:** 🔬 Research & Guest Recruitment

### Core Question
In mixed reality, holograms drift, stick to cameras, and fail to stay where you placed them. What are the fundamental limits of registering digital content to the physical world — and how close are we to solving them?

### Key Topics
- **Hologram registration errors** (Issue #221 — microsoft/MixedRealityCompanionKit): "Holograms sticking to camera" — 18 comments on reprojection drift when using network stacks
- **Plane detection & spatial mapping** (visionOS-examples): How Apple's plane detection works and its limitations in dynamic environments
- **Hand tracking & gesture recognition** (visionOS-examples): The gap between detected hand positions and intended interactions
- **Spatial UI paradigms**: How visionOS, HoloLens, and Meta Quest approach spatial interfaces differently
- **April Tag anchoring** (SYNC-MR): A pragmatic approach to spatial anchoring in collaborative MR experiences
- **ARKit head tracking & surroundings classification**: Foundational tech for understanding spatial perception

### Research Notes
- The "holograms sticking to camera" issue (assignee: fieldsJacksonG, 18 comments) reveals that even Microsoft's own SpectatorView pipeline can't perfectly reconcile camera feed with hologram placement — a fundamental challenge in MR registration
- VisionOS Examples (405⭐, maintained by Ivan Campos) shows the breadth of approaches: head-anchored entities, hand tracking, plane detection, RealityKit shaders — each with different registration tradeoffs
- SYNC-MR's use of April Tags for spatial anchoring represents a practical middle ground: reliable butRequires physical markers

### Potential Guest Contributors
| Name | Role | Relevance |
|------|------|-----------|
| **Ivan Campos** | Creator, visionOS-examples (405⭐) | Deep hands-on with visionOS spatial computing paradigms |
| **fieldsJacksonG** | Microsoft MRC assignee | Direct experience with hologram registration problems |
| **chrisfromwork** | MRC deprecation contributor | Long-term MR development at Microsoft |
| **alextawes19** | SYNC-MR creator | MR spatial anchoring with April Tags |
| **chenzlabs** | Creator, aframe-ar (255⭐) | WebXR AR tracking and browser-based spatial computing |

### Open Issues to Reference
- [microsoft/MixedRealityCompanionKit #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221): Holograms sticking to camera (18 comments)
- [microsoft/MixedRealityCompanionKit #299](https://github.com/microsoft/MixedRealityCompanionKit/issues/299): PosterCalibration Camera Not Working in Unity 2018 (13 comments)
- [IvanCampos/visionOS-examples](https://github.com/IvanCampos/visionOS-examples): Plane Detection, Hand Tracking, AnchorToHead examples

---

## Episode 3: "The Sound of Space — How Spatial Audio Redefines Presence"

**Status:** 🔬 Research & Guest Recruitment

### Core Question
When a voice appears to come from behind your left shoulder in AR, what makes you *believe* it's really there? The physics of spatial audio, the biology of auditory perception, and the engineering of rendering sound in 3D space.

### Key Topics
- **Spatial audio rendering** (alextawes19/SYNC-MR): Mixed reality percussion with spatially-placed instruments — how does audio placement affect presence?
- **Microphone arrays & beamforming**: How headsets capture real-world sound for mixed reality passthrough
- **Head-Related Transfer Functions (HRTFs)**: Why personalized HRTFs matter for accurate spatial audio
- **Ambisonics & binaural rendering**: The pipeline from 3D audio capture to headphone playback
- **Spacial audio for accessibility** (ameliaeckard/spatial-audio-research-arvr): Using Vision Pro's spatial audio to help visually impaired users navigate indoor spaces
- **The cocktail party problem in MR**: How do you isolate a voice in a spatially-rendered noisy environment?

### Research Notes
- SYNC-MR's use of Velnet for multi-client spatial audio synchronization demonstrates that networked MR audio is a lattice problem — latency differences between clients break the illusion
- The spatial-audio-research-arvr project (3⭐, by ameliaeckard) is an Accessibility-focused application of spatial audio — a compelling angle for Episode 3's "why this matters" segment
- The original research on HRTF personalization shows that off-the-shelf HRTFs work for ~80% of listeners, but the remaining 20% experience significant front-back confusion and distance misperception

### Potential Guest Contributors
| Name | Role | Relevance |
|------|------|-----------|
| **ameliaeckard** | Spatial audio researcher (AR/VR accessibility) | Direct research on spatial audio for navigation assistance |
| **alextawes19** | Creator, SYNC-MR | Hands-on with spatialized audio in collaborative MR |
| **ynagatomo** | visionOS Shader Graph materials | Spatial audio context in Apple's spatial computing ecosystem |

### Open Issues / Community Discussions to Reference
- [alextawes19/SYNC-MR](https://github.com/alextawes19/SYNC-MR): Multi-client spatial audio with Velnet networking
- [ameliaeckard/spatial-audio-research-arvr](https://github.com/ameliaeckard/spatial-audio-research-arvr): Accessibility research using Vision Pro spatial audio

---

## Guest Coordination Checklist

- [ ] Reach out to Ivan Campos (visionOS-examples) for Episode 2
- [ ] Contact leinardi about SteamVR latency experiences for Episode 1
- [ ] Connect with jd-3d (ALVR) about latency research for Episode 1
- [ ] Invite alextawes19 (SYNC-MR) for Episode 3 — spatial audio
- [ ] Follow up with ameliaeckard (spatial audio accessibility) for Episode 3
- [ ] Identify Microsoft MRC community contacts (fieldsJacksonG, chrisfromwork) for Episode 2
- [ ] Research WebXR community voices (chenzlabs, aframe-ar) for cross-episode perspectives

---

## Community Discussion Themes

1. **Perceptual vs. Measured Latency**: Is the latency we measure with instruments the same as the latency the human perceptual system detects? (Episode 1)
2. **Registration ≠ Understanding**: Just because a hologram is geometrically aligned doesn't mean the brain accepts it as real. (Episode 2)
3. **Audio Before Vision**: In human perception, auditory spatial cues are processed faster and more reflexively than visual ones. What does this mean for MR design? (Episode 3)
