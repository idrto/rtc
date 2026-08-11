# IDR Upstream Delta Registry

This document records **every** IDR-specific or IDR-motivated change to the webrtc-rs `rtc` fork.

## Current baseline

| Field | Value |
|-------|--------|
| Fork HEAD | `b0ab7f405b5d0eebf1ad2d6cd37095ee1a491a05` |
| Upstream project | https://github.com/webrtc-rs/rtc |
| Upstream suitability of current tree | Identical in intent to upstream Sans-I/O `rtc` `0.21.0-alpha.1` |
| **IDR-specific code changes** | **None** |

As of the creation of this file, the IDR fork has not modified upstream-owned protocol code for IDR product features. Remotes and documentation for fork maintenance have been added under `docs/` only.

## Remotes

```text
origin   = https://github.com/idrto/rtc.git
upstream = https://github.com/webrtc-rs/rtc.git
```

## Delta registry

No applied patches yet. Candidate future entries use this template:

```yaml
id: IDR-RTC-XXX
purpose: short description
affected_files: []
reason_external_adapter_insufficient: |
  Why an agent-sdk adapter alone is not enough.
upstream_suitability: true|false
upstream_issue_or_pr: ""
conflict_risk: low|medium|high
removal_condition: |
  When this delta can be dropped (e.g. upstream exposes equivalent API).
status: proposed|applied|upstreamed|removed
```

### Proposed (not applied)

```yaml
id: IDR-RTC-001
purpose: expose nominated/selected ICE path-change on PeerConnection public events
affected_files: []
reason_external_adapter_insufficient: |
  SelectedCandidatePairChange exists on rtc-ice::Agent but PeerConnection
  currently consumes the internal event for DTLS only and does not surface it.
upstream_suitability: true
upstream_issue_or_pr: ""
conflict_risk: low
removal_condition: upstream exposes equivalent public PeerConnection event
status: proposed
```

```yaml
id: IDR-RTC-002
purpose: optional ICE demux / app datagram bypass before DTLS
affected_files: []
reason_external_adapter_insufficient: |
  Shared ICE (Mode 1) for QUIC + WebRTC needs non-STUN bytes to be classifiable
  as DTLS vs opaque app traffic; today IceHandler forwards only to DTLS.
upstream_suitability: true
upstream_issue_or_pr: ""
conflict_risk: medium
removal_condition: upstream provides a generic pre-DTLS demux hook
status: proposed
```

```yaml
id: IDR-RTC-003
purpose: public nominated candidate-pair getter if distinct from selected
affected_files: []
reason_external_adapter_insufficient: |
  nominated_pair is pub(crate); callers can use get_selected_candidate_pair.
  Only needed if nomination must be observed before final selection.
upstream_suitability: true
upstream_issue_or_pr: ""
conflict_risk: low
removal_condition: upstream public API or Mode 2 remains sufficient
status: proposed
```

## Policy

Every applied fork patch **must** be recorded here before merge to the IDR default branch. Prefer adapters in `agent-sdk` over new deltas. Keep this list short.
