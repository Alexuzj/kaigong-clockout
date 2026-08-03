# 开工 Kaigong · 收工 Clock Out

一个给 Codex 使用的双语 Skill。说“开工”，Codex 会恢复项目上下文并继续明确的下一步；说“收工”，Codex 会审查本次改动、运行必要检查并留下可靠交接。

A bilingual Codex skill for reliable project-session startup and wrap-up. Say “开工” to recover context and continue; say “收工” to review, verify, and leave a durable handoff.

## 它解决什么问题

- 新会话开始时，不必反复解释项目做到哪里。
- 结束工作时，不会忘记最终检查和下一步记录。
- 区分本次改动与原有改动，避免误碰用户的工作。
- 验证失败时不会提交、推送或假装已经完成。
- 不会擅自创建分支、worktree、仓库、发布或部署。

## 安装 | Install

### 从 GitHub 下载 | Download ZIP

1. 在 GitHub 仓库页面选择 **Code → Download ZIP**。
2. 解压后找到 `skills/kaigong-clockout`。
3. 把整个 `kaigong-clockout` 文件夹复制到 `~/.codex/skills/`。
4. 重新打开 Codex。

Download the repository ZIP, then copy `skills/kaigong-clockout` to `~/.codex/skills/` and restart Codex.

### 使用 Git | Install with Git

```bash
git clone https://github.com/Alexuzj/kaigong-clockout.git
mkdir -p ~/.codex/skills
cp -R kaigong-clockout/skills/kaigong-clockout ~/.codex/skills/
```

更新时重新下载并替换该 Skill 文件夹。卸载时删除 `~/.codex/skills/kaigong-clockout`。

To update, download the latest version and replace the skill folder. To uninstall, remove `~/.codex/skills/kaigong-clockout`.

## 使用 | Usage

```text
开工
收工
```

也可以明确调用：

```text
$kaigong-clockout 开工，继续上次的任务
$kaigong-clockout 收工
```

English examples:

```text
$kaigong-clockout start this project session
$kaigong-clockout wrap up this project session
```

## 工作方式 | How it works

“开工”会读取适用的项目规则和交接记录，核对真实文件状态，区分已有改动，再继续清晰且安全的下一步。“收工”会复查目标与最终改动，执行与风险相称的检查，并记录停止位置、剩余工作和实际交付状态。

The start flow recovers only relevant context and verifies it against the workspace. The finish flow reviews the final changes, runs risk-appropriate checks, and records the exact delivery state.

## 搜索记录

2026-08-03 检索了 skills.sh 与 GitHub。已有方案主要关注跨会话 handoff 或仓库上下文初始化；本 Skill 将上下文恢复与安全收尾合成一套中英文对称流程。

- [OpenAI Codex Skill 示例](https://github.com/openai/codex/blob/main/codex-rs/skills/src/assets/samples/skill-creator/SKILL.md)
- [repository-context-bootstrap 提案](https://github.com/openai/skills/issues/368)
- [Codex Session Handoff Skill](https://gist.github.com/tegnike/09dbb98711d8b91e66de21611f5b88ff)

## 状态 | Status

- 已完成：开工恢复、收工审查、中英文触发、安全边界、Codex 元数据。
- 已发布：[Alexuzj/kaigong-clockout](https://github.com/Alexuzj/kaigong-clockout)

## 许可证 | License

[MIT](LICENSE)
