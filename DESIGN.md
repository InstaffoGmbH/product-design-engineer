# Instaffo Design System (simplified)

A short version of the design system we use at Instaffo. It covers the judgment we apply when we design and build UI. It doesn't depend on a framework: use it with any stack.

| File | Use it for |
| --- | --- |
| [`FOUNDATIONS.md`](./FOUNDATIONS.md) | Colour, spacing, radii, borders, typography, icons, states, motion |
| [`COMPONENTS.md`](./COMPONENTS.md) | When to use which basic component, and what to avoid |
| [`tokens.css`](./tokens.css) | The token values as CSS custom properties |
| This file | Voice and tone for every user-facing string |

## Product surfaces

Instaffo has a candidate-facing app and a recruiter-facing app. Both use brand purple (`primary-*`) as their accent colour. Don't paint customer-facing UI blue.

## Voice and tone

Apply these to every string: buttons, headings, labels, errors, empty states.

- **German-first.** Every string exists in German and English. Don't hard-code one language.
- **Second person:** `du` / `dein` in German, `you` / `your` in English. Never `Sie`. Don't use "we" when talking about the candidate's own data: _your_ profile, _your_ answers.
- **Sentence case** for buttons, headings and labels: _Save_, _Your profile_. Never ALL CAPS or Title Case.
- **Short sentences:** about 15–20 words at most. One thought per sentence.
- **Same concept, same word.** Pick one term and use it everywhere.
- **Use names when you know them.** "Message Anna" beats "Message the talent". At most twice per component.
- **"Talent"** is what we call a candidate, in the singular.
- **Active form.** "Wir berücksichtigen deine Gehaltsvorstellung" beats "Deine Gehaltsvorstellung wird berücksichtigt".
- **Positive phrasing.** Look for "can't", "don't" and "not" and try to flip them.
- **No emoji in UI.** Emoji only appear in content people write themselves.
- **No exclamation marks** in default copy. Save them for real celebration moments.
- **No abbreviations**, and no technical-sounding compound words. "Bevorzugter Arbeitsort" beats "Arbeitsort-Präferenz".
- **Errors say what's wrong and how to fix it.** Never just "Invalid input". Don't blame the user.

### English

- British English: _colour_, _realise_, _centre_.
- Short forms by default: _you'll_, _it's_.
- Numbers: `1,000`, `2.1%`, `€7,000` (currency first, no space).
