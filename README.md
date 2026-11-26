# agent-baton

**Your AI coding agent ran out of quota mid-task. The next model knows nothing. Now what?**

`agent-baton` is a zero-install, file-based handoff protocol for AI coding agents.
No plugin. No database. No memory service. Just one markdown file + git.

> Plan first, saved to disk. One micro-step, one commit. Half-finished work gets committed too.
> The model is replaceable — the ledger on disk is not.

## The problem

Claude, GPT, Gemini — every coding agent is amnesiac:

- Context window fills up → early decisions get compressed away
- Quota runs out in minutes on large tasks → work stops mid-file
- You switch models → the new one re-does finished work, or worse, resurrects things you deleted

Chat history is not a ledger. This repo gives you one.

## How it works (30 seconds)

1. Copy [`templates/HANDOFF.md`](templates/HANDOFF.md) to your project root.
2. Start every session by pasting [`prompts/start.md`](prompts/start.md) to your agent.
3. When quota dies or you switch models, paste [`prompts/handoff.md`](prompts/handoff.md) to the next agent.
4. The new agent reads `HANDOFF.md` + `git log`, repeats the checkpoint back in 3 lines, then continues — without redoing a single finished step.

## The 5-section handoff file

`HANDOFF.md` never changes structure. Any model can scan it in seconds:

| Section | Contents |
|---|---|
| 1. Goal | One sentence + 2–3 acceptance criteria |
| 2. Done | Only steps with a real commit hash |
| 3. In progress | Current micro-step, exact file/function, what's missing |
| 4. Next step | The very next action, named to file level |
| 5. Off-limits | Locked decisions. Deleted features stay deleted. |

Section 5 is the one most people skip — and the one that matters most.
It's the only defense against an agent "helpfully" re-adding what you removed.

## Micro-steps, not minutes

Never size a step by time. A step that takes 15 minutes can die at minute 2,
and everything unsaved is air.

A step = **one file, or one function, or one independently verifiable change.**
Done means: a commit exists, and a checkbox in `HANDOFF.md` is ticked.
Half-finished? Commit it anyway, prefixed `WIP:`, noting where you stopped.

## Works with

Claude Code · Cursor · Antigravity · Windsurf · Aider · any agent that can read files and run git.

**Hands-on demo:** [DEMO.md](DEMO.md) — a 5-minute walkthrough of a quota death and a clean takeover.

## Example

See a filled-in handoff from a real project: [`examples/filled-handoff.md`](examples/filled-handoff.md)

## Why not a memory plugin?

Plugins are great — until the tool changes, the service is down, or you switch agents.
A markdown file in your repo survives all of that. It diffs, it rolls back, it reviews in a PR.

## License

MIT
