# mhi2-k3346-carplay-audio-upmix

Stereo to 5-speaker upmix research for CarPlay and, separately, Bluetooth/USB/SD on Audi MHI2 `K3346` / MU1438 (G22/MLB Evo, Tegra3, QNX 6.5, internal amp, retrofit centre speaker, stock sub).

> **Status: inert, not installed in any car.** The audio hook stays disabled (`MHI2_NV_SIX_CHANNEL_QUALIFIED=0`). Not ready for installation.

This is a fork of [ProManiFest2122/mhi2-k3346-carplay-vc](https://github.com/ProManiFest2122/mhi2-k3346-carplay-vc). CarPlay on the Virtual Cockpit, route guidance, D-pad and calls are that project's work, not ours. Our contribution is only the audio side, in [`audio_k3346/`](audio_k3346/).

## What is tested where

| Evidence | Covered |
|---|---|
| Car (read-only and RAM tests, by ear and logs) | MPL1/MPL5 geometry, channel-to-speaker map, centre/sub behaviour, Tegra3 CPU cost, nav-prompt stream |
| Host / ARM-QNX emulator | NVIDIA PCM sink, FDK-AAC bridge, realtime upmix, `LD_PRELOAD` claim of libairplay, installer simulations |
| Not tested | Hook in the real `dio_manager` in a live CarPlay session, BT shim via `medialauncher`, MMI "CarPlay UpMix" row with 3D hidden, independent sub/LFE, on-unit install and restore |

## Where to read

- [`audio_k3346/README.md`](audio_k3346/README.md): layout, integration notes
- [`audio_k3346/REPRODUCE.md`](audio_k3346/REPRODUCE.md): pinned inputs, one-command dependency fetch, what is and is not reproducible
- [`audio_k3346/docs/STATUS.md`](audio_k3346/docs/STATUS.md) and [`INSTALL_READINESS`](audio_k3346/docs/INSTALL_READINESS_20261028.md): open gates
- [`CAR_FACTS_K3346`](audio_k3346/docs/CAR_FACTS_K3346_20261016.md): what was measured in the car
- Upstream discussion: [pull request #3](https://github.com/ProManiFest2122/mhi2-k3346-carplay-vc/pull/3), [issue #4](https://github.com/ProManiFest2122/mhi2-k3346-carplay-vc/issues/4)

## Licence

GPL-3.0-or-later for our code; mixed provenance for the rest, see [LICENSING.md](LICENSING.md) and [`audio_k3346/NOTICE.md`](audio_k3346/NOTICE.md). No warranty. A bad audio hook can mute or distort a head unit.
