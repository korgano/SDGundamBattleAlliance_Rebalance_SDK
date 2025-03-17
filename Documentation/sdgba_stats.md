# Stat Locations

The game stores a wide variety of statistics in various data tables, which are basically Unreal Engine spreadhseets. Chagning specific values or outright deleting rows from these tables can alter the behavior of the game.

## GOP_UnitMS:
All mobile suit/mobile armor statistics, including Balance (hidden stagger stat).
![GOP_UnitMS data table example - 00 Quanta with 162 rows of data points.](./Images/GOP_UnitMS.jpg)

By default, boss units have a Balance value of `1000000` (one million).

Edited GOP_UnitMS.uasset with boss `Balance` stat set to `200000` is available for use as a base mod file.

## GOP_UnitArms:
Controls ships, ELS, and Aires(?) stats.
![GOP_UnitArms data table example - White Base, with all defense values set to 0.](./Images/GOP_UnitArms.jpg)

## GOP_PartsBase:
Contains template for the randomly generated effects parts, as well as parts generated from defeating specific enemies.
![GOP_PartsBase data table example - Infighter Auto-repair part.](./Images/GOP_PartsBase.jpg)

`RollPar` numbers control part spawning based on unit role (Infighter, All-Rounder, Sharpshooter), `NumPar[1-3]` control some sort of value (base stat?), `Param[1-3]` are used in DLC parts. Interaction between `NumPar` and `Param` is unclear.

`SelectType[1-3]` controls how the effect for a part is chosen. Options are:
- `EPartsSelectType::NONE`
- `EPartsSelectType::FIX`
- `EPartsSelectType::RANDOM`

When using `EPartsSelectType::FIX`, the corresponding `SelectId[1-3]` field **MUST** contain a `PARTSEFFECT_` value.

When using `EPartsSelectType::RANDOM`, the `SelectId[1-3]` field **MUST** contain one of the following values:
- `GroupId` value (see below) for `SelectId1`
- `ALL` for `SelectId2-3`

When using `EPartsSelectType::NONE`, the corresponding `SelectId[1-3]` field **MUST** contain an `ALL` value.

## GOP_PartsEffect:
Controls drop rates for effects when randomly generating effect parts (uncertain about this). Also tracks which ones are debuffs.
![GOP_PartsEffect data table example - Base HP Up.](./Images/GOP_PartsEffect.jpg)

Known `GroupId` values: 
- BASE_GROUP
- ATK_GROUP
- WEAPON_GROUP
- REDUCE_GROUP
- GUARD_GROUP
- MOVE_GROUP
- RPAIR_GROUP
- DROP_GROUP
- HATE_GROUP
- DEBUFF_ONLY
- UDM_GROUP
- UNIQUE_GROUP

## GOP_Missions:
Controls mission timer, what enemies are displayed on the selection screen.
![GOP_Mission data table example, with LimitTime set to 9999.](./Images/GOP_Mission_modded.jpg)

Set `EnableTimeLimit` to 9999 and `EnableTimeLimit` to `EMissionEnable::DISABLE` to disable mission timers.

`CollectItemTime` controls the gap between end of mission and auto-exit.

`EnemyId0` through `EnemyId23` control the enemies that display on the mission select screen. Enemies display from left to right based on their number. `EnemyId0` will always be the last unit displayed on the right.

`EnemyId#` DOES NOT control spawns. It exists to alert players to what rare/important enemies appear in the mission.

TBD: Whether spawns are controlled by `LevelFile`.

Edited GOP_Mission.uasset with unlimited mission time and `CollectItemTime` set to 60 is available for use as a base mod file.

## GOP_Mission_HetereoBreak:
Seems to control variants of Chaos missions. Duplicates many fields from GOP_Mission.
![GOP_Mission_HeteroBreak data table example, showing many duplicate fields from GOP_Mission.](./Images/GOP_Mission_HeteroBreak.jpg)