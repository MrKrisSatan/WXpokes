# Weather Variants

Weather-form Pokémon for [Weather FX](https://github.com/MrKrisSatan/Weather-fx).
Up to 1,103 persistent weather forms can register when their base species is
available. A WX form can replace its base Pokémon only when that base Pokémon
is a native encounter on the current map and matching Weather FX weather is
active.

Weather Variants does not draw weather itself. It requires Weather FX and can
be installed or updated independently.

## Install

Import the release ZIP through gen1recomp's mod manager, or place the mod in
your `mods/` folder alongside Weather FX. Then make sure **WX POKEMON** is `ON`
in Weather Variants' settings.

The manifest points gen1recomp's updater at `MrKrisSatan/WXpokes`, so newer
release ZIPs can be offered through **Update / Versions**.

## Evolution and artwork inheritance

WX Pokémon evolve by the **same method and requirement as their base form**.
The mod copies the base evolution rule exactly and changes only the destination
to the matching WX form when that weather-form lineage exists. Level, stone,
trade, friendship and custom evolution-method metadata are left unchanged. If
no matching WX evolved form exists, evolution falls back to the normal evolved
species rather than becoming stuck.

WX forms deliberately use the **base species artwork**. Battle sprites, summary
and Pokédex sprites, evolution/trade/Hall of Fame art, and party-menu icons are
resolved from the base species at draw time. Follower and overworld integrations
also remap WX species to their base species. Compatible sprite packs therefore
only need to replace the normal Pokémon art once and WX forms follow it.

## What you get

- **300 core WX forms** for the original Kanto roster.
- **Up to 470 extended forms for species #152-386**, registered whenever their
  base species and required types exist.
- **Up to 240 modern forms** for compatible expanded-dex installations.
- **94 Primalweather Legendary/Mythical gifts**. A holiday visitor can appear
  in the player's home on New Year's Day, Valentine's Day, St Patrick's Day,
  Easter Sunday, Halloween, Christmas Eve, Christmas Day, Boxing Day and New
  Year's Eve and give one level-5 registered Primalweather gift per holiday per
  save per year. Full storage does not consume the claim.
- **Persistent caught forms**. Turning WX POKEMON off stops new substitutions
  without deleting Pokémon already caught.

With `gen1recomp-national-dex`, WX forms register as forms of their base species
rather than flooding the main Pokédex with synthetic species numbers.

## Wild encounter rules

Current gen1recomp builds use the documented `encounter.species` seam after the
normal encounter has been chosen, with an `encounter.roll` fallback for older
engines and a dedicated fishing bridge. The base species must genuinely exist
on the map's native encounter table before a WX substitution is allowed.

Current and legacy Weather FX weather IDs are recognised, including light and
heavy rain, primal rain, thunderstorm, snow, sleet, harsh sun and strong winds.

## Settings

| Setting | Effect |
| --- | --- |
| **WX POKEMON** | Enables/disables new weather-form wild substitutions. |

Rarity tuning lives in this mod's own `config.lua`.

## Version 1.2.1

- WX evolution rules now inherit the base form's method and requirements
  exactly and only redirect the evolved species when a matching WX form exists.
- Added live base-art resolution through gen1recomp's `pokemon.sprite` and
  `pokemon.icon` hooks, covering battles, summaries, Pokédex, evolution,
  trades, Hall of Fame and party menus.
- Compatible visual-overhaul mods that replace base Pokémon art now carry
  through automatically to WX forms.
- Retains the v1.2.0 wild-spawn fix and holiday Primalweather gift system.

## Troubleshooting

**No WX Pokémon appear:** make sure Weather Variants' **WX POKEMON** is `ON`
and Weather FX's **WEATHER** is not `OFF`.

**A later-generation WX form is missing:** its base species and every required
type must exist in the merged game data.

**A caught form loses data after an update:** report the `WX_###_...` species ID
because that is a save-compatibility bug.

## Credits

Weather-form roster, typing and Pokédex text: **MrKrisSatan**.
