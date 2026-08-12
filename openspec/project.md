# Project Context

## Purpose

IDR fork of [webrtc-rs/rtc](https://github.com/webrtc-rs/rtc): Sans-I/O WebRTC
stack used by agent-sdk façades (`idr-ice`, `idr-turn`, etc.). Prefer external
adapters in agent-sdk; record every IDR-specific protocol change in
`docs/idr-upstream-delta.md`.

## Tech Stack

- Rust crates (`rtc-ice`, `rtc-turn`, `rtc-stun`, PeerConnection, …)
- Sans-I/O protocol cores with deterministic-time discipline where applicable

## Project Conventions

### Architecture Patterns

- `origin` = `https://github.com/idrto/rtc.git`
- `upstream` = `https://github.com/webrtc-rs/rtc.git`
- Fork policy and sync notes live under `docs/`

### Git Workflow

- Default branch `master`
- Document applied deltas before shipping IDR protocol patches

## Domain Context

As of the current baseline, **no IDR-specific protocol code changes** are
applied. Mode-2 ICE+QUIC and TURN façades live in agent-sdk. Proposed future
deltas (selected path events, pre-DTLS demux) are listed in the upstream delta
registry.

## Important Constraints

- Do not silently diverge from upstream; every applied patch needs a registry entry
- Prefer upstreaming when suitable

## External Dependencies

- Upstream webrtc-rs/rtc
- Consumers: idrto/agent-sdk
