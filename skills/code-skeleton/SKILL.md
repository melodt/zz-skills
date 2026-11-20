---
name: code-skeleton
description: 根据已确认的 spec、tickets 和详细设计生成可编译、可验证、可继续实现的代码骨架。用户明确要求搭建实现骨架、从设计开始落代码结构，或执行 code-skeleton 时使用；不用于替代需求分析、详细设计或直接完成全部业务逻辑。
metadata:
  version: "1.0.0"
---

# Code Skeleton

把已确认的 `spec`、tickets 和详细设计转成可继续实现的代码骨架。默认先做 `plan`，只有用户明确要求执行或指定 `--apply` 才写入工作区。自然语言与 `--spec`、`--design`、`--tickets`、`--ticket`、`--plan`、`--dry-run`、`--apply`、`--verify` 均按相同流程解释；这些是对话参数，不代表提供了 CLI。

## 运行顺序

1. 读取适用的 `AGENTS.md`、用户指定文档、仓库配置和相关代码。优先使用 CodeGraph / codebase-memory-mcp 理解符号关系；图谱不可用时读取具体文件。
2. 按“用户指令 > 详细设计 > ticket 验收标准 > spec > 代码约定”处理冲突。现有代码约定只补全未规定的实现细节。
3. 确定范围：用户指定 ticket 时只处理这些 ticket；未指定时先列出发现到的未完成 ticket，等待范围明确。
4. 建立“文档条目 → ticket → 模块 → 文件 → 验证”的追踪矩阵，并按依赖做拓扑排序。发现冲突、循环依赖或缺失公共契约时，阻塞受影响 ticket，不猜测公开接口。
5. 生成或更新 `docs/implementation-plan.md`，记录输入哈希、目标文件、接口、依赖、占位点、验证命令、风险和状态。计划格式见 [references/plan-template.md](references/plan-template.md)。
6. 在 `plan` 模式只展示计划、预期 diff、冲突和阻塞项。`apply` 模式按 ticket 处理：公共接口与类型 → 模块边界 → 适配器和依赖 → 最小实现 → 明确支持的入口注册 → 测试骨架。
7. 每个 ticket 先生成到临时位置并做语法级检查，再应用到工作区。记录应用前内容和哈希，仅恢复本 ticket 实际写入且未被其他人改动的内容；无法安全恢复时停止并报告。保护人工修改；无法可靠合并时跳过并报告。失败时保留前面已验证的结果。
8. 使用 `TODO(ticket:<id>, kind:<category>): <remaining work>` 标记未完成工作。`kind` 使用 `business-logic`、`integration`、`validation`、`design-gap` 或 `manual-decision`。
9. 从仓库真实配置识别验证命令，按 `syntax`、`unit`、`build`、`integration` 分层执行。外部服务不可用时使用本地替身，并明确未执行的集成验证。
10. 更新 `.code-skeleton/manifest.json` 和 `.code-skeleton/runs/<run_id>.json`，输出 Markdown 报告与 JSON 结果。恢复前核对输入哈希和文件现状，变更时重新计划；不静默覆盖历史记录。报告格式见 [references/report-template.md](references/report-template.md)。

## 约束

- 默认只修改当前 ticket 及直接支撑文件；跨模块重构必须单独列出并解释。
- 不自动引入新框架、访问真实外部系统、读取或生成真实凭据、执行真实迁移、commit、push、建分支或关闭 ticket。
- 数据库、消息队列和第三方 API 只生成接口、模型、迁移草稿、mock、本地替身和配置样例。
- 路由、容器、插件或 CLI 注册只有在详细设计或现有注册模式明确支持时才自动修改。
- CI 只允许 `plan` 和 `verify`，不自动 `apply`；存在未映射需求、未解析变量或阻塞项时报告非成功状态。仅在实际存在命令行集成时返回非零退出码。
- 计划、日志和报告不得记录密钥、令牌、连接串或不必要的个人信息。外部 ticket 状态只按已有约定和用户授权更新，不自动关闭。
- 成功条件是：目标 ticket 的骨架完成、阻塞项已记录、验证结果已归档且 diff 可解释。否则报告 `partial`、`blocked` 或 `failed`。

## 持久化产物

- `docs/implementation-plan.md`：计划、追踪矩阵和运行历史。
- `.code-skeleton/manifest.json`：文件、ticket、输入哈希、skill 版本、生成时间和状态。
- `.code-skeleton/runs/<run_id>.json`：单次运行的结构化结果。
- `.code-skeleton/tmp/`：成功后清理，失败时保留诊断产物。

配置规则和字段见 [references/configuration.md](references/configuration.md)。验证和错误分类见 [references/verification.md](references/verification.md)。
