# Foundations

Theme-level rules: colour, spacing, radii, borders, shadows, typography, icons, states and motion. Token values live in [`tokens.css`](./tokens.css). Use the tokens; never invent raw colours, sizes or font sizes.

## Colour

Pick a colour family by intent, not by looks.

| Family | Intent |
| --- | --- |
| `primary-*` (brand purple) | **Interactive elements only:** buttons, links, focus rings, clickable icons |
| `brand-*` (pastels) | **Decoration** on non-interactive surfaces. Hue still carries meaning: green only in positive contexts |
| `neutrals-*` | Backgrounds, surfaces, dividers, borders, icon fills |
| `text-*` | Neutral text. `text-200` / `text-300` for normal text, `text-100` only for placeholder and disabled text, `text-0` for white text on colour |
| `danger-*` | Destructive or irreversible actions, and critical errors. One red moment per view |
| `success-*` | Positive confirmation. Understated, not celebration |
| `warning-*` | Something missing, incomplete or expiring that the user can still get past. Prefer it over `danger-*` when nothing is destructive |

Rules:

- **Tokens only.** No raw hex, `rgb()` or named colours. `transparent` and `currentColor` are fine.
- **One coloured moment per signal per view.** If a red button carries the signal, don't add a red badge, icon and border too.
- **Action ≠ accent.** `primary-*` tells people something is clickable. Don't use it on static text or surfaces.
- **Text that carries a signal takes the signal's colour:** errors `danger-*`, warnings `warning-300`, confirmations `success-*`, links `primary-300`. Everything else uses `text-*`.
- **Icons take their colour from `neutrals-*`**, never from `text-*`.
- **App background** is `neutrals-100`, a warm off-white. Surfaces and cards are `neutrals-0` (white).

### Contrast

WCAG 2.2 AA at minimum: 4.5:1 for body text, 3:1 for large text, icons, meaningful borders and focus rings. Aim for AAA (7:1) on anything a user must read to decide, such as errors and the main call to action.

## Spacing

All sizes use one scale (`1rem = 10px`):

- **Small steps:** `0.2rem`, `0.4rem`, `0.8rem`, `1.2rem` (2 / 4 / 8 / 12 px).
- **Beyond that:** multiples of `0.8rem`: `1.6rem`, `2.4rem`, `3.2rem`, `4rem`, `4.8rem` and so on.

No off-scale values (`0.5rem`, `1rem`, `2rem`). Round to the nearest step.

| Typical use | Value |
| --- | --- |
| Hairline, focus-ring thickness | `0.2rem` |
| Icon-to-text gap | `0.4rem` |
| Tag inner padding | `0.8rem` |
| Form-field padding | `1.2rem` |
| Card padding | `1.6rem`–`2.4rem` |
| Section spacing | `2.4rem`–`4rem` |
| Page rhythm | `4.8rem`+ |

## Corner radii

Small interactive elements feel tight; containers feel friendly. No values in between.

| Radius | Use it on |
| --- | --- |
| `0.4rem` | Checkboxes |
| `0.8rem` | Buttons, inputs, alerts, tags |
| `1.2rem` | Badges |
| `2rem` | Cards, panels, chips |
| `9999px` | Status dots |

## Borders

| Border | Use it for |
| --- | --- |
| `0.1rem` solid `neutrals-200` / `neutrals-300` | Default: inputs, dividers |
| `0.2rem` | Buttons |
| `0.15rem` `danger-200` | Error state on form fields |

No other widths. For more emphasis, raise the border's contrast instead.

## Shadows

Shadows are warm, never cool or blue. Cards that need to read as elevated use the large, soft panel shadow (`--shadow-panel`). Don't author one-off shadows, and don't put a shadow on every card.

## Typography

**Brand font:** our brand typeface is licensed, so it isn't included. Use the fallback stack: `Arial, "Helvetica Neue", Helvetica, sans-serif`.

| Style | Size / line height | Use it for |
| --- | --- | --- |
| `body-base` | 14/20 | **Default** for interface text: buttons, inputs, labels |
| `body-m` | 16/24 | Prose, paragraphs |
| `body-l` | 18/24 | Lead paragraphs |
| `body-s` | 12/16 | Metadata, captions, hints. Never primary content |
| `title-m`, `title-l` | see `tokens.css` | Section and card headings |
| `display-m`, `display-l` | see `tokens.css` | Hero titles only, rarely in product UI |

- **Weights:** 400 for body text. What we call "bold" is 500 (medium). 700 rarely.
- Don't introduce new sizes, weights or families.

## Icons

Use Material Symbols:

- **Rounded** variant, **weight 300**, **fill off** (outlined).
- Filled only for the active state of a toggle icon (favourite, save).
- Size **24px** by default, **20px** in dense places. **Never smaller than 20px.**
- Every icon-only button has an accessible label.

## Interactive states

| State | Treatment |
| --- | --- |
| Hover | Primary fill goes one shade darker (`primary-300` → `primary-400`). Ghost and secondary elements get a light tint (`primary-50`). Never use opacity as a hover effect |
| Pressed | A 2px ring in `primary-200`. No scaling or movement |
| Focus | Keyboard only (`:focus-visible`): 2px outline in the element's border colour, 2px offset |
| Disabled | Opacity 0.6, background `neutrals-100`, text `text-100`, `cursor: not-allowed` |

## Motion

Functional, never decorative. Hover transitions: 0.3s ease on buttons, 0.2s ease on chips and tags. No springs, bounces, scale on hover or elaborate entrance animations.

## Gradients and imagery

Don't invent gradients, and never put one on a button, chip or tag. No illustrations, patterns or textures. Photos only appear as profile pictures and company logos.
