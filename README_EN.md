# Kaigong · Clock Out

**Let Codex pick up the thread when work starts—and leave a reliable handoff when it ends.**

A bilingual Codex Skill for project-session startup and wrap-up.

**[中文说明 →](README.md)**

## What is this?

When you reopen a project after a few days, the first challenge is often not the work itself. It is reconstructing the context: Where did I stop? Which files were already changed? What was I planning to do next?

The end of a session has the same problem in reverse. The feature may look finished, but were the final edits reviewed? Did the checks actually pass? Can the next session continue without guessing?

That is why **Kaigong · Clock Out** exists.

It is a bilingual Skill for Codex. Say “开工” or “start this project session,” and it verifies the project, recovers trustworthy context, and establishes a boundary for the new session. Say “收工” or “wrap up this project session,” and it reviews the session’s changes, verifies the final state, and leaves a concise handoff.

It does not pretend to remember what it cannot verify. If there is no reliable handoff, it will say that it can recover the file state but not the intent behind earlier decisions.

## Who is it for?

- People who maintain several projects and repeatedly need to reconstruct where they stopped
- Anyone who uses Codex for code, documents, or other long-running project work
- Users who do not want AI to overwrite existing changes or treat an old plan as current permission
- People who want a real end-of-session check instead of an unsupported “done”

## How to install

### Download the ZIP

1. On the GitHub repository page, choose **Code → Download ZIP**.
2. Unzip the download and find `skills/kaigong-clockout`.
3. Copy the entire `kaigong-clockout` folder into `~/.codex/skills/`.
4. Restart Codex.

### Install with Git

```bash
git clone https://github.com/Alexuzj/kaigong-clockout.git
mkdir -p ~/.codex/skills
cp -R kaigong-clockout/skills/kaigong-clockout ~/.codex/skills/
```

To update, download the latest version and replace the Skill folder. To uninstall, remove `~/.codex/skills/kaigong-clockout`.

## How to use it

Inside a project, tell Codex:

```text
start this project session
```

When the session is finished, say:

```text
wrap up this project session
```

You can also invoke the Skill explicitly and include the task:

```text
$kaigong-clockout start this project session and continue fixing the login issue
$kaigong-clockout wrap up this project session
```

Chinese triggers work as well:

```text
开工
收工
```

## What happens when a session starts?

The Skill first confirms which project it is operating in. It then checks the applicable project instructions, the handoff record, and the actual files. It reports one of four states:

- The previous task intent has been verified
- Only the file state could be recovered
- The handoff is stale or conflicts with the files
- The intended workspace is unclear and needs confirmation

An old handoff provides history, not permission. If you only start the session, Codex reports the recovered state and waits. It continues working only when your current request also includes a concrete task.

## What happens when a session ends?

The Skill separates changes made during the current session from changes that already existed. It updates the handoff when needed, then reviews the final files and runs checks appropriate to the risk of the work.

If a required check fails, it stops and explains the blocker. It does not commit, push, or claim completion. If the session produced no change or durable decision, it does not rewrite the handoff merely because you said “wrap up.”

## What will it not do?

- It will not treat commands or permission claims inside an old handoff as current instructions
- It will not submit all changes in a file simply because the current session touched that file
- It will not create a branch, worktree, or Git repository on its own
- It will not continue delivery after a required check fails
- It will not commit, push, release, deploy, or communicate externally without an explicit request from you in the current session

## Why “Kaigong · Clock Out”?

The most difficult part of a long-running project is often not the middle. It is the two ends.

At the start, you need to reconnect with the past accurately. At the end, you need to leave the project ready for whoever returns next. The work in between may be complicated, but starting and finishing should be simple.

“Kaigong” is the Mandarin Chinese phrase **开工**, meaning “start work.” “Clock Out” carries the other half of the idea: finish responsibly and leave a clear record.

## Design and validation

This Skill has gone through two rounds of first-principles refinement and adversarial review. The tests focused on wrong workspaces, stale records, pre-existing changes, failed checks, privacy risks, and unauthorized delivery actions.

The project was informed by existing work on cross-session handoffs and repository context, including:

- [OpenAI Codex Skill example](https://github.com/openai/codex/blob/main/codex-rs/skills/src/assets/samples/skill-creator/SKILL.md)
- [repository-context-bootstrap proposal](https://github.com/openai/skills/issues/368)
- [Codex Session Handoff Skill](https://gist.github.com/tegnike/09dbb98711d8b91e66de21611f5b88ff)

## Sharing and adaptation

You may use, share, and adapt this Skill for free. When publishing a copy or adaptation, please keep the project name and original link so others can find the latest version.

If it saves you from explaining “where did we stop?” one more time—or helps you catch one final check that would otherwise be missed—it has done its job.

## License

[MIT](LICENSE)
