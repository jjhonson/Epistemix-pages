---
name: prism-design-system
description: Apply the Prism design system when building UI components, demos, dashboards, or any Epistemix data interface. Use whenever creating cards, tables, charts, maps, input forms, or any data-dense analytical UI that should follow the Prism visual language.
---

# Prism Design System — Epistemix

You are building UI that follows the Prism design system. Prism is a card-based dashboard application for data-dense analytical interfaces. Apply these rules to every component you create.

## Core Principles

1. **Glanceability** — users scan, not read. Layout, color, and hierarchy serve scanability.
2. **Restraint with color** — bright colors are used sparingly, only for meaningful data highlighting. Default to grays.
3. **Light mode first** — support both modes via tokens, but optimize for light.
4. **Clean and minimal** — when in doubt on design decisions, reference Notion's aesthetic: generous whitespace, subtle shadows, no decorative flourishes.

---

## Color System

### Design Tokens

All colors are defined as tokens for centralized light/dark mode control.

| Role | Value | Usage |
|------|-------|-------|
| Surface | `#ffffff` | Card backgrounds, modals |
| Surface Muted | `#f8f9fa` | Table headers, grouped row backgrounds |
| Page Background | `#f0f1f3` | App/page background |
| Text Primary | `#1a1a1a` | Body text, values |
| Text Secondary | `#6b7280` | Labels, subtitles |
| Text Muted | `#9ca3af` | Placeholders, disabled states |
| Border | `#e5e7eb` | Card borders, dividers |
| Border Strong | `#d1d5db` | Emphasized dividers |

### Epistemix Brand Colors (Interactive Elements Only)

These are used ONLY for interactive states — active tabs, selected controls, CTA buttons, focus rings. Never use brand blue for decorative purposes or data labels.

| Role | Value | Usage |
|------|-------|-------|
| Brand Blue | `#4056F4` | Buttons, active tabs, selected states, sliders |
| Brand Navy | `#1C3080` | Dark card backgrounds, primary header text |
| Page Header | `#0E1B4F` | App header background |

### Semantic Highlight Colors (Data Only)

Used exclusively for highlighting data values in cells and charts. Never for UI decoration.

| Role | Value | Cell fill (15% opacity) |
|------|-------|------------------------|
| Highlight Green | `#6FD93F` | `rgba(111, 217, 63, 0.15)` |
| Highlight Yellow | `#F5C542` | `rgba(245, 197, 66, 0.15)` |
| Highlight Red | `#EF5350` | `rgba(239, 83, 80, 0.15)` |
| Highlight Blue | `#4056F4` | Linked/active area indicators |

### Categorical Palette (Charts, Segments, Programs)

Desaturated by default. Use 12% opacity variants for background fills.

| Slot | Color | 12% Opacity Variant |
|------|-------|---------------------|
| 0 | `#5B8FD4` | `rgba(91, 143, 212, 0.12)` |
| 1 | `#4DB6AC` | `rgba(77, 182, 172, 0.12)` |
| 2 | `#D4915B` | `rgba(212, 145, 91, 0.12)` |
| 3 | `#9575CD` | `rgba(149, 117, 205, 0.12)` |
| 4 | `#81C784` | `rgba(129, 199, 132, 0.12)` |
| 5 | `#E57373` | `rgba(229, 115, 115, 0.12)` |

### Table Cell Color Highlighting

Color does NOT fill the entire cell. It is a rounded rectangle inset within the cell:
- Corner radius: **3px**
- Inset from cell edges: **2px**
- Fill: **linear gradient left-to-right** — highlight color at 15% opacity on left, fading to 0% on right

### Spotlight Highlighting (Metric Cards)

For large metric values, use a subtle **elliptical radial gradient with blur** behind the number — not a background rectangle. The glow should feel like a soft light source, not a block of color. Implement as a `::before` pseudo-element with `filter: blur()` and a radial gradient.

### Chart Colors

- Default to **gray tones** (`#374151` primary, `#9CA3AF` secondary)
- Add color only when semantically meaningful
- Stacked charts: use the categorical palette, stepped not continuous, favor gray
- Highlight **few** elements, not all

---

## Typography

### Font Stack
```
-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif
```

### Scale

| Token | Size | Weight | Usage |
|-------|------|--------|-------|
| xs | 11px | 500 | Tiny labels, badges |
| sm | 12px | 400/600 | Column headers, secondary text |
| base | 14px | 400 | Body text, table cells |
| md | 15px | 600 | Card titles |
| lg | 18px | 600 | Section headings |
| xl | 22px | 700 | Page titles |
| metric | 36px | 300–700 | Featured numbers in cards |
| metric-hero | 48–64px | 300 | Headline metrics in demos (TAM, key output numbers) |

Note: `metric` (36px) is appropriate for metric cards within the Prism dashboard. `metric-hero` (48–64px, weight 300) is for headline numbers in demo outputs where the number should dominate the screen — e.g., the TAM figure on a population tab.

### Weights
- 300: Light — large metric numbers, hero numerals
- 400: Normal — body text
- 500: Medium — labels, secondary headings
- 600: Semibold — card titles, column headers
- 700: Bold — page titles, featured metrics

### Text Alignment

| Context | Alignment |
|---------|-----------|
| Data Table cells and headers | Left (including numbers) |
| Overview Table cells | Center (horizontal and vertical) |
| Overview Table row titles | Right |
| Metric Card values | Center |
| Metric Cluster column headers | Center (both axes) |

### Text Truncation
- Table cells: clip overflow (no ellipsis)
- Dropdowns and labels: **middle truncation** — show beginning and end, truncate middle ("Anthem Bl...ss PPO")
- Full text visible on hover tooltip

### Number Formatting
- Percentages: `93%`
- Integers: `1,356` (commas)
- Abbreviated: `50K`, `$500M`, `$1.2B`
- Use `font-variant-numeric: tabular-nums` for aligned number columns

---

## Spacing

| Token | Value | Usage |
|-------|-------|-------|
| space-1 | 4px | Tight gaps, insets |
| space-2 | 8px | Inline spacing |
| space-3 | 12px | Component gaps |
| space-4 | 16px | Section padding |
| space-5 | 20px | Card internal padding |
| space-6 | 24px | Page-level padding |
| space-8 | 32px | Large section gaps |
| space-10 | 40px | Hero spacing |

---

## Border Radii

| Token | Value | Usage |
|-------|-------|-------|
| radius-sm | 3px | Bars, cell highlights, small elements |
| radius-md | 6px | Buttons, inputs, form elements |
| radius-lg | 10px | Cluster table outer edges |
| radius-xl | 12px | Primary cards, modals |

---

## Shadows

| Token | Value | Usage |
|-------|-------|-------|
| shadow-card | `0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04)` | Default card |
| shadow-card-hover | `0 4px 12px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.04)` | Card hover |
| shadow-modal | `0 20px 60px rgba(0,0,0,0.15), 0 4px 16px rgba(0,0,0,0.08)` | Modal overlay |
| shadow-dropdown | `0 4px 16px rgba(0,0,0,0.12), 0 1px 4px rgba(0,0,0,0.06)` | Dropdowns, popovers |

---

## Transitions

| Speed | Duration | Usage |
|-------|----------|-------|
| Fast | 120ms ease | Hover states, button feedback |
| Base | 200ms ease | Most transitions |
| Slow | 300ms ease | Modals, overlays, larger movements |

---

## Row Heights

| Context | Height |
|---------|--------|
| Standard table row (no groups) | 40px |
| Group / parent row | 50px |
| Department-level child row | 36px |
| Child / role row | 30px |
| Overview Table (all rows) | 50px |
| Deeper nesting | Reduce in ~10px increments |

---

## Card Component

Every card (except Overview Tables) has a header:

```
┌─────────────────────────────────────────────────┐
│  Title          [Scenario Picker ▾]    [⤢] [⚙]  │
├─────────────────────────────────────────────────┤
│  Card content                                    │
└─────────────────────────────────────────────────┘
```

- Title: always present
- Scenario Picker: centered, always visible when in use (not hover-only)
- Action buttons (Expand, Settings): appear only on card hover, right side
- Modals: resizable by hovering near left/right/bottom edge; handle appears inside card boundary

---

## Data Table

- Sticky header row with muted background
- Column widths: user-adjustable by dragging dividers; persist as client state
- Sort: click column header
- Row groups: expandable parent/child with expand arrows
- Visualization cells: horizontal bar background fills left-to-right proportionally, same 3px radius / 2px inset as color highlights

---

## Overview Table

- One per tab, no card title
- All rows 50px tall (including within groups)
- Groups expand into visually separated boxes
- Cell types: value, checkmark, checkbox
- Text: center-aligned; row titles: right-aligned
- User can reorder rows by dragging; add rows via right-click context menu

---

## Metric Card

- 1–3 large values per card
- Column structure (top to bottom): large number → unit label → scenario label
- Scrolls horizontally if more values than fit
- Color highlighting: spotlight style (elliptical radial gradient, not rectangle)

---

## Metric Cluster Table

- 3-axis: rows, top-level columns (plans/scenarios), sub-columns (metrics per cluster)
- Within-cluster gap: 2px; between-column gap: 20px
- Inner corner radius: 5px; outer corner radius: 10px
- Column headers: center-aligned both axes
- Row title capsules: colored pill backgrounds
- Spotlight highlighting cropped by cell boundary

---

## Bar Chart

- Bar corner radius: 3px
- Bar thickness: Small / Medium / Large
- Default color: gray (`#374151`), color only for semantic meaning
- Value labels at bar end by default (toggleable via gear menu)
- User options: orientation (H/V), show value labels (on/off)

---

## Map Card

- Minimal custom UI overlaid on map engine — do not use the map's own built-in controls
- Overlay elements: card title, scenario picker, expand, settings gear, legend button, zoom controls, breadcrumb
- Breadcrumb hierarchy: Country > State > MSA > Zip
- Legend: triggered by list icon, shows color scale in popover
- Base map theme: subdued, data overlays are the visual focus
- Area fills: neutral-to-saturated color scale (heatmap style)

---

## Text Card

- Markdown only: bold, italic, link, H1/H2/H3, bullet/numbered lists
- No font family, size, alignment, or color options
- Margins increase with card size
- Height: natural (auto) or fixed (scroll) — user-configurable

---

## Split Layouts

Map or Chart + Table side by side:
- Resize handle between panes, always visible, prominent on hover, snaps to 50/50
- Linked: hover on map highlights matching table row; click syncs zoom and scroll
- Visible map area shows faint blue gradient on left edge of matching table rows
- Shared scenario picker state across both panes

---

## Gantt Chart

- Monthly or quarterly column toggle in header
- Month width: ~72–80px; quarter width: ~120px
- Program bars: 3px corner radius, categorical palette colors
- Ongoing programs (no end date): extend to edge with faded/dashed right edge
- Headcount staircase: SVG polyline stepping up at milestones, filled below with subtle gradient
- Row heights: group 50px, department 36px, role 30px
- Existing headcount: solid fill; new hires: diagonal hatch or lighter fill

---

## Interactions

| Element | Interaction | Behavior |
|---------|------------|----------|
| Card | Hover | Show action buttons in header |
| Card | Click expand | Open modal |
| Table header | Click | Sort column |
| Table column divider | Drag | Resize column |
| Group row arrow | Click | Expand/collapse children |
| Modal edge | Hover + drag | Resize modal |
| Split handle | Drag | Resize pane ratio |
| Map area | Hover | Highlight in map and matching table row |
| Map area | Click | Sync map zoom and table scroll |
| Scenario Picker | Select | Update card data; shared in split layouts |
| Truncated text | Hover | Show full text in tooltip |

---

## Implementation Notes

- All colors as CSS custom properties for centralized theming
- Use `font-variant-numeric: tabular-nums` for number columns
- Transitions: 120ms fast, 200ms base, 300ms slow — all ease
- Use semantic class names, not utility classes
- Every interactive element needs visible hover/focus states

---

## Gaps — To Be Resolved with Peter

These items are not yet specified and should be filled in before the system is considered complete:

1. **Button system** — primary, secondary, ghost variants; hover/active/disabled states
2. **Form controls** — slider track and thumb, dropdown appearance, toggle switch, text input
3. **Map base tile style** — specific subdued tile theme for light and dark mode
4. **Application chrome** — header height, logo sizing, case/client context display convention
5. **Dark mode token values** — exact values for all tokens in dark mode
6. **Loading and empty states** — computing/loading skeleton, empty card treatment
