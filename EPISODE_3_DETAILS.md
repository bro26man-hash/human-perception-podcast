# 🕶️ Episode 3: "Interfaces Beyond the Flat Screen — MR Interfaces, Hologram Drift & the WebXR Blind Spot"

---

## Synopsis

We call it "spatial" computing, but our interfaces are still designed for 2D. Gamepads, flat panels, and 2D input APIs dominate. The "three-dimensional" part of 3D interfaces is mostly visual, not interactive. This episode asks the uncomfortable question: are we building "3D interfaces with 2D constraints" — and what would truly spatial interfaces even feel like?

---

## Talking Points

### 1. The 2D Input Trap
- XRControllers must be "flattened" into Gamepad API
- Spatial input (6DoF positions, rotations) is reduced to 2D axes before the app sees it
- The spec acknowledges the mismatch but doesn't solve it
- We're pointing at 3D space with a 2D abstraction

### 2. Spatial Navigation for D-Pads
- You navigate a 3D space with a 2D input device
- The cognitive mapping between flat input and spatial output is lossy
- Is this ergonomic pragmatism or paradigm capture?

### 3. Content Discovery & Launching
- How do you discover MR content in a spatial context?
- The "launching immersive elements" problem (#2071) is Chromium-specific
- The discovery problem for MR content is barely addressed in any spec
- If the interface is the space, how do you navigate the space?

### 4. Markerless AR at City Scale
- Local SLAM doesn't scale to global reference frames
- AR.js #833: tracking paradigm breaks at geographic scope
- Geospatial AR (#834) needs earth-centered coordinates
- AR.js only handles local tracking
- The gap between "where am I?" and "what's around me?"

### 5. Hologram Drift & Registration
- MR content that drifts, wobbles, or loses tracking breaks the illusion more decisively than visual glitches
- Calibration that works once but never twice
- The perceptual cost of "almost right" vs. "precisely wrong"

### 6. Hand Tracking vs. Controllers
- Which paradigm better supports "natural" interaction?
- Is either truly spatial, or are both just different flavors of 2D?
- The mid-air interaction problem: no haptic feedback, no proprioceptive anchor

### 7. Wayfinding in MR
- How do you navigate a spatial interface when the interface IS the space?
- The map is the territory, but the territory is the interface
- Proprioceptive, haptic, and auditory wayfinding as the next frontier

### 8. 3D LLMs as World Understanding
- SpatialLM could provide semantic world understanding that tracking-only approaches lack
- "There's a wall" vs. "there's a wall that separates the kitchen from the living room"
- Semantic understanding as the missing layer for true spatial interfaces

---

## Demo Ideas
- **2D vs. 3D input comparison:** Show the Gamepad API flattening problem
- **Markerless AR drift demo:** Live demonstration of tracking instability over time
- **Spatial wayfinding prototype:** A simple MR navigation experience using gaze + voice

---

## Key GitHub Issues to Reference
| Issue | What It Reveals |
|-------|------------------|
| [Igalia/wolvic #993](https://github.com/Igalia/wolvic/issues/993) | XRControllers flattened to Gamepad API — spatial input reduced to 2D |
| [Igalia/wolvic #1110](https://github.com/Igalia/wolvic/issues/1110) | Spatial navigation for D-pads — 3D space, 2D input |
| [Igalia/wolvic #2071](https://github.com/Igalia/wolvic/issues/2071) | Launching immersive elements — discovery problem barely addressed |
| [AR-js-org/AR.js #833](https://github.com/AR-js-org/AR.js/issues/833) | City-scale markerless AR — SLAM doesn't scale to global frames |
| [AR-js-org/AR.js #834](https://github.com/AR-js-org/AR.js/issues/834) | Geospatial AR — needs earth-centered coordinates, AR.js only does local |
| [AR-js-org/AR.js #217](https://github.com/AR-js-org/AR.js/issues/217) | Markerless debate — Jerome's original vision of `tracking: best` |
| [hiukim/mind-ar-js #526](https://github.com/hiukim/mind-ar-js/issues/526) — Abandonware & fork discussion |
| [SpatialLM Paper](https://arxiv.org/abs/2506.07491) — 3D LLMs for spatial understanding |

---

## Guest Notes

### Primary: Jérôme Étienne (@jeromeetienne)
- Creator of AR.js (15,800★)
- His decision to transfer maintenance to the AR.js org
- Key thread: [Issue #217](https://github.com/AR-js-org/AR.js/issues/217) — the markerless debate, his vision of `tracking: best`
- **Talking point:** "Why markerless was never built — and what I'd do differently"
- **The big question:** Did making AR.js marker-focused from the start lock Web AR into a local-tracking paradigm that it can't escape?

### Secondary: kylebakerio (@kylebakerio)
- WebXR/ARCore integration advocate
- Built 3Dof AR proof of concept and multiplayer WebXR VR apps
- **Talking point:** "AR.js is going to lose relevance if an open-source library supports ARCore/ARKit and AR.js doesn't"
- **The pragmatic position:** ARCore/ARKit are the reality today

### Secondary: nickw1 (@nickw1)
- AR.js location-based AR contributor
- Created arjs-peakfinder (POI AR browser)
- Spent years debugging GPS-AR drift
- **Talking point:** "Why location-based AR drifts, the iOS vs. Android perception gap"

### Secondary: CoderSilas (@CoderSilas)
- Found encantar.js as a replacement for MindAR/AR.js
- **Talking point:** "AR.js is definitively dead if you dig around a bit" — the canary in the coal mine
- **The forward question:** What comes after AR.js? Does it exist?

### Secondary: Yongsen Mao (@manycore-research)
- SpatialLM — 3D LLMs for spatial perception
- **Bridge question:** Could semantic world understanding finally provide the "third dimension" that interfaces are missing?

---

## Closing Reflection

> "We call it 'spatial' computing, but our interfaces are 2D. We wear 3D displays and interact through 2D controllers. The perceptual transparency problem asks: when we mask the spatial nature of interaction, is that ergonomics — or have we just accepted a paradigm without questioning it?"

---

*Research compiled from GitHub issues across Igalia/wolvic, AR-js-org/AR.js, hiukim/mind-ar-js, and the SpatialLM research project.*