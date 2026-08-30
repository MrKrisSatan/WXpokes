# Weather Variants

Weather-form Pokémon for [Weather FX](https://github.com/MrKrisSatan/Weather-fx).
Up to 1,103 persistent weather forms. A WX form can replace its base Pokémon
only when that base Pokémon is a native encounter on the current map and the
matching Weather FX weather is actually happening.

This mod does not draw any weather itself and changes nothing about how
Weather FX looks or behaves. It requires Weather FX to be installed, and does
nothing on its own.

---

## Install

Drop the `weather_variants` folder into your `mods/` folder, or import the
`.modpkg` through the launcher, alongside Weather FX. Both mods can be
installed and updated independently: uninstalling this one leaves Weather FX
exactly as it was before this mod existed, and updating Weather FX does not
require updating this mod (or vice versa) unless a changelog says otherwise.

Then open this mod's own page in the mod manager and check **WX POKEMON** is
`ON` (it is, by default).

### Updates

This package points gen1recomp's native updater at
[`MrKrisSatan/WXpokes`](https://github.com/MrKrisSatan/WXpokes). When a newer
installable ZIP is published in that repository's **Releases**, the launcher
can detect it and offer it through **Update / Versions**. Release assets should
prefer the standard `weather_variants-<version>.zip` name and contain the mod
files at the ZIP root.

---

## What you get

**300 core weather variants**, one to three per base species across the
original 151 plus a second full pass on 1–150, each with its own name,
typing and a small chance to replace a normal wild encounter once its
weather is live. Rain-form Bulbasaur ("Bloom"), Ashfall-form Charmander
("Cinder"), Blizzard-form Gyarados, and so on. See
[`docs/WEATHER_VARIANTS.md`](docs/WEATHER_VARIANTS.md) for the full table.

**Up to 470 extended forms for species #152-386.** These register whenever
the base species exists in the merged game data. Native Gen 2 gets
Chikorita-through-Celebi WX forms without requiring Kanto-Reforged, while
Kanto-Reforged or another compatible dex can expose later rows through Deoxys.

**Up to 240 modern forms**, two weather variants each for a curated
120-species modern roster. They register opportunistically when a compatible
expanded dex provides the base species and required types. See
[`docs/GEN9_WEATHER_VARIANTS.md`](docs/GEN9_WEATHER_VARIANTS.md).

**94 Primalweather Legendary/Mythical gifts** are supported. Mew keeps its
original `WX_300_MEW_PRIMALWEATHER` identity; 93 additional gift-only forms
register when their base species exists. On New Year's Day, Valentine's Day,
St Patrick's Day, Easter Sunday, Halloween, Christmas Eve/Day, Boxing Day and
New Year's Eve, a holiday visitor appears in the player's home and offers one
level-5 Primalweather gift. Each holiday can be claimed once per save per year;
a full party/Boxes does not consume the claim.

**Clean Pokédex integration.** With
[`gen1recomp-national-dex`](https://github.com/sanjinpepic/gen1recomp-national-dex)
installed, every variant registers as a *form* of its base species (synthetic
dex numbers 30000+, invisible on the main list) instead of a new numbered
entry. Variants show up only when you open the base species and cycle forms,
like megas or regional forms.

**A caught variant is permanent.** Turning WX POKEMON off stops *new* wild
substitutions; anything already caught, and its Pokédex/save record, stays
exactly as it was.

---

## Settings

One row, on this mod's own page in the mod manager:

| Row | What it does |
| --- | --- |
| **WX POKEMON** | ON/OFF. Changes take effect on the next wild encounter, no reload. |

Rarity tuning lives in this mod's own `config.lua`, documented inline. It is
separate from Weather FX's `config.lua`.

---

## How it talks to Weather FX

Weather Variants depends on Weather FX and reads the live `WeatherState`,
scene information, and base encounter tables through Weather FX's exported
module namespace. Since Weather FX 4.31 no longer calls back into this mod,
Weather Variants owns the final `encounter.species` rewrite on current
gen1recomp builds, with an `encounter.roll` fallback for older builds. Weather
FX rolls or biases the normal encounter first; Weather Variants then gets
exactly one chance to substitute a matching WX form.

The bridge checks the unmodified route table before substitution. If Weather
FX injects an off-route Water, Ghost, Fire, etc. because of weather bias, that
Pokémon stays its normal form. A WX form appears only on a map where its base
species is genuinely present. Rod encounters use the same final substitution
rule through `encounter.fishing`. Current and legacy Weather FX ids are both
recognised, including `LIGHT_RAIN`/`RAIN_LIGHT`, `THUNDERSTORM`/`STORM`,
`SUN`/`SUNNY`, and `PRIMAL_RAIN`/`HEAVY_RAIN`.

The bridge is backwards-safe: if an older Weather FX build already returned a
`WX_*` encounter, this mod detects it and does not substitute twice.

---

## Troubleshooting

**No weather variants ever appear.** Check this mod's **WX POKEMON** row is
`ON`, and Weather FX's **WEATHER** row is not `OFF`. No active weather means no
variant can qualify.

**An extended variant never shows up.** Extended rows register only when the
base species exists in the merged Pokémon registry and every required type is
available. Native Gen 2 makes #152-251 eligible automatically; later species
need a compatible expanded-dex/content mod.

**A caught variant lost its nickname or moves after an update.** That is a
save-compatibility bug. Please report it with the variant species id
(`WX_###_...`).

---

## Version 1.2.0

- Fixed WX weather variants not spawning in the wild with current Weather FX.
- Uses the current `encounter.species` substitution seam with a legacy fallback.
- Expanded weather-name compatibility across current and legacy Weather FX ids.
- Added the holiday visitor to the player's home.
- Added gift-only Primalweather Legendary and Mythical variants.
- Holiday gifts are always level 5 and limited to one successful claim per holiday per save per year.
- Full party/Boxes no longer consume a holiday claim.

## Credits

Weather-form roster, typing and Pokédex text: **MrKrisSatan**.
