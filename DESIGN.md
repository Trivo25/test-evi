# Design notes

Product: a clinical evidence workspace. A clinician asks for a brief, agents read the sources, and every statement in the brief links to an exact passage. The main task is verifying evidence, so citations, excerpts, and the flagged claim get the strongest treatment.

## Direction

A flat, tonal product surface: white panels on a light grey ground, hairline separators only where they mark a boundary (sidebar, top bar, panel headers), one soft shadow per elevation level, and solid fills for controls. Hierarchy comes from tone and spacing, not from stacked effects. Reading text is set in Georgia; interface text in Inter, which the original brief specified.

## Tokens (see `styles.css` `:root` and the pass blocks that override it)

| Role | Value |
| --- | --- |
| Ground | `#f6f7f9` |
| Surface | `#ffffff`; tonal cards `#f3f4f6` / `#f9fafb` |
| Text | `#111827`; muted `#5b6470` (4.5:1 or better on tonal cards) |
| Border | `#eceef1`; frame edges `#e2e5ea` |
| Source (blue) | text `#335e92`, fill `#edf3fa`, edge `#9fb9d6` |
| Evidence (cream) | fill `#fffcf5`, header `#f8f0df`, border `#e2d8c3`, highlight `#f6e6b8` |
| Attention (amber) | text `#866022`, fill `#fff6e6`, edge `#e3bd6f` |
| Supported (green) | text `#426751`, fill `#eef4ef` |
| Remove (red) | text `#9a463e`, fill `#fbf0ee` |
| Primary action | `#111827` solid |
| Elevation | 1 cards, 2 panels and composer, 3 menus and hover cards, 4 pop-outs |
| Radius | panels 14px, cards 10-12px, buttons 8px, chips and citations pill |
| Type | UI 14px/1.5 Inter; brief 16px/1.7 Georgia; labels 11-13px; headings 14-26px, tracking -0.01 to -0.02em |

## Deliberate choices

- Pills for chips, citations, and composer toggles: they are the interactive "tokens" of the interface and should read differently from rectangular panels and text.
- One amber side stripe, reserved for the unsupported claim. No other stripes.
- Blue is reserved for sources and citations; green appears only with an explicit "supports" statement; amber only for items needing attention.
- Evidence cards use the cream palette so a quotation never looks like assistant text.
- Motion: one spinner for the running agent job, progress bars, and a short fade for arriving content. Reduced motion disables all of it.

## Not in scope

No pricing, testimonials, FAQ, notification center, or theme switch. No invented credentials; marketplace entries are sample data.
