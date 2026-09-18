# 🎙️ The Future of Human Perception — Episode Outline

> **A podcast series exploring the engineering and human science behind how technology reshapes perception.**
> 
> Research compiled from GitHub's most active AR, spatial computing, and mixed reality repositories on **September 18, 2026**.

---

## 📋 Series Overview

| Episode | Title | Core Debate | Primary Repos | Seeded Guests |
|---------|-------|-------------|----------------|---------------|
| **1** | **Latency and the Perceptual Threshold** | Can foveation trick the brain into forgiving lag? | AR.js, MindAR, Google Lullaby | Jerome Etienne, Hiukim, Nicolò Carpignoli |
| **2** | **Spatial Sound and the Third Dimension** | Why is the WebXR spec still visual-only for spatial audio? | Google Lullaby, JeelizFaceFilter, immersive-web/webxr | Jeeliz Team, marcusx2, Hiukim |
| **3** | **Interfaces Beyond the Flat Screen** | Is the WebXR spec blind to non-visual perception? | AR.js, MindAR, MixedRealityToolkit-Unity | Jerome Etienne, Nicolò Carpignoli, microsoft/MRTK devs |

---

## 🔬 Research Backbone — Most Active GitHub Communities

### Tier 1: Flagship Repositories

| Repo | Stars | Language | Focus | Last Active |
|------|-------|----------|-------|---------------|
| [**AR.js**](https://github.com/AR-js-org/AR.js) (formerly jeromeetienne/AR.js) | 15,791 | HTML/JS | Marker-based & location-based Web AR | Sep 2026 |
| [**MindAR**](https://github.com/hiukim/mind-ar-js) | 2,733 | JavaScript | Image & face tracking via TensorFlow.js/WebGL | Sep 2026 |
| [**JeelizFaceFilter**](https://github.com/jeeliz/jeelizFaceFilter) | 2,938 | JavaScript | Real-time multi-face WebGL tracking for AR filters | Sep 2026 |
| [**Google Lullaby**](https://github.com/google/lullaby) | 1,197 | C++ | VR/AR experiences with spatial audio & ECS | Sep 2026 |

### Tier 2: Ecosystem Repositories

| Repo | Stars | Language | Focus |
|------|-------|----------|-------|
| [**AR-Source**](https://github.com/GeekLiB/AR-Source) | 1,903 | — | Comprehensive AR development resource hub |
| [**Magic-Sand**](https://github.com/thomwolf/Magic-Sand) | 1,020 | C++ | AR sandbox software |
| [**MixedRealityToolkit-Unity**](https://github.com/microsoft/MixedRealityToolkit-Unity) | 6,100+ | C# | Microsoft's MR framework for Unity |
| [**immersive-web/webxr**](https://github.com/immersive-web/webxr) | 3,100+ | JS | WebXR Device API specification |
| [**Hubs-Foundation/hubs**](https://github.com/Hubs-Foundation/hubs) | 2,200+ | JS | Social VR/AR experiences |

---

## 🎙️ Episode 1: "Latency and the Perceptual Threshold"

### The Big Question
*Can foveation rendering trick the brain into forgiving lag — or is the 20ms motion-to-photon deadline a hard physiological limit?*

### Key Topics

#### 1. The Neuroscience of Perceptual Latency
- **Motion-to-photon latency**: The end-to-end delay from head movement to pixel update
- **The 20ms rule**: Research suggests ~20ms is the threshold below which the brain stops perceiving lag as "wrong"
- **Vestibulo-ocular reflex**: How the inner ear detects latency mismatches before the eyes even adjust
- **Foveal vs. peripheral rendering**: Could we render the fovea at full resolution and the periphery at reduced fidelity to buy back latency?

#### 2. What the GitHub Issues Reveal

**From MindAR (#556 — "Unstable AR Content and Ineffective Tracking Configurations")**
🔗 https://github.com/hiukim/mind-ar-js/issues/556
- Users report **tracking jitter and drift** that correlates with frame-rate drops
- 5 comments, actively discussed — this is a live pain point

**From MindAR (#475 — "r.backend(...).compileAndRun is not a function")**
🔗 https://github.com/hiukim/mind-ar-js/issues/475
- WebGL backend compilation failures suggest **GPU pipeline instability** under load — directly impacts latency budgets

**From JeelizFaceFilter — `enableAsyncReadPixels` trade-off**
🔗 See source code: `helpers/JeelizResizer.js` and `set_scanSettings` docs
- "It will free a lot of CPU resource but **it may add latency on some devices**"
- This is a **one-line comment in the source code** that captures the entire latency-perception problem

**From AR.js / AR-js-org (#278 — "Content 'sticking to' camera on certain devices")**
🔗 https://github.com/AR-js-org/AR.js/issues/278
- 40 comments — a **positional latency artifact** where the render pipeline lags behind the sensor feed
- Labeled as `bug, location based` — fundamental to how AR content is anchored

**From AR.js / AR-js-org (#466 — "DeviceOrientationControls iOS initial heading/alpha correction")**
🔗 https://github.com/AR-js-org/AR.js/issues/466
- 26 comments — **sensor-to-render pipeline mismatch** on iOS
- Labeled as `bug, location based, iOS` — platform-specific latency artifacts

**From Google Lullaby**
🔗 https://github.com/google/lullaby
- ECS architecture explicitly designed for "efficient runtime performance" — latency-minimization philosophy
- Spatial audio built into the engine — suggests audio latency is treated as a first-class concern
- Only 2 open issues total — development may have plateaued, but the architecture is sound

### 🎤 Seeded Guests

| Name | GitHub Handle | Role | Outreach Priority |
|------|---------------|------|-------------------|
| **Jerome Etienne** | @jeromeetienne | Creator of AR.js (15.8k ⭐) | ⭐⭐⭐ — The pioneer of web AR; has navigated the latency/performance trade-off from day one |
| **Hiukim** | @hiukim | Creator of MindAR (2.7k ⭐) | ⭐⭐⭐ — Single developer writing custom WebGL tracking ops; lives in the latency budget problem |
| **Nicolò Carpignoli** | @nicolocarpignoli | AR.js maintainer (AR-js-org) | ⭐⭐⭐ — Took over AR.js; manages community latency/compatibility debates |
| **Jeeliz Team** | @jeeliz | FaceFilter developers (2.9k ⭐) | ⭐⭐ — Their codebase explicitly documents latency-compromise mechanisms (`animateDelay`, `enableAsyncReadPixels`) |

### 🗣️ Debate Propositions

| Position | Argument | Likely Proponent |
|----------|----------|-----------------|
| **Foveation is the answer** | Render only what the user is looking at at full fidelity; periphery can tolerate lag | Eye-tracking researchers |
| **Raw throughput wins** | Push more frames; AI upscaling can handle the rest | Mobile AR advocates (MindAR/AR.js communities) |
| **Predictive tracking** | Use ML to predict head position 2 frames ahead and pre-render | Game engine teams (Lullaby ECS) |
| **The 20ms limit is cultural** | The brain adapts; consistency matters more than absolute latency | Perceptual psychologists |

### 📚 Recommended Pre-Reading
1. [WebXR Device API Specification](https://immersive-web.github.io/webxr/) — latency requirements section
2. [AR-js-org Issues — Latency, Jitter, Sticking](https://github.com/AR-js-org/AR.js/issues?q=is:issue+latency+or+jitter+or+sticking)
3. [MindAR #556 — Unstable AR Content](https://github.com/hiukim/mind-ar-js/issues/556)
4. [JeelizFaceFilter `set_scanSettings` API docs](https://github.com/jeeliz/jeelizFaceFilter#using-module)
5. [Google Lullaby — ECS Architecture](https://github.com/google/lullaby/blob/master/lullaby/docs/arch_overview.md)

---

## 🎙️ Episode 2: "Spatial Sound and the Third Dimension"

### The Big Question
*Why does the WebXR spec treat spatial audio as an afterthought — and can HRTF-based rendering ever feel truly "present" on the web?*

### Key Topics

#### 1. The Science of Spatial Audio in AR/VR
- **Head-Related Transfer Functions (HRTFs)**: How your pinnae shape sound before it hits your eardrum — and why generic HRTFs feel "off" for some listeners
- **Ambisonics vs. binaural**: The trade-off between scene-accurate encoding and personalized rendering
- **The "presence paradox"**: You can have perfect visual presence and zero audio presence — or vice versa. The brain prioritizes audio for spatial orientation
- **Dynamic audio rendering**: How head tracking must be coupled to audio in real-time, or the illusion collapses

#### 2. What the GitHub Issues Reveal

**From Google Lullaby — Spatial Audio as Core Feature**
🔗 https://github.com/google/lullaby
- Defines spatial audio as a **core feature**: *"Support for full 3D VR environments, including geometric worlds, panoramic images, and spatial audio"*
- ECS architecture + Java-based API for Android integration
- Used internally by Google: VR Home, Play Store, YouTube, Play Movies, and Earth
- **Yet only 2 open issues exist** — spatial audio development appears to have plateaued. The tech may have gone proprietary internally

**From JeelizFaceFilter — Audio Playback Compatibility**
🔗 [Issue #463: "Play both video and its audio on both Android and IOS"](https://github.com/jeeliz/jeelizFaceFilter/issues/463)
- 4 comments — **basic audio playback itself is still a device-compatibility problem** in web AR
- This isn't spatial audio yet — it's *any* audio. The gap is fundamental

**From JeelizFaceFilter — Audio Continuity When Switching Tabs**
🔗 See `isKeepRunningOnWinFocusLost` option in source docs
- *"This option is useful for a videoconferencing app, where a face mask should still be computed even if the window is not active"*
- The **audio continuity problem** — what happens to spatial audio when the user switches browser tabs? — is treated as an edge case, not a core design requirement

**From MindAR — The Silent Audio Roadmap**
🔗 https://github.com/hiukim/mind-ar-js
- Official roadmap: *"Supports more augmented reality features, like **Hand Tracking, Body Tracking and Plane Tracking**"*
- **Zero audio-related roadmap items** — confirming that the web AR ecosystem is overwhelmingly visual
- MindAR's README emphasizes GPU (WebGL) and Web Worker for **visual** performance — audio is not mentioned

**From AR.js — Visual-Only by Default**
🔗 https://github.com/AR-js-org/AR.js
- A-Frame integration: AR.js markers drive 3D object placement, but **no audio components** in the A-Frame AR ecosystem
- Location-based AR uses GPS for positioning, but **no geospatial audio** discussion

### 🎤 Seeded Guests

| Name | GitHub Handle | Role | Outreach Priority |
|------|---------------|------|-------------------|
| **Jeeliz Team** | @jeeliz | FaceFilter developers (2.9k ⭐) | ⭐⭐⭐ — They've wrestled with audio-on-web-AR device compatibility (#463) firsthand; their library is the most sound-aware web AR project |
| **marcusx2** | @marcusx2 | Unity WebAR Foundation creator, AR.js contributor | ⭐⭐⭐ — Bridges Unity's audio pipeline with web AR; has shipped both visual and audio AR experiences |
| **Hiukim** | @hiukim | MindAR creator (2.7k ⭐) | ⭐⭐⭐ — Can explain why MindAR's roadmap prioritizes visual tracking over audio — is it deliberate or just scope? |
| **Google Lullaby Maintainers** | (org:google) | Lullaby's spatial audio architects | ⭐⭐ — Lullaby is one of the few open-source VR/AR engines treating spatial audio as a core feature |

### 🗣️ Debate Propositions

| Position | Argument | Likely Proponent |
|----------|----------|-----------------|
| **WebXR is visually overweight** | Rich visual rendering APIs but spatial audio is a stub — the ecosystem neglects non-visual perception | Audio researchers, presence scientists |
| **Browser audio APIs are Good Enough** | Web Audio API + PannerNode can do HRTF; the gap is in tooling, not capability | Web audio developers, Jeeliz team |
| **Personalization is the bottleneck** | Generic HRTFs work for ~60% of people; the rest need personalized scans — impractical for mass web AR | HR researchers, Oculus/Valve audio teams |
| **Audio presence is secondary** | Users tolerate mono or poorly spatialized audio if the visual experience is compelling | Mobile AR pragmatists (MindAR, AR.js users) |

### 📚 Recommended Pre-Reading
1. [Google Lullaby — Module Architecture](https://github.com/google/lullaby/tree/master/lullaby/modules)
2. [JeelizFaceFilter Issue #463 — Audio on Android/iOS](https://github.com/jeeliz/jeelizFaceFilter/issues/463)
3. [Web Audio API Specification](https://www.w3.org/TR/webaudio/)
4. [HRTF Personalization Research (Google Research)](https://research.google/pubs/hrtf-personalization/)
5. [W3C WebXR Inputs & Audio Working Draft](https://immersive-web.github.io/webxr/)

---

## 🎙️ Episode 3: "Interfaces Beyond the Flat Screen"

### The Big Question
*Are current MR interface paradigms — reticles, gazes, hand gestures — designed for 2D thinking? What would a truly spatial UI look like?*

### Key Topics

#### 1. The Crisis of Mixed Reality Interfaces
- **The reticle problem**: Every MR headset uses a 2D gaze-pointing reticle — are we just doing mouse cursors in 3D space?
- **Gaze + pinch** (Magic Leap, HoloLens): Is the combination of gaze and finger pinch the natural interaction model, or are we forcing 2D paradigms into 3D?
- **Hologram drift**: When virtual objects slowly shift position relative to the real world — a perceptual betrayal that breaks presence
- **Wayfinding in MR**: How do you navigate a spatial interface without a 2D menu bar? The "air tapping" fatigue problem

#### 2. What the GitHub Issues Reveal

**From AR.js / AR-js-org (#278 — "Content 'sticking to' camera on certain devices")**
🔗 https://github.com/AR-js-org/AR.js/issues/278
- 40 comments, labeled `bug, location based`
- **Fundamental MR interface question**: Should AR content be tied to the camera view (like a heads-up display) or to the physical world (like a hologram)?
- This issue is the **interface design debate** playing out in real code

**From AR.js / AR-js-org (#217 — "Markerless tracking without tango (/ios equivalent)")**
🔗 https://github.com/AR-js-org/AR.js/issues/217
- 22 comments, labeled `enhancement, question`
- Developers are **begging for persistent spatial understanding** without proprietary hardware
- The interface question is really a **sensor question**: what hardware do you need for true spatial interfaces?

**From AR.js / AR-js-org (#26 — "Add possibility to choose which Camera use for AR for multi-camera devices")**
🔗 https://github.com/AR-js-org/AR.js/issues/26
- 22 comments, labeled `bug` — opened by maintainer Nicolò Carpignoli himself
- **The interface question is a hardware question**: which sensor feeds the perception pipeline? Front camera? Back camera? LiDAR? Multiple?

**From MindAR (#461 — "Get distance from camera to tracked image?")**
🔗 https://github.com/hiukim/mind-ar-js/issues/461
- 5 comments — developers need **depth relationships** for interface design, and current APIs don't expose them cleanly
- Without depth, you can't build interfaces that respect physical spacing

**From MindAR (#410 — "Object remains when switch camera")**
🔗 https://github.com/hiukim/mind-ar-js/issues/410
- Switching between front/back cameras **breaks spatial tracking state**
- MR frameworks treat camera as binary (on/off) rather than as a **spatial continuum** — this is an interface architectural problem

**From JeelizFaceFilter — Head-Controlled Interface Demos**
🔗 See demos: `pacman/`, `headCursor/`, `headControls/`
- These are **early interface prototypes** for MR interaction paradigms
- Head-controlled PAC-MAN and head-controlled mouse cursor are **proof-of-concept spatial interfaces** that predate current MR hype
- The `headControls` demo uses face rotation (rx, ry, rz) for navigation — essentially a **gaze-plus-orientation interface**

**From Microsoft MixedRealityToolkit-Unity**
🔗 https://github.com/microsoft/MixedRealityToolkit-Unity
- MRTK defines **six core hand interactions**: Poke, Grab, Menu, Palm Dismiss, Navigation, Pointing
- All are **two-handed or hand + gaze** combinations
- **No MRTK interaction profile accounts for head-only or eye-only input** — despite both being universally available on MR headsets
- The interface paradigm is **hand-centric**, even though eyes and head are more always-available inputs

### 🎤 Seeded Guests

| Name | GitHub Handle | Role | Outreach Priority |
|------|---------------|------|-------------------|
| **Jerome Etienne** | @jeromeetienne | AR.js creator (15.8k ⭐) | ⭐⭐⭐ — Has thought deeply about what makes AR "feel real" vs. "feels like a HUD"; the markerless vs. marker debate is fundamentally an interface philosophy |
| **Nicolò Carpignoli** | @nicolocarpignoli | AR.js maintainer (AR-js-org) | ⭐⭐⭐ — Manages the community's interface debates daily; the AR-js-org GitHub discussions are a running interface design workshop |
| **marcusx2** | @marcusx2 | Unity WebAR Foundation, AR.js contributor | ⭐⭐⭐ — Bridges Unity's MRTK interaction system with web-based AR; uniquely positioned to compare native vs. web MR interface paradigms |
| **Microsoft MRTK Team** | (org:microsoft) | MixedRealityToolkit-Unity maintainers | ⭐⭐ — Define the de facto standard for MR hand/gaze interactions; can speak to the design decisions behind reticle-based interfaces |

### 🗣️ Debate Propositions

| Position | Argument | Likely Proponent |
|----------|----------|-----------------|
| **We need a new interaction grammar** | Reticles and pinches are 2D thinking; spatial UIs should exploit depth, proximity, and gesture naturally | MR researchers, HoloLens enthusiasts |
| **2.5D is good enough** | Users don't want full immersion; they want productivity tools that float information in peripheral vision | Productivity-focused MR devs, Glass Enterprise advocates |
| **Voice is the missing interface** | Hands-free, eyes-free voice commands are the only modality that scales beyond "tech demos" to daily use | Voice-first advocates, NLP researchers |
| **Persistent spatial anchors are the real UI** | The interface isn't the interaction — it's the persistent layer of anchored information that follows you through physical space | AR.js location-based advocates, Niantic's Lightship team |

### 📚 Recommended Pre-Reading
1. [MixedRealityToolkit-Unity Documentation](https://aka.ms/mrtkdocs)
2. [AR-js-org Issue #278 — Content Sticking to Camera](https://github.com/AR-js-org/AR.js/issues/278)
3. [AR-js-org Issue #217 — Markerless Tracking Without Tango](https://github.com/AR-js-org/AR.js/issues/217)
4. [MindAR Issue #461 — Distance from Camera to Tracked Image](https://github.com/hiukim/mind-ar-js/issues/461)
5. [W3C WebXR Hand Input Module](https://immersive-web.github.io/hand-input/)
6. [JeelizFaceFilter — Head Controls Demos](https://github.com/jeeliz/jeelizFaceFilter/tree/master/demos/headControls)

---

## 📡 Production Workflow

### Episode Lifecycle
1. **Research** → Open an issue for the episode (see `#122`, `#124`, `#126` for episode seeds)
2. **Pre-production** → Add show notes, outreach status, and fact-checking items as issue comments
3. **Recording** → Create a draft file in `episodes/` with timestamps and talking points
4. **Post-production** → Update the issue with episode link, transcript, and listener feedback prompts
5. **Community feedback** → Encourage listeners to open issues with questions for future episodes

### Episode Issue Template
```
## 🎙️ Episode N: [Title]

### Status
- [ ] Research complete
- [ ] Guest confirmed
- [ ] Script drafted
- [ ] Recording scheduled
- [ ] Episode published

### Key Topics
- Topic 1
- Topic 2
- Topic 3

### Guest Contacts
- Name (GitHub handle) — Role — Outreach status

### GitHub Source Material
- [Repo Issue #X](url) — Brief description
- [Repo Issue #Y](url) — Brief description

### Talking Points
1. Opening question
2. Deep-dive segment
3. Debate prompt
4. Closing thought

### Listener Engagement
- Question for the community:
- Follow-up episode idea:
```

---

## 🤝 Community Guidelines

- **Be curious, not cynical** — This is about understanding, not dismissing
- **Cite your sources** — Link to GitHub issues, research papers, and docs
- **Respect the maintainers** — The people building these tools deserve thoughtful questions
- **Embrace disagreement** — The best episodes happen when guests and hosts see the problem differently
- **Open everything** — Episode scripts, research notes, and show logs should be public

---

*Last researched: September 18, 2026*
*Next review: October 2026*
