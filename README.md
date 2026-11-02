# 🚀 CODEX ITER — Recruitment & Orientation Portal 2026

> **A Decade of Technical Culture.**  
> The official recruitment portal and interactive induction platform for **CODEX ITER** (SOA University, Bhubaneswar), featuring a Neo-Brutalist design language, interactive syllabus notepad, dynamic recruitment timelines, and the iconic **Spidey Tracker** geospatial command center.

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Design & Aesthetic Philosophy](#-design--aesthetic-philosophy)
  - [Neo-Brutalism Meets Retro-Tech Comic UI](#neo-brutalism-meets-retro-tech-comic-ui)
  - [Color Palette & Design Tokens](#color-palette--design-tokens)
  - [Micro-Interactions & Animation Stack](#micro-interactions--animation-stack)
- [Page Architecture & Core Sections](#-page-architecture--core-sections)
  - [1. Sticky Glassmorphic Navbar](#1-sticky-glassmorphic-navbar)
  - [2. Hero & Legacy Theme Transition](#2-hero--legacy-theme-transition)
  - [3. Impact Stats ("A Community Built on Results")](#3-impact-stats-a-community-built-on-results)
  - [4. Academic Archives & Ruled Notepad Viewer](#4-academic-archives--ruled-notepad-viewer)
  - [5. Previous Year Questions (PYQ) Preparation](#5-previous-year-questions-pyq-preparation)
  - [6. Neo-Brutalist Recruitment Roadmap](#6-neo-brutalist-recruitment-roadmap)
  - [7. Club Code of Conduct & Rules](#7-club-code-of-conduct--rules)
  - [8. Open Recruitment Tracks (Tech & Non-Tech)](#8-open-recruitment-tracks-tech--non-tech)
  - [9. Animated FAQ Accordion](#9-animated-faq-accordion)
  - [10. Final Call-to-Action & Community Hub](#10-final-call-to-action--community-hub)
- [🕷️ Deep Dive: The Spidey Tracker Engine](#️-deep-dive-the-spidey-tracker-engine)
  - [Concept & Architecture](#concept--architecture)
  - [Desktop Window Framing (`codex_tracker.exe`)](#desktop-window-framing-codex_trackerexe)
  - [Interactive Map Engine & Vector Layer](#interactive-map-engine--vector-layer)
  - [The Glowing Purple "Aarambh" Event Pin](#the-glowing-purple-aarambh-event-pin)
  - [Community Updates Sidebar & Sightings System](#community-updates-sidebar--sightings-system)
  - [Preloader Diagnostic Stream & Ticker Module](#preloader-diagnostic-stream--ticker-module)
  - [Coordinate Transformation Pipeline](#coordinate-transformation-pipeline)
- [💻 Tech Stack & Dependencies](#-tech-stack--dependencies)
- [📁 Project Directory Structure](#-project-directory-structure)
- [🛠️ Getting Started & Local Development](#️-getting-started--local-development)
- [👥 Credits & Team](#-credits--team)

---

## 🌟 Overview

The **CODEX Orientation Portal** is the official digital gateway for the 2026 induction drive at **Institute of Technical Education and Research (ITER)**, Siksha 'O' Anusandhan (SOA) University, Bhubaneswar.

Engineered to inspire incoming freshmen and sophomore developers, the portal ditches generic corporate templates in favor of a bold, high-octane **Neo-Brutalist comic aesthetic** fused with a fully interactive tactical radar map — the **Spidey Tracker**.

Key capabilities:
- **Interactive Induction Roadmap**: Clear step-by-step guidance across Technical (3 rounds) and Non-Technical (2 rounds) recruitment tracks.
- **Academic Archives (Notepad Viewer)**: Year-wise essential syllabus and topics required for college exams and placement preparation.
- **Embedded Geospatial Tracker**: A customized, radar-styled vector map showcasing CODEX mentors, alumni achievements across Fortune 500 companies (Dell, JPMorgan, Reltio), and real-time orientation venue markers.
- **Zero-Latency Client Persistence**: Local storage and state-driven sighting reporting without heavy database overhead.

---

## 🎨 Design & Aesthetic Philosophy

### Neo-Brutalism Meets Retro-Tech Comic UI

The visual identity combines modern web performance with the raw, confident energy of comic book halftones and 90s OS tactical software:

1. **Stark Structural Borders**: Prominent `3px` to `4px` solid slate borders (`#0f172a` / `#000000`) enclosing every container and card.
2. **Hard-Edge Offset Shadows**: Unblurred brutalist drop shadows (`box-shadow: 4px 4px 0px 0px #03045E;` and `7px 7px 0px #03045E`), delivering tactile depth without fuzzy blur layers.
3. **Intentional Skew & Rotation**: Asymmetrical card tilts (`rotate(-0.8deg)` vs. `rotate(0.8deg)`) and text skews (`transform: skewY(-2deg)`) that mimic cut-and-paste comic layouts.
4. **Halftone Dot Matrix**: Background surfaces styled with subtle radial dot grids (`radial-gradient(circle, rgba(255, 255, 255, 0.6) 2.5px, transparent 2.5px)`) over vibrant gradient fills.
5. **Terminal & Tactical Badges**: Monospace status indicators (`[ TECH_TRACK ]`, `// INDUCTION PHASES`, `STATUS: HIRING`, `codex_tracker.exe`).

### Color Palette & Design Tokens

| Token / Color | Hex Code | Role & Usage |
| :--- | :--- | :--- |
| **Vibrant Magenta** | `#F53D8A` | Primary accent, primary CTA buttons, active state toggles, highlight badges |
| **Deep Cosmic Navy** | `#03045E` / `#0707F2` | Hard brutalist shadow layers, display heading accents, active tab borders |
| **Dusty Light Blue** | `#C4DFED` | Card backgrounds, tactical badge backings, window title bars |
| **Icy Sky Blue** | `#B3E5FC` / `#CAF0F8` | Page background gradients, transition overlays, notebook ruling |
| **Soft Rose** | `#FCB6D1` | Non-technical domain cards, gradient stops, contrast badges |
| **Legal Notepad Yellow** | `#FFF9C4` | Authentic retro ruled notepad background for the syllabus section |
| **Slate 900** | `#0F172A` | Core typography, structural boundaries, container outlines |
| **Aarambh Purple** | `#A855F7` / `#7E22CE` | Glowing neon star pin representing the CODEX Aarambh Orientation Event |

### Micro-Interactions & Animation Stack

- **Dynamic Typewriter (`useTypingEffect`)**: Simulates a live cyber-terminal typing the welcome message with a blinking cursor block.
- **Staggered Character Reveals (`AnimatedHeading`)**: Splits headings into individual letter spans, animating them upward with progressive delays and blur dissipation.
- **Sonar Radar Waves (`SonarButton`)**: Constant expanding ring pulse on primary actions, guiding the eye toward registration.
- **Ambient Code Badges (`FloatingCode`)**: Lightweight, floating monospace code tags (`<div>`, `{ CODEX }`, `npm run build`) drifting subtly across the canvas.
- **Legacy Theme Transition Wipe**: On first load, a radial circle wipe (`clipPath: circle(0% at 100% 0%)`) expands out to transition from CODEX's legacy dark UI into the 2026 theme.
- **Reduced Motion Guard**: Full support for accessibility; all motion springs gracefully fall back to static layouts when `(prefers-reduced-motion: reduce)` is detected.

---

## 🏛️ Page Architecture & Core Sections

```
┌────────────────────────────────────────────────────────┐
│ 1. Sticky Glassmorphic Navbar (CODEX ITER Logo + Menu) │
├────────────────────────────────────────────────────────┤
│ 2. Hero Section: Split Grid                            │
│    - Left: Dramatic Typography & Registration CTAs    │
│    - Right: Embedded Spidey Tracker (codex_tracker.exe)│
├────────────────────────────────────────────────────────┤
│ 3. Impact Stats: "A Community Built on Results"        │
├────────────────────────────────────────────────────────┤
│ 4. Academic Archives: Retro Ruled Notepad Viewer       │
├────────────────────────────────────────────────────────┤
│ 5. Practice Makes Perfect: PYQ Question Bank           │
├────────────────────────────────────────────────────────┤
│ 6. Recruitment Roadmap: Phased Induction Timeline      │
│    - [ TECH_TRACK ] vs. [ NON_TECH_TRACK ] Toggles     │
├────────────────────────────────────────────────────────┤
│ 7. Club Code of Conduct: Official Rules & Regulations  │
├────────────────────────────────────────────────────────┤
│ 8. Open Domains: Technical & Non-Technical Tracks      │
├────────────────────────────────────────────────────────┤
│ 9. Frequently Asked Questions (FAQ Accordions)         │
├────────────────────────────────────────────────────────┤
│ 10. Full-Bleed Call to Action & Community Footer       │
└────────────────────────────────────────────────────────┘
```

### 1. Sticky Glassmorphic Navbar
- **Dynamic Scroll State**: Transitions from clean solid white to translucent frosty blue (`rgba(179, 229, 252, 0.85)`) with an active `10px` backdrop blur upon scrolling past 80px.
- **Brutalist Outlines**: Separated from the page body by a heavyweight `4px` black border.
- **Responsive Navigation**: Features smooth anchor jumps to `#domains`, `#timeline`, `#syllabus`, `#pyq`, `#faq`, and a external link button to the club's main portal.

### 2. Hero & Legacy Theme Transition
- Displays bold skewed headers: `CODEX START 2026`.
- Direct action triggers: **"Register Now"** (linking to Google Forms) and **"View Timeline"** (smoothly scrolling to recruitment phases).
- Houses the live **Spidey Tracker iframe** mounted inside a tilted window frame.

### 3. Impact Stats ("A Community Built on Results")
- High-impact data grid tracking club achievements, active members, production-grade applications shipped, and industry hackathon accolades.
- Wrapped in asymmetric brutalist cards with deep offset shadows.

### 4. Academic Archives & Ruled Notepad Viewer
- Built like a classic yellow legal notepad (`#FFF9C4`) with continuous blue ruled lines (`repeating-linear-gradient(transparent, transparent 31px, #B3E5FC 31px, #B3E5FC 32px)`).
- Provides tabs for **First Year** and **Second Year** coursework.
- Breaks down semester subjects, core conceptual topics, and targeted mastery levels (Foundational, Intermediate, Advanced).

### 5. Previous Year Questions (PYQ) Preparation
- Provides prospective recruits with realistic exam expectations.
- Direct link to past test papers, problem sets, and coding assessment guidelines.
- Features prep advice, difficulty breakdowns, and syllabus change disclaimers.

### 6. Neo-Brutalist Recruitment Roadmap
- Interactive state-driven tabs:
  - **`[ TECH_TRACK ]`** (3 Phases): Online Coding Assessment & Aptitude ➔ Domain Task & Project Building ➔ Personal Technical & HR Interview.
  - **`[ NON_TECH_TRACK ]`** (2 Phases): Portfolio & Creative Task Submission ➔ Group Discussion & Personal Interview.
- Each phase is detailed with date tags, required competencies, and submission warnings.

### 7. Club Code of Conduct & Rules
- Transparent club policy governing test integrity (strict ban on unapproved AI-cheating tools and tab switching during assessments).
- Ground rules on attendance, collaborative spirit, and communication discipline.

### 8. Open Recruitment Tracks (Tech & Non-Tech)
- Two asymmetric card columns:
  - **Technical Domains**: Full-Stack Web Development, Native & Cross-Platform Mobile Apps, Competitive Programming (CP & DSA), Cloud & DevOps, AI / Machine Learning, Cybersecurity.
  - **Non-Technical Domains**: UI/UX & Interaction Design, Motion Graphics & Video Editing, Technical Content Writing & SEO, Public Relations & Event Management, Social Media Strategy.

### 9. Animated FAQ Accordion
- Answers common freshman queries: eligibility criteria, branch restrictions (open to all engineering streams), preparation strategies, and time commitment.
- Interactive chevron toggles with smooth Framer Motion height expansions.

### 10. Final Call-to-Action & Community Hub
- High-energy magenta banner inviting candidates to register immediately.
- Direct invitation to the official **CODEX WhatsApp Channel** for announcements.
- Full footer with social links (LinkedIn, Instagram, Email) and copyright information.

---

## 🕷️ Deep Dive: The Spidey Tracker Engine

The **Spidey Tracker** (`/SpideyTracker/index.html`) is an immersive, Marvel-inspired real-time tactical radar integrated directly into the orientation page. Originally developed on an Astro & Mapbox/Google Maps vector engine, it has been transformed into CODEX's dedicated campus reconnaissance console.

```
┌────────────────────────────────────────────────────────┐
│  🔴 🟡 🟢  codex_tracker.exe                           │
├────────────────────────────────────────────────────────┤
│ ┌────────────────────────────────────────────────────┐ │
│ │  [RADAR VIEW - BHUBANESWAR, ODISHA]                │ │
│ │                                                    │ │
│ │         🟣 ★ AARAMBH ORIENTATION PIN (GLOWING)     │ │
│ │              [20.24919° N, 85.80163° E]            │ │
│ │                                                    │ │
│ │    🔵 Core Recruits Pins                           │ │
│ │    🟡 Mentor / Coordinator Locations               │ │
│ │                                                    │ │
│ └────────────────────────────────────────────────────┘ │
│ [FEED] Open Community Updates  │ Ticker: Welcome to CODEX
└────────────────────────────────────────────────────────┘
```

### Concept & Architecture
The tracker operates as an autonomous web application embedded inside an `<iframe>` within `App.tsx`. It runs a rich client-side runtime including:
- Vector/Canvas 2D map projection (`window.spideyMap`).
- Event-driven communication bus (`document.dispatchEvent`).
- Reactive UI layers (preloader, audio opt-in, modal system, ticker track, community sidebar).

### Desktop Window Framing (`codex_tracker.exe`)
Rather than appearing as a generic web map, the tracker is enclosed in a stylized retro OS container:
- **Chrome Bar**: Displays macOS/retro-terminal traffic light dots (Red, Yellow, Green) and title `codex_tracker.exe`.
- **Brutalist Tilted Backing**: Sits on top of an animated tilted background layer (`rotate: [3, 4, 3]`) with deep blue shadow borders.
- **Smart Audio Bypass**: An automated `onLoad` observer script quietly triggers the "Sound Off" action to skip intro audio prompts without user friction:
  ```typescript
  const btn = doc.querySelector<HTMLButtonElement>('[data-sound-enabled="false"]');
  if (btn) btn.click();
  ```

### Interactive Map Engine & Vector Layer
- **Engine**: Map2D engine rendering tiles, satellite textures, and SVG vector markers.
- **Event Bus Sync**:
  1. Map loads and dispatches `app:map-2d-ready`.
  2. The custom runtime listener captures this event and broadcasts `app:event-pins-ready` with custom pin payloads.
  3. Pins are dynamically bound to the map's vector layer (`#map-vector-layer`).

### The Glowing Purple "Aarambh" Event Pin
To commemorate **Aarambh — The CODEX Orientation Event**, an exclusive pin was engineered directly into the map engine:

- **Geographic Coordinates**:
  - **Latitude**: `20.24919° N`
  - **Longitude**: `85.80163° E`
  - **Location**: ITER Campus, SOA University, Bhubaneswar.
- **Visual Design**: An inline SVG Data URI rendering an 8-pointed star with a radial violet-to-magenta gradient (`#e879f9` to `#7e22ce`) and bright highlight borders (`#f0abfc`).
- **Continuous Pulsing Glow**:
  ```css
  @keyframes aarambh-glow {
    0%, 100% {
      filter: drop-shadow(0 0 4px #c084fc) drop-shadow(0 0 10px #a855f7);
      transform: scale(1);
    }
    50% {
      filter: drop-shadow(0 0 12px #e879f9) drop-shadow(0 0 24px #c026d3);
      transform: scale(1.15);
    }
  }
  #map-vector-layer .pin-aarambh {
    content: url("data:image/svg+xml,...");
    width: 44px !important;
    animation: aarambh-glow 2s ease-in-out infinite;
  }
  ```
- **Interactive Sighting Card**: Clicking the pin launches an event card displaying the orientation date, venue details, and live status.

### Community Updates Sidebar & Sightings System
1. **Repurposed Header Button**:
   - The original `#sound-toggle-btn` was repurposed into the **FEED / Community Updates** trigger.
   - Clicking dispatches `app:open-x-feed` to slide out the community log.
2. **Alumni & Mentor Data Feed (`x-feed.json`)**:
   - Features active updates from key club coordinators and alumni placed at leading tech giants:
     - **Uddalak Mukhopadhyay** (Frontend / UI/UX @ Dell)
     - **Tushar Kumar** (CP / DSA @ ITER)
     - **Amlan Anshuman Nayak** (CP / DSA @ Dell)
     - **Pritish Biswas** (DevOps / Frontend @ JPMorgan)
     - **Amaresh Swain** (CP / Algorithms @ Reltio)
     - **P Shreetam Kumar** (Technical Writing / SEO)
3. **Interactive Sighting Reporting**:
   - Users can pin their own location or report a sighting by picking coordinates on the map.
   - Sightings are processed and stored in local state (`userPins`), with automatic pin DOM rendering and cleanup.

### Preloader Diagnostic Stream & Ticker Module
The tracker preloader mimics a high-security tactical terminal boot sequence with 34 real-time diagnostic checks:
```
[01] Initializing CODEX Tracker v4.2.0…
[02] BOOTING CORE SERVICES [OK]
[03] INITIALIZING MAP RENDER PIPELINE...
...
[33] SECURE CHANNEL ESTABLISHED [OK]
[34] ALL SYSTEMS NOMINAL - TRACKER ONLINE
```
- **Ticker Track**: Bottom ticker continuously scrolls updates: `Welcome to CODEX` and `CODEX ITER - A DECADE OF TECHNICAL CULTURE`.

### Coordinate Transformation Pipeline
To support map projection accuracy across global and regional systems, `app.js` includes built-in **GCJ-02 to WGS-84** geodesic conversion algorithms (`gcj02ToWgs84`), preventing spatial drift when converting user-picked coordinates to vector overlay pins.

---

## 💻 Tech Stack & Dependencies

### Frontend Core
- **React 19 (`v19.2.4`)**: Component rendering and reactive state hooks.
- **TypeScript (`v5.9.3`)**: Complete type safety across components and event payloads.
- **Vite 8 (`v8.0.0`)**: Blazing fast ESM dev server and optimized production bundler.

### Styling & Animation
- **Tailwind CSS v4 (`v4.2.1`)**: Next-gen CSS utility engine with native `@theme` configuration.
- **`@tailwindcss/postcss` & `tw-animate-css`**: Custom animations and styling pipeline.
- **Framer Motion (`v12.36.0`)**: Spring animations, character staggering, scroll-triggered reveals, and layout transitions.

### Icons & Utilities
- **Lucide React (`v0.577.0`)**: Crisp, scalable icons for social links and navigation.
- **Google Material Symbols**: Vector iconography for recruitment phases.
- **clsx & tailwind-merge**: Conditional CSS class combination.
- **React Helmet Async (`v3.0.0`)**: SEO metadata, Open Graph cards, and Twitter preview tags.

### Tracker Subsystem
- **Astro v6.2.2 Runtime**: Compiled static engine powering the standalone `SpideyTracker`.
- **Mapbox / Vector Maps**: 2D coordinate rendering and marker collision detection.

---

## 📁 Project Directory Structure

```text
codex-tracker-orientation/
├── public/
│   ├── SpideyTracker/               # Standalone interactive tactical tracker
│   │   ├── api/
│   │   │   ├── sightings.json       # Coordinator, mentor & recruit map pins
│   │   │   └── x-feed.json          # Live alumni placement updates & feed
│   │   ├── assets/app/
│   │   │   ├── app.js               # User system, pin dispatcher, Aarambh pin
│   │   │   └── app.css              # Custom modal styling & UI frames
│   │   ├── css/_astro/              # Compiled Astro style sheets
│   │   ├── fonts/                   # Pixel & technical fonts (PF Videotext, etc.)
│   │   ├── img/images/              # UI frames, buttons, and icons
│   │   ├── js/_astro/               # Astro map controllers (Map2D, XFeed, etc.)
│   │   ├── sounds/                  # Audio clips and sound effects
│   │   ├── config.js                # Tracker runtime configurations
│   │   ├── favicon.png              # Tracker favicon
│   │   └── index.html               # Main SpideyTracker document
│   ├── city-map.png                 # Auxiliary map textures
│   ├── codex_dark.png               # CODEX dark emblem
│   └── favicon.png                  # Site favicon
│
├── src/
│   ├── assets/                      # Logos, background webs, and mascot artwork
│   │   ├── bg_logo.png              # Watermark background logo
│   │   ├── codex_dark.png           # Primary club brand logo
│   │   └── code_light.png           # Inverted brand logo
│   ├── components/
│   │   ├── animations/
│   │   │   └── ScrollReveal.tsx     # Framer Motion scroll and stagger wrappers
│   │   └── tactical/                # Tactical map types, controls, and pixel bits
│   │       ├── CustomizePanel.tsx
│   │       ├── PixelBits.tsx
│   │       ├── TacticalMap.tsx
│   │       └── types.ts
│   ├── lib/
│   │   └── utils.ts                 # Class merging helpers (cn utility)
│   ├── App.tsx                      # Master layout and page orchestrator (1300+ lines)
│   ├── index.css                    # Tailwind v4 theme tokens and neo-brutalist utilities
│   ├── main.tsx                     # React application entry point
│   └── vite-env.d.ts                # Vite environment definitions
│
├── index.html                       # HTML5 root template with font preloads
├── package.json                     # Project scripts and dependencies
├── postcss.config.js                # PostCSS build pipeline
├── tsconfig.json                    # TypeScript compiler options
└── vite.config.ts                   # Vite bundler configurations
```

---

## 🛠️ Getting Started & Local Development

### Prerequisites
- **Node.js**: `v18.0.0` or higher (Node 20+ recommended)
- **Package Manager**: `npm`, `pnpm`, or `yarn`

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/codex-iter/codex-tracker-orientation.git
   cd codex-tracker-orientation
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the local development server:**
   ```bash
   npm run dev
   ```
   Open [http://localhost:5173](http://localhost:5173) in your browser to view the portal.

4. **Build for production:**
   ```bash
   npm run build
   ```
   The compiled output will be generated inside the `dist/` directory, ready to be deployed to Vercel, Netlify, or GitHub Pages.

5. **Preview the production build locally:**
   ```bash
   npm run preview
   ```

---

## 👥 Credits & Team

- **Organization**: [CODEX ITER](https://www.codex-iter.in/) — The Official Coding & Development Club of ITER, SOA University.
- **Design & Engineering**: Built with ❤️ by the CODEX Core Development Team.
- **Inspiration**: Marvel's Spider-Man Promotional Web Systems, retro hacker terminals, and Neo-Brutalist graphic design movements.

---

<div align="center">
  <b>CODEX ITER — BUILD • CREATE • GROW</b><br>
  <sub>© 2026 CODEX ITER. All rights reserved.</sub>
</div>

