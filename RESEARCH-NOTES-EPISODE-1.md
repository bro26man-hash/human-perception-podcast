# Research Notes — Episode 1: "Latency and the Perceptual Threshold"

## Key GitHub Sources

### WiVRn #1099 — Per-Client Scheduled Frames Stall xrEndFrame
- **URL:** https://github.com/WiVRn/WiVRn/issues/1099
- **Reported by:** @IceyMint (2026-09-08)
- **Key finding:** After Quest 3 enters passthrough and regains focus, `xrEndFrame` stalls because per-client scheduled frames were set *days* in the future. The compositor reports healthy 80 FPS while the app freezes for 47+ minutes.
- **Technical detail:** `wait_for_scheduled_free()` in Monado holds `scheduled_in_ms` values that countdown from ~2,862,818 seconds (47.7 minutes) for VRChat, and ~2,386,725 seconds (27.6 days) for WayVR overlay.
- **Perception insight:** The brain may detect frame pacing irregularity rather than average latency. This reframes the entire 20ms optimization target.

### ALVR #334 — Missing Latency
- **URL:** https://github.com/polygraphene/ALVR/issues/334
- **Reported by:** @jd-3d (2019-05-28, closed 2021-11-08)
- **Key finding:** Encode 8.3ms + transport 5.7ms + decode 18.9ms = 32.9ms, but total reported latency is 66.5ms. Missing 33.6ms unaccounted for.
- **Perception insight:** VR stacks underreport total system latency by 30-50%. We may be optimizing against a phantom number.

### google-ar/arcore-android-sdk #1779 — Camera/IMU Clock Offset
- **URL:** https://github.com/google-ar/arcore-android-sdk/issues/1779
- **Key finding:** Hardware clock synchronization between camera and IMU introduces 13-35ms offsets on Xiaomi/OPPO devices.
- **Perception insight:** Invisible to developers but catastrophic for perceptual stability. Visual feed lags vestibular input by up to 35ms.

### MixedRealityToolkit-Unity #82 — Input Threshold
- **URL:** https://github.com/MixedRealityToolkit/MixedRealityToolkit-Unity/issues/82
- **Reported by:** @ryan-motive (2023-08-20)
- **Key finding:** `triggerPressed` fires in natural hand position. Meta's "pinch" requires deliberate tension.
- **Perception insight:** Input threshold is a perceptual question, not just UX. Connects to rubber hand illusion.

### SteamVR-for-Linux #21 — Tracking Lag
- **URL:** https://github.com/ValveSoftware/SteamVR-for-Linux/issues/21
- **Key finding:** 97+ comments from users describing nausea-inducing lag between head movement and rendered frame.
- **Perception insight:** Even "smoothed" tracking can't hide the gap between head motion and visual feedback.

## Guest Contact Notes
- **xytovl**: WiVRn maintainer. Primary source on WiVRn #1099. Reach via Twitter/X.
- **jd-3d**: ALVR developer. Discovered missing latency. Reach via GitHub or ALVR Discord.
- **leinardi**: SteamVR-for-Linux maintainer. Long-standing VR latency researcher.
- **IceyMint**: WiVRn reporter. Instrumented the freeze measurements. Reach via Twitter/X.

## Unanswered Questions for Script
1. Does the brain detect frame pacing irregularity or average latency? (WiVRn #1099 suggests irregularity)
2. Can we trust industry latency measurements if 33.6ms goes unaccounted? (ALVR #334 suggests no)
3. Is the WebXR spec's visual-only design a perceptual bug? (webxr #815 suggests yes)
4. What's the right input threshold for MR controllers? (MRTK #82 suggests it's perceptual, not ergonomic)