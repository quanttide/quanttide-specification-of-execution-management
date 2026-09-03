# Changelog

本文件记录 **执行管理领域模型规格（quanttide-specification-of-execution-management）** 的版本变更。

## [0.1.0] - 2026-09-03

### Added

- 领域模型规格首版：**List**（清单/次级法人）× **Task**（任务）× **Outcome**（结果）三个业务实体 + **Executor**（执行者，引用实体）
- Task 完整字段：id / list_id / title / description / priority / owner_id / reviewer_id / started_at / due_at / completed_at / status / is_active / outcome_ids / created_at / updated_at
- Task ↔ Outcome 多对多关联（outcome_ids ↔ task_ids，对称）；Outcome 承载任务交付结论（title/description），复核通过构成下一环节的输入
- Executor 只有 id + label，暂靠人工维护，不绑定账户系统
- Task.is_active 软归档：False 不进看板不再流转，仍可被 Outcome 引用备查
- 各实体字段语义、交付规则、JSON 示例（合法 uuid）
