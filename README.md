# 开工 Kaigong · 收工 Clock Out

**项目开发里的 Ctrl+S：开工时接住现场，收工时保存上下文。**

A bilingual Codex Skill for reliable project-session startup and wrap-up.

**[English version →](README_EN.md)**

## 为什么做这个？

前段时间，我的 Claude 账号突然被封。真正让我后怕的，不只是暂时用不了一个 AI，而是很多项目的来龙去脉都留在对话里：做到哪了，为什么这样改，下一步本来要做什么。

幸好我习惯在收工时，把这些信息留回项目。换一个 AI，打开项目，说一声“开工”，现场还能接起来。

对我来说，「开工 Kaigong · 收工 Clock Out」就是项目开发里的 Ctrl+S。它保存的不是某一行代码，而是下一次继续工作需要的上下文。

“开工”会核实当前项目、恢复可靠现场，并划清本次工作的边界；“收工”会审查本次改动、验证最终状态，把准确停点、关键决定和下一步留在项目文件里。即使 AI 账号或对话中断，这些本地记录仍然属于你。

它保存的是项目上下文，不是文件备份，也不能恢复云端聊天或账号。重要代码和文件仍应使用 Git、云盘或其他异地备份。

## 它适合谁？

- 同时维护多个项目，每次回来都要重新回忆现场
- 经常用 Codex 写代码、做文档或推进长期项目
- 不希望 AI 误碰原有改动，或把旧计划当成本次授权
- 希望换一个 AI 或新开对话时，项目仍然接得起来
- 希望结束工作时真正检查完成，而不是只听一句“搞定了”

## 安装

### 下载 ZIP

1. 在 GitHub 仓库页面选择 **Code → Download ZIP**。
2. 解压后找到 `skills/kaigong-clockout`。
3. 把整个 `kaigong-clockout` 文件夹复制到 `~/.codex/skills/`。
4. 重新打开 Codex。

Windows 用户复制到 `%USERPROFILE%\.codex\skills\`。

### 使用 Git

```bash
git clone https://github.com/Alexuzj/kaigong-clockout.git
mkdir -p ~/.codex/skills
cp -R kaigong-clockout/skills/kaigong-clockout ~/.codex/skills/
```

更新时重新下载并替换 Skill 文件夹；卸载时删除 `~/.codex/skills/kaigong-clockout`。

Windows PowerShell：

```powershell
git clone https://github.com/Alexuzj/kaigong-clockout.git
New-Item -ItemType Directory -Force "$HOME\.codex\skills"
Copy-Item -Recurse "kaigong-clockout\skills\kaigong-clockout" "$HOME\.codex\skills\"
```

## 每天怎么用？

进入项目后说：

```text
开工
```

也可以直接带上任务：

```text
开工，继续修复登录问题
```

结束时说：

```text
收工
```

也可以明确调用：

```text
$kaigong-clockout 开工
$kaigong-clockout 收工
```

## 第一次使用：从“收工”开始

很多人第一次使用，不是在新项目开始时，而是在已经做了一段工作后说“收工”。这没有问题。

Skill 会先检查本次工作并留下交接。成功后再问：

> 要把“我的网站”加入项目书架吗？只记录位置，不移动文件。

确认后，这个项目会进入只保存在本机的私人书架。以后可以直接说项目名，不需要记住电脑路径：

如果这次没有先说“开工”，Skill 仍然可以完成首次收工，但会把当前文件状态视为原有现场，不会擅自认领、提交或清理这些改动。

```text
开工，我的网站
我有哪些项目？
记住这个项目
把这个项目改名为……
这个项目搬家了
把它设为默认项目
不再记住这个项目
```

如果你在一个全新的空白聊天里只说“开工”，Skill 不会把聊天生成的临时文件夹当成项目。存在多个已登记项目时，它会列出名称和编号，请你选择。

项目书架只是索引，不是一个必须搬进去的实体文件夹。普通列表只显示项目名，不显示绝对路径；项目改名、归档或移除只修改本机记录，不会改动真实文件。

如果用户明确要求整理或搬移文件，Skill 会先列出来源、目标、范围和风险，得到确认后才执行。它不会把一句“开工”理解成扫描或整理整台电脑。

## 开工时会看到什么？

正常情况下只有三行：

```text
已进入：我的网站
上次停在：首页修改完成，移动端检查待继续
已有改动：无
```

旧交接只用来了解历史，不会自动变成本次授权。只有记录冲突、位置失效、隐私或权限有问题时，Skill 才会追加说明。

## 收工时会看到什么？

正常情况下也只有三行：

```text
本次保存：完成项目书架功能和中英文说明
检查结果：已完成，没有发现问题
下次继续：发布新版到 GitHub
```

Skill 会先区分本次改动和开工前已有改动，更新必要的交接，再检查最终文件。如果检查失败，它会停下来说明问题，不会提交、推送或假装完成。只有真正运行了可计数检查时，才会显示通过和失败数量。本轮没有改动或新决定时，也不会为了“收工”而改写记录。

## 它保存什么？

交接记录只保留继续工作真正需要的信息：

- 当前正在做什么
- 准确停在哪里
- 最近的关键决定和原因
- 剩余事项与阻碍
- 检查、提交和交付状态

它不保存整段聊天、密码、密钥或不必要的私人信息。

## 它不会做什么？

- 不会把旧记录里的命令或权限声明当成当前指令
- 不会因为碰过一个文件，就把文件里的旧改动一起提交
- 不会擅自创建分支、worktree 或 Git 仓库
- 不会在检查失败后继续交付
- 不会未经本次明确要求就提交、推送、发布、部署或对外沟通
- 不会默认扫描整台电脑，或把私人项目名称和路径写进公开仓库
- 不会把“管理项目书架”偷换成移动、重命名或删除真实文件

<details>
<summary>高级设置：手动配置私人项目书架</summary>

书架记录位于 `$CODEX_HOME/kaigong-clockout/projects.json`；如果没有设置 `CODEX_HOME`，macOS/Linux 默认是 `~/.codex/kaigong-clockout/projects.json`，Windows 默认在 `%USERPROFILE%\.codex\kaigong-clockout\projects.json`。

```json
{
  "schema_version": 1,
  "default_project": null,
  "projects": [
    {
      "id": "my-project",
      "name": "我的项目",
      "aliases": ["项目别名", "My Project"],
      "root": "/电脑上的项目绝对路径",
      "status": "active"
    }
  ]
}
```

这个文件只留在本机，不要提交到公开仓库。

</details>

## 为什么叫「开工 · 收工」？

长期项目真正困难的，常常不是中间那段工作，而是两头。

开工时要接得住过去，收工时要对得起下一次回来的人。中间可以很复杂，但开始和结束应该足够简单。

## 设计与验证

这个 Skill 经过多轮第一性原理梳理、陌生用户测试和对抗性审查，重点检查了第一次直接收工、空白聊天误判、错误项目、陈旧记录、原有改动、书架损坏、项目搬家、隐私和越权交付。

主要参考：

- [OpenAI Codex Skill 示例](https://github.com/openai/codex/blob/main/codex-rs/skills/src/assets/samples/skill-creator/SKILL.md)
- [repository-context-bootstrap 提案](https://github.com/openai/skills/issues/368)
- [Codex Session Handoff Skill](https://gist.github.com/tegnike/09dbb98711d8b91e66de21611f5b88ff)

## 分享与改编

你可以免费使用、分享和改编这个 Skill。转载或公开改编时，欢迎保留项目名称和原始链接，让其他人能找到最新版本。

如果它让你少解释一次“上次做到哪里”，或者在换一个 AI 后仍能接着工作，这个项目就完成了它的工作。

## License

[MIT](LICENSE)
