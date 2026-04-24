---
name: onboarding-wizard
description: "Customize the Treasure AI first-time user onboarding wizard for demos. Use when you need to add, remove, or modify onboarding questions, options, or the system prompt generated from wizard answers."
argument-hint: "[industry or goal to tailor for]"
allowed-tools:
  - Read
  - Edit
  - Grep
  - Glob
  - Bash(cd *:*)
  - Bash(npm run *:*)
  - Bash(npx *:*)
---

# Onboarding Wizard Customization

Customize the Treasure AI sandbox onboarding wizard for a specific demo audience.

## Key Files

- `ui/packages/shared/src/constants/onboardingWizard.ts` — wizard questions, options, skip logic, and `formatWizardPrefix()` which generates the system prompt injected into the agent session.

## Workflow

### Phase 1 — Understand the request

1. Read `ui/packages/shared/src/constants/onboardingWizard.ts` to see the current wizard config.
2. If the user provided an argument (e.g., an industry or goal), use it to tailor the changes. Otherwise, ask what audience or scenario the demo targets.

### Phase 2 — Make changes

The wizard has four question pages, each an entry in `ONBOARDING_WIZARD_QUESTIONS`:

| Index | Header | Purpose |
|-------|--------|---------|
| 0 | Goal | What the user wants to accomplish |
| 1 | Industry | User's industry vertical |
| 2 | Data source | Where to pull data from |
| 3 | Output | Preferred result format |

Each question follows the `AskUserQuestion` type:

```ts
{
  question: string;       // displayed to user
  header: string;         // short label, used as key in formatWizardPrefix
  multiSelect: boolean;
  options: { label: string; description: string }[];
}
```

When modifying:

- **Adding options**: Add to the `options` array. Keep labels short (≤4 words). Descriptions are optional but helpful.
- **Removing options**: Remove from the array. Check if the removed label is referenced in `formatWizardPrefix()` or `WIZARD_SKIP_LABEL`.
- **Reordering questions**: The order in the array is the display order.
- **Changing the system prompt**: Edit the `lines` array in `formatWizardPrefix()`. This is the prompt injected into the agent when the user completes the wizard. Tailor instructions, KPIs, terminology, and behavior to match the demo scenario.
- **Skip behavior**: `WIZARD_SKIP_LABEL` controls which option label triggers the skip flow. `WIZARD_SKIP_GREETING` is the message shown when skipping.

### Phase 3 — Verify

1. Run `cd ui && npm run typecheck` to ensure type safety.
2. Run `cd ui && npm run check` to lint.
3. Review the generated system prompt by mentally tracing `formatWizardPrefix()` with sample answers to confirm it reads naturally.

## What NOT to Do

- Do not change the `AskUserQuestion` type definition — it is shared across the platform.
- Do not remove the `WIZARD_SKIP_LABEL` or skip flow — it must always be available.
- Do not add more than 10 options per question — the UI scrolls poorly beyond that.
- Do not hardcode database or table names in questions — those belong in the system prompt only.
