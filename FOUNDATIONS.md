# Foundations

The theme-level rules: color, spacing, radii, borders, shadows, typography, icons, states and motion. Use the token names below in your code (as CSS custom properties, theme values or whatever your stack uses). Don't write raw hex values, off-scale sizes or one-off font sizes in components.

## Color

Pick a color by what it means, not by how it looks.

| Family       | Intent                                                                                                                                                                       |
| :----------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `primary-*`  | **Interactive elements only**: buttons, links, focus rings, selected options, clickable icons. Purple on static text teaches people it's clickable.                          |
| `brand-*`    | **Decorative accents** on non-interactive surfaces: accent tags, atmospheric backgrounds. Green only in positive contexts.                                                   |
| `neutrals-*` | Backgrounds and structure: page background, cards, dividers, borders, icon fills.                                                                                            |
| `text-*`     | Neutral text. `text-200` / `text-300` for normal text. `text-100` only for placeholders and disabled text, never for content (it fails contrast). `text-0` on colored fills. |
| `danger-*`   | **Errors and destructive actions only.** One red moment per view. Not for "you can still continue" cases; that's `warning-*`.                                                |
| `success-*`  | **Positive confirmation**: "you did the right thing, keep going". Understated, not celebratory.                                                                              |
| `warning-*`  | **Non-blocking attention**: something is missing, incomplete or about to expire, and the person can still continue.                                                          |
| `utility-*`  | Orange. Reserved for system-level signals.                                                                                                                                   |

### Tokens

```css
:root {
  --primary-400: #431d60; /* hover on primary actions */
  --primary-300: #5e2f82; /* primary actions, links */
  --primary-200: #8951b5; /* press ring */
  --primary-100: #e2bdff;
  --primary-50: #faf3ff; /* hover on ghost and secondary actions */

  --brand-200: #e7ffc0; /* pale green accent */
  --brand-100: #e6e0ff; /* lavender accent */

  --neutrals-400: #3e4242;
  --neutrals-300: #7a7c84;
  --neutrals-200: #d3d4d6; /* default borders and dividers */
  --neutrals-100: #f5f5f7; /* page background */
  --neutrals-0: #ffffff; /* surfaces */

  --text-300: #222222;
  --text-200: #3e4242; /* default text */
  --text-100: #7a7c84; /* placeholder, disabled */
  --text-0: #ffffff; /* text on colored fills */

  --danger-300: #991219;
  --danger-200: #ed1c27;
  --danger-100: #ffe8e9;

  --success-300: #145931;
  --success-200: #219653;
  --success-100: #dcf8db;

  --warning-300: #664d00;
  --warning-200: #ffc000;
  --warning-100: #fff5cd;

  --utility-300: #662a0e;
  --utility-200: #ff6922;
  --utility-100: #ffc4a8;
}
```

### Rules

- **Every color comes from a token.** Text, backgrounds, borders, shadows and SVG fills too. `transparent` and `currentColor` are the only literals allowed. If no token fits, that's a design decision: write it down in `DECISIONS.md`.
- **One colored moment per signal per view.** If a field is in an error state, don't add a red icon, a red border and a red banner. Pick the element that carries the message and keep the rest neutral.
- **Text with a signal takes that signal's color.** Errors `danger-200` / `danger-300`, warnings `warning-300`, confirmations `success-200` / `success-300`, links `primary-300`. All other text uses `text-*`.
- **Icons use `neutrals-*`, never `text-*`**, even when they inherit their color through `currentColor`. `text-300` has no neutrals equivalent, so icons never use it.
- **Translucent colors** are a token with an alpha channel (for example `--neutrals-400` at 10%). Don't invent new colors with `darken()` or similar.

### Contrast

WCAG 2.2:

- **AA minimum**: 4.5:1 for body text, 3:1 for large text, 3:1 for icons, meaningful borders and focus rings.
- **AAA target** on critical UI: error states, primary buttons, anything a person must read to decide. 7:1 for body text, 4.5:1 for large text.
- When in doubt, use `text-300` instead of `text-200`, and a solid `neutrals-0` surface instead of a translucent one.

## Spacing

One scale for every size: padding, gap, margin, icon boxes, focus-ring thickness.

- **Small steps:** 2, 4, 8, 12 px.
- **Above 12 px:** multiples of 8: 16, 24, 32, 40, 48, 56, 64 px.

Nothing else. No 5, 10, 15 or 20 px. If a value doesn't fit, round to the nearest step.

| Typical use                        | Value        |
| :--------------------------------- | :----------- |
| Hairline divider, focus-ring width | 2 px         |
| Gap between an icon and its label  | 4 px         |
| Padding inside a tag or chip       | 8 px         |
| Padding inside a form field        | 12 px        |
| Card and panel padding             | 16 to 24 px  |
| Section spacing, dialog padding    | 24 to 40 px  |
| Page-level rhythm                  | 48 px and up |

Our codebase sets `1rem = 10px`, so `0.8rem` is 8 px. Use px, rem or whatever your stack prefers, as long as the values land on the scale.

## Corner radii

Two tiers: small interactive elements are tight, containers are friendly. The jump from 8 to 20 px is deliberate.

| Radius    | Use it on                                       |
| :-------- | :---------------------------------------------- |
| 4 px      | Checkboxes only                                 |
| 8 px      | Buttons, inputs, alerts, tags. The most common. |
| 12 px     | Badges                                          |
| 20 px     | Panels, cards, chips, company logos             |
| full pill | Status dots, notification dots                  |

## Borders

| Border                                     | Use it for                                                               |
| :----------------------------------------- | :----------------------------------------------------------------------- |
| 1 px solid `neutrals-200` / `neutrals-300` | Default: input borders, dividers, card borders                           |
| 2 px                                       | Buttons, so the border and the fill don't blur together                  |
| 1.5 px `danger-200`                        | Form fields in an error state. Slightly thicker so it reads at a glance. |

No other widths. If something needs more emphasis than 1 px, raise the border color's contrast.

## Shadows

Shadows are warm gray, never cool or blue.

| Name     | Value                                       | Use it for                                                                       |
| :------- | :------------------------------------------ | :------------------------------------------------------------------------------- |
| `panel`  | `15px 15px 40px 0 rgba(199, 195, 195, 0.4)` | Cards and panels that must read as elevated. A designed glow, not a subtle lift. |
| `filter` | `0 4px 10px rgba(122, 124, 132, 0.3)`       | Dropdown menus and popovers                                                      |
| `toggle` | `0 2px 4px rgba(0, 0, 0, 0.25)`             | The knob of a toggle switch                                                      |

Don't add one-off shadows.

## Backgrounds, gradients, transparency

- **Page background:** `neutrals-100`, a warm off-white. **Surfaces:** `neutrals-0`.
- **No full-bleed photos, illustrations, patterns or textures.** Photos only appear as profile pictures and company logos.
- **Atmospheric gradients**, for hero and empty-state backgrounds only: `linear-gradient(180deg, var(--neutrals-100) 0%, <pastel> 200%)`, where the pastel is `brand-100` (purple), `brand-200` (green), `warning-100` (yellow) or `danger-100` (red). Never on buttons, chips, tags or other small UI. Never stack two gradients.
- **No `backdrop-filter` blur.**
- **Opacity** only for alpha tints in tokens and for disabled elements (0.6). Don't use it to fade content; use a lighter `text-*` token.

## Interactive states

| State              | Treatment                                                                                                                                                       |
| :----------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hover**          | Primary actions: a darker shade of the same hue (`primary-300` → `primary-400`). Ghost and secondary: a light tint (transparent → `primary-50`). Never opacity. |
| **Press / active** | A 2 px `box-shadow` ring in `primary-200`. No `transform` or `scale`: the element stays in place.                                                               |
| **Focus**          | 2 px solid outline in the element's own border color, offset 2 px. Keyboard only (`:focus-visible`).                                                            |
| **Disabled**       | `opacity: 0.6`, background `neutrals-100`, text `text-100`, `cursor: not-allowed`.                                                                              |
| **Error**          | 1.5 px `danger-200` border plus a message below the field in `danger-200` / `danger-300`.                                                                       |

## Motion

Motion explains what happened. It never decorates.

| Use                     | Duration and easing |
| :---------------------- | :------------------ |
| Hover on buttons        | `0.3s ease`         |
| Hover on chips and tags | `0.2s ease`         |

No springs, bounces, `scale()` on hover or elaborate enter and exit animations.

## Typography

**Font.** Our brand font is Aeonik Pro, a licensed font. You don't have a licence for it, so use the fallback stack below or a free sans-serif with a similar geometric, warm character, and note your choice.

```css
font-family: "Aeonik Pro", Arial, "Helvetica Neue", Helvetica, sans-serif;
letter-spacing: 0.25px;
color: var(--text-200);
```

**Weights.** Two in product UI: 400 (regular) and 500. Our "bold" is 500, not 700.

| Style       | Size / line height | Weight | Use it for                                                                             |
| :---------- | :----------------- | :----- | :------------------------------------------------------------------------------------- |
| `display-l` | 40 / 48            | 500    | Hero titles. Rarely inside the product.                                                |
| `display-m` | 32 / 40            | 500    | Hero titles. Rarely inside the product.                                                |
| `title-l`   | 24 / 32            | 500    | Page and section headings                                                              |
| `title-m`   | 20 / 28            | 500    | Panel headings, question titles                                                        |
| `body-l`    | 18 / 24            | 500    | Lead text, high-density info cards                                                     |
| `body-m`    | 16 / 24            | 400    | Prose: paragraphs, longer explanations                                                 |
| `body-base` | 14 / 20            | 400    | **The default for interface text**: buttons, inputs, labels, options, most inline text |
| `body-s`    | 12 / 16            | 500    | Metadata, captions, hints. Never the main content.                                     |

Any body style can switch to 500 for emphasis. Don't add other sizes or weights.

## Icons

Use **Material Symbols Rounded** (free from Google Fonts):

- **Style:** rounded. Not outlined, not sharp.
- **Weight:** 300.
- **Fill:** off. A filled glyph only shows the selected state of a toggle (favorite, save).
- **Size:** 24 px by default, 20 px in dense spots (chips, tags, small icon buttons). Never smaller than 20 px.
- **Color:** `neutrals-*` (see Color above).

Every icon-only button needs an accessible name (`aria-label`).
