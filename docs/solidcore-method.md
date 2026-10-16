# solidcore method

Repo: Rust port of NVIDIA SMLib (B-rep kernel). Fork: Ian-cmd-ops/solidcore.
Upstream: tangency-labs/solidcore. Local clone: ~/Projects/solidcore.

Read first: AGENTS.md in the repo, then plan/PROGRESS.md and plan/STATUS.md.

Goals: no unsafe, no panics on bad input, deterministic results, no global
state, wasm32 build, match the C++ to 1e-9 relative with identical topology.

Checks before each commit:
  cargo fmt --all --check
  cargo clippy --workspace --all-targets -- -D warnings
  cargo test -p solidcore
  cargo check -p solidcore --target wasm32-unknown-unknown

Difftest needs the C++ reference (usd-brep at c9c5979, built by
harness/cpp/build.sh) and the cpp feature:
  cargo run -p difftest --features cpp -- --unit <unit id>

Contribution rule: one PR per port unit. Draft PR titled "port: <unit id>".
Booleans and fillets are not ported yet. Check plan/PROGRESS.md before you
plan boolean work.

Repo path: /home/ian/Projects/solidcore
Run cd /home/ian/Projects/solidcore before any repo command.
Paths such as plan/PROGRESS.md are relative to that folder.
