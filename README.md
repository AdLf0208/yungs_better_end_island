# YUNG's Better End Island — a Horizon port

**YUNG's Better End Island** is a Minecraft mod. Enhances the Ender Dragon arena. This repository is a **port of it to [Horizon](https://github.com/horizon-rust/horizon)**, the Rust engine for Minecraft Java 26.3. It carries the complete source of the port plus the content files it ships, and installs as a single `.hmod` package.

Upstream: [YUNG-GANG/YUNGs-Better-End-Island](https://github.com/YUNG-GANG/YUNGs-Better-End-Island) — licence **LGPL-3.0-only**.

| | |
|---|---|
| Upstream mod | YUNG's Better End Island ([source](https://github.com/YUNG-GANG/YUNGs-Better-End-Island)) |
| Ported to | Horizon 0b14f8a, Minecraft Java 26.3, mod API `0.2` |
| Package | `betterendisland.hmod` (install it with the Horizon launcher) |
| Licence | **LGPL-3.0-only** — the upstream mod's licence; see [Licence and credit](#licence-and-credit) |

## What this port implements

- **Read the jar's `data/` before believing the brief's shape.** This mod is
- **`/place template` is the right in-game probe for a data-only structure
- **Audit palette states against `.local/horizon-client/26.3/facts.json`**
- **A content `.hmod` may hold `icon.png` at its root** (the `cargo
- **`/fill` is capped at 32,768 blocks per command** at this pin, and
- **The End's arena is features, not structures**, so the SDK's

## Not yet ported

No omissions are recorded for this slice; `notes.md` is the authoritative list.

## Installing

1. Install the [Horizon launcher](https://github.com/horizon-rust/horizon/releases) (0.2.70 or newer).
2. Add `betterendisland.hmod` to the instance's mods.
3. The package is pinned to a specific Horizon build; the launcher checks that pin.

## Licence and credit

YUNG's Better End Island was created by its upstream authors; the code, models and assets in the original mod
remain theirs and are used here under **LGPL-3.0-only**. The Rust in this repository is a clean-room
rewrite for Horizon, not a translation of the original source.

- `LICENSE` — the upstream licence text.
- `LICENSE-NOTICE.md` — what this port carries and where it came from.
- The upstream project: https://github.com/YUNG-GANG/YUNGs-Better-End-Island

## Technical details

```
horizon-mod.toml   package manifest (id, version, api, [native] pin)
Cargo.toml         the crate; depends on `horizon-mod-api` from the fetched SDK
src/               lib.rs (the one `impl Hooks`), runtime.rs (pure logic + tests), glue
assets/ data/      the content the package ships
tools/             content generators and the e2e scenario
```

- Build: `cargo horizon-mod build` (packages; it does not compile against the game).
- Test: `cargo test`, `cargo clippy --all-targets -- -D warnings`.
- In-game: `ports/tools/launcher-game.sh run betterendisland` in the campaign tree, or install the
  `.hmod` and play; the harness scenario is `tools/e2e.sh`.

This repository is generated from the campaign's port at `ports/betterendisland/`; the port's own
`notes.md` is the full record (decisions, traps, evidence).
