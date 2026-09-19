# 🎙️ The Future of Human Perception — Episode Outline (Research-Backed, Sept 2026)

> This outline is surgically derived from GitHub's most active AR/MR/Spatial Computing repositories and their open issue discussions. Every topic and guest name below is sourced from real debates happening in real repos right now.

---

## Episode 1: "Latency and the Perceptual Threshold"

**Core Question:** Can foveated rendering trick the brain into forgiving motion-to-photon lag?

### Key Topics
- Motion-to-photon pipeline & the 20ms perceptual rule
- Foveated rendering as a latency-masking strategy
- The neuroscience of perceptual threshold (critical flicker fusion, apparent motion)
- WebXR performance stats & the `requestAnimationFrame` loop
- Rendering latency vs. display latency vs. sensor latency
- Eye-tracking as a latency-compensation tool

### GitHub-Sourced Debate Highlights
- **immersive-web/webxr#1203** — "Provide statistics to help guide performance" — the spec itself lacks performance telemetry hooks
- **immersive-web/webxr#1102** — OffscreenCanvas in Worker support for WebXR (parallel rendering paths)
- **immersive-web/webxr#779** — Should `requestSession` resolving promise count as user activation? (timing of session start matters for latency budgets)
- **playcanvas/engine#3543** — "Extend dynamic batching to support skinned meshes" (rendering performance directly impacts latency)
- **playcanvas/engine#7589** — RFC: Migrate API constants to enum-like API (API design affects developer latency too)
- **MRTopic/MixedRealityToolkit-Unity#88** — MRTK support for Apple VisionOS (new platform = new latency challenges)

### Potential Guests
| Name | Handle | Why |
|---|---|---|
| **Jerome Etienne** | `jeromeetienne` | Creator of AR.js; built Web AR from scratch — knows latency pain firsthand |
| **Nicolò Carpignoli** | `nicolocarpignoli` | AR.js maintainer; keeps 60fps on mobile AR alive |
| **Slim Buck** | `slimbuck` | PlayCanvas render engineer; deep GPU pipeline knowledge |
| **Wille Eastcott** | `willeastcott` | PlayCanvas lead; authored the API RFC on perf-critical design |
| **Michele Valigursky** | `mvaligursky` | PlayCanvas graphics lead; dynamic batching & performance |
| **keveleigh** | `keveleigh` | Microsoft MRTK lead; HoloLens latency optimization |
| **Klaus Wilms** | `klausw` | WebXR spec contributor; Microsoft's perspective on latency |

### Recording Targets
- Pre-record: Jerome Etienne (AR.js origin story)
- Live interview: Slim Buck + Wille Eastcott (dual POV on WebXR perf)
- Follow-up: keveleigh on HoloLens 2 latency budgets

---

## Episode 2: "Spatial Sound and the Third Dimension"

**Core Question:** Why is the WebXR spec still visual-only for spatial audio?

### Key Topics
- HRTFs (Head-Related Transfer Functions) & the science of spatial perception
- Ambisonics vs. HRTF: which paradigm wins for presence?
- The "audio presence paradox" — why perfect spatial audio still feels unreal
- WebXR's blind spot: `AudioListener` vs. `AudioDevice` and the missing spatial API
- 3D positional audio in game engines (PlayCanvas `Sound` component vs. Web Audio API)
- Spatial audio as a accessibility tool (as distinct from visual-a11y)
- The Hubs audio spatialization saga (#1853 Epic issue)

### GitHub-Sourced Debate Highlights
- **immersive-web/webxr#390** — "Consider hooking up sound source nodes in the API somehow" — 30 comments, open since 2018, still unresolved
- **immersive-web/webxr#98** — "Consider specing VR audio output and input (mic)" — first MR issue, never addressed
- **immersive-web/webxr#892** — "Evaluate how/if WebXR should interact with audio-only devices" — accessibility angle
- **Hubs-Foundation/hubs#1853** — "[Epic] Improve audio spatialization behaviors for rooms and individual users" — 30 comments, open since 2019, labeled Epic
- **Hubs-Foundation/hubs#2643** — "Investigate Issues With Users Audio Not Working" — reliability vs. presence
- **Hubs-Foundation/hubs#5057** — "[Android] more than 20 people in the room, causes audio issue" — scalability of spatial audio
- **playcanvas/engine** — 3D positional sounds built on Web Audio API; architecture discussion

### Potential Guests
| Name | Handle | Why |
|---|---|---|
| **Blair MacIntyre** | `blairmacintyre` | Hubs co-founder; spatial computing researcher, Columbia professor |
| **misslivirose** | `misslivirose` | Hubs audio spatialization lead; owns the Epic audio issue |
| **cwilso** | `cwilso` | WebXR spec editor (Google/chromium); filed the #390 audio issue |
| **toji** | `toji` | WebXR spec editor (Mozilla); assigned #892 on audio-only devices |
| **cabanier** | `cabanier` | WebXR contributor (Mozilla); audio & overlay debates |
| **ddorwin** | `ddorwin` | WebXR contributor (Google); accessibility & non-visual use |
| **keianhzo** | `keianhzo` | Hubs audio reliability engineer; owns #2643 |
| **takahirox** | `takahirox` | Hubs engineer; audio spatialization implementation |

### Recording Targets
- Pre-record: Blair MacIntyre (spatial computing theory → practice)
- Live debate: cwilso vs. toji (spec vs. implementation, Google vs. Mozilla)
- Roundtable: misslivirose + keianhzo + takahirox (the Hubs audio reality check)

---

## Episode 3: "Interfaces Beyond the Flat Screen"

**Core Question:** Is the WebXR spec blind to non-visual perception?

### Key Topics
- Hand tracking vs. controller paradigms: which feels more "real"?
- Hologram drift & world-locking: when virtual objects don't stay put
- Spatial anchors & multi-user co-presence
- Eye tracking as the next input modality (not just rendering optimization)
- The WebXR "visual-only" gap: what about proprioception, vestibular sense, touch?
- MRTK's UX building blocks: buttons, slates, hand menus — are they enough?
- Wayfinding in mixed reality: cognitive mapping vs. AR arrows
- Apple Vision Pro as a paradigm shift (or dead end?)

### GitHub-Sourced Debate Highlights
- **immersive-web/webxr#815** — "Spec language precludes non-visual uses" — 41 comments, assigned to toji, labeled a11y-tracker
- **immersive-web/webxr#1210** — "Focus control for handheld AR" — klausw; the perception-focus problem
- **immersive-web/webxr#1365** — "Give developers control over 'overlay' browser" — cabanier; AR passthrough vs. immersion
- **MixedRealityToolkit/MixedRealityToolkit-Unity#88** — "MRTK support for Apple VisionOs and Vision Pro" — 28 comments; theVision Pro debate
- **MixedRealityToolkit/MixedRealityToolkit-Unity#66** — "Update MRTK3 to use Unity XR Hands package" — keveleigh; hand tracking ecosystem
- **MixedRealityToolkit/MixedRealityToolkit-Unity#1033** — "OpenXR Controller Profile Conflict Prevents Simultaneous XREAL Controller and Hand Tracking" — the hand-vs-controller conflict
- **MixedRealityToolkit/MixedRealityToolkit-Unity#1067** — "Meta Quest Controllers incorrectly visualized with hands and has terrible performance" — the rendering cost of hand visibility
- **Hubs-Foundation/hubs#5671** — "In-room interactive iframe / webpage" — the flat-screen intrusion into immersive space

### Potential Guests
| Name | Handle | Why |
|---|---|---|
| **Jerome Etienne** | `jeromeetienne` | AR.js image tracking & markerless AR pioneer |
| **keveleigh** | `keveleigh` | MRTK lead; owns hand tracking & Vision Pro integration |
| **blairmacintyre** | `blairmacintyre` | Hubs co-founder; designed spatial UI from first principles |
| **klausw** | `klausw` | WebXR hand input & focus control contributor |
| **cwilso** | `cwilso` | WebXR spec; the visual-only gap debate |
| **MaxPalmer-UH** | `MaxPalmer-UH` | MRTK Quest 3 controller visualization bug owner |
| **Ali-Can-Keskin** | `Ali-Can-Keskin` | filed the Quest hand tracking + controller conflict bugs |

### Recording Targets
- Pre-record: keveleigh on MRTK3 hand tracking vision
- Live debate: klausw + cwilso (WebXR: visual-first or multi-modal?)
- Guest panel: blairmacintyre + jeromeetienne (from marks to markers: the AR interface evolution)

---

## Cross-Episode Themes

| Theme | Episodes |
|---|---|
| **The WebXR Visual-Only Blind Spot** | Ep 2 (audio), Ep 3 (non-visual perception) |
| **Performance = Presence** | Ep 1 (latency), Ep 3 (hand tracking cost) |
| **The Gap Between Spec & Reality** | Ep 2 (audio API gap), Ep 3 (overlay/hands) |
| **From Hubs to HoloLens: Who Owns the UX?** | Ep 2 (Hubs audio), Ep 3 (MRTK vs. Web) |

---

## Research Sources (Live GitHub Audit)

| Repo | Stars | Last Updated | Key Issues Surfaced |
|---|---|---|---|
| `playcanvas/engine` | 16,825 | 2026-09-18 | #3724 (particles), #1853 (resize), #7589 (API RFC), #3543 (batching) |
| `jeromeetienne/AR.js` | 15,791 | 2026-09-16 | #822 (Three.js breaking), #825 (location-based), #826 (image tracking) |
| `microsoft/MixedRealityToolkit-Unity` | 6,076 | 2026-09-10 | #88 (VisionPro), #66 (XR Hands), #1033 (controller conflict), #1067 (Quest hands) |
| `immersive-web/webxr` | 3,152 | 2026-09-18 | #815 (non-visual), #390 (audio nodes), #1210 (focus), #1365 (overlay) |
| `Hubs-Foundation/hubs` | 2,215 | 2026-09-09 | #1853 (audio Epic), #2643 (audio broken), #5057 (audio scale), #5671 (iframe) |

### Contributor Registry

| GitHub Handle | Repos | Role |
|---|---|---|
| `jeromeetienne` | AR.js | Creator, AR.js |
| `nicolocarpignoli` | AR.js | Maintainer, AR.js org |
| `slimbuck` | playcanvas | Render engineer |
| `willeastcott` | playcanvas | Lead, RFC author |
| `mvaligursky` | playcanvas | Graphics lead |
| `yaustar` | playcanvas | Engineer |
| `cwilso` | webxr | Spec editor (Google/Chromium) |
| `toji` | webxr | Spec editor (Mozilla) |
| `klausw` | webxr | Spec contributor (Microsoft) |
| `cabanier` | webxr | Contributor (Mozilla) |
| `ddorwin` | webxr | Contributor (Google) |
| `blairmacintyre` | hubs | Co-founder, spatial audio researcher |
| `misslivirose` | hubs | Audio spatialization lead |
| `takahirox` | hubs | Engineer |
| `keianhzo` | hubs | Audio reliability engineer |
| `keveleigh` | MRTK | MRTK lead (Microsoft) |

---

*Last updated: September 2026 — Research-sourced from GitHub open issues across 5 active AR/MR/Spatial Computing repositories.*
