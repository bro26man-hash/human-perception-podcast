# 🔊 Episode 2: "Spatial Sound & the Third Dimension — Sound as the Ultimate Spatial Sense"

---

## Synopsis

WebXR was built for visuals. Spatial audio — the sense that makes you feel like you're *inside* a world rather than *watching* one — is either absent from the spec or relegated to inconsistent browser extensions. This episode investigates why the most important sense for presence is the one the spec ignores, and whether SDK-level innovation can bridge the gap before the next generation of XR hardware ships.

---

## Talking Points

### 1. The WebXR Audio Gap
- No `XRSoundLayer` in the specification
- No HRTF API, no ambisonic encoding, no room modeling
- Visual compositing has Layers; audio has nothing
- "The spec prioritizes visual immersion because that's where the perceptual ROI is highest"

### 2. Bluetooth Audio Delay — A Per-User Manual Slider
- Wolvic issue #1180: users manually tune latency compensation
- No automatic calibration, no HRTF adaptation, no room modeling
- Just a raw number that users must tune themselves
- What does this say about how seriously spatial audio is taken?

### 3. The Resolution Asymmetry
- 8K HEVC on Quest 2 for visuals
- 48kHz mono audio accepted as "good enough"
- The visual arms race has no audio parallel
- Is this a market assumption or a perceptual hierarchy?

### 4. HRTF Personalization
- Default HRTFs feel "off" because they're averaged
- Individual head shape, ear geometry, and torso size affect spatial perception
- Personalized HRTFs could be the difference between "cool tech" and "I believe this is real"

### 5. SDK-Level Innovation vs. Spec-Level Stagnation
- facebook/immersive-web-sdk has spatial audio as a first-class system
- They've BUILT what the spec doesn't have
- "Same code, two experiences" — SDK innovation can outpace spec stagnation
- But: who maintains the SDK when the spec catches up?

### 6. 3D LLMs as a Bridge
- SpatialLM (NeurIPS 2025) processes point clouds to generate structured 3D scene understanding
- Could semantic world understanding enable better spatial audio?
- If machines can "understand" space, can they also "render" sound for it?

### 7. The Presence Paradox
- Visual immersion without spatial audio creates an uncanny valley
- You see the world but can't hear your way around it
- The brain catches the mismatch faster than you'd think

---

## Demo Ideas
- **Binaural vs. stereo comparison:** Show listeners the difference between flat audio and spatial audio
- **HRTF personalization demo:** How changing head-related transfer functions changes presence
- **WebXR spatial audio prototype:** Live demo of a WebXR app using SDK-level spatial audio

---

## Key GitHub Issues to Reference
| Issue | What It Reveals |
|-------|------------------|
| [Igalia/wolvic #1180](https://github.com/Igalia/wolvic/issues/1180) | Bluetooth audio delay is a manual slider — no automatic calibration |
| [Igalia/wolvic #992](https://github.com/Igalia/wolvic/issues/992) | WebXR Layers are visual-only — audio has no spec representation |
| [Igalia/wolvic #1196](https://github.com/Igalia/wolvic/issues/1196) | 8K HEVC visual quality vs. "good enough" audio |
| [google/spatial-media spatial-audio-rfc](https://github.com/google/spatial-media/blob/main/docs/spatial-audio-rfc.md) | Spatial audio metadata RFC exists but has no WebXR integration |
| [facebook/immersive-web-sdk](https://github.com/facebook/immersive-web-sdk) | SDK-level spatial audio as first-class system |

---

## Guest Notes

### Primary: Yongsen Mao (@manycore-research)
- Lead researcher, SpatialLM (NeurIPS 2025)
- 3D LLM for spatial perception — processes point clouds, generates structured scene understanding
- Paper: [arxiv.org/abs/2506.07491](https://arxiv.org/abs/2506.07491)
- Dataset: [HuggingFace](https://huggingface.co/datasets/manycore-research/SpatialLM-Dataset)
- **Talking point:** "Can 3D LLMs replace traditional SLAM? How close are we to machines that truly 'understand' space?"
- **Bridge question:** Could semantic understanding enable spatial audio rendering that currently can't exist?

### Secondary: facebook/immersive-web-sdk team
- Built spatial audio when the spec didn't have it
- **Talking point:** "We stopped waiting for the spec and started building"

### Secondary: google/spatial-media maintainers
- Know the spatial audio RFC inside and out
- **Talking point:** "The gap between 'documented' and 'implemented' is the episode"

---

## Closing Reflection

> "If we can't get the spec to represent spatial audio as a first-class concept, are we building associative solutions or architectural ones? And more importantly: is the absence of spatial audio in WebXR a scope decision, or a perceptual discrimination?"

---

*Research compiled from GitHub issues across Igalia/wolvic, french/immersive-web-sdk, google/spatial-media, and the SpatialLM research project.*