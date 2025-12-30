# DPS Labs Portfolio UI Specification
**Version:** 1.0  
**Date:** December 30, 2025  
**Designer:** Agentic UI Studio  
**Aesthetic:** Dark, Bold, Premium (ŌRBIT-inspired)  
**Tech:** Astro + Tailwind CSS

---

## 1. Design Tokens

### 1.1 Color Palette
Implementation: Tailwind `theme.extend.colors`

| Token Name | Hex Value | Tailwind Class | Usage |
|:---|:---|:---|:---|
| **Background** | `#0A0A0A` | `bg-charcoal-900` | Main page background |
| **Surface** | `#121212` | `bg-charcoal-800` | Cards, Sections, Modals |
| **Surface Highlight**| `#1E1E1E` | `bg-charcoal-700` | Hover states, Inputs |
| **Primary** | `#FFFFFF` | `text-white` | Headings, Primary Text |
| **Secondary** | `#888888` | `text-gray-400` | Body text, Meta info |
| **Accent (Gold)** | `#D4A574` | `text-gold` / `bg-gold` | CTAs, Links, Highlights |
| **Accent Dim** | `#A37E58` | `border-gold-dim` | Borders, subtle accents |
| **Success** | `#10B981` | `text-emerald-500` | Status indicators |

### 1.2 Typography
**Font Family:**
- **Headings:** `Space Grotesk` (Google Fonts) – Tech/Futuristic, bold personality.
- **Body:** `Inter` (Google Fonts) – Clean, highly legible, timeless.
- **Monospace:** `JetBrains Mono` – For code snippets/terminal vibes.

**Type Scale (Mobile / Desktop):**

| Element | Size (px) | Line Height | Tracking | Tailwind |
|:---|:---|:---|:---|:---|
| **Display (Hero)** | 48 / 80 | 1.1 | -0.02em | `text-5xl md:text-7xl font-bold` |
| **H1 (Page)** | 36 / 48 | 1.2 | -0.01em | `text-4xl md:text-5xl font-bold` |
| **H2 (Section)** | 30 / 36 | 1.25 | -0.01em | `text-3xl md:text-4xl font-semibold` |
| **H3 (Card Title)**| 20 / 24 | 1.3 | Normal | `text-xl md:text-2xl font-medium` |
| **Body Large** | 18 / 20 | 1.6 | Normal | `text-lg` |
| **Body Default** | 16 / 16 | 1.6 | Normal | `text-base` |
| **Small/Label** | 14 / 14 | 1.4 | 0.05em | `text-sm uppercase tracking-wider` |
| **Tiny** | 12 / 12 | 1.4 | Normal | `text-xs` |

### 1.3 Spacing System
Based on 4px grid.

- **Section Padding:** `py-20 md:py-32` (80px / 128px)
- **Component Gap:** `gap-6 md:gap-8` (24px / 32px)
- **Card Padding:** `p-6 md:p-8` (24px / 32px)
- **Element Spacing:** `mb-4` (16px)

### 1.4 Borders & Radius
- **Radius:** `rounded-xl` (12px) for cards, `rounded-full` for buttons/pills.
- **Borders:** 1px solid `border-white/10` (subtle) or `border-gold/20` (accented).

---

## 2. Layout Grid

- **Container:** `max-w-7xl` centered.
- **Padding:** `px-4 md:px-8` horizontal padding.
- **Columns:**
  - **Mobile:** 1 column (Stack).
  - **Tablet:** 6 columns.
  - **Desktop:** 12 columns.

---

## 3. Component Specifications

### 3.1 Buttons
**Primary Button (CTA)**
- Background: `#D4A574` (Gold)
- Text: `#0A0A0A` (Dark)
- Font: `Inter`, Semibold, Uppercase tracking wide.
- Hover: Lighten 5%, Scale 1.02.
- Class: `bg-gold text-charcoal-900 px-8 py-3 rounded-full font-semibold uppercase tracking-widest hover:bg-gold-light transition-all`

**Secondary Button (Outline)**
- Background: Transparent
- Border: 1px `#D4A574`
- Text: `#D4A574`
- Hover: Bg Gold/10.
- Class: `border border-gold text-gold px-8 py-3 rounded-full uppercase tracking-widest hover:bg-gold/10 transition-all`

### 3.2 Project Cards (Featured Work)
*Layout:*
- **Mobile:** Stacked (Image top, content bottom).
- **Desktop:** Split 50/50 or 60/40 zigzag.

*Visuals:*
- **Background:** `bg-charcoal-800`
- **Border:** `border border-white/5`
- **Image Area:** Subtle gradient overlay (Black alpha) to make text pop if text overlays, or distinct container.
- **Hover:** `group-hover:border-gold/30 transition-colors`. Image subtle zoom.

### 3.3 Tech Badge (Pill)
- Background: `bg-white/5`
- Text: `text-gray-300`
- Border: `border border-white/10`
- Size: `text-xs`
- Radius: `rounded-full`
- Class: `px-3 py-1 bg-white/5 border border-white/10 rounded-full text-xs text-gray-300`

---

## 4. Section Details

### 4.1 Hero Section ("The Hook")
- **Layout:** Centered or Left-aligned (Left preferred for "Studio" vibe).
- **Content:**
  - Label: `ENGINEER & MUSICIAN` (Gold, Small Caps)
  - H1: "I ship products." (White, Display Size)
  - Sub: "Full-stack engineering meets creative composition. Building at the intersection of logic and art." (Gray, Body Large)
  - CTA: "View Work" + "Contact"
- **Visual:** Subtle noise texture background + radial gradient glow `#D4A574` at very low opacity (5%) in corner.

### 4.2 Featured Work (The "Meat")
- **Header:** "Selected Work"
- **List:** Vertical stack of large cards.
- **Card Content:**
  - Project Title (H3)
  - One-line hook (e.g., "Music Theory for everyone")
  - Stat Highlight (e.g., "21k+ Users" in Gold)
  - Tech Stack Badges
  - Links: Live Demo (Icon), GitHub (Icon)
  - **Visual Treatment:** App screenshots tilted with 3D perspective or flat clean mockup on hover.

### 4.3 Creative Work (The "Soul")
- **Layout:** Masonry or Grid (2x2 or 3x3).
- **Content:** Square aspect ratio cards (Album Art style).
- **Overlay:** Play button icon on hover.
- **Info:** Title + Release Year below image. Minimal.

### 4.4 About Section
- **Layout:** 2-Column (Text Left, Image Right).
- **Image:** Headshot with **Duotone effect** or Grayscale + Gold overlay on hover.
- **Shape:** Image clipped in `rounded-2xl` or an abstract organic shape if using SVG masks.

---

## 5. Animation & Transitions
*Keep it performant (CSS transforms).*

- **Scroll Reveal:** Elements slide up 20px + Fade In (`opacity-0 translate-y-4` -> `opacity-100 translate-y-0`).
- **Hover States:**
  - Cards: Lift `translate-y-[-4px]`, Border glow.
  - Links: Underline expands from center.
- **Micro-interactions:** Buttons press down slightly `active:scale-95`.

---

## 6. Implementation Checklist (Astro)

1.  [ ] **Setup Tailwind Config:** Add colors (`charcoal`, `gold`) and fonts (`Space Grotesk`, `Inter`).
2.  [ ] **Create Layout:** `Layout.astro` with `<main>` and `max-w-7xl`.
3.  [ ] **Build Base Components:** `Button.astro`, `Section.astro`, `Card.astro`.
4.  [ ] **Hero Implementation:** Ensure H1 uses `text-balance` for nice wrapping.
5.  [ ] **Responsive Check:** Test stacking order on Mobile vs Desktop.
