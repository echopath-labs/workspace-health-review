# Workspace Health Review

一个用于 AI 辅助工作区的轻量级治理健康检查 Skill。

让 AI 辅助工作区保持可理解、可恢复，并且可以安全继续推进。

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Skill](https://img.shields.io/badge/skill-Codex%20Skill-111827.svg)
![Agents](https://img.shields.io/badge/agents-Codex%20%7C%20Claude%20Code%20%7C%20Cursor%20%7C%20Gemini-2563eb.svg)

> English version: [README.md](README.md)

Workspace Health Review 帮助 Agent 检查一个仓库或工作区是否仍然可维护、可恢复，并且适合 AI Agent 安全协作。

它是工作区级治理审计，不是实现流程，也不是发版工具。

它适合与 [Agent Workflow Governance](https://github.com/echopath-labs/agent-workflow-governance) 配合使用：

| Skill | 范围 | 作用 |
| --- | --- | --- |
| `agent-workflow-governance` | 单次任务 / 工作流 | 让 Agent 执行过程保持有纪律。 |
| `workspace-health-review` | 工作区 | 发现上下文漂移、过期规则和治理债务。 |

## 为什么需要它

AI 编码 Agent 可以快速推进任务，但工作区会在长期协作中慢慢变得难以理解：

- Agent 指令变长并发生漂移；
- Skills 或规则变得过宽；
- 持久化记录不断堆积但缺少归属；
- 旧决策过期后仍然看起来有效；
- 后续人类或 Agent 不知道从哪里恢复上下文。

Workspace Health Review 提供一种轻量方式，用于在大重构、发版、入职交接或清理前识别这些风险。

## 适合谁使用

当一个工作区开始显得臃肿、难恢复，或者不适合 Agent 直接安全修改时，使用这个 Skill。

典型场景包括：

- 周期性工作区健康检查；
- 大重构或发版前的治理检查；
- 新成员或新 Agent 入场前的可恢复性检查；
- AGENTS、CLAUDE、Cursor rules 或自定义指令检查；
- 持久化记录、Skill 或规则清理规划。

## 这个 Skill 会做什么

它会检查工作区边界、持久化记录、Agent 指令、Skill / 规则负载、归属清晰度、恢复准备度、上下文漂移和上下文债务。

默认模式是先分析：

```text
先审查。
再建议。
经人确认后再修改。
```

## 非目标

这个 Skill 不实现功能、不修 Bug、不执行发版、不部署基础设施、不重写项目记忆，也不会自动删除或修改治理文件。

生产操作请使用项目自己的发布或运维流程。

## 30 秒开始

### 安装

推荐使用一行命令安装：

```bash
npx skills add https://github.com/echopath-labs/workspace-health-review --skill workspace-health-review
```

手动安装：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/echopath-labs/workspace-health-review.git ~/.codex/skills/workspace-health-review
```

如果你的 Agent 使用不同的 Skill 目录，请把这个仓库复制到对应 Agent 的 Skill 路径。

安装后重启 Codex 会话，让 Codex 重新发现 Skill。

### 使用

直接调用：

```text
$workspace-health-review
```

或者对 Agent 说：

```text
使用 $workspace-health-review 在大重构前检查这个工作区。先分析，不要在未经确认的情况下修改文件。
```

更多示例见 [examples/](examples/)。

## 示例报告

一次检查应该输出简洁、基于证据的摘要：

```text
Workspace Health Review

状态：Warning

信号：
- Agent 指令可读，但正在变长。
- 当前可能同时存在两套持久化记录系统。
- 部分旧规则可能已经不匹配当前工作方式。

P0：
- 在下一次大重构前确认工作区边界。

P1：
- 检查 AGENTS.md，移除重复指令。
- 经人确认后归档过期决策记录。

P2：
- 为后续 Agent 入场补充一条简短恢复说明。
```

## 上下文占用与触发方式

这个 Skill 设计为轻量、按需触发。

- 推荐范围：项目级或工作区级安装。
- 全局安装：如果你希望大多数编码项目都使用这套健康检查纪律，可以全局安装。
- 建议在健康检查、大重构、发版、入职交接、清理、规则过期和上下文债务检查时触发。
- 不建议在日常闲聊、只读问答或简单命令输出中触发。

大致上下文成本：

- 核心 Skill 入口：较小。
- 完整参考资料：中等。
- 示例：可选。

除非用户明确调用，或主动配置为默认流程，否则它不应该长期占用模型上下文。

## 文档

- [健康检查参考](references/health-review.md)
- [报告模板](references/report-template.md)
- [示例](examples/)
- [路线图](ROADMAP.md)
- [变更日志](CHANGELOG.md)

## 平台支持

这个 Skill 按 Codex Skill 规范编写。它的审查流程也可以迁移到 Claude Code、Cursor、Gemini CLI 等支持可复用指令的 AI 编码工具。

## 开源边界

这个仓库只包含通用工作区健康检查指导。

请不要提交公司内部流程、客户名称、生产凭证、专有发布流程、内部项目记忆或私有治理数据集。

## 贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 安全

见 [SECURITY.md](SECURITY.md)。

## 开源协议

本项目采用 MIT 协议，见 [LICENSE](LICENSE)。
