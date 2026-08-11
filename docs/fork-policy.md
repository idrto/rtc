# Fork Policy — idrto/rtc

## Purpose

`idrto/rtc` is a **thin fork** of [webrtc-rs/rtc](https://github.com/webrtc-rs/rtc). It must remain understandable to an upstream WebRTC.rs maintainer who knows nothing about IDR.

## Remotes

```text
origin   = https://github.com/idrto/rtc.git
upstream = https://github.com/webrtc-rs/rtc.git
```

Do not rewrite upstream history. Prefer explicit upstream **merge** commits over rebasing long IDR history.

## What may change in this fork

Only **generic** WebRTC / ICE enhancements that could reasonably help other WebRTC.rs users:

- Expose nominated / selected ICE pair metadata and events
- Standalone ICE-driving conveniences
- Sans-I/O hook improvements
- Protocol correctness and browser interoperability fixes
- Tests and docs for the above

Before modifying code, ask:

> Could this capability reasonably be useful to another WebRTC.rs user?

If **yes**, design it as a candidate upstream PR (no IDR terminology in public APIs).  
If **no**, implement it in `agent-sdk` instead.

## What must never enter this fork

- IDR Presence client
- IDR FQHN routing
- IDR proxy / billing / quotas / device registration
- IDR transport preference or QUIC orchestration
- WireGuard
- Flutter / Dart / FFI
- Product telemetry
- IDR-specific certificates

## Upstream-first checklist for every fork patch

1. Make it generic
2. Document it in `docs/idr-upstream-delta.md`
3. Add tests
4. Evaluate upstreamability
5. Avoid IDR branding in API names (`selected_candidate_pair`, not `idr_quic_path`)

## Related docs

- [idr-upstream-delta.md](./idr-upstream-delta.md) — applied/proposed deltas
- [upstream-sync.md](./upstream-sync.md) — how to sync from upstream
- Upstream `docs/semver.md` — API stability toward 1.0
