# Workspace Health Review

A lightweight governance health review skill for AI-assisted workspaces.

Keep AI-assisted workspaces understandable, recoverable, and safe to continue.

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Skill](https://img.shields.io/badge/skill-Codex%20Skill-111827.svg)
![Agents](https://img.shields.io/badge/agents-Codex%20%7C%20Claude%20Code%20%7C%20Cursor%20%7C%20Gemini-2563eb.svg)
![Core context](https://img.shields.io/badge/core_context-%E2%89%880.8k_tokens-7c3aed.svg)
![Core size](https://img.shields.io/badge/core_size-3.0KB-0f766e.svg)

> 简体中文说明: [README.zh-CN.md](README.zh-CN.md)

Workspace Health Review helps agents inspect whether a repository or workspace is still maintainable, recoverable, and safe for AI-assisted work.

It is a workspace-level governance audit, not an implementation workflow and not a release tool.

This skill pairs well with [Agent Workflow Governance](https://github.com/echopath-labs/agent-workflow-governance):

| Skill | Scope | Purpose |
| --- | --- | --- |
| `agent-workflow-governance` | Task / workflow | Keep agent execution disciplined. |
| `workspace-health-review` | Workspace | Detect context drift, stale rules, and governance debt. |

## Why This Exists

AI coding agents can move quickly, but workspaces can quietly become hard to understand:

- agent instructions grow and drift;
- skills or rules become too broad;
- durable records accumulate without ownership;
- old decisions stay active after they become stale;
- future humans or agents cannot tell where to resume.
- parent workspaces lose track of which child workspace owns the authoritative
  record.

Workspace Health Review gives teams a lightweight way to inspect these risks before large refactors, releases, onboarding, or cleanup.

## Who Should Use It

Use this skill when a workspace feels bloated, hard to recover, or risky for agents to modify.

Typical use cases include:

- periodic workspace health reviews;
- pre-refactor or pre-release governance checks;
- onboarding readiness reviews;
- AGENTS, CLAUDE, Cursor rule, or custom instruction review;
- durable record, skill, root index, or rule cleanup planning.

## What The Skill Does

The skill reviews workspace boundary, durable records, agent instructions,
skill/rule load, ownership clarity, root index health, recovery readiness,
context drift, and context debt.

It defaults to Analyze First:

```text
Review first.
Recommend next.
Modify only after human approval.
```

## Non-goals

This skill does not implement features, fix bugs, execute releases, deploy infrastructure, rewrite project memory, or automatically delete/modify governance files.

Use project-specific release or operations procedures for production work.

## Quick Start

### Install

Recommended one-line install:

```bash
npx skills add https://github.com/echopath-labs/workspace-health-review --skill workspace-health-review
```

Manual installation:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/echopath-labs/workspace-health-review.git ~/.codex/skills/workspace-health-review
```

If your agent uses a different skill directory, copy this repository into that agent's skill path.

Restart your Codex session after installing the skill so it can be discovered.

### Usage

Invoke the skill directly:

```text
$workspace-health-review
```

Or ask your coding agent:

```text
Use $workspace-health-review to review this workspace before a large refactor. Start with analysis only and do not modify files without approval.
```

More prompts are available in [examples/](examples/).

## Sample Report

A review should produce a concise, evidence-based summary:

```text
Workspace Health Review

Status: Warning

Signals:
- Agent instructions are readable but growing.
- Two durable record systems appear active.
- Several stale rules may no longer match current workflow.

P0:
- Confirm the workspace boundary before the next large refactor.

P1:
- Review AGENTS.md and remove duplicated instructions.
- Archive stale decision records after human approval.

P2:
- Add a short recovery note for onboarding future agents.
```

## Context Cost & Activation

This skill is lightweight and mostly on-demand.

- Recommended scope: project or workspace level.
- Global installation: optional if you want this review discipline across most coding projects.
- Trigger it for health checks, large refactors, releases, onboarding, cleanup, stale rules, and context debt reviews.
- Avoid triggering it for casual chat, read-only questions, or simple command output.

Approximate context cost:

- Core skill entry: about 3.0 KB source size, roughly 0.8k tokens by broad English Markdown estimates.
- Full reference set: moderate.
- Examples: optional.

The skill should not continuously occupy model context unless explicitly invoked or configured by the user.

## Documentation

- [Health Review Reference](references/health-review.md)
- [Report Template](references/report-template.md)
- [Examples](examples/)
- [Roadmap](ROADMAP.md)
- [Changelog](CHANGELOG.md)

## Compatibility

The skill is written for Codex skill conventions. The review workflow can be adapted to Claude Code, Cursor, Gemini CLI, and similar AI coding agents that support reusable instructions.

Standalone use is the default. It can also consume user-approved governance
state and return review findings through an optional context governance
platform without depending on that platform.

See [Platform Integration Contract](references/context-governance-platform.md).

## Open Source Boundary

This repository contains only generic workspace health review guidance.

It should not contain private company process, customer names, production credentials, proprietary release procedures, internal project memory, or private governance datasets.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
