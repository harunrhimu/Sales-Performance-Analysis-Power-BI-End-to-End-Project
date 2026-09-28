# TOKENS — Core Analysis Portfolio (Sales Budget)

Set once per project. Every visual in this report references these values.

```
PROJECT:          Sales Budget — Core Analysis Portfolio
PBIP:             H:\Data Analyst\Core Analysis Portfolio\Power BI Reports\Sales Budget.pbip
SEMANTIC MODEL:   Sales Budget.SemanticModel  (12 tables, 17 measures on _Measures)
BASE THEME:       Fluent2-CY26SU08   ← report.json baseTheme (NOT CY26SU05)
PALETTE:          Teal / Clean

ACCENT:           #1FB6A6   primary series fill — bars, lines, main value
ACCENT DARK:      #12897D   secondary series in the same chart
ACCENT LIGHT:     #6FCF97   tertiary / comparison series
POSITIVE:         #27AE60   variance badge — good
NEUTRAL:          #F2C94C   warning
NEGATIVE:         #EB5757   variance badge — bad
SURFACE:          #FFFFFF   visual card background
PAGE BG:          #F4F6F8   (see note below)
TITLE TEXT:       #2D3436
BORDER RADIUS:    10px      modern / tight
CARD VALUE SIZE:  20pt
CARD LABEL SIZE:  10pt
CARD STYLE:       rich where a PY family exists, simple otherwise
BG IMAGE:         none registered
```

## Notes and deviations

- **Accent is literal hex, never `ThemeDataColor`.** Per SKILL.md, a ColorId resolves against the
  base theme rather than the project accent and silently renders the wrong colour. Chart series
  fills are always literal.
- **`ACCENT DARK` (`#12897D`) is not in the design-system Teal/Clean starter** — that palette only
  defines accent + accent light. This is a derived darker teal, needed because multi-series charts
  walk accent → accent dark → accent light.
- **`POSITIVE` / `NEGATIVE` follow the Teal/Clean palette** (`#27AE60` / `#EB5757`), not SKILL.md's
  Procurement defaults (`#00B53F` / `#D64550`).
- **Page title is `#2D3436`, not `#ffffff`.** §1 of the design system specifies white because its
  reference pages sit on a dark background image. This project has **no registered BG image**, so a
  white title would be invisible on the light canvas. Revert to white if a BG image is added.
- **Page background** is the PBIR default (white) rather than `#F4F6F8` — `makePage()` only supports
  a background *image*, not a solid fill. The difference is subtle; set it in Desktop if it matters.
- **`CARD STYLE` is mixed on purpose.** Only `Total Sales` has a full PY family
  (`Total Sales PY` / `PY Var` / `PY Var % Label`), so `makeCard` renders one rich card and lets the
  rest degrade to simple cards. Adding `Total Margin PY`, `Margin % PY` etc. would upgrade them.
