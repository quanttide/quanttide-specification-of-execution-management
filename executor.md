# 执行者`Executor`

任务的参与主体——负责人（owner_id）与复核人（reviewer_id）都是执行者。

## 字段

- `id`: 必选，唯一标识（uuid）。
- `label`: 必选，展示名（姓名/称呼）。

## 维护规则

- 执行者只有身份与名字，**暂不绑定账户系统**，靠人工维护。
- 未来接入账户系统时，在此字段集上演进，不改动 Task 的引用方式（Task 只持有 `owner_id`/`reviewer_id`）。

## JSON 示例

```json
{
  "id": "b3d3486a-19de-4f0d-8f6e-2a5c4b6d7e8f",
  "label": "张三"
}
```
