# The Future of Human Perception — Episode Outline (Master)

> A collaborative podcast series exploring the bleeding edge of **augmented reality, spatial computing, and perceptual science**.
> Each episode targets a core question about how humans perceive and interact with digital environments — grounded in real open-source debates and active XR communities.
>
> **Repo:** https://github.com/bro26man-hash/human-perception-podcast
> **Format:** Audio interview + live demo segments | **Cadence:** Bi-weekly | **License:** MIT

---

## Episode 1: "The Latency Gap — When Perception Meets Processing"

**Focus:** Why even a few milliseconds of system latency can break the illusion of reality — and where the latency actually hides.

**Core Question:** If a headset introduces just 20 ms of motion-to-photon delay, the vestibular system detects it. What does that *feel* like, and what's happening in the pipeline that makes it so hard to eliminate?

### Key Topics
- **Perceptual latency thresholds:** the ~20 ms rule, vestibular-visual conflict, motion-sickness onset, and the "perceptual clock."
- **Motion-to-photon pipeline:** Sensor → Predict → Render → Encode → Transport → Decode → Display.
- **Camera↔IMU hardware clock synchronization:** Xiaomi/OPPO 13–35 ms offsets ([`google-ar/arcore-android-sdk` #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779)).
- **Tracking & floor-plane drift:** "Tracking not smooth and a little delayed" — 97 comments ([`ValveSoftware/SteamVR-for-Linux` #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21)); ARCore floor plane drift that is metrically correct then incorrectly updated ([#1781](https://github.com/google-ar/arcore-android-sdk/issues/1781)).
- **"Missing" latency:** a researcher found ~33.6 ms of unaccounted latency in a VR streaming stack ([`polygraphene/ALVR` #334](https://github.com/polygraphene/ALVR/issues/334)).
- **Depth-map noise on mid-range devices** ([`google-ar/arcore-android-sdk` #1723](https://github.com/google-ar/arcore-android-sdk/issues/1723)).
- **Calibration instability:** SpectatorView calibration that works once but never twice ([`microsoft/MixedRealityCompanionKit` #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228)).
- **HoloLens / OpenXR timing:** Direct3D 12 performance, frame timestamp precision, and temporal synchronization ([`microsoft/OpenXR-MixedReality` #131, #132](https://github.com/microsoft/OpenXR-MixedReality/issues?q=is%3Aissue+131)).
- **Web / mobile AR pipeline:** how AR.js (markerless & location-based, 15.8k★) and MindAR (TensorFlow.js image/face tracking, 2.7k★) handle the camera→render loop.

### Research Notes
- The SteamVR-for-Linux thread shows that even UX-level smoothing can't hide the gap between head movement and rendered frame delivery.
- ALVR's "missing latency" finding suggests current VR streaming stacks underreport total system latency by 30–50%, misdirecting optimization.
- SpectatorView calibration fragility (MRC #228, still unresolved) is a serious barrier to research reproducibility in spatial tracking.

### Potential Guest Contributors
| Name | Handle / Affiliation | Relevance |
|------|----------------------|-----------|
| **leinardi** | SteamVR for Linux maintainer | Direct experience with motion-to-photon latency on open-source VR |
| **jd-3d** / polygraphene | ALVR developer & latency researcher | First-hand investigation into missing pipeline latency |
| **fieldsJacksonG** | Microsoft MRC contributor | Assignee on hologram registration & calibration issues |
| **chrisfromwork** | Microsoft MRC | Long-term MR development insights |
| **maluoi** | StereoKit maintainer | OpenXR-based XR engine & rendering pipeline |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform & motion-to-photon perspective |
| **brycehutchings** | Microsoft OpenXR contributor | MR performance, Direct3D 12 |

### Community Debates to Surface
- *Perceptual vs. measured latency*: Is the latency our instruments measure the same as what the brain detects? (see ALVR "missing" latency).
- *Where does latency "live"?* Sensor fusion, prediction, encode/transport, decode, display — which stage is least optimized？

---

## Episode 2: "Spatial Audio & the HRTF Frontier — Sound as the Ultimate Spatial Sense"

**Focus:** When a voice appears behind your left shoulder in AR, what makes you believe it's real? The physics, biology, and engineering of rendering sound in 3D.

**Core Question:** How do spatial audio algorithms trick the brain into hearing sound in 3D space — and why do off-the-shelf HRTFs still fail for a meaningful minority of listeners?

### Key Topics
- **Head-Related Transfer Functions (HRTFs):** personalization vs. generic profiles; front-back confusion and distance misperception in the remaining ~20% of listeners.
- **Spatial rendering pipelines:** Vector Base Amplitude Panning (VBAP), higher-order ambisonics, binaural rendering ([`leomccormack/Spatial_Audio_Framework` #66](https://github.com/leomccormack/Spatial_Audio_Framework/issues/66)).
- **HRTF dataset quality:** SONICOM loading bugs and perceptual accuracy ([`leomccormack/Spatial_Audio_Framework` #55](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55)).
- **Room acoustics simulation:** ISM reverberation and perceptual quality ([`leomccormack/Spatial_Audio_Framework` #58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58)).
- **Real-time spatial audio:** web-based (Google/Chrome Omnitone,beatsync), 360° video sync ([`Google/spatial-media`](https://github.com/google/spatial-media)).
- **Audio-visual integration:** how vision dominates when auditory and visual cues conflict; the cocktail party problem in MR.
- **Accessibility:** using Apple Vision Pro spatial audio to help visually impaired users identify and navigate to indoor objects ([`ameliaeckard/spatial-audio-research-arvr`](https://github.com/ameliaeckard/spatial-audio-research-arvr)).
- **Networked MR audio:** multi-client spatial audio sync via Velnet — a "lattice problem" where inter-client latency breaks the illusion ([`alextawes19/SYNC-MR`](https://github.com/alextawes19/SYNC-MR)).

### Research Notes
- Off-the-shelf HRTFs work for ~80% of listeners; the remaining 20% experience significant front-back confusion — a key open research problem.
- Auditory spatial cues are processed faster and more reflexively than visual ones, making spatial audio a first-class design primitive for MR (not just an afterthought).
- SYNC-MR's Velnet sync shows that networked MR audio demands tight latency budget per client.

### Potential Guest Contributors
| Name | Handle / Affiliation | Relevance |
|------|----------------------|-----------|
| **leomccormack** | `Spatial_Audio_Framework` creator | Ambisonics, HRTFs, spatialization |
| **@BinWang28** | `audio-ai-hub` | HRTF augmentation, spatial speech perception |
| **edurnebernal** | Audio-visual spatial perception in VR | Head-body rotation modeling |
| **ameliaeckard** | Spatial audio researcher (AR/VR accessibility) | Spatial audio for navigation assistance |
| **alextawes19** | `SYNC-MR` creator | Spatially-placed instruments, networked MR audio |
| **TheBarmaEffect** | `echo` engine | Perception-first spatial audio engine |
| **crlandsc / ali-vosoughi / jacobhollebon** | `Spatial_Audio_Framework` contributors | Spatialization algorithms |

### Community Debates to Surface
- *Generic vs. personalized HRTFs:* why one-size-fits-all fails and what "good enough" looks like.
- *Audio before vision:* spatial hearing is processed faster and more reflexively — what does that mean for MR design priority？
- *Networked presence:* can distributed listeners share a coherent spatial audio scene？

---

## Episode 3: "Interfaces Beyond the Flat Screen — Passthrough, Presence & the Attention Economy"

**Focus:** How mixed reality collapses the boundary between digital UI and physical space — and who it competes for attention with.

**Core Question:** In mixed reality, holograms drift, stick to cameras, and fail to stay where you place them. What are the fundamental limits of *registering* digital content to the physical world — and how close are we to solving them?

### Key Topics
- **Hologram registration:** "Holograms sticking to camera" — reprojection drift over network stacks ([`microsoft/MixedRealityCompanionKit` #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221), assignee fieldsJacksonG).
- **Hand tracking & gesture recognition:** roadmap, hand-controller simulation, pointer/Gaze breakdown during fast motion ([`XRTK/com.xrtk.core` #645, #902](https://github.com/XRTK/com.xrtk.core/issues?q=is%3Aissue+645)); visionOS hand tracking ([`IvanCampos/visionOS-examples`](https://github.com/IvanCampos/visionOS-examples)).
- **Plane detection & spatial mapping:** Apple's plane detection and its limits in dynamic environments ([`IvanCampos/visionOS-examples`](https://github.com/IvanCampos/visionOS-examples)).
- **Spatial anchoring:** April Tag–based pragmatism ([`alextawes19/SYNC-MR`](https://github.com/alextawes19/SYNC-MR)) vs. shared spatial anchors & colocation (Meta Quest).
- **Passthrough safety:** boundary-aware vs. depth-aware techniques ([`TXST-CS7389I/DreamGuard`](https://github.com/TXST-CS7389I-Spring-2026-Group-Project/DreamGuard)).
- **Spatial UI paradigms:** how visionOS, HoloLens, and Meta Quest approach spatial interfaces differently; AnchorToHead, plane detection, RealityKit shaders.
- **Rendering fidelity:** Scriptable Render Pipeline for MR ([`XRTK/com.xrtk.core` #407](https://github.com/XRTK/com.xrtk.core/issues/407)); OpenXR 1.1 spec implications ([`StereoKit/StereoKit` #1329](https://github.com/StereoKit/StereoKit/issues/1329)); WebXR backend ([`StereoKit/StereoKit` #345](https://github.com/StereoKit/StereoKit/issues/345), display issues [#1209](https://github.com/StereoKit/StereoKit/issues/1209)).
- **Cloud anchors:** ARCore keyless auth silent failures ([`google-ar/arcore-android-sdk` #1777](https://github.com/google-ar/arcore-android-sdk/issues/1777)).
- **The attention economy:** how MR interfaces manipulate perceptual focus; emerging neuroadaptive MR (brain-controlled experiences) as the next frontier ([`Caerii/OpenGalea`](https://github.com/Caerii/OpenGalea)).

### Research Notes
- "Registration ≠ understanding": geometric alignment does not mean the brain accepts a hologram as real.
- OpenGalea (MIT Reality Hack Meta winner) fuses an 8-channel EEG with a Quest 3 for brain-controlled, colocated multiplayer MR — hinting at attention/relaxation-driven interfaces.
- visionOS examples (405★) expose the breadth of registration strategies: head-anchored entities, hand tracking, plane detection, RealityKit shaders — each with different trade-offs.

### Potential Guest Contributors
| Name | Handle / Affiliation | Relevance |
|------|----------------------|-----------|
| **Ivan Campos** | `visionOS-examples` (405★) | Hands-on visionOS spatial computing |
| **maluoi** | StereoKit maintainer | OpenXR / WebXR MR engine |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration |
| **chrisfromwork** | Microsoft MRC | Long-term MR development |
| **alextawes19** | `SYNC-MR` | Spatial anchoring (April Tags) & spatial audio |
| **StephenHodgson** | XRTK core | MR interaction design |
| **FejZa** | XRTK maintainer | Rendering & input systems |
| **jdwalker** | XRTK | Record/replay & framework tooling |
| **jasongraham** | visionOS spatial UI | Apple ecosystem |
| **jeromeetienne / nicolocarpignoli** | `AR.js` (15.8k★) | Web AR, markerless & geospatial |
| **hiukim** | `MindAR` (2.7k★) | Web AR, TensorFlow.js tracking |
| **S. Hussain Ather / Alif Jakir / Tsing Liu / Yechan Ian Seo** | `OpenGalea` (Team Syncer) | Neuroadaptive, brain-controlled MR |

### Community Debates to Surface
- *Hand vs. gaze vs. gesture:* which input modality wins, and when do false triggers break presence？
- *Controller vs. hand tracking roadmap* and pointer validation during fast motion.
- *Neuroadaptive MR:* should interfaces respond to attention/relaxation (EEG) rather than (or in addition to) physical input？

---

## Guest Coordination Checklist

- [ ] Reach out to **Ivan Campos** (`IvanCampos`, visionOS) — Episode 3
- [ ] Contact **leomccormack** — Episode 2 (spatial audio)
- [ ] Reach **leinardi** (SteamVR for Linux) & **jd-3d** (ALVR) — Episode 1
- [ ] Invite **alextawes19** (SYNC-MR) — Episodes 2 & 3 (spatial audio + anchoring)
- [ ] Connect with **fieldsJacksonG** / **chrisfromwork** (Microsoft MRC) — Episodes 1 & 3
- [ ] Invite **@BinWang28** / **edurnebernal** / **ameliaeckard** — Episode 2
- [ ] Contact **maluoi** (StereoKit) & **StephenHodgson/FejZa/jdwalker** (XRTK) — Episodes 1 & 3
- [ ] Follow up with **S. Hussain Ather** / Team Syncer (OpenGalea, neuroadaptive MR) — Episode 3
- [ ] Engage web-AR voices **jeromeetienne / nicolocarpignoli** & **hiukim** (AR.js / MindAR) — cross-episode

---

## Community Discussion Themes (Source Material)

1. **Perceptual vs. Measured Latency** — Is instrument-measured latency the same as perceptually detected latency? (Ep. 1; ALVR "missing" latency, SteamVR-for-Linux)
2. **Registration ≠ Acceptance** — Geometric hologram alignment ≠ the brain accepting it as real. (Ep. 3; MRC #221, visionOS)
3. **Audio Before Vision** — Auditory spatial cues are processed faster/more reflexively than visual; implications for MR design priority. (Ep. 2)
4. **Neuroadaptivity** — Should MR respond to brain-derived attention/relaxation instead of only physical input? (Ep. 3; OpenGalea)

---

## Research Sources (Active Repos & People)

| Repo | Stars | Relevance |
|------|-------|-----------|
| `jeromeetienne/AR.js` → `AR-js-org/AR.js` | 15.8k | Web AR (markerless, location-, image-based) |
| `hiukim/mind-ar-js` | 2.7k | Web AR, TensorFlow.js image/face tracking |
| `google-ar/arcore-android-sdk` | 5.2k | Android AR; clock-offset, floor-drift, depth-map issues |
| `IvanCampos/visionOS-examples` | 405 | visionOS spatial computing examples |
| `StereoKit/StereoKit` | 1.1k | C# XR engine (WebXR + OpenXR) |
| `microsoft/xr-development-for-beginners` | 564 | Microsoft XR curriculum (comfort, interaction, spatial design) |
| `microsoft/MixedRealityCompanionKit` | — | MR calibration & hologram registration |
| `alextawes19/SYNC-MR` | — | Colocated MR + Velnet spatial audio |
| `ameliaeckard/spatial-audio-research-arvr` | — | Spatial audio for visual impairment |
| `Caerii/OpenGalea` (Team Syncer) | — | Neuroadaptive (EEG + Quest 3) MR |

**Prominent community voices:** leomccormack, @BinWang28, edurnebernal, ivan_campos, @maluoi, fieldsJacksonG, chrisfromwork, jeromeetienne/nicolocarpignoli, hiukim, alextawes19, ameliaeckard, fredemmott.

---

*Status: Planning — Episode outlines, guest research, and community-sourced debate topics in progress.*
