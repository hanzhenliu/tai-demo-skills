# Goal: Journey Planning

## Workflow

1. **Greet the user** — acknowledge their goal ("journey planning") and output preference. Be concise and action-oriented.

2. **Ask industry** — follow `shared/ask-industry.md`.

3. **Ask data source** — follow `shared/ask-data-source.md`.

4. **Ask journey type** — use AskUserQuestion with:
   - Question: "What type of customer journey would you like to plan?"
   - Single-select, options:
     | Label | Description |
     |-------|-------------|
     | Welcome / onboarding series | Guide new customers through their first experience |
     | Re-engagement / win-back | Bring back inactive or lapsed customers |
     | Upsell / cross-sell | Drive additional purchases from existing customers |
     | Loyalty program | Reward and retain your best customers |
     | Custom journey | Describe your own journey scenario |

5. **Ask audience and channels** — ask 1–2 follow-up questions using AskUserQuestion:
   - "Who is the target audience for this journey?" (e.g., new signups, high-value customers, cart abandoners)
   - "Which channels should the journey use?" (multi-select: Email, SMS, Push notification, In-app message, Paid media)

6. **Build journey structure** — design a journey with up to 8 stages, incorporating:
   - Entry criteria (what triggers a customer to enter)
   - Stages with wait steps (e.g., wait 1 day, wait 3 days)
   - Decision branches (e.g., opened email vs. did not open)
   - Activations at each stage (channel + message)
   - Exit criteria (e.g., customer converts, unsubscribes, or reaches max stages)
   Keep the total under 120 events. Use industry-tailored examples and terminology.

7. **Deliver results** — call `mcp__tas__open_file` to display. Present in the user's preferred output format:
   - Interactive chart: HTML page with a visual journey diagram showing stages, branches, and activations
   - Data table: stage-by-stage breakdown with columns for stage name, trigger, wait time, channel, action, and exit condition
   - Written summary: narrative walkthrough of the journey with rationale for each stage

## Behavior

- Ask one question at a time. Do not overwhelm the user.
- Use the AskUserQuestion tool for all structured questions — do NOT ask as plain text.
- Keep journey plans practical — max 8 stages, clear decision logic, realistic wait times.
- Proactively suggest optimizations (e.g., A/B test branches, re-entry rules, timing adjustments) after presenting the plan.
