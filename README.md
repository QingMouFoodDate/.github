# 轻眸识刻组织主页配置

本仓维护 QingMouFoodDate 组织主页内容，不承载业务 API、模型推理、训练或客户端工程。

项目保持 **8 仓：7 个项目仓 + `.github` 组织配置仓**，不新增、合并或重命名仓库。Inference Runtime 是 InferPlatform 内部逻辑模块，不独立建仓。

当前处于需求与架构设计阶段，**M0 单图闭环推进中**。MobileClient、WxClient 作为后续规划储备，工程暂缓。

## 目录结构

```text
.github/                           # 组织配置仓库
├── README.md                      # 维护规则与主页展示条件
└── profile/                       # 组织主页内容目录
    └── README.md                  # 主页内容源文件
```

## 主页维护与展示条件

1. 内容统一维护在 [`profile/README.md`](profile/README.md)，保留阶段声明、七项目仓导航与契约入口，不承诺未实现功能。
2. GitHub 组织公开主页生效条件：`.github` 仓库公开且默认分支包含 `profile/README.md`（不限 `main` 分支）。本地修改不代表已发布。
3. 发布由维护者确认仓库可见性、默认分支与文件位置；公开前核验敏感信息。
4. 当前仓库为 private，访问需相应权限；保留导航不等于公开仓库。
5. 主页严禁包含本地私有路径或未脱敏数据；不得将规划目标写成实测成果。系统输出严格限定为包装标示状态，不作食品安全结论。

## 统一事实源

产品与职责以 [ProjectPRD README](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/README.md)、[REQUIREMENTS](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/REQUIREMENTS.md)、[ARCHITECTURE](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/ARCHITECTURE.md) 为准；跨仓契约以 [API](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md)、[DATA](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md)、[DATE_RULES](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATE_RULES.md)、[MODEL](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md)、[TRAINING](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/TRAINING.md) 为准；仓库边界见 [ADR-001](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/decisions/ADR-001-REPOSITORY_BOUNDARIES.md)。

OpenAPI 与四份 JSON Schema 已纳入 ProjectPRD 作为设计依据；组织配置仓仅引用，不重复定义。
