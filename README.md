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

| 维护维度 | 规范准则与生效要求 | 维护红线与注意事项 |
| :--- | :--- | :--- |
| **主页内容源** | 统一维护于 `profile/README.md` | 严禁复制冗长 PRD 全文，仅保留核心架构与导航入口 |
| **生效前置条件** | `.github` 仓库公开（Public）且默认分支包含主页文件 | 默认分支不必为 `main`，本地单机修改不等于已公开生效 |
| **公开安全边界** | 仓库面向全网公开，任何人均可访问 | 严禁写入本地私有路径、绝对磁盘地址或未脱敏的数据信息 |
| **成果宣传准则** | 遵循实事求是原则，如实标示当前阶段为“M0 原型研发” | 严禁将规划目标或示例指标伪装成已经跑通的实测成果 |

系统输出严格限定为包装标示状态，不作食品安全结论。

## 统一事实源

产品与职责以 [ProjectPRD README](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/README.md)、[需求规格](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/需求规格.md)、[系统架构](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/系统架构.md) 为准；跨仓契约以 [contracts/API.md](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/API.md)、[contracts/DATA.md](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/DATA.md)、[日期推导规则](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/日期推导规则.md)、[contracts/MODEL.md](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/MODEL.md)、[contracts/TRAINING.md](https://github.com/QingMouFoodDate/ProjectPRD/blob/main/contracts/TRAINING.md) 为准。

OpenAPI 与四份 JSON Schema 已纳入 ProjectPRD 作为设计依据；组织配置仓仅引用，不重复定义。
