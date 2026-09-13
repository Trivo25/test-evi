# Evidence workspace prototype

Static HTML and CSS. Three objects: source document, evidence excerpt, working brief. Chat is where the user requests work. The example scenario is a clinical evidence review: a sepsis guideline, a hospital protocol, and a trial report.

## Open

Open `index.html` in a browser. No server or build step.

| File | Content |
| --- | --- |
| `index.html` | Workspace: a sepsis antibiotic-timing review with three clinical sources, a clinical brief, the conversation, and an agent run. |
| `styles.css` | Tokens, components, responsive layout. |
| `assets/icons.svg` | Local icon sprite, also inlined in each page so it works from `file://`. |

Fonts: Inter with Arial fallback, Georgia with serif fallback. No font files shipped.

## What works without JavaScript

- **Evidence on hover or tap.** Hovering or focusing a citation (`E1`, `E2`, `E3`) or the flagged phrase shows the source excerpt: the quotation with the relevant words highlighted, whether the brief uses the exact words or a paraphrase, the source chip, page, and section. Clicking, tapping, or pressing Enter pins the card open and lights up the source card; clicking elsewhere or Escape releases it. `:has()` needs Chrome 105+, Safari 15.4+, or Firefox 121+.
- **Menus, disclosures, forms.** Native `<details>`, `<input>`, `<textarea>`.

## Static controls

Controls that are not wired (sidebar navigation, account, Pin, Rename, the formatting bar, voice input, the plus button, PubMed search, marketplace Install, Add custom skill) show a short "not wired in this prototype" notice when used. File pickers open but uploads are not processed. Replace file and Remove from project change citation states on the page only.

Pop-outs (the document and the marketplace) close with Escape, the Close button, or a click on the backdrop; focus moves into them on open and returns to the opener on close. Menus close with Escape or a click elsewhere. Send echoes your text and shows the assistant thinking indefinitely. No AI call, PDF processing, authentication, or storage.

## Verification

Headless Chrome on macOS at 1024, 736, 360, and 320px on the page: no horizontal overflow, three columns above 900px, one column at 620px and below, 44px targets and 16px inputs on narrow screens.

Not verified:

- `reference-fragment.html` was not in the repository. The build follows the written brief only.
- Safari, Firefox, and screen readers were not tested.
