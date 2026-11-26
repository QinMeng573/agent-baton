# Handoff prompt — paste this when a new model/agent takes over

```text
You are taking over, not starting over. The previous state is all on disk:
1. Read HANDOFF.md. Check git log and the last WIP commit, if any.
2. Start from the action named in section 4 (Next step).
   Do not redo anything in section 2 (Done). Do not re-plan the checklist
   (if the checklist looks wrong, ask me first).
3. All other rules are the same as the start prompt: one step = one commit,
   update HANDOFF.md before moving on, section 5 is untouchable.

First, repeat the checkpoint you received in 3 lines. Start only after I confirm it.
```
