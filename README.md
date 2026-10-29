# 真机采集、后训练与测评：问题原因与经验总结

本仓库沉淀前面讨论的真机问题：**发生了什么、为什么会发生、证据支持什么、怎样处理与验证、下次应记住什么。** 面向 Piper 入门者与具身后训练工程实践，学习资料用于支撑这些分析和结论。

核心内容包括 **10 项讨论结论、6 类 30 个基础问题、8 项擦黑板现场专题、3 篇公开实战复盘与 1 篇现场材料整理**。公开作者报告、受限材料核对、通用机制与待验证原因分别注明；尚未对用户的 Piper 做现场验证。

## 先看这些结论

| 讨论的问题 | 原因与经验结论 | 完整分析 |
|---|---|---|
| 数据最重要，为什么脚本还会影响性能？ | 字段、配对、采样和优化决定数据如何被利用；先查语义，再比较方法 | [AN-01](docs/causes-and-lessons.md#an-01) |
| 为什么 loss 很低仍然抓空？ | 离线平均误差没有直接测量多阶段闭环成功，偏差还会累积 | [AN-01](docs/causes-and-lessons.md#an-01) |
| 相机挪一点、腕部相机移动有什么区别？ | 相机安装关系与预处理改变会改变输入分布；腕部正常随动另作区分 | [AN-02](docs/causes-and-lessons.md#an-02) |
| 校准文件丢失为什么影响旧模型？ | 重新加载或标定可能改变角度／坐标含义，先核对实际映射 | [AN-03](docs/causes-and-lessons.md#an-03) |
| USB 掉线、画面互换和卡顿是什么原因？ | 分别定位身份绑定、传输与处理吞吐，处理方法不同 | [AN-04](docs/causes-and-lessons.md#an-04) |
| Linux、转换器和线缆分别做什么？ | 控制、相机与供电是不同链路，转换器不会自动接通录制 | [AN-05](docs/causes-and-lessons.md#an-05) |
| 鼠标怎样控制？适配是否等于逆动力学？ | 输入意图需转换为环境接受的动作，末端转关节常涉及逆运动学 | [AN-06](docs/causes-and-lessons.md#an-06) |
| 开始和成功键在哪里？能遥操为什么没采到？ | 控制、录制事件、保存和任务结果分别实现，逐条回读验收 | [AN-07](docs/causes-and-lessons.md#an-07) |
| 数据越多、范围越大，覆盖是否越好？ | 独立条件、有效密度和关键组合决定覆盖；按失败分布补采 | [AN-08](docs/causes-and-lessons.md#an-08) |
| RLinf 开源后还差什么？ | 核对具体版本的硬件、遥操、任务、数据与部署集成，区分 SFT 和在线 RL | [AN-09](docs/causes-and-lessons.md#an-09) |
| 怎样确认性能提升、benchmark 完成？ | 固定协议、保留全部尝试，将完整流程与性能达标分开记录 | [AN-10](docs/causes-and-lessons.md#an-10) |

完整入口：[原因分析与经验总结](docs/causes-and-lessons.md)。第一次搭建可接着看 [Piper 入门](docs/piper-start.md)与 [采集→训练→测评流程](docs/workflow.md)。

## 新增现场案例：双臂 Piper 擦黑板

[完整复盘：故障定位、处理与评测](docs/blackboard-wiping.md)把本次讨论合并为八项问题：

| 问题 | 主要经验与结论 |
|---|---|
| [过热掉臂、甩臂](docs/blackboard-wiping.md#wipe-01) | 对齐硬件状态、目标、IK 与实测反馈；DLS 不独立证明热问题已解决 |
| [求解慢与动作停顿](docs/blackboard-wiping.md#wipe-03) | 分开计时模型、网络、IK 和队列，记录预测步数与执行步数 |
| [倾斜压持与右臂死角](docs/blackboard-wiping.md#wipe-04) | 先分清倾斜方式、滑移、离面、可达性与覆盖，再针对原因处理 |
| [37/70 相机槽位异常](docs/blackboard-wiping.md#wipe-06) | 按 episode 修正映射；跨 episode 错位不证明单条录像中途切换 |
| [夹爪二值化与 0/1 还原](docs/blackboard-wiping.md#wipe-07) | 区分主手命令和从手开度；只有二值标签时无法恢复全部连续意图 |
| [EEF-rel 参考与旋转](docs/blackboard-wiping.md#wipe-08) | 核对固定参考、rot6d 排列、左右臂、有效维度和分段执行 |

另含 [SOP 与提采](docs/blackboard-wiping.md#wipe-sop)、[流程](docs/blackboard-wiping.md#wipe-workflow)、[已有质检的证据边界](docs/blackboard-wiping.md#wipe-quality-checks)，以及 [RoboDojo 任务归属与示教／评测视频区别](docs/blackboard-wiping.md#wipe-task-and-video)。月报成绩和 DLS 修复陈述未独立复验；公开版不分发受限原始材料，见 [证据摘要](resources/blackboard-evidence.json)。

## 公开实战中的问题怎样发生

- [CS-01 Sherry Chen](docs/case-studies.md#cs-01)：相机变化、错误重标定和采集分布空洞，怎样同时影响 ACT。
- [CS-02 ggando](docs/case-studies.md#cs-02)：为什么更多示范仍可能抓空，夹爪变化和采集阻塞又怎样影响数据。
- [CS-03 ML6](docs/case-studies.md#cs-03)：为什么低 loss、展示顺滑和真实闭环成功需要不同证据。

每篇复盘区分作者报告、机制解释和结论边界；各轮多因素变化时不把结果归因于单一调整。

## 分类问题库：30 项基础问题与现场专题

| 分类 | 编号 | 主要解决什么 | 专题讨论 |
|---|---|---|---|
| [相机与标定](docs/camera-and-calibration.md) | CAM-01～05 | 相机移动、裁剪遮挡、标定丢失、换硬件 | [专题 #1](https://github.com/pm1255/real-robot-field-guide/issues/1) |
| [遥操与动作接口](docs/teleoperation-and-actions.md) | TEL-01～05 | 鼠标如何控制、关节／末端动作、开始与成功键 | [专题 #2](https://github.com/pm1255/real-robot-field-guide/issues/2) |
| [采集与存储](docs/capture-and-storage.md) | IO-01～05 | USB 身份、掉线、实际帧率、写盘与中断 | [专题 #3](https://github.com/pm1255/real-robot-field-guide/issues/3) |
| [数据质量与覆盖](docs/data-quality-and-coverage.md) | DATA-01～05 | 覆盖与密度、示范一致性、恢复、标签和切分 | [专题 #4](https://github.com/pm1255/real-robot-field-guide/issues/4) |
| [训练与部署](docs/training-and-deployment.md) | RUN-01～05 | loss、动作变换、推理延迟、公平比较和版本 | [专题 #5](https://github.com/pm1255/real-robot-field-guide/issues/5) |
| [真机测评](docs/evaluation.md) | EVAL-01～05 | 成功定义、多次试验、人工介入、回放与证据 | [专题 #6](https://github.com/pm1255/real-robot-field-guide/issues/6) |

每项均包含现象与影响、**原因分析、处理与验证、经验总结**及来源；[总表](docs/problem-index.md)同时收录 30 项基础问题与 WIPE-01～08 擦黑板专题，可直接按原因查找。

## 把现场问题继续沉淀为经验

记录现象 → 列原因假设及支持／反对证据 → 记录处理与验证 → 形成有适用范围的结论 → 更新分类条目。

使用 [问题复盘模板](templates/problem-postmortem.md)或 [现场问题表单](https://github.com/pm1255/real-robot-field-guide/issues/new?template=01-field-issue.yml)。原因未验证时保留待核查；修复后写清验证结果和后续预防办法。

## 模板与维护

| 用途 | 模板 |
|---|---|
| 沉淀问题原因、处理过程和经验结论 | [问题复盘](templates/problem-postmortem.md) |
| 定义采集条件、设备和有效示范 | [采集任务书](templates/collection-plan.md) · [逐条采集记录](templates/collection-log.csv) · [覆盖矩阵](templates/coverage-matrix.csv) |
| 预先固定成功标准与测试条件 | [测评协议](templates/evaluation-protocol.md) · [逐次测评记录](templates/evaluation-log.csv) |
| 比较数据或训练方案 | [实验记录](templates/experiment-record.md) |
| 跟踪多个 benchmark 的完整闭环 | [benchmark 台账](templates/benchmark-register.csv) |

CSV 仅有表头，未填入虚构的实验结果。模板是字段建议，需映射到实际录制器的数据结构。

## 辅助学习与引用来源

- [文章、官方与社区代码](resources/articles-and-code.md)：为问题分析提供原始出处。
- [视频与逐次评测记录](resources/videos.md)：辅助理解操作和证据记录。
- [23 条结构化来源记录](resources/sources.json)：20 条公开资料与 3 条受限材料说明，保留核对范围及限制。
- [擦黑板证据摘要](resources/blackboard-evidence.json)：区分月报摘录、只读源码／旧日志、示教关键帧与官方任务列表。
- [RLinf 固定版本源码清单](resources/rlinf-source-manifest.json)：公开链接与哈希。

公开视频多只核对页面或章节；擦黑板受限示教抽看八个时刻的关键帧，没有作为全片或自主成功录像审计。150 次公开评测只核对数据卡与规模，没有逐条审片。详见 [证据规则](docs/evidence-levels.md)。

欢迎在 [Issues](https://github.com/pm1255/real-robot-field-guide/issues)提交现场问题、资料推荐或实验记录；填写时区分已观测现象、原因假设和已验证结论。提交规则见 [CONTRIBUTING.md](CONTRIBUTING.md)，常用词见 [术语表](docs/glossary.md)。

本仓库整理的是知识和模板，没有启动机械臂、采集、训练或评估任务。公开整理检查见 [report_summary.md](report_summary.md)。原创文档和模板采用 [MIT License](LICENSE)，外部资料的权利和许可归原作者。
