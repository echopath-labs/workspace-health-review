---
name: workspace-health-review
description: Use for periodic or requested workspace health reviews focused on durable records, agent instructions, skills, rules, ownership, stale context, context drift, context debt, and recovery risks. Use before large refactors, releases, onboarding, repository cleanup, or when a workspace feels bloated or hard to resume. Do not use for implementation or release execution.
---

# Workspace Health Review

Use this skill to review long-term workspace governance health.

It answers:

```text
Is this workspace still maintainable, recoverable, and safe for agents to work in?
```

It does not implement features, fix bugs, execute releases, or modify governance files without approval.

Default to standalone operation. If the user has enabled a context governance
platform, read `references/context-governance-platform.md` and use only its
approved, observable inputs. Platform availability must never block the review.

## Project Extensions

Treat this skill as a portable baseline. Apply nearer workspace instructions and
project-specific review checks as named extensions when they are more specific or
stricter. Keep their findings distinguishable from the core review, and surface
material conflicts instead of silently reconciling them.

## Activation

Use this skill when the user asks for:

- workspace health;
- context debt;
- stale rules, stale docs, or stale decisions;
- agent instruction, `AGENTS.md`, `CLAUDE.md`, Cursor rule, or custom instruction review;
- skill growth, duplicate rules, or prompt bloat;
- durable record hygiene across OpenSpec, ADRs, issues, docs, runbooks, or project notes;
- ownership, recovery, onboarding, or handoff readiness;
- a pre-refactor, pre-release, or periodic governance audit.

Use `agent-workflow-governance` for task-level implementation workflow. Use this skill for workspace-level health review.

Do not activate this review automatically inside an implementation task merely
because `agent-workflow-governance` is active. Run it as an explicit or periodic
workspace audit, or propose it separately when a task exposes workspace-wide
governance debt.

## Mode

Default to Analyze First.

Do not modify files, archive records, delete rules, rewrite skills, or change agent instructions until the user approves the proposed actions.

## Review Workflow

1. Identify the workspace boundary and any child workspaces.
2. Inventory agent entry files, durable record systems, skills, docs, and visible governance rules.
3. Inspect the smallest useful context set. Do not bulk-read unrelated archives, generated files, dependencies, or private data.
4. Review health signals using `references/health-review.md`.
5. Produce a report with:
   - workspace inventory;
   - evidence-backed overall status;
   - an optional numeric score only when its method and evidence are shown;
   - durable record health;
   - agent instruction and rule health;
   - skill/load health;
   - ownership and recovery health;
   - context drift and context debt;
   - P0/P1/P2 recommendations;
   - actions that require human approval.
6. Keep recommendations specific and path-based. Prefer precise file paths and concrete cleanup targets over broad advice.

When the user requests machine-readable results, or an approved platform needs
the report, read `references/result-contract.md`. Do not emit the structured
payload by default.

## References

Read only the reference needed for the current task:

- `references/health-review.md`: detailed review signals, scoring guidance, and report structure.
- `references/report-template.md`: copy-ready report format.
- `references/context-governance-platform.md`: when a user-authorized platform supplies governance state or receives the review result.
- `references/result-contract.md`: when a user or approved integration requests structured review input or output.

If the workspace has no durable record system, do not initialize one silently. Report the gap and propose options for the user to approve.
