# 🎙️ The Future of Human Perception — Season 1 Episode Outline (Refined)

> **Compiled from GitHub issue analysis across 10+ active AR/MR/Spatial Computing repositories, September 2026.**

---

## About the Series

**The Future of Human Perception** is a collaborative podcast exploring the cutting edge of augmented reality, spatial computing, mixed reality interfaces, and the neuroscience of how humans experience immersive digital environments.

We interview the developers, researchers, and designers who are reshaping how we see, hear, and interact with virtual worlds — and we dig into the open debates that are moving the field forward.

**Research Backbone:** All topics and guest names are sourced from live GitHub issue analysis across AR.js, MindAR, MRTK, WebXR spec, SpatialLM, and 7+ other active repositories.

---

## Season 1 — Three Pilot Episodes

---

### 🔴 Episode 1: "Latency and the Perceptual Threshold"
**Subtitle:** *Can foveation trick the brain into forgiving lag?*

**Core Question:** How much perceptual latency can the human visual system tolerate before AR content feels "wrong," and can predictive rendering or foveal techniques buy us enough headroom?

#### 🔥 Primary Debate: The 20ms Rule vs. The Invisible Pipeline

The "20ms motion-to-photon rule" is the dogma of immersive computing. But GitHub's issue trackers tell a more complicated story:

| Issue | Repo | Key Finding |
|-------|------|-------------|
| [#334](https://github.com/polygraphene/ALVR/issues/334) | ALVR | VR stacks **underreport total system latency by 30-50%** — ~33.6ms of "missing" latency |
| [#1099](https://github.com/WiVRn/WiVRn/issues/1099) | WiVRn | After Quest 3 passthrough reacquisition, VRChat **freezes for 47 minutes** — brain detects pacing irregularity, not just absolute latency |
| [#1779](https://github.com/google-ar/arcore-android-sdk/issues/1779) | ARCore | Camera↔IMU clock offset of **13-35ms** on mid-range Android — invisible to devs, catastrophic for perceptual stability |
| [#816](https://github.com/microsoft/Azure-Kinect-Sensor-SDK/issues/816) | Azure Kinect | Modern cameras have **0.2s latency** vs. 0.02s for Rift S and 0.006s for RealSense — the industry standard is far higher than MR hardware requires |
| [#21](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21) | SteamVR-for-Linux | **97+ comments** from users describing nausea-inducing tracking lag — the most-commented latency issue in VR |

**The Cross-Cutting Pattern:** *Perceptual ≠ Measured.* Every repo in this survey deals with latency that users never notice — until it's there. The best perceptual systems are the ones you never feel.

#### 💰 The Commercial Gap Debate

| Solution | Cost | Tracking Quality | Open Source? | Smoothing? |
|---|---|---|---|---|
| **8thWall** | $750/project | Tuned models | ❌ | ✅ |
| **MyWebAR** | $799/total | Smoothed | ❌ | ✅ |
| **Zappar** | Commercial | Professional | ❌ | ✅ |
| **MindAR** | Free | Jitter without smoothing | ✅ | ❌ |
| **AR.js** | Free | Marker/Geo only | ✅ | ❌ |
| **Encantar.js** | Free | Updated, limited params | ✅ (emerging) | ⚠️ |

> **Key quote from @dogzilla on MindAR #556:** *"Given the option between those prices and jitter, all of my clients so far have chosen to live with the jitter."*

> **Key quote from @param-fsd:** *"In 8th Wall and MyWebAR, the tracking was actually good. I observed that they apply smoothing to the camera movement and content."*

> **Key quote from @nicolocarpignoli on AR.js #217:** *"We are in between where there is no OSS markerless cross-browser Web AR, but we know there will be."*

#### 🎯 Discussion Questions

1. **Is the 20ms rule still valid?** What psychophysics data supports it, and do modern foveated rendering techniques change the math?
2. **Why haven't tracking models improved?** MindAR's last update was January 2024. AR.js is maintained but hasn't addressed the core latency problem. Is this a resource issue or a fundamental technical barrier?
3. **Can community-driven smoothing close the gap?** @param-fsd and @dogzilla are both experimenting with custom smoothing algorithms. Is this viable, or does it require dedicated model tuning?
4. **Should AR.js integrate ARCore/WebXR directly?** @kylebakerio argues yes. @nicolocarpignoli argued the WebXR Device API isn't ready and won't be on Apple "for a lot, probably — another couple of years."
5. **What's the Latency Belt?** Is there a "latency belt" between what open-source Web AR can achieve and what commercial SDKs deliver — and will anyone ever bridge it?

#### 🎙️ Suggested Guest Lineup

| Priority | Guest | GitHub | Angle |
|---|---|---|---|
| ⭐ **Primary** | **hiukim** | @hiukim | MindAR creator — why tracking models haven't been updated; what would it take to fix? |
| ⭐ **Primary** | **Nicolò Carpignoli** | @nicolocarpignoli | AR.js former maintainer — the architectural challenges; "We are in between" — the markerless gap |
| **Secondary** | **@param-fsd** | @param-fsd | MindAR tracking researcher — real-world experimentation with smoothing algorithms |
| **Secondary** | **@dogzilla** | @dogzilla | Community fork maintainer — "We just forked it and started hacking" — the grassroots approach |
| **Secondary** | **@xytovl** | @xytovl | WiVRn maintainer — OpenXR streaming; packet-timing & pacing algorithm design; the WiVRn #1099 frame scheduling crisis |
| **Wildcard** | **@kylebakerio** | @kylebakerio | WebXR/ARCore advocate — the pragmatic case for integrating proprietary frameworks |
| **Wildcard** | **Jay Gullapalli** | @jaygullapalli | Azure Kinect SDK lead — sensor latency engineering; the 0.2s vs 0.006s gap |

#### 📚 Pre-Reading

- [AR.js #498 — Stretched camera feed (50💬)](https://github.com/AR-js-org/AR.js/issues/498)
- [MindAR #556 — Unstable tracking (5💬)](https://github.com/hiukim/mind-ar-js/issues/556)
- [MindAR #526 — Abandonware debate (13💬)](https://github.com/hiukim/mind-ar-js/issues/526)
- [ALVR #334 — Missing latency (33.6ms)](https://github.com/polygraphene/ALVR/issues/334)
- [WiVRn #1099 — 47-minute freeze](https://github.com/WiVRn/WiVRn/issues/1099)
- [ARCore #1779 — Camera↔IMU clock offset](https://github.com/google-ar/arcore-android-sdk/issues/1779)
- [SteamVR-for-Linux #21 — Tracking lag (97💬)](https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21)

---

### 🔴 Episode 2: "Spatial Sound and the Third Dimension"
**Subtitle:** *HRTFs, ambisonics & the audio presence paradox*

**Core Question:** Why does the WebXR specification remain effectively visual-only for spatial audio, and what would it take to make 3D audio a first-class citizen of the immersive web?

#### 🔥 Primary Debate: The Audio Presence Paradox

The WebXR Device API defines spatial tracking, hand interactions, and locomotion — but **has no spatial audio session mode**. There is no standard API for:
- HRTF (Head-Related Transfer Function) configuration
- Ambisonics decoding  
- 3D audio source positioning relative to head tracking
- Personalized auditory rendering

Yet **spatial audio is arguably MORE important than visuals for spatial presence.** A VR experience with perfect visuals but monaural audio feels hollow. A VR experience with imperfect visuals but convincing 3D audio feels *present*.

**The Spec Gap Evidence:**

| Issue | Repo | Age | Comments | What's Missing |
|-------|------|-----|----------|----------------|
| [#390](https://github.com/immersive-web/webxr/issues/390) | webxr | **8 years** | 30 | @cwilso (W3C): Should WebXR hook up sound source nodes with HRTF? |
| [#2](https://github.com/GoogleChrome/omnitone/issues/2) | omnitone | **10 years** | 23 | Mobile browser support still unresolved — binaural rendering is desktop-only |
| [#573](https://github.com/microsoft/MixedReality-WebRTC/issues/573) | MR-WebRTC | Active | — | ADM2 breaks with multiple audio outputs — spatial audio fails during social XR |
| [#58](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58) | SAF | Active | — | ISM RIR band summing bug invalidates perceptual room-acoustics research |
| [#1853](https://github.com/Hubs-Foundation/hubs/issues/1853) | Hubs | Active | 30 | Spatial audio **degrades with more users** — quality collapses when presence matters most |

**The Three Competing Answers:**

| Argument | Proponent | Counter-argument |
|---|---|---|
| "HRTF personalization is too individual" | google/spatial-media | IWSDK proves you CAN ship a default; users can calibrate |
| "The spec should stay render-mode-agnostic" | W3C Immersive Web WG | Audio IS rendering; you can't separate them |
| "SDKs can fill the gap" | Facebook/IWSDK | This fragments the platform — every app builds its own audio stack |
| "3D LLMs will make it moot" | SpatialLM researchers | We need the spec to define HOW LLM outputs connect to audio rendering |

#### 🧠 The Cross-Modal Perception Insight

Research consistently shows that **auditory perception is faster than visual perception** for spatial events. A 40ms audio delay destroys presence MORE than a 20ms visual delay. Yet there is no equivalent WebXR audio latency standard — no "20ms audio rule."

> **Key quote from @leomccormack on SAF #58:** The Image Source Method (ISM) room acoustics model has a fundamental bug in how bands are summed — any research using ISM-based modeling may be measuring **incorrect reverb characteristics**.

> **Key quote from @ThreeDeeJay on OpenAL Soft #1113:** NFC degrades HRTF quality; multi-field SOFA improves it but requires specialized HRTFs. **3DTI sets the gold standard** for personalized spatial audio.

#### 🎯 Discussion Questions

1. **The 50% rule:** If spatial audio contributes more to presence than visual quality, why does WebXR treat it as optional? Is there a cognitive bias toward "visuals = reality" in the working group?
2. **HRTF personalization: fairy tale or necessity?** Can a generic HRTF work for 80% of users, or does the 20% who can't localize with generic HRTFs defeat the purpose?
3. **The IWSDK proof of concept:** Facebook has built spatial audio for WebXR. Why hasn't this been proposed to the W3C? Standards politics or architecture disagreement?
4. **Could SpatialLM be the bridge?** If a 3D LLM can understand room layout, and acoustic simulation can then compute reverb, do we need a "spatial audio spec" — or just a way to feed LLM outputs into ANY audio renderer?
5. **Where is the research reproducibility crisis?** SAF #58 (ISM bug) and #55 (SONIMO dataset bugs) — how many papers on spatial audio perception are built on faulty data?

#### 🎙️ Suggested Guest Lineup

| Priority | Guest | GitHub | Angle |
|---|---|---|---|
| ⭐ **Primary** | **@leomccormack** | @leomccormack | SAF creator — ambisonics, HRTFs & temporal rendering; the ISM bug and SONIMO dataset crisis |
| ⭐ **Primary** | **@cwilso** | @cwilso | W3C Immersive Web member — authored the sound source node proposal (#390); why hasn't it progressed? |
| ⭐ **Primary** | **Yongsen Mao** | @manycore-research | SpatialLM lead (NeurIPS 2025) — Can 3D LLMs generate spatial audio layouts from camera input? |
| **Secondary** | **@orighst (Boris Smus)** | @orighst | Omnitone maintainer / Google — browser-based binaural rendering; why mobile is still broken |
| **Secondary** | **@brandonpjones** | @brandonpjones | Omnitone / Google — Web Audio API spatial rendering; ambisonic codecs |
| **Secondary** | **@jkarmer** | @jkarmer | Omnitone / Google — real-time spatial audio in web browsers |
| **Wildcard** | **@rudybear** | @rudybear | glTF audio extension — KHR_audio layered architecture; TypeScript reference implementation |
| **Wildcard** | **@alankila** | @alankila | EasyEffects — Localization Cue Correction DSP; crossfeed research |
| **Wildcard** | **@ameliaeckard** | @ameliaeckard | Apple Vision Pro — Accessibility via spatial audio; indoor navigation for visually impaired |

#### 📚 Pre-Reading

- [WebXR #390 — Sound source nodes (30💬, 8 years)](https://github.com/immersive-web/webxr/issues/390)
- [Omnitone #2 — Mobile browsers (23💬, 10 years)](https://github.com/GoogleChrome/omnitone/issues/2)
- [Spatial Audio RFC](https://github.com/google/spatial-media/blob/main/docs/spatial-audio-rfc.md)
- [SAF #58 — ISM RIR bug](https://github.com/leomccormack/Spatial_Audio_Framework/issues/58)
- [SAF #55 — SONIMO dataset bugs](https://github.com/leomccormack/Spatial_Audio_Framework/issues/55)
- [Hubs #1853 — Spatial audio quality (30💬)](https://github.com/Hubs-Foundation/hubs/issues/1853)
- [SpatialLM Paper (NeurIPS 2025)](https://arxiv.org/abs/2506.07491)
- [IWSDK — Spatial Audio System](https://iwsdk.dev/)
- [OpenAL Soft #1113 — HRTF proximity](https://github.com/kcat/openal-soft/issues/1113)

---

### 🔴 Episode 3: "Interfaces Beyond the Flat Screen"
**Subtitle:** *MR interfaces, hologram drift & wayfinding*

**Core Question:** Are we designing interfaces for screens that happen to be transparent, or interfaces that actually leverage the geometry of physical space — and what does the WebXR spec get wrong about non-visual perception?

#### 🔥 Primary Debate: The Markerless AR Gap

AR.js supports three tracking modes:
1. **Marker-based** — printed QR-like markers
2. **Image-based (NFT)** — trained image descriptors
3. **Location-based (GeoAR)** — GPS coordinates

**None of these are markerless** — the kind of tracking you see in Google's Model Viewer, Apple's VisionOS, or Magic Leap, where the system understands the real world without any visual or GPS cues.

The question has been open since **[AR.js #217](https://github.com/AR-js-org/AR.js/issues/217) "markerless tracking without tango"** (22💬, filed February 2021). Three years later, no answer.

**What the Contributors Said:**

> **@kylebakerio:** *"AR.js is going to lose relevance if an open source library supports that tech and AR.js doesn't. It's just a matter of time. The original aim included a 'tracking: best' that would use Tango if available, and fall back to other options when not."*

> **@nicolocarpignoli (former maintainer):** *"We are in between where there is no OSS markerless cross-browser Web AR, but we know there will be. If someone wants to put some effort on filling this gap (that will last, at least, another couple of years I guess) I think It will be great. When WebXR Device API will arrive on Apple, with Markerless and other features, probably AR.js markerless solution will be deprecated, because WebXR Device API will be more maintained and standard."*

> **@nickw1:** Pointed to **TrackingJS** as a potential FOSS markerless solution 3 years ago. *"Thorsten Bux gave me this pointer: TrackingJS. It sounds like TrackingJS needs updating to reflect some changes in web camera APIs, but also it looks like it could be used to implement real FOSS markerless AR within AR.js."*

But three years later, no one has executed.

#### 🔥 The Hologram Drift Problem

| Issue | Repo | Comments | What's Broken |
|-------|------|----------|---------------|
| [#278](https://github.com/AR-js-org/AR.js/issues/278) | AR.js | **40💬** | Location-based AR content **sticks to camera** instead of staying anchored — perceptual anchoring failure |
| [#547](https://github.com/AR-js-org/AR.js/issues/547) | AR.js | 16💬 | Android GPS-based AR **floats in random spaces** — platform perception gap |
| [#466](https://github.com/AR-js-org/AR.js/issues/466) | AR.js | 26💬 | iOS compass heading reports differently — AR content appears **rotated** |
| [#228](https://github.com/microsoft/MixedRealityCompanionKit/issues/228) | MRC | **19💬** | HoloLens ↔ phone calibration that **works once and never twice** |
| [#221](https://github.com/microsoft/MixedRealityCompanionKit/issues/221) | MRC | **18💬** | Holograms that **"stick to camera"** instead of staying anchored — reprojection drift across network stacks |
| [#1420](https://github.com/immersive-web/webxr/issues/1420) | WebXR | 3💬 | **Dynamic foveation & visibility masking** — can the renderer cheat the brain by reducing peripheral resolution? |

**Three Schools of Thought on Anchoring:**

| Position | Argument | Proponents |
|---|---|---|
| **"It's a code bug"** | Better math, better filters, better models — we can fix it | @nickw1, @kalwalt |
| **"It's a spec failure"** | WebXR has no concept of persistent spatial anchors that survive GPS drift | @kylebakerio, @nicolocarpignoli |
| **"It's a perceptual assumption"** | We assume space is absolute; maybe AR content should be explicitly semantic (anchored to *concepts*, not *coordinates*) | SpatialLM researchers |

#### 🔥 The Non-Visual Perception Blind Spot

| Perception Channel | WebXR Support | Commercial MR Support |
|---|---|---|
| **Visual** | ✅ Full | ✅ Full |
| **Spatial Audio** | ❌ No session type | ✅ (Samsung, Apple, Meta) |
| **Haptics** | ❌ No standard API | ✅ (controllers, wrist bands) |
| **Proprioception** | ❌ Not addressed | ✅ (hand tracking, body modeling) |
| **Vernacular acoustics** | ❌ Not addressed | ✅ (partial, RoomKit) |

WebXR treats the human as **eyes + hands**. It doesn't model the rest of the perceptual system.

**The Wayfinding Crisis:** [WebXR #992](https://github.com/immersive-web/webxr/issues/992) — 36 comments. Users in immersive XR sessions **can't find content that wasn't visible when they entered**. Spatial memory and navigation are core human abilities; XR interfaces that break them violate basic perceptual expectations.

#### 🧠 The 3D World Model Opportunity

**[SpatialLM](https://github.com/manycore-research/SpatialLM)** (4.7k ⭐, NeurIPS 2025) processes point clouds and generates structured scene understanding:
- Walls, doors, windows, and oriented object bounding boxes
- Supports monocular video, RGBD, and LiDAR inputs
- **Zero-shot detection** on real RGB video from phone cameras

Could SpatialLM provide the **shared world model** that AR.js has been missing? Instead of just tracking markers, AR could understand that there's a wall ahead, a door to the left, and a table in the center — and anchor content to **semantic understanding** rather than geometric drift.

#### 🎯 Discussion Questions

1. **Why has markerless AR taken 5 years and counting?** Is the technical barrier real (SLAM is hard) or political (ARCore/ARKit don't want competition)?
2. **The "tracking: best" vision:** @kylebakerio describes what Jérôme Étienne originally envisioned — use the best available tracker per platform. Why wasn't this built?
3. **TrackingJS and the FOSS path:** @nickw1 found a potential open-source markerless solution 3 years ago. What happened? Is it technically viable in 2026?
4. **iOS vs Android: Can we design for the delta?** The same AR code produces different results on different platforms. Should we accept this, or fight it?
5. **SpatialLM as the new anchor:** If a 3D LLM can say "there's a wall 2 meters ahead and a door to the left," does that replace geometric tracking entirely? Or do we need both?
6. **Haptics and the invisible channels:** WebXR has no haptic API. When was the last time you considered that the Web is *visual*?

#### 🎙️ Suggested Guest Lineup

| Priority | Guest | GitHub | Angle |
|---|---|---|---|
| ⭐ **Primary** | **@jeromeetienne** | @jeromeetienne | AR.js creator — the original vision of `tracking: best` — what happened? |
| ⭐ **Primary** | **@kylebakerio** | @kylebakerio | WebXR/ARCore advocate — the pragmatic case for markerless with ARCore/ARKit |
| **Secondary** | **@nickw1** | @nickw1 | AR.js Location AR contributor — iOS vs Android perception gap, TrackingJS hopes |
| **Secondary** | **Yongsen Mao** | @manycore-research | SpatialLM lead — Can 3D LLMs provide the semantic world model that geometry can't? |
| **Secondary** | **@fieldsJacksonG** | @fieldsJacksonG | Microsoft MRC maintainer — Hologram registration & calibration; SpectatorView instability |
| **Wildcard** | **Thorsten Bux** | — | TrackingJS author — What would it take to update TrackingJS for markerless Web AR? |
| **Wildcard** | **@AdaRoseCannon** | @AdaRoseCannon | W3C — Dynamic foveation & accessibility; authored WebXR #1420 on foveation |

#### 📚 Pre-Reading

- [AR.js #217 — Markerless tracking (22💬)](https://github.com/AR-js-org/AR.js/issues/217)
- [AR.js #278 — Content sticking to camera (40💬)](https://github.com/AR-js-org/AR.js/issues/278)
- [AR.js #547 — GPS floating on Android](https://github.com/AR-js-org/AR.js/issues/547)
- [AR.js #466 — iOS heading correction](https://github.com/AR-js-org/AR.js/issues/466)
- [MRC #228 — Calibration instability (19💬)](https://github.com/microsoft/MixedRealityCompanionKit/issues/228)
- [MRC #221 — Holograms sticking to camera (18💬)](https://github.com/microsoft/MixedRealityCompanionKit/issues/221)
- [WebXR #815 — Spec precludes non-visual uses (41💬)](https://github.com/immersive-web/webxr/issues/815)
- [WebXR #992 — Wayfinding crisis (36💬)](https://github.com/immersive-web/webxr/issues/992)
- [WebXR #1420 — Dynamic foveation](https://github.com/immersive-web/webxr/issues/1420)
- [SpatialLM Paper (NeurIPS 2025)](https://arxiv.org/abs/2506.07491)

---

## 🔄 Cross-Cutting Themes for Season 1

| Theme | Evidence | Episodes |
|---|---|---|
| **Perceptual ≠ Measured** | ALVR #334, WiVRn #1099, ARCore #1779 | Ep 1 |
| **Spatial Audio Has No Standard** | webxr #390 (8 yrs), omnitone #2 (10 yrs, 23 comments) | Ep 2 |
| **MR Registration Fragility** | MRC #228, MRC #221, AR.js #278 | Ep 3 |
| **Spec Accessibility Gap** | webxr #815 (41 comments), #892 (audio-only devices) | Ep 2 & 3 |
| **Performance Breaks Presence** | Hubs #1853/2643/5057, D3D12 #131 | Ep 1 & 2 |
| **Platform Convergence Without Abstraction** | MRTK #914 (MX Ink for Quest), MRTK #511 (vendor plugins) | Ep 3 |
| **Cross-Modal Perception** | auditory faster than visual, SONIMO HRTF research | Ep 2 |
| **Research Reproducibility Crisis** | SpectatorView calibration, ISM bug (SAF #58) | Ep 1 & 2 |
| **The Open-Source Audio Dead End** | google/lullaby (no external PRs), omnitone (desktop-only 8+ yrs), MR-WebRTC (deprecated) | Ep 2 |
| **The Modular vs. Monolithic Debate** | AR.js #681 (ECS architecture — message-passing overhead vs. end-to-end optimization) | Ep 1 |
| **3D LLMs as World Models** | SpatialLM (NeurIPS 2025) — semantic anchoring vs. geometric drift | Ep 3 |

---

## 📊 Season 1 Timeline

| Week | Activity |
|------|----------|
| 1 | Finalize episode outlines, begin guest outreach |
| 2 | Pre-interviews with primary guests; confirm recording dates |
| 3 | Record Episode 1 (Latency); edit and publish |
| 4 | Record Episode 2 (Spatial Audio); edit and publish |
| 5 | Record Episode 3 (MR Interfaces); edit and publish |
| 6 | Season retrospective; plan Season 2 topics |

---

## ✅ Season 1 Action Items

- [ ] Reach out to **hiukim** and **@nicolocarpignoli** for Episode 1 recording
- [ ] Contact **@leomccormack** and **@cwilso** for Episode 2
- [ ] Interview **@jeromeetienne** and **@kylebakerio** for Episode 3
- [ ] Reach out to **Yongsen Mao** (SpatialLM) for Episodes 2 & 3
- [ ] Follow up with **@param-fsd** and **@dogzilla** on smoothing algorithm results
- [ ] Contact **@fieldsJacksonG** about MRC calibration research
- [ ] Research psychophysics studies on motion-to-photon latency thresholds
- [ ] Investigate Whether the W3C has any open drafts for spatial audio in WebXR
- [ ] Document the iOS vs Android AR behavior differences across all open issues
- [ ] Test Encantar.js and document its tracking behavior vs. MindAR

---

*Outline refined September 2026 from GitHub issue analysis across AR-js-org/AR.js, hiukim/mind-ar-js, microsoft/MixedRealityToolkit-Unity, microsoft/MixedRealityCompanionKit, immersive-web/webxr, GoogleChrome/omnitone, leomccormack/Spatial_Audio_Framework, Hubs-Foundation/hubs, manycore-research/SpatialLM, polygraphene/ALVR, WiVRn/WiVRn, ValveSoftware/SteamVR-for-Linux, google-ar/arcore-android-sdk, and microsoft/Azure-Kinect-Sensor-SDK. All claims sourced from actual issue threads and public contributions.*