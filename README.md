# 轻眸识刻组织主页配置

本仓维护 QingMouFoodDate 组织主页内容，不承载业务 API、模型推理、训练或客户端工程。

项目保持 **8 仓：7 个项目仓 + `.github` 组织配置仓**，不新增、合并或重命名仓库。Inference Runtime 是 InferPlatform 内部逻辑模块，不是独立仓库，也不形成第 9 仓。

当前处于需求与架构设计阶段，**M0 单图闭环待实现**。各仓设计文档不能证明代码、测试、部署或模型已经交付；MobileClient、WxClient 仅为后续规划，工程暂缓。

## 目录结构

```text
.github/                           # 组织配置仓库
├── README.md                      # 维护规则与主页展示条件
└── profile/                       # 组织主页内容目录
    └── README.md                  # 主页内容源文件，不是发布证明
```

## 主页维护与展示条件

1. 内容统一维护在 [`profile/README.md`](profile/README.md)，保留真实阶段声明、七项目仓导航与契约入口，不复制完整 PRD 或承诺未实现功能。
2. GitHub 自动展示组织公开主页的条件是：组织拥有**公开的 `.github` 仓库**，且其**默认分支**包含 `profile/README.md`。默认分支不必叫 `main`，本地修改或文档链接不能证明已发布。
3. 发布需由有权限的维护者确认仓库可见性、实际默认分支与文件位置；公开前检查敏感信息。本地文档变更不代表已推送或已自动更新主页。
4. 当前 GitHub 仓库为 private，仓库及文档链接需要相应访问权限，不保证所有访客可访问。保留导航不等于将仓库公开，也不绕过访问控制。
5. 主页不得包含本地数据路径、数据规模或脚本完成状态；不得将模型示例指标、规划目标或接口定义写成实测成果。食品包装标示状态不是食品安全结论。

## 统一事实源

产品与职责以 [ProjectPRD README](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/README.md)、[REQUIREMENTS](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/REQUIREMENTS.md)、[ARCHITECTURE](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ARCHITECTURE.md) 为准；契约以 [API](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md)、[DATA](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md)、[DATE_RULES](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATE_RULES.md)、[MODEL](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md)、[TRAINING](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/TRAINING.md) 为准；仓库边界见 [ADR-001](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/decisions/ADR-001-REPOSITORY_BOUNDARIES.md)。

DATE_RULES、TRAINING、ADR-001、OpenAPI 与四份 JSON Schema 已纳入 ProjectPRD，均仍为候选或设计依据；组织配置仓只引用，不重复定义。链接中的分支需由维护者按目标仓实际情况核对。
