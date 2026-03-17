---
name: frontend-slides
description: Create stunning, animation-rich HTML presentations from scratch or by converting PowerPoint files. Use when the user wants to build a presentation, convert a PPT/PPTX to web, or create slides for a talk/pitch. Helps non-designers discover their aesthetic through visual exploration rather than abstract choices.
---

# Frontend Slides

Create zero-dependency, animation-rich HTML presentations that run entirely in the browser.

## Core Principles

1. **Zero Dependencies** - Single HTML files with inline CSS/JS. No npm, no build tools.
2. **Show, Don't Tell** - Generate visual previews, not abstract choices. People discover what they want by seeing it.
3. **Distinctive Design** - No generic "AI slop." Every presentation must feel custom-crafted.
4. **Viewport Fitting (NON-NEGOTIABLE)** - Every slide MUST fit exactly within 100vh. No scrolling within slides, ever. Content overflows? Split into multiple slides.

## Design Aesthetics

You tend to converge toward generic, "on distribution" outputs. In frontend design, this creates what users call the "AI slop" aesthetic. Avoid this: make creative, distinctive frontends that surprise and delight.

Focus on:
- Typography: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics.
- Color & Theme: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes. Draw from IDE themes and cultural aesthetics for inspiration.
- Motion: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions.
- Backgrounds: Create atmosphere and depth rather than defaulting to solid colors. Layer CSS gradients, use geometric patterns, or add contextual effects that match the overall aesthetic.

Avoid generic AI-generated aesthetics:
- Overused font families (Inter, Roboto, Arial, system fonts)
- Cliched color schemes (particularly purple gradients on white backgrounds)
- Predictable layouts and component patterns
- Cookie-cutter design that lacks context-specific character

Interpret creatively and make unexpected choices that feel genuinely designed for the context. Vary between light and dark themes, different fonts, different aesthetics. You still tend to converge on common choices (Space Grotesk, for example) across generations. Avoid this: it is critical that you think outside the box.

## Viewport Fitting Rules

These invariants apply to EVERY slide in EVERY presentation:

- Every `.slide` must have `height: 100vh; height: 100dvh; overflow: hidden;`
- ALL font sizes and spacing must use `clamp(min, preferred, max)` - never fixed px/rem
- Content containers need `max-height` constraints
- Images: `max-height: min(50vh, 400px)`
- Breakpoints required for heights: 700px, 600px, 500px
- Include `prefers-reduced-motion` support
- Never negate CSS functions directly (`-clamp()`, `-min()`, `-max()` are silently ignored) - use `calc(-1 * clamp(...))` instead

**When generating, read `viewport-base.css` and include its full contents in every presentation.**

### Content Density Limits Per Slide

| Slide Type | Maximum Content |
|------------|-----------------|
| Title slide | 1 heading + 1 subtitle + optional tagline |
| Content slide | 1 heading + 4-6 bullet points OR 1 heading + 2 paragraphs |
| Feature grid | 1 heading + 6 cards maximum (2x3 or 3x2) |
| Code slide | 1 heading + 8-10 lines of code |
| Quote slide | 1 quote (max 3 lines) + attribution |
| Image slide | 1 heading + 1 image (max 60vh height) |

**Content exceeds limits? Split into multiple slides. Never cram, never scroll.**

---

## Phase 0: Detect Mode

Determine what the user wants:

- **Mode A: New Presentation** - Create from scratch. Go to Phase 1.
- **Mode B: PPT Conversion** - Convert a `.pptx` file. Go to Phase 4.
- **Mode C: Enhancement** - Improve an existing HTML presentation. Read it, understand it, enhance. **Follow Mode C modification rules below.**

### Mode C: Modification Rules

When enhancing existing presentations, viewport fitting is the biggest risk:

1. **Before adding content:** Count existing elements, check against density limits
2. **Adding images:** Must have `max-height: min(50vh, 400px)`. If slide already has max content, split into two slides
3. **Adding text:** Max 4-6 bullets per slide. Exceeds limits? Split into continuation slides
4. **After ANY modification, verify:** `.slide` has `overflow: hidden`, new elements use `clamp()`, images have viewport-relative max-height, content fits at 1280x720
5. **Proactively reorganize:** If modifications will cause overflow, automatically split content and inform the user. Don't wait to be asked

**When adding images to existing slides:** Move image to new slide or reduce other content first. Never add images without checking if existing content already fills the viewport.

---

## Phase 1: Content Discovery (New Presentations)

Ask for:
- Purpose: Pitch deck / Teaching-Tutorial / Conference talk / Internal presentation
- Length: Short 5-10 / Medium 10-20 / Long 20+
- Content readiness: All content ready / Rough notes / Topic only
- Inline editing: Yes / No

If the user has source content, ask them to share it.

### Step 1.2: Image Evaluation

If the user provides image assets:
1. Scan image files.
2. View and evaluate each image.
3. Mark each as usable or not usable, with reason.
4. Let image choices affect slide outline from the start.
5. Confirm the outline and image mapping before generating.

If a usable logo exists, include it in style previews so the user sees their own brand in context.

---

## Phase 2: Style Discovery

This is the "show, don't tell" phase. Most people cannot describe visual preference precisely in words.

### Step 2.0: Style Path

Ask whether they want:
- Show me options
- I know what I want

If they choose direct selection, use [STYLE_PRESETS.md](STYLE_PRESETS.md).

### Step 2.1: Mood Selection

Ask what feeling the audience should have:
- Impressed/Confident
- Excited/Energized
- Calm/Focused
- Inspired/Moved

### Step 2.2: Generate 3 Style Previews

Generate three distinct single-slide previews based on mood and presets in [STYLE_PRESETS.md](STYLE_PRESETS.md).

Suggested mapping:

| Mood | Suggested Presets |
|------|-------------------|
| Impressed/Confident | Bold Signal, Electric Studio, Dark Botanical |
| Excited/Energized | Creative Voltage, Neon Cyber, Split Pastel |
| Calm/Focused | Notebook Tabs, Paper & Ink, Swiss Modern |
| Inspired/Moved | Dark Botanical, Vintage Editorial, Pastel Geometry |

Save previews to `.claude-design/slide-previews/` as `style-a.html`, `style-b.html`, and `style-c.html`, then open them for the user.

### Step 2.3: User Picks

Ask the user to choose Style A, B, C, or mix elements.

---

## Phase 3: Generate Presentation

Generate the final presentation using text and selected style. If images were provided, incorporate them into the outline already decided in Phase 1.

**Before generating, read:**
- [html-template.md](html-template.md)
- [viewport-base.css](viewport-base.css)
- [animation-patterns.md](animation-patterns.md)

**Requirements:**
- Single self-contained HTML file
- Inline CSS and JS
- Include the full contents of `viewport-base.css`
- Use Google Fonts or Fontshare, never default system fonts
- Add clear section comments

---

## Phase 4: PPT Conversion

When converting PowerPoint files:

1. Run `python scripts/extract-pptx.py <input.pptx> <output_dir>`
2. Confirm extracted slide titles, content, images, and notes with the user
3. Do style discovery
4. Generate HTML while preserving slide order, text, assets, and notes

If needed, install dependency with `pip install python-pptx`.

---

## Phase 5: Delivery

1. Clean up preview files
2. Open the generated HTML presentation
3. Summarize:
   - file location
   - chosen style
   - slide count
   - navigation controls
   - how to customize colors, fonts, and animations
   - how inline editing works if enabled

---

## Supporting Files

| File | Purpose | When to Read |
|------|---------|-------------|
| [STYLE_PRESETS.md](STYLE_PRESETS.md) | Curated visual presets | Style selection |
| [viewport-base.css](viewport-base.css) | Mandatory viewport-safe CSS | HTML generation |
| [html-template.md](html-template.md) | HTML structure and JS expectations | HTML generation |
| [animation-patterns.md](animation-patterns.md) | Animation guidance | HTML generation |
| [scripts/extract-pptx.py](scripts/extract-pptx.py) | PPT content extraction | PPT conversion |
