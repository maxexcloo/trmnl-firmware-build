# trmnl-firmware-build

Automated build pipeline for [maxexcloo/trmnl-firmware](https://github.com/maxexcloo/trmnl-firmware), a fork of the [TRMNL](https://usetrmnl.com) open-source firmware.

## How it works

Every 15 minutes this repo checks whether there are new commits on the `main` branch of the firmware fork. If there are, it builds all PlatformIO environments in parallel and publishes a GitHub release with the compiled binaries.

No changes are made to the firmware source repo — it stays stock.

## Releases

Each release is tagged `build-{short_sha}` and contains one `.bin` file per environment, named by environment (e.g. `trmnl.bin`, `TRMNL_X_PAPERS3.bin`).

Pre-releases correspond to regular commits. Releases without the `build-` prefix correspond to tags in the firmware repo.

## Manual builds

Trigger a build from the [Actions tab](../../actions/workflows/build.yml) using the **Run workflow** button. You can optionally specify a branch, tag, or full SHA to build; leaving it blank builds the latest `main`.

## Environments

Environments are discovered automatically from the firmware repo via `scripts/list_build_envs.py`. Any environment added upstream will be picked up on the next build.

## Source repo

- Firmware fork: [maxexcloo/trmnl-firmware](https://github.com/maxexcloo/trmnl-firmware)
- Upstream: [usetrmnl/trmnl-firmware](https://github.com/usetrmnl/trmnl-firmware)
