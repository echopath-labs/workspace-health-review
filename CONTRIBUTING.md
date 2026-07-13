# Contributing

Contributions are welcome when they keep the skill generic, lightweight, and safe for open-source use.

## Guidelines

- Keep private company rules, customer information, credentials, and production procedures out of this repository.
- Keep the skill focused on workspace health review, not implementation workflow or release execution.
- Prefer concise, reusable review guidance.
- Put detailed review material in `references/` instead of expanding `SKILL.md`.
- Add examples when they clarify real usage.

## Local Checks

Before proposing changes:

```bash
python3 "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-creator/scripts/quick_validate.py" .
```

If you do not have that validator, manually check that `SKILL.md` has valid YAML frontmatter with `name` and `description`.
