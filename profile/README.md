# 轻眸食期

> 小目标驱动的食品包装日期智能识别方法研究
>
> 面向真实食品包装场景的小尺度日期文本检测与轻量化识别方法，构建面向消费者、商超与仓储场景的智能识别原型系统。
>
> **工程状态**：M0 单图闭环待实现 · Web 优先 · 移动端与微信端暂缓

轻眸食期聚焦食品包装上微小、模糊、反光及位置任意的生产日期与保质期信息，通过计算机视觉、字符识别与日期语义解析技术，辅助用户辨析包装标示并完成期限判定。

---

## 核心挑战

包装日期是核对标示期限的参考，不足以证明食品安全。但在实际场景中，日期常以小字号或低对比度喷码印制在瓶盖、瓶底、封口或折角处。包装材质反光、软包褶皱变形、字符断笔粘连及复杂装潢背景，导致辨识难度极高，给视力退化的老年人及视障群体带来显著障碍。

本项目聚焦非受控实拍环境下的五大工程挑战：

- **目标微小且背景干扰大**：日期区域面积占比极低，易被整包装图文装饰与说明干扰；
- **印刷退化与点阵字符粘连**：喷码工艺常存在断笔、粘连、墨迹晕染及低对比度褪色；
- **物理形变与非受控成像**：金属与塑料曲面易反光，软包装易发生褶皱扭曲与透视变形；
- **多字段混杂与语义歧义**：生产日期、有效截止日、保质期时长（如“常温保存12个月”）与批号混排，需准确解耦；
- **置信度度量与人机协同复核**：针对残损、模糊等边缘样本，需量化置信度并提供人工复核兜底。

**应用场景**：涵盖消费者购买查验、家庭食品临期管理，以及商超零售与仓储物流效期巡检。

---

## 技术闭环

以下是待端到端验证的设计流程，不是已取得的识别或可靠性成绩：

- **区域定位**：构建小目标日期专用检测模型，快速抑制复杂背景干扰；
- **文本识别**：针对点阵喷码与退化字符，评估自适应增强与训练侧字表的识别收益；
- **语义推导**：抽取生产日期、到期日与保质期，完成效期状态智能推导；
- **复核与回流**：基于置信度区分可靠决策与疑难样本，支持人机协同复核与闭环回流。

```mermaid
flowchart LR
    A["图像输入"] --> B["日期区域定位"]
    B --> C["局部增强与 OCR"]
    C --> D["日期语义解析"]
    D --> E["标示期限推导"]
    E --> F["结果展示与人工复核"]
```

---

## 项目文档

核心设计、架构与跨仓契约集中维护于 [`ProjectPRD`](https://github.com/QingMouFoodDate/ProjectPRD) 仓库：

- [需求规格](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/需求规格.md)
- [系统架构](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/系统架构.md)
- [算法实验体系](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/experiments/README.md)
- [研究现状](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/研究现状.md)
- [推进路线](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/开发路线.md)
- [数据模型与接口契约](https://github.com/QingMouFoodDate/ProjectPRD/tree/main/contracts)
- [数据质量规范](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/standards/数据质量规范.md)

---

## 仓库导航

项目包含八个系统仓（含文档仓和 .github）及独立受控数据仓 data；职责划分不代表八仓均已实现：

| 仓库                                                                | 模块定位         | 主要职责                                                              |
| :------------------------------------------------------------------ | :--------------- | :-------------------------------------------------------------------- |
| [`ProjectPRD`](https://github.com/QingMouFoodDate/ProjectPRD)       | 需求与契约规范   | 需求、架构、算法方案、接口和质量规范                                  |
| [`TrainPlatform`](https://github.com/QingMouFoodDate/TrainPlatform) | 集成调度训练平台 | 样本资产、数据集版本与切分、标注作业、训练任务调度和模型仓库          |
| [`ModelTrain`](https://github.com/QingMouFoodDate/ModelTrain)       | 算法研发与评测   | 小目标检测、工业 OCR、消融实验和模型导出                              |
| [`InferPlatform`](https://github.com/QingMouFoodDate/InferPlatform) | 推理平台         | 识别会话、证据聚合与标示状态决策，完整视觉 Runtime 尚待实现 |
| [`WebClient`](https://github.com/QingMouFoodDate/WebClient)         | Web 原型系统     | 优先实现单图识别与双重视图，多图会话和人工纠偏按 C0 推进              |
| [`MobileClient`](https://github.com/QingMouFoodDate/MobileClient)   | 移动端客户端     | 实拍辅助、离线台账和端侧推理探索                                      |
| [`WxClient`](https://github.com/QingMouFoodDate/WxClient)           | 微信小程序端     | 轻量查验、大字模式和结果分享                                          |
| [`data`](https://github.com/QingMouFoodDate/data)                   | 数据集与质检门禁 | 数据清单、标注治理、防泄漏切分与质量检查  |
| [`.github`](https://github.com/QingMouFoodDate/.github)             | 组织主页配置     | 项目介绍、仓库导航与公开展示维护                                      |

---

## 安全边界

项目遵循“真实数据、契约先行、渐进落地”原则：

1. **真实数据基准**：严禁伪造标签与营销修图，实行真实原图规范管理（100% SHA-256 唯一），严格遵循 8:1:1 科学分层防泄漏切分。
2. **多端契约协同**：各端严格依循统一的 [API 契约](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md)、[数据模型](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md) 与 [模型规约](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md) 进行跨仓解耦。
3. **标示状态界定**：系统输出仅代表包装客观标示状态，明确不替代专业理化或生物学食品安全检测。
4. **置信度与复核**：信息缺失不等于超期；对置信度不足或证据冲突样本提示人工复核或补拍，起算依据不明时不主观补全。
5. **渐进迭代节奏**：首期聚焦 Web 单图 M0 闭环验证，移动端与微信端暂缓，端侧离线轻量化部署待独立评估。

---

## 本地协作与克隆拓扑

团队开发采用并排多仓工作区拓扑（非 git 子模块或单一巨石仓）：

```text
QingMouFoodDate/
├── ProjectPRD/      # 需求与契约规范
├── InferPlatform/   # 在线服务与契约 DTO（开发就绪）
├── WebClient/       # Web 交互原型（契约类型对齐）
├── MobileClient/    # 移动端规划仓
├── WxClient/        # 小程序规划仓
├── ModelTrain/      # 算法与实验仓
├── TrainPlatform/   # 训练平台调度仓
├── data/            # 数据集真值、切分与质量门禁仓
└── .github/         # 组织主页配置与公用工作流
```

新成员并行克隆各子仓至同一工作区，统一使用 Python 3.12 运行各仓基础门禁，在遵守各端接口契约的前提下开展分工。

---

## 项目引用

如本课题的方法研究、数据集组织方案或原型系统对您的工作有所启发，欢迎引用：

### GB/T 7714

```text
林方魁, 吕宇轩, 韩天阳, 首雯彬, 彭琨. 轻眸识刻：小目标驱动的食品包装日期智能识别方法研究[R/OL]. 2026. https://github.com/QingMouFoodDate. (指导教师: 林振荣)
```

### BibTeX

```bibtex
@misc{lin2026qingmou,
  title        = {轻眸识刻：小目标驱动的食品包装日期智能识别方法研究 (QingMouFoodDate)},
  author       = {林方魁 and 吕宇轩 and 韩天阳 and 首雯彬 and 彭琨},
  howpublished = {\url{https://github.com/QingMouFoodDate}},
  note         = {指导教师: 林振荣},
  year         = {2026}
}
```
