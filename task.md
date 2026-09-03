# Task（任务）

法人需要记住的一件执行——它是什么、做到哪一步、优先级多高、属于哪个方面。

## 字段

- `id`: 必选，唯一标识（uuid）。
- `list_id`: 必选，→ List.id，归属的次级法人。
- `title`: 必选，标题（动作 + 对象，一个标题一件事，禁止无信息量标题）。
- `description`: 必选，描述须回答三问：做什么 / 为什么 / 怎样算完成（可验证的验收口径）；流转中的关键信息（口径变更、结论、交付物链接）追加于此，保持任务卡是这项执行的完整记忆。
- `priority`: 必选，优先级（约定档位；原始信息无信号时默认最低档，由负责人确认）。
- `owner_id`: 必选，负责人——对任务的执行与交付负责；执行者（Executor）的 uuid。
- `reviewer_id`: 必选，复核人——对任务交付结果进行评审验收；执行者（Executor）的 uuid。
- `started_at`: 可选，开始时间（原始信息无时不虚构，留空由交办人确认）。
- `due_at`: 可选，截止时间（原始信息无时不虚构，留空由交办人确认）。
- `completed_at`: 可选，完成时间（status 进入 done 时回填）。
- `status`: 必选，状态（按看板泳道：如 created / in_progress / reviewing / done）。
- `outcome_ids`: 可选，→ Outcome.id 数组，任务产生的结果。**多对多**（与 Outcome.task_ids 对称）。
- `created_at`: 必选，创建时间（系统生成）。
- `updated_at`: 必选，更新时间（系统生成，每次变更刷新）。

## JSON 示例

```json
{
  "id": "7c9e6679-7425-40de-944b-e07fc1f90ae7",
  "list_id": "5f0c9a1e-3d4b-4e8f-9a2c-1b7d6e5f4a3c",
  "title": "整理客户面板口径确认单",
  "description": "做什么：产出二期指标口径确认文件（变量定义、算例、边界条件）。为什么：第一版策划书曾因口径误解返工。怎样算完成：客户书面确认算例与边界条件。",
  "priority": "high",
  "owner_id": "b3d3486a-19de-4f0d-8f6e-2a5c4b6d7e8f",
  "reviewer_id": "c4e4597b-20ef-4a1e-9a7f-3b6d5c7e8f9a",
  "started_at": "2026-09-05",
  "due_at": "2026-09-10",
  "completed_at": null,
  "status": "in_progress",
  "outcome_ids": [
    "9b2f8c3d-1a4e-4f5b-8c6d-7e0a9b1c2d3e"
  ],
  "created_at": "2026-09-03T09:30:00+08:00",
  "updated_at": "2026-09-03T15:20:00+08:00"
}
```
