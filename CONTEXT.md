# Context

## Current work

已修复空白新聊天误认项目的问题：新聊天生成目录不会再被当作真实项目。

## Stopped at

规则、私人目录参考和中英文说明已更新；真实 `kai` 失败场景及六类项目选择分支均已验证。

## Decisions

- 核心仍是两次可信状态转换：开工恢复现场，收工保存交接。
- 私人项目目录是独立模式，用自然语言完成记住、列出、改名、修复、默认、归档和移除。
- 普通用户不需要手写 JSON；手动配置只放在高级说明。
- 正常开工和收工各使用三行人话输出，内部恢复术语只在冲突时解释。
- 项目目录管理不授权移动、重命名或删除真实文件；真正搬家必须单独预览、确认和验证。
- 私人项目名称和路径只保存在本机，不进入公开仓库。
- “Ctrl+S”保存的是项目上下文，不是文件备份，也不能恢复云端聊天或账号。
- 中英文 README 内容对等，但分别使用自然表达。
- 新聊天目录必须先匹配私人项目目录或提供持续项目证据；否则视为未绑定，并从已登记项目中选择。

## Remaining

- 无。

## Delivery

- Checks: skill structure, final diff, real blank-chat case, and 6 selection scenarios passed; 0 failures.
- Commit/push: authorized for this correction; publish the verified state to `main`.
