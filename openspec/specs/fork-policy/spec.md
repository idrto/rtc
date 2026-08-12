# fork-policy

## Purpose

Document how the IDR `rtc` fork relates to upstream webrtc-rs and when protocol
deltas may be applied.

## Requirements

### Requirement: Empty applied-delta baseline

The fork SHALL record that no IDR-specific protocol code changes are applied
until an entry is added to `docs/idr-upstream-delta.md` with status `applied`.

#### Scenario: Current baseline
- GIVEN the published delta registry
- WHEN an assistant or engineer checks for IDR protocol patches
- THEN the applied list is empty and Mode-2/TURN work is expected in agent-sdk

### Requirement: Registry before apply

Any IDR-motivated change to upstream-owned protocol crates MUST be registered
(id, purpose, files, upstream suitability, conflict risk, removal condition)
before merge to the IDR default branch.

#### Scenario: Proposed Mode-1 helpers stay proposed
- GIVEN proposed deltas for selected-path events or pre-DTLS demux
- WHEN agent-sdk Mode-2 TURN e2e ships
- THEN those rtc deltas remain `proposed` unless explicitly applied
