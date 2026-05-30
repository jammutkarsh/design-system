---
name: utc-ds
description: |
  Terminal-inspired design system for Utkarsh Chourasia's portfolio and project websites.
  Use this skill whenever building or modifying any web page, component, or layout that should
  follow the utc-ds design language. This ensures visual consistency across all projects.
---

# utc-ds Design System

A dark-first, terminal-inspired design system built with pure CSS. Inspired by PlanetScale and charmbracelet/glow.

## When to Use

Apply this skill whenever you are:
- Building a new page or component for any of Utkarsh's websites
- Writing HTML/CSS that should match the portfolio aesthetic
- Creating blog posts, documentation, or project pages
- Modifying existing UI to align with the design system

## Core Principles

1. **Dark-first** — `#0a0a0a` background, light text. Light mode via `[data-theme="light"]`
2. **Content-first** — Typography is the hero. No flashy animations
3. **Terminal-native** — Monospace accents, pipe `|` separators, dashed borders, bracket `[tags]`, `$ ` prompts
4. **Zero-animation** — CSS `transition` on hover only. No JS animations, no layout shifts
5. **Token-driven** — All values via `var(--ds-*)`. Never use raw colors, sizes, or fonts

## File Structure

```
design-system/
├── utc-ds.css      ← Import this one file (loads everything)
├── tokens.css      ← Design tokens (colors, fonts, spacing)
├── base.css        ← Semantic HTML element styles (classless)
├── components.css  ← Component classes (.btn, .card, .nav, etc.)
└── index.html      ← Live showcase
```

## How to Use

```html
<link rel="stylesheet" href="path/to/utc-ds.css">
```

## Theming

Only two variables control the entire color system:

```css
:root {
  --ds-primary: #f15817;   /* Orange — change this */
  --ds-secondary: #47b7f8; /* Blue — change this */
}
```

All hover, muted, active, and subtle variants auto-derive via `color-mix()`.

## Design Tokens Reference

### Colors
| Token | Purpose |
|---|---|
| `--ds-primary` | Brand accent (links, buttons, highlights) |
| `--ds-secondary` | Secondary accent |
| `--ds-bg-primary` | Page background (#0a0a0a dark, #fafafa light) |
| `--ds-bg-secondary` | Card/surface background |
| `--ds-bg-code` | Code block background |
| `--ds-text-primary` | Main text |
| `--ds-text-secondary` | Muted text (metadata, captions) |
| `--ds-text-tertiary` | Decorative text (pipes, dashes) |
| `--ds-border` | Default borders |
| `--ds-border-strong` | Dashed borders, strong separators |
| `--ds-success/info/warning/danger/purple` | Semantic colors |

### Typography
| Token | Value |
|---|---|
| `--ds-font-sans` | Inter (headings, body) |
| `--ds-font-mono` | JetBrains Mono (code, terminal, decorative) |
| `--ds-text-base` | 1rem (16px) |
| `--ds-text-sm` | 0.875rem (14px) |
| `--ds-leading` | 1.7 (body line-height) |
| `--ds-leading-tight` | 1.2 (headings) |

### Spacing
4px grid: `--ds-space-1` (4px) through `--ds-space-24` (96px).

### Layout
| Token | Value |
|---|---|
| `--ds-max-width` | 72rem (1152px) |
| `--ds-content-width` | 48rem (768px) — prose width |

## Component Quick Reference

### Navigation
```html
<nav class="nav">
  <div class="nav-inner container">
    <a href="/" class="nav-brand">site-name</a>
    <div class="nav-links">
      <a href="/about" class="nav-link">About</a>
      <span class="nav-sep">|</span>
      <a href="/blog" class="nav-link">Blog</a>
    </div>
  </div>
</nav>
```

### Buttons
```html
<button class="btn">Default</button>
<button class="btn btn-primary">Primary</button>
<button class="btn btn-ghost">Ghost</button>
<a href="#" class="btn btn-primary arrow">Get Started</a>
```

### Cards
```html
<div class="card-grid">
  <div class="card">
    <h4>Title</h4>
    <p>Description</p>
    <span class="badge badge-info">Category</span>
  </div>
</div>
```

### Badges (bracket-wrapped)
```html
<span class="badge badge-primary">Primary</span>
<span class="badge badge-success">Success</span>
<span class="badge badge-info">Info</span>
<span class="badge badge-warning">Warning</span>
<span class="badge badge-danger">Danger</span>
<span class="badge badge-purple">Purple</span>
```

### Callouts
```html
<div class="callout callout-note">
  <div class="callout-title">Note</div>
  <p>Content here.</p>
</div>
<!-- Variants: callout-note, callout-tip, callout-warning, callout-caution -->
```

### Terminal Block
```html
<div class="terminal">
  <div class="terminal-header">
    <span class="terminal-dot"></span>
    <span class="terminal-dot"></span>
    <span class="terminal-dot"></span>
    <span class="terminal-title">~/project</span>
  </div>
  <div class="terminal-body">
    <div class="prompt">echo "hello"</div>
    <div class="output">hello</div>
  </div>
</div>
```

### ASCII Diagram
```html
<pre class="ascii">
┌──────────┐    ┌──────────┐
│ <span class="highlight">Service</span>  │───▶│ <span class="highlight">Database</span> │
└──────────┘    └──────────┘
</pre>
```

### Metadata Line
```html
<div class="meta">
  <a href="#">Author Name</a>
  <a href="#" class="handle">[@handle]</a>
  <span class="sep">|</span>
  <time>May 30, 2026</time>
</div>
```

### Horizontal Rules
```html
<hr>                    <!-- dashed (default) -->
<hr class="dot-fill">   <!-- dotted pattern -->
<hr class="ascii-hr">   <!-- box-drawing characters -->
```

### Footer
```html
<footer class="footer container">
  <div class="footer-grid">
    <div class="footer-col">
      <h3>Section</h3>
      <a href="#">Link 1</a>
      <a href="#">Link 2</a>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2026 Name. Built with utc-ds.</p>
  </div>
</footer>
```

## HTML Patterns

### Heading Prefixes
Add `data-heading-prefix` to any parent to get markdown-style `#` prefixes:
```html
<article data-heading-prefix>
  <h1>Shows as: # Heading</h1>
  <h2>Shows as: ## Heading</h2>
</article>
```

### Theme Toggle
```html
<html data-theme="light"> <!-- light mode -->
<html>                     <!-- dark mode (default) -->
```

## Do NOT

- Use raw color values — always use `var(--ds-*)`
- Add JavaScript animations or heavy transitions
- Use rounded corners larger than `--ds-radius-lg` (8px)
- Use shadows (borders define surfaces in this system)
- Use gradient backgrounds
- Import external icon libraries — use inline SVGs or text symbols
- Use `font-weight: bold` — use `var(--ds-weight-semibold)` or `var(--ds-weight-bold)`
