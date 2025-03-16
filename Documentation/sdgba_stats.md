# Stat Locations

## GOP_UnitMS:
All mobile suit/mobile armor statistics, including Balance (hidden stagger stat).

By default, boss units have a Balance value of `1000000` (one million).

Edited GOP_UnitMS.uasset with boss `Balance` stat set to `200000` is available for use as a base mod file.

## GOP_UnitArms:
Controls ships, ELS, and Aires(?) stats.

## GOP_PartsBase:
Contains template for the randomly generated effects parts, as well as parts generated from defeating specific enemies.

`RollPar` numbers control part spawning (?), `NumPar[1-3]` control some sort of value (base stat?), `Param[1-3]` are used in DLC parts. Interaction between `NumPar` and `Param` is unclear.

`SelectType[1-3]` controls how the effect for a part is chosen. Options are:
- `EPartsSelectType::NONE`
- `EPartsSelectType::FIX`
- `EPartsSelectType::RANDOM`

When using `EPartsSelectType::FIX`, the corresponding `SelectId[1-3]` field **MUST** contain a `PARTSEFFECT_` value.

When using `EPartsSelectType::RANDOM`, the `SelectId[1-3]` field **MUST** contain one of the following values:
- `BASE_GROUP` for `SelectId1`
- `ALL` for `SelectId2-3`

When using `EPartsSelectType::NONE`, the corresponding `SelectId[1-3]` field **MUST** contain an `ALL` value.

## GOP_PartsEffect:
Controls drop rates for effects when randomly generating effect parts (uncertain about this). Also tracks which ones are debuffs.

## GOP_Missions:
Controls mission timer, what enemies are displayed on the selection screen.

Set `EnableTimeLimit` to 9999 and `EnableTimeLimit` to `EMissionEnable::DISABLE` to disable mission timers.

`CollectItemTime` controls the gap between end of mission and auto-exit.

`EnemyId0` through `EnemyId23` control the enemies that display on the mission select screen. Enemies display from left to right based on their number. `EnemyId0` will always be the last unit displayed on the right.

`EnemyId#` DOES NOT control spawns. It exists to alert players to what rare/important enemies appear in the mission.

TBD: Whether spawns are controlled by `LevelFile`.

Edited GOP_Mission.uasset with unlimited mission time and `CollectItemTime` set to 60 is available for use as a base mod file.

## GOP_Mission_HetereoBreak:
Seems to control variants of Chaos missions. Duplicates many fields from GOP_Mission.