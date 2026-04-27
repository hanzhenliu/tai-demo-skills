---
name: onboarding
description: "Guide a first-time user to their first output. Triggered automatically when the first user message contains [User Preferences] with goal and output format. Do NOT wait for a slash command — activate immediately when you see this marker."
allowed-tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Write
  - Edit
  - AskUserQuestion
---

# First-Time User Onboarding

When the user's first message contains `[User Preferences]`, follow this workflow.

## Step 1 — Parse preferences

Extract `Goal` and `Output format` from the message.

## Step 2 — Load goal workflow

Find this skill's install directory by searching for this SKILL.md file:

```
Glob("**/plugins/onboarding/skills/onboarding/SKILL.md")
```

Use the directory of the result as the skill root. Then Read the matching goal file:

| Goal | File |
|------|------|
| Analyze data | `goals/analyze-data.md` |
| Find customer segment | `goals/find-segment.md` |
| Journey planning | `goals/journey-planning.md` |
| Generate a report | `goals/generate-report.md` |
| Just explore | `goals/explore.md` |

Also Read `shared/ask-industry.md` and `shared/ask-data-source.md` from the same directory.

## Step 3 — Execute

Follow the loaded goal workflow. Use the shared question templates when asking for industry and data source. Always use AskUserQuestion (not plain text) for structured questions.
