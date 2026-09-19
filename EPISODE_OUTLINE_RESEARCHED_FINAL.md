# 🎙️ The Future of Human Perception — Episode Outline (Researched)

> Generated from GitHub research across the most active AR/MR/Spatial Computing repositories.
> Research date: September 2026

---

## Episode 1: "Latency and the Perceptual Threshold"

**Core Question:** Can foveation trick the brain into forgiving lag?

### Key Debate Topics

| Topic | Description | Source |
|---|---|---|
| CPU/GPU Sync Modes | The trade-off between pipelining (high FPS) and sequential rendering (low latency). Godot PR #100031 proposes `CPU_GPU_SYNC_PARALLEL` vs `CPU_GPU_SYNC_SEQUENTIAL` modes. | [godotengine/godot PR #100031](https://github.com/godotengine/godot/pull/100031) — 46 comments, 7 👍, 12 👀 |
| Latency Pacing Modes | Unified `latency_mode` setting with 4 levels: `low_extreme`, `low`, `medium`, `high_throughput`. Can reduce display latency from 5 frames to 0-1. | [godotengine/godot PR #106221](https://github.com/godotengine/godot/pull/106221) — 9 comments, 10 👍, 13 🎉 |
| Motion-to-Photon Pipeline | The full chain from head movement → render → display. Each frame of pipelining adds ~11ms of latency. The 20ms perceptual threshold is the holy grail. | General XR research |
| Waitable Swapchains | Vulkan extension that lets the CPU wait on the GPU, eliminating swapchain recreation overhead. AMD doesn't support on Windows yet. | [godotengine/godot PR #105496](https://github.com/godotengine/godot/pull/105496) |
| Android Swappy | Google's frame-pacing library for Android, now integrated as an alternative pacing method in Godot. | Godot PR #106221 |
| Audio Output Latency | `AudioServer::get_output_latency()` is inaccurate in Godot. Buffer size mismatches cause perceptual drift in spatial audio. | [godotengine/godot Issue #38215](https://github.com/iina/iina/issues/3444) — 7 comments |

### Potential Guests

| Name | Role | Expertise |
|---|---|---|
| **BastiaanOlij** | Godot XR Maintainer | OpenXR integration, hand tracking, spatial entities. Author of PRs #60313, #78032, #81533, #107391 |
| **darksylinc** | Godot Contributor | CPU/GPU sync mode, latency pacing. Author of PRs #106221, #105435 |
| **KeyboardDanni** | Godot Contributor | CPU/GPU sync mode, latency tester tool. Author of PR #100031 |
| **benjarmstrong** | Godot Audio Contributor | Audio latency fixes. Author of PR #38280, Issue #38215 |
| **ellenhp** | Godot Audio Contributor | AudioServer buffer sync. Author of PR #52626 |
| **StephenHodgson** | XR Researcher | WebXR & VR perception research |

### Discussion Questions
1. Is the 20ms motion-to-photon threshold a hard physiological limit or a comfortable guideline?
2. Can foveated rendering justify the latency cost of pipelining?
3. Should game engines expose latency modes as user-facing settings, or hide them in developer options?
4. How does audio latency differ from visual latency in its perceptual impact?

---

## Episode 2: "Hands in the Air — Hand Tracking & Mixed Reality Interfaces"

**Core Question:** Are we building intuitive MR interfaces or just fancy gimmicks?

### Key Debate Topics

| Topic | Description | Source |
|---|---|---|
| OpenXR Hand Tracking | Godot's progression from raw hand data (#60313, #78032) to generic interface (#88639) to gesture detection (#113183). The API evolution mirrors the industry's maturity curve. | Multiple Godot PRs by BastiaanOlij, dsnopek |
| Hand Tracking Mesh Rendering | On Android/Oxygen (Lynx-R1), hand armature rendering crashes with OpenGL Due to FBO view mismatch. Vulkan required for proper rendering. | [godotengine/godot Issue #74074](https://github.com/godotengine/godot/issues/74074) — 14 comments |
| Hand Tracking Position Offset | In A-Frame, the hand tracking dots model is offset from the actual hand root. Impacts presence and interaction accuracy. | [aframevr/aframe Issue #5793](https://github.com/aframevr/aframe/issues/5793) |
| Hand Tracking + Controller Detach | In A-Frame, adding `hand-tracking-controls` causes child entities to detach from laser controllers. Children no longer show up with either input mode. | [aframevr/aframe Issue #5517](https://github.com/aframevr/aframe/issues/5517) — by coderofsalvation |
| Pen/Stylus Responsiveness | Input sampling rate insufficient for fast handwriting. Only `InputEventMouseMotion` events, no button events. Duplicate positions with varying pressure. | [godotengine/godot Issue #75903](https://github.com/godotengine/godot/issues/75903) — 13 comments |
| Mixed Reality Passthrough | Godot's passthrough extension wrapper (#65898), environment blend mode fixes (#94550), and Windows Mixed Reality compatibility issues (#72211, #59506). | Multiple Godot PRs/Issues |
| Vision Pro Hand Tracking | New support for Apple Vision Pro hand tracking and PSVR2 controllers. The gold standard for consumer hand tracking fidelity. | [godotengine/godot PR #122567](https://github.com/godotengine/godot/pull/122567) |

### Potential Guests

| Name | Role | Expertise |
|---|---|---|
| **dsnopek** | Godot XR Editor & WebXR Contributor | Hand tracking, WebXR support, XR Editor. Author of PRs #88411, #88639, #112009 |
| **Rodolphe** | Godot Android XR Developer | OpenGL rendering issues, mobile XR. Author of Issue #74074 |
| **Diego Marcos** | A-Frame Maintainer | WebXR interfaces, hand tracking controls. @dmarcos on X |
| **Don McCurdy** | A-Frame Maintainer | 3D web frameworks, educational VR. @donrmccurdy on X |
| **Kevin Ngo** | A-Frame Maintainer | WebXR performance, cross-platform. @andgokevin on X |
| **coderofsalvation** | A-Frame Community Contributor | Hand tracking controls, component architecture |

### Discussion Questions
1. Is hand tracking a replacement for controllers or a complementary modality?
2. How do we handle the "uncanny valley" of hand avatars that are almost but not quite correct?
3. What's the minimum tracking fidelity required for a mixed reality interface to feel "real"?
4. Should MR interfaces default to visual-only, or should they incorporate haptic and spatial audio channels from day one?

---

## Episode 3: "Sound in Space — Spatial Audio & 3D Soundscapes"

**Core Question:** Why is the WebXR spec still visual-only for spatial audio?

### Key Debate Topics

| Topic | Description | Source |
|---|---|---|
| Spatial Audio in Godot | Godot supports 3D positional audio, but buffer size management and latency inaccuracies undermine presence. The audio server and driver buffer sizes must be synchronized. | [godotengine/godot PR #38280](https://github.com/godotengine/godot/pull/38280), [PR #52626](https://github.com/godotengine/godot/pull/52626) |
| macOS Spatial Audio Support | Apple platforms have native spatial audio, but implementation in media players is inconsistent. Feature requests date back to 2021. | [iina/iina Issue #3444](https://github.com/iina/iina/issues/3444) — 54 comments |
| MPV Spatial Audio | rcombs investigated spatial audio support for mpv-player on macOS. The feature was eventually fixed. | [mpv-player/mpv Issue #9252](https://github.com/mpv-player/mpv/issues/9252) — 21 comments |
| Google Lullaby Spatial Audio | Google's Lullaby library explicitly supports "spatial audio" as a core feature for VR environments, used across Google VR Home, YouTube, and Play Movies. | [google/lullaby](https://github.com/google/lullaby) — 1,197 ⭐ |
| Spatial Entities Extension | OpenXR spatial entities let apps place persistent 3D content in the real world. Godot added support via PR #107391. | [godotengine/godot PR #107391](https://github.com/godotengine/godot/pull/107391) — 16 comments |
| HRTF & Ambisonics | Head-Related Transfer Functions and ambisonics are the two dominant approaches to 3D audio rendering. Web spec has no standardized spatial audio API. | General XR research |
| Audio Presence Paradox | In VR, you can "hear" a sound behind you even when you're facing forward. This suggests spatial audio may be more threatening to the ego boundary than visuals. | Philosophical / perceptual science |

### Potential Guests

| Name | Role | Expertise |
|---|---|---|
| **benjarmstrong** | Godot Audio Engineer | Audio latency, buffer management. Author of PR #38280, Issue #38215 |
| **ellenhp** | Godot Audio Engineer | AudioServer synchronization. Author of PR #52626 |
| **Calinou** | Godot Maintainer | Audio documentation, project settings. Author of PR #118983 |
| **Google Lullaby Team** | Google VR Engineers | Spatial audio in C++ VR frameworks. Used in Google VR Home, YouTube, Play Movies |
| **StephenHodgson** | XR Perception Researcher | Multisensory integration in VR |

### Discussion Questions
1. Why does the WebXR Device API specification focus almost entirely on visuals and input, leaving spatial audio as an afterthought?
2. Can spatial audio exist independently of visual context, or does it require a virtual environment to be meaningful?
3. How does the "presence paradox" — hearing a sound from an impossible direction — challenge our models of spatial perception?
4. Should spatial audio be treated as a rendering concern (like graphics) or a perceptual concern (like UX)?

---

## appendix: Research Sources

### Most Active AR/MR/Spatial Computing Repos Surveyed

| Repo | Stars | Focus | XR Relevance |
|---|---|---|---|
| [godotengine/godot](https://github.com/godotengine/godot) | 117.4k | 2D/3D Game Engine | XR module, OpenXR, hand tracking, spatial audio, passthrough |
| [aframevr/aframe](https://github.com/aframevr/aframe) | 17.6k | WebXR Framework | AR/VR experiences, hand tracking, spatial audio |
| [jeromeetienne/AR.js](https://github.com/AR-js-org/AR.js) | 15.8k | Web AR | Marker-based AR, image tracking, location-based AR |
| [google/lullaby](https://github.com/google/lullaby) | 1.2k | VR/AR C++ Libraries | Spatial audio, geometric worlds, Material VR |
| [microsoft/xr-development-for-beginners](https://github.com/microsoft/xr-development-for-beginners) | 564 | Spatial Computing Curriculum | Mixed reality development education |

### Key Community Members Identified

| GitHub Handle | Project | Role |
|---|---|---|
| BastiaanOlij | Godot | XR maintainer, OpenXR PRs |
| dsnopek | Godot | XR editor, WebXR hand tracking |
| darksylinc | Godot | Latency/pacing improvements |
| KeyboardDanni | Godot | CPU/GPU sync mode |
| benjarmstrong | Godot | Audio latency |
| elleenhp | Godot | AudioServer sync |
| rodolpheh | Godot | Android XR rendering |
| Diego Marcos | A-Frame | Maintainer |
| Don McCurdy | A-Frame | Maintainer |
| Kevin Ngo | A-Frame | Maintainer |
| Jerome Etienne | AR.js | Creator |
| Nicolò Carpignoli | AR.js | Maintainer |
| StephenHodgson | WebXR | Perception research |
| peterclemenko | WebXR | VR/AR development |
