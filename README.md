# .github

> 维护 [QingMouFoodDate](https://github.com/QingMouFoodDate) 组织的公开主页展示与跨仓可复用 CI 门禁配置。

---

## 一、目录结构与核心职责

```text
.github/
├── README.md                     # 组织级配置仓库运维说明
├── .gitignore                    # Git 忽略与云盘防冲突规则
├── .gitattributes                # 跨平台纯 LF 换行约束
├── .pre-commit-config.yaml       # 提交前自动化门禁配置
├── .github/
│   ├── PULL_REQUEST_TEMPLATE.md  # 组织级统一合并请求与五道门禁核验模板
│   └── workflows/
│       └── reusable-contract-check.yml # 跨仓可复用契约与质量门禁工作流
└── profile/
    └── README.md                 # 组织公开主页源文件，由 GitHub 引擎直接渲染于组织首页
```

- **主页源码**：[`profile/README.md`](profile/README.md)
- **线上主页**：[github.com/QingMouFoodDate](https://github.com/QingMouFoodDate)
- **可复用契约工作流**：[reusable-contract-check.yml](.github/workflows/reusable-contract-check.yml)，供 `ProjectPRD`、`InferPlatform`、`WebClient` 等仓库在 GitHub Actions 中统一调用 `contracts.py` 进行跨语言契约校验；
- **当前工程边界**：M0 单图闭环与 v2.0 双阶段算法深化、多图聚合、字段级人工纠偏、双栏核验工作台及 Android 混合容器均已完成封板；v3.0 正推进端侧量化引擎、C++ 微批次 Worker 池 SLA 攻坚、全站 HTTPS 切换与微信小程序端落地。

---

## 二、维护准则

1. **内容收敛**：对外公开展示内容统一在 [`profile/README.md`](profile/README.md) 中维护，遵守知识产权“先申请、后公开”保密原则；
2. **隐私脱敏**：严禁提交本地私有绝对路径、服务器密钥凭证或未脱敏样本；
3. **状态求真**：主页所列工程状态必须与实际研发进展严格同步，严禁将规划目标写为已验收成绩；
4. **自动生效**：变更经审查合入 `main` 分支后，GitHub 组织首页自动同步更新。
