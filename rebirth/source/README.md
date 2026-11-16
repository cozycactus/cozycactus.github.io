# Source of the ReBirth simulator page

The page one level up runs the firmware of the ReBirth RP2040 pattern sequencer,
compiled to WebAssembly (`../core.js`). This folder is the complete
corresponding source of that build, under the GNU General Public License v3.0
(see `LICENSE`).

- `src/`, `include/`: the firmware, unmodified (commit 20125c2 of its repository).
- `test/fakes/`: host-side stand-ins for the Pico SDK headers.
- `sim/core/`: the virtual board around the firmware.
- `sim/build.sh`: builds the native core and, with Emscripten, `core.js`.
- `sim/test/`: checks. The Node checks load the page scripts from `sim/web/`:
  copy `index.html` and the `.js` files from one level up into `sim/web/` first.
- `sim/README.md`: what is real, what is modelled, and what the simulator does not show.

The page scripts (`app.js`, `artist.js`, `device.js`, `rig.js`) are served as
written, one level up.

Behaviour of the original ReBirth RB-338 is taken from
[OpenRB-338](https://github.com/pingw33n/openrb-338) (also GPL-3.0).
