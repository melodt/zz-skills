# Configuration

仓库可选 `.code-skeleton.yml`。未配置的字段使用自动检测，再回退到 skill 默认值。用户当前参数优先于所有配置。

```yaml
version: 1
paths:
  specs: [spec, docs/spec]
  tickets: [tickets, docs/tickets]
  designs: [design, docs/design]
outputs:
  plan: docs/implementation-plan.md
  manifest: .code-skeleton/manifest.json
  runs: .code-skeleton/runs
verification:
  layers: [syntax, unit, build]
  timeout_seconds: 120
adapters:
  - typescript
todo_kinds:
  - business-logic
  - integration
  - validation
  - design-gap
  - manual-decision
```

配置只描述路径、适配器、验证和输出等机械规则。它不能覆盖必需输入、冲突处理、安全边界、ticket 范围或用户当前指令。
