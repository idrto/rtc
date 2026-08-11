# Upstream Synchronization

Regular synchronization with [webrtc-rs/rtc](https://github.com/webrtc-rs/rtc) is a core acceptance criterion for this fork.

## Remotes

```bash
git remote -v
# origin    https://github.com/idrto/rtc.git
# upstream  https://github.com/webrtc-rs/rtc.git
```

If `upstream` is missing:

```bash
git remote add upstream https://github.com/webrtc-rs/rtc.git
```

## Sync procedure

Prefer **merge**, not rebase of accumulated IDR history.

1. Fetch upstream:

   ```bash
   git fetch upstream
   ```

2. Create or update a temporary sync branch from the IDR default branch:

   ```bash
   git checkout -B sync/upstream-YYYYMMDD main
   ```

3. Merge upstream main (or the tracked upstream branch):

   ```bash
   git merge upstream/main
   ```

4. Run **upstream-only** tests (workspace tests that do not require IDR):

   ```bash
   cargo test --workspace
   ```

5. Resolve conflicts with **minimal** adapter-preserving fixes. Do not smuggle new IDR product logic into the fork during conflict resolution.

6. Merge the sync branch into the IDR default branch when green.

7. Record the new upstream SHA in [idr-upstream-delta.md](./idr-upstream-delta.md) (baseline table). If any delta patches conflicted, update their entries (`conflict_risk`, status).

8. Notify `agent-sdk` maintainers to bump `rtc_commit` in `docs/compatibility.toml` / Cargo git `rev` pins.

## Do not

- Routinely rebase years of IDR fork history onto upstream
- Force-push the default branch to rewrite shared history without explicit coordination
- Drop delta documentation when resolving conflicts

## After each sync

- [ ] Upstream SHA recorded
- [ ] `docs/idr-upstream-delta.md` still accurate
- [ ] Workspace tests passed
- [ ] agent-sdk pin updated (when agent-sdk depends on this fork)
