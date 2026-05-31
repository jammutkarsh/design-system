---
name: utc-ds
description: |
  Terminal-inspired design system for Utkarsh Chourasia's portfolio and project websites.
  Use this skill whenever building or modifying any web page, component, or layout that should
  follow the utc-ds design language. This ensures visual consistency across all projects.
---

# utc-ds Design System

A dark-first, terminal-inspired design system built with pure CSS. Colors derived from Utkarsh's personal ZSH terminal theme. Inspired by PlanetScale and charmbracelet/glow.

## When to Use

Apply this skill whenever you are:
- Building a new page or component for any of Utkarsh's websites
- Writing HTML/CSS that should match the portfolio aesthetic
- Creating blog posts, documentation, or project pages
- Modifying existing UI to align with the design system

## Core Principles

1. **Dark-first** — `#0a0a0a` background, light text. Light mode via `[data-theme="light"]`
2. **Content-first** — Typography is the hero. No flashy animations
3. **Terminal-native** — Monospace accents, pipe `|` separators, dashed borders, bracket `[tags]`, `$ ` prompts, `~/` breadcrumbs
4. **Zero-animation** — CSS `transition` on hover only. No JS animations, no layout shifts
5. **Token-driven** — All values via `var(--ds-*)`. Never use raw colors, sizes, or fonts
6. **ZSH-themed colors** — Primary orange (#ff5f00), secondary light blue (#afd7ff), purple (#af00d7), pink (#ffd7ff) from Utkarsh's terminal theme

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
  --ds-primary: #ff5f00;   /* Orange (ANSI 202) — change this */
  --ds-secondary: #afd7ff; /* Light Blue (ANSI 153) — change this */
}
```

All hover, muted, active, and subtle variants auto-derive via `color-mix()`.

## Design Tokens Reference

### Colors (from ZSH terminal theme)
| Token | Value | ZSH Origin |
|---|---|---|
| `--ds-primary` | `#ff5f00` | ANSI 202 — directory background |
| `--ds-secondary` | `#afd7ff` | ANSI 153 — success prompt (ƛ) |
| `--ds-purple` | `#af00d7` | ANSI 128 — username background |
| `--ds-pink` | `#ffd7ff` | ANSI 225 — connector text |
| `--ds-danger` | `#ff0000` | ANSI 196 — error prompt |
| `--ds-success` | `#22a652` | Green — git clean status |
| `--ds-warning` | `#f5a623` | Yellow — git dirty status |
| `--ds-bg-primary` | `#0a0a0a` | Terminal background |
| `--ds-bg-secondary` | `#111111` | Card/surface background |
| `--ds-text-primary` | `#e8e8e8` | Main text |
| `--ds-text-secondary` | `#888888` | Muted text |
| `--ds-text-tertiary` | `#555555` | Decorative text (pipes, dashes) |
| `--ds-border` | `#222222` | Default borders |
| `--ds-border-strong` | `#333333` | Dashed borders, strong separators |

### Typography
| Token | Value |
|---|---|
| `--ds-font-sans` | Inter (headings, body) |
| `--ds-font-mono` | JetBrains Mono (code, terminal, decorative) |
| `--ds-text-base` | 1rem (16px) |
| `--ds-leading` | 1.7 (body line-height) |
| `--ds-leading-tight` | 1.2 (headings) |

### Heading Style
- h1: `text-5xl`, weight `300`, letter-spacing `-0.04em` (large, light)
- h2: `text-3xl`, weight `300`, dashed bottom border
- h3-h5: `text-2xl` to `text-lg`, weight `medium`
- h6: `text-sm`, mono, uppercase, letter-spaced
- **No `#` prefix** — clean headings without markdown markers

### Spacing
4px grid: `--ds-space-1` (4px) through `--ds-space-24` (96px).

### Layout
| Token | Value |
|---|---|
| `--ds-max-width` | 72rem (1152px) |
| `--ds-content-width` | 48rem (768px) — prose width |

## Component Quick Reference

### Navigation (with `~/` breadcrumb)
```html
<nav class="nav">
  <div class="nav-inner container">
    <a href="/" class="nav-brand"><span class="nav-prefix">~/</span>site-name</a>
    <div class="nav-links">
      <a href="/about" class="nav-link">About</a>
      <span class="nav-sep">|</span>
      <a href="/blog" class="nav-link">Blog</a>
    </div>
  </div>
</nav>
```

### Breadcrumb (terminal-style path)
```html
<div class="breadcrumb">
  <span class="bc-home">~</span><span class="bc-sep">/</span>
  <a href="#">projects</a><span class="bc-sep">/</span>
  <span class="bc-current">utc-ds</span>
</div>
```

### Buttons
```html
<button class="btn">Default</button>
<button class="btn btn-primary">Primary</button>
<button class="btn btn-ghost">Ghost</button>
<a href="#" class="btn btn-primary arrow">Get Started</a>
```

### Cards (3 variants)
```html
<!-- Standard card with footer -->
<div class="card">
  <div class="card-title">Title</div>
  <div class="card-body">Description</div>
  <div class="card-footer">
    <span class="badge badge-success">running</span>
    <a href="#" class="btn btn-ghost btn-sm arrow">View</a>
  </div>
</div>

<!-- Accent card -->
<div class="card card-accent">...</div>

<!-- Image card (with pixel-art placeholder) -->
<div class="card card-image">
  <div class="card-pixel-placeholder">🖥️</div>
  <div class="card-content">
    <div class="card-title">Title</div>
    <div class="card-body">Description</div>
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

### Terminal Block (with copy-on-hover)
```html
<div class="terminal">
  <div class="terminal-header">
    <span class="terminal-dot"></span>
    <span class="terminal-dot"></span>
    <span class="terminal-dot"></span>
    <span class="terminal-title">~/project</span>
  </div>
  <div class="terminal-body">
    <div class="terminal-cmd">
      <div class="prompt">echo "hello"</div>
      <div class="output">hello</div>
      <button class="copy-btn" data-copy="echo &quot;hello&quot;">copy</button>
    </div>
  </div>
</div>
```
JS needed for copy functionality:
```js
document.querySelectorAll('.copy-btn').forEach(btn => {
  btn.addEventListener('click', async () => {
    await navigator.clipboard.writeText(btn.getAttribute('data-copy'));
    btn.textContent = 'copied!';
    btn.classList.add('copied');
    setTimeout(() => { btn.textContent = 'copy'; btn.classList.remove('copied'); }, 2000);
  });
});
```

### Blockquotes (with citation)
```html
<blockquote>
  The best tools get out of your way.
  <cite>— someone on Hacker News, probably</cite>
</blockquote>
```

### Horizontal Rules
```html
<hr>                          <!-- dashed (default) -->
<hr class="dot-fill">          <!-- dotted pattern -->
<hr class="ascii-hr">          <!-- box-drawing characters -->
<div class="hr-label">label</div>  <!-- labeled divider -->
```

### Colored Code Blocks
```html
<pre><code><span class="token-comment">// comment</span>
<span class="token-keyword">func</span> <span class="token-function">main</span>() {
    x := <span class="token-string">"hello"</span>
    n := <span class="token-number">42</span>
}</code></pre>
```

Token classes: `token-keyword`, `token-function`, `token-string`, `token-comment`, `token-type`, `token-number`, `token-operator`, `token-variable`, `token-builtin`

### Blog Post Metadata
```html
<div class="card">
  <div class="card-title"><a href="#">Post Title</a></div>
  <div class="meta">
    <a href="#">Author</a>
    <a href="#" class="handle">[@handle]</a>
    <span class="sep">|</span>
    <time>Date</time>
    <span class="sep">|</span>
    <span class="badge badge-info">Category</span>
  </div>
  <div class="card-body">Description text.</div>
  <div style="margin-top: var(--ds-space-3);">
    <a href="#" class="btn btn-ghost btn-sm arrow">Read more</a>
  </div>
</div>
```
**Note**: "Read more" goes on its own line, not inline with description.

### Footer
```html
<footer class="footer container">
  <div class="footer-grid">
    <div class="footer-col">
      <h3>Section</h3>
      <a href="#">Link 1</a>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2026 Name. Built with utc-ds.</p>
  </div>
</footer>
```

## Do NOT

- Use raw color values — always use `var(--ds-*)`
- Add JavaScript animations or heavy transitions
- Use rounded corners larger than `--ds-radius-lg` (8px)
- Use shadows (borders define surfaces in this system)
- Use gradient backgrounds
- Import external icon libraries — use inline SVGs or emoji
- Use `font-weight: bold` — use `var(--ds-weight-medium)` or `var(--ds-weight-semibold)`
- Add `#` prefix markers to headings (removed from the design)
- Put "Read more" links inline with blog descriptions (use a new line)
