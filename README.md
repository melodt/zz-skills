# zz-skills

一组针对 mattpocock skills 工作流精简的替代 skills，减少过度设计、重复确认、任务编排和验证开销，保留需求验收及用户、仓库要求的检查。

## Skills

| Skill | 用途 | 主要调整 |
| --- | --- | --- |
| [simple-grill-with-docs](skills/simple-grill-with-docs/SKILL.md) | 追问方案并持续更新 Markdown 文档 | 只展开影响当前目标的决策；每轮通常最多三个问题；达到可执行状态后收敛 |
| [simple-to-spec](skills/simple-to-spec/SKILL.md) | 把已有讨论整理为可实现的 spec | 覆盖已定范围，精简用户故事；按需核查未知事实；默认本地文档 |
| [simple-to-tickets](skills/simple-to-tickets/SKILL.md) | 把 spec 拆成带验收标准和依赖的任务 | 使用最少必要 tickets；小需求可以只有一个；默认一份任务清单 |
| [simple-implement](skills/simple-implement/SKILL.md) | 实现单个任务或有明确边界的改动 | 按影响选择检查，复用有效验证结果，最后统一自查 |
| [simple-implement-spec](skills/simple-implement-spec/SKILL.md) | 按依赖顺序完成整个 spec | 默认同一分支连续实现，共享验证，最后统一提交 |
| [simple-pr](skills/simple-pr/SKILL.md) | 撰写或更新 PR 描述 | 优先仓库模板，复用真实验证证据，按需添加图示和风险说明 |
| [simple-retro](skills/simple-retro/SKILL.md) | 复盘开发过程，改善后续执行 | 根据实际证据提出少量最小整改，衡量收益和维护成本 |

## 使用方式

将需要的 skill 目录复制到所用工具支持的 skills 目录，并确认工具已发现它们。`simple-implement-spec` 会读取同级的 `simple-implement/SKILL.md`，使用前需同时安装这两个目录并保留相邻结构。

在支持 `$skill-name` 调用的工具中，例如：

```text
$simple-grill-with-docs 帮我收敛这个需求，边讨论边更新 docs/search.md。
$simple-to-spec 根据刚才的讨论完善 docs/search.md。
$simple-to-tickets 将 docs/search.md 拆成最少必要任务。
$simple-implement-spec 按 docs/search.md 和 docs/search-tickets.md 完成实现。
$simple-pr 根据本次改动和已有验证结果起草 PR 描述。
$simple-retro 复盘当前会话，找出最值得处理的时间开销。
```

这些步骤按需选择。需求已经明确时可以直接实现；小改动可使用 `$simple-implement`，无需先写 spec 或拆 tickets。PR 描述和复盘也可单独使用。

## 默认约定

- **范围收敛**：以当前需求和验收标准为准，避免为了完整而补出新功能、额外重构或复杂流程。
- **文档交付**：优先用户指定路径和已有文档；否则使用 `docs/<topic>.md` 和 `docs/<topic>-tickets.md`。写方案、拆任务本身不启动实现。
- **连续实现**：默认使用当前分支，按依赖顺序完成任务，最后统一提交。用户或仓库另有要求时遵循相应要求；提交只包含本任务改动。
- **适量验证**：优先受影响的行为测试和必要检查。验证输入未变化时复用通过结果；修改后重跑受影响检查。明确要求、影响广泛或无法限定影响范围时运行全量测试。
- **按需编排**：TDD、额外评审、多代理和 worktree 按需求或仓库规则启用，ticket 边界本身不触发分支切换、合并或完整测试。
- **发布范围**：spec 和 tickets 可直接保存本地，无需配置 issue tracker；外部发布、PR 操作及环境修改遵循用户授权和仓库工作流。
- **如实交付**：区分已实现、已验证和未完成内容，保留检查失败及验证缺口。复盘可以得出“没有值得新增的规则”。

## 来源与验证

本项目基于使用 mattpocock skills 的实际反馈进行精简适配。`simple-pr` 保留了原 PR skill 对 [Humanlayer / show-me](https://github.com/humanlayer/skills/blob/main/plugins/show-me/skills/show-me/SKILL.md) 的来源署名。

当前各 skill 已通过格式校验，实际效果仍需在真实任务中持续验证。
