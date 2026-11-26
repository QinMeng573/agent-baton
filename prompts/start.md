# Start prompt — paste this as the first message of every session

```text
Do not write code yet. In order:
1. Read HANDOFF.md in the project root, especially section 5 (Off-limits).
2. Check the last 10 entries of git log and git status. Confirm the branch and checkpoint.
3. Repeat back in 3 lines: the goal, where the last session stopped, and the next step.
If your summary doesn't match HANDOFF.md, stop and ask me. Do not guess.

Then follow the micro-step rules:
- Split this round's work into a micro-step checklist (one file / one function per step),
  write it into HANDOFF.md and commit it BEFORE writing any code.
- After each step: commit first, then tick the step in HANDOFF.md and update sections 3-4.
- Half-finished work gets committed too, prefixed WIP:, noting the exact function and what's missing.
- Work single-threaded on the current branch only. No parallel sub-tasks.
- Never modify or re-add anything listed in section 5, even as an "optimization".
- If you hit quota / rate-limit signs: stop new work immediately.
  WIP-commit, update the checkpoint in HANDOFF.md, report the checkpoint in 3 lines, then stop.
```
