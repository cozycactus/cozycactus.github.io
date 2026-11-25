# Source of the ReBirth simulator page

The page one level up runs the firmware of the ReBirth RP2040 pattern sequencer,
compiled to WebAssembly (`../core.js`). This folder is the complete
corresponding source of that build, under the GNU General Public License v3.0
(see `LICENSE`).

- Built from commit c70c7aaf55c89eae82e8180888816262a4de818a of the firmware repository
  (branch `master`, 2026-11-25: "Merge pull request #31 from cozycactus/claude/sham-live"), with Emscripten 7.0.0,
  by `sim/build.sh web` and checked by `sim/check.sh`.
- `src/`, `include/`: the firmware, unmodified.
- `test/fakes/`: host-side stand-ins for the Pico SDK headers.
- `sim/core/`: the virtual board around the firmware.
- `sim/sh101/`: the SH-101 MCS-48 decoder and virtual board (`../sh101_cpu.js`).
  The page fetches the Roland ROM from a pinned upstream GitHub revision and
  checks its SHA-256. The file picker is available if the download fails.
- `sim/build.sh`: builds the native core and the two WebAssembly modules.
- `sim/test/`, `sim/check.sh`: checks. The Node checks load the page scripts
  from `sim/web/`: copy `index.html` and the `.js` files from one level up
  into `sim/web/` first (without the `?v=` the page adds to their names).
- `sim/README.md`: what is real, what is modelled, and what the simulator does not show.
- `sim/vendor/`: how `three.js` and `handmodel.js` one level up are built.

The page scripts (`app.js`, `artist.js`, `device.js`, `rig.js`, `acid.js`,
`sh101.js`, `sh101_rom.js`, `handrig.js`, `handplan.js`, `handlayer.js`) are
served as written, one level up. `dsp.js` there is the x0xb0x filter model from
[x0xb0x VCF Bench](https://github.com/cozycactus/x0xb0x-vcf-bench), copied
unchanged from its commit 8384696 (CC0). `three.js` (three.js 0.187.0, MIT) and
`handmodel.js` (the hands of Godot XR Tools, CC0) are built from other people's
work by the scripts in `sim/vendor/`; `notices.txt` beside the page holds
their notices. `manual-ru.pdf` is the user manual.

Behaviour of the original ReBirth RB-338 is taken from
[OpenRB-338](https://github.com/pingw33n/openrb-338) (also GPL-3.0).
