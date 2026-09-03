# The Future of Human Perception — Episode Outlines

## Episode 1: The Latency Gap — When Perception Meets Processing
**Focus:** Perceptual latency in AR/VR systems — the camera↔IMU clock-offset problem, motion-to-photon delays, and why even 50ms can break presence.

**Key Topics:**
- Camera↔IMU hardware clock synchronization (Xiaomi/OPPO 13–35ms offset bug — ARCore #1779)
- Motion-to-photon pipeline: sensor fusion, prediction, frame warping
- Floor-plane drift and incorrect metric readings (ARCore #1781)
- The psychoacoustic threshold: how latency manifests differently across senses
- Depth-map noise on mid-range devices (ARCore #1723)

**Potential Guests:**
- Maintainers of `google-ar/arcore-android-sdk` (5,233★)
- StereoKit XR engine team (@maluoi)
- Sensor-fusion researchers working on predictive head-tracking

**Background Reading:**
- `google-ar/arcore-android-sdk` — issues #1779, #1781, #1723
- `KhronosGroup/OpenXR-SDK` — runtime configuration challenges
- Research: "Modeling the Impact of Head-Body Rotations on Audio-Visual Spatial Perception" (edurnebernal/Audiovisual-Spatial-Perception-in-VR)

---

## Episode 2: Spatial Audio & the HRTF Frontier — Sound as the Ultimate Spatial Sense
**Focus:** How spatial audio engineering shapes our perception of virtual space, and why personalized HRTFs remain the holy grail.

**Key Topics:**
- HRTF personalization vs. generic profiles — why one-size-fits-all fails
- HRTF augmentation effects on spatial release from masking (BinWang28/audio-ai-hub #169)
- Spatial speech perception: source localization, directional enhancement, ASR (BinWang28/audio-ai-hub #104)
- Audio-visual integration in VR: how vision dominates when cues conflict
- Perception-first spatial audio engines (TheBarmaEffect/echo)
- Accessibility: spatial audio for the visually impaired (Electrosquib/Auditory-Spatial-Perception-System)

**Potential Guests:**
- Spatial audio researchers (BinWang28, edurnebernal)
- Perception-first engine designers (TheBarmaEffect)
- Accessibility technologists building audio-based navigation for blind users

**Background Reading:**
- `BinWang28/audio-ai-hub` — issues #169, #104
- `TheBarmaEffect/echo` — perception-first spatial audio engine
- `Electrosquib/Auditory-Spatial-Perception-System` — CV + spatial audio for the visually impaired
- `edurnebernal/Audiovisual-Spatial-Perception-in-VR` — head-body rotation modeling paper

---

## Episode 3: Mixed Reality Interfaces — Passthrough, Presence, and the Attention Economy
**Focus:** The design of mixed-reality interfaces: optical passthrough quality, boundary systems, and how MR competes for our attention.

**Key Topics:**
- MR passthrough safety: boundary-aware vs. depth-aware techniques (TXST-CS7389I/DreamGuard)
- WebXR backend as the future of cross-platform MR (StereoKit #345)
- Quest 3 display & passthrough rendering issues (StereoKit #1209)
- ARCore Cloud Anchors silent auth failures (ARCore #1777)
- The attention economy: how MR interfaces manipulate perceptual focus
- OpenXR 1.1 spec implications for future MR interaction paradigms (StereoKit #1329)

**Potential Guests:**
- StereoKit team (@maluoi) — WebXR and OpenXR integration
- Meta Quest platform engineers
- Mixed-reality safety researchers (DreamGuard project)
- UX researchers studying attention and presence in MR

**Background Reading:**
- `StereoKit/StereoKit` — issues #345, #1209, #1329
- `TXST-CS7389I-Spring-2026-Group-Project/DreamGuard` — MR passthrough safety comparison
- `google-ar/arcore-android-sdk` issue #1777 (Cloud Anchors)
- `arghyasur1991/synth-vr` — hand physics & room integration on Quest

---

## Community & Collaboration
This repo is managed via GitHub Issues for episode planning, guest outreach, and topic research. Each episode issue is labeled `episode-1`, `episode-2`, `episode-3` and tagged with `research-needed`, `guest-outreach` as appropriate.

**Contributing:**
- Add guest suggestions as issue comments
- Fork and submit research pull requests
- Tag relevant GitHub users from the AR/XR community