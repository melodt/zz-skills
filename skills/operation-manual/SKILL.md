---
name: operation-manual
description: 维护项目级系统操作手册：从 Git 提交增量识别用户可感知变更，核验 Web 页面并更新中文 Markdown、截图和 manifest。适用于实现任务后的手册同步，也适用于独立补录或修订操作说明。
---

# 系统操作手册

把手册当作项目级、可追溯的用户文档维护。默认输出目录是目标项目的 `docs/operation-manual/`；如果项目已有明确的手册目录，沿用现有结构并在结果中说明。

## 工作流程

### 1. 读取状态和范围

- 读取 `docs/operation-manual/manifest.yml`、`index.md` 和适用的项目说明。
- 检查 Git 状态、当前 `HEAD`、manifest 中的 `source.checked_commit` 和已有待补事项。
- 用户指定 commit、范围或功能名时，以指定范围为主；否则从 `source.checked_commit` 到当前源码 `HEAD` 增量分析。
- 没有基准提交时进入首次盘点；Git 历史被改写或基准不存在时，停止猜测并记录需要重新确定基准。

### 2. 建立或刷新功能目录

首次盘点时，从前端路由、菜单、权限配置、页面组件和后端公开接口交叉发现候选功能，再用运行中的导航确认用户入口。后端只有在存在用户入口或改变用户可见行为时才进入业务操作手册。

使用稳定的 `function_id` 关联功能、章节、截图和代码变更。优先使用 manifest 中已有标识；路由、菜单、权限和 API 推断不确定时，记录待确认项，不要求给内部函数增加注解。

### 3. 分析提交影响

将变更分为：

- **需要更新**：页面、路由、字段、校验、权限、状态流转、成功结果、错误提示或 API 契约改变了用户操作。
- **无需更新**：内部重构、性能、日志、存储或测试调整，且用户行为不变。
- **待确认**：无法判断影响、代码与页面矛盾或缺少运行环境。

删除或重命名的功能默认归档原章节，保留历史截图和迁移说明；不要因为代码删除就直接删除手册文件。

### 4. 核验页面和采集截图

优先使用验证环境中的真实 Web 页面，其次使用已授权的浏览器自动化，最后才使用用户提供的截图。每张截图都记录来源页面、采集时间、验证环境和对应步骤。

截图保存前检查密码、Token、AccessKey、个人信息和业务数据。能可靠遮盖才保存；否则将条目标为待人工复核，不把原始敏感图放入仓库。无法运行、登录或准备测试数据时，继续处理不依赖这些条件的章节，并生成具体待补事项；代码分析不能替代页面证据。

### 5. 编写操作说明

按用户任务组织章节，而不是按代码模块组织。每项已覆盖功能至少说明：

- 适用角色、前置条件和进入路径；
- 编号步骤及对应页面截图；
- 成功结果、异常或限制、相关权限；
- `function_id`、覆盖状态和最后验证时间。

使用 `references/chapter-template.md` 作为默认模板。保持页面文字、按钮、菜单和截图一致；不把内部类名、数据库结构或未验证的推测写成用户步骤。

### 6. 更新状态和索引

维护 `manifest.yml` 中的功能目录、截图、角色、环境、覆盖状态、待补事项和 `source.checked_commit`。即使某项缺少截图，也可以记录本次已分析到的源码 commit，但必须保留该项的 `pending` 状态。

更新 `index.md`，让读者能按功能分类进入章节，并能看出待补内容。使用 `references/manifest-schema.md` 校验字段和状态含义。

### 7. 验证和提交

在标记为已覆盖前逐项检查：功能标识唯一；章节和图片路径有效；步骤引用的页面元素在截图中可见或有说明；角色和权限已标注；待补项没有被标为完成；基准 commit 可追溯；截图没有敏感信息。

检查工作区。如果存在与手册无关的改动，不要提交，只报告已生成的文件和阻塞项。否则只暂存手册 Markdown、图片、索引和 manifest，创建独立提交，例如：

```text
docs(manual): update access-key operations
```

最终报告应包含：更新的功能、未完成的待补事项、使用的 commit 范围、实际验证方式、生成目录和提交 ID。

## 输出结构

默认创建或维护：

```text
docs/operation-manual/
├── index.md
├── manifest.yml
├── sections/
│   └── <function-id>.md
├── assets/
│   └── screenshots/<function-id>/
└── archive/
```

`archive/` 只保存已移除或重命名功能的历史章节；不要复制同一份当前说明到多个位置。

## 参考资料

- 需要编写章节时，读取 [references/chapter-template.md](references/chapter-template.md)。
- 需要创建或校验状态文件时，读取 [references/manifest-schema.md](references/manifest-schema.md)。
- 需要判断后端改动是否进入用户手册时，读取 [references/change-classification.md](references/change-classification.md)。
