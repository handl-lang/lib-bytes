# lib-bytes

`bytes` — byte-buffer primitives for the `Bytes` scalar type
(`from_list`/`to_list`, concat, slice, len, at, UTF-8 coding).

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the interface — `cap`/`op` declarations (ADR-0077/ADR-0160) |
| `src/bytes.test.hnl` | `.hnl` tests |
| `src/lib.rs`, `src/ops.rs` | Rust atoms / transitional impl crate |
| `atoms.yaml`, `Cargo.toml`, `xtask/` | atom registry + Rust crate + gate |
| `pkg.hnl`, `scripts/hnl-gate.sh` | manifest + `.hnl` gate |
| `workflows/gate.yaml` | CI — shared `handl-gates` campaign |

## Contract

- Transitional layout: the interface is `.hnl`; implementations are
  native `op` atoms (plugin-lib-stdlib side).
- Deps resolve from git — a plain clone test-runs as-is, no sibling
  checkouts needed.

## Verification

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
cargo xtask gate        # fmt --check → clippy -D warnings → test → doc
```

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
