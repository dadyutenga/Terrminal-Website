# Terminal Agent Landing Page

A high-contrast, cyber-minimalist marketing surface for the Terminal Agent — an advanced AI terminal assistant engineered for precision automation, sandboxed execution, and developer-first workflows. The interface is built with Vue 3 and Tailwind CSS, layering CRT-inspired textures, glitch typography, and a live faux-terminal to deliver a distinctly technical experience.

## Features
- **Glitch-reactive hero** with animated caret, GSAP-driven text reveals, and a decisive "Open Terminal" call-to-action.
- **Angular feature matrix** showcasing execution, reasoning, and automation capabilities with micro-interactions on hover.
- **System architecture spotlight** rendered as a syntax-highlighted code block for transparent storytelling.
- **Interactive terminal window** simulating conversational command streams within a draggable glass panel.
- **Final command CTA** reinforcing the launch narrative with geometric framing and accent lighting.

## Tech Stack
- [Vue 3](https://vuejs.org/) + `<script setup>` Composition API
- [Vite](https://vitejs.dev/) bundler
- [Tailwind CSS](https://tailwindcss.com/) utility framework
- [GSAP](https://greensock.com/gsap/) for performant timeline animations

## Getting Started
1. **Install dependencies**
   ```bash
   npm install
   ```
2. **Start the dev server**
   ```bash
   npm run dev
   ```
3. **Build for production**
   ```bash
   npm run build
   ```
4. **Preview the production build**
   ```bash
   npm run preview
   ```

> **Note:** If your environment restricts access to npm mirrors (e.g., 403 fetching `@vitejs/plugin-vue`), configure an alternate registry before running `npm install`.

## Project Structure
```
├── index.html
├── src
│   ├── App.vue                # Layout composition that sequences hero, features, architecture, live demo, and CTA
│   ├── assets
│   │   └── main.css           # Global variables, typography, scanline overlays, utility styles
│   └── components
│       ├── TerminalHero.vue   # Hero section with glitch reveal and command-line headline
│       ├── FeaturesSection.vue# Asymmetric feature grid with accent motion
│       ├── CodeBlock.vue      # Syntax-highlighted architecture narrative
│       ├── TerminalWindow.vue # Faux-terminal demo with streaming dialogue
│       ├── CtaSection.vue     # Closing call-to-action block
│       └── ScanlineOverlay.vue# CRT texture overlay for ambience
├── tailwind.config.js
└── vite.config.js
```

## Design System
- **Typography:** `Space Grotesk` for primary copy, `IBM Plex Mono` for technical labeling and code-inspired accents.
- **Color Variables:** Defined under `:root` in `src/assets/main.css` (`--bg-primary`, `--accent-primary`, etc.) for consistent palette management.
- **Motion Language:** GSAP timelines power glitch reveals, staggered feature reveals, and caret blinking without compromising performance.
- **Atmospherics:** Noise overlays, holographic gradients, and geometric clip-paths reinforce the cyber-minimalist identity.

## License
This project is provided as-is for demonstration purposes. Adapt or extend it to align with your Terminal Agent deployment needs.
