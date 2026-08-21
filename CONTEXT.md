# Context

## Current work

公开版定位已统一为“Vibe Coding 时代的 Ctrl+S”，首次收工与项目书架体验保持不变。

## Stopped at

中文 README、英文 README、Skill 界面文案和 GitHub 简介已统一更新并通过最终检查。

## Decisions

- 核心仍是两次可信状态转换：开工恢复现场，收工保存交接。
- 私人项目书架是独立模式，用自然语言完成记住、列出、改名、修复、默认、归档和移除。
- 普通用户不需要手写 JSON；手动配置只放在高级说明。
- 正常开工和收工各使用三行人话输出，内部恢复术语只在冲突时解释。
- 项目书架管理不授权移动、重命名或删除真实文件；真正搬家必须单独预览、确认和验证。
- 私人项目名称和路径只保存在本机，不进入公开仓库。
- “Ctrl+S”保存的是项目上下文，不是文件备份，也不能恢复云端聊天或账号。
- 中英文 README 内容对等，但分别使用自然表达。
- 新聊天目录必须先匹配私人项目目录或提供持续项目证据；否则视为未绑定，并从已登记项目中选择。
- 第一次直接收工仍可留下事实性交接，但没有开工基线时，当前文件一律视为原有现场。
- 只有交接成功后才邀请加入项目书架；收工本身不授权登记，书架也不移动真实文件。
- 普通检查结果不强制伪造数量；只有真实可计数时才报告通过与失败数。
- “Vibe Coding 时代的 Ctrl+S”作为传播定位，必须紧接“保存上下文，不是代码备份”的准确边界。

## Remaining

- 无。

## Delivery

- Checks: positioning consistency, skill structure, bilingual parity, final diff, privacy scan, and prior 14 adversarial scenarios passed; 0 failures.
- Commit/push: completed for this iteration on `main`.
