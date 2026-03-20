# HârnWorld Location Module: Khuzdul Outpost
[![Version (latest)](https://img.shields.io/github/v/release/toastygm/hm-loc-ko)](https://github.com/toastygm/hm-loc-ko/releases/latest)
[![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https%3A%2F%2Fforge-vtt.com%2Fapi%2Fbazaar%2Fpackage%2Fhm-loc-ko&colorB=4aa94a)](https://forge-vtt.com/bazaar#package=hm-loc-ko)
[![GitHub downloads (latest)](https://img.shields.io/badge/dynamic/json?label=Downloads@latest&query=assets[?(@.name.includes('zip'))].download_count&url=https://api.github.com/repos/toastygm/hm-loc-ko/releases/latest&color=green)](https://github.com/toastygm/hm-loc-ko/releases/latest)

Khuzdul (Dwarven) Outpost is a "Location Module" for the Foundry VTT system. It is designed to depict
a long-abandoned Khuzdul (Dwarven) outpost. This location module is designed for the
[HârnWorld](https://columbiagames.com/harnworld/) fantasy setting; however, this manor
could be adapted to exist anywhere in any fantasy setting.

Although designed for use with the [HârnMaster](https://foundryvtt.com/packages/hm3)
system, this module is mostly system-agnostic.  Detailed descriptions of the actors
has been provided in journal entries to facilitate conversion to other game systems.

This outpost could be located anywhere, but on Hârn the most likely locations would be
Orbaal or Kaldor.

# Maps

The original maps from this work have been used as inspiration, and new maps have been
designed specifically to meet the requirements of the VTT environment.  The following
maps are part of this module.

## Khuzdul Outpost

First level.

<img src="assets/scenes/ko1.webp" alt="Khuzdul Outpost First Level" width="600"/>

Second level.

<img src="assets/scenes/ko2.webp" alt="Khuzdul Outpost Second Level" width="600"/>

# Credits

This module is made possible by the hard work of HârnWorld fans,
and is provided at no cost. This work is an adaptation of the article
[Khuzdul Outpost](https://www.lythia.com/harnworld/settlements/khuzan-outpost/) available at the HârnWorld
fan site [Lythia.com](https://www.lythia.com/).

**Writer:** Kerry Mould

**Original Maps:** Thomas Shook

**Adapted to Foundry VTT:** Tom Rodriguez

This module is "[Fanon](https://www.lythia.com/about/publishing-fan-written-material/)",
a derivative work of copyrighted material by Columbia Games Inc. and N. Robin Crossby.

Some assets used to create the maps in this module are from
[Forgotton Adventures](https://www.forgotten-adventures.net/).


# Development

Requires Node.js >= 24.

## Project structure

- `assets/packs/<name>/unique/` — source JSON files for each compendium pack
- `assets/templates/module.template.json` — module manifest template (version/URLs are injected at build time from `package.json`)
- `scripts/init.js` — ScenePacker integration
- `utils/` — build scripts

## Common tasks

```sh
npm install                  # install dependencies (first time / after pulling)
npm run deploy:qa            # build and deploy to local QA Foundry instance
npm run deploy:release       # build and create build/dist/module.zip
npm run release              # create GitHub release (needs GITHUB_TOKEN)
npm run clean                # remove build/
```

## Making content changes

Edit the JSON files in `assets/packs/<name>/unique/`. These are the source of truth — LevelDB packs are compiled from them at build time.

## Deploying locally for testing

Set environment variables for your Foundry data paths (in `.env.local` or your shell):

```
FOUNDRYVTT_DEV_DATA=/path/to/foundry/dev
FOUNDRYVTT_QA_DATA=/path/to/foundry/qa
FOUNDRYVTT_PROD_DATA=/path/to/foundry/prod
```

Then `npm run deploy:qa` (or `:dev` / `:prod`) will build and rsync to that instance.

## Releasing

1. Bump the version in `package.json`
2. Commit and push to `main`
3. `npm run deploy:release` — builds and creates `build/dist/module.zip`
4. `export GITHUB_TOKEN=$(gh auth token)` (or set in `.env.local`)
5. `npm run release` — creates a GitHub release with `module.zip` and `module.json` attached
