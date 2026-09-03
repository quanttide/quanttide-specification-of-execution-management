# 量潮执行管理标准

核心领域模型：**List**（清单/次级法人）× **Task**（任务）× **Outcome**（结果），任务通过 uuid 引用**Executor**（执行者）

本领域模型由 quanttide-execute-toolkit 承载（JSON 契约定义）：三个业务实体 + 一个引用实体：

- **List**：一个次级法人——有自己的身份、名字和一份独立于任何人的执行记忆（tasks）
- **Task**：法人需要记住的一件执行——它是什么、做到哪一步、优先级多高、属于哪个方面
- **Outcome**：任务产生的结果——独立领域模型，承载交付结论，是下一环节的输入
- **Executor**：执行者（负责人/复核人的引用目标）——只有 id 与 label，暂靠人工维护，不绑定账户系统

## 设计原则

**List 管归属，Task 管执行。**

- 执行记忆的主体是**法人**（公司为顶层法人，可层层嵌套；一个清单 = 一个次级法人），不归属于任何自然人——自然人参与推进，不拥有记忆
- Task 必须同时具备**负责人与复核人**（交付规则见执行管理章程）——复核通过构成下一环节的输入，任务交付结果因此得以流转
- Task 的**标题与描述**遵循简洁明确原则：描述必须能回答做什么、为什么、怎样算完成（书写规则见执行管理章程第二、三章）

## 实体

### List（清单/次级法人）

```
List {
  id: uuid           # 唯一标识
  name: string       # 清单名
  tasks: Task[]      # 本法人的执行记忆
}
```

### Task（任务）

```
Task {
  id: uuid           # 唯一标识
  list_id: uuid      # → List.id，归属的次级法人
  title: string      # 标题（动作 + 对象）
  description: text  # 描述（做什么/为什么/怎样算完成）
  priority: enum     # 优先级
  owner_id: uuid     # 负责人（→ Executor，执行者）
  reviewer_id: uuid  # 复核人（→ Executor，执行者）
  start_at: datetime # 开始时间，可选
  due_at: datetime   # 截止时间，可选
  completed_at: datetime # 完成时间（status 进入 done 时回填），可选
  status: enum       # 状态
  outcome_ids: uuid[] # → Outcome.id，产生的结果（多对多），可选
  created_at: datetime # 创建时间（系统生成）
  updated_at: datetime # 更新时间（系统生成，每次变更刷新）
}
```

### Outcome（结果）

```
Outcome {
  id: uuid       # 唯一标识
  task_ids: uuid[] # → Task.id，关联的任务（多对多），可选
  title: string  # 标题（结果的一句话概括）
  description: text # 描述（交付了什么/验收依据/对下一环节的意义）
}
```

### Executor（执行者）

```
Executor {
  id: uuid      # 唯一标识
  label: string # 展示名（姓名/称呼）
}
```

## 子文档

- [list.md](list.md) — List 字段语义与 JSON 示例
- [task.md](task.md) — Task 字段语义与 JSON 示例
- [outcome.md](outcome.md) — Outcome 字段语义与 JSON 示例
- [executor.md](executor.md) — Executor 字段语义与维护规则
