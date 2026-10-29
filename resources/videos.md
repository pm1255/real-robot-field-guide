# 视频学习路线

中文分集适合先建立工作流程，英文长课的公开目录覆盖校准、遥操、采集、训练和评测；想看多次成功与失败，参考独立的逐次评测视频集。它们主要是 SO-ARM／SO-101，不是已经验证的 Piper 全流程。

核对日期：2026-10-29。以下视频没有完整观看；“已核对”通常表示页面信息或公开章节，具体范围见 [sources.json](sources.json)。

<a id="v01-v04"></a>
## V01～V04 中文分集：先看这四集

作者：矽递科技 SeeedStudio；页面发布日期：2025-11-25；总时长 **34 分 53 秒**。

| 编号 | 视频 | 时长 | 建议学习重点 |
|---|---|---|---|
| V01 | [5 校准及遥操作](https://www.bilibili.com/video/BV1w6UUBcEGR/) | 10:47 | 输入设备、人如何控制真实机器人、反馈 |
| V02 | [6 添加摄像头](https://www.bilibili.com/video/BV1r6UUBFE8r/) | 05:06 | 设备身份、画面与视角 |
| V03 | [7 搭建实验场景及采集数据](https://www.bilibili.com/video/BV1r6UUBFEzq/) | 10:05 | 工位、摆放、录制与保存 |
| V04 | [8 训练及部署](https://www.bilibili.com/video/BV1r6UUBFEz2/) | 08:55 | 数据到训练、部署的关系 |

[课程合集](https://space.bilibili.com/3546665994685307/channel/collectiondetail?sid=6825772)还有前置环境与组装内容。已核对页面标题、作者、日期、时长及列表；部分页面有登录／试看限制，没有逐段确认具体操作。表中是建议观察点，不是未经观看的逐段内容结论。

看完建议产物：画出自己的连接图，填好相机身份、动作定义、录制事件和任务结果四项；硬件参数仍以 Piper 方案为准。

<a id="v05"></a>
## V05 英文长课：公开目录覆盖采集与评测

[Train an ACT Policy for the SO-101 Robot with LeRobot](https://www.youtube.com/watch?v=-tkEMLOLEwo)，Trelis Research，索引时长 **1:45:19**。

公开章节通过视频索引与 [Class Central 课程目录](https://www.classcentral.com/course/youtube-train-an-act-policy-for-the-so-101-robot-with-lerobot-468669)交叉核对：

| 时间 | 目录所列内容 | 跳转 |
|---|---|---|
| 08:53 | 校准 | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=533) |
| 12:33 | 遥操 | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=753) |
| 27:10 | 录制与管理数据 | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=1630) |
| 39:05 | 训练 ACT | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=2345) |
| 01:27:04 | 模型评测 | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=5224) |
| 01:28:37 | 回放与评测 | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=5317) |
| 01:35:21 | 泛化与数据需求 | [观看该章节](https://www.youtube.com/watch?v=-tkEMLOLEwo&t=5721) |

播放页访问超时，未获取字幕，也未完整观看。因此可称为“目录覆盖全流程的学习候选”，不能称为已验证的未经剪辑采集与多次验收录像。

<a id="v06"></a>
## V06 中文长课候选

[LeRobot训练SO-101机械臂ACT模型全流程解析](https://www.bilibili.com/video/BV1enHizcEk6/)，GPUS 开发者，2025-09-11，**1:01:53**。

已核对页面、简介和时长。未完整观看，不能根据“全流程”标题保证包含完整数据采集或多次真机测试；观看时建议用 [工作流程](../docs/workflow.md)逐项做笔记。

<a id="v07"></a>
## V07 Piper 短演示

[【开源】松灵piper集成lerobot](https://www.bilibili.com/video/BV16H9BYDEva/)，茄子们大喊人类，2025-03-04，**1:05**。

页面简介提到单手柄遥操数采并链接 [lerobot_piper](articles-and-code.md#c02)。适合建立直觉，不是完整采集与评测课程；未完整观看，也未定位演示代码的兼容版本。再结合 [D02 Piper 手柄教程](articles-and-code.md#d02)看输入映射。

<a id="e01"></a>
## E01 看真正逐次记录：150 次 SO-101 评测

[V1-LeRobot-SO101-Eval-Videos](https://huggingface.co/datasets/cons909/V1-LeRobot-SO101-Eval-Videos)，作者 cons909。

已阅读数据卡并确认预览显示 **150 行**。作者报告三种相机配置各 50 次，附视频、逐次结果、延迟、停止原因和检查点等记录，包含成功与失败；可配合 [E02 协议](articles-and-code.md#e02)学习怎样归档。

- [作者标注的成功样例](https://huggingface.co/datasets/cons909/V1-LeRobot-SO101-Eval-Videos/resolve/main/1cam/videos/trial_007_side.mp4)
- [作者标注的失败样例](https://huggingface.co/datasets/cons909/V1-LeRobot-SO101-Eval-Videos/resolve/main/1cam/videos/trial_004_side.mp4)

这里没有逐个审看全部视频或独立审计标签。作者说明多相机配置每次只发布一个视角；配置间检查点步数不同，不能据结果推断增加相机的纯因果收益，也不能当作 Piper 的性能承诺。

## 推荐观看顺序

中文分集建立流程 → Piper 资料明确硬件差异 → 长课采集与评测章节 → 逐次成功／失败记录 → 回到自己的采集任务书和测评协议。

展示片适合理解动作；判断可靠性还要看未经挑选的尝试、失败、等待、人工介入及分母。

## 擦黑板示教的核对说明

[双臂 Piper 擦黑板案例](../docs/blackboard-wiping.md#wipe-task-and-video)另外记录了一段受限训练示教的观察：约 20.27 秒，抽看八个时刻的关键帧，左臂固定边框、右臂擦拭并放回板擦。没有核实到自主策略运行、成功标签或月报试次对应；淡白残留是否合格也缺原 SOP 判据。

原片与截图未取得公开许可，因此不附下载地址，也不计入上述 7 个公开视频教程／演示。本段只说明观察内容和证据边界，来源范围见 F03 的 [结构化记录](sources.json)。
