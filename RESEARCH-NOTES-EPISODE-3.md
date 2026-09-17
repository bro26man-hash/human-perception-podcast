# Research Notes — Episode 3: "Interfaces Beyond the Flat Screen"

## Key GitHub Sources

### MixedRealityCompanionKit #228 — SpectatorView Calibration
- **URL:** https://github.com/microsoft/MixedRealityCompanionKit/issues/228
- **Status:** Open, 19 comments
- **Key insight:** SpectatorView calibration works once and never again. Hologram registration instability — even 2-3mm drift breaks the "presence" illusion.
- **Perception angle:** Blocks research reproducibility. If calibration can't be trusted, how can we measure presence?

### AR.js #833 — City-Scale Markerless AR
- **URL:** https://github.com/jeromeetienne/AR.js/issues/833
- **Status:** Open, 1 comment
- **Key insight:** "How to create Markerless AR visible in the entire territory of a city?" GPS + IMU + visual fusion can't yet achieve persistent, cm-accurate world-locked content at city scale.
- **Perception angle:** The web platform doesn't expose sensor fusion, SLAM, or spatial mapping APIs that native MR stacks take for granted.

### MixedRealityToolkit-Unity #82 — Input Threshold (cross-episode with Episode 1)
- **URL:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/82
- **Key insight:** triggerPressed fires in natural hand position. Input threshold is a perceptual question.

### vladmandic/human #530 — Hand Tracking Stability
- **URL:** https://github.com/vladmandic/human/issues/530
- **Status:** Open
- **Key insight:** WASM backend initialization failures affect hand/finger tracking. Core MR interaction modality has stability issues.

### microsoft/MixedRealityToolkit-Unity #11845 — Holographic Remoting Crash
- **URL:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/11845
- **Status:** Open
- **Key insight:** MR interaction stacks break in unpredictable ways when pushed past their design envelopes.

### immersive-web/webxr #390 + #815 — Cross-Cutting Spec Bias (cross-episode)
- **URL:** https://github.com/immersive-web/webxr/issues/390 + https://github.com/immersive-web/webxr/issues/815
- **Key insight:** Both issues connect — the WebXR spec is structurally visual-biased. Audio and haptic channels are second-class citizens.

## Guest Contact Notes
- **jeromeetienne**: AR.js creator. The most prominent web AR voice. Can speak to the gap between web AR and native MR.
- **hiukim**: MindAR creator. On-device tracking for production AR.
- **keveleigh**: MRTK lead. Can speak to input design philosophy and the gap between hardware capabilities and perceptual design.
- **ryan-motive**: MRTK contributor. Filed the trigger sensitivity issue. Can speak to the interaction design process.
- **toji**: WebXR spec editor. Can speak to structural reasons for spec visual bias.

## Unanswered Questions for Script
1. Is the WebXR spec's visual-only design a bug or a feature? Who decides what senses get API support?
2. Can city-scale AR ever work on the web, or is it inherently a native platform problem?
3. What's the right input threshold for MR? Is it perceptual (rubber hand illusion) or ergonomic?
4. Does hand tracking reliability determine whether the brain accepts virtual content as "real"?