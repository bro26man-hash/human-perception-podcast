# GitHub Research Addendum — The Future of Human Perception

> Research conducted 2026-09-12. Hot issues, contributor names, and debate topics mined from the most active AR/MR/Spatial Computing repositories on GitHub.

## Repositories Surveyed

| Repository | Stars | Language |Focus |
|---|---|---|---|
| jeromeetienne/AR.js | 15,791 | HTML | Web AR — marker-based & location-based |
| playcanvas/engine | 16,703 | JavaScript | Web graphics runtime (WebGL/WebGPU/WebXR) |
| microsoft/MixedRealityToolkit-Unity | 6,076 | C# | MRTK for HoloLens & immersive headsets |
| immersive-web/webxr | 3,150 | Bikeshed | WebXR Device API spec |
| Hubs-Foundation/hubs | 2,215 | JavaScript | Multi-user virtual spaces (A-Frame) |
| tentone/nunuStudio | 2,230 | JavaScript | WebXR game engine |
| hiukim/mind-ar-js | 2,729 | JavaScript | Web AR with TensorFlow.js |
| google/lullaby | 1,197 | C++ | VR/AR C++ libraries |
| microsoft/MixedReality-WebRTC | 944 | C# | MR audio/video real-time communication |
| microsoft/MixedRealityToolkit | 867 | C++ | MRTK C++ components |

## Hottest Open Issues by Episode Topic

### Episode 1 — Perceptual Latency

| # | Issue | Repo | Comments | Why it's hot |
|---|---|---|---|---|
| 1 | Instant Preview not connected to editor after first run | arcore-unity-sdk #206 | 44 | Dev workflow latency kills creative flow |
| 2 | Camera feed does not show when using OPENGLES2 | arcore-unity-sdk #277 | 25 | GPU path selection breaks perceptual continuity |
| 3 | Instant Preview "Not connected to editor" in Unity 2019 | arcore-unity-sdk #566 | 22 | Repeated workflow disruption |
| 4 | iOS massive slowdown with AsyncOperation | arfoundation-samples #1113 | 16 | Frame drops = vestibular-visual conflict = sickness |
| 5 | False Camera bug under Metal | arcore-unity-extensions #250 | 11 | Platform-level crash breaks presence |
| 6 | TrueDepth front-facing depth map (feature) | arfoundation-samples #615 | 21 | Depth sensor latency limits avatar fidelity |
| 7 | Off centre tracking behaviour | aitrack #270 | 0 (added) | Tracking accuracy = perceptual stability |
| 8 | Face pose accuracy & consistency | arcore-android-sdk #1658 | 2 | Avatar presence depends on tracking |

### Episode 2 — Spatial Audio

| # | Issue | Repo | Comments | Why it's hot |
|---|---|---|---|---|
| 1 | Improve audio spatialization behaviors | hubs #1853 | 30 | Core MR presence — sound must feel 3D |
| 2 | Investigate issues with user audio not working | hubs #2643 | 30 | Broken audio = broken presence |
| 3 | >20 people in room causes audio issues | hubs #5057 | 24 | Spatial audio doesn't scale for social XR |
| 4 | Consider hooking up sound source nodes | webxr #390 | 30 | Open since 2018 — spec still lacks spatial audio API |
| 5 | Sonic Palette (Color-Hearing for the Blind) | XuanJi-ISA #62 | 6 | Cross-modal spatial audio for accessibility |
| 6 | Instagram Turbo (spatial audio PR) | Instagram-Turbo PR #1 | 12 | Real-time spatial audio for social media |

### Episode 3 — Mixed Reality Interfaces

| # | Issue | Repo | Comments | Why it's hot |
|---|---|---|---|---|
| 1 | Spec language precludes non-visual uses | webxr #815 | 41 | Accessibility gap in the spec |
| 2 | Content in immersive session search around | webxr #992 | 36 | Wayfinding — where am I in XR? |
| 3 | Holograms sticking to camera (SpectatorView) | MRC #221 | 18 | Core MR presence problem |
| 4 | SpectatorView calibration fragility | MRC #228 | 19 | Blocks research reproducibility |
| 5 | Give developers control over "overlay" browser | webxr #1365 | 16 | UI/UX design in XR |
| 6 | Location-based AR example doesn't work | AR.js #825 | 4 | Geo-AR precision too low for reliable overlays |
| 7 | AR Foundation — Image Tracking Offset/Drift | arfoundation-samples #1220 | 0 | Large-scale model tracking drift |

## Prominent Developers & Researchers (Potential Guests)

### AR / Web AR
- **jeromeetienne** — Creator of AR.js; Web AR pioneer
- **leinardi** — SteamVR-for-Linux maintainer; motion-to-photon latency expert
- **jd-3d** — ALVR developer; VR streaming latency researcher

### Mixed Reality / HoloLens
- **brycehutchings** — Microsoft OpenXR contributor (MR performance)
- **fredemmott** — Microsoft XR Advocate; HoloLens platform
- **fieldsJacksonG** — Microsoft MRC; hologram registration & calibration
- **mascma** — HoloLens 2 user experience designer
- **ActiveNick** — MR developer (HoloLens)
- **AfterNow** — Spatial computing organization

### WebXR / Immersive Web
- **cwilso** — W3C Immersive Web; dynamic foveation & visibility masking
- **cabanier** — WebXR DOM overlays & visibility
- **AdaRoseCannon** — Dynamic foveation & accessibility
- **himorin** — WebXR security/privacy
- **chrisdavidmills** — WebXR visibility-mask events
- **danrossi** — WebXR layers & projection layers
- **aphillia** — Input profiles & i18n for XR
- **ddorwin** — Accessibility in XR; non-visual spec language
- **idrisshah** — WebXR accessibility; immersive content search
- **toji** — WebXR spec maintainer

### Spatial Audio
- **leomccormack** — Spatial_Audio_Framework creator; HRTF & ambisonics
- **crlandsc**, **ali-vosoughi**, **jacobhollebon** — Spatial_Audio_Framework contributors
- **BinWang28** — HRTF research & spatial speech perception
- **edurnebernal** — Audio-visual spatial perception in VR
- **TheBarmaEffect** — Perception-first spatial audio engine
- **misslivirose** — Hubs-Foundation audio spatialization & accessibility lead
- **robertlong** — Hubs-Foundation audio reliability engineering

### AR Tracking & Calibration
- **dylanmenzies** — AR tracking researcher (aitrack, ARCore face tracking)
- **sam598** — ARKit TrueDepth front-facing depth map researcher

### XR Engine / Framework
- **maluoi** — StereoKit maintainer; XR engine & OpenXR backend

## Cross-Cutting Hot Debates

1. **Perceptual Latency & Motion Sickness** — The <20ms motion-to-photon threshold is well-known but continuously violated by platform bugs, rendering pipeline issues, and frame drops. ARFoundation #1113, ARCore #206/#277, and arcore-unity-extensions #250 all show that even major platforms struggle with latency-related perceptual breaks.

2. **Spatial Audio at Scale** — Hubs-Foundation issues #1853, #2643, and #5057 reveal that spatial audio quality degrades exactly when it matters most — with more users and more CPU load. The WebXR spec still can't natively do spatial audio (#390, open since 2018).

3. **MR Presence & Registration** — Hologram drift ("stick to camera") and calibration fragility (MRC #221, #228) are the core MR presence problems. If holograms don't stay put, the brain rejects the illusion.

4. **WebXR Accessibility Gap** — webxr #815 (41 comments) shows the spec language is heavily visual-centric. webxr #992 (36 comments) reveals a fundamental wayfinding problem: users don't know where they are in immersive sessions.

5. **Cross-Modal Perception** — The Sonic Palette (#62) and HRTF personalization research show that spatial audio isn't just about hearing — it can substitute for other senses and reshape how humans perceive space.
