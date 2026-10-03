# 轻眸识刻

> 面向消费者、商超和仓储场景的食品包装日期智能识别原型系统

轻眸识刻聚焦食品包装上微小、模糊、反光或位置不固定的生产日期与保质期信息，尝试通过计算机视觉和日期语义解析，帮助用户更清晰地查看包装标示并完成期限判断。

## 解决的问题

食品包装日期常见于瓶盖、瓶底、封口、袋身边缘或标签角落，容易受到以下因素影响：

- 日期区域面积小，容易被整图文字和包装图案干扰；
- 点阵喷码可能存在断笔、粘连和低对比度；
- 金属、塑料等曲面容易产生反光、褶皱或透视变形；
- 生产日期、有效期、保质期和批号需要进一步区分；
- 信息不完整或识别置信度不足时，需要明确提示人工复核。

典型应用场景包括消费者购买前查验、家庭食品整理，以及商超和仓储场景中的日期巡检。

---

## 核心技术闭环

项目围绕“找得到、读得准、判得清、能改进”展开：

- **找得到**：面向小目标日期区域进行定位检测，减少整图文字干扰；
- **读得准**：对局部日期区域进行增强和受限字符序列识别，针对点阵喷码等场景开展纠错研究；
- **判得清**：聚合生产日期、到期日和保质期等证据，解析日期语义并输出结构化标示状态；
- **能改进**：支持人工纠偏和难例样本回流，为后续模型和规则迭代提供数据基础。

系统规划的处理链路如下：

```text
图像输入 → 日期区域定位 → 局部增强与 OCR
→ 日期语义解析 → 标示期限推导 → 结果展示与人工复核
```

---

## 项目文档

完整的需求、架构、算法方案和跨仓契约集中维护在 [`ProjectPRD`](https://github.com/QingMouFoodDate/ProjectPRD)：

- [项目需求](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/REQUIREMENTS.md)
- [系统架构](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ARCHITECTURE.md)
- [算法研究方案](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/RESEARCH.md)
- [推进路线](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ROADMAP.md)
- [数据模型与接口契约](https://github.com/QingMouFoodDate/ProjectPRD/tree/main/contracts)
- [数据质量规范](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/standards/DATA_QUALITY.md)

---

## 七仓库职责导航

项目按职责拆分为七个相互协作的代码仓库：

| 仓库                                                                | 模块定位       | 主要职责                                 |
| :------------------------------------------------------------------ | :------------- | :--------------------------------------- |
| [`ProjectPRD`](https://github.com/QingMouFoodDate/ProjectPRD)       | 设计与文档中枢 | 需求、架构、算法方案、接口和质量规范     |
| [`TrainPlatform`](https://github.com/QingMouFoodDate/TrainPlatform) | 集成调度训练平台 | 样本资产、数据集版本与切分、标注作业、训练任务调度和模型仓库 |
| [`ModelTrain`](https://github.com/QingMouFoodDate/ModelTrain)       | 算法研发与评测 | 小目标检测、工业 OCR、消融实验和模型导出 |
| [`InferPlatform`](https://github.com/QingMouFoodDate/InferPlatform) | 推理平台       | 模型加载与前向推理、识别会话、证据聚合和标示状态决策 |
| [`WebClient`](https://github.com/QingMouFoodDate/WebClient)         | Web 原型系统   | 多图会话、检测结果展示和人工纠偏         |
| [`MobileClient`](https://github.com/QingMouFoodDate/MobileClient)   | 移动端客户端   | 实拍辅助、离线台账和端侧推理探索         |
| [`WxClient`](https://github.com/QingMouFoodDate/WxClient)           | 微信小程序端   | 轻量查验、大字模式和结果分享             |

---

## 数据与安全边界

项目坚持真实数据、契约先行和渐进式工程原则：

1. 样本以真实食品包装实拍为基础，禁止伪造标签、红圈涂鸦和营销字幕污染；
2. 各端通过统一的 [API 契约](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md)、[数据模型](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md) 和 [模型规约](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md) 协作；
3. 系统输出的是食品包装上的**标示状态**，不替代食品安全检测；
4. 对信息缺失、证据冲突或识别置信度不足的情况，优先提示补拍或人工核对；
5. 项目优先验证单机闭环，再逐步探索移动端、微信小程序和端侧推理等扩展方向。
