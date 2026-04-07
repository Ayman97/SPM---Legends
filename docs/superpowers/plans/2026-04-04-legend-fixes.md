# Legend Fixes Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply 7 UI fixes to the legend reference document in `index.html`.

**Architecture:** All changes are in a single self-contained HTML file. No build step. No dependencies. Verify by opening in a browser.

**Tech Stack:** Vanilla HTML, CSS, JavaScript (inline in `index.html`)

---

### Task 1: Map gradient legend — slider style + two variants

**Files:**
- Modify: `index.html` — widget section 10 (lines ~304–327)

- [ ] **Step 1: Replace widget 10a (Filled map) with two sub-rows: Monochrome and Categorical**

Find this block in `index.html`:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">10</div><h2>Map</h2></div>
  <div class="variant-row">
    <div class="variant-name">a. Filled map</div>
    <div class="variant-legend">
      <div class="gradient-group"><div class="gradient-bar" style="background:linear-gradient(90deg,#e9f2ff,#0c66e4);width:140px"></div><div class="gradient-labels" style="width:140px"><span>0</span><span>500</span><span>1,000</span></div></div>
      <span class="shape-tag">gradient</span>
    </div>
  </div>
```

Replace with:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">10</div><h2>Map</h2></div>
  <div class="variant-row">
    <div class="variant-name">a. Filled map<br><span style="font-size:11px;font-weight:400;color:var(--color-text-subtlest)">Monochrome</span></div>
    <div class="variant-legend">
      <div style="display:flex;align-items:center;gap:8px">
        <span style="font-size:11px;color:var(--color-text-subtlest);font-weight:500;white-space:nowrap">0</span>
        <div style="width:160px;height:10px;border-radius:5px;background:linear-gradient(90deg,#e0e3e8,#172b4d);flex-shrink:0"></div>
        <span style="font-size:11px;color:var(--color-text-subtlest);font-weight:500;white-space:nowrap">1,000</span>
      </div>
      <span class="shape-tag">gradient</span>
    </div>
  </div>
  <div class="variant-row">
    <div class="variant-name">a. Filled map<br><span style="font-size:11px;font-weight:400;color:var(--color-text-subtlest)">Categorical</span></div>
    <div class="variant-legend">
      <span class="leg-item"><div class="sw-circle" style="background:#0c66e4"></div> Category A</span>
      <span class="leg-item"><div class="sw-circle" style="background:#2898bd"></div> Category B</span>
      <span class="leg-item"><div class="sw-circle" style="background:#6a9a23"></div> Category C</span>
      <span class="leg-item"><div class="sw-circle" style="background:#e97f33"></div> Category D</span>
      <span class="leg-item"><div class="sw-circle" style="background:#af59e1"></div> Category E</span>
      <span class="leg-item"><div class="sw-circle" style="background:#e2483d"></div> Category F</span>
      <span class="shape-tag">circle</span>
    </div>
  </div>
```

- [ ] **Step 2: Verify in browser** — Widget 10a now shows two rows: a slider-style gradient (`0 ──bar── 1,000`) and a row of 6 categorical circles.

- [ ] **Step 3: Commit**
```bash
git add index.html
git commit -m "fix: update map legend to slider style and add categorical variant"
```

---

### Task 2: Sankey legend → roundRect swatch

**Files:**
- Modify: `index.html` — widget section 12 (lines ~357–364)

- [ ] **Step 1: Replace flow-band swatches with sw-roundrect**

Find:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">12</div><h2>Sankey</h2></div>
  <div class="variant-row single"><div class="variant-legend">
    <span class="leg-item"><div class="flow-band" style="background:var(--c-blue)"></div> Flow A</span>
    <span class="leg-item"><div class="flow-band" style="background:var(--c-teal)"></div> Flow B</span>
    <span class="leg-item"><div class="flow-band" style="background:var(--c-green)"></div> Flow C</span>
    <span class="shape-tag">rounded band</span>
  </div></div>
</div>
```

Replace with:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">12</div><h2>Sankey</h2></div>
  <div class="variant-row single"><div class="variant-legend">
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-blue)"></div> Flow A</span>
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-teal)"></div> Flow B</span>
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-green)"></div> Flow C</span>
    <span class="shape-tag">roundRect</span>
  </div></div>
</div>
```

- [ ] **Step 2: Verify in browser** — Sankey legend shows the same rounded rect swatches as Bar/Table widgets.

- [ ] **Step 3: Commit**
```bash
git add index.html
git commit -m "fix: sankey legend uses roundRect swatch matching bar chart style"
```

---

### Task 3: Card and List legends → roundRect swatch

**Files:**
- Modify: `index.html` — widget sections 17 and 18 (lines ~404–422)

- [ ] **Step 1: Replace accent-bar with sw-roundrect in Card (widget 17)**

Find:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">17</div><h2>Card</h2></div>
  <div class="variant-row single"><div class="variant-legend">
    <span class="leg-item"><div class="accent-bar" style="background:var(--c-blue)"></div> Category A</span>
    <span class="leg-item"><div class="accent-bar" style="background:var(--c-teal)"></div> Category B</span>
    <span class="leg-item"><div class="accent-bar" style="background:var(--c-green)"></div> Category C</span>
    <span class="shape-tag">vertical line</span>
  </div></div>
</div>
```

Replace with:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">17</div><h2>Card</h2></div>
  <div class="variant-row single"><div class="variant-legend">
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-blue)"></div> Category A</span>
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-teal)"></div> Category B</span>
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-green)"></div> Category C</span>
    <span class="shape-tag">roundRect</span>
  </div></div>
</div>
```

- [ ] **Step 2: Replace accent-bar with sw-roundrect in List (widget 18)**

Find:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">18</div><h2>List</h2></div>
  <div class="variant-row single"><div class="variant-legend">
    <span class="leg-item"><div class="accent-bar" style="background:var(--c-blue)"></div> Category A</span>
    <span class="leg-item"><div class="accent-bar" style="background:var(--c-teal)"></div> Category B</span>
    <span class="leg-item"><div class="accent-bar" style="background:var(--c-green)"></div> Category C</span>
    <span class="shape-tag">vertical line</span>
  </div></div>
</div>
```

Replace with:
```html
<div class="widget-section">
  <div class="widget-header"><div class="wn">18</div><h2>List</h2></div>
  <div class="variant-row single"><div class="variant-legend">
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-blue)"></div> Category A</span>
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-teal)"></div> Category B</span>
    <span class="leg-item"><div class="sw-roundrect" style="background:var(--c-green)"></div> Category C</span>
    <span class="shape-tag">roundRect</span>
  </div></div>
</div>
```

- [ ] **Step 3: Verify in browser** — Card and List legends now show roundRect swatches.

- [ ] **Step 4: Commit**
```bash
git add index.html
git commit -m "fix: card and list legends use roundRect swatch matching bar chart style"
```

---

### Task 4: Shapes overview section at bottom of Tab 1

**Files:**
- Modify: `index.html` — just before `</div><!-- /tab-defaults -->` (line ~424)

- [ ] **Step 1: Add CSS for the shapes overview grid** inside the `<style>` block (before `@media`):

Find `@media(max-width:800px){` and insert before it:
```css
  /* ===== SHAPES OVERVIEW ===== */
  .shapes-overview{background:var(--surface);border:1px solid var(--color-border);border-radius:var(--radius-lg);margin-bottom:16px;overflow:hidden}
  .shapes-overview-header{display:flex;align-items:center;gap:12px;padding:14px 20px;border-bottom:1px solid var(--color-border);background:var(--surface-sunken)}
  .shapes-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:1px;background:var(--color-border)}
  .shape-cell{background:var(--surface);padding:14px 18px;display:flex;flex-direction:column;gap:6px}
  .shape-cell-name{font-size:11px;font-weight:700;color:var(--color-text);font-family:monospace;letter-spacing:.2px}
  .shape-cell-example{display:flex;align-items:center;gap:6px;min-height:20px}
  .shape-cell-usage{font-size:10px;color:var(--color-text-subtlest)}
```

- [ ] **Step 2: Add the shapes overview HTML block** just before `</div><!-- /tab-defaults -->`:

```html
<!-- SHAPES OVERVIEW -->
<div class="section-title" style="margin-top:36px"><span class="badge">REF</span> Legend Shape Reference</div>
<div class="shapes-overview">
  <div class="shapes-overview-header"><div class="wn" style="background:#44546f">S</div><h2>All Shapes — Developer Reference</h2></div>
  <div class="shapes-grid">

    <div class="shape-cell">
      <div class="shape-cell-name">circle</div>
      <div class="shape-cell-example">
        <span class="leg-item"><div class="sw-circle" style="background:#0c66e4"></div> Label</span>
      </div>
      <div class="shape-cell-usage">Donut · Pie · Hierarchical · Network · Scatter · RAG · Bubble Map (color) · Map categorical</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">roundRect</div>
      <div class="shape-cell-example">
        <span class="leg-item"><div class="sw-roundrect" style="background:#0c66e4"></div> Label</span>
      </div>
      <div class="shape-cell-usage">Bar · Combo · Table · Timeline · Treemap · Sankey · Card · List · Gauge · Progress Bar</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">line</div>
      <div class="shape-cell-example">
        <span class="leg-item"><svg width="22" height="6"><line x1="0" y1="3" x2="22" y2="3" stroke="#0c66e4" stroke-width="2" stroke-linecap="round"/></svg> Label</span>
      </div>
      <div class="shape-cell-usage">Line · Area (no markers)</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">line + marker</div>
      <div class="shape-cell-example">
        <span class="leg-item"><svg width="22" height="12"><line x1="0" y1="6" x2="22" y2="6" stroke="#0c66e4" stroke-width="2" stroke-linecap="round"/><circle cx="11" cy="6" r="3" fill="#0c66e4"/></svg> Label</span>
      </div>
      <div class="shape-cell-usage">Line · Area (with markers)</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">roundRect + diamond</div>
      <div class="shape-cell-example">
        <span class="leg-item"><div class="sw-roundrect" style="background:#0c66e4"></div> Phase</span>
        <span class="leg-item"><div class="tm-diamond" style="background:#af59e1"></div> Milestone</span>
      </div>
      <div class="shape-cell-usage">Timeline (phases + milestones)</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">roundRect + line</div>
      <div class="shape-cell-example">
        <span class="leg-item"><div class="sw-roundrect" style="background:#0c66e4"></div> Bar</span>
        <span class="leg-item"><svg width="22" height="12"><line x1="0" y1="6" x2="22" y2="6" stroke="#e97f33" stroke-width="2" stroke-linecap="round"/><circle cx="11" cy="6" r="3" fill="#e97f33"/></svg> Line</span>
      </div>
      <div class="shape-cell-usage">Combo chart</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">gradient</div>
      <div class="shape-cell-example">
        <div style="display:flex;align-items:center;gap:6px">
          <span style="font-size:10px;color:var(--color-text-subtlest)">0</span>
          <div style="width:80px;height:10px;border-radius:5px;background:linear-gradient(90deg,#e0e3e8,#172b4d)"></div>
          <span style="font-size:10px;color:var(--color-text-subtlest)">1K</span>
        </div>
      </div>
      <div class="shape-cell-usage">Map (monochrome) · Heatmap</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">fill + stroke</div>
      <div class="shape-cell-example">
        <span class="leg-item"><div class="radar-swatch" style="background:var(--c-blue);border-color:var(--c-blue)"></div> Label</span>
      </div>
      <div class="shape-cell-usage">Radar chart</div>
    </div>

    <div class="shape-cell">
      <div class="shape-cell-name">size bubbles</div>
      <div class="shape-cell-example">
        <div class="size-group">
          <div class="size-item"><div class="size-bubble" style="width:10px;height:10px"></div><span class="size-label">10</span></div>
          <div class="size-item"><div class="size-bubble" style="width:18px;height:18px"></div><span class="size-label">50</span></div>
          <div class="size-item"><div class="size-bubble" style="width:28px;height:28px"></div><span class="size-label">100</span></div>
        </div>
      </div>
      <div class="shape-cell-usage">Bubble · Bubble Map (size dimension)</div>
    </div>

  </div>
</div>
```

- [ ] **Step 3: Verify in browser** — a "Legend Shape Reference" grid appears at the bottom of Tab 1 showing all 9 shape types with live examples and usage notes.

- [ ] **Step 4: Commit**
```bash
git add index.html
git commit -m "feat: add legend shapes developer reference section to Tab 1"
```

---

### Task 5: Remove pagination indicator from Tab 2

**Files:**
- Modify: `index.html` — the `render()` function inside `<script>` (lines ~566–601)

- [ ] **Step 1: Remove the `indicator` variable and all its usages from the render function**

Find the `render()` function. Remove this line entirely:
```js
var indicator = '<span class="page-indicator" style="background:var(--surface);padding:2px 10px;border-radius:10px;border:1px solid var(--color-border)">' + (page+1) + ' / ' + totalPages + '</span>';
```

Also remove every usage of `indicator` in the render output. In the horizontal branch:
- Remove `+ indicator` from the `left`, `right`, `top`, `bottom` assignments and their usages
- Remove `bottom` and `top` variable appends where they only contained the indicator

Updated horizontal branch (replace the entire `if (orient === 'h')` block):
```js
if (orient === 'h') {
  var justify = align === 'left' ? 'flex-start' : align === 'right' ? 'flex-end' : 'center';
  el.innerHTML = '<div style="display:flex;align-items:center;gap:8px;width:100%">' + prevBtn + '<div style="flex:1;display:flex;align-items:center;gap:12px;justify-content:' + justify + ';overflow:hidden;min-width:0">' + items + '</div>' + nextBtn + '</div>';
} else {
  el.innerHTML = '<div style="display:flex;flex-direction:column;align-items:center;gap:6px;max-width:140px">' + prevBtn + '<div style="display:flex;flex-direction:column;gap:6px">' + items + '</div>' + nextBtn + '</div>';
}
```

- [ ] **Step 2: Remove the `.page-indicator` CSS rule** from the `<style>` block:

Find and delete:
```css
  .page-indicator{font-size:10px;color:var(--color-text-subtlest);font-weight:500;white-space:nowrap}
```

- [ ] **Step 3: Verify in browser** — Tab 2 legends show arrow buttons and items only; no "1 / 2" counter appears anywhere.

- [ ] **Step 4: Commit**
```bash
git add index.html
git commit -m "fix: remove pagination indicator from overflow legend navigation"
```

---

### Task 6: Consistent SVG chevron arrows in Tab 2

**Files:**
- Modify: `index.html` — the `render()` function in `<script>` and the `.arrow-btn` CSS

- [ ] **Step 1: Replace text character arrows with SVG chevrons**

In the `render()` function, find:
```js
var prevChar = orient === 'h' ? '‹' : '▲';
var nextChar = orient === 'h' ? '›' : '▼';
```

Replace with:
```js
var prevChar = orient === 'h'
  ? '<svg width="8" height="12" viewBox="0 0 8 12" fill="none"><polyline points="6,1 2,6 6,11" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>'
  : '<svg width="12" height="8" viewBox="0 0 12 8" fill="none"><polyline points="1,6 6,2 11,6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>';
var nextChar = orient === 'h'
  ? '<svg width="8" height="12" viewBox="0 0 8 12" fill="none"><polyline points="2,1 6,6 2,11" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>'
  : '<svg width="12" height="8" viewBox="0 0 12 8" fill="none"><polyline points="1,2 6,6 11,2" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>';
```

- [ ] **Step 2: Update `.arrow-btn` CSS** to ensure SVG inherits color correctly. Find:
```css
  .arrow-btn{display:inline-flex;align-items:center;justify-content:center;width:24px;height:24px;border-radius:50%;border:1px solid var(--color-border);background:var(--surface);cursor:pointer;flex-shrink:0;color:var(--color-text-subtle);font-size:12px;font-weight:700;transition:all .15s;user-select:none}
```

Replace with (remove `font-size` and `font-weight`, keep everything else, add `line-height:0`):
```css
  .arrow-btn{display:inline-flex;align-items:center;justify-content:center;width:24px;height:24px;border-radius:50%;border:1px solid var(--color-border);background:var(--surface);cursor:pointer;flex-shrink:0;color:var(--color-text-subtle);line-height:0;transition:all .15s;user-select:none}
```

- [ ] **Step 3: Verify in browser** — all navigation arrows in Tab 2 (horizontal and vertical) use the same clean SVG chevron style; horizontal shows `‹` `›` shape, vertical shows `^` `v` shape, both same visual weight and size.

- [ ] **Step 4: Commit**
```bash
git add index.html
git commit -m "fix: replace text character arrows with consistent SVG chevrons in legend navigation"
```

---

## Self-Review

**Spec coverage check:**
1. ✅ Map gradient slider style — Task 1
2. ✅ Two map variants (monochrome + categorical) — Task 1
3. ✅ Sankey → roundRect — Task 2
4. ✅ List & Card → roundRect — Task 3
5. ✅ Shapes overview section — Task 4
6. ✅ Remove pagination — Task 5
7. ✅ Consistent arrows — Task 6

**Placeholder scan:** No TBDs, no vague steps — all code blocks are complete.

**Type consistency:** No shared types across tasks. Each task is self-contained.
