# Super Yoshi Derby

Unofficial, noncommercial Nintendo fan-game prototype. Eight racers, two mount types, eleven selectable riders, five championship tracks. Original procedural pixel artwork; no ripped game sprites, music, or reference-image pixels are included.

**Intended website (NOT DEPLOYED OR VERIFIED):** https://jellomel.github.io/SUPER-YOSHI-DERBY/

**Proposed repository:** https://github.com/jellomel/SUPER-YOSHI-DERBY

## Play locally

Extract the package. From this directory run `python3 -m http.server 8080`, then open http://localhost:8080. Use a local HTTP server because the game uses JavaScript modules. Phaser 3.90.0 is bundled, so playing does not require a CDN, server backend, account, or paid service.

1. Choose a rider, Yoshi or Koopa, color, and mode.
2. Start the championship. The chosen pair is racer ★ in lane one.
3. Spectator mode automatically controls all eight competitors. In manual mode your mount accelerates automatically; you time jumps and boosts.
4. Continue through five worlds. Points per finishing position are 15, 12, 10, 8, 6, 4, 2, 1. Highest total wins. Ties use the last race finish order.
5. New Championship returns to selection.

## Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Accelerate | — | Tap to Run pad (manual mode) |
| Jump | Space or Up | Jump button |
| Boost | Shift or X | Boost button |
| Pause / resume | P | Pause button |

Keyboard race shortcuts apply when focus is outside form controls. Click the track after changing selections. Backgrounding the tab pauses the race.

## Phone portrait play

On phones the game uses a taller 600 × 720 logical canvas so all eight lanes remain visible. A compact touchpad stays at the bottom above the safe area, alongside Jump and Boost. Choose Manual Racing and tap **TAP TO RUN** repeatedly for extra mount speed. Each tap adds speed up to a cap; speed decays when you stop tapping. Taps are limited to one per 120 ms. Both mount types support this control. Spectator mode remains automatic.

## Features

- Mario, Luigi, Wario, Waluigi, Peach, Daisy, Toad, Bowser, Bowser Jr., Donkey Kong, Rosalina.
- Every rider can use either mount; six colors; larger artwork for heavy riders.
- Eight visible lanes, start gates, scrolling environment, running animation, jump arc, boost trails, changing positions, finish line and results.
- Yoshi acceleration and longer jump duration; Koopa endurance, boost recharge and faster collision recovery. Rider choice adds a small deterministic speed bonus.
- Randomized pacing, AI decisions and obstacle placement; no predetermined winner.
- Yoshi’s Island, Underground Caverns, Haunted Forest, Bowser’s Castle, Rainbow Road; longer tracks, denser hazards and tougher AI obstacle checks.
- Responsive interface, touch controls, visibility pause, standings and championship podium.

## Development

`npm test` runs model and mocked scene/UI lifecycle tests; no dependency install required. `node --check src/game.js` checks scene syntax.

- `src/model.js`: race physics, AI, race data, scores. Separate from Phaser for repeatable tests.
- `src/game.js`: Phaser renderer and UI/championship flow.
- `style.css`, `index.html`: responsive shell.
- `vendor/phaser.min.js`: pinned Phaser 3.90.0, MIT licensed; see `vendor/LICENSE.phaser.txt`.
- `tests/`: simulation, mount/rider matrix, randomized winners, collision recovery, mocked rendering and complete five-race UI flow.
- `.github/workflows/pages.yml`: tested static deployment to GitHub Pages from `main`.

## Deployment, pending owner authorization

The owner authorized uploading and publication. Public deployment remains unverified until the Pages workflow completes and the website is checked.

After authorization, create or reuse the repository, push these files on `main`, select **Settings → Pages → Source: GitHub Actions**, and run the included workflow. Verify the public URL, engine loading, race completion, manual controls and mobile layout before marking deployment complete. The workflow uses relative asset paths for project Pages hosting.

## Verification and remaining polish

Seven automated tests pass, including 40 randomized races and a complete mocked five-world UI flow. Browser rendering, real keyboard/touch input and mobile performance have NOT been verified: the permitted browser QA capability is unavailable in the current environment. These checks remain required before public release.

World hazards currently use lane obstacles themed as logs, rocks, ghosts, Thwomps and stars. Falling-rock timing, moving Thwomps, traversable cave tunnels and surprise ghost behavior are future enhancements. Artwork is a compact procedural pixel interpretation, rather than an extensive hand-drawn sprite set. No audio is included. Offscreen trailing racers are clamped to the left edge to keep all eight visible; rankings use actual race distance.

## Fan-game publication decision

Nintendo character names and recognizable designs can raise copyright and trademark concerns even when the project is free, noncommercial and uses newly drawn assets. A disclaimer does not grant permission, and the project may receive a takedown request. No Nintendo rights are licensed here. Seek qualified advice or rights-holder permission for publication decisions.

An original-character alternative can retain the gameplay with renamed riders, original dinosaur/turtle mounts, original environments and a new title such as **Shell & Saddle Derby**, removing Nintendo-specific designs and branding. Choose this option before public deployment if desired.
