# 问题索引

先找现象，再按详情页收集证据。下表的“影响”是问题真实存在时的影响，不是对某个工位的检测结论。

| 编号 | 问题／常见现象 | 主要影响 | 详情 |
|---|---|---|---|
| CAM-01 | 外部相机或机器人底座挪动 | 输入视角变化，旧数据适用性需复核 | [排查与验证](camera-and-calibration.md#cam-01) |
| CAM-02 | 腕部相机支架松动或重装 | 相机相对手腕关系改变 | [排查与验证](camera-and-calibration.md#cam-02) |
| CAM-03 | 预览正常，保存后看不清目标 | 裁剪、缩放、遮挡丢失任务信息 | [排查与验证](camera-and-calibration.md#cam-03) |
| CAM-04 | 校准文件丢失或加载错版本 | 角度／坐标映射可能不一致 | [排查与验证](camera-and-calibration.md#cam-04) |
| CAM-05 | 换夹爪、换相机或重标定后退化 | 旧数据、模型与新装配不一定兼容 | [排查与验证](camera-and-calibration.md#cam-05) |
| TEL-01 | 机械臂能遥操，但没有有效数据 | 控制链路与录制链路没有完整连接 | [排查与验证](teleoperation-and-actions.md#tel-01) |
| TEL-02 | 鼠标／手柄输出与环境动作不匹配 | 末端增量不能直接作为绝对关节角 | [排查与验证](teleoperation-and-actions.md#tel-02) |
| TEL-03 | 方向、幅度或夹爪行为不对 | 单位、顺序、坐标和归一化混用 | [排查与验证](teleoperation-and-actions.md#tel-03) |
| TEL-04 | 不知道按什么开始、成功或中止 | 轨迹边界与标签不明确 | [排查与验证](teleoperation-and-actions.md#tel-04) |
| TEL-05 | 启动、复位、松手或退出时行为异常 | 默认目标和保持语义未验证 | [排查与验证](teleoperation-and-actions.md#tel-05) |
| IO-01 | 重启后腕部与桌面画面互换 | 动态设备编号导致身份错配 | [排查与验证](capture-and-storage.md#io-01) |
| IO-02 | USB 设备消失、重连或图像断流 | 供电、带宽、线缆或驱动链路不稳定 | [排查与验证](capture-and-storage.md#io-02) |
| IO-03 | 写着 30 FPS，数据却重复或错位 | 实际时序与元信息不一致 | [排查与验证](capture-and-storage.md#io-03) |
| IO-04 | 一录制，遥操就变慢 | 相机或写盘阻塞控制循环 | [排查与验证](capture-and-storage.md#io-04) |
| IO-05 | 中断后仍显示采集完成 | 尾部数据、索引或视频不完整 | [排查与验证](capture-and-storage.md#io-05) |
| DATA-01 | 数据条数很多，只会少数摆放 | 有效覆盖不足或覆盖范围过稀 | [排查与验证](data-quality-and-coverage.md#data-01) |
| DATA-02 | 同类场景下动作犹豫或不一致 | 示范质量、风格或隐藏条件冲突 | [排查与验证](data-quality-and-coverage.md#data-02) |
| DATA-03 | 一旦抓偏就重复失败 | 缺少可控偏差下的正确恢复示范 | [排查与验证](data-quality-and-coverage.md#data-03) |
| DATA-04 | 成功标签不可靠或轨迹切断过早 | 监督目标和真正任务完成不一致 | [排查与验证](data-quality-and-coverage.md#data-04) |
| DATA-05 | 离线指标很好，换天／换物体就差 | 相邻帧或同场景泄漏到测试集 | [排查与验证](data-quality-and-coverage.md#data-05) |
| RUN-01 | loss 很低，真机仍然失败 | 拟合指标不能代表闭环成功 | [排查与验证](training-and-deployment.md#run-01) |
| RUN-02 | 离线预测像对的，部署动作不对 | 转换、归一化、mask 或逆变换错误 | [排查与验证](training-and-deployment.md#run-02) |
| RUN-03 | 动作段之间停顿或执行滞后 | 推理、通信、chunk 执行方式不匹配 | [排查与验证](training-and-deployment.md#run-03) |
| RUN-04 | 无法判断加数据还是换方法有效 | 比较时多个变量同时改变 | [排查与验证](training-and-deployment.md#run-04) |
| RUN-05 | 昨天能复现，今天找不到对应版本 | 数据、标定、代码、权重缺少关联 | [排查与验证](training-and-deployment.md#run-05) |
| EVAL-01 | 短视频看似成功，验收却不通过 | 成功定义或保持时间未预先约定 | [排查与验证](evaluation.md#eval-01) |
| EVAL-02 | 两模型测试条件不同 | 起点、场景、预算或任务范围不一致 | [排查与验证](evaluation.md#eval-02) |
| EVAL-03 | 只报一个成功率，介入和重试不明 | 分母与不确定性不可判断 | [排查与验证](evaluation.md#eval-03) |
| EVAL-04 | 回放能完成，被当成自主成功 | 数据回放与闭环自主控制混淆 | [排查与验证](evaluation.md#eval-04) |
| EVAL-05 | 宣称完成 benchmark，证据却不全 | 缺少逐次记录及阶段产物关联 | [排查与验证](evaluation.md#eval-05) |

现场严重程度需按具体任务判断：先处理会改变动作含义、造成异常运动或毁损记录的问题；再处理吞吐和泛化。定位中保留“已观测”“待核查”“已验证”状态，不能仅凭现象认定根因。
