# Evidence workspace prototype

A static HTML and CSS prototype of the document workspace. It shows three objects: the source document, the evidence excerpt, and the working draft. Chat stays visible as the place where the user requests work.

## Open the prototype

Open `index.html` in a browser. No server, build step, or network access is needed. Every page links to the others.

| File | Content |
| --- | --- |
| `index.html` | The populated workspace. Draft v3, three sources, the conversation, and evidence E3 selected. |
| `outputs.html` | The review brief and the requirements comparison, with a recheck example. |
| `workflow.html` | The saved workflow `Agreement comparison` and a `Prepare new project` example. |
| `states.html` | Labeled examples of source management, editing, and review states. |
| `styles.css` | Design tokens, components, and responsive layout. |
| `assets/icons.svg` | The local icon sprite (Lucide-style line icons). The same sprite is inlined at the top of each page so `<use>` works from `file://` in every browser. |

The prototype uses Inter with Arial and sans-serif fallbacks, and Georgia with a serif fallback. No font files are shipped. If Inter is not installed, the browser uses Arial.

## What works without JavaScript

The pages contain no JavaScript. These interactions are native HTML or CSS only:

- **Evidence selection on the workspace.** `E1`, `E2`, `E3` and the inline citations are links to `#e1`, `#e2`, `#e3`. CSS `:target` and `:has()` show the matching panel, mark the selector, the citation, and the source card. Without a fragment, E3 is selected.
- **Source menus, surrounding text, and forms.** These use `<details>`, `<summary>`, `<input>`, and `<textarea>`.
- **Navigation.** Links move between pages and named example states.

`:has()` needs a browser from 2023 or later (Chrome 105+, Safari 15.4+, Firefox 121+). In an older browser the E3 panel still shows by default, but selecting E1 or E2 does not update the citation and source card styling.

## Actions that are static demonstrations

A static page cannot apply typed input or process a chat request. Each of these actions opens a prepared, labeled example instead:

| Action | What happens in the prototype |
| --- | --- |
| Rename | The form shows a prepared name. `Preview renamed state` opens `states.html#renamed`. The typed value is not applied. |
| Replace file | The file input does nothing. `Preview replaced state` opens `states.html#replaced` with Data Handling Schedule v2. |
| Exclude, Pin, Remove, Undo | Checkboxes toggle visually but do not change counts. The examples in `states.html` show the resulting states. `Undo removal` returns to the workspace. |
| Open a source | Opens `states.html#source-preview`, which shows the source page in the center pane with `Back to draft`. |
| Edit paragraph | Opens `states.html#edit`. The text area is editable but nothing is saved. `Save as draft v4 (example)` opens the prepared v4 state. |
| Apply to draft | Opens `states.html#draft-v4`, then `Run recheck (example)` opens `states.html#recheck`. |
| Send | Opens `states.html#example-reply`. The reply is labeled as an example. Typed text is not read. |
| Save as workflow | Opens `workflow.html`. |
| Add file, Start project | Static links inside the `Prepare new project` example. |

No live AI call, PDF processing, authentication, or storage exists in this prototype.

## Verification

Checked with headless Chrome (macOS) at 1024px, 736px, 360px, and 320px on all four pages:

- No horizontal page overflow. Comparison tables scroll inside their own container on narrow screens.
- Three columns above 900px, evidence below the center pane at 900px and below, one column at 620px and below.
- Long source names wrap inside their cards. Source menus open above adjacent cards.
- Touch targets are at least 44px high at 620px and below. Text inputs use 16px text at that width.

Not verified:

- **`reference-fragment.html` was not present in the repository.** The brief refers to it as the primary visual reference. The implementation follows the brief's written specification and the earlier `index.html` and `styles.css` that were in the repository. Composition fidelity to the reference fragment could not be compared.
- Safari and Firefox rendering were not tested. Only Chrome was available.
- Screen reader behavior was not tested. Accessible names, labels, focus styles, and reading order are present in the markup.
