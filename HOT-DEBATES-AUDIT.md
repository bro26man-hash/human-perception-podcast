# Hot Debates Audit — September 2026 Update

> Live audit of the fiercest open debates across the most active AR/MR/Spatial Computing repos, mined 2026-09-15. Each entry links to the actual GitHub issue so contributors can follow along and add insights.

---

## 🔥 Episode 1 — Perceptual Latency

### 1. WiVRn #1099 — Future Per-Client Scheduled Frames Stall `xrEndFrame` After Refocus (40+ comments, 15+ reactions)
**Status:** 🟢 ACTIVE & HOTTEST  \
**What's happening:** After a Quest 3 enters system passthrough and regains focus, VRChat and other apps freeze for up to 47 minutes. Monado's `wait_for_scheduled_free()` holds per-client frame slots scheduled *days* in the future. The compositor itself stays healthy at 80 FPS — this is a per-client scheduling bug, not a global stall.  \
**Perception impact:** This is the ultimate "perceptual vs. measured" latency bug. The system reports healthy frame rates, but the user experiences minutes-long freezes. The brain's vestibular system certainly notices.  \
**Maintainer:** @xytovl (Xytovl, WiVRn creator)  \
**Guests to watch:** @xytovl, @IceyMint (reporter), @maxkojju (Pico GPU issues reporter)  \
**Read more:** https://github.com/WiVRn/WiVRn/issues/1099

### 2. WiVRn #1078 — 144/207/240Hz Support for Quest 3 (1 comment)
**Status:** 🟡 ACTIVE  \
**What's happening:** The Quest 3 panel now supports higher refresh rates via firmware update. WiVRn needs a UI toggle and ADB-based preset for >207Hz modes. Higher refresh rates = lower per-frame latency = reduced motion-to-photon jitter.  \
**Perception impact:** Refresh rate is the most direct hardware lever for perceptual latency. 120Hz→240Hz cuts frame time from 8.3ms to 4.2ms — nearly halving the perceptual gap.  \
**Reported via:** @zoeleu  \
**Read more:** https://github.com/WiVRn/WiVRn/issues/1078

### 3. ValveSoftware/SteamVR-for-Linux #21 — "Tracking Not Smooth and a Little Delayed" (97+ comments)
**Status:** 🟡 ACTIVE (foundational)  \
**What's happening:** Community-reported lag between head movement and rendered frame. 97+ comments from users describing nausea-inducing lag.  \
**Perception impact:** Even "smoothed" tracking can't hide the gap between head motion and visual feedback.  \
**Read more:** https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21

### 4. ALVR #334 — Latency Measurements Are Missing Info / Incorrect
**Status:** 🟡 ACTIVE  \
**What's happening:** Community finding that VR streaming stacks underreport total system latency by 30–50%.  \
**Perception impact:** If we're optimizing against the wrong number, the "20 ms rule" may be unreachable in practice even when reported numbers look fine.  \
**Read more:** https://github.com/polygraphene/ALVR/issues/334

### 5. google-ar/arcore-android-sdk #1779 — Camera↔IMU Clock Offset 13–35ms on Xiaomi/OPPO
**Status:** 🟢 ACTIVE  \
**What's happening:** Hardware clock synchronization between camera and IMU introduces 13–35ms offsets on mid-range Android devices.  \
**Perception impact:** This is invisible to the developer but catastrophic for perceptual stability — the visual feed lags behind vestibular input by up to 35ms.  \
**Read more:** https://github.com/google-ar/arcore-android-sdk/issues/1779

### 6. microsoft/OpenXR-MixedReality #131 & #132 — Frame Timestamp Precision & D3D12 Performance
**Status:** 🟡 ACTIVE  \
**What's happening:** HoloLens 2 frame-timestamp precision issues and Direct3D 12 performance regressions.  \
**Perception impact:** D3D12 should reduce latency, but on HoloLens it introduces instabilities that break perceptual continuity.  \
**Read more:** https://github.com/microsoft/OpenXR-MixedReality/issues?q=is%3Aissue+131

---

## 🔥 Episode 2 — Spatial Audio

### 1. GoogleChrome/omnitone #2 — Support for Mobile Browsers (23 comments, open since 2016)
**Status:** 🔴 OLDEST UNRESOLVED — 10 YEARS!  \
**What's happening:** The Chrome Omnitone spatial audio library doesn't work on mobile browsers. 23 comments across a decade, no resolution.  \
**Perception impact:** Billion mobile users cannot experience any form of 3D audio in the browser. The "spatial" part of WebXR is fundamentally incomplete for audio.  \
**Maintainers:** @orighst, @brandonpjones, @jkarmer (Google Chrome audio team)  \
**Read more:** https://github.com/GoogleChrome/omnitone/issues/2

### 2. immersive-web/webxr #390 — Hook Up CSS / HTML Spatial Audio (open since 2018)
**Status:** 🔴 SPEC GAP — 8 YEARS  \
**What's happening:** The WebXR Device API has no built-in spatial audio specification. CSS/HTML spatial audio for WebXR has been debated since 2018 with no spec progress.  \
**Perception impact:** Web developers must use proprietary extensions (Omnitone, Resonance Audio) for basic spatial audio in XR — there's no W3C standard.  \
**Read more:** https://github.com/immersive-web/webxr/issues/390

### 3. microsoft/MixedReality-WebRTC #573 — ADM2 Does Not Play Sound with Multiple Audio Outputs
**Status:** 🟢 ACTIVE  \
**What's happening:** When mixing spatial audio with communication stacks (WebRTC), the ADM2 audio pipeline breaks with multiple output devices.  \
**Perception impact:** Spatial audio breaks precisely when you need it most — during social XR communication.  \
**Read more:** https://github.com/microsoft/MixedReality-WebRTC/issues/573

### 4. leomccormack/Spatial_Audio_Framework #58 — ISM RIR Incorrect Summing of Bands
**Status:** 🟡 ACTIVE  \
**What's happening:** A fundamental bug in Image Source Method (ISM) room acoustics modeling — bands are summed incorrectly, invalidating perceptual room-acoustics research built on this library.  \
**Perception impact:** Any research using ISM-based room modeling may be measuring incorrect reverb characteristics.  \
**Read more:** https://github.com/leomccormack/Spatial_Audio_Framework/issues/58

### 5. Spatial_Audio_Framework #55 — SONIMO Dataset Loading Bugs
**Status:** 🟡 ACTIVE  \
**What's happening:** The SONIMO HRTF dataset has loading bugs that affect perceptual accuracy of spatial audio rendering.  \
**Read more:** https://github.com/leomccormack/Spatial_Audio_Framework/issues/55

### 6. Hubs-Foundation/hubs #1853 / #2643 / #5057 — Spatial Audio Scales Poorly
**Status:** 🔴 ACTIVE (multi-issue)  \
**What's happening:** Hubs (A-Frame social VR) shows spatial audio degrades with more users: #1853 (30 comments), #2643 (30 comments), #5057 (24 comments).  \
**Perception impact:** Spatial audio quality collapses under CPU load exactly when social presence matters most.  \
**Community:** @misslivirose (audio spatialization & accessibility lead), @robertlong (audio reliability)

---

## 🔥 Episode 3 — Mixed Reality Interfaces

### 1. microsoft/MixedRealityCompanionKit #228 — SpectatorView Calibration Instability (19 comments)
**Status:** 🔴 HOTTEST MR ISSUE  \
**What's happening:** HoloLens ↔ phone photographic calibration that works once and never twice.  \
**Perception impact:** If holograms can't be reliably registered, the brain rejects the illusion. This is a fundamental research reproducibility blocker.  \
**Maintainers:** @fieldsJacksonG, @chrisfromwork  \
**Read more:** https://github.com/microsoft/MixedRealityCompanionKit/issues/228

### 2. microsoft/MixedRealityCompanionKit #221 — Holograms Sticking to Camera (18 comments)
**Status:** 🔴 HOTTEST MR ISSUE  \
**What's happening:** Holograms that "stick to camera" instead of staying anchored reproduce reprojection drift across network stacks.  \
**Perception impact:** This breaks the fundamental promise of mixed reality — digital content that stays where you put it.  \
**Read more:** https://github.com/microsoft/MixedRealityCompanionKit/issues/221

### 3. immersive-web/webxr #815 — Spec Language Precludes Non-Visual Uses (41 comments)
**Status:** 🔴 SPEC GAP  \
**What's happening:** WebXR spec language is heavily vision-centric, leaving accessibility gaps for non-visual XR experiences. 41 comments from the community.  \
**Perception impact:** The spec itself makes assumptions about how humans perceive XR that may exclude spatial audio, haptics, and other modalities.  \
**Read more:** https://github.com/immersive-web/webxr/issues/815

### 4. immersive-web/webxr #992 — Content in Immersive Session Search Around (36 comments)
**Status:** 🔴 WAYFINDING CRISIS  \
**What's happening:** Users in immersive XR sessions can't find content that wasn't visible when they entered — fundamental wayfinding problem.  \
**Perception impact:** Spatial memory and navigation are core human abilities; XR interfaces that break them violate basic perceptual expectations.  \
**Read more:** https://github.com/immersive-web/webxr/issues/992

### 5. MixedRealityToolkit/MixedRealityToolkit-Unity #914 — MX Ink MR Stylus for Meta Quest (feature request)
**Status:** 🟡 ACTIVE  \
**What's happening:** A Meta Quest user is requesting Microsoft's MX Ink stylus support, revealing platform convergence without interface abstraction.  \
**Perception impact:** Input fragmentation means spatial interface designers must choose between ecosystems — breaking cross-platform presence.  \
**Read more:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/914

### 6. MixedRealityToolkit/MixedRealityToolkit-Unity #987 — Missing Docs on HoloLens 2 Mixed Reality Capture (4 comments)
**Status:** 🟡 ACTIVE  \
**What's happening:** Microsoft can't document how to enable mixed reality capture for HoloLens 2.  \
**Perception impact:** How do you document presence if you can't document its reproduction?  \
**Read more:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/987

### 7. MixedRealityToolkit/MixedRealityToolkit-Unity #511 — Vendor Plugin Architecture (high priority)
**Status:** 🟡 ARCHITECTURAL  \
**What's happening:** Should vendor-specific RealityProviders live inside the MRTK core? High-priority architectural decision with 2 active commenters.  \
**Perception impact:** The answer determines whether MR interfaces can be truly cross-platform.  \
**Read more:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/511

### 8. immersive-web/webxr-samples #228/#231/#235 — Projection-Layer Scaling Artifacts
**Status:** 🟢 ACTIVE  \
**What's happening:** WebXR layers produce cut-off and visual artifacts at certain scales. DOM overlays in canvas (#1414) has additional rendering challenges.  \
**Perception impact:** Visual comfort vs. fidelity trade-off in layered XR rendering.  \
**Read more:** https://github.com/immersive-web/webxr-samples/issues/228

### 9. immersive-web/webxr #1420 — Dynamic Foveation & Visibility Masking
**Status:** 🟡 PERCEPTUAL PERFORMANCE LEVER  \
**What's happening:** Dynamic foveation and visibility masking as tools to reduce rendering cost while preserving perceptual quality.  \
**Perception impact:** The brain's foveal resolution is much higher than peripheral — exploiting this perception/performance trade-off is fundamental to scalable XR.  \
**Contributor:** @AdaRoseCannon (W3C, Foveated Rendering CG)  \
**Read more:** https://github.com/immersive-web/webxr/issues/1420

### 10. IvanCampos/visionOS-examples (404★) — Passthrough Quality & SE(3) Anchor Drift
**Status:** 🟡 FREQUENTLY UPDATED  \
**What's happening:** Apple Vision Pro passthrough contrast/resolution limits and SE(3) anchor instability in dynamic environments.  \
**Perception impact:** Optical passthrough quality is the new measurement of MR fidelity — and it's still evolving.  \
**Read more:** https://github.com/IvanCampos/visionOS-examples

---

## 🔄 Cross-Cutting Patterns

| Pattern | Evidence | Episode |
|---|---|---|---|
| **Perceptual ≠ Measured** | ALVR #334, WiVRn #1099, ARCore #1779 | Ep. 1 |
| **Spatial Audio Has No Standard** | webxr #390 (8 yrs), omnitone #2 (10 yrs, 23 comments) | Ep. 2 |
| **MR Registration Fragility** | MRC #228, MRC #221 | Ep. 3 |
| **Spec Accessibility Gap** | webxr #815 (41 comments) | Ep. 2 & 3 |
| **Performance Breaks Presence** | Hubs #1853/#2643/#5057, D3D12 #131 | Ep. 1 & 2 |
| **Platform Convergence Without Abstraction** | MRTK #914, MRTK #511 | Ep. 3 |
| **Cross-Modal Perception** | auditory faster than visual, SONIMO HRTF research | Ep. 2 |
| **Research Reproducibility Crisis** | SpectatorView calibration, ISM bug | Ep. 1 & 2 |

---

## 📊 Engagement Metrics — Top 10 Hottest Issues by Comment Volume

| Rank | Issue | Comments | Age |
|------|-------|----------|-----|
| 1 | Ultralytics #1915 — pose model consistency | 106 | active |
| 2 | SteamVR-for-Linux #21 — tracking lag | 97+ | 7 years |
| 3 | webxr #815 — non-visual accessibility | 41 | active |
| 4 | webxr #992 — wayfinding | 36 | active |
| 5 | Hubs #1853 — spatial audio quality | 30 | active |
| 6 | Hubs #2643 — user audio broken | 30 | active |
| 7 | omnitone #2 — mobile browsers | 23 | 10 years |
| 8 | MRC #228 — calibration | 19 | active |
| 9 | Hubs #5057 — audio at scale | 24 | active |
| 10 | StereoKit #1209 — display returns 0 | 3 | recent |

*Last audited: 2026-09-15 | Maintainer: podcast research team*
