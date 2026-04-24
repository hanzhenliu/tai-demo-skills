# Goal: Find Customer Segment

## Workflow

1. **Greet the user** — acknowledge their goal ("find customer segment") and output preference. Be concise and action-oriented.

2. **Ask industry** — follow `shared/ask-industry.md`.

3. **Ask data source** — follow `shared/ask-data-source.md`.

4. **Ask segment type** — use AskUserQuestion with:
   - Question: "What kind of segment are you looking for?"
   - Single-select, options:
     | Label | Description |
     |-------|-------------|
     | High-value customers | Identify top spenders or most engaged users |
     | At-risk / churning | Find users showing signs of disengagement |
     | Lookalike audience | Find users similar to a known high-performing group |
     | Behavioral cohort | Group users by specific actions or patterns |
     | Custom criteria | Describe your own segmentation rules |

5. **Explore available data** — based on data source, inspect tables/columns relevant to segmentation (purchase history, engagement events, demographics).

6. **Build segment definition** — construct the segmentation criteria using the available data. Show the user:
   - Criteria used (filters, thresholds)
   - Estimated segment size
   - Key characteristics of the segment

7. **Deliver results** — present in the user's preferred output format:
   - Interactive chart: distribution visualization, segment comparison charts via HTML, call `mcp__tas__open_file`
   - Data table: segment member list with key attributes, offer CSV/XLSX download
   - Written summary: segment profile with actionable insights

## Behavior

- Ask one question at a time. Do not overwhelm the user.
- Use the AskUserQuestion tool for all structured questions — do NOT ask as plain text.
- When presenting segment results, always include the segment size and a brief profile summary.
- Proactively suggest activation ideas (campaigns, journeys) for the identified segment.
