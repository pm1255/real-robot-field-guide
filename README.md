# 真机采集与测评问题手册

面向 Piper 入门者及具身后训练工程实践的中文知识库。先把相机、动作、标定、录制与部署约定对齐，再用独立真机评测决定补数据还是改训练和执行方式。

当前整理 **6 类、30 个问题条目**，提供采集、实验和测评模板，以及文章、代码与视频索引。条目来自公开复盘和通用工程建议，**不表示某台机器人已发生这些故障，也不代表我们复现了来源中的实验**。

## 从这里开始

1. 初次接触 Piper：读 [Piper 入门与接线](docs/piper-start.md)，弄清电脑、机械臂、相机和遥操设备分别做什么。
2. 准备第一次采集：按 [采集→训练→测评流程](docs/workflow.md)建立一条能回读、能追溯的短轨迹。
3. 想看实操：按 [视频学习路线](resources/videos.md)观看中文分集，再看长课的采集与评测章节。
4. 遇到现场问题：在 [30 项问题索引](docs/problem-index.md)找现象，再提交现场问题 Issue。
5. 准备扩大任务：填写 [采集任务书](templates/collection-plan.md)和 [测评协议](templates/evaluation-protocol.md)，使用 [benchmark 台账](templates/benchmark-register.csv)跟踪各阶段。

## 问题分类

| 分类 | 编号 | 主要解决什么 | 专题讨论 |
|---|---|---|---|
| [相机与标定](docs/camera-and-calibration.md) | CAM-01～05 | 相机移动、裁剪遮挡、标定丢失、换硬件 | [专题 #1](https://github.com/pm1255/real-robot-field-guide/issues/1) |
| [遥操与动作接口](docs/teleoperation-and-actions.md) | TEL-01～05 | 鼠标如何控制、关节／末端动作、开始与成功键 | [专题 #2](https://github.com/pm1255/real-robot-field-guide/issues/2) |
| [采集与存储](docs/capture-and-storage.md) | IO-01～05 | USB 身份、掉线、实际帧率、写盘与中断 | [专题 #3](https://github.com/pm1255/real-robot-field-guide/issues/3) |
| [数据质量与覆盖](docs/data-quality-and-coverage.md) | DATA-01～05 | 覆盖与密度、示范一致性、恢复、标签和切分 | [专题 #4](https://github.com/pm1255/real-robot-field-guide/issues/4) |
| [训练与部署](docs/training-and-deployment.md) | RUN-01～05 | loss、动作变换、推理延迟、公平比较和版本 | [专题 #5](https://github.com/pm1255/real-robot-field-guide/issues/5) |
| [真机测评](docs/evaluation.md) | EVAL-01～05 | 成功定义、多次试验、人工介入、回放与证据 | [专题 #6](https://github.com/pm1255/real-robot-field-guide/issues/6) |

## 学习资料

- [文章、官方与社区代码](resources/articles-and-code.md)：优先读三篇第一手复盘，再按硬件选接口参考。
- [视频与逐次评测记录](resources/videos.md)：区分全流程课程、短演示和带失败样例的评测资料。
- [结构化来源目录](resources/sources.json)：记录核对日期、硬件、核对深度、适用范围和限制。
- [RLinf 固定版本源码清单](resources/rlinf-source-manifest.json)：公开链接和哈希；不将当前主分支与固定版本混为一谈。

视频大多只核对页面信息或公开章节，没有完整观看。150 次公开评测记录已核对数据卡与行数，没有逐个审片或独立审计结果。详见 [证据等级与引用规则](docs/evidence-levels.md)。

## 模板与维护

| 用途 | 模板 |
|---|---|
| 定义采集条件、设备和有效示范 | [采集任务书](templates/collection-plan.md) · [逐条采集记录](templates/collection-log.csv) · [覆盖矩阵](templates/coverage-matrix.csv) |
| 预先固定成功标准与测试条件 | [测评协议](templates/evaluation-protocol.md) · [逐次测评记录](templates/evaluation-log.csv) |
| 比较数据或训练方案 | [实验记录](templates/experiment-record.md) |
| 跟踪多个 benchmark 的完整闭环 | [benchmark 台账](templates/benchmark-register.csv) |

CSV 仅有表头，未填入虚构的实验结果。模板是字段建议，需映射到实际录制器的数据结构。

欢迎在 [Issues](https://github.com/pm1255/real-robot-field-guide/issues)提交现场问题、资料推荐或实验记录；填写时区分已观测现象、原因假设和已验证结论。提交规则见 [CONTRIBUTING.md](CONTRIBUTING.md)，常用词见 [术语表](docs/glossary.md)。

本仓库整理的是知识和模板，没有启动机械臂、采集、训练或评估任务。公开整理检查见 [report_summary.md](report_summary.md)。原创文档和模板采用 [MIT License](LICENSE)，外部资料的权利和许可归原作者。
