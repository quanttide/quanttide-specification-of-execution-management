# 清单`List`

执行记忆的归属主体——一个清单就是一个次级法人：有自己的身份（id）、名字（name）、和一份独立于任何人的执行记忆（tasks）。公司是顶层法人，清单可层层嵌套对齐业务结构。

## 字段

- `id`: 必选，唯一标识（uuid）。
- `name`: 必选，清单名。
- `tasks`: 本法人的执行记忆（Task 数组）。
- `outcomes`: 可选，本清单产生的结果（Outcome.id 数组），清单层面的交付汇总。

## JSON 示例

```json
{
  "id": "5f0c9a1e-3d4b-4e8f-9a2c-1b7d6e5f4a3c",
  "name": "量潮数据",
  "tasks": [
    "7c9e6679-7425-40de-944b-e07fc1f90ae7",
    "2a4b6c8d-1e3f-4a5b-9c0d-8e7f6a5b4c3d"
  ],
  "outcomes": [
    "9b2f8c3d-1a4e-4f5b-8c6d-7e0a9b1c2d3e"
  ]
}
```
