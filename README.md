# Evidence workspace prototype

Static HTML and CSS. Three objects: source document, evidence excerpt, working draft. Chat is where the user requests work.

## Open

Open `index.html` in a browser. No server or build step.

| File | Content |
| --- | --- |
| `index.html` | Workspace: three sources, draft v3, conversation, evidence E3 selected. |
| `styles.css` | Tokens, components, responsive layout. |
| `assets/icons.svg` | Local icon sprite, also inlined in each page so it works from `file://`. |

Fonts: Inter with Arial fallback, Georgia with serif fallback. No font files shipped.

## What works without JavaScript

- **Evidence on hover.** Hovering or focusing a citation (`E1`, `E2`, `E3`) or the flagged phrase shows the source excerpt: the quotation with the relevant words highlighted, the source chip, page, section, and source version. The matching source card lights up at the same time. Clicking a citation jumps to that source card. `:has()` needs Chrome 105+, Safari 15.4+, or Firefox 121+.
- **Menus, disclosures, forms.** Native `<details>`, `<input>`, `<textarea>`.

## Static controls

Source menus, pin, rename, replace, remove, Edit paragraph, the formatting bar, and the composer toolbar are visual only. Clicking them does nothing. Send echoes your text and shows the assistant thinking indefinitely. No AI call, PDF processing, authentication, or storage.

## Verification

Headless Chrome on macOS at 1024, 736, 360, and 320px on the page: no horizontal overflow, three columns above 900px, one column at 620px and below, 44px targets and 16px inputs on narrow screens.

Not verified:

- `reference-fragment.html` was not in the repository. The build follows the written brief only.
- Safari, Firefox, and screen readers were not tested.
