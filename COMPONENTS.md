# Components

When to use which basic component, and what to avoid. These describe intent and states, not code: build them in whatever stack you choose, using the rules in [`FOUNDATIONS.md`](./FOUNDATIONS.md).

## Buttons

### Button

Variants: `primary`, `secondary`, `tertiary`, `danger`, `plain`. Sizes: `small`, `medium`.

- **`primary`:** the one main action on the page (save, submit, confirm). **Exactly one per page.**
- **`secondary`:** the usual alternative (cancel, back).
- **`tertiary`:** ghost button, least emphasis.
- **`danger`:** destructive or irreversible actions only (delete, remove). One per view.
- **`plain`:** text-only, link-like, for navigating or revealing ("Learn more"). Underlined on hover.

Avoid:

- More than one `primary` button on a page.
- `danger` for "reset" or "cancel". Use `secondary` or `tertiary`.
- `plain` for actions that change data. Use `tertiary`.

### Icon button

Icon-only button. Variants: `primary`, `secondary`, `tertiary`. **Always give it an accessible label**, since it has no visible text. For a toggle (favourite, save), swap between the outlined and filled glyph.

## Form fields

Every field has a label, and every error message says what's wrong and how to fix it. Never just "Invalid input".

| Use | When the answer is |
| --- | --- |
| Input | Short, single-line text or a number |
| Text area | Longer text. Can show a character count and grow with its content |
| Select | One value from a longer list. Can allow several values (selected values show as chips in the field) |
| Radio group | Exactly one from a small set of options |
| Checkbox | An opt-in, or one item in a multiple choice |
| Toggle | An on/off setting that takes effect immediately |
| Block button | A large, card-style option, for choices that need a short description |

**States for every field:** default, hover, focus, filled, disabled, error. In the error state the border turns `danger-200` (`0.15rem`) and the message appears below the field in `danger-*` text.

## Alerts

Variants: `info`, `primary`, `success`, `warning`, `error`.

- **`info`:** information that needs no action. Calm.
- **`primary`:** neutral system messages, neither good nor bad.
- **`success`:** confirms the user did the right thing. Short. Reserve it for real moments, not every small save.
- **`warning`:** a non-blocking issue. Urgent without panic; suggest what to do.
- **`error`:** a critical failure. Explain what went wrong and how to fix it, without blame.

Avoid: `error` when the user can still proceed (use `warning`), and stacking several errors in one view (combine them).

## Badges and tags

- **Badge:** a static status (`In review`, `Verified`). Variants: `default`, `neutral`, `positive`, `warning`, `alert`.
- **Tag:** a static category label. Variants: `default`, `neutral`, `warning`, `danger`, `accent`. `accent` also marks something that matches the user's profile.
- **Chip:** interactive. Either selectable (toggles like a checkbox) or dismissible (a value the user added). Never both.

## Containers

### Panel (card)

The default opaque card.

- Background `neutrals-0` on the `neutrals-100` page background.
- Radius `2rem`. Padding `1.8rem` on desktop, `1.5rem` on mobile.
- No border. Use the panel shadow when it needs to read as elevated.

Avoid: custom radii, borders on panels, and panels inside panels.

### Modal

For when the user must deal with something before doing anything else.

- **Informational:** header, body and a close icon. No buttons in the footer.
- **Action:** header, body and a footer with one `primary` action and a `tertiary` dismiss. The dismiss says what it does ("Cancel", "Discard changes"), never "OK".

### Tooltip

A small (i) icon with a short explanation on hover or focus. For explaining a single field, not for onboarding.

Choose by weight: tooltip < modal.

## Loading

Use skeletons that look like the content when its shape is known; they avoid layout shift. Use a spinner only when it isn't.

## Checklist before you ship

1. Sizes snap to the spacing scale.
2. Colours are picked by intent, from tokens only.
3. One coloured moment per signal per view.
4. One `primary` button per page.
5. Every icon-only button has a label.
6. Icons: rounded, weight 300, outlined, 20px or larger.
7. Sentence case, German and English, no emoji in UI.
