# Context

## Current work
已完成公开 Skill 的第二轮第一性原理优化、对抗性审查和 GitHub README 重写，使它能安全服务不了解用户历史的陌生人。

## Stopped at
本地修改和独立失败路径测试已完成，本次更新已获授权提交并推送到 `main`。

## Decisions
- 使用 `kaigong-clockout` 作为仓库名和 Skill 名，以中文“开工”建立辨识度，以英文“Clock Out”解释收工场景。
- 开工的产出是已核实的项目现场和本次授权边界；旧记录只提供历史事实，不能授权新动作。
- 开工按恢复程度分状态；只有本次请求同时给出具体任务时才继续执行。
- 原有改动与本次改动按内容区分，不能因本次碰过文件就整份提交。
- 所有记录修改完成后再统一复查和验证最终状态。
- 提交、推送、发布、部署和外部沟通都必须由当前用户明确要求。
- GitHub 介绍先从用户真实处境出发，再解释用途、使用方法、结果和边界，避免只罗列功能。
- 中文与英文 README 内容对等并互相链接，让中英文用户都能完整理解和安装。

## Remaining
- 无。

## Delivery
- Checks: passed skill validation, final diff and privacy checks, 3 adversarial scenarios, and 3 unfamiliar-user scenarios after two minimal corrections.
- Commit/push: completed for this iteration on `main`.
