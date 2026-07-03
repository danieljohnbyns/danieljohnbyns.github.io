# Design Document — Daniel John Baynosa

> **Role:** System Architect | AI Agent Engineer | Software Developer
> **Location:** Rodriguez, Rizal, Philippines
> **Website:** https://danieljohnbyns.online

---

## 1. Brand Identity

### Core Values
- **Clarity through architecture** — systems should be well-structured, documented, and scalable.
- **Practical innovation** — leverage AI and modern tooling to solve real problems, not chase hype.
- **Managed Open Source** — build transparently, share intentionally, sustain responsibly.
- **Cross-platform fluency** — web, desktop, mobile, and IoT are not silos.

### Personality
- Analytical but approachable
- Self-taught rigor meets academic foundation
- "I tend to overcomplicate things" — but delivers

### Tagline Concepts
- *Architecting systems. Engineering intelligence.*
- *From architecture to deployment — end to end.*

---

## 2. Color Palette

A professional, tech-forward palette with warmth from Filipino heritage.

| Token | Hex | Usage |
|-------|-----|-------|
| `--primary` | `#1a1a2e` | Deep navy — backgrounds, headers |
| `--secondary` | `#e94560` | Vibrant coral — accents, CTAs, highlights |
| `--accent` | `#0f3460` | Midnight blue — secondary surfaces |
| `--surface` | `#16213e` | Dark card/panel backgrounds |
| `--text-primary` | `#eaeaea` | Primary text on dark |
| `--text-secondary` | `#a0a0b0` | Muted text, metadata |
| `--success` | `#2ecc71` | Positive indicators |
| `--warning` | `#f39c12` | Warning / attention |
| `--glow` | `#e94560` | Subtle glow effects on interactive elements |

### Why this palette
The deep navy-to-coral scheme reflects:
- Professionalism and depth (navy)
- Energy and passion for code (coral)
- Modern developer tooling aesthetic (dark mode first)

---

## 3. Typography

| Element | Font | Weight | Fallback |
|---------|------|--------|----------|
| Headings | `JetBrains Mono` | 700, 600 | `monospace` |
| Body | `Inter` | 400, 500 | `sans-serif` |
| Code / Tech | `JetBrains Mono` | 400, 500 | `monospace` |
| Labels / Captions | `Inter` | 500 | `sans-serif` |

### Scale

```
--text-xs:   0.75rem   (12px)
--text-sm:   0.875rem  (14px)
--text-base: 1rem      (16px)
--text-lg:   1.125rem  (18px)
--text-xl:   1.25rem   (20px)
--text-2xl:  1.5rem    (24px)
--text-3xl:  1.875rem  (30px)
--text-4xl:  2.25rem   (36px)
--text-5xl:  3rem      (48px)
```

### Rationale
- **JetBrains Mono** for headings and code — aligns with developer identity, pairs technical credibility with readability.
- **Inter** for body — highly legible at all sizes, designed for screens.

---

## 4. Layout & Spacing

### Grid
- 12-column grid with 24px gutter
- Max container width: `1200px`
- Breakpoints: `640px` / `768px` / `1024px` / `1280px`

### Spacing Scale

```
--space-1:  4px
--space-2:  8px
--space-3:  12px
--space-4:  16px
--space-5:  24px
--space-6:  32px
--space-8:  48px
--space-10: 64px
--space-12: 80px
```

### Page Structure
- Full-bleed hero section with animated terminal / architectural diagram
- Consistent section padding: `--space-12` top and bottom
- Cards with subtle border `1px solid rgba(255,255,255,0.06)` and rounded corners `12px`

---

## 5. Design Philosophy

### Dark Mode First
The portfolio defaults to dark mode. This matches developer tooling conventions and the chosen color palette. A light mode toggle may be added later but is **not** a priority.

### Minimal but Expressive
- Clean layouts with generous whitespace.
- Use of subtle glow and gradient effects (not flat, not overdone).
- Interactive code snippets and terminal emulators embedded in project showcases.

### Motion
- Subtle fade-in-up animations on scroll (`IntersectionObserver`).
- Hover states: scale(1.02) + increased glow on cards.
- Page transitions: fade + slight slide (`50ms` ease-out).
- Terminal cursor blink for hero typewriter effect.

### Accessibility
- All color combinations pass WCAG AA contrast ratios.
- Focus indicators visible on all interactive elements.
- `prefers-reduced-motion` respected.

---

## 6. Content Architecture

### Pages / Sections

| Section | Purpose |
|---------|---------|
| **Hero** | Typewriter intro, role, CTA to projects |
| **About** | Professional summary + personal philosophy |
| **Experience** | Timeline of work history (TaoCrowd, Freelance, EnticeAds) |
| **Projects** | Featured work — cyra, iOSAS, RapCap, tapang-sarap, snipboard, System-Architecture-Course |
| **Skills** | Tag cloud / matrix of technologies |
| **Education** | Colegio de Montalban — BSIT 2022–2026 |
| **Contact** | Form + links to GitHub, LinkedIn, email |

### Project Card Schema

```json
{
  "title": "cyra",
  "subtitle": "Can You Really Assist?",
  "description": "Real-time AI voice assistant powered by Google Gemini",
  "tech": ["TypeScript", "Gemini AI", "Node.js"],
  "links": {
    "github": "https://github.com/cyra-ai/cyra",
    "demo": null
  },
  "featured": true,
  "year": 2025
}
```

---

## 7. Technology Stack

| Layer | Technology |
|-------|-----------|
| Framework | React (Vite) or Astro |
| Language | TypeScript |
| Styling | CSS Modules / Tailwind CSS |
| Animation | Framer Motion / CSS animations |
| Deployment | Vercel or Cloudflare Pages |
| Analytics | Plausible or Umami (self-hosted) |
| Forms | Formspree or custom API endpoint |
| Fonts | JetBrains Mono + Inter (Google Fonts) |

### Why these choices
- **Astro** would be ideal for a content-heavy portfolio (zero JS by default, islands architecture).
- **React + Vite** if more interactivity is needed (e.g., embedded terminal, live demos).
- **Tailwind CSS** aligns with rapid prototyping and the design token system above.
- **Vercel/Cloudflare** — free tier, global CDN, excellent DX.

---

## 8. File Structure (Proposed)

```
/
├── public/
│   ├── favicon.svg
│   ├── og-image.png
│   └── resume/
│       └── daniel-john-baynosa-resume.pdf
├── src/
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Header.astro
│   │   │   ├── Footer.astro
│   │   │   └── Layout.astro
│   │   ├── sections/
│   │   │   ├── Hero.astro
│   │   │   ├── About.astro
│   │   │   ├── Experience.astro
│   │   │   ├── Projects.astro
│   │   │   ├── Skills.astro
│   │   │   ├── Education.astro
│   │   │   └── Contact.astro
│   │   └── ui/
│   │       ├── Button.astro
│   │       ├── Card.astro
│   │       ├── Tag.astro
│   │       ├── Terminal.astro
│   │       └── Timeline.astro
│   ├── data/
│   │   ├── projects.json
│   │   ├── experience.json
│   │   └── skills.json
│   ├── styles/
│   │   ├── tokens.css
│   │   ├── base.css
│   │   └── utilities.css
│   ├── pages/
│   │   └── index.astro
│   └── utils/
│       └── animations.ts
├── Design.md
├── package.json
├── tsconfig.json
├── astro.config.mjs
└── tailwind.config.mjs
```

---

## 9. Featured Projects Detail

### cyra — AI Voice Assistant
- **Stack:** TypeScript, Google Gemini AI, Node.js
- **Highlights:** Real-time voice conversation, file system tool execution, MIT-licensed
- **Why it matters:** Demonstrates AI integration, async architecture, and open-source contribution

### iOSAS Suite (7 repos)
- **Stack:** Node.js/Express, React Native (Expo), Tauri + React, Supabase
- **Components:** API backend, mobile app, administrative-staff desktop, superadmin desktop, website
- **Highlights:** 56 releases on admin-staff, full student affairs lifecycle management
- **Why it matters:** System architecture at scale — multi-app ecosystem with shared API

### RapCap — Rapid Capture Photobooth
- **Stack:** Electron, JavaScript, Webpack
- **Highlights:** Image template import, frame adjustment, photo capture, 3 GitHub stars
- **Why it matters:** Desktop application engineering, real-time media processing

### tapang-sarap — IoT Temperature Monitor
- **Stack:** React Native (Expo), Node.js/Express, hardware integration
- **Highlights:** Real-time temperature monitoring, threshold notifications
- **Why it matters:** Full-stack + IoT, hardware-software bridge

### snipboard — npm Package
- **Stack:** TypeScript
- **Highlights:** Published on npm (`@danieljohnbyns/snipboard`), automated CI/CD tests
- **Why it matters:** Package publishing discipline, API design

### System-Architecture-Course
- **Stack:** Documentation / Markdown
- **Highlights:** Self-built curriculum for system architecture proficiency
- **Why it matters:** Teaching and knowledge sharing, depth in architectural thinking

---

## 10. Performance Targets

| Metric | Target |
|--------|--------|
| Lighthouse Performance | ≥ 95 |
| Lighthouse Accessibility | 100 |
| First Contentful Paint (FCP) | < 1.0s |
| Largest Contentful Paint (LCP) | < 1.5s |
| Cumulative Layout Shift (CLS) | < 0.05 |
| Total Bundle Size (JS) | < 100KB |
| Total Page Weight | < 500KB |

---

## 11. Future Considerations

- **Blog / writing section** — publish system architecture deep-dives
- **Interactive terminal component** — showcase cyra-like interactions in-browser
- **Dark/light mode toggle** — based on `prefers-color-scheme`
- **Internationalization** — English + Filipino (Tagalog)
- **RSS feed** for blog content
- **Guestbook / comments** — lightweight, serverless
- **Particle / network graph background** — subtle architectural diagram aesthetic

---

*Design document v1.0 — reflecting Daniel John Baynosa's professional identity as a System Architect, AI Agent Engineer, and Full-Stack Developer. Built from resume, GitHub profile, and LinkedIn data.*
