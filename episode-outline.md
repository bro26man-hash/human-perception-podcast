# 🎙️ The Future of Human Perception — Episode Outline

## About the Series

**The Future of Human Perception** is a collaborative podcast exploring the cutting edge of augmented reality, spatial computing, mixed reality interfaces, and the neuroscience of how humans experience immersive digital environments.

We interview the developers, researchers, and designers who are reshaping how we see, hear, and interact with virtual worlds — and we dig into the open debates that are moving the field forward.

---

## Season 1 — Planned Episodes

### Episode 1: "The Latency Problem — Why Your Brain Rejects Fake Reality"
**Central Question:** What is perceptual latency, and why is it the #1 enemy of immersive experiences?

**Topics Covered:**
- Motion-to-photon latency: what it is, why it matters, and the 20ms threshold
- How the brain's predictive coding model creates the "uncanny valley" of digital motion
- Render pipeline optimization: foveated rendering, reprojection, and late-latching
- The Holographic Remoting problem: streaming VR/MR content without breaking presence
- Frame rate drops and their neurological impact on presence and comfort

**Key Debate:** Is 20ms a hard limit, or can perceptual tricks trick the brain into accepting higher latency?

**Potential Guests:**
- **jeromeetienne** (Nicolò Carpignoli) — AR.js creator, Web AR pioneer; perspective on latency in browser-based AR
- **Darcy Wilson** — Microsoft MRTK, input and microphone systems; latency in HoloLens 2 capture pipelines
- **szendeffybalint** — HTC Vive XR enterprise integration; latency challenges in enterprise VR

**Research Links:**
- [MRTK Optimize Window — performance profiling tools](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk3)
- [AR Foundation Camera Feed Lag after 6.1 upgrade](https://github.com/Unity-Technologies/arfoundation-samples/issues/1206)
- [MRTK Holographic Remoting Crashes](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/11845)

---

### Episode 2: "Hands That See — The Promise & Peril of Hand Tracking"
**Central Question:** Can hand tracking truly replace controllers, or are we fooling ourselves?

**Topics Covered:**
- Articulated hand tracking: HoloLens 2 vs. Ultraleap Leap Motion vs. camera-only solutions
- Gesture recognition accuracy and the "philandering finger" problem
- Hand physics: collision detection, grasping, and tactile feedback in mid-air
- The UX debate: direct hand interaction vs. controller-assisted precision
- Fingertip visualization and the confidence gap — when you *think* you grabbed something but didn't
- Hand tracking in the wild: lighting conditions, occlusion, and edge cases

**Key Debate:** Is pose-based hand tracking fundamentally limited by 21 joint degrees of freedom, or is the bottleneck inference speed?

**Potential Guests:**
- **Darcy Wilson** — Microsoft MRTK hand tracking and MicrophoneStream lead
- **david-c-kline** — Microsoft, MicStreamSelector and sharing architecture
- **Unité Ultraleap / Leap Motion community** — external hand tracking expertise

**Research Links:**
- [Object Manipulator Bug (MRTK #278)](https://github.com/microsoft/MixedRealityToolkit/issues/278)
- [MRTK Hand Physics Service (Experimental)](https://github.com/microsoft/MixedRealityToolkit-Unity#hand-physics-service)
- [AR.js Image Tracking](https://github.com/AR-js-org/AR.js) — marker-based vs. markerless hand tracking approaches

---

### Episode 3: "The Phantom Room — Spatial Audio & Mixed Reality Capture"
**Central Question:** How does spatial audio make or break the illusion of mixed reality?

**Topics Covered:**
- Spatial audio rendering: HRTF personalization, room acoustics, and environmental modeling
- Echo cancellation and voice isolation in shared MR spaces
- Mixed reality capture: passthrough quality, color grading, and the "uncanny window"
- The VOIP problem: why voice sounds garbled over WAN in MR applications
- Audio-visual coupling: when what you hear and see don't match
- Boundary systems and audio containment — the invisible walls of MR

**Key Debate:** Can personalized HRTFs ever be good enough for mass-market MR headsets, or is spatial audio forever compromised?

**Potential Guests:**
- **Darcy Wilson** — MRTK microphone & VOIP pipeline
- **david-c-kline** — MicStreamSelector and audio routing
- **reillydonovan** — Multi-display/MR camera setups
- **Microsoft Mixed Reality Audio Team** (TBD)

**Research Links:**
- [Voice VOIP garbled & slow on WAN (MRTK #72)](https://github.com/microsoft/MixedRealityToolkit/issues/72)
- [Failed to read microphone stream data (MRTK #300)](https://github.com/microsoft/MixedRealityToolkit/issues/300)
- [MicStreamSelector fails to build (MRTK #263)](https://github.com/microsoft/MixedRealityToolkit/issues/263)
- [MixedReality-WebRTC audio/video components](https://github.com/microsoft/MixedReality-WebRTC)

---

## Season 2 — Teaser Topics
- Eye tracking: gaze-based interaction and attention heat maps
- Spatial anchors & persistence: anchoring digital content to the real world
- The ethics of perception: manipulation, persuasion, and MR in advertising
- Neural interfaces: BCIs and the next frontier of human-computer perception

---

## How to Contribute

This repo is meant to be a **living collaboration**. To contribute:

1. Fork this repo
2. Add your research, episode notes, or guest suggestions in a new file under `research/`
3. Open an issue to discuss episode topics or propose new guests
4. Submit a PR with your proposed changes

## Repository Structure

```
human-perception-podcast/
├── episode-outline.md          # This file — master episode plan
├── research/                   # Deep-dive research docs per topic
│   ├── perceptual-latency.md
│   ├── hand-tracking.md
│   └── spatial-audio.md
├── guest-notes/                # Researcher & guest profiles
│   ├── jeromeetienne.md
│   ├── darcy-wilson.md
│   └── david-kline.md
├── scripts/                    # Episode scripts & talking points
│   ├── ep01-latency.md
│   ├── ep02-hand-tracking.md
│   └── ep03-spatial-audio.md
└── show-notes/                 # Published episode show notes
    ├── ep01-show-notes.md
    ├── ep02-show-notes.md
    └── ep03-show-notes.md
```

## License

This project is open under the [MIT License](LICENSE). Share freely, attribute.
