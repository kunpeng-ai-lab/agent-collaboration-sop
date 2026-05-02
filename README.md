# Agent Collaboration SOP

一套面向主流 AI 编程/工程 Agent 的双 Agent 协作 SOP。

它不是 Codex 专用，也不是 Claude Code 专用，而是一套通用协作协议，适用于：

- Codex
- Claude Code
- OpenClaw
- Hermes
- 其他支持项目读写、代码修改、测试、review、handoff 的 Agent

## 解决什么问题

当同一台机器、同一个仓库、同一个项目里有两个 Agent 协作时，最容易出现这些问题：

- 两个 Agent 都在改，没人真正审核
- 测试过了，但偏离了产品目标
- 实现看起来对，但破坏了原架构
- 新阶段还没获得 Owner 确认就直接开始
- 口头说“已完成”，但没有证据、截图、台账、验证记录
- Reviewer 只做代码风格检查，没有做工程质量和项目目标守门

本项目给出一套可复制的流程：

```text
初始化问卷 -> 固化角色/简称/Owner 称呼 -> Executor 实现 -> Reviewer 全面审核
-> Reviewer 向 Owner 汇报共识 -> Owner 批准 -> 进入下一阶段
```

## 默认协作模式

默认是单一职责模式：

| 角色 | 职责 |
| --- | --- |
| Owner | 项目最终决策者，确认目标、边界、阶段进入、发布和上游提交 |
| Executor Agent | 主责实现：设计细化、编码、文档、自测、交付 handoff |
| Reviewer Agent | 主责审核：代码、架构、工程结构、目标偏离、测试、安全、证据、发布风险 |

交叉模式仅作为高级变体，不作为默认模式。

## 快速开始

1. 复制 `templates/project-sop.md` 到你的项目：

```text
docs/PROJECT_SOP.md
```

2. 让两个 Agent 先执行初始化问卷：

```text
请使用 Agent Collaboration SOP。先不要开始开发，先根据 docs/initialization-questionnaire.md 向 Owner 提问，确认项目简称、Owner 称呼、Executor Agent 名称/简称、Reviewer Agent 名称/简称、当前阶段、范围和红线规则，并写入 docs/PROJECT_SOP.md。
```

3. Executor 开始执行已批准范围。

4. Executor 完成后使用 `templates/executor-handoff.md` 交付。

5. Reviewer 使用 `templates/reviewer-checklist.md` 全面审核。

6. Reviewer 使用 `templates/owner-consensus-report.md` 向 Owner 汇报，等待确认。

## Reviewer 必须审核什么

Reviewer 不是“跑一下测试”的角色。Reviewer 必须审核：

- 是否偏离项目目标
- 是否偏离前期设计和 Owner 决策
- 工程结构是否健康
- 模块边界是否合理
- 是否引入不必要复杂度
- 是否存在安全/脱敏/凭证泄露风险
- 测试是否覆盖关键路径和失败路径
- 文档是否夸大验证结果
- 是否需要截图、证据、台账
- 是否涉及发布、部署、上游 PR、客户可见输出

## 目录结构

```text
agent-collaboration-sop/
  README.md
  LICENSE
  docs/
    initialization-questionnaire.md
    protocol.md
    naming-rules.md
    reviewer-quality-bar.md
  templates/
    project-sop.md
    executor-handoff.md
    reviewer-report.md
    owner-consensus-report.md
    evidence-ledger.md
  adapters/
    codex.md
    claude-code.md
    openclaw.md
    hermes.md
  examples/
    single-responsibility-example.md
```

## 开源定位

这是一个工程协作 SOP 项目，不包含任何私有业务代码。

建议开源仓库名：

```text
agent-collaboration-sop
```

或：

```text
dual-agent-collaboration-sop
```

