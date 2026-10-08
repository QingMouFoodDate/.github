# 轻眸识刻组织主页配置

本目录维护 QingMouFoodDate 组织的公开主页内容和全局展示配置。

---

## 目录结构

```text
.github/
├── README.md          # 组织配置说明
└── profile/           # 组织公开主页内容
```

- [`profile/README.md`](profile/README.md)：组织公开主页的内容源文件，由 GitHub 官方引擎解析并展示在组织主页。

## 主页维护指引

1. 组织主页内容统一维护在 [`profile/README.md`](profile/README.md)；
2. 主页只展示适合公开访问的项目介绍、仓库导航和技术文档入口；
3. 仓库面向全网公开，严禁写入本地私有路径、绝对磁盘地址或未脱敏数据；
4. 遵循实事求是原则，如实标示当前阶段为“M0 原型研发”；
5. 修改后合并推送到 `main` 分支，GitHub 组织主页将自动同步更新。
