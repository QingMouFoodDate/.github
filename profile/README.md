# 轻眸识刻

> 面向消费者、商超和仓储场景的食品包装日期智能识别原型系统
>
> **当前处于需求与架构设计阶段，M0 单图闭环待实现。** 各仓设计不能证明代码、测试、部署或模型已经交付，具体实现状态须以代码、测试和发布记录核验。

轻眸识刻聚焦食品包装上微小、模糊、反光或位置不固定的生产日期与保质期信息，规划以计算机视觉和日期语义解析帮助用户查看包装标示。系统输出的是**食品包装标示状态**，不替代食品安全检测，不保证食品可食用；性能和准确度需要实际评测，不能由设计目标推断。

## 解决的问题

包装日期可能位于瓶盖、瓶底、封口或标签角落，受到小目标、点阵断笔、曲面反光与背景文字干扰；还需区分生产日期、到期日、保质期和批号。信息缺失、证据冲突或低置信度时应明确提示复核，而不是给出未经证据支持的结论。

## 阶段与技术主线

当前优先验证 Web M0：**创建会话 -> 上传单图 -> 查看原图检测框、OCR、证据和 Decision**，该链路待实现。多图、完整结果展示、手工纠偏与审核回流属于 C0 后续，文本或框修正不是 M0 前置条件。MobileClient、WxClient 仅为后续规划、工程暂缓，不代表所有客户端已经运行。

规划的数据主线：

```text
客户端图片 -> InferPlatform -> 内部 Inference Runtime 检测与 OCR
-> Observation -> InferPlatform 聚合 Evidence、生成 Decision -> 客户端展示
```

- **找得到、读得准**：研究小目标定位、局部增强和受限字符 OCR，效果仍需基线与实验验证。
- **判得清**：InferPlatform 按日期规则输出在期 / 临期 / 超期 / 无法判定，并独立提供证据完备 / 信息缺失 / 证据冲突 / 低置信度四种复核状态。推理失败不是“无法判定”，必须明确报错。
- **能改进**：C0 规划契约内纠偏；合法纠偏接受后立即更新当前 Decision，成为训练候选另需 TrainPlatform 质量审核，不自动修改线上模型。当前 `correction.v1` 仅定义生产日期、到期日、保质期（value + DAY/MONTH/YEAR 单位）与保存条件修正；原始 OCR 文本和框修正尚未在 v1 定义。

机器 Observation 来自 Runtime，不由客户端提交或改写；平台返回完整、版本化 Observation、Evidence、Decision 安全 DTO。客户端不计算日期业务规则，也不通过重算剩余天数改变业务结果。摘要结果、图像 variants、跨端继续处理和服务端订阅任务需要未来独立契约，不宣称已有接口能力。

## 七项目仓职责导航

组织保持 **8 仓：以下 7 个项目仓 + [`.github`](https://github.com/QingMouFoodDate/.github) 组织配置仓**，不新增、合并或重命名仓库。下表说明设计职责，不代表实现完成。

| 项目仓 | 设计职责与阶段 |
| :--- | :--- |
| [ProjectPRD](https://github.com/QingMouFoodDate/ProjectPRD) | 需求、架构、跨仓契约、质量规范与架构决策的事实源 |
| [TrainPlatform](https://github.com/QingMouFoodDate/TrainPlatform) | 内部样本资产、数据集版本/切分、标注审核、训练调度、模型仓库与血缘 |
| [ModelTrain](https://github.com/QingMouFoodDate/ModelTrain) | 由 TrainPlatform 调度的算法训练、评测与标准模型包导出 |
| [InferPlatform](https://github.com/QingMouFoodDate/InferPlatform) | 对外业务 API、识别会话、内部推理运行时、证据聚合与标示状态决策 |
| [WebClient](https://github.com/QingMouFoodDate/WebClient) | M0 单图优先入口，待实现；C0 后续多图、完整展示与契约内纠偏 |
| [MobileClient](https://github.com/QingMouFoodDate/MobileClient) | 后续拍摄/传感器辅助、弱网任务、本地记录与通知；C3 端侧探索，工程暂缓 |
| [WxClient](https://github.com/QingMouFoodDate/WxClient) | 后续大字结果、家庭分享与授权订阅探索，工程暂缓 |

**Inference Runtime 是 InferPlatform 内部逻辑模块，不是独立仓库，也不是第 9 仓。** TrainPlatform 不承载客户端查验 API。端侧探索需具备授权数据、模型和设备验证条件；跨端会话接续与订阅服务契约尚未实现，不承诺无缝迁移或提醒送达。

## 文档与接口事实源

产品定位、范围与架构统一查阅：

- [ProjectPRD README](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/README.md)
- [REQUIREMENTS](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/REQUIREMENTS.md) 与 [ARCHITECTURE](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ARCHITECTURE.md)
- [API](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md) 与 [DATA](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md)
- [DATE_RULES](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATE_RULES.md)、[MODEL](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md) 与 [TRAINING](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/TRAINING.md)
- [decisions/ADR-001-REPOSITORY_BOUNDARIES.md](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/decisions/ADR-001-REPOSITORY_BOUNDARIES.md)

DATE_RULES、TRAINING、ADR-001、OpenAPI 与四份 JSON Schema 已纳入 ProjectPRD，均仍为候选或设计依据。接口描述是契约目标，不是已上线服务：创建 `POST /api/v1/sessions`，上传 `POST /api/v1/sessions/{session_id}/images`，查询 `GET /api/v1/sessions/{session_id}`；纠偏 `POST /api/v1/sessions/{session_id}/correction` 属 C0 后续。`GET /api/v1/models/latest` 仅供 Mobile 的 C3 端侧探索，不是 M0 依赖。

## 访问、隐私与发布边界

- 创建会话返回 `session_token`，后续会话请求使用 `Authorization: Bearer`，写操作使用 `Idempotency-Key`；令牌安全持有，不分享、不日志、不放 URL。请求失败不能显示 success。
- 图片与纠偏记录不自动成为训练数据，需授权与质量审核；不公开内部资产或凭证，不承诺尚未验证的功能。
- 当前 GitHub 仓库为 **private**，上述导航与文档链接需要相应访问权限，不保证所有访客可访问。
- 本文件是组织主页内容源，不证明已发布。GitHub 自动显示公开组织主页需组织的 `.github` 仓库公开，且默认分支包含 `profile/README.md`；默认分支不必是 `main`，本地编辑不等于主页已更新。
