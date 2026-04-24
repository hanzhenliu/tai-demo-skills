# Goal: Analyze Data

## Workflow

1. **Greet the user** — acknowledge their goal ("analyze data") and output preference. Be concise and action-oriented.

2. **Ask industry** — follow `shared/ask-industry.md`.

3. **Ask data source** — follow `shared/ask-data-source.md`.

4. **Explore data** — based on the data source answer:
   - Synthetic data: list available tables in the `treasurebikes` database, describe their schemas, and suggest which tables are most relevant to the user's industry.
   - Upload my own data: wait for file upload, then inspect the data structure.

5. **Suggest analysis approaches** — offer 2–3 concrete analysis ideas tailored to the user's industry. Use AskUserQuestion to let them pick or describe their own. Examples by industry:
   - Retail: basket analysis, customer lifetime value, seasonal trends
   - CPG: brand switching, promotion lift, channel mix
   - Travel: booking funnel, destination affinity, loyalty tier analysis
   - Automotive: lead-to-sale conversion, service retention, model preference
   - Media: content engagement, churn prediction, audience overlap
   - D2C: cohort retention, acquisition channel ROI, repeat purchase rate
   - B2B Tech: pipeline velocity, product adoption, expansion revenue

6. **Execute analysis** — run queries, compute metrics, and build the output.

7. **Deliver results** — present in the user's preferred output format:
   - Interactive chart: generate an HTML page with charts, call `mcp__tas__open_file`
   - Data table: present structured table, offer CSV/XLSX download
   - Written summary: natural language analysis with key takeaways

## Behavior

- Ask one question at a time. Do not overwhelm the user.
- Proactively suggest next steps after each deliverable.
- If the user's request doesn't make sense with the available data, suggest alternatives rather than failing.
