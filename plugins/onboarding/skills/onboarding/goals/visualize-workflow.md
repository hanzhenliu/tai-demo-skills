# Goal: Visualize a Workflow

## Workflow

1. **Greet the user** — acknowledge their goal ("visualize a workflow") and output preference. Be concise and action-oriented.

2. **Ask industry** — follow `shared/ask-industry.md`.

3. **Ask data source** — follow `shared/ask-data-source.md`.

4. **Ask workflow type** — use AskUserQuestion with:
   - Question: "What type of workflow would you like to visualize?"
   - Single-select, options:
     | Label | Description |
     |-------|-------------|
     | Customer journey | Map the end-to-end customer experience across touchpoints |
     | Campaign flow | Visualize a marketing campaign's trigger, steps, and branches |
     | Data pipeline | Show how data flows from source to activation |
     | Conversion funnel | Visualize drop-off at each stage of a process |
     | Custom workflow | Describe your own workflow to visualize |

5. **Gather workflow details** — based on the type selected, ask 1–2 follow-up questions to understand the specific workflow (e.g., which touchpoints, which campaign channels, which funnel stages).

6. **Generate visualization** — create the workflow as:
   - An HTML page with an interactive diagram (preferred for journey/campaign flows)
   - A Mermaid diagram (`.mmd` file) for simpler flows
   - Use clear labels, directional arrows, and decision branches where applicable

7. **Deliver results** — call `mcp__tas__open_file` to display the visualization. Regardless of the user's output format preference, workflow visualizations are always visual — but accompany with:
   - Interactive chart: the visualization itself is the output
   - Data table: include a step-by-step table alongside the diagram
   - Written summary: include a narrative walkthrough of the workflow

## Behavior

- Ask one question at a time. Do not overwhelm the user.
- Use the AskUserQuestion tool for all structured questions — do NOT ask as plain text.
- Keep visualizations clean and readable — avoid cramming too many nodes into a single diagram.
- Proactively suggest variations or optimizations to the workflow after presenting it.
