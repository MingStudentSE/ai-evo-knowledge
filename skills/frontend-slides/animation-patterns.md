# Animation Patterns Reference

Use this reference when generating presentations. Match animations to the intended feeling.

## Effect-to-Feeling Guide

| Feeling | Animations | Visual Cues |
|---------|-----------|-------------|
| Dramatic / Cinematic | Slow fade-ins, large scale transitions, parallax | Dark backgrounds, spotlight effects |
| Techy / Futuristic | Neon glow, glitch text, grid reveals | Particle systems, monospace accents |
| Playful / Friendly | Bouncy easing, floating motion | Rounded corners, pastel colors |
| Professional / Corporate | Subtle fast animations | Precise spacing, restrained palette |
| Calm / Minimal | Gentle fades, very subtle motion | High whitespace, muted palette |
| Editorial / Magazine | Staggered text reveals | Strong type hierarchy |

## Entrance Animations

```css
.reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s var(--ease-out-expo),
                transform 0.6s var(--ease-out-expo);
}
.visible .reveal {
    opacity: 1;
    transform: translateY(0);
}

.reveal-scale {
    opacity: 0;
    transform: scale(0.9);
    transition: opacity 0.6s, transform 0.6s var(--ease-out-expo);
}

.reveal-left {
    opacity: 0;
    transform: translateX(-50px);
    transition: opacity 0.6s, transform 0.6s var(--ease-out-expo);
}
```

## Interactive Effects

```javascript
class TiltEffect {
    constructor(element) {
        this.element = element;
        this.element.style.transformStyle = 'preserve-3d';
        this.element.style.perspective = '1000px';
    }
}
```

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Fonts not loading | Check font URL and font family names |
| Animations not triggering | Verify Intersection Observer and `.visible` class |
| Scroll snap not working | Check `scroll-snap-type` and per-slide alignment |
| Mobile issues | Reduce heavy effects and simplify interactions |
