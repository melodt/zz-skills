# zz-skills

一组针对 mattpocock skills 工作流精简的替代 skills，减少过度设计、重复确认、任务编排和验证开销，保留需求验收及用户、仓库要求的检查。

## Skills

| Skill | 用途 | 主要调整 |
| --- | --- | --- |
| [feature-detail-design](skills/feature-detail-design/SKILL.md) | 根据已有方案独立编写详细设计 | 覆盖页面布局、操作链路、状态和验收标准，明确待确认问题 |
| [implementation-plan](skills/implementation-plan/SKILL.md) | 根据 spec、tickets 和详细设计编写实施计划 | 明确实施顺序、需求追踪、验证方式和阻塞项 |
| [code-skeleton](skills/code-skeleton/SKILL.md) | 根据 spec、tickets 和详细设计搭建代码骨架 | 先计划并追踪需求，再按授权生成骨架和记录验证结果 |
| [test-case-code-skeleton](skills/test-case-code-skeleton/SKILL.md) | 根据测试用例和设计搭建代码骨架 | 逐条映射用例并区分骨架检查与功能用例通过 |
| [test-case-workflow](skills/test-case-workflow/SKILL.md) | 生成、维护和执行可追溯的功能测试用例 | 逐条记录结果与证据，全部适用用例通过才算验证完成 |
| [verified-implement](skills/verified-implement/SKILL.md) | 按测试用例完成单项实现 | 衔接第三方 `implement`，验证通过后才进行获授权的完成动作 |
| [verified-implement-spec](skills/verified-implement-spec/SKILL.md) | 按测试用例完成完整 spec | 分别验证 ticket 和集成场景，衔接第三方 `implement-spec` |
| [verified-simple-implement](skills/verified-simple-implement/SKILL.md) | 按测试用例完成单项精简实现 | 沿用 `simple-implement` 的实现方式，验证通过后才执行完成动作 |
| [verified-simple-implement-spec](skills/verified-simple-implement-spec/SKILL.md) | 按测试用例完成完整 spec 的精简实现 | 沿用单分支工作流，分别验证任务和集成场景 |
| [verified-fast-implement](skills/verified-fast-implement/SKILL.md) | 按测试用例快速实现明确功能 | 保留直接实现方式，并要求用例通过后才能完成验证 |
| [simple-grill-with-docs](skills/simple-grill-with-docs/SKILL.md) | 追问方案并持续更新 Markdown 文档 | 只展开影响当前目标的决策；每轮通常最多三个问题；达到可执行状态后收敛 |
| [simple-to-spec](skills/simple-to-spec/SKILL.md) | 把已有讨论整理为可实现的 spec | 覆盖已定范围，精简用户故事；按需核查未知事实；默认本地文档 |
| [simple-to-tickets](skills/simple-to-tickets/SKILL.md) | 把 spec 拆成带验收标准和依赖的任务 | 使用最少必要 tickets；小需求可以只有一个；默认一份任务清单 |
| [fast-implement](skills/fast-implement/SKILL.md) | 根据功能描述直接快速实现 | 独立运行，无需 spec 或 tickets；不创建或切换分支；最小验证，默认保留工作区改动 |
| [simple-implement](skills/simple-implement/SKILL.md) | 实现单个任务或有明确边界的改动 | 按影响选择检查，复用有效验证结果，最后统一自查 |
| [simple-implement-spec](skills/simple-implement-spec/SKILL.md) | 按依赖顺序完成整个 spec | 默认同一分支连续实现，共享验证，最后统一提交 |
| [simple-pr](skills/simple-pr/SKILL.md) | 撰写或更新 PR 描述 | 优先仓库模板，复用真实验证证据，按需添加图示和风险说明 |
| [simple-retro](skills/simple-retro/SKILL.md) | 复盘开发过程，改善后续执行 | 根据实际证据提出少量最小整改，衡量收益和维护成本 |
| [operation-manual](skills/operation-manual/SKILL.md) | 维护系统操作手册 | 按 Git 提交增量更新 Markdown、截图和功能清单，支持 Web 页面核验与待补记录 |

## 使用方式

将需要的 skill 目录复制到所用工具支持的 skills 目录，并确认工具已发现它们。`simple-implement-spec` 会读取同级的 `simple-implement/SKILL.md`，使用前需同时安装这两个目录并保留相邻结构。`simple-implement`、`simple-implement-spec` 和 `fast-implement` 还需同级安装 `test-case-workflow`，以读取共享的实现状态回写规则。

`verified-implement` 和 `verified-implement-spec` 均读取同级的 `test-case-workflow/SKILL.md`，安装任一入口时需同时安装 `test-case-workflow` 并保留相邻结构。它们读取已安装的第三方 `implement` 或 `implement-spec` 并在自有入口中编排，不修改第三方目录；第三方 skill 不可用时会报告衔接缺口。需要在直接调用第三方实现 skill 时也应用门槛的项目，可将 [项目级测试用例规则模板](docs/test-case-agents-template.md) 合并到该项目的 `AGENTS.md`。这些规则是指令，不是技术强制门禁。

`test-case-code-skeleton` 需要与 `code-skeleton`、`test-case-workflow` 相邻安装，并读取已有的对应功能测试用例文档；默认只规划，明确要求执行时才生成骨架。骨架完成不代表功能测试用例通过。

三个 `verified-simple-*` / `verified-fast-*` 入口也需与 `test-case-workflow` 和对应原始 skill 安装在相邻目录；其中 `verified-simple-implement-spec` 还需要 `simple-implement`。`verified-fast-implement` 保留快速直接实现，但正式用例仍需要至少一份 spec、ticket 或详细设计；缺少来源时可继续不依赖来源的实现，但验证及完成动作受阻。

在支持 `$skill-name` 调用的工具中，例如：

```text
$fast-implement 为搜索框增加清空按钮，按现有交互实现，只做必要验证。
$simple-grill-with-docs 帮我收敛这个需求，边讨论边更新 docs/search.md。
$simple-to-spec 根据刚才的讨论完善 docs/search.md。
$simple-to-tickets 将 docs/search.md 拆成最少必要任务。
$feature-detail-design 根据 docs/search.md 和 docs/search-tickets.md 编写独立的详细设计文档。
$test-case-workflow 根据 docs/search.md 和 docs/search-tickets.md 生成搜索功能测试用例。
$verified-implement 按测试用例实现 docs/search-tickets.md 中的搜索任务。
$verified-implement-spec 按测试用例实现 docs/search.md 及关联任务。
$verified-simple-implement 按测试用例实现 docs/search-tickets.md 中的搜索任务。
$verified-simple-implement-spec 按测试用例完成 docs/search.md 及关联任务。
$verified-fast-implement 按 docs/search.md 的测试用例快速实现搜索功能。
$implementation-plan 根据 spec、tickets 和详细设计编写实施计划。
$code-skeleton 根据 spec、tickets 和详细设计规划代码骨架。
$test-case-code-skeleton 根据 spec、tickets、详细设计和测试用例规划代码骨架。
$operation-manual 根据最近的 Git 提交更新 docs/operation-manual/，补齐页面截图并记录待补事项。
$simple-implement-spec 按 docs/search.md、docs/search-tickets.md 和详细设计文档完成实现。
$simple-pr 根据本次改动和已有验证结果起草 PR 描述。
$simple-retro 复盘当前会话，找出最值得处理的时间开销。
```

这些步骤按需选择。功能已经明确、希望直接快速落地时可使用 `$fast-implement`，它不依赖其他 skill，无需先写 spec 或拆 tickets。需要最终统一提交的常规实现可使用 `$simple-implement`；多任务交付可使用 `$simple-implement-spec`。PR 描述和复盘也可单独使用。

## 默认约定

- **范围收敛**：以当前需求和验收标准为准，避免为了完整而补出新功能、额外重构或复杂流程。
- **文档交付**：优先用户指定路径和已有文档；否则使用 `docs/<topic>.md` 和 `docs/<topic>-tickets.md`。写方案、拆任务本身不启动实现。
- **连续实现**：`simple-implement` 和 `simple-implement-spec` 默认使用当前分支，最后统一提交，提交只包含本任务改动。`fast-implement` 不创建或切换分支、不创建 worktree、不合并分支，默认将改动留在工作区，按用户要求提交。
- **适量验证**：优先受影响的行为测试和必要检查。验证输入未变化时复用通过结果；修改后重跑受影响检查。明确要求、影响广泛或无法限定影响范围时运行全量测试。
- **按需编排**：TDD、额外评审、多代理和 worktree 按需求或仓库规则启用，ticket 边界本身不触发分支切换、合并或完整测试。
- **发布范围**：spec 和 tickets 可直接保存本地，无需配置 issue tracker；外部发布、PR 操作及环境修改遵循用户授权和仓库工作流。
- **如实交付**：区分已实现、已验证和未完成内容，保留检查失败及验证缺口。复盘可以得出“没有值得新增的规则”。
- **状态回写**：实现入口在报告或提交前更新任务涉及的已有 spec、tickets 和测试用例；部分完成或阻塞也如实记录。详细设计不记录任务进度，设计偏差在任务或 spec 及交付报告中说明；外部系统更新遵循授权。

## 来源与验证

本项目基于使用 mattpocock skills 的实际反馈进行精简适配。`simple-pr` 保留了原 PR skill 对 [Humanlayer / show-me](https://github.com/humanlayer/skills/blob/main/plugins/show-me/skills/show-me/SKILL.md) 的来源署名。

当前各 skill 已通过格式校验，实际效果仍需在真实任务中持续验证。
