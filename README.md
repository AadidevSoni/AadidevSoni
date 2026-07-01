# Aadidev Soni

**Systems & Graphics Programmer** · Open Source Contributor @ Blender · B.Tech CSE, IIITM Gwalior (2028)

[Blender Developer Profile](https://projects.blender.org/Aadidev-Soni) · [LinkedIn](https://linkedin.com/in/aadidev-soni) · [LeetCode](https://leetcode.com/aadidevsoni) · [Codeforces](https://codeforces.com/profile/aadidev)

---

## About

I work on real-time rendering and low-level engine architecture. Currently contributing to **Blender's** core codebase (materials, Grease Pencil, GPU/draw module) and building **BerryFlux**, a C++/OpenGL game engine written from scratch. Targeting GSoC 2027 under Blender's GPU/draw/EEVEE modules.

---

## Open Source — Blender

**[Fix #160789 — Crash when moving Grease Pencil material slot with invalid active material index](https://projects.blender.org/blender/blender/pulls/160798)**
Merged into `blender-v5.2-release` by Blender core developer Brecht Van Lommel · `+39 / −27` across 4 files

Diagnosed and fixed a crash rooted in a broader data-integrity bug rather than a surface-level operator error. Objects could end up with an invalid active material index (`actcol == 0`) despite 1-based indexing conventions, which caused the material slot move operator to compute a bad remap array and crash inside `BLI_array_permute()`. Traced this back to Grease Pencil's `remove_unused_materials()` helper, which could decrement `actcol` to zero.

**Fix approach:**
- Generalized the fix by moving the Grease Pencil-specific helper into `blenkernel/intern/material.cc` as `BKE_object_material_remove_unused()`, reusing the existing index-sanitization utility rather than patching the symptom.
- Added active-material-index sanitization on `.blend` file load, so malformed or legacy files can no longer load into the invalid state at all.
- Verified against a reproduction file and confirmed no regressions in existing Grease Pencil operators.

This fix shipped as part of the Blender 5.2 release branch.

---

## Projects

### [BerryFlux](https://github.com/AadidevSoni/BerryFlux) — C++ Game Engine
`C++17` `OpenGL` `GLFW` `CMake` `ImGui` `GLM`

A real-time game engine built from the ground up, designed as an open, collaborative platform for engine-level learning and contribution.

- Full renderer abstraction over OpenGL with a batched 2D renderer (single draw call architecture)
- Shader asset pipeline with a uniform-typed material system
- ImGui-based editor tooling with docking/viewport support
- Custom smart pointer library (`Ref<T>`, `Scope<T>`) and a bitmask event dispatch system
- CPU-side instrumentation profiler emitting Chrome-trace-compatible JSON
- In progress: Vulkan backend, ECS, physics integration

### [Gamified Mental Health Tracker](https://github.com/AadidevSoni/Gamified-Mental-Health-Tracker) — Full-Stack Web App
`React` `Node.js` `Express` `MongoDB` `Redux`

A full-stack platform that applies game mechanics — daily assessments, score progression, leaderboards — to mental well-being tracking, built to make self-monitoring approachable rather than clinical.

---

## Technical Skills

**Systems & Graphics:** C++, C, OpenGL, GLFW, CMake, Vulkan (in progress)
**Web:** React, TypeScript, Node.js, MongoDB, TailwindCSS
**Languages:** JavaScript, Python, Java, Kotlin, C#
**Tools:** Git, Linux, Unity, Blender

---

## GitHub Stats

<div align="center">
<img height="165em" src="https://github-readme-stats.vercel.app/api?username=aadidevsoni&show_icons=true&theme=default&hide_border=true&hide_title=true&text_color=333333&icon_color=0a84ff&title_color=0a84ff"/>
<img height="165em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=aadidevsoni&layout=compact&theme=default&hide_border=true&text_color=333333&title_color=0a84ff"/>
</div>

---

## Currently

- Contributing to Blender's GPU/draw/EEVEE modules, working toward GSoC 2027
- Seeking internships in graphics/systems engineering (targets: NVIDIA, Qualcomm, Ubisoft)
- Adding a concurrency-based feature (asset loading worker thread / ECS job system) to BerryFlux

---

Open to collaboration on graphics programming, engine development, and open-source contribution. Feel free to reach out.
