# B10 — Responsive / Mobile QA Matrix

## Purpose

B10 verifies that LAUNCH OS remains usable across desktop, tablet and mobile browser widths.

## Current source-level checks

- Responsive viewport meta is present.
- Desktop shell uses a two-column layout.
- Tablet breakpoint at <=980px collapses the workspace side column.
- Mobile breakpoint at <=760px switches the shell to a single-column layout.
- Mobile sidebar becomes an off-canvas navigation.
- Mobile menu control is 38px × 38px.
- Mobile content uses reduced padding and single-column cards.
- Top export/import actions are hidden on mobile to reduce crowding.
- `min-width:0` is applied to the main content boundary to reduce horizontal overflow risk.
- The prototype now contains one consolidated CSS block; a stray duplicate CSS block was removed during B10 hardening.

## Viewport verification matrix

| Target | Width | Source checks | Real device/browser |
|---|---:|---|---|
| Desktop | 1440px | PASS | Pending |
| Desktop compact | 1200px | PASS | Pending |
| Tablet | 980px | PASS | Pending |
| Tablet narrow | 820px | PASS | Pending |
| Mobile | 760px | PASS | Pending |
| Mobile | 480px | PASS | Pending |
| Narrow phone | 390px | PASS | Pending |

## Manual browser/device checklist

When a real browser/device runtime is available, verify:

1. Sidebar navigation opens and closes on mobile.
2. No horizontal page scrolling at 390px, 480px and 760px.
3. Workflow navigation remains horizontally scrollable without clipping.
4. Product Profile inputs remain usable and do not overflow cards.
5. Pricing two-input rows remain usable at narrow widths.
6. Research buttons wrap without clipping.
7. Save/export/import controls remain reachable.
8. Language selector remains reachable in the sidebar.
9. All stage cards fit the viewport.
10. Text remains readable without overlap.
11. Sticky top bar does not cover primary content.
12. Desktop/tablet side cards do not create unexpected overflow.

## Acceptance boundary

B10 is **not 100% closed** until the manual browser/device checklist is executed. Source-level verification is complete; runtime visual verification remains pending.

No browser/device execution is claimed by this document.
