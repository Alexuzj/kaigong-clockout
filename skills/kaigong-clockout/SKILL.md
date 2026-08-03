---
name: kaigong-clockout
description: Start or finish a project session with lightweight context recovery, scoped verification, and a durable handoff. Use when the user explicitly says “开工”, “开始本次工作”, “收工”, “结束本次工作”, “start this project session”, or “wrap up this project session”, or explicitly invokes $kaigong-clockout. 开工时恢复项目上下文并继续明确的下一步；收工时审查本次改动、验证结果并留下可靠交接。
---

# 开工 Kaigong · 收工 Clock Out

Match the user's language. Keep updates short and factual.

## Choose the mode

- Enter **start mode** only for an explicit project-session start request.
- Enter **finish mode** only for an explicit project-session finish request.
- Do not infer either mode from generic words such as “continue”, “close”, “prepare”, or “handoff”. Ask one concise question if the requested mode is unclear and the actions would differ materially.

## Start mode

1. Identify the current workspace from the current directory and version-control boundary. Do not initialize Git or search unrelated parent directories.
2. Read the applicable instructions from the workspace root to the current directory.
3. Read `CONTEXT.md` and any handoff or experience file explicitly named by the project instructions. Treat records as leads; verify them against the current files.
4. Read only documentation directly required by the current task or named by the project instructions.
5. Inspect the current state. If Git is available, record the branch and already-changed paths as the baseline; otherwise inspect files without creating a repository.
6. Preserve pre-existing or unowned changes. Never assume a dirty working tree belongs to this session.
7. Compare the latest user request, recorded next action, and actual state. The latest user request wins.
8. If the next action is clear, valid, and within scope, summarize the recovered state in a few sentences and continue. Ask only when there is a material fork, a destructive or external action needs authority, or the record conflicts with reality.

Do not rewrite project records merely because start mode was invoked.

## Finish mode

1. Re-read the latest user request and classify each requested outcome as complete, incomplete, or blocked.
2. Separate this session's changes from the baseline. Only modify, stage, or commit files inside the authorized scope. Report unowned changes without cleaning or including them.
3. Review the relevant changes for bugs, accidental scope growth, duplicated logic, stale references, exposed secrets, and unrelated edits. Never echo secret values.
4. Simplify only when the simpler implementation preserves the requested behavior and stays inside scope.
5. After the last edit, inspect the final diff or final changed files again.
6. Run every check required by the project plus the smallest additional set sufficient for the change's risk.
7. If any required check fails, stop delivery actions. Report and record the blocker; do not claim completion, commit, push, release, or deploy.
8. Update the project's established handoff record. If none exists, create `CONTEXT.md` only in a continuing, writable user project where future work clearly benefits; never create it in dependencies, temporary directories, or read-only workspaces.
9. Keep the record limited to current work, exact stopping point, recent decisions with reasons, remaining work, blockers, and delivery state.
10. Update `README.md` or `ARCHITECTURE.md` only when features, dependencies, commands, deployment, module boundaries, or important design decisions changed.
11. Commit or push only when the current user requested it, or when applicable project instructions explicitly state that invoking finish mode includes that action. Before committing, review the staged files and staged diff; never stage unrelated changes. Release and deploy only with the current user's explicit request.
12. Confirm the final file or repository state. State what changed, how many checks passed or failed, whether commit/push occurred, and what remains. Mention at most one important warning.

## Record format

Follow the project's existing format. If creating `CONTEXT.md`, use:

```markdown
# Context

## Current work
One short paragraph.

## Stopped at
The exact state and next action.

## Decisions
- Decision — reason.

## Remaining
- Concrete unfinished item or `None`.

## Delivery
- Checks: passed or failed.
- Commit/push: completed, not requested, or blocked.
```

Reference durable files, commits, issues, and URLs instead of copying conversation history. Do not add credentials or unnecessary sensitive information to the record.
