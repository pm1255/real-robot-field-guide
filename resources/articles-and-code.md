# 文章、文档与代码

本页保留支撑分析的原始来源。先看本仓库的 [原因与经验总结](../docs/causes-and-lessons.md)和 [案例复盘](../docs/case-studies.md)，再按引用查原文与代码。公开经验不是 Piper 环境的兼容性测试；固定版本源码也没有经过本仓库真机执行。

核对日期：2026-10-29。逐条核对范围见 [sources.json](sources.json)，核对深度说明见 [证据规则](../docs/evidence-levels.md)。

<a id="d03"></a>
## D03 RoboDojo 官方真机任务列表

[Real Robot Tasks](https://robodojo-benchmark.com/doc/real-tasks/)。已核对当日公开原文：Piper X、Piper、ARX X5 各 6 项，共 18 项，不包含擦黑板。结论只针对该公开版本，不排除历史或未公开任务集；采用 RoboDojo-real 数据接口不能单独证明任务被官方收录。对应 [擦黑板任务归属核对](../docs/blackboard-wiping.md#wipe-task-and-video)，任务路径摘要见 [证据记录](blackboard-evidence.json)。

## 先读的第一手复盘

<a id="a01"></a>
### A01 Sherry Chen：ACT／SO-101 的失败与改进

[How I Trained Action Chunking Transformer (ACT) on SO-101: My Journey, Gotchas, and Lessons](https://huggingface.co/blog/sherryxychen/train-act-on-so-101)，2025-09-30。

**建议关注：** 相机位置变化、关节校准文件与错误重标定、USB 设备识别、随机摆放留下覆盖空洞、示范精度与独立评测。已阅读原文相关叙述。

**范围：** 作者的 SO-101／ACT 个案。原帖主要丢失的是关节校准文件，不是所有相机标定；相同型号／身份难区分不能单独证明物理断流根因。

<a id="a02"></a>
### A02 ggando：SmolVLA／SO-101 数据迭代

[Fine-tuning SmolVLA for Cube Pick-and-Place on SO-101](https://ggando.com/blog/smolvla-so101/)，2026-03-01。

**建议关注：** 任务范围与示范密度、不同抓取技巧混用、夹爪及标定变化、USB 2.0 链路、相机 I/O 阻塞遥操，以及腕部／外部视角。已阅读原文。

**范围：** 多轮实验同时改变多个因素，不能推导单因素因果，也不能把作者条数作为所有任务的数据预算。

<a id="a03"></a>
### A03 ML6：模仿学习的团队实机复盘

[AI Robotics: A Field Report on Imitation Learning with LeRobot](https://www.ml6.eu/en/blog/ai-robotics-a-field-report-on-imitation-learning-with-lerobot)，Robin Dehullu／ML6；2025-11-27 发布，2025-12-02 更新。

**建议关注：** SO-100 上 ACT 与 GR00T-N1 的任务经验，为什么 loss 不等于闭环成功、精度与恢复覆盖、推理及网络停顿。已阅读原文。

**范围：** 不是统一跨模型基准。文章明确披露部分 GR00T 展示省略了推理等待，不能用剪辑后的顺滑程度估计真实耗时。

<a id="a04"></a>
### A04 AMD：π0 采集、微调与部署教程

[Fine-tuning Robotics Vision Language Action Models with AMD ROCm and LeRobot](https://rocm.blogs.amd.com/artificial-intelligence/rocm-lerobot/README.html)，2025-07-14。

**建议关注：** Koch 主从机械臂、双相机示范、设备映射、π0 微调和部署的整体链路。已阅读原文。

**范围：** Koch／π0／AMD ROCm，不是 Piper／π0.5／RLinf。文章中的 Phoenix 指 AMD 电脑平台，同名不能证明是另一个模型项目。

## 图文入门与 Piper 资料

<a id="d01"></a>
### D01 Seeed：SO-ARM 全流程图文

[LeRobot SO-ARM 教程](https://wiki.seeedstudio.com/lerobot_so100m_new/)。已阅读校准与遥操相关章节，特别关注使用相同 robot ID 加载相应标定。

适合串起安装、校准、遥操和录制概念；SO-ARM 的校准动作、端口和参数不能照搬 Piper。配套视频见 [V01～04](videos.md#v01-v04)。

<a id="d02"></a>
### D02 松灵社区：Piper 手柄遥操

[手柄遥操机械臂——直观的机械臂控制新体验](https://bbs.agilex.ai/d/55-手柄遥操机械臂直观的机械臂控制新体验)，松灵机器人账号，2025-12-08。已阅读完整可见帖子。

适合看手柄、关节／位姿模式、夹爪、虚拟与真机入口的区别。START 是模式切换，A 是位置保存；这不是任意采集器的开始与成功键，也不能证明已接通 RLinf 录制器。

<a id="c01"></a>
### C01 Gamepad_PiPER

[kehuanjack/Gamepad_PiPER](https://github.com/kehuanjack/Gamepad_PiPER)，D02 关联仓库。已核对仓库存在、简介和默认 main 分支；没有执行代码或验证与 RLinf 的版本兼容性。

<a id="c02"></a>
### C02 lerobot_piper

[brucecai-2001/lerobot_piper](https://github.com/brucecai-2001/lerobot_piper)，[V07 短演示](videos.md#v07)关联仓库。核对时默认 main 显示通用 LeRobot README，未定位演示的具体 Piper 分支／提交；作为线索保留，不当作已验证安装方案。

<a id="c04"></a>
### C04 pyAgxArm 官方驱动

[agilexrobotics/pyAgxArm](https://github.com/agilexrobotics/pyAgxArm)。已核对官方仓库、简介和默认 master 分支；具体型号、固件和适配器兼容性应继续读厂商文档，本仓库未安装或测试 SDK。

## RLinf 公开代码入口

<a id="c03"></a>
### C03 固定版本的采集与 Piper 接口

参考提交：[91a302ec50ddacd1fdabc5859b85e3661d768236](https://github.com/RLinf/RLinf/tree/91a302ec50ddacd1fdabc5859b85e3661d768236)。七个公开源文件已下载核对，SHA256 与大小见 [清单](rlinf-source-manifest.json)。未执行代码，不代表当前主分支状态或真机可用性。

| 入口 | 用来理解什么 |
|---|---|
| [collect_data.sh](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/examples/embodiment/collect_data.sh) | 通用采集启动层 |
| [collect_real_data.py](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/examples/embodiment/collect_real_data.py) | 创建环境、遥操与采集循环 |
| [realworld_collect_data.yaml](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/examples/embodiment/config/realworld_collect_data.yaml) | 格式、输出和任务等配置；默认示例不是 Piper 完整任务 |
| [collect_episode.py](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/rlinf/envs/wrappers/collect_episode.py) | 轨迹边界与保存；需区分不同模式的行为 |
| [Piper 环境 base.py](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/rlinf/envs/real/piper/base.py) | 动作、观测、遥操声明和复位 |
| [Piper 驱动 piper.py](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/rlinf/robotics/parts/arms/piper.py) | 关节和夹爪命令与反馈 |
| [piper_reach.yaml](https://github.com/RLinf/RLinf/blob/91a302ec50ddacd1fdabc5859b85e3661d768236/examples/embodiment/config/env/piper_reach.yaml) | Piper 示例环境，包含 `teleop: none` |

读代码时分别回答：动作来自哪里、发给什么接口、保存了什么、何时标记结果、初始化和退出有什么副作用。详细解释见 [Piper 入门](../docs/piper-start.md)和 [遥操问题库](../docs/teleoperation-and-actions.md)。

## 逐次评测协议参考

<a id="e02"></a>
### E02 SO-101 Evaluation Protocol

[cons909 的评测协议](https://github.com/cons909/V1-LeRobot-SO101-Learning-by-Demonstration-SmolVLA/blob/main/docs/EVALUATION_PROTOCOL.md)，由 [E01 数据卡](videos.md#e01)链接。可进一步学习逐次记录形式；本次只核对链接，未逐条审计协议全文，也不把其参数作为通用验收标准。
