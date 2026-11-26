# Demo: surviving a quota death in 5 minutes

A walkthrough of one real handoff. No setup — just read the two sessions.

## Session 1 — Agent A starts, then dies

You paste the [start prompt](prompts/start.md). Agent A replies with its 3-line check:

> Goal: add a heartbeat pulse under the BGM at critical health.
> Last checkpoint: none — fresh start.
> Next: write the micro-step checklist into HANDOFF.md and commit it.

It works in micro-steps. Two commits land:

```
e4f5a6b  feat: pulse oscillator in src/audio/pulse.ts (step 2/6)
9ab12cd  WIP: health hook written, threshold check missing
```

Then the quota dies mid-file. Nothing is lost: the half-finished file is a `WIP:` commit, and `HANDOFF.md` section 3 says exactly where it stopped (see [the filled example](examples/filled-handoff.md)).

## Session 2 — Agent B (a different model) takes over

Hours later, you open a *different* agent and paste the [handoff prompt](prompts/handoff.md). It replies:

> Goal: heartbeat pulse under BGM at critical health.
> Checkpoint: step 3/6, WIP commit 9ab12cd — health hook written, threshold check missing.
> Next: open src/battle/health.ts, add the threshold check, wire pulse.start()/stop().

Three lines, all matching the file. It does **not** redo steps 1–2. It does **not** touch anything in section 5 (Off-limits). It finishes step 3, commits, ticks the checkbox.

## What just happened

| Without a baton | With a baton |
|---|---|
| New agent re-reads the whole repo and guesses | Reads 1 file + git log |
| Re-does finished work "to be safe" | Section 2 is verified by commit hashes |
| Resurrects a feature you deleted last week | Section 5 forbids it, in writing |
| Half-written file lost when the session died | `WIP:` commit + section 3 note |

## Try it yourself

1. Copy `templates/HANDOFF.md` into any project you are building with an AI agent.
2. Fill sections 1 and 5 (five minutes, once).
3. Start your next session with `prompts/start.md`.
4. Kill the session on purpose halfway. Start a new one with `prompts/handoff.md`.
5. Check the 3-line repeat-back against your file. That is the whole demo.
