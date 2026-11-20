# manifest.yml 约定

```yaml
schema_version: 1
project: <project-name>
source:
  checked_commit: <git-commit>
  checked_at: <ISO-8601>
  range_from: <commit-or-null>
entries:
  - function_id: <stable-id>
    title: <功能名称>
    category: <功能分类>
    chapter: sections/<function-id>.md
    status: covered | pending | archived
    roles: [<role>]
    verification:
      environment: <environment>
      checked_at: <ISO-8601>
      commit: <git-commit>
    screenshots:
      - path: assets/screenshots/<function-id>/01-<name>.png
        step: 1
        source: <page-url-or-description>
        captured_at: <ISO-8601>
    pending_items: []
pending_items:
  - function_id: <stable-id>
    reason: <具体缺口>
    needed: <账号、权限、环境、数据或人工决定>
    discovered_at: <ISO-8601>
```

`source.checked_commit` 表示已经完成影响分析的源码 commit，不代表所有条目都已覆盖。条目若缺少截图、无法登录或存在事实冲突，使用 `pending` 并在 `pending_items` 中说明。
