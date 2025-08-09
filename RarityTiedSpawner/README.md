Rarity Tied Spawner (RTS) is a mod for HBS's Battletech computer game. It is a small, focused mod with a single purpose - adjusting the rarity of units based on their tags. The mod's homepage is https://github.com/BlueWinds/RarityTiedSpawner, where you can always find the most up to date source code.

RTS is distributed under the GNU General Public License v3.0 license. Special permission is granted to Battletech Advanced: 3062 and Roguetech to distribute this alongside Custom Bundle and other proprietary code. Please reach out to BlueWinds on github, or the BTA discord for more details.

## `moreCommonTags`
In settings.json, `moreCommonTags` is a dictionary of tags, mapping each to an integer.

When the game spawns random units for a lance, it makes a list of all units that match the lance's tags. For each unit, RTS then calculates a `toAdd` value based on its tags, and pushes that many copies of the unit onto the list.

Think of it as a bunch of raffle tickets in a hat. If a unit matches a tag in `moreCommonTags`, then RTS puts additional copies of that unit into the hat the game pulls from. Simple.

`toAdd` can be negative in the configuration, but the total can never go below 0. `"unit_never_spawn": -1000` will not remove the initial copy of a unit from the list, but it will counteract any other `moreCommonTags` the unit might also have.

## Dynamic tags

In addition to predefined `moreCommonTags`, you can build "dynamic" tags in one of the following formats:

- `unit_rarity_{X}` (eg `unit_rarity_3`) - Adds {X} entries to the spawn list
- `{targetTag}_unit_rarity_{X}` (eg `ClanWolf_unit_rarity_2`) - Adds {X} entries to the spawn list if the `RequiredTags` for the slot in the lance have the {targetTag}.
- `not_{targetTag}_unit_rarity_{X}` (eg `not_unit_heavy_unit_rarity_3`) - Adds {X} entries to the spawn list if the `RequiredTags` for the slot do *not* have the {targetTag}.
