# 🔥 Hot Debates — Consolidated Audit

Surfaced from open issues across 5 major AR/MR/Spatial Computing repositories.

---

## Debate 1: The 20ms Rule — Is It Real, and Can We Dodge It?

**Source issues:** ValveSoftware/openvr #1012, #1729, #1917, #681

**The claim:** Motion-to-photon latency above 20ms causes discomfort,
nausea, and perceptual disconnection. It's the "speed limit" of presence.

**The counterclaim:** Foveated rendering, motion smoothing, and predictive
display can effectively "hide" latency from the user's conscious perception.
Is that a feature or a deception?

**What the issues reveal:**
- Developers want programmatic control over reprojection (#1012) — but the
  perceptual consequences of forcing vs. allowing smoothing are unresolved
- GPU timestamp corruption on AMD 7900 XTX (#1729) means the timing data
  that drives prediction can be *wrong*, and there's no fallback
- `xrWaitFrame` returning `XR_SUCCESS` with negative `predictedDisplayTime`
  (#1917) means the runtime is telling the app the frame will display in
  the past — a fundamental spec violation that no one has flagged as a
  perceptual emergency
- Playspace rotation limited to yaw-only (#681) may create a perceptual
  disconnect for natural head movement

**Podcast angle:** Is the 20ms rule a hard physical limit or a soft cultural
norm? Should developers be ethically required to disclose when they're
"hiding" latency via reprojection?

---

## Debate 2: Spatial Audio — The Spec's Blind Spot

**Source issues:** Igalia/wolvic #1180, #992, #1196

**The claim:** WebXR has no first-class spatial audio channel. HRTFs,
ambisonics, and room modeling are either absent from the spec or relegated
to extensions that browsers implement inconsistently.

**The counterclaim:** The spec prioritizes visual immersion because that's
where the perceptual ROI is highest. Audio presence is a "nice to have,"
not a "must have."

**What the issues reveal:**
- Bluetooth audio delay is a per-user manual slider (#1180) — meaning
there's no automatic calibration, no HRTF adaptation, no room modeling
just a raw latency compensation number that users must tune themselves
- WebXR Layers (#992) are about *visual* compositing. The lack of an
  equivalent audio layer means spatial audio has no spec representation
  whatsoever — it's an afterthought or an extension, never a primitive
- 8K HEVC on Quest 2 (#1196) — the resolution arms race for visuals hasno parallel in audio. We accept 60fps visual but 48kHz mono audio as
  "good enough"

**Podcast angle:** If we can't get the spec to represent spatial audio as a
first-class concept, are we building associative or architectural solutions?
Should there be a "WebXR Audio Layer 1.0" requirement?

---

## Debate 3: The Interface Paradigm Trap — Are We Still Designing for 2D?

**Source issues:** Igalia/wolvic #1110, #993, #2071; AR-js-org/AR.js #833, #834

**The claim:** Despite being"spatial" computing, XR interfaces are still
designed around 2D paradigms — gamepads, flat screens, and 2D input APIs.
The"three-dimensional" part of 3D interfaces is mostly visual, not interactive.

**The counterclaim:** The gamepad metaphor works because it's learned.
Switching to gaze, voice, or proprioceptive input would create new barriers.

**What the issues reveal:**
- XRControllers must be "flattened" into Gamepad API (#993) — the spatial
  input is reduced to 2D axes before the app ever sees it
- Spatial navigation for D-pads (#1110) assumes a 3D space traversed by
  a 2D input device — the mismatch is acknowledged but unsolved
- Launching immersive elements (#2071) is a Chromium-specific path纠结 —
  the discovery problem for MR content is barely addressed in the spec
- City-scale markerless AR (#833) breaks because the tracking paradigm
  (local SLAM) doesn't scale to global reference frames
- Geospatial AR (#834) needs earth-centered coordinates but AR.jsonly
  handles local tracking

**Podcast angle:** Are we building "3D interfaces with 2D constraints" or
"truly spatial interfaces"? What would the latter even feel like?

---

## Cross-Cutting Theme: The Perceptual Transparency Problem

All three debates surface a deeper question: **when technology hides
perceptual realities from users, is that a feature or a betrayal?**

- Motion smoothing hides latency → is that "immersion enhancement" or
  "sensory deception"?
- Spatial audio omission hides the third dimension → is that "spec scope
  management" or "perceptual discrimination"?
- 2D input masking hides the spatial nature of interaction → is that
  "ergonomic pragmatism" or "paradigm capture"?

This meta-debate should frame every episode's closing reflection.
