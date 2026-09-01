# WX Pokes / Weather Variants

WX Pokes adds persistent weather-adapted Pokémon forms to [Weather FX](https://github.com/MrKrisSatan/Weather-fx) for gen1recomp and gen2recomp.

## Version 1.4.0

Version 1.4.0 expands WX Pokes into a complete weather-form matrix for the first 386 Pokémon.

- **10,808 WX forms:** every Pokémon from Bulbasaur (#001) through Deoxys (#386) gets a form for each of Weather FX 4.35.32's 28 non-clear weather types.
- **50% matching-weather wild conversion:** after the game rolls a normal wild Pokémon, it has a 50% chance to become its WX form when the matching weather is active.
- **Distinct weather typing:** every WX form receives its own deterministic weather-derived type combination.
- **Distinct weather learnset:** every WX form receives a weather-oriented learnset while keeping the base Pokémon's original level-up milestones.
- **Original progression preserved:** growth rate, EXP progression, evolution level/method and other evolution requirements stay the same as the base species.
- **Abilities on every WX Pokémon:** weather/theme abilities are assigned to every registered form.
- **SPECIAL POWER:** underperforming special-oriented forms can receive this custom special counterpart to Huge/Pure Power. It doubles Special Attack, or Gen 1 Special for special damage, without boosting physical Attack.
- **Base artwork inheritance:** WX forms use the base Pokémon's battle sprites, icons, cries and compatible follower/overworld art.
- **Integrated type charts:** ZyranCZ's Steel/Dark/Fairy and historical/modern typing-chart controls are included directly in WX Pokes.

Examples include **Bloom Pikachu** in Verdant Rain and **Draconic Rattata** during Dragon Storm. The base species still has to be the Pokémon the game actually rolled for that encounter.

## Requirements

- A compatible current gen1recomp/gen2recomp build.
- [Weather FX](https://github.com/MrKrisSatan/Weather-fx), which supplies the live weather state.

Do not install the standalone `steel_typing` mod alongside WX Pokes 1.4.0 because its functionality is already integrated.

## Installation

Import the release ZIP through the mod manager, or place the extracted mod in the game's `mods/` folder alongside Weather FX. Make sure **WX POKEMON** is enabled in WX Pokes and **WEATHER** is enabled in Weather FX.

The manifest points the mod manager at `MrKrisSatan/WXpokes`, so future GitHub releases can appear through the normal **Update / Versions** flow.

## Wild encounter rules

WX Pokes does not increase or decrease the base game's encounter rate. It waits until the game has selected a normal wild Pokémon, reads the current Weather FX weather, and then checks for the matching WX form.

If a matching form exists and is registered:

1. The base Pokémon keeps its normal route/location eligibility.
2. The original encounter level is preserved.
3. WX Pokes rolls an exact **50%** conversion chance.
4. Success replaces the species with the matching WX form; failure leaves the normal species unchanged.

The bridge supports both the newer `encounter.species` path and the long-lived `encounter.roll` path, with a per-encounter guard preventing duplicate 50% rolls.

## Typing, learnsets and evolution

Each WX form has a weather-derived type identity and weather-oriented moves. WX Pokes changes moves only at levels where the base species already learns a move, so it does not invent extra level-up milestones.

Evolution remains tied to the original species. Level, stone, trade, friendship and supported custom evolution methods keep the same requirement. When the corresponding WX evolution exists, a WX Pokémon evolves into the matching weather form of its evolved species; otherwise it safely falls back to the normal evolved species.

## Abilities

Every registered WX Pokémon receives an ability. The selector prefers abilities appropriate to the form's weather and final typing, with a guaranteed non-empty fallback.

**SPECIAL POWER** is a WX Pokes ability for genuinely weak special-oriented forms. It mirrors Huge/Pure Power on the special side:

- doubles Gen 1 Special when calculating special damage;
- doubles Gen 2 / split-system Special Attack;
- never boosts physical Attack;
- is only assigned when the form is special-oriented and the base special offense is weak or significantly behind Attack.

## Artwork and save persistence

WX forms deliberately inherit the base species' visual assets. Compatible sprite packs therefore only need to replace the normal Pokémon art once.

Caught WX forms are persistent species. Turning **WX POKEMON** off prevents new wild substitutions but does not delete already-owned forms.

With `gen1recomp-national-dex`, WX forms can register as forms of their base species rather than flooding the main Pokédex with synthetic entries.

## Other features

The holiday visitor and Primalweather Legendary/Mythical gift system remain included. Supported holidays can grant one level-5 registered Primalweather gift per holiday, per save, per year, without consuming the claim if storage is full.

## Troubleshooting

**No WX Pokémon appear:** confirm WX Pokes is enabled, Weather FX weather is enabled, and the active weather matches the form you are hunting. The base Pokémon must also normally be eligible for that encounter.

**A form is missing:** the base species and any required type support must exist in the merged game data. The integrated GEN VI typing preset supplies Steel, Dark and Fairy support where needed.

**A caught form breaks after an update:** report the exact `WX_...` species ID. Persistent WX IDs are treated as save-compatibility data.

## Credits

Weather-form system, roster design, typing direction and Pokédex text: **MrKrisSatan**.

Integrated Steel/Dark/Fairy and type-chart system: **ZyranCZ**, from `Fairy-Steel-Dark-and-Typing-Charts` v2.0.1.

Weather state and effects are provided by **Weather FX**.
