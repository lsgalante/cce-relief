# cce-relief

The DE's relief editors. Read the workspace guide (`../cce-compositor/WORKSPACE.md`)
first; this file covers only what is particular to this crate. The relief itself — the
wall and edge profiles, the finish, the frost, the config keys they write — is
documented in `../cce-ui/CLAUDE.md` ("The relief is two shapes", "The surface config
shape"), since every app draws it.

## Shape

Two binaries, both launched by name by other apps (cce-data-editor's `(bevel)` and
`(ramp)` previews, cce-grid's line relief), so the names must not change:

- `src/main.rs` — **`cce-relief`**: a relief shape shown as a lit cross-section of the
  edge, shaped by Shoulder / Base / Bias, with the shading strip under it, the Finish
  and Frost columns, and Save (the shared config, a retargeted file, or one
  `--key <flat.path>` value). Its slider positions are its own state, not style:
  `~/.config/cce/cce-relief/state.kdl` (`knob_state`). Save writes the current
  spellings and removes every retired key it finds; it is the migration for them.
- `src/bin/cce-ramp.rs` — **`cce-ramp`**: a ramp spec editor, `--key <flat.path>`
  writing the spec back to that value.

Until 2026-10-08 both were bins of the cce-ui crate, which installed them with the
toolkit; they moved out because an app does not belong in the toolkit.

## Build, test, run

```sh
cargo build -p cce-relief
cargo test  -p cce-relief
ccebuild install cce-relief     # installs both bins
```
