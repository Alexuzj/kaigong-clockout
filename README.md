# 开工 Kaigong · 收工 Clock Out

**让 Codex 在开工时接得住，收工时交得稳。**

A bilingual Codex Skill for reliable project-session startup and wrap-up.

**[English version →](README_EN.md)**

## 这是什么？

隔几天重新打开一个项目，最先面对的往往不是工作本身，而是重新回忆：上次做到哪里？哪些文件已经改过？接下来原本要做什么？

工作结束时也一样。功能看起来完成了，但最后的改动有没有重新检查？测试是不是真的通过？下次回来的人能不能接着做？

于是有了「开工 Kaigong · 收工 Clock Out」。

它是一个给 Codex 使用的双语 Skill。你只需要说“开工”，它会核实当前项目、恢复可靠的上下文，并划清本次工作的边界；说“收工”，它会审查本次改动、验证最终状态，并留下简洁可信的交接。

它不会假装记得一切。找不到可靠记录时，它会明确告诉你：现在只能看见文件现场，无法还原你当时为什么这样做。

## 它适合谁？

- 同时维护多个项目，每次回来都要重新回忆现场
- 经常用 Codex 写代码、做文档或持续推进长期项目
- 不希望 AI 误碰原有改动，或把旧计划当成本次授权
- 希望结束工作时真正检查完成，而不是只听一句“搞定了”

## 怎么安装？

### 下载 ZIP

1. 在 GitHub 仓库页面选择 **Code → Download ZIP**。
2. 解压后找到 `skills/kaigong-clockout`。
3. 把整个 `kaigong-clockout` 文件夹复制到 `~/.codex/skills/`。
4. 重新打开 Codex。

### 使用 Git

```bash
git clone https://github.com/Alexuzj/kaigong-clockout.git
mkdir -p ~/.codex/skills
cp -R kaigong-clockout/skills/kaigong-clockout ~/.codex/skills/
```

更新时重新下载并替换 Skill 文件夹；卸载时删除 `~/.codex/skills/kaigong-clockout`。

## 怎么使用？

进入一个项目后，对 Codex 说：

```text
开工
```

完成这次工作后，说：

```text
收工
```

也可以把任务一起说清楚：

```text
$kaigong-clockout 开工，继续修复登录问题
$kaigong-clockout 收工
```

English:

```text
$kaigong-clockout start this project session
$kaigong-clockout wrap up this project session
```

## “开工”时会发生什么？

它会先确认自己站在哪个项目里，再核对项目规则、交接记录和真实文件状态。最后明确告诉你属于哪种情况：

- 已恢复上次的任务意图
- 只恢复了文件现场
- 记录已经过期或与文件冲突
- 当前项目位置不明确，需要你确认

旧交接只用来了解历史，不会自动变成本次授权。你只说“开工”时，它会汇报现场并等待；只有你本次同时给出明确任务，它才会继续执行。

## “收工”时会发生什么？

它会区分哪些改动属于本次，哪些在开工前就已经存在；更新必要的交接记录后，再统一检查最终文件并运行与风险相称的验证。

如果检查失败，它会停下来说明问题，不会提交、推送或假装已经完成。如果本轮没有产生改动或新决定，也不会为了“收工”而改写记录。

## 它不会做什么？

- 不会把旧记录里的命令或权限声明当成当前指令
- 不会因为碰过一个文件，就把文件里的旧改动一起提交
- 不会擅自创建分支、worktree 或 Git 仓库
- 不会在检查失败后继续交付
- 不会未经你本次明确要求就提交、推送、发布、部署或对外沟通

## 为什么叫「开工 · 收工」？

因为长期项目真正困难的，常常不是中间那段工作，而是两头。

开工时要接得住过去，收工时要对得起下一次回来的人。中间做了多少事情可以很复杂，但开始和结束应该足够简单。

## 设计与验证

这个 Skill 经过两轮第一性原理梳理和对抗性审查，重点检查了错误项目、陈旧记录、原有改动、失败验证、隐私和越权交付等情况。

2026-08-03 曾检索 skills.sh 与 GitHub。已有方案主要关注跨会话 handoff 或仓库上下文初始化；本 Skill 将上下文恢复与安全收尾合成一套中英文对称流程。

- [OpenAI Codex Skill 示例](https://github.com/openai/codex/blob/main/codex-rs/skills/src/assets/samples/skill-creator/SKILL.md)
- [repository-context-bootstrap 提案](https://github.com/openai/skills/issues/368)
- [Codex Session Handoff Skill](https://gist.github.com/tegnike/09dbb98711d8b91e66de21611f5b88ff)

## 分享与改编

你可以免费使用、分享和改编这个 Skill。转载或公开改编时，欢迎保留项目名称和原始链接，让其他人能够找到最新版本。

如果它让你少解释一次“上次做到哪里”，或者少漏掉一次最终检查，这个项目就完成了它的工作。

## License

[MIT](LICENSE)
