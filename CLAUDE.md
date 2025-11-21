# CLAUDE.md

This file provides guidance to Claude Code when working with this A2M Concepts showcase website.

## 🎯 Project Overview

**Single-page showcase website for A2M Concepts** - Carrelage and renovation company (BTP sector) based in France.

**Goal:** Present the company, its services, and generate quote requests through a professional and performant website.

### Tech Stack
- **Framework:** Astro v5.15.8 (SSG - Static Site Generation)
- **Styling:** Tailwind CSS ONLY (no custom CSS)
- **Language:** TypeScript (strict mode)
- **Deployment:** Vercel
- **Template:** Minimal Astro starter

---

## 🔄 Development Workflow

**This project follows the EPCT methodology** documented in `/commands/epct.md`.

⚠️ **ALWAYS start by reading `/commands/epct.md` before any feature work.**

Quick reference:
- **E**xplore → Gather context (codebase analysis, research)
- **P**lan → Design solution and get approval
- **C**ode → Implement approved plan
- **T**est → Validate with existing tools

---

## 🎨 Design Inspiration

Sites to draw inspiration from:

- **[URL 1]** - Hero section and overall layout
- **[URL 2]** - Portfolio/gallery presentation
- **[URL 3]** - Clean style and contact form

**Target style:** Modern, professional, trustworthy (BTP sector), expertise-driven, clear call-to-action.

---

## 📱 MOBILE FIRST - CRITICAL CONSTRAINT

**⚠️ ABSOLUTE RULE: Development MUST start with mobile design.**

### Why?
BTP workers and clients primarily browse from their phones on construction sites or while traveling.

### Strict Rules

#### Minimum Sizes
- ✅ **Buttons/touch targets:** 44x44px minimum
- ✅ **Font size:** 16px minimum (prevents iOS auto-zoom)
- ✅ **Spacing between clickable elements:** 8px minimum

#### Mobile Design Principles
- ✅ Simple, intuitive navigation (natural scroll)
- ✅ **NO hover states** (no mouse on mobile)
- ✅ Forms easy to fill with fingers
- ✅ Optimized images (WebP, lazy loading)
- ✅ Load time < 2 seconds

#### Tailwind Breakpoints
```css
default:     < 768px   (mobile - BASE STYLES)
sm:          640px+    (large mobile)
md:          768px+    (tablet)
lg:          1024px+   (desktop)
xl:          1280px+   (large desktop)
```

**Development Order:**
1. Mobile design (< 768px) - ALWAYS FIRST
2. Tablet adaptation (768px - 1024px)
3. Desktop adaptation (> 1024px)

---

## 🎨 Design System

### Color Palette
```css
/* Brand Colors - A2M Concepts */
--primary: #c0955e;       /* Gold/Bronze (buttons, links, accents) */
--secondary: #35353d;     /* Anthracite Grey (buttons secondary, headings) */
--light: #f8fafc;         /* Light background */
--white: #ffffff;         /* White background */

/* Tailwind Equivalents */
primary:   gold-600       /* #c0955e - Main brand color */
secondary: dark-800       /* #35353d - Secondary brand color */
light:     slate-50       /* Neutral light backgrounds */

/* Extended Palette */
gold-50:   #faf7f2        /* Very light gold - subtle backgrounds */
gold-100:  #f5ece0        /* Light gold - icon backgrounds */
gold-600:  #c0955e        /* PRIMARY - Buttons, links, accents */
gold-700:  #ab7f4a        /* Hover states for buttons */

dark-800:  #35353d        /* SECONDARY - Headings, dark buttons */
dark-900:  #2a2a31        /* Footer, dark overlays */
dark-600:  #55555d        /* Muted text */

slate-50:  #f8fafc        /* Light section backgrounds */
slate-600: #475569        /* Body text */
slate-700: #334155        /* Form labels */
```

### Typography
```css
/* Font Sizes (minimum 16px for body) */
H1: text-4xl md:text-5xl lg:text-6xl (bold)
H2: text-3xl md:text-4xl lg:text-5xl (bold)
H3: text-2xl md:text-3xl (semibold)
Body: text-base (16px) md:text-lg
Small: text-sm (14px minimum)

/* Line Heights */
Headings: leading-tight (1.25)
Body: leading-relaxed (1.625)
```

### Spacing
```css
/* Section Spacing */
section: py-12 md:py-16 lg:py-20

/* Container Padding */
container: px-4 md:px-6 lg:px-8
max-width: max-w-7xl
```

---

## 📋 Site Structure (Sections)

**Single page with smooth scroll and anchor link navigation.**

1. **Hero** - Headline, CTA "Get Free Quote", background image
2. **Services** - Service list with icons/photos
3. **About** - Company presentation, experience, values
4. **Portfolio** - Photo gallery of completed projects
5. **Coverage Area** - Map or list of cities/regions served
6. **Testimonials** (optional) - Customer reviews
7. **Contact** - Contact form + phone/email + direct call button (mobile)
8. **Footer** - Legal links, social media, copyright

---

## 📂 Project Structure
```
a2m-vitrine/
├── public/               # Static assets
│   ├── images/          # Project photos, logo
│   ├── favicon.svg
│   └── robots.txt
├── src/
│   ├── components/      # Reusable Astro components
│   │   ├── Hero.astro
│   │   ├── Services.astro
│   │   ├── About.astro
│   │   ├── Portfolio.astro
│   │   ├── Contact.astro
│   │   └── Footer.astro
│   ├── layouts/
│   │   └── Layout.astro # Main layout (head, nav, footer)
│   └── pages/
│       └── index.astro  # Single page (all sections)
├── commands/
│   └── epct.md         # EPCT workflow methodology
├── astro.config.mjs    # Astro + Tailwind config
├── tailwind.config.mjs # Custom theme config
├── tsconfig.json       # TypeScript strict mode
├── claude.md           # This file
└── package.json
```

---

## 💻 Development Commands
```bash
# Install dependencies
npm install

# Start dev server (localhost:4321)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Add Tailwind CSS integration
npm run astro add tailwind

# Type check
npm run astro check
```

---

## ✅ Validation Checklist

### Mobile (< 768px)
- [ ] Perfect design on mobile (iPhone & Android)
- [ ] Buttons minimum 44x44px
- [ ] Font minimum 16px
- [ ] Sufficient touch spacing
- [ ] Smooth, natural scroll
- [ ] Easy-to-fill forms

### Performance
- [ ] Optimized images (WebP, lazy loading)
- [ ] Lighthouse Performance > 90
- [ ] Load time < 2s
- [ ] No unnecessary JavaScript

### Accessibility
- [ ] Alt text on all images
- [ ] Text/background contrast WCAG AA (4.5:1)
- [ ] Keyboard navigation
- [ ] Form input labels
- [ ] Visible focus on interactive elements

### SEO
- [ ] Meta title and description
- [ ] Hierarchical H1/H2/H3 tags
- [ ] Schema.org LocalBusiness
- [ ] Open Graph tags
- [ ] sitemap.xml and robots.txt

### Responsive
- [ ] Mobile (< 768px) perfect
- [ ] Tablet (768px - 1024px) adapted
- [ ] Desktop (> 1024px) optimized
- [ ] No horizontal scroll
- [ ] Responsive images

---

## 🏗️ Architecture Notes

### Routing
- **Single page** site: everything in `src/pages/index.astro`
- Sections accessible via anchor links (`#services`, `#contact`)
- Smooth scroll with Tailwind `scroll-smooth`

### Components
- Astro components (`.astro`) in `src/components/`
- Each section = 1 component for modularity
- TypeScript props for configuration
- No client-side JavaScript (except contact form if needed)

### Styling
- **Tailwind CSS ONLY** (no custom CSS)
- Theme config in `tailwind.config.mjs`
- Responsive with prefixes (`sm:`, `md:`, `lg:`)

### Static Assets
- Images in `public/images/`
- WebP format, compressed
- Lazy loading with `loading="lazy"`
- Astro Image component for automatic optimization

---

## 🚀 Deployment

### Vercel (recommended)
```bash
npm i -g vercel
vercel --prod
```

Site is generated in `./dist/` and can be deployed to any static host.

---

## 🎯 Development Principles for Claude Code

1. **Always start mobile** - Mobile design before desktop
2. **Section by section** - Incremental development
3. **Atomic commits** - 1 commit = 1 feature/section
4. **Continuous testing** - Validate on mobile at each step
5. **Tailwind only** - No custom CSS
6. **Simplicity** - Avoid over-engineering (it's a showcase site)
7. **Performance** - Lightweight, fast, optimized

### Effective Prompts
```
✅ Good prompt:
"Claude, create Hero.astro component mobile-first with:
- Catchy headline for BTP company
- CTA button 'Get Free Quote'
- Background image
- Tailwind only"

❌ Bad prompt:
"Make the hero"
```

## 🎨 Design Inspiration

**Site de référence principal :**
- **https://daumont-carrelage.fr/** - Style professionnel, simple et efficace
  - Layout épuré et moderne
  - Navigation claire
  - Section services bien présentée
  - Formulaire de contact accessible
  - Mise en avant de l'expertise (20+ ans)
  - Slogan accrocheur ("Carrelons l'avenir")

**Éléments à reproduire :**
- Structure single-page avec scroll fluide
- Hero avec slogan fort
- Présentation de l'expertise (transmission, exigence, durabilité)
- Section services/réalisations
- Call-to-action clair (devis gratuit)
- Formulaire de contact simple

**Adaptations pour A2M Concepts :**
- Utiliser l'identité visuelle A2M (couleurs définies dans Design System)
- Adapter le contenu à A2M (slogan, services, zone géographique)
- Optimisation mobile-first stricte

---

**Version:** 1.0.0  
**Last Updated:** January 2025  
**Maintained by:** Youssef (A2M Concepts)