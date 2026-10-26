---
name: simple-pr
description: Write or update a concise PR description using the actual changes and existing validation evidence. Use when the user wants a PR body or help preparing a pull request.
metadata:
  credits:
    skill: show-me
    author: Dex Horthy
    organisation: Humanlayer
    url: https://github.com/humanlayer/skills/blob/main/plugins/show-me/skills/show-me/SKILL.md
---

Write for a reviewer who has not seen the conversation. Read the applicable repository instructions and PR template, then use the requested change, relevant diff, and available validation results. Use the project's domain language. Confirm the comparison base from the user's request or repository/PR context; ask only if an unresolved ambiguity would materially change the description. Distinguish local pending changes from changes already included in the PR.

## Description

Follow the repository's PR template when present. Otherwise use a brief summary and validation section, adding risks or rollout notes when they affect the review:

- **Summary:** lead with the concrete problem and resulting behavior. Explain implementation details only when they help assess the change. Scale detail to complexity; a small change may need only one or two sentences.
- **Validation:** report the relevant checks actually run and their outcomes. Identify known failures, checks not run, and meaningful verification gaps. Reuse results only when they apply to the current changes; distinguish local results from CI status and passing results from pending checks.
- **Risks and rollout, when relevant:** describe evidenced compatibility effects, affected consumers, migrations, and rollback limitations. State concrete consequences rather than generic risk labels or speculative possibilities.

Use before/after evidence, screenshots, a diagram, or a small code sketch only when it materially clarifies the change. Label illustrative sketches as such. A passing result alone does not establish that the old behavior was observed failing.

Writing the description does not require recreating old failures, generating screenshots, or rerunning valid checks just to fill a template. If the user also requested validation or PR preparation, complete the applicable checks for that scope; otherwise accurately document the evidence available.

## Finish

Review the description once against the final changes and available evidence. Remove abandoned approaches, unsupported claims, conversational history, and unrelated details. Include issue references only when verified, and use closing keywords only for issues actually resolved by the change.

Return the body in chat or save it to the user's requested path. Create or update a remote PR when the user requested that action, preserving unrelated existing content and following the repository workflow. Report the resulting reference only after the operation succeeds. Keep merging and publishing code within the user's authorized scope.
