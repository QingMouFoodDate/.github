## 变更说明

### 变更类型
- [ ] 契约/规格/Schema 变更
- [ ] 治理脚本/门禁测试
- [ ] 架构文档与工程指南
- [ ] 业务实现（M0/后续阶段）

### 关联问题 / 跨仓配套
- 关联 Issue / PR: 
- 配套 PR:
  - ProjectPRD: 
  - InferPlatform: 
  - WebClient: 
  - data: 

---

## 契约与跨仓影响自查

- [ ] 是否涉及 `ProjectPRD/contracts/` 下的 OpenAPI、JSON Schema 或 Markdown 契约？
- [ ] 若涉及契约修改，是否已同步更新 Python DTO (`InferPlatform/app/schemas/`) 与 TypeScript 类型 (`WebClient/src/types/`)？
- [ ] 是否已在本机执行跨仓对齐检查：`python standards/verify_contracts.py`？
- [ ] 本次改动是否坚守“仅声明包装标示状态，不向用户保证食品绝对可食用”的系统判定边界？

---

## 验证与测试证据

请粘贴本地执行门禁或测试的具体命令与实际输出：

```text
[请在此粘贴测试命令与输出]
```

---

## 回滚与兼容性方案

- [ ] 本次改动向后兼容；
- [ ] 若需回滚，直接 revert 本 PR 无跨仓脏数据或状态滞留风险；
- [ ] 回滚步骤说明：
