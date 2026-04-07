---
title: Legend Reference — UI Fixes
date: 2026-04-04
status: approved
---

# Legend Reference — UI Fixes

All changes are confined to `index.html`.

## 1. Map gradient legend (widget 10a — Monochrome)

**Current:** gradient bar with 3 labels underneath (0, 500, 1,000).

**New:** Image-style layout — `176K ──[gradient bar]── 700K`. Labels flank the bar left/right inline. Gradient: light silver-gray (#e0e3e8) → dark navy (#172b4d). Shape tag: `gradient`.

## 2. Two map legend variants (widget 10a split into two rows)

- **Row: Monochrome** — the updated gradient bar (see §1)
- **Row: Categorical** — 8 circle swatches using Atlassian categorical palette: Blue `#0c66e4`, Teal `#2898bd`, Green `#6a9a23`, Orange `#e97f33`, Purple `#af59e1`, Red `#e2483d`, Yellow `#b38600`, Magenta `#943d73`. Shape tag: `circle`.

## 3. Sankey legend (widget 12)

Replace `flow-band` swatch (opacity 0.7 rounded rect) with `sw-roundrect` — same swatch as Bar/Table/Treemap. Shape tag: `roundRect`.

## 4. List & Card legends (widgets 17–18)

Replace `accent-bar` (4px wide vertical line) with `sw-roundrect`. Shape tag: `roundRect`.

## 5. Shapes overview section (Tab 1 bottom)

New section at the bottom of Tab 1: **"Legend Shape Reference"**. Grid layout. Each cell shows: shape name, live rendered example, and comma-separated list of which widgets use it.

Shapes covered:
| Shape | Used by |
|---|---|
| circle | Donut, Pie, Hierarchical, Network, Scatter, RAG Matrix |
| roundRect | Bar, Combo, Table, Timeline, Treemap, Sankey, List, Card |
| line | Line, Area (no markers) |
| line + marker | Line, Area (with markers) |
| roundRect + diamond | Timeline (with milestones) |
| roundRect + line | Combo |
| gradient | Map (monochrome), Heatmap |
| categorical circles | Map (categorical) |
| fill + stroke | Radar |
| size bubbles | Scatter Bubble, Bubble Map |

## 6. Remove pagination (Tab 2)

Remove the `page-indicator` span (`1 / 2` counter) from all scrollable legend renders in both horizontal and vertical orientations. Arrow buttons remain.

## 7. Consistent arrow style (Tab 2)

Replace text characters (`‹`, `›`, `▲`, `▼`) with inline SVG chevrons of the same visual weight. All arrow buttons: 24×24px, 1px border, border-radius 50%, same hover state. Horizontal: `<` and `>` chevrons. Vertical: `^` and `v` chevrons.
