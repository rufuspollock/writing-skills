# writing-skills

Patterns and AI skills for writing work — talks, presentations, essays, blog
posts, and more.

Each entry comes in two forms:

- **`skills/<name>/SKILL.md`** — the installable skill. Lean, operational; what
  an agent loads.
- **`patterns/<name>.md`** — the human-oriented writeup. The reasoning, the
  philosophy, a worked example.

## Contents

| Skill | Pattern writeup | What it covers |
|-------|-----------------|----------------|
| [`creating-talks`](skills/creating-talks/SKILL.md) | [patterns/creating-talks.md](patterns/creating-talks.md) | Building a talk as a chain of markdown files: README → notes → script → slides brief → artwork pass → slide build handoff. |

## Installing a skill

### With `npx skills`

[`npx skills`](https://github.com/vercel-labs/skills) installs a `SKILL.md`
straight from GitHub.

```bash
# one skill, by path
npx skills add https://github.com/rufuspollock/writing-skills/tree/main/skills/creating-talks

# or list what's in the repo first
npx skills add rufuspollock/writing-skills --list
```

### Manual / copy-paste

Drop the skill folder into your agent's skills directory
(`~/.claude/skills/` for Claude Code):

```bash
mkdir -p ~/.claude/skills/creating-talks
curl -fsSL https://raw.githubusercontent.com/rufuspollock/writing-skills/main/skills/creating-talks/SKILL.md \
  -o ~/.claude/skills/creating-talks/SKILL.md
```

Or just open the raw file and paste it in:
<https://raw.githubusercontent.com/rufuspollock/writing-skills/main/skills/creating-talks/SKILL.md>
