# 模板使用说明

遇到问题先用 [问题复盘模板](problem-postmortem.md)记录原因、证据、处理和经验。实际采集与测评先填任务书和协议，再用 CSV 记录过程。所有 CSV **只有表头**，没有示例实验或真实结果；可在表格软件或自己的数据管线中使用。

| 文件 | 一行代表什么 |
|---|---|
| [collection-log.csv](collection-log.csv) | 一次实际录制的 episode，包括失败和中止 |
| [coverage-matrix.csv](coverage-matrix.csv) | 一个预先定义的采集条件格 |
| [evaluation-log.csv](evaluation-log.csv) | 一次测评尝试；重试另开一行 |
| [benchmark-register.csv](benchmark-register.csv) | 一个预先定义的独立 benchmark／协议单元 |

## 字段约定

- ID 使用稳定代号；各表通过 `task_id`、`condition_id`、`episode_id`、`run_id` 等关联。
- 时间字段明确时区；设备原始时间戳和时钟映射保存在数据中，CSV 汇总不替代原始时间序列。
- `outcome` 可使用 `success`、`failure`、`timeout`、`aborted`、`undetermined`；人工介入另记，成功不自动表示自主成功。
- 检查状态区分 `not_checked`（未检测）、`insufficient_evidence`（证据不足）、`confirmed_issue`（已确认异常）、`checked_ok`（在注明的方法与范围内通过）。
- 布尔字段统一用 `true`／`false`；未知值留空并在备注解释，不用 0 代替未知。
- 阶段状态可用 `not_started`、`in_progress`、`complete`、`blocked`，并填写证据引用；未开始阶段没有实际完成进度。
- `valid_for_sft` 需要依据监督目标审核，不能只由 episode 是否保存或是否成功决定。
- `actual_new_fps`、`max_gap_ms` 是实测摘要；完整间隔与同步诊断另存。
- `planned_valid_episodes` 和“该格已覆盖”的数量要求由任务书定义；`valid_episodes` 应来自逐条记录汇总，不能手填计划数冒充实绩。
- `included_in_primary_metric` 与 `exclusion_reason` 按冻结协议填写，同时报告全部尝试；不能因为失败就排除。
- `benchmark-register.csv` 的 `closure_status` 表示证据链是否完成，`performance_acceptance` 另记达标／未达标／待核查。失败结果也可以形成完整测评；成功短片不能替代完整流程。
- `*_uri` 是实际产物引用，不要求公开；公开发布前移除凭证、受限数据和不适合公开的绝对路径。

Markdown 模板： [问题复盘](problem-postmortem.md) · [采集任务书](collection-plan.md) · [测评协议](evaluation-protocol.md) · [实验记录](experiment-record.md)。
