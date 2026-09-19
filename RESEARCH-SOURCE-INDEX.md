# 📚 Research Source Index

> Master index of all GitHub sources consulted for 'The Future of Human Perception' podcast research.

---

## Repositories

| # | Repository | Stars | URL | Role in Research |
|---|---|---|---|---|
| 1 | jeromeetienne/AR.js | 15,791 | https://github.com/jeromeetienne/AR.js | Web AR tracking & latency |
| 2 | AR-js-org/AR.js | 5,988 | https://github.com/AR-js-org/AR.js | Web AR image/location tracking |
| 3 | hiukim/mind-ar-js | 2,733 | https://github.com/hiukim/mind-ar-js | Web AR + TensorFlow.js tracking |
| 4 | google-ar/three.ar.js | 2,914 | https://github.com/google-ar/three.ar.js | ARCore/Cardboard AR helper |
| 5 | ValveSoftware/openvr | 6,661 | https://github.com/ValveSoftware/openvr | OpenVR SDK — latency measurement |
| 6 | fholger/openvr_fsr | 1,809 | https://github.com/fholger/openvr_fsr | Foveated rendering / SuperResolution for VR |
| 7 | polygraphene/ALVR | 1,844 | https://github.com/polygraphene/ALVR | Wireless VR streaming |
| 8 | facebook/immersive-web-sdk | 357 | https://github.com/facebook/immersive-web-sdk | WebXR framework — interfaces & APIs |
| 9 | KhronosGroup/glTF | — | https://github.com/KhronosGroup/glTF | glTF spec — spatial audio extensions |
| 10 | mrdoob/three.js | 115,636 | https://github.com/mrdoob/three.js | Foundational 3D library |

## Issues & PRs Consulted

### Latency & Perceptual Threshold
- [ValveSoftware/openvr#249](https://github.com/ValveSoftware/openvr/issues/249) — Motion-to-photon latency measurement
- [ValveSoftware/openvr#258](https://github.com/ValveSoftware/openvr/issues/258) — Displaying old data, avoiding glFinish()
- [ValveSoftware/openvr#374](https://github.com/ValveSoftware/openvr/issues/374) — Periodic lag spikes
- [ValveSoftware/openvr#1704](https://github.com/ValveSoftware/openvr/issues/1704) — OVR tracker delay vs SteamVR

### Spatial Audio
- [KhronosGroup/glTF#2561](https://github.com/KhronosGroup/glTF/issues/2561) — Layered audio extension architecture proposal
- [KhronosGroup/glTF PR#2137](https://github.com/KhronosGroup/glTF/pull/2137) — KHR_audio_emitter
- [KhronosGroup/glTF PR#2631](https://github.com/KhronosGroup/glTF/pull/2631) — KHR_audio_environment
- [KhronosGroup/glTF PR#2632](https://github.com/KhronosGroup/glTF/pull/2632) — KHR_audio_graph
- [KhronosGroup/glTF#2506](https://github.com/KhronosGroup/glTF/issues/2506) — Synchronized immersive video + audio

### MR Interfaces & APIs
- [facebook/immersive-web-sdk#13](https://github.com/facebook/immersive-web-sdk/issues/13) — WebXR Hit-Test & Depth APIs
- [facebook/immersive-web-sdk#11](https://github.com/facebook/immersive-web-sdk/issues/11) — Locomotion floor collision
- [facebook/immersive-web-sdk#41](https://github.com/facebook/immersive-web-sdk/issues/41) — iOS Safari spatial UI activation
- [facebook/immersive-web-sdk#53](https://github.com/facebook/immersive-web-sdk/issues/53) — Cursor surface alignment
- [jeromeetienne/AR.js#826](https://github.com/jeromeetienne/AR.js/issues/826) — Image tracking reliability
- [jeromeetienne/AR.js#825](https://github.com/jeromeetienne/AR.js/issues/825) — Location-based AR failures
- [KhronosGroup/glTF#2162](https://github.com/KhronosGroup/glTF/issues/2162) — Light/audio under viewer scale

## Key Contributors
- @jeromeetienne — AR.js creator
- @hiukim — mind-ar-js creator
- @ekmett — OpenVR rendering/latency engineer
- @fholger — openvr_fsr creator
- @polygraphene — ALVR creator
- @rudybear — glTF spatial audio Architect
- @robertlong — KHR_audio_emitter PR author
- @najadojo — MSFT glTF audio extension
- @aribornstein — WebXR hit-test API advocate
- @mrdoob — three.js creator
- @jumpjack — three.ar.js AR+VR contributor

## External Resources
- [W3C Immersive Web Working Group](https://www.w3.org/immersive-web/)
- [WebXR Device API Specification](https://immersive-web.github.io/webxr/)
- [glTF Specification](https://www.khronos.org/gltf/)
- [Mixed Reality Toolkit Documentation](https://aka.ms/mrtkdocs)
- [AR.js Documentation](https://github.com/AR-js-org/AR.js/wiki)

---

*Last updated: September 2026*