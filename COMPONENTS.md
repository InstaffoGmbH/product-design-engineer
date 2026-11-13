# Components

When to use which component, and what each one is not for. This is about usage, not about props. Build the components in your stack; follow the rules here and the tokens in [`FOUNDATIONS.md`](./FOUNDATIONS.md).

## Buttons

Variants: `primary`, `secondary`, `tertiary`, `danger`, `plain`. Sizes: `small`, `medium`.

- **`primary`**: the page's **one main action** (send, save, confirm). Exactly one per page.
- **`secondary`**: the usual alternative (back, cancel).
- **`tertiary`**: a ghost button, the least emphasis. For low-priority actions.
- **`danger`**: destructive or irreversible actions only (delete, withdraw). One per view.
- **`plain`**: text only, like a link. For "Learn more" or "Edit in profile". Underline on hover.

Don't:

- Put two `primary` buttons on one page.
- Use `danger` for "reset" or "clear". Use `secondary` or `tertiary`.
- Use `plain` for an action that changes data. People expect it to navigate or reveal. Use `tertiary`.

### Icon buttons

Icon-only buttons always need an accessible name (`aria-label`); there is no visible text. Variants: `primary`, `secondary`, `tertiary`. On colored surfaces, use `tertiary` (no background at rest).

## Form fields

Pick the field by the shape of the data:

| Field             | Use it when the answer is…                                               |
| :---------------- | :----------------------------------------------------------------------- |
| Text input        | Short text on one line                                                   |
| Text area         | Longer text. Can show a character count and grow with its content.       |
| Radio group       | Exactly one choice from a small set                                      |
| Select (dropdown) | One choice from a long list                                              |
| Multi-select      | Several choices from a list. Selected values show as chips in the field. |
| Checkbox          | An agreement or opt-in, or one item in a short multi-choice list         |
| Selectable chips  | Several choices from a short list, as toggles                            |
| Block buttons     | Large card-style options, when each option needs a description           |
| Toggle            | An on/off setting that takes effect immediately                          |
| Step slider       | A value on a short discrete scale, such as a level or rating             |

**Error messages** say what's wrong and how to fix it, in plain words. Not just "Invalid input". See `FOUNDATIONS.md` → Interactive states for the error style.

## Alerts

Variants: `info`, `primary`, `success`, `warning`, `error`.

- **`info`**: background information that needs no action. Calm tone.
- **`primary`**: neutral messages, neither good nor bad news.
- **`success`**: confirms the person did the right thing. Short. Keep it for real moments, such as "Application sent".
- **`warning`**: a risk that doesn't block. Urgent without panic; suggest what to do.
- **`error`**: something failed. Say what went wrong and how to fix it. Don't blame the person.

Don't:

- Use `error` when the person can still continue. That's `warning`.
- Use `success` for every small save. The signal wears out.
- Stack several `error` alerts. Merge them into one.

## Badges and tags

**Badge**: a static status. Variants `default` (counts), `neutral` (_In review_, _Draft_), `positive` (_Active_, _Verified_), `warning` (_Expires soon_), `alert` (_Failed_, _Expired_).

**Tag**: a static label for a category. Variants `default`, `neutral`, `warning`, `danger`, `accent`. On Instaffo, `accent` marks things that **match the person's profile**, such as matched skills.

**Chip**: interactive. Either _selectable_ (toggles like a checkbox) or _dismissible_ (a value the person added, with a remove icon). Never both.

## Dialogs and overlays

Choose by weight: tooltip < popover < dialog < drawer.

- **Info icon with tooltip**: a short explanation next to a field ("We only use this to …"). Not for anything the person must read.
- **Dialog**: the person must deal with this before anything else.
  - _Informational_: header, body, close icon. No footer buttons.
  - _Action_: header, body, footer with one primary action and a tertiary dismiss. The dismiss says what it does (_Cancel_, _Discard changes_), never _OK_.
  - _Multi-step_: a back button top left. Going back keeps what the person entered.
- **Drawer**: a panel that slides up from the bottom. Made for mobile, works on desktop.

Dialogs lock the page scroll, trap focus while open and return focus when closed.

## Progress and loading

| Component      | Use it for                                                                                           |
| :------------- | :--------------------------------------------------------------------------------------------------- |
| Spinner        | Short, generic waits                                                                                 |
| Progress bar   | Continuous progress from 0 to 100%                                                                   |
| Step indicator | Progress through steps ("Step 3 of 5")                                                               |
| Steps          | Named steps with titles and optional descriptions, clickable to go back. Full-page multi-step forms. |
| Skeletons      | Loading content with a known shape. Prefer them over spinners; they avoid layout shift.              |

## Containers

**Panel**: the default card. `neutrals-0` background on the `neutrals-100` page, 20 px radius, 16 to 24 px padding, no border. Use the `panel` shadow only for content that must read as elevated, not on every card. Header and footer run edge to edge.

Don't change the radius, add a border, or put a panel inside a panel.

**Surface**: a semi-transparent white container (25, 50, 75 or 100% white). 100% for overlays such as dialogs, drawers and popovers. Lower values for supporting containers that should sit closer to the background.

**AI surfaces.** When content is generated or suggested by AI, Instaffo marks it with its own light gradient surface or an AI badge. Use one gradient per region at most, and never on buttons, chips or tags.

**Accordion / collapse**: hide secondary content behind a toggle. A collapse for a single "More details"; an accordion for a list of sections.

**Scroll hint**: a small pill that tells the person there's something to act on below the fold, for example in a long step or a dialog body. Not for short lists.

## Before you ship: checklist

1. Every size is on the spacing scale: 2, 4, 8, 12 px, then multiples of 8.
2. Colors are picked by meaning, from tokens. No raw hex in components.
3. One colored moment per signal per view.
4. One `primary` button per page.
5. `body-base` (14 / 20) is the default for interface text.
6. Every icon-only button has an `aria-label`.
7. Icons: Material Symbols Rounded, weight 300, fill off, 20 or 24 px. Colored with `neutrals-*`.
8. Sentence case, `du` in German, no emoji in UI chrome.
