# 🔍 GitHub Research Addendum — Live Audit

> Continuously updated audit of the most active AR, MR, and Spatial Computing repositories on GitHub, their hottest debates, and the people driving the conversations.

---

## 📊 Top Repositories Survey

### Tier 1: Flagship Projects

| Repository | Stars | Language | Focus | Maintenance Status |
|---|---|---|---|---|
| [jeromeetienne/AR.js](https://github.com/jeromeetienne/AR.js) | ⭐ 15,791 | HTML/JS | Web AR (marker + location-based) | 🟢 Community-maintained via AR-js-org org |
| [playcanvas/engine](https://github.com/playcanvas/engine) | ⭐ 16,700+ | JS | 3D engine with WebXR support | 🟢 Active |
| [immersive-web/webxr](https://github.com/immersive-web/webxr) | ⭐ 3,100+ | Spec | WebXR Device API standard | 🟢 W3C Working Group |
| [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity) | ⭐ 6,100+ | C# | Enterprise MR SDK | 🟢 Active (Microsoft) |
| [google/lullaby](https://github.com/google/lullaby) | ⭐ 1,197 | C++ | VR/AR rendering + spatial audio | 🟡 WIP — internal Google proven, external open |

### Tier 2: Specialized & Emerging

| Repository | Stars | Language | Focus | Maintenance Status |
|---|---|---|---|---|
| [hiukim/mind-ar-js](https://github.com/hiukim/mind-ar-js) | ⭐ 2,733 | JS | Web AR (image + face tracking via TF.js/WebGL) | 🟡 Solo developer (Hiukim) actively maintaining |
| [jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) | ⭐ 2,938 | JS | WebGL face tracking + AR filters | 🟢 Active |
| [exyte/ARTetris](https://github.com/exyte/ARTetris) | ⭐ 1,524 | Swift | ARKit + SceneKit demo | 🟡 Demo project |
| [thomwolf/Magic-Sand](https://github.com/thomwolf/Magic-Sand) | ⭐ 1,020 | C++ | AR sandbox software | 🟢 Active |
| [GeekLiB/AR-Source](https://github.com/GeekLiB/AR-Source) | ⭐ 1,903 | — | AR development resources collection | 🟢 Active |

---

## 👥 Key Contributors & Potential Guests

### The Pioneers

| Name | GitHub | Project | Why They'd Be Great Guests |
|---|---|---|---|
| **Jerome Etienne** | @jeromeetienne | AR.js creator | Built the most popular Web AR library; deep thoughts on making AR accessible on the web |
| **Nicolò Carpignoli** | @nicolocarpignoli | AR.js maintainer |_led the community transition to AR-js-org org model; 94-comment debate leader (issue #469) |
| **Hiukim** | @hiukim | MindAR creator | Solo developer building comparable Web AR to commercial products; candid about challenges |

### The Architecture Thinkers

| Name/Group | Project | Why They'd Be Great Guests |
|---|---|---|
| **Google Lullaby Team** | google/lullaby | Spatial audio + ECS rendering in C++; used across Google VR products (VR Home, YouTube, Earth) |
| **Microsoft MRTK Team** | MixedRealityToolkit-Unity | Enterprise MR interface design patterns at scale |
| **WebXR Working Group** | immersive-web/webxr | Spec authors who can speak to design gaps (especially the audio blind spot) |

### Active Community Voices (from Issue Authors)

| Name | GitHub | Notable Contribution |
|---|---|---|
| **Janpio** | @janpio | Filed the "Ensure the future of AR.js" critical issue (#469, 94 comments, 22 👀) — sustainability champion |
| **Dogzilla** | @dogzilla | Problematic the MindAR maintenance model (issue #526) — asks the question everyone hesitated to raise |
| **Marcusx2** | @marcusx2 | Exposed phone orientation tracking latency in MindAR (issue #428) — real-world perceptual lag case study |
| **Marco6ocram** | @marco6ocram | Working on A-Frame scene compositing outside MindAR targets (issue #537) — MR interface designer |
| **Blitzy** | @Blitzy | Decoupled ThreeJS from MindAR (issue #104, 18 comments) — architectural purist |
| **Maxfyk** | @maxfyk | Implementing "keep objects always visible" feature (PR #327) — MR persistence researcher |

---

## 🔥 Hottest Debates by Perceptual Theme

### 1. 🕐 Perceptual Latency & the 20ms Threshold

**The Core Question:** *How much lag can the human brain tolerate before VR/AR becomes physically uncomfortable?*

| Source | Debate Summary | Link |
|---|---|---|
| **AR.js #469** | "Ensure the future of AR.js" — 94-line thread on whether open-source AR can meet commercial latency requirements. Janpio highlighted that the repo state wasn't sellable to clients. Labeled `critical`. 22 👀, 15 👍, 7 🎉. Nicolò Carpignoli closed it by moving to AR-js-org. | [Link](https://github.com/jeromeetienne/AR.js/issues/469) |
| **AR.js #544** | "NFT (Natural Feature Tracking) on AR.js" — 27-comment debate on whether natural feature tracking can achieve the low latency that marker-based tracking provides. The trade-off between tracking robustness and perceptual lag. | [Link](https://github.com/jeromeetienne/AR.js/issues/544) |
| **MindAR #428** | "Switching phone orientation makes detection terrible" — Marcusx2 documented that even after the claimed fix in v1.2.2, orientation switching still causes detection failure and incorrect rotation. A visceral case study in perceptual latency affecting real users. 2 👀. | [Link](https://github.com/hiukim/mind-ar-js/issues/428) |

**Key Insight for Episode 1:** The tension isn't just engineering — it's perceptual. The brain doesn't care about your render pipeline architecture; it cares that the virtual pencil lines up with the real edge *now*. Every millisecond of mismatch is a betrayal of presence.

---

### 2. 🔊 Spatial Audio & the WebXR Gap

**The Core Question:** *Why does the WebXR spec prioritize vision when hearing is arguably more important for presence?*

| Source | Debate Summary |
|---|---|
| **Google Lullaby** | Lullaby explicitly supports "spatial audio" as a key feature (per README), used internally by VR Home, YouTube, and Play Movies. But the repo is labeled "work-in-progress" for external contribution — the spatial audio implementation isn't available as a public API yet. |
| **WebXR Spec** | The W3C Immersive Web Working Group spec focuses heavily on visual rendering APIs. Spatial audio rendering lacks a standardized web API — implementations are left to proprietary SDKs or自行 roll-your-own. |
| **MindAR** | Zero spatial audio integration. MindAR is purely visual tracking. This is symptomatic of the broader Web AR ecosystem: sound is an afterthought, if it's included at all. |

**Key Insight for Episode 2:** We trust what we hear more than what we see in virtual environments. Auditory presence is the canary in the coal mine — if the audio lies, the whole experience collapses, even if the visuals are perfect. The WebXR spec's visual bias isn't just an oversight; it's a perceptual blind spot in the standards community.

---

### 3. 🕶️ Mixed Reality Interfaces & the Compositing Crisis

**The Core Question:** *How do you blend virtual content with reality so seamlessly that the brain stops questioning it?*

| Source | Debate Summary | Link |
|---|---|---|
| **MindAR #537** | "Render the rest of the A-Frame Scene outside the MindAR Target" — Marco6ocram is tackling the fundamental MR compositing problem: how do you render AR content that exists *beyond* the tracked target, in the real user's environment? 3 comments. | [Link](https://github.com/hiukim/mind-ar-js/issues/537) |
| **MindAR #526** | "Is this repo abandonware? Should I switch to ar.js?" — Dogzilla asked the question that haunts every solo-dev AR project: can an individually-maintained Web AR library compete with Microsoft and Google's MR stacks? 13 comments, 3 heart reactions. | [Link](https://github.com/hiukim/mind-ar-js/issues/526) |
| **MindAR #527** | "Can track multiple faces on face-tracking?" — Nninnnin wants multi-user face tracking. This is the MR interface scalability question: tracking one face is a demo; tracking a room full of people is an interface. | [Link](https://github.com/hiukim/mind-ar-js/issues/527) |
| **MindAR #539** | "Front camera image tracking" — Totius wants front-camera support, which is essential for MR passthrough and environmental understanding. Currently MindAR only supports back-camera. | [Link](https://github.com/hiukim/mind-ar-js/issues/539) |
| **MindAR #104** | "Decouple ThreeJS from MindAR" — Blitzy's 18-comment architectural debate about whether the 3D rendering engine should be a hard dependency. This is about MR interface flexibility: how easily can you swap rendering strategies for different MR contexts? | [Link](https://github.com/hiukim/mind-ar-js/issues/104) |

**Key Insight for Episode 3:** MR isn't an engineering problem — it's a perceptual negotiation. Every virtual object is a diplomat that must convince the brain it belongs in the physical world. The compositing crisis isn't about pixels; it's about trust.

---

## 🔄 Ongoing Community Dynamics

### The Open-Source AR Sustainability Question
AR.js #469 (94 comments) and MindAR #526 (13 comments) both surface the same meta-debate: **Can community-driven AR projects survive against corporate-backed alternatives?**

- AR.js survived by moving to an org model (AR-js-org)
- MindAR is still solo-dev (Hiukim), fundraising via Udemy courses and MindAR Studio
- Google Lullaby is proven internally but not yet open for external contributions
- Microsoft MRTK is enterprise-backed but complex for indie developers

**Podcast angle:** The sustainability of open AR directly impacts the pace of perceptual innovation. If the best researchers can't get their latency breakthroughs into a maintained public repo, the 20ms rule stays a research paper, not a shipping feature.

### The Web vs. Native AR Divide
- AR.js and MindAR are **web-first** (run in browsers)
- Google Lullaby is **native C++** (Android/iOS/Linux/Windows)
- MRTK is **Unity-based** (cross-platform but engine-dependent)

**Podcast angle:** The platform choice IS a perceptual choice. Web AR trades performance for accessibility. Native AR trades accessibility for frame-time guarantees. The brain doesn't care about your build system — but it cares about your frame budget.

---

## 📋 Issue Telegram Channel — Topics to Watch

| Repo | Issue # | Why It Matters | Urgency |
|---|---|---|---|
| AR.js | #469 | Open-source AR survival = perceptual progress speed | 🔴 High |
| AR.js | #544 | NFT tracking latency = the perceptual cost of markerless |
| MindAR | #428 | Orientation switching lag = real user pain, not hypothetical |
| MindAR | #526 | Solo-dev sustainability = can open AR compete with MS/Google? |
| MindAR | #537 | MR compositing outside targets = the core interface challenge |
| MindAR | #527 | Multi-face tracking = scalable MR interfaces |
| MindAR | #539 | Front-camera MR = environmental occlusion for realism |
| MindAR | #104 | Engine decoupling = architectural flexibility for MR |
| Lullaby | README | Spatial audio + ECS = the only open-source spatial audio stack in C++ |

---

*Last updated: September 2026*  
*Contributors to this audit: @jeromeetienne, @nicolocarpignoli, @hiukim, @janpio, @dogzilla, @marcusx2, @marco6ocram, @Blitzy, @maxfyk*
*To add findings, comment on the corresponding issues or submit a PR to this file.*