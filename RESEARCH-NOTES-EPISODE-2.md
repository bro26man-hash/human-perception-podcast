# Research Notes — Episode 2: "Spatial Sound and the Third Dimension"

## Key GitHub Sources

### immersive-web/webxr #390 — Sound Source Nodes
- **URL:** https://github.com/immersive-web/webxr/issues/390
- **Opened by:** @cwilso (2018-09-06, WebXR contributor)
- **Status:** Open, 30 comments, milestone: "Future"
- **Key insight:** WebXR has no spatial audio API. Developers must bridge Web Audio PannerNodes with head poses manually, introducing latency and desync.
- **Quote from @cwilso:** "The problem lies in keeping the headpose (and the sound source pose) updated on a high enough frequency - ideally, letting the audio thread directly get headpose info somehow or the like."

### immersive-web/webxr #815 — Spec Visual-Only Bias
- **URL:** https://github.com/immersive-web/webxr/issues/815
- **Opened by:** @ddorwin (2019-08-22)
- **Status:** Open, 41 comments, assigned to @toji (WebXR spec editor), labeled "a11y-tracker"
- **Key insight:** Spec language requires "imagery" to be "seen by the user" — making audio-only AR technically incompatible.
- **Quote from @ddorwin:** "There are XR use cases (e.g., 'audio AR') that could build on poses and other capabilities exposed by core WebXR. The current spec language, though, appears to require visual devices."

### GoogleChrome/omnitone #2 — Mobile Browser Audio
- **URL:** https://github.com/GoogleChrome/omnitone/issues/2
- **Status:** Open, 23 comments — longest-running debate
- **Key insight:** Mobile browsers can't decode multichannel audio properly. #1 blocker for web spatial audio.

### GoogleChrome/omnitone #84 — Ambisonics Export Broken
- **URL:** https://github.com/GoogleChrome/omnitone/issues/84
- **Status:** Open, 12 comments
- **Key insight:** FOA→HOA conversion produces unplayable video output.

### GoogleChrome/omnitone #109 — "Is This Project Still Alive?"
- **URL:** https://github.com/GoogleChrome/omnitone/issues/109
- **Status:** Open
- **Key insight:** Leading web spatial audio project shows signs of stagnation after 7+ years.

### leomccormack/Spatial_Audio_Framework
- **URL:** https://github.com/leomccormack/Spatial_Audio_Framework
- **Stars:** 748 ⭐
- **Key insight:** Cross-platform ambisonic processing in C. Reference implementation for HRTF research.

## Guest Contact Notes
- **leomccormack**: 30+ years of spatial audio research. Creator of Spatial_Audio_Framework. Primary authority on HRTFs and ambisonics.
- **orighst (Boris Smus)**: Google/omnitone. Browser-based binaural rendering. Can speak to the gap between web audio and spatial audio.
- **cwilso**: WebXR contributor. Authored the sound source nodes proposal. Can speak to why audio was deferred.
- **toji**: WebXR spec editor. Can speak to the structural reasons audio was deferred.
- **hoch**: Omnitone maintainer. 7+ years of spatial audio pain points on the web.

## Unanswered Questions for Script
1. Why did the WebXR spec defer audio? Was it technical debt or design philosophy?
2. Can the web ever catch up to native spatial audio (Resonance Audio, Steam Audio)?
3. Is HRTF personalization a solved problem or still research-grade?
4. Does the "presence paradox" (audio matters more than visuals, but gets less investment) reflect a deeper perceptual truth?