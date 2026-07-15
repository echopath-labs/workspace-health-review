# Activation Guide

Workspace Health Review is an explicit or periodic governance audit. It should
not run automatically inside every implementation task.

## Recommended Activation

For actively changing repositories, consider running the review weekly or at a
team-defined cadence. Also activate it:

- at important milestones;
- when OpenSpec changes, ADRs, instructions, Skills, or other durable records
  have accumulated significantly;
- before archive, release readiness review, onboarding, ownership transfer, or
  resuming work after a long interruption;
- when rules appear stale, duplicated, conflicting, or difficult to recover.

Keep it inactive for casual chat, ordinary read-only questions, simple command
output, and routine implementation work with no workspace-wide health signal.

The default mode is Analyze First. A review produces evidence and
recommendations; it must not archive, delete, rewrite, or initialize governance
files without explicit human approval.

## Ask An Agent To Configure The Project

Use this prompt when you want an Agent to add a repository-level trigger rule:

```text
Add a concise project-level activation rule for $workspace-health-review to
AGENTS.md. Preserve all existing instructions and avoid duplicate review rules.
Recommend an explicit or periodic review for active repositories, important
milestones, accumulated OpenSpec or durable records, archive or release
readiness, onboarding, ownership transfer, and long-interruption recovery. Do
not run it automatically for every implementation task. Keep the default mode
Analyze First and require human approval before modifying governance files.
Show me the proposed block before writing it.
```

Review the proposed block before approving the edit. The Agent should append or
merge the smallest useful rule instead of replacing `AGENTS.md`.

## Add The Rule Manually

Copy and adapt this minimal block:

```markdown
## Workspace Health Review

- Use `$workspace-health-review` periodically for active repositories and at
  important milestones, or when durable records, rules, or Skills accumulate.
- Also use it before archive or release readiness, onboarding, ownership
  transfer, and recovery after a long interruption.
- Do not run it automatically for every implementation task or simple read-only request.
- Default to Analyze First. Do not modify governance files without explicit approval.
```

Choose the cadence that fits the repository. Weekly is a practical starting
point for an active workspace, not a universal requirement.

For Claude Code, Cursor, Gemini CLI, or another Agent, adapt the same rule to
that tool's project instruction file.
