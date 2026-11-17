# Source of the ReBirth simulator page

The page one level up runs the firmware of the ReBirth RP2040 pattern sequencer,
compiled to WebAssembly (`../core.js`). This folder is the complete
corresponding source of that build, under the GNU General Public License v3.0
(see `LICENSE`).

- `src/`, `include/`: the firmware, unmodified, as of commit 8a1833a of its
  repository (branch `claude/pad-keys`: `master` plus the last-note rule, clip
  copy, the piano-roll Pattern view, note entry from a MIDI keyboard, and the
  pads as a keyboard while a step is held).
- `test/fakes/`: host-side stand-ins for the Pico SDK headers.
- `sim/core/`: the virtual board around the firmware.
- `sim/build.sh`: builds the native core and, with Emscripten, `core.js`.
- `sim/test/`: checks. The Node checks load the page scripts from `sim/web/`:
  copy `index.html` and the `.js` files from one level up into `sim/web/` first.
- `sim/README.md`: what is real, what is modelled, and what the simulator does not show.

The page scripts (`app.js`, `artist.js`, `device.js`, `rig.js`, `acid.js`) are
served as written, one level up. `dsp.js` there is the x0xb0x filter model from
[x0xb0x VCF Bench](https://github.com/cozycactus/x0xb0x-vcf-bench), copied
unchanged from its commit 8384696 (CC0). `manual-ru.pdf` is the user manual.

Behaviour of the original ReBirth RB-338 is taken from
[OpenRB-338](https://github.com/pingw33n/openrb-338) (also GPL-3.0).
