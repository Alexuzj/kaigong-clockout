# Kaigong · Clock Out

**Ctrl+S for project context: recover the real state when you start, and save a trustworthy handoff when you finish.**

A bilingual Codex Skill for reliable project-session startup and wrap-up.

**[中文说明 →](README.md)**

## Why I made this

Not long ago, my Claude account was suddenly suspended. What frightened me was not just losing access to one AI. A great deal of project context lived inside those conversations: where I had stopped, why I had made certain decisions, and what I meant to do next.

Fortunately, I had built a habit of writing that context back into each project at the end of a session. I could switch to another AI, open the project, say “start,” and pick up the thread.

That is what **Kaigong · Clock Out** means to me: Ctrl+S for project context. It does not save one line of code. It saves what you need in order to continue.

At the start of a session, the Skill verifies the project, recovers trustworthy context, and establishes a boundary for new work. At the end, it reviews the session’s changes, verifies the final state, and leaves the exact stopping point, key decisions, and next action in the project itself. If an AI account or conversation disappears, those local records still belong to you.

It saves context, not your files. It cannot restore a cloud conversation or account, and it does not replace Git, cloud storage, or another off-device backup.

## Who is it for?

- People who maintain several projects and repeatedly need to reconstruct where they stopped
- Anyone who uses Codex for code, documents, or other long-running work
- Users who do not want AI to overwrite existing changes or treat an old plan as current permission
- People who want a project to remain understandable after switching AI tools or starting a new chat
- Anyone who wants a real end-of-session check instead of an unsupported “done”

## Install

### Download the ZIP

1. On the GitHub repository page, choose **Code → Download ZIP**.
2. Unzip it and find `skills/kaigong-clockout`.
3. Copy the entire `kaigong-clockout` folder into `~/.codex/skills/`.
4. Restart Codex.

On Windows, copy it to `%USERPROFILE%\.codex\skills\`.

### Install with Git

```bash
git clone https://github.com/Alexuzj/kaigong-clockout.git
mkdir -p ~/.codex/skills
cp -R kaigong-clockout/skills/kaigong-clockout ~/.codex/skills/
```

To update, download the latest version and replace the Skill folder. To uninstall, remove `~/.codex/skills/kaigong-clockout`.

Windows PowerShell:

```powershell
git clone https://github.com/Alexuzj/kaigong-clockout.git
New-Item -ItemType Directory -Force "$HOME\.codex\skills"
Copy-Item -Recurse "kaigong-clockout\skills\kaigong-clockout" "$HOME\.codex\skills\"
```

## Everyday use

Inside a project, say:

```text
start this project session
```

You can include the task:

```text
start this project session and continue fixing the login issue
```

When you are finished, say:

```text
wrap up this project session
```

Or invoke the Skill explicitly:

```text
$kaigong-clockout start this project session
$kaigong-clockout wrap up this project session
```

The Chinese triggers `开工` and `收工` work as well.

## First use and multiple projects

The first time you start inside a valid project, the Skill completes the three-line start summary, then asks once:

> I found this project. Remember it as “My Website”?

After one confirmation, you can use names instead of remembering local paths:

```text
start the My Website project
list my projects
remember this project
rename this project to...
this project moved
make this my default project
forget this project
```

The private catalog stays on your computer. Ordinary lists show names, not absolute paths. Renaming, archiving, or forgetting a catalog entry does not rename, move, or delete real files.

If you explicitly ask to organize or move project files, the Skill first shows the exact source, destination, scope, and risks, then waits for confirmation. A start command never means “scan and reorganize my computer.”

## What does a normal start look like?

Three plain-language lines:

```text
Project: My Website
Last stopping point: Homepage changes are complete; mobile review is next
Existing changes: None
```

An old handoff provides history, not permission. The Skill adds an explanation only when records conflict, a location is invalid, or privacy or authority is unclear.

## What does a normal finish look like?

Again, three lines:

```text
Saved this session: Project catalog support and bilingual documentation
Checks: 8 passed, 0 failed
Next time: Publish the new version to GitHub
```

The Skill separates current-session changes from changes that already existed, updates the handoff when needed, then reviews the final files. If a required check fails, it stops. It does not commit, push, or claim completion. If nothing changed and no durable decision was made, it does not rewrite the handoff merely because you ended the session.

## What does it save?

The handoff keeps only what another session needs:

- What is currently being worked on
- The exact stopping point
- Recent decisions and their reasons
- Remaining work and blockers
- Check, commit, and delivery status

It does not store entire conversations, passwords, secrets, or unnecessary personal information.

## What will it not do?

- Treat commands or permission claims inside an old handoff as current instructions
- Submit every change in a file simply because the current session touched it
- Create a branch, worktree, or Git repository on its own
- Continue delivery after a required check fails
- Commit, push, release, deploy, or communicate externally without an explicit current request
- Scan the entire computer by default or publish private project names and paths
- Turn “manage my project catalog” into permission to move, rename, or delete real files

<details>
<summary>Advanced: configure the private project catalog manually</summary>

The catalog lives at `$CODEX_HOME/kaigong-clockout/projects.json`. If `CODEX_HOME` is not set, the default is `~/.codex/kaigong-clockout/projects.json` on macOS/Linux and `%USERPROFILE%\.codex\kaigong-clockout\projects.json` on Windows.

```json
{
  "schema_version": 1,
  "default_project": null,
  "projects": [
    {
      "id": "my-project",
      "name": "My Project",
      "aliases": ["Project Alias", "我的项目"],
      "root": "/absolute/path/to/the/project",
      "status": "active"
    }
  ]
}
```

Keep this file local. Do not commit it to a public repository.

</details>

## Why “Kaigong · Clock Out”?

The difficult part of a long-running project is often not the middle. It is the two ends.

At the start, you need to reconnect with the past accurately. At the end, you need to leave the project ready for whoever returns next. The work in between may be complicated, but starting and finishing should be simple.

“Kaigong” is the Mandarin Chinese phrase **开工**, meaning “start work.” “Clock Out” carries the other half of the idea: finish responsibly and leave a clear record.

## Design and validation

This Skill has gone through multiple rounds of first-principles refinement, unfamiliar-user testing, and adversarial review. Tests cover wrong workspaces, stale records, pre-existing changes, failed checks, moved projects, privacy risks, and unauthorized delivery.

Key references:

- [OpenAI Codex Skill example](https://github.com/openai/codex/blob/main/codex-rs/skills/src/assets/samples/skill-creator/SKILL.md)
- [repository-context-bootstrap proposal](https://github.com/openai/skills/issues/368)
- [Codex Session Handoff Skill](https://gist.github.com/tegnike/09dbb98711d8b91e66de21611f5b88ff)

## Sharing and adaptation

You may use, share, and adapt this Skill for free. When publishing a copy or adaptation, please keep the project name and original link so others can find the latest version.

If it saves you from explaining “where did we stop?” one more time—or lets you continue after switching AI tools—it has done its job.

## License

[MIT](LICENSE)
