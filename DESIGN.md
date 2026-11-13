# Instaffo Design Foundations

This is the entry point to Instaffo's design system for the take-home challenge. It is a trimmed version of what our product teams work with.

We don't ship our component library with this repo. Use any stack you like. Take the decisions below as the rules a reviewer at Instaffo would apply to your flow. If you break one on purpose, say why in `DECISIONS.md`.

| File                                 | Read it before…                                                                                    |
| :----------------------------------- | :------------------------------------------------------------------------------------------------- |
| [`FOUNDATIONS.md`](./FOUNDATIONS.md) | Picking a colour, a spacing value, a corner radius, a text style, an icon, a hover or focus state. |
| [`COMPONENTS.md`](./COMPONENTS.md)   | Reaching for a button, field, alert, dialog, progress indicator or container.                      |
| This file                            | Writing any text the candidate sees.                                                               |

## Who you design for

Instaffo has two customer-facing surfaces:

- **Talent app**: what candidates use. The application question flow lives here.
- **Company app**: what recruiters use. They write the questions you render.

Both use the brand purple as their accent (`primary-*` in `FOUNDATIONS.md`). Don't use blue in either. Blue belongs to our internal tools only.

On Instaffo, candidates are called **Talent** in English (also in the plural: _1,000 Talent_) and **Talente** in German, not _Bewerber_ or _Kandidaten_. "Talents" with an s means skills, never people.

## Voice and tone

Our voice is **relatable, encouraging and inclusive**. In UI text this means:

- **Address the candidate directly.** German: always `du` / `dein`, never `Sie`. English: `you` / `your`.
- **Sentence case** for buttons, headings and labels: _Send application_, not _Send Application_. Never all caps.
- **Short sentences.** One thought per sentence, at most 15 to 20 words.
- **Active, positive phrasing.** _Wir berücksichtigen deine Gehaltsvorstellung_ beats _Deine Gehaltsvorstellung wird berücksichtigt_. Look for `can't`, `don't`, `not` and try to flip them.
- **Say what to do, not what went wrong.** _Enter a number between 0 and 50_ beats _Invalid input_.
- **Same thing, same word.** Pick _Send application_ or _Apply_ once and use it everywhere.
- **No abbreviations, no technical compound words.** _Bevorzugter Arbeitsort_ beats _Arbeitsort-Präferenz_. _evtl._, _ggf._ and _z.B._ are out.
- **Gender-inclusive German.** Prefer direct address (`du`) or neutral words (_Talente_, _Unternehmen_, _Team_). The colon form (_Mitarbeiter:innen_) is a last resort.
- **No emoji in UI chrome**: buttons, labels, alerts, badges. No exclamation marks, except for a real moment of celebration.

### English specifics

- American English: _color_, _realize_.
- Contractions by default: _you'll_, _it's_, _we're_.
- Numbers: `1,000`, `2.1%`, `€7,000` (currency before the number, no space).

### German specifics

- Numbers: `1.000`, `2,1 %`.

## Languages

German comes first. Every string you write needs a German and an English version. Recruiters write their questions in one language (`language` in the job config), and that language is not always the one the candidate uses. How you handle that is your call.
