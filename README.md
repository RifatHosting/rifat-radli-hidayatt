# RIFAT RADLI HIDAYAT — Portfolio

> Student by day. Programmer always.

Portfolio website untuk **Rifat Radli Hidayat** — seorang student-programmer dari Bandung, Indonesia yang membangun web dengan obsesi terhadap setiap piksel dan milidetik.

---

## Tech Stack

| Kategori | Teknologi |
|----------|-----------|
| 3D Rendering | Three.js r128 — Custom GLSL ShaderMaterial |
| Animation | GSAP 3.12 + ScrollTrigger + CustomEase |
| Smooth Scroll | Lenis 1.1 |
| Text Splitting | Splitting.js |
| Typography | Bunny Fonts (Plus Jakarta Sans, Instrument Serif, DM Sans, DM Mono) |
| CSS Architecture | Vanilla CSS — `@layer` cascade system |
| Build Tools | **Tidak ada.** Zero build step. |

---

## Fitur Utama

### Three.js Hero Scene
- **IcosahedronGeometry(2.2, 64)** dengan custom vertex + fragment shader
- Vertex shader: 3D simplex noise displacement, hover-reactive amplitude
- Fragment shader: Iridescent color cycling (indigo → vermilion → gold → teal), fresnel rim lighting, translucent alpha
- Wireframe overlay via `EdgesGeometry` + `LineSegments`, rotasi lebih cepat dari mesh utama
- Fake bloom post-process: canvas kedua di 0.25x resolusi, CSS `blur(24px)` + `mix-blend-mode: screen`
- Mouse-tracking camera, elastic scale-in saat load, scroll-linked shrink/fade

### Preloader
- Slot-machine digit animation — 3 span terpisah dengan kecepatan berbeda
- Vermilion progress line 0% → 100%
- Blinking "LOADING..." dots
- Clip-path upward wipe exit

### Work Section
- 4 project dalam stacked full-width strips (bukan card grid biasa)
- Setiap project punya **animated Canvas2D** yang unik:
  - **NEXUS DASHBOARD** — Flowing bezier data lines + pulsing dots
  - **ECHO SOCIAL** — 150 particle network dengan connection lines
  - **PIXEL STUDIO** — 24x24 pixel grid yang terisi real-time
  - **ORBIT API** — Concentric sonar ripples dengan data labels
- Hover: background berubah, canvas speed 2x, info & visual "breathe apart"
- IntersectionObserver: canvas berhenti render saat tidak terlihat

### About Section
- Typographic essay style — 3 kolom editorial
- Quote dengan scroll-scrubbed word-by-word color transition
- SVG timeline yang draw-on-scroll dengan elastic node pop
- Scattered skill pills dengan random rotation, fly-in dari arah acak

### Lab Section
- Bento grid (4 kolom × 3 baris) dengan 0px border-radius
- Cycling text dengan clip-path wipe animation
- Commit heatmap 16×8 dengan tooltip on hover
- Live code snippet typing effect
- Now playing dengan animated equalizer bars
- Counter animasi 12,405+

### Contact Section
- Cinematic full-viewport CTA
- Mixed solid + outline typography
- Magnetic button (280×80px, elastic return)
- Functional copy-to-clipboard dengan toast notification
- Form dengan floating labels + fill-from-left submit button

### Micro-Interactions
- Custom cursor dengan contextual labels (VIEW, COPY, SEND)
- Vermilion follower dengan lerp 0.08
- Page transitions — vermilion bar wipe on anchor navigation
- Custom scrollbar (4px, vermilion thumb)
- Magnetic hover pada nav links (±6px)
- Noise texture overlay (SVG feTurbulence, 0.025 opacity)

---

## Color System

```
--void:       #060608   /* Background utama */
--ink:        #0D0D10   /* Surface/card layer */
--smoke:      #1A1A22   /* Borders, dividers */
--paper:      #F2EDE4   /* Primary text — warm, bukan putih */
--dust:       #6A6A7A   /* Muted/secondary text */
--vermilion:  #FF3D00   /* Hero accent — electric & dangerous */
--gold:       #C9A84C   /* Rare secondary accent */
```

---

## Typography

| Role | Font | Usage |
|------|------|-------|
| Display | Plus Jakarta Sans 500/700 | Headlines, tracking -0.04em |
| Serif | Instrument Serif 400i | Pull quotes, editorial accents |
| Body | DM Sans 300/400 | Paragraphs, descriptions |
| Mono | DM Mono 300/400 | Labels, counters, code, technical data |

Semua font size menggunakan `clamp()` — fluid, tanpa breakpoint jumps.

---

## CSS Architecture

```
@layer reset → tokens → base → layout → components → animations → utilities
```

- Semua warna via CSS custom properties
- Semua ukuran via `clamp()` atau custom properties
- Border radius: hanya `0px` atau `9999px`
- Spacing: 8pt base system
- Zero Tailwind, Zero Bootstrap, Zero jQuery

---

## Performance

- Three.js: `setPixelRatio(Math.min(dpr, 2))`, debounced resize, `dispose()` on pagehide
- Canvas animations: `IntersectionObserver` — stop render saat tidak terlihat
- GSAP: `ScrollTrigger.normalizeScroll(true)` untuk mobile
- `will-change` hanya saat animasi aktif
- `prefers-reduced-motion` dihormati — semua animasi dimatikan
- Custom cursor hidden pada touch devices
- Mobile: Three.js → gradient fallback, horizontal scroll → vertical

---

## Accessibility

- Skip to main content link
- `:focus-visible` ring (2px solid vermilion, offset 4px)
- ARIA labels pada icon-only buttons
- `prefers-reduced-motion` support
- Semantic HTML structure

---

## Cara Menjalankan

1. Download `index.html`
2. Buka di Chrome atau Firefox
3. Selesai. Tidak perlu build step, server, atau dependency apapun.

> Semua library dimuat via CDN. Semua visual dihasilkan secara prosedural — zero external images.

---

## Struktur File

```
index.html
├── <head>
│   ├── CDN links (Bunny Fonts, Three.js, GSAP, Lenis, Splitting.js)
│   └── <style> — Semua CSS via @layer
├── <body>
│   ├── Noise overlay
│   ├── Custom cursor elements
│   ├── Preloader
│   ├── Navigation
│   ├── <main>
│   │   ├── #hero — Three.js scene + typography
│   │   ├── .marquee-strip
│   │   ├── #work — 4 project strips dengan canvas animations
│   │   ├── #about — Editorial 3-column layout
│   │   ├── #lab — Bento grid
│   │   └── #contact — CTA + form
│   ├── Footer
│   └── <script> — Semua JS, modular per section
└── </html>
```

---

## Lisensi

Kode ini dibuat untuk portfolio personal Rifat Radli Hidayat. Desain dan implementasi adalah hasil craft yang intentional — setiap piksel, setiap animasi, setiap interaksi ada karena alasan.

**Built with obsession.**
