# 《轻眸识刻》组织全局配置库

> **仓库定位**：`QingMouFoodDate` 组织级特殊配置仓库，托管组织公开主页与全局规范。

---

## 一、 目录结构

```text
.github/
├── README.md                      # 仓库内部配置说明文档
└── profile/                       # 组织官方主页展示内容目录
```

- **`profile/README.md`**：组织公开主页的内容源文件，由 GitHub 官方引擎直接解析并展示于 [github.com/QingMouFoodDate](https://github.com/QingMouFoodDate)。

---

## 二、 组织主页维护指引

1. **修改源文件**：组织主页如有更新，直接编辑本仓库下的 `profile/README.md`；
2. **规范对齐**：主页内容需与 `ProjectPRD` 保持一致，重点展示核心业务主线、6 仓矩阵与工程守则；
3. **实时生效**：改动合并推送到 `main` 分支后，组织公开主页将秒级自动同步更新。
