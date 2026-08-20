# Context

## Current work

公开 Skill 的下一版已经完成：用“项目上下文的 Ctrl+S”解释真实价值，增加私人项目目录管理，并简化正常开工与收工的输出。

## Stopped at

核心 Skill、中英文 README、界面说明和项目目录参考文件已修改，格式、隐私和8个独立行为场景均已验证通过。

## Decisions

- 核心仍是两次可信状态转换：开工恢复现场，收工保存交接。
- 私人项目目录是独立模式，用自然语言完成记住、列出、改名、修复、默认、归档和移除。
- 普通用户不需要手写 JSON；手动配置只放在高级说明。
- 正常开工和收工各使用三行人话输出，内部恢复术语只在冲突时解释。
- 项目目录管理不授权移动、重命名或删除真实文件；真正搬家必须单独预览、确认和验证。
- 私人项目名称和路径只保存在本机，不进入公开仓库。
- “Ctrl+S”保存的是项目上下文，不是文件备份，也不能恢复云端聊天或账号。
- 中英文 README 内容对等，但分别使用自然表达。

## Remaining

- 无。

## Delivery

- Checks: passed skill validation, diff and privacy checks, bilingual structure review, and 8 independent behavior scenarios after one correction; 0 failures.
- Commit/push: authorized for this iteration; publish this completed state to `main`.
