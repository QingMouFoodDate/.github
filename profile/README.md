# 轻眸识刻 · QingMouFoodDate

> **基于小目标驱动的食品包装日期智能识别与标示时效推导系统**  
> 南昌大学大学生创新训练计划项目 · 数字化食品安全流通与消费辅助

---

## 核心业务闭环

针对食品包装生产日期普遍存在的**打码微小、曲面反光、点阵断笔、图文干扰**等现实痛点，系统确立“找得到、读得准、判得清、能改进”的技术主线：

- **找得到**：针对微小面积（< 1%）打码区域设计浅层高分辨率特征检测网络，精准定位打码主体；
- **读得准**：构建受限字符集轻量序列识别模型，结合局部自适应增强与断针纠错矩阵，破解断笔点阵识别难题；
- **判得清**：聚合包装生产日期、到期日与保质期多源证据，基于国家标准与日历进位输出客观标示状态；
- **能改进**：前台一键纠偏回流，错误样本沉淀入待审难例池，驱动算法持续微调与自我进化。

---

## 组织仓库矩阵与职责导航

系统按职责严格解耦为 6 个核心代码仓库：

| 仓库 | 模块定位 | 技术栈属性 | 核心职责与关键文档 |
| :--- | :--- | :--- | :--- |
| **[`ProjectPRD`](https://github.com/QingMouFoodDate/ProjectPRD)** | **设计与文档中枢** | Markdown / Docs | 核心需求：[`REQUIREMENTS.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/REQUIREMENTS.md)<br>系统架构：[`ARCHITECTURE.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ARCHITECTURE.md)<br>算法科研：[`RESEARCH.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/RESEARCH.md)<br>推进计划：[`ROADMAP.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ROADMAP.md) |
| **[`TrainPlatform`](https://github.com/QingMouFoodDate/TrainPlatform)** | **业务后端与平台** | Python / Go / DB | 会话编排、多端统一接口、样本资产管理、日期决策引擎 |
| **[`ModelTrain`](https://github.com/QingMouFoodDate/ModelTrain)** | **算法研发与评测** | PyTorch / Python | 小目标检测、点阵OCR、8项消融实验、标准ONNX导出 |
| **[`WebClient`](https://github.com/QingMouFoodDate/WebClient)** | **Web 原型系统** | 前端现代框架 | 大创验收核心成果：多图会话、双重视图、纠偏回流 |
| **[`MobileClient`](https://github.com/QingMouFoodDate/MobileClient)** | **移动端客户端** | Flutter / 原生 | 移动实拍工具、传感器防抖、本地离线台账、端侧推理探索 |
| **[`WxClient`](https://github.com/QingMouFoodDate/WxClient)** | **微信小程序端** | 微信原生 / Taro | 轻量扫码免安装通道、长辈关怀大字模式、微信一键分享 |

---

## 团队工程守则

1. **契约先行**：各端通信严格对齐接口协议 [`contracts/API.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md)、模型规约 [`contracts/MODEL.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md) 与数据模型 [`contracts/DATA.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md)，实现细节互不耦合；
2. **数据零伪造**：样本库 100% 来源于真实包装实拍，严格遵守 [`standards/DATA_QUALITY.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/standards/DATA_QUALITY.md)，一票否决红圈涂鸦、营销大字与虚假数据；
3. **协作规范化**：全域遵循主干分支模型与 Conventional Commits 提交规范，详见 [`standards/ENGINEERING.md`](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/standards/ENGINEERING.md)；
4. **单机闭环优先**：优先在单机多核工作站跑通最小可用闭环（MVP），拒绝过度分布式设计；
5. **渐进式演进**：立项承诺核心（C0）确保 100% 验收，工程增强（C1）与科学消融（C2）有序推进。
