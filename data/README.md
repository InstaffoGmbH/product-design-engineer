# Sample data

**Mock data.** Sample analytics and feedback from a similar application question flow. These are not real Instaffo figures. Use them, or don't, as you see fit.

Period: 8 weeks. Each row counts flows, not people: a candidate who applied to three jobs counts three times.

## completion_by_flow.csv

| Column | Meaning |
| :-- | :-- |
| `segment` | What the rows are split by: number of questions in the flow, or device |
| `value` | The group within that segment |
| `flows_started` | Candidates who opened the flow |
| `flows_completed` | Candidates who reached the end of the flow |

## drop_off_by_step.csv

| Column | Meaning |
| :-- | :-- |
| `step` | The question type the candidate saw last. `before_first_question`: opened the flow but left before answering anything |
| `times_shown` | How often a question of this type was shown |
| `left_at_this_step` | How often the candidate closed the flow on this step |
| `median_seconds_on_step` | Median time on the step, for candidates who moved on |
| `share_prefilled_from_profile` | Share of these questions that were prefilled from the profile |

## feedback.md

Short quotes from candidates and recruiters, collected in support tickets and interviews.
