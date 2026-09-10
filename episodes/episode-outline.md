# Episode Outline — The Future of Human Perception

> A collaborative podcast exploring augmented reality, spatial computing, and the science of how we perceive virtual and mixed-reality worlds.

This living document maps each planned episode to the hottest open debates and contributor voices surfacing from the GitHub XR / WebXR / spatial-media communities.

## How to use this repo collaboratively
- Add research notes to `RESEARCH-Database.md`.
- Propose guest outreach in the linked episode issues.
- Open PRs with show notes, transcripts, or listener questions.

---

## Episode 1 — "Is the lag in your headset lying to your brain?" (Perceptual Latency)

**Core question:** When visual/audio feed delivery lags behind head and hand motion, the brain rejects the scene as "fake." How close are we to closing the loop — and what does that mean for presence, motion sickness, and the design of virtual worlds?

**Key open debates (GitHub):**
- **WebXR spec readiness** — [immersive-web/webxr#815](https://github.com/immersive-web/webxr/issues/815) ("Spec language precludes non-visual uses"): whether the core WebXR spec's vision-centric definitions block audio-first and non-visual AR use cases.
- **Spatial audio & HRTF timing** — [immersive-web/webxr#390](https://github.com/immersive-web/webxr/issues/390) ("Consider hooking up sound source nodes in the API somehow"): the challenge of feeding head-pose data to the audio thread fast enough for convincing HRTF positioning.
- **Foundations of perceptual latency** — Open questions clouding current search results signal how *under-discussed* genuine sensorimotor-delay research still is in open-source spaces — a gap the episode aims to name.

**Prominent voices to invite:**
- **Jérôme Étienne** (@jeromeetienne) — creator of AR.js; front-line build experience shipping 60fps WebAR on mobile.
- **Chris Wilson** (@cwilso) — Web Audio / WebXR spec editor; authored the spatial-audio-HRTF positioning discussion.
- **Brandon ("Toji") Jones** (@toji) — WebXR / WebGL spec editor; one of the accessibility & spec leads tracking non-visual use cases.

**Suggested segments:** sensorimotor delay 101 · the "video eats audio first" race (KHR_video timeline sync) · latency budgets that neuroscientists care about · worst-case VR design.

---

## Episode 2 — "Whose reality, and whose hand?" (Mixed Reality Interfaces & Presence)

**Core question:** As MR headsets blend digital content into shared physical space, interface metaphors (hand tracking, gaze + pinch, proxies, spatial anchors) shape who feels at home in the scene — and who feels manipulated.

**Key open debates (GitHub):**
- **Tracking stability vs. jitter** — [hiukim/mind-ar-js#556](https://github.com/hiukim/mind-ar-js/issues/556) ("Unstable AR Content and Ineffective Tracking Configurations"): the community's real frustration when jittered tracked content breaks presence and comfort.
- **Platform viability & abandonware fears** — [hiukim/mind-ar-js#526](https://github.com/hiukim/mind-ar-js/issues/526) ("Is this repo abandonware? Should I switch to ar.js?"): a soul-searching debate about open-maintenance, sustainability, and lock-in as MR tooling matures.
- **City-scale markerless AR** — [jeromeetienne/AR.js#833](https://github.com/jeromeetienne/AR.js/issues/833) (world-scale geographic AR): the dreaming-big end of spatial interfaces — what it means to anchor experience to an entire city.

**Prominent voices to invite:**
- **Jérôme Étienne** (@jeromeetienne) — AR.js, spanning lightweight WebAR to large-scale location-based experiences.
- **MindAR core contributors** (@hiukim + community) — on the ground truth of building vs. maintaining open MR stacks.
- A spatial-design researcher (to be confirmed) on MR interface metaphors and presence.

**Suggested segments:** hand-tracking ergonomics · jitter as a presence killer · open-source MR stack sustainability · from pocket to city scale.

---

## Episode 3 — "Hearing the room that isn't there" (Spatial Audio)

**Core question:** Sound is the fastest route into a virtual scene — yet mostXR audio is still stereo panning. What would it take for open tooling to deliver room-scale, HRTF-accurate, synchronized spatial audio tied to moving light and content?

**Key open debates (GitHub):**
- **Immersive synchronized AV standards** — [KhronosGroup/glTF#2506](https://github.com/KhronosGroup/glTF/issues/2506) ("Extending glTF for Synchronized Immersive Video and Audio in glTF"): the community's strategic push for timeline markers, stereo/volumetric layout, and shared clock sync across spatial media.
- **WebXR audio API hooks** — [immersive-web/webxr#390](https://github.com/immersive-web/webxr/issues/390): why almost a decade later hooking the audio thread to live head pose is still a "future enhancement."
- **Audio AR beyond vision** — [immersive-web/webxr#815](https://github.com/immersive-web/webxr/issues/815): the foundational argument that an audio-first spatially-aware web is technically conceivable today.

**Prominent voices to invite:**
- **Chris Wilson** (@cwilso) — spatial-audio advocate and WebXR/Web Audio spec editor.
- **Ben Erwin** (@powersimple) — glTF contributor authoring the synchronized immersive-AV roadmap (SIGGRAPH-facing).
- A spatial-audio composer / researcher (to be confirmed) on HRTF personalization and real-world room acoustics.

**Suggested segments:** why sound leads presence · HRTF personalization is the unsolved problem · AV sync at the standards layer (KHR_video + timeline) · mixing real room tone into virtual space.

---

*Last updated: project kickoff. PRs and issue conversations welcome — each episode issue below tracks its own guest list and research threads.*
