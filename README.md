<div align="center">

![Profile Views](https://komarev.com/ghpvc/?username=aadidevsoni&style=for-the-badge&color=0a84ff&label=PROFILE+VIEWS)

</div>

<br/>

<div align="center">

```
                                     ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
                                    █                                                           █
                                    █               A A D I D E V   S O N I                     █
                                    █             ─────────────────────────────                 █
                                    █          Game Engine Dev  ·  Systems Programmer           █
                                    █       Open Source Contributor @ Blender  ·  IIITM Gwalior █
                                    █                                                           █
                                     ▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀
```

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=14&pause=1000&color=0A84FF&center=true&vCenter=true&width=650&lines=Open+Source+Developer+%40+Blender;Building+BerryFlux+%E2%80%94+An+open-source+C%2B%2B+Game+Engine;Graphics+Programming+%7C+Real-Time+Rendering+%7C+Low-Level+Systems;Open+to+collaborate+on+game+dev+%26+open-source)](https://git.io/typing-svg)

[![Blender Dev Profile](https://img.shields.io/badge/Blender-Developer_Profile-E87D0D?style=for-the-badge&logo=blender&logoColor=white)](https://projects.blender.org/Aadidev-Soni)

</div>

<br/>

---

## `// ABOUT`

```yaml
name:       Aadidev Soni
role:       Open Source Developer @ Blender · Game Engine Developer & Systems Programmer
location:   IIITM Gwalior, India
focus:      Real-time rendering · Engine architecture · Graphics programming
interests:  Game engines · Low-level systems · Open-source software
open_to:    Collaborations on game dev · Graphics · Open-source projects
```

---

## `// OPEN SOURCE @ BLENDER`

I contribute to **Blender**, working primarily in the core codebase around materials, Grease Pencil, and object data integrity.

### 🩹 [Fix #160789: Crash when moving Grease Pencil material slot with invalid active material index](https://projects.blender.org/blender/blender/pulls/160798)

**Status:** ✅ Merged into `blender-v5.2-release` by [Brecht Van Lommel](https://projects.blender.org/brecht) · `+39 −27` across 4 files

<details>
<summary><strong>Summary</strong></summary>

<br/>

Fixed a crash triggered when moving a Grease Pencil material slot, caused by an invalid active material index (`actcol == 0`).

**Root cause:** Some objects could end up with `ob->totcol > 0` while `ob->actcol == 0`, even though material indices are expected to be 1-based. This invalid state caused the material slot move operator to compute a bad remap index, leading to an out-of-bounds write and a crash in `BLI_array_permute()`. The invalid state could also be produced by Grease Pencil's `remove_unused_materials()` helper, which decremented `actcol` while removing unused slots.

**Fix:** Rather than patching the symptom in the operator, the fix addresses the invalid state at its source:
- Moved the Grease Pencil–specific `remove_unused_materials()` helper into `blenkernel/intern/material.cc` as a generic material utility, `BKE_object_material_remove_unused()`, reusing the existing `object_material_active_index_sanitize()` helper.
- Added sanitization of invalid active material indices in `object_blend_read_data()` on file load, preventing malformed or older `.blend` files from loading into an invalid state.

**Testing:** Verified against a repro file — before the fix, moving the first material slot down on a Grease Pencil object crashed Blender; after the fix, it no longer does. Also confirmed existing Grease Pencil operators using the new shared helper continue to work correctly.

</details>

> 🔗 [View the merged pull request →](https://projects.blender.org/blender/blender/pulls/160798)
> 🔗 [View my Blender developer profile →](https://projects.blender.org/Aadidev-Soni)

---

## `// CURRENT PROJECT`

### [`BerryFlux`](https://github.com/AadidevSoni/BerryFlux) — Open-Source C++ Game Engine

> A real-time game engine built from scratch — and built in the open.
> Collaborative platform where developers publish projects, fork, and submit PRs.
> Ships with an AI-powered prompt-to-code system (in development).

```
Language    C++17
Renderer    OpenGL → Vulkan (planned)
Build       CMake · Cross-platform
License     Apache 2.0
Status      [ ACTIVE DEVELOPMENT ]
```

**Systems shipped:**

| Module | Status |
|---|---|
| Event System — bitmask dispatcher, type-safe | ✅ Complete |
| Layer & LayerStack architecture | ✅ Complete |
| GLFW Window abstraction | ✅ Complete |
| OpenGL Renderer + API abstraction | ✅ Complete |
| Shader System — asset files, library, uniform API | ✅ Complete |
| Texture System — stb_image, blending, tinting | ✅ Complete |
| 2D Batch Renderer — single draw call | ✅ Complete |
| Material & Shader uniforms | ✅ Complete |
| Orthographic Camera Controller | ✅ Complete |
| ImGui Integration — docking & viewports | ✅ Complete |
| Custom smart pointers `Ref<T>` / `Scope<T>` | ✅ Complete |
| CPU-side instrumentation / profiling (Chrome trace format) | ✅ Complete |
| Entity Component System (ECS) | 🔲 Planned |
| Vulkan Backend | 🔲 Planned |
| Physics Engine | 🔲 Planned |
| AI Prompt-to-Code | 🔲 Planned |

---

## `// PROJECTS`

### [`BerryFlux Game Engine`](https://github.com/AadidevSoni/BerryFlux)
`C++` `OpenGL` `GLFW` `CMake` `ImGui` `GLM`

Open-source, real-time C++ game engine with full renderer abstraction, 2D batch renderer, shader library, material system, and ImGui editor integration. Designed as a collaborative platform — fork, contribute, merge.

---

### [`Gamified Mental Health Tracker`](https://github.com/AadidevSoni/Gamified-Mental-Health-Tracker)
`React` `Node.js` `Express` `MongoDB` `Redux`

Full-stack web platform that applies game mechanics to mental well-being. Daily SCADS assessments, score tracking over time, frog-and-lilypad progression system, and an interactive leaderboard. Built to make mental health monitoring engaging rather than clinical.

---

## `// TECH STACK`

**Systems & Graphics**

![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![C](https://img.shields.io/badge/C-555555?style=flat-square&logo=c&logoColor=white)
![OpenGL](https://img.shields.io/badge/OpenGL-5586A4?style=flat-square&logo=opengl&logoColor=white)
![GLFW](https://img.shields.io/badge/GLFW-lightgrey?style=flat-square)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)

**Web Development**

![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

**Languages**

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=java&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white)

**Tools**

![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Unity](https://img.shields.io/badge/Unity-FFFFFF?style=flat-square&logo=unity&logoColor=black)
![Blender](https://img.shields.io/badge/Blender-E87D0D?style=flat-square&logo=blender&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)

---

## `// STATS`

<div align="center">

<img height="175em" src="https://github-readme-stats.vercel.app/api?username=aadidevsoni&show_icons=true&theme=github_dark&hide_border=true&bg_color=00000000&title_color=0a84ff&icon_color=0a84ff&text_color=8b949e&include_all_commits=true&count_private=true"/>
<img height="175em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=aadidevsoni&layout=compact&theme=github_dark&hide_border=true&bg_color=00000000&title_color=0a84ff&text_color=8b949e"/>

</div>

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=aadidevsoni&theme=github-dark-blue&hide_border=true&background=00000000&ring=0a84ff&fire=0a84ff&currStreakLabel=0a84ff&sideLabels=8b949e&dates=8b949e&currStreakNum=ffffff&sideNums=ffffff"/>

</div>

---

## `// ROADMAP`

```
2025 ──────────────────────────────────────────────────────
         BerryFlux v1 — Core engine systems shipped
         Renderer2D · Shader Library · Material System
         Camera Controller · ImGui · Batch Renderer

2025–26 ────────────────────────────────────────────────────
         Blender open-source contributions (GPU / draw / EEVEE)
         Entity Component System (ECS)
         Scene serialization & asset pipeline
         Vulkan backend
         Physics integration

2026 ──────────────────────────────────────────────────────
         GSoC 2027 — Blender (target: GPU / draw / EEVEE)
         Native editor UI (built on BerryFlux)
         AI Prompt-to-Code system
         Open-source game hub platform
         Plugin & asset registry
```

---

## `// CONNECT`

<div align="center">

[![Blender](https://img.shields.io/badge/Blender_Dev_Profile-E87D0D?style=for-the-badge&logo=blender&logoColor=white)](https://projects.blender.org/Aadidev-Soni)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aadidev-soni)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/aadidev.2006)
[![LeetCode](https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black)](https://leetcode.com/aadidevsoni)
[![Codeforces](https://img.shields.io/badge/Codeforces-1F8ACB?style=for-the-badge&logo=codeforces&logoColor=white)](https://codeforces.com/profile/aadidev)
[![HackerRank](https://img.shields.io/badge/HackerRank-2EC866?style=for-the-badge&logo=hackerrank&logoColor=white)](https://hackerrank.com/aadidevbahrain)
[![CodeChef](https://img.shields.io/badge/CodeChef-5B4638?style=for-the-badge&logo=codechef&logoColor=white)](https://codechef.com/users/aadidev_soni)

</div>

<br/>

<div align="center">

```
// open to collaborations · PRs welcome · let's build something
```

</div>
