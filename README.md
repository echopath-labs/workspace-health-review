# Workspace Health Review

A lightweight governance health review skill for AI-assisted workspaces.

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Skill](https://img.shields.io/badge/skill-Codex%20Skill-111827.svg)
![Agents](https://img.shields.io/badge/agents-Codex%20%7C%20Claude%20Code%20%7C%20Cursor%20%7C%20Gemini-2563eb.svg)

> 简体中文说明: [README.zh-CN.md](README.zh-CN.md)

Workspace Health Review helps agents inspect whether a repository or workspace is still maintainable, recoverable, and safe for AI-assisted work.

It is a workspace-level governance audit, not an implementation workflow and not a release tool.

This skill pairs well with [Agent Workflow Governance](https://github.com/echopath-labs/agent-workflow-governance):

```text
agent-workflow-governance
= task-level workflow guardrails

workspace-health-review
= workspace-level governance audit
```

## Why This Exists

AI coding agents can move quickly, but workspaces can quietly become hard to understand:

- agent instructions grow and drift;
- skills or rules become too broad;
- durable records accumulate without ownership;
- old decisions stay active after they become stale;
- future humans or agents cannot tell where to resume.

Workspace Health Review gives teams a lightweight way to inspect these risks before large refactors, releases, onboarding, or cleanup.

## Who Should Use It

Use this skill when a workspace feels bloated, hard to recover, or risky for agents to modify.

Typical use cases include:

- periodic workspace health reviews;
- pre-refactor or pre-release governance checks;
- onboarding readiness reviews;
- AGENTS, CLAUDE, Cursor rule, or custom instruction review;
- durable record, skill, or rule cleanup planning.

## What The Skill Does

The skill reviews workspace boundary, durable records, agent instructions, skill/rule load, ownership clarity, recovery readiness, context drift, and context debt.

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

## Context Cost & Activation

This skill is lightweight and mostly on-demand.

- Recommended scope: project or workspace level.
- Global installation: optional if you want this review discipline across most coding projects.
- Trigger it for health checks, large refactors, releases, onboarding, cleanup, stale rules, and context debt reviews.
- Avoid triggering it for casual chat, read-only questions, or simple command output.

Approximate context cost:

- Core skill entry: small.
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

## Open Source Boundary

This repository contains only generic workspace health review guidance.

It should not contain private company process, customer names, production credentials, proprietary release procedures, internal project memory, or private governance datasets.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
