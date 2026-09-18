# 🎧 Episode 1: "The Latency Gap — When Perception Meets Processing"

---

## Synopsis

Why does a 20-millisecond delay between moving your head and seeing the world respond make you nauseous? And what's actually happening inside the pipeline that makes latency so hard to eliminate? This episode traces the motion-to-photon pipeline from sensor to display, surfaces the "missing latency" that current measurements miss, and asks whether foveated rendering is a brilliant optimization or a sensory deception.

---

## Talking Points

### 1. The 20ms Rule — Myth or Physical Limit?
- The vestibular system detects mismatches at ~20ms
- Is this a hard biological constraint or a cultural norm that happened to stick?
- Different researchers cite different thresholds — who's right?

### 2. The Motion-to-Photon Pipeline
- **Sensor (IMU + camera)** → **Predict** → **Render** → **Encode** → **Transport** → **Decode** → **Display**
- Each stage adds latency; each stage has optimization opportunities
- Where is the biggest bottleneck?

### 3. "Missing" Latency — The 33.6ms Problem
- ALVR researcher found 33.6ms of unaccounted latency in a VR streaming stack
- Current measurement tools underreport total system latency by 30-50%
- Implications: we're optimizing the wrong thing

### 4. Hardware Clock Synchronization
- Camera and IMU clocks can drift 13-35ms on mobile (Xiaomi/OPPO)
- ARCore floor plane drift: metrically correct, then incorrectly updated
- Calibration that works once but never twice (SpectatorView)

### 5. Foveated Rendering — The Latency Cheat?
- Reduce render resolution in periphery → brain doesn't notice
- Is this "immersion enhancement" or "sensory deception"?
- What are the perceptual consequences of forcing vs. allowing smoothing?

### 6. The Web AR Angle
- How AR.js handles camera→render (marker-based, no prediction)
- How MindAR handles it (TensorFlow.js, webgl-based tracking)
- Why open-source Web AR lags behind commercial SDKs on latency

---

## Demo Ideas
- **Latency measurement toolkit:** Show listeners how to measure motion-to-photon latency on their own devices
- **AR.js marker tracking demo:** Live demonstration of marker-based AR and the visible lag
- **Foveated rendering visualization:** Simulate peripheral blur vs. full-resolution rendering

---

## Key GitHub Issues to Reference
| Issue | What It Reveals |
|-------|------------------|
| [ValveSoftware/openvr #1012](https://github.com/ValveSoftware/openvr/issues/1012) | Developers want programmatic reprojection control — but perceptual consequences unknown |
| [ValveSoftware/openvr #1729](https://github.com/ValveSoftware/openvr/issues/1729) | GPU timestamp corruption means prediction data can be *wrong* |
| [ValveSoftware/openvr #1917](https://github.com/ValveSoftware/openvr/issues/1917) | `xrWaitFrame` returns `XR_SUCCESS` with negative `predictedDisplayTime` — frame displays in the past |
| [google-ar/arcore-android-sdk #1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | Camera-IMU clock offset: 13-35ms on mobile |
| [google-ar/arcore-android-sdk #1781](https://github.com/google-ar/arcore-android-sdk/issues/1781) | Floor plane drift: correct then incorrect updates |
| [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334) | 33.6ms of unaccounted latency in VR streaming |
| [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | Calibration instability — works once, never twice |
| [AR-js-org/AR.js #288](https://github.com/AR-js-org/AR.js/issues/288) | Markerless location-based AR — realistic placement still broken |
| [hiukim/mind-ar-js #556](https://github.com/hiukim/mind-ar-js/issues/556) | Tracking jitter — the open-source vs. commercial quality gap |

---

## Guest Notes

### Primary: hiukim (@hiukim)
- Creator of MindAR
- Can speak to the technical challenges of Web AR tracking latency
- Key thread: [Issue #526](https://github.com/hiukim/mind-ar-js/issues/526) — "Is this repo abandonware?"
- **Talking point:** "MindAR applies no smoothing — commercial SDKs do. That's the gap."

### Primary: Nicolò Carpignoli (@nicolocarpignoli)
- AR.js former maintainer
- Deepest knowledge of Web AR architecture and the markerless gap
- Key thread: [Issue #217 comment](https://github.com/AR-js-org/AR.js/issues/217#issuecomment-849888943)
- **Talking point:** "We are in between where there is no OSS markerless cross-browser Web AR"

### Secondary: kalwalt (@kalwalt)
- AR.js current maintainer
- Decision-maker on ARCore/WebXR integration
- **Talking point:** The maintainer's dilemma — scarce resources, what to prioritize

### Secondary: dogzilla (@dogzilla)
- MindAR fork maintainer
- Community voice on open-source vs. commercial
- **Talking point:** "We just forked it and started hacking on it"

### Secondary: param-fsd (@param-fsd)
- MindAR tracking stability researcher
- Documents the gap between open-source and commercial tracking quality
- **Talking point:** "8thWall and MyWebAR apply smoothing that MindAR doesn't — here's what that means for presence"

---

## Closing Reflection

> "The 20ms rule is either a physical limit or a cultural norm. If it's the former, we need fundamentally new approaches. If it's the latter, we need to be honest about when we're 'helping' the brain versus deceiving it. Either way, the question isn't just engineering — it's ethics."

---

*Research compiled from GitHub issues across ValveSoftware/openvr, google-ar/arcore-android-sdk, microsoft/MixedRealityCompanionKit, AR-js-org/AR.js, hiukim/mind-ar-js, and polygraphene/ALVR.*