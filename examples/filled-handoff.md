# HANDOFF (filled example — from a real game project)

## 1. Goal
Add a low heartbeat pulse under the BGM when the player is at critical health.
Acceptance: pulse audible at critical health; stops automatically after healing; normal BGM is not drowned out.

## 2. Done
- [x] Step 1: micro-step checklist for this round (commit: a1b2c3d)
- [x] Step 2: `src/audio/pulse.ts` — pulse oscillator created (commit: e4f5a6b)

## 3. In progress
Step 3/6: health hook in `src/battle/health.ts` written, threshold check missing.
WIP commit: 9ab12cd.

## 4. Next step
Open `src/battle/health.ts`, add the critical-health threshold check, call `pulse.start()` / `pulse.stop()`, build, commit, tick step 3.

## 5. Off-limits & locked decisions
- Grid shockwave tiles: flat solid fill + border + piece emblem only. No gradients, no noise texture.
- Flames only on true-damage tiles.
- Deleted effects/features must not return under the name of a "fix" or "optimization".
- `cloudsave.ts` and the login / ads wiring must not be modified or removed.
