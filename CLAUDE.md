# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

**Eurotur Portal** — a corporate intranet portal for Eurotur S.A., a travel agency. It provides employees access to tools like ticketing, the corporate directory, Travel Designers, tax documents, USD exchange rates, product catalog, and operational weather data.

## Running the project

No build step required. Open `index.html` directly in a browser:

```
start index.html        # Windows
open index.html         # macOS
```

There is no package manager, bundler, or local dev server. Tailwind CSS is loaded from CDN.

## Architecture

The entire application lives in a single file: [index.html](index.html).

**Layout structure:**
- `SideNavBar` — fixed left sidebar (hidden on mobile, visible `md:flex`), contains logo, navigation links, and a Quick Ticket CTA button
- `TopNavBar` — fixed top bar with brand name, notification/apps buttons, and user avatar
- `main` — scrollable content area with a bento grid of action cards and a weather widget section
- `footer` — full-width bottom bar with copyright and links

## Design system

The Tailwind config is embedded inline in a `<script id="tailwind-config">` block. It defines:

- **Color tokens** — Material Design 3 semantic palette (`primary`, `secondary`, `tertiary`, `surface`, `on-*`, `*-container`, etc.). Never use raw Tailwind colors like `blue-500`; always use the semantic tokens.
- **Typography scale** — Custom font sizes (`display-lg`, `headline-lg/md/sm`, `body-lg/md/sm`, `label-md`) with paired `fontFamily` entries. Use both the size and family class together, e.g. `text-headline-sm font-headline-sm`.
- **Spacing** — `base`, `container-max`, `margin-mobile`, `margin-desktop`, `gutter` tokens.

**Custom CSS class:** `.glass-card` — glassmorphism card with blur background, white border, and hover lift effect. Applied to all action cards.

**Dark mode:** uses `class` strategy (`dark:` prefix). The `<html>` tag has `class="light"`.

**Icons:** Google Material Symbols font. Use `<span class="material-symbols-outlined">icon_name</span>`. Icon fill is controlled via `font-variation-settings` or the inline `style` attribute (`'FILL' 1` for filled).
