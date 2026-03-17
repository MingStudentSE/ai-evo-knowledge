# Style Presets Reference

Curated visual styles for Frontend Slides. Each preset is inspired by real design references - no generic "AI slop" aesthetics. **Abstract shapes only - no illustrations.**

**Viewport CSS:** For mandatory base styles, see [viewport-base.css](viewport-base.css). Include in every presentation.

---

## Dark Themes

### 1. Bold Signal

**Vibe:** Confident, bold, modern, high-impact

**Layout:** Colored card on dark gradient. Number top-left, navigation top-right, title bottom-left.

**Typography:**
- Display: `Archivo Black` (900)
- Body: `Space Grotesk` (400/500)

**Colors:**
```css
:root {
    --bg-primary: #1a1a1a;
    --bg-gradient: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 50%, #1a1a1a 100%);
    --card-bg: #FF5722;
    --text-primary: #ffffff;
    --text-on-card: #1a1a1a;
}
```

**Signature Elements:**
- Bold colored card as focal point
- Large section numbers
- Navigation breadcrumbs
- Grid-based layout

### 2. Electric Studio

**Vibe:** Bold, clean, professional, high contrast

**Layout:** Split panel-white top, blue bottom. Brand marks in corners.

**Typography:**
- Display: `Manrope` (800)
- Body: `Manrope` (400/500)

**Colors:**
```css
:root {
    --bg-dark: #0a0a0a;
    --bg-white: #ffffff;
    --accent-blue: #4361ee;
    --text-dark: #0a0a0a;
    --text-light: #ffffff;
}
```

### 3. Creative Voltage

**Vibe:** Bold, creative, energetic, retro-modern

**Layout:** Split panels-electric blue left, dark right. Script accents.

**Typography:**
- Display: `Syne` (700/800)
- Mono: `Space Mono` (400/700)

**Colors:**
```css
:root {
    --bg-primary: #0066ff;
    --bg-dark: #1a1a2e;
    --accent-neon: #d4ff00;
    --text-light: #ffffff;
}
```

### 4. Dark Botanical

**Vibe:** Elegant, sophisticated, artistic, premium

**Typography:**
- Display: `Cormorant` (400/600)
- Body: `IBM Plex Sans` (300/400)

**Colors:**
```css
:root {
    --bg-primary: #0f0f0f;
    --text-primary: #e8e4df;
    --text-secondary: #9a9590;
    --accent-warm: #d4a574;
    --accent-pink: #e8b4b8;
    --accent-gold: #c9b896;
}
```

---

## Light Themes

### 5. Notebook Tabs

**Vibe:** Editorial, organized, elegant, tactile

**Typography:**
- Display: `Bodoni Moda` (400/700)
- Body: `DM Sans` (400/500)

### 6. Pastel Geometry

**Vibe:** Friendly, organized, modern, approachable

**Typography:**
- Display: `Plus Jakarta Sans` (700/800)
- Body: `Plus Jakarta Sans` (400/500)

### 7. Split Pastel

**Vibe:** Playful, modern, friendly, creative

**Typography:**
- Display: `Outfit` (700/800)
- Body: `Outfit` (400/500)

### 8. Vintage Editorial

**Vibe:** Witty, confident, editorial, personality-driven

**Typography:**
- Display: `Fraunces` (700/900)
- Body: `Work Sans` (400/500)

---

## Specialty Themes

### 9. Neon Cyber

**Vibe:** Futuristic, techy, confident

**Typography:** `Clash Display` + `Satoshi`

**Colors:** Deep navy, cyan accent, magenta

### 10. Terminal Green

**Vibe:** Developer-focused, hacker aesthetic

**Typography:** `JetBrains Mono`

### 11. Swiss Modern

**Vibe:** Clean, precise, Bauhaus-inspired

**Typography:** `Archivo` + `Nunito`

### 12. Paper & Ink

**Vibe:** Editorial, literary, thoughtful

**Typography:** `Cormorant Garamond` + `Source Serif 4`

---

## DO NOT USE

- Inter, Roboto, Arial, or system fonts as the display face
- generic purple gradients on white
- cookie-cutter hero layouts
- realistic illustrations for decoration

## CSS Gotchas

Never negate CSS functions directly. Use `calc(-1 * ...)` instead.
