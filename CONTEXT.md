# Context

## Current work
已完成“开工 Kaigong · 收工 Clock Out”公开 Skill 的第一性原理优化、对抗式审查和最终命名统一。

## Stopped at
公开 GitHub 仓库已创建，当前版本准备提交到 `main` 并发布首个 Release。

## Decisions
- 使用 `kaigong-clockout` 作为仓库名和 Skill 名，以中文“开工”建立辨识度，以英文“Clock Out”解释收工场景。
- 开工只恢复必要上下文，并记录已有改动边界。
- 收工在最后一次修改后重新审查最终改动，验证失败时停止所有交付动作。
- 提交和推送必须来自当前用户要求，或项目规则对“收工”动作的明确约定；发布和部署必须由当前用户明确要求。

## Remaining
- 无。

## Delivery
- Checks: passed final validation and failure-path forward test.
- Commit/push: authorized for the public GitHub release.
