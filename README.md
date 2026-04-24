# tai-demo-skills

A curated collection of Claude Code skills for demo and productivity workflows.

## Installation

Add this marketplace to Claude Code:

```bash
/plugin marketplace add hanzhenliu/tai-demo-skills
```

Then install individual skills:

```bash
/plugin install <skill-name>@tai-demo-skills
```

## Available Skills

| Skill | Description | Invoke |
|-------|-------------|--------|
| `onboarding-wizard` | Customize the Treasure AI onboarding wizard for demos | `/onboarding-wizard [audience]` |

## Adding a New Skill

1. Create the plugin directory structure:

```
plugins/
└── my-skill/
    ├── .claude-plugin/
    │   └── plugin.json
    └── skills/
        └── my-skill/
            └── SKILL.md
```

2. Define `plugin.json`:

```json
{
  "name": "my-skill",
  "description": "What this skill does",
  "version": "1.0.0",
  "license": "MIT"
}
```

3. Write `SKILL.md` with YAML frontmatter:

```markdown
---
name: my-skill
description: What this skill does and when to use it
argument-hint: "[optional-arg]"
allowed-tools:
  - Read
  - Bash(git *:*)
---

# My Skill

Step-by-step instructions Claude follows when this skill is invoked.
```

4. Register the plugin in [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json):

```json
{
  "name": "my-skill",
  "source": "./my-skill",
  "description": "What this skill does",
  "version": "1.0.0",
  "author": { "name": "Han" },
  "license": "MIT",
  "keywords": ["keyword1", "keyword2"]
}
```

## Validate

```bash
claude plugin validate .
```
