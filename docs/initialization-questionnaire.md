# Initialization Questionnaire

在任何开发、修改、review 前，两个 Agent 必须先向 Owner 提问，并把答案固化到项目的 `docs/PROJECT_SOP.md`。

不要跳过这一步。

## 1. 项目身份

请 Owner 回答：

```text
1. 这个项目的正式名称是什么？
2. 后续沟通使用什么项目简称？例如 GA、OWSL、KAB。
3. 当前项目是开源、闭源，还是暂时内部项目？
4. 项目当前最重要的短期目标是什么？
5. 项目长期目标是什么？
```

## 2. Owner 称呼

请 Owner 回答：

```text
1. 后续在文档和汇报里如何称呼你？
   例如：Owner、项目 Owner、产品 Owner、负责人、你的名字。
2. 哪些事项必须由你最终确认？
```

默认必须 Owner 确认：

- 新阶段开始
- 范围变更
- 上线部署
- 上游 PR
- 对外发布
- 客户可见报告
- 商业边界
- 凭证或敏感配置使用

## 3. Agent 身份与简称

请 Owner 回答：

```text
1. 哪个 Agent 是 Executor？
2. Executor 的显示名称是什么？
3. Executor 的简称是什么？
4. 哪个 Agent 是 Reviewer？
5. Reviewer 的显示名称是什么？
6. Reviewer 的简称是什么？
```

示例：

```text
Executor Agent: Claude Code
Executor Short Name: CC

Reviewer Agent: Codex
Reviewer Short Name: CX
```

## 4. 当前阶段

请 Owner 回答：

```text
1. 当前阶段叫什么？
2. 这个阶段允许做什么？
3. 这个阶段明确不允许做什么？
4. 完成标准是什么？
5. 哪些测试或证据必须提供？
```

## 5. Reviewer 权限

请 Owner 回答：

```text
1. Reviewer 是否有权阻止进入下一阶段？
2. Reviewer 是否有权要求补测试、补文档、补截图、补证据？
3. Reviewer 是否可以指出项目目标/架构/产品方向偏离？
4. Reviewer 是否可以要求重新讨论范围？
```

建议默认答案：全部可以。

## 6. 写入 PROJECT_SOP

确认后，Agent 必须把答案写入：

```text
docs/PROJECT_SOP.md
```

然后再进入开发或 review。

