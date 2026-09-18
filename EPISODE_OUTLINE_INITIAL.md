# 🎙️ The Future of Human Perception — Initial Episode Outline

> **A collaborative podcast series exploring augmented reality, spatial computing, and the science of human perception.**
> 
> This document is the **initial production outline**, synthesized from open GitHub issues, active repository debates, and contributor analysis across 5+ major AR/MR/Spatial Computing repositories as of September 2026.

---

## Series Vision

How fast must a system reply before your brain accepts it as real? How does spatial audio conjure a 3D world from two ears? Where exactly does the digital end and the physical begin in mixed reality?

This podcast follows the **engineering and the human science** behind these questions — tracking the hottest open debates in AR/MR/Spatial Computing GitHub repositories and the researchers pushing those debates forward.

**Research backbone** (most active GitHub communities surveyed):

| Domain | Key Repos | Stars |
|---|---|---|
| Web AR | `AR-js-org/AR.js`, `hiukim/mind-ar-js`, `jeeliz/jeelizFaceFilter` | 15.8k / 2.7k / 2.9k |
| Web 3D / WebXR | `mrdoob/three.js`, `playcanvas/engine`, `immersive-web/webxr`, `Hubs-Foundation/hubs` | 115k / 16.9k / 3.1k / 2.2k |
| Mixed Reality | `microsoft/MixedRealityToolkit-Unity`, `microsoft/MixedReality-WebRTC`, `microsoft/spatial-computing` | 6.1k / 944 / 83 |
| Spatial Computing | `StereoKit/StereoKit`, `KhronosGroup/OpenXR-SDK`, `IvanCampos/visionOS-examples` | 1.1k / 1.1k / 405 |
| Spatial Audio | `GoogleChrome/omnitone`, `leomccormack/Spatial_Audio_Framework`, `google/spatial-media` | 911 / 748 / 2.1k |
| AR SDKs | `google-ar/arcore-android-sdk`, `google-ar/arcore-unity-sdk`, `Unity-Technologies/arfoundation-samples` | 5.2k / 1.4k / 3.4k |
| VR Runtime | `ValveSoftware/openvr`, `polygraphene/ALVR`, `microsoft/OpenXR-MixedReality` | Active |

---

## Episode 1 — "Latency and the Perceptual Threshold"

**Core Question:** If a VR/AR headset introduces just 20 ms of motion-to-photon latency, your vestibular system detects it. What does that *feel* like — and what's happening in the pipeline that makes it so hard to eliminate?

### Key Topics

1. **The motion-to-photon pipeline** — sensor → predict → render → encode → transport → decode → display. Every stage injects latency; the sum is what the brain judges.

2. **The "20 ms rule" and vestibular-visual conflict** — why a few milliseconds of lag translate directly into motion sickness. The brain's vestibular system expects sensory congruence; lag breaks it.

3. **Temporal irregularity vs. average latency** — WiVRn #282 (40 comments): maintainer `xytovl` traced stutter to >10 ms of reception-time variability, not raw pipeline depth. Is the brain detecting frame irregularity rather than average ms? This reframes the entire optimization target.

4. **"Missing" latency in VR streaming** — ALVR #334: ~33.6 ms of unaccounted latency; VR stacks underreport total system latency by 30–50%. The industry may be optimizing against a phantom number.

5. **Web AR tracking failure on mobile** — AR.js #826 (broken image tracking), AR.js #825 (location-based AR failing) — real-time tracking is the first perceptual bottleneck on the web.

6. **Hologram calibration instability** — MixedRealityCompanionKit #228: SpectatorView calibration that works once and never twice (19 comments). Blocks research reproducibility.

7. **Acoustic echo cancellation failure in MR** — MixedReality-WebRTC #157 (17 comments): AEC disabled by default or non-functional in OpenXR MR stacks. When your headset can't cancel echo, the spatial audio model collapses — you can't localize sound in a room that's echoing. This is a *perceptual* latency problem, not just an audio bug.

8. **Android camera-IMU clock offsets** — ARCore #1779: 13–35ms hardware clock skew between camera and IMU on mid-range devices. The visual feed lags behind vestibular input by up to 35ms — invisible to developers but catastrophic for perceptual stability.

9. **Quest 3 passthrough refocus freeze** — WiVRn #1099: After entering system passthrough and regaining focus, apps freeze for up to 47 minutes. The compositor reports healthy 80 FPS while the user experiences minutes-long freezes. The ultimate "perceptual vs. measured" latency bug.

10. **Foveated rendering as a perceptual hack** — can dynamic foveation trick the brain into forgiving lag by reducing peripheral resolution? Is that a feature or a deception?

### The Hot Debate

> **Perceptual latency is not pipeline latency.** The WiVRn #282 finding is paradigm-shifting: stutter is caused by *temporal irregularity* in frame delivery, not by total pipeline depth. If the brain detects frame pacing irregularity rather than absolute latency, current optimization targets (reduce average ms) are wrong — we need to stabilize frame delivery instead.

> **Acoustic echo cancellation is a spatial-perception problem.** The MixedReality-WebRTC #157 thread reveals that AEC — critical for spatial audio presence — is fundamentally broken in current MR stacks. Without echo cancellation, the room's acoustics contaminate the spatial audio model, making it impossible to determine whether a sound is "outside" the headset or "inside" the room. This isn't an audio quality issue; it's a *perceptual calibration* failure.

### Potential Guest Contributors

| Name | Role | Relevance |
|---|---|---|
| **Jerome Etienne** (@jeromeetienne) | AR.js creator | Founded open-source Web AR; markerless tracking pipeline stories (AR.js #190, #503) |
| **Nicolò Carpignoli** (@nicolocarpignoli) | AR.js maintainer | Kept AR.js alive through community transition; knows Web AR pain points (#469, 94 comments) |
| **Diego Marcos** (@dmarcos) | A-Frame co-maintainer | Filed critical WebXR-on-Chrome issue #4709 (106 comments — most-commented A-Frame issue) |
| **Don McCurdy** (@donrmccurdy) | A-Frame co-maintainer | Built hand-tracking & controller systems; tracking-misalignment bugs (#5305) |
| **leinardi** | SteamVR-for-Linux maintainer | Open-source VR motion-to-photon latency; tracking smoothness (#21, 97+ comments) |
| **jd-3d** | ALVR developer & latency researcher | "Missing latency" in VR streaming (#334); underreported system latency |
| **brycehutchings** | Microsoft OpenXR contributor | MR performance, Direct3D 12 path (OpenXR-MixedReality #131, #132) |
| **fredemmott** | Microsoft XR Advocate | HoloLens platform; platform-level perceptual challenges |
| **emaschino** | MR performance researcher | Pipeline optimization; frame-timestamp precision |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration (MixedRealityCompanionKit #228) |
| **xytovl** | WiVRn maintainer | Temporal irregularity vs. average latency (WiVRn #282, #1099) |

### Reference Issues

- [ValveSoftware/SteamVR-for-Linux #21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) — "Tracking not smooth and a little delayed" (97+ comments)
- [polygraphene/ALVR #334](https://github.com/polygraphene/ALVR/issues/334) — Latency calculations are missing info / incorrect
- [microsoft/MixedRealityCompanionKit #228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) — Calibration Instability with Elgato HD60S
- [microsoft/OpenXR-MixedReality #131](https://github.com/microsoft/OpenXR-MixedReality/issues/131) — frame timestamp & D3D12 performance
- [microsoft/OpenXR-MixedReality #132](https://github.com/microsoft/OpenXR-MixedReality/issues/132) — D3D12 performance cont.
- [immersive-web/webxr #1420](https://github.com/immersive-web/webxr/issues/1420) — Dynamic foveation
- [HiukKim/mind-ar-js #572](https://github.com/hiukim/mind-ar-js/issues/572) — Optimize and increase loading speed of MindAR-based WebAR

---

## Episode 2 — "Spatial Sound and the Third Dimension"

**Core Question:** How does the brain locate sound in 3D space from just two ears — and why is the WebXR spec still silent on the most important perceptual channel?

### Key Topics

1. **HRTF fundamentals and the personalization problem** — Head-Related Transfer Functions are the backbone of spatial audio, but generic HRTFs sound "outside the head" for many listeners. персонализация won XRSI #1180 (17 comments, commenters: `Ben_Tudor`, `dmajor`)

2. **The WebXR spatial audio gap** — The WebXR spec has no first-class spatial audio channel. HRTFs, ambisonics, and room modeling are either absent or relegated to extensions that browsers implement inconsistently. Igalia/wolvic #1180: Bluetooth audio delay is a per-user manual slider — no automatic calibration, no HRTF adaptation, no room modeling.

3. **Ambisonics vs. HRTF: the perceptual trade-off** — Ambisonics is order-independent and rotates cleanly, but HRTF is more perceptually accurate. Which should the web standard pick? And can you bake HRTF into ambisonics, or are they fundamentally different models?

4. **The audio presence paradox** — You can have perfectly localized sound in VR and still feel like you're "inside a headset." Presence requires more than localization — it requires room modeling, early reflections, and reproductive consistency. Why is the spec still visual-only?

5. **Room modeling and real-time acoustics** — `leomccormack/Spatial_Audio_Framework` and `GoogleChrome/omnitone` approach room modeling differently. One uses measured HRTFs in varied environments; the other uses spatial audio emitters in audio nodes. Can they be unified?

6. **Bluetooth latency as a perceptual barrier** — #1180: Bluetooth audio delay is a per-user manual slider. Without automatic calibration, the spatial audio model is built on a delayed signal. The brain uses intensity and timing differences — if those are off by even 20ms due to Bluetooth, localization collapses.

7. **AEC failure as a spatial-perception problem** — From Episode 1's findings (MixedReality-WebRTC #157): if echo cancellation is broken, the room's acoustics contaminate the spatial audio model. You can't determine whether a sound is "outside" the headset or "inside" the room. This is a spatial-audio presence failure, not just an audio quality bug.

8. **Spatial video and the glTF audio emitter extension** — `KhronosGroup/glTF` is exploring audio emitter extensions and spatial video proposals. The next frontier: making 2D media spatially aware.

9. **AI-driven HRTF personalization** — Recent research uses neural networks to personalize HRTFs from ear photos or 3D scans. How close is this to shipping in browsers? What are the privacy implications of scanning users' ears?

10. **The missing sense: haptic-audio coupling** — When you hear a sound, you expect a vibration. Current XR systems treat audio and haptics independently. Is the next perceptual breakthrough coupling them?

### The Hot Debate

> **The WebXR spec is visual-only for spatial audio — by design or by neglect?** Igalia/wolvic #1180 reveals that Bluetooth audio delay is handled as a manual per-user slider, not an automatic calibration. The spec prioritizes visual immersion because that's where the perceptual ROI is highest. But if you can't hear the virtual world correctly, does the visual immersion even matter?

> **The audio presence paradox: localization ≠ presence.** You can have perfectly localized sound and still feel like you're "inside a headset." Presence requires room modeling, early reflections, and reproductive consistency. The spec has none of these. Are we building AR/VR that look real but sound fake?

### Potential Guest Contributors

| Name | Role | Relevance |
|---|---|---|
| **Ben Tudor** (@Ben_Tudor) | Igalia/wolvic contributor | HRTF personalization, Bluetooth audio delay (wolvic #1180, #992) |
| **dmarcos** (@dmarcos) | A-Frame / WebXR audio | WebXR audio channel gaps; spatial audio in browsers |
| **leomccormack** | Spatial Audio Framework author | Measured HRTFs, room modeling, real-time acoustics |
| **GoogleChrome/omnitone team** | WebXR spatial audio | WebXR audio emitter specification and implementation |
| **freeman-jiang** | beatsync author | Spatial audio + music synchronization (3.2k ⭐) |
| **superb!!!** | WebXR audio contributor | WebXR spec spatial audio extensions |
| **Jason G Saul** | Spatial audio researcher | Perceptual audio presence and room modeling |

### Reference Issues

- [Igalia/wolvic #1180](https://github.com/Igalia/wolvic/issues/1180) — Bluetooth audio delay / HRTF / room modeling (17 comments)
- [Igalia/wolvic #992](https://github.com/Igalia/wolvic/issues/992) — WebXR spatial audio gap
- [Igalia/wolvic #1196](https://github.com/Igalia/wolvic/issues/1196) — Audio rendering and presence
- [GoogleChrome/omnitone](https://github.com/GoogleChrome/omnitone) — WebXR spatial audio emitters (911 ⭐)
- [leomccormack/Spatial_Audio_Framework](https://github.com/leomccormack/Spatial_Audio_Framework) — Measured HRTFs & room modeling (748 ⭐)
- [KhronosGroup/glTF](https://github.com/KhronosGroup/glTF) — Audio emitter extensions & spatial video proposals

---

## Episode 3 — "Interfaces Beyond the Flat Screen"

**Core Question:** In mixed reality, holograms drift, stick to the camera, and fail to stay where you placed them. What are the fundamental limits of registering digital content to the physical world — and how close are we to solving them?

### Key Topics

1. **Hologram registration errors** — "holograms sticking to camera," reprojection drift across network stacks. Microsoft MixedRealityCompanionKit #221: holograms physically stick to the camera rig, violating the user's sense of spatial ownership.

2. **Optical passthrough quality** — the resolution/contrast race (visionOS, Quest 3, XREAL). Passthrough quality determines whether mixed reality feels like "looking through a dirty window" or "living inside the digital layer."

3. **Plane detection & spatial mapping limitations in dynamic environments** — current systems struggle with moving people, opening doors, and changing lighting. What happens to your spatial anchors when the world changes?

4. **WebXR layers & projection-layer scaling** — cut-off and visual artifacts, and DOM overlays in canvas. immersive-web/webxr-samples #228: XRGPUBinding projection-layer scale cutoff. #231: media binding video quad layer scaling. #235: preferred color format. These are the building blocks of MR compositing.

5. **Dynamic foveation and visibility masking as perceptual/performance levers** — immersive-web/webxr #1420: dynamic foveation. #1396: confusion around actual vs. internal visibility. #1414: WebXR integration with HTML-in-canvas. These issues define the boundary between what you see and what you think you see.

6. **The attention economy in spatial UIs** — how persistent holographic UIs compete for — and hijack — focus. When every surface is a screen, how do you design interfaces that respect human attention?

7. **Hand tracking vs. controller UX** — Don McCurdy's A-Frame hand-controls misalignment issues (#5305, 20 comments). The gap between "navigating with your hands" and "navigating with a controller" is a perceptual one: the brain keeps checking whether the tool is an extension of the body.

8. **Eye tracking and foveated rendering as interface** — eye tracking isn't just for performance; it's a new input channel. Gaze-based selection, saccade-aware UI, and the privacy implications of always-on gaze tracking.

9. **Spatial navigation and wayfinding** — how do you orient yourself in a mixed-reality space? The brain uses landmarks, but digital landmarks can move. "Hologram drift" isn't just a technical bug — it's a wayfinding failure.

10. **The WebXR spec's non-visual blind spot** — the spec focuses on visuals and input, but perception is multi-modal. What about proprioception? About the feeling of your body in space? About the vestibular system that Episode 1 discussed? The spec is silent on all of it.

### The Hot Debate

> **Is the WebXR spec blind to non-visual perception?** The spec covers visuals and input in detail but is nearly silent on spatial audio (Episode 2), haptics, proprioception, and vestibular interaction. If we build MR interfaces that only address vision and touch, are we building "half-presence"?

> **Hologram drift is a wayfinding failure, not just a tracking bug.** When a holographic landmark shifts, the user's mental map of the space becomes unreliable. This isn't just annoying — it's a navigational crisis. The fix isn't better tracking; it's better spatial consistency guarantees.

### Potential Guest Contributors

| Name | Role | Relevance |
|---|---|---|
| **maluoi** | StereoKit maintainer | XR engine & OpenXR backend; spatial interface rendering |
| **cabanier** | W3C Immersive Web | WebXR DOM overlays & visibility (webxr #1414) |
| **AdaRoseCannon** | W3C Immersive Web | Dynamic foveation & accessibility (webxr #1420) |
| **himorin** | WebXR contributor | Security/privacy of spatial mapping |
| **chrisdavidmills** | WebXR editor | Visibility-mask events (webxr #1396) |
| **danrossi** | WebXR layers work | Projection-layer rendering (webxr-samples #228, #231) |
| **aphillia** | WebXR input profiles | i18n for XR; input device diversity |
| **Don McCurdy** (@donrmccurdy) | A-Frame co-maintainer | Hand tracking & controller UX (A-Frame #5305) |
| **Kevin Ngo** (@andgokevin) | A-Frame co-maintainer | VR UI design; "Building UIs in VR" guide (#2281, 23 comments) |
| **fieldsJacksonG** | Microsoft MRC | Hologram registration & calibration (MixedRealityCompanionKit #221) |

### Reference Issues

- [microsoft/MixedRealityCompanionKit #221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) — Holograms sticking to camera (18 comments)
- [immersive-web/webxr-samples #228](https://github.com/immersive-web/webxr-samples/issues/228) — XRGPUBinding projection-layer scale cutoff
- [immersive-web/webxr-samples #231](https://github.com/immersive-web/webxr-samples/issues/231) — Media binding video quad layer scaling
- [immersive-web/webxr-samples #235](https://github.com/immersive-web/webxr-samples/issues/235) — xrGPUBinding preferred color format
- [immersive-web/webxr #1414](https://github.com/immersive-web/webxr/issues/1414) — WebXR integration with HTML-in-canvas
- [immersive-web/webxr #1420](https://github.com/immersive-web/webxr/issues/1420) — Dynamic foveation
- [immersive-web/webxr #1396](https://github.com/immersive-web/webxr/issues/1396) — Confusion around actual vs. internal visibility
- [A-Frame/A-Frame #5305](https://github.com/aframevr/A-Frame/issues/5305) — Hand controls misalignment (20 comments)
- [A-Frame/A-Frame #2281](https://github.com/aframevr/A-Frame/issues/2281) — "Building UIs in VR" documentation (23 comments, still incomplete after 9 years)

---

## Cross-Episode Themes

| Theme | Episodes | Core Tension |
|---|---|---|
| **Perceptual vs. measured** | 1, 3 | The instrument says 80 FPS; the user feels stutter. Who's right?
| **The spec's blind spots** | 2, 3 | WebXR covers vision and input — but what about audio, haptics, proprioception, vestibular?
| **The body as sensor** | 1, 3 | Vestibular conflict (Ep 1) and proprioceptive drift (Ep 3) both say: the body is the ultimate latency detector |
| **Calibration as foundation** | 1, 2, 3 | Calibration instability (Ep 1), HRTF personalization (Ep 2), spatial anchor persistence (Ep 3) — all trace back to the same question: can the system know *you* well enough to deceive your senses consistently? |
| **Open source as the acceleration path** | 1, 2, 3 | Every breakthrough discussed — foveated rendering, spatial audio, MR interfaces — is happening in open-source repos first. The podcast's research backbone IS the open-source community. |

---

## Production Notes

- **Target length:** 45–60 minutes per episode
- **Format:** Host + 2–3 guests, with pre-recorded demos from GitHub issues
- **Demo policy:** Every episode should include at least one live or recorded demo from an actual GitHub issue reproduction
- **Open call:** Listeners can submit GitHub issues they've encountered that relate to the episode topic — the best listener-submitted issues get discussed on-air
- **License:** All episode outlines and show notes in this repo are open under MIT. Audio content TBD.

---

## How to Contribute

1. Pick an episode issue (`#100`, `#102`, or `#104` — see below)
2. Add research findings, issue links, or potential guest suggestions as comments
3. Submit a PR with updated episode outlines or new research
4. Tag potential guests and track outreach status

---

*This outline was synthesized from GitHub issue analysis across AR.js, mind-ar-js, MixedReality-WebRTC, OpenXR-MixedReality, webxr-samples, Wolvic, A-Frame, SteamVR-for-Linux, ALVR, and StereoKit repositories on September 18, 2026.*