# 30 项问题：现象、原因与经验总结

本表把前面讨论的问题落到原因机制和可复用经验。原因摘要用于指导判断，不能代替现场证据；详情页列出检查、处理、验证与出处。

先读 [十项核心分析](causes-and-lessons.md)及 [公开实战复盘](case-studies.md)，再按具体条目排查。

| 编号 | 问题／常见现象 | 原因机制摘要 | 经验总结 | 详情 |
|---|---|---|---|---|
| CAM-01 | 外部相机或底座挪动 | 安装关系变化导致输入分布改变 | 装配、预处理与数据一起留版本 | [详细分析](camera-and-calibration.md#cam-01) |
| CAM-02 | 腕部相机支架变化 | 支架变化改变相机—手腕关系 | 用相同姿态核对腕部基准画面 | [详细分析](camera-and-calibration.md#cam-02) |
| CAM-03 | 预览清楚，训练输入却丢信息 | 预处理或遮挡丢失关键任务信息 | 检查最终输入及关键阶段 | [详细分析](camera-and-calibration.md#cam-03) |
| CAM-04 | 校准文件丢失或加载错误 | 查找失败与实际映射改变混淆 | 标定版本关联数据与硬件 | [详细分析](camera-and-calibration.md#cam-04) |
| CAM-05 | 换硬件或重标定后继续用旧数据 | 装配与数值的物理对应关系改变 | 旧数据先分版，再验证复用 | [详细分析](camera-and-calibration.md#cam-05) |
| TEL-01 | 能遥操，不代表能录制 | 控制和记录是分别实现的链路 | 用完整短轨迹验收采集 | [详细分析](teleoperation-and-actions.md#tel-01) |
| TEL-02 | 末端输入与关节动作不匹配 | 输入动作空间与环境接口不同 | 先定义语义，再完成映射 | [详细分析](teleoperation-and-actions.md#tel-02) |
| TEL-03 | 单位、关节顺序与夹爪映射错误 | 维度相同但单位或字段含义不同 | 逐层记录动作契约与反馈 | [详细分析](teleoperation-and-actions.md#tel-03) |
| TEL-04 | 开始、成功、中止按键不明确 | 模式和事件映射未明确 | 逐个验证开始、结果与停止事件 | [详细分析](teleoperation-and-actions.md#tel-04) |
| TEL-05 | 初始化、复位与保持行为未验证 | 默认目标与保持语义混用 | 核对状态转换及真实副作用 | [详细分析](teleoperation-and-actions.md#tel-05) |
| IO-01 | 重启后相机身份改变 | 动态枚举编号无法稳定表示身份 | 绑定身份，并逐台确认画面 | [详细分析](capture-and-storage.md#io-01) |
| IO-02 | 真实断流、设备重连与 USB 链路问题 | 传输链路存在多个候选瓶颈 | 分环节取证，再验证具体处理 | [详细分析](capture-and-storage.md#io-02) |
| IO-03 | 实际 FPS、时序与观测动作配对不符 | 名义频率与真实时序分离 | 验证时间配对，不只填 FPS | [详细分析](capture-and-storage.md#io-03) |
| IO-04 | 录制 I/O 阻塞遥操 | 阻塞处理或队列积压拖慢控制 | 同时检查延迟与数据完整性 | [详细分析](capture-and-storage.md#io-04) |
| IO-05 | 中断、磁盘满与残缺 episode | 结束事件先于持久化完成 | 以回读完整性确认有效条数 | [详细分析](capture-and-storage.md#io-05) |
| DATA-01 | 条数多，但覆盖不足或太稀 | 独立条件不足或组合样本过稀 | 覆盖与密度一起统计 | [详细分析](data-quality-and-coverage.md#data-01) |
| DATA-02 | 示范风格冲突或精度不足 | 隐藏技巧差异或示范动作不准确 | 规范示范并保留可区分条件 | [详细分析](data-quality-and-coverage.md#data-02) |
| DATA-03 | 缺少恢复示范 | 执行偏差进入未覆盖恢复状态 | 补正确恢复，保留接管边界 | [详细分析](data-quality-and-coverage.md#data-03) |
| DATA-04 | 标签与结束边界不可靠 | 结果事件与真实完成条件不一致 | 标签绑定物理结果与尾部证据 | [详细分析](data-quality-and-coverage.md#data-04) |
| DATA-05 | 数据切分与测试泄漏 | 相关样本泄漏或测试被反复调参 | 按泛化目标分组留出 | [详细分析](data-quality-and-coverage.md#data-05) |
| RUN-01 | loss 低，但真机成功率差 | 离线平均误差没有直接测闭环成功 | 分开报告拟合与任务结果 | [详细分析](training-and-deployment.md#run-01) |
| RUN-02 | 数据转换、归一化或 mask 不一致 | 跨阶段变换或有效维度约定不一致 | 检查自洽及真实物理含义 | [详细分析](training-and-deployment.md#run-02) |
| RUN-03 | 推理延迟与动作段衔接不合适 | 观测变旧及动作执行时序不匹配 | 分别评估推理与执行收益 | [详细分析](training-and-deployment.md#run-03) |
| RUN-04 | 多变量变化，无法判断什么有效 | 多因素混杂及选择规则不同 | 固定基线，限制因果归因 | [详细分析](training-and-deployment.md#run-04) |
| RUN-05 | 数据、权重和现场版本无法对应 | 产物与版本缺少稳定关联 | 用实验 ID 贯通证据链 | [详细分析](training-and-deployment.md#run-05) |
| EVAL-01 | 成功定义不明确 | 成功标准含糊或观察不足 | 预先定义结果与观察要求 | [详细分析](evaluation.md#eval-01) |
| EVAL-02 | 模型之间条件不一致 | 方法差异与测试条件混杂 | 固定协议和条件后比较 | [详细分析](evaluation.md#eval-02) |
| EVAL-03 | 分母、重试、介入与不确定性不清楚 | 尝试筛选、分母或介入语义不清 | 逐次留档并可重算汇总 | [详细分析](evaluation.md#eval-03) |
| EVAL-04 | 回放与自主闭环测评混淆 | 固定动作执行与实时决策混淆 | 区分回放与自主闭环 | [详细分析](evaluation.md#eval-04) |
| EVAL-05 | benchmark 缺少闭环证据 | 阶段和完成标准未定义 | 流程完成与性能达标分开 | [详细分析](evaluation.md#eval-05) |

优先处理会改变动作含义、引起异常运动或毁损记录的问题，再处理吞吐和泛化。结论区分“已观测”“原因待核查”“已验证”，按 [问题复盘模板](../templates/problem-postmortem.md)记录具体证据和适用范围。
