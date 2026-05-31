# utc-ds

A terminal-inspired design system for developer portfolios and project websites.

**Dark-first. Content-first. Zero-animation. Pure CSS.**

Colors from [Utkarsh's ZSH terminal theme](uc_theme.zsh). Inspired by [PlanetScale](https://planetscale.com/) and [charmbracelet/glow](https://github.com/charmbracelet/glow).

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

- **Classless base styles** — All markdown-to-HTML elements (h1-h6, p, a, ul, ol, blockquote, code, table, hr, etc.) styled automatically
- **Derived color system** — Set `--ds-primary` and `--ds-secondary`, everything else auto-derives via `color-mix()`
- **ZSH-themed palette** — Orange (#ff5f00), light blue (#afd7ff), purple (#af00d7) from a real terminal theme
- **Dark + light modes** — Dark by default, light via `data-theme="light"` attribute
- **Terminal-inspired components** — Pipe-separated nav with `~/` breadcrumb, dashed-border cards, bracket-wrapped `[badges]`, terminal blocks with copy-on-hover, ASCII diagrams
- **Colored code blocks** — Syntax token classes for keywords, functions, strings, comments, etc.
- **Zero JavaScript** — Pure CSS, no build step (tiny inline JS for theme toggle, hamburger, and copy buttons)
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
  --ds-primary: #ff5f00;   /* Your brand color (default: ANSI 202 orange) */
  --ds-secondary: #afd7ff; /* Your secondary color (default: ANSI 153 light blue) */
}
```

Toggle light mode:

```html
<html data-theme="light">
```

## Components

| Component | Class | Description |
|---|---|---|
| Navigation | `.nav` + `.nav-brand` | Pipe-separated sticky nav with `~/` prefix |
| Breadcrumb | `.breadcrumb` | Terminal-style path: `~/projects/name` |
| Buttons | `.btn`, `.btn-primary`, `.btn-ghost` | Monospace terminal-style buttons |
| Cards | `.card`, `.card-accent`, `.card-image` | 3 variants with title/body/footer areas |
| Badges | `.badge .badge-*` | Bracket-wrapped `[tags]` in 6 colors |
| Callouts | `.callout .callout-*` | GitHub-style alerts (note, tip, warning, caution) |
| Terminal | `.terminal` | Faux terminal with copy-on-hover |
| Code tokens | `.token-*` | Syntax coloring for code blocks |
| ASCII | `.ascii` | Box-drawing diagram container |
| HR variants | `hr`, `.dot-fill`, `.ascii-hr`, `.hr-label` | 4 divider styles including labeled |
| Footer | `.footer` | Multi-column dashed-border footer |
| Metadata | `.meta` | Author / date / category line |

## Fonts

- **Inter** — Headings (light weight h1-h2, medium h3-h5) and body text
- **JetBrains Mono** — Code, terminal, badges, buttons, breadcrumbs

Both loaded via Google Fonts in `utc-ds.css`.

## Browser Support

Requires browsers supporting `color-mix()` in oklch (Baseline 2023):
- Chrome 111+
- Firefox 113+
- Safari 16.2+

## License

MIT
