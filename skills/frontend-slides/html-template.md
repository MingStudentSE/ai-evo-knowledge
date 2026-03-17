# HTML Presentation Template

Reference architecture for generating slide presentations. Every presentation follows this structure.

## Base HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Presentation Title</title>
    <style>
        :root {
            --bg-primary: #0a0f1c;
            --text-primary: #ffffff;
            --accent: #00ffcc;
            --font-display: 'Clash Display', sans-serif;
            --font-body: 'Satoshi', sans-serif;
            --title-size: clamp(2rem, 6vw, 5rem);
            --body-size: clamp(0.75rem, 1.2vw, 1rem);
            --slide-padding: clamp(1.5rem, 4vw, 4rem);
            --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);
            --duration-normal: 0.6s;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        /* Paste viewport-base.css here */

        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity var(--duration-normal) var(--ease-out-expo),
                        transform var(--duration-normal) var(--ease-out-expo);
        }

        .slide.visible .reveal {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <div class="progress-bar"></div>
    <nav class="nav-dots"></nav>

    <section class="slide title-slide">
        <h1 class="reveal">Presentation Title</h1>
        <p class="reveal">Subtitle</p>
    </section>

    <section class="slide">
        <div class="slide-content">
            <h2 class="reveal">Slide Title</h2>
            <p class="reveal">Content</p>
        </div>
    </section>

    <script>
        class SlidePresentation {
            constructor() {
                this.slides = document.querySelectorAll('.slide');
                this.currentSlide = 0;
                this.setupIntersectionObserver();
                this.setupKeyboardNav();
                this.setupTouchNav();
            }
        }

        new SlidePresentation();
    </script>
</body>
</html>
```

## Required JavaScript Features

Every presentation should include:

1. Keyboard navigation
2. Touch/swipe support
3. Progress bar updates
4. Navigation dots
5. Intersection Observer for reveal effects

## Inline Editing

If inline editing is enabled by the user:
- use a JS-controlled toggle button
- support local save behavior
- avoid CSS-only sibling-selector hover tricks for the edit button

## Image Placement

- use direct file paths, not base64, for local presentations
- keep image height within `min(50vh, 400px)`
- avoid repeating the same image across multiple slides unless it is a logo

## Accessibility

- semantic sections and nav
- keyboard navigation must work
- include reduced-motion support
