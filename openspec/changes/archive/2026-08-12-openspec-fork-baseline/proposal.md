# Proposal: OpenSpec baseline for IDR rtc fork

## Intent

Introduce OpenSpec and capture the fork policy / empty applied-delta baseline so
assistants do not invent rtc patches when agent-sdk façades suffice.

## Scope

- `openspec/` init + `project.md`
- `specs/fork-policy` mirroring `docs/idr-upstream-delta.md` intent

## Approach

Document only; no protocol code changes.

## Impact

Clearer cross-repo guidance with agent-sdk TURN/ICE work.
