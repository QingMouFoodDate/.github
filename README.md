# 组织全局配置

> 维护 [QingMouFoodDate](https://github.com/QingMouFoodDate) 组织的公开主页展示与全局规范配置。

---

## 目录结构

```text
.github/
├── README.md          # 仓库运维说明
├── .github/workflows/ # 可复用契约门禁
└── profile/
    └── README.md      # 组织公开主页源文件（由 GitHub 引擎直接渲染于组织首页）
```

- **主页源码**：[`profile/README.md`](profile/README.md)
- **线上主页**：[github.com/QingMouFoodDate](https://github.com/QingMouFoodDate)
- **契约工作流**：[reusable-contract-check.yml](.github/workflows/reusable-contract-check.yml)，负责安装中央校验依赖并执行对应语言门禁；配置存在不代表线上已运行通过。
- **当前边界**：M0 尚未准出，完整视觉 Runtime、真实模型包与 Web UI 待交付；主页不能将设计目标写成已取得的成绩。

---

## 维护规范

1. **内容收敛**：对外展示内容统一在 [`profile/README.md`](profile/README.md) 中维护。
2. **隐私脱敏**：严禁提交本地私有绝对路径、密钥凭证或未脱敏样本。
3. **状态求真**：主页所列工程状态必须与实际研发进展严格同步。
4. **自动生效**：变更经审查合入 `main` 分支后，GitHub 组织首页自动同步更新。
