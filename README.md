# utc-ds

A terminal-inspired design system for developer portfolios and project websites.

**Dark-first. Content-first. Zero-animation. Pure CSS.**

Inspired by [PlanetScale](https://planetscale.com/) and [charmbracelet/glow](https://github.com/charmbracelet/glow).

## Quick Start

Add a single stylesheet to your project:

```html
<link rel="stylesheet" href="path/to/utc-ds.css">
```

Or import in CSS:

```css
@import 'path/to/utc-ds.css';
```

Open `index.html` in your browser to see every element and component in action.

## Features

- **Classless base styles** — All markdown-to-HTML elements (h1-h6, p, a, ul, ol, blockquote, code, table, hr, etc.) are styled automatically
- **Derived color system** — Set `--ds-primary` and `--ds-secondary`, everything else auto-derives via `color-mix()`
- **Dark + light modes** — Dark by default, light via `data-theme="light"` attribute
- **Terminal-inspired components** — Pipe-separated nav, dashed-border cards, bracket-wrapped badges, terminal blocks, ASCII diagrams
- **Zero JavaScript** — Pure CSS, no build step (tiny inline JS only for theme toggle and hamburger menu in the showcase)
- **Responsive** — Mobile-first with hamburger menu at 768px breakpoint

## File Structure

```
design-system/
├── utc-ds.css          ← Main entry point (imports everything)
├── tokens.css          ← Design tokens (colors, fonts, spacing)
├── base.css            ← Semantic HTML element styles
├── components.css      ← Component classes
├── index.html          ← Live showcase page
├── SKILL.md            ← AI model reference
└── README.md           ← This file
```

## Theming

Change two variables to re-theme everything:

```css
:root {
  --ds-primary: #f15817;   /* Your brand color */
  --ds-secondary: #47b7f8; /* Your secondary color */
}
```

Toggle light mode:

```html
<html data-theme="light">
```

## Components

| Component | Class | Description |
|---|---|---|
| Navigation | `.nav` | Pipe-separated sticky nav with hamburger |
| Buttons | `.btn`, `.btn-primary`, `.btn-ghost` | Monospace terminal-style buttons |
| Cards | `.card`, `.card-grid` | Dashed-border containers |
| Badges | `.badge .badge-*` | Bracket-wrapped `[tags]` |
| Callouts | `.callout .callout-*` | GitHub-style alerts (note, tip, warning, caution) |
| Terminal | `.terminal` | Faux terminal window with pixel dots |
| ASCII | `.ascii` | Box-drawing diagram container |
| Footer | `.footer` | Multi-column dashed-border footer |
| Metadata | `.meta` | Author / date / category line |

## Fonts

- **Inter** — Headings and body text
- **JetBrains Mono** — Code, terminal, badges, buttons, decorative elements

Both loaded via Google Fonts in `utc-ds.css`.

## Browser Support

Requires browsers supporting `color-mix()` in oklch (Baseline 2023):
- Chrome 111+
- Firefox 113+
- Safari 16.2+

## License

MIT
