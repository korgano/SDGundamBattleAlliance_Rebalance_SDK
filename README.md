# SDGundamBattleAlliance_Rebalance_SDK

SD Gundam Battle Alliance stat rebalance SDK for retoc.

Currently, only stats can be modded via this method, due to lack of knowledge regarding where enemy spawns are set and controlled.

## Required Software

To mod SD Gundam Battle Alliance, the following software is required:
- [retoc](https://github.com/trumank/retoc) - a command prompt program for extracting and repackaging Unreal uAssets for games using UTOC/UCAS/PAK. [(Compiled version here.)](./Pre-Edited%20Assets/retoc-03-2025.zip)
- [uAssetGUI](https://github.com/atenfyr/UAssetGUI) - GUI for editing uAsset files.
- Visual Studio Code - Optional, for JSON asset edits.

## Key Commands

There are two key commands for modding this game:

### Extract Assets

Here is an example command for extracting all datatables used by the game:

```
.\retoc.exe --override-container-header-version PreInitial to-legacy "E:\SteamLibrary\steamapps\common\SDGundamBA\SDGundamBA\Content\Paks" "E:\SteamLibrary\steamapps\common\SDGundamBA\SDGundamBA\Content\Paks\Extracted" -f GOP_
```

Change drive letters, destination (second file path), and filter (text after `-f`) as necessary.

### Pack Mods

Packing mods after completing your edits is simple, and does not require access to the game, only retoc.

To properly pack mods, you **MUST** follow the example folder structure:

`..\[ModName]\SDGundamBA\Content\Data\Gop`

Attempting to pack mods from the `SDGundamBA` folder **WILL** render mods unusable.

The command to pack mods is as follows:

```
.\retoc.exe --override-container-header-version PreInitial to-zen -v --version UE4_27 "[FilePath]\[ModName]" "[FilePath]\[ModName]\zMod_[ModName]_P.utoc"
```

`zMod_` ensures that your content loads after all game assets load.

`_P.utoc` ensures that the game treats your mod as a patch. retoc will automatically generate matching UCAS and PAK files to match the file name of your mod.

## Where to Find Stats

To find stats, check out the [Stat Locations page](./Documentation/sdgba_stats.md).

## Mod Warning

Only **ONE** mod can change values in a uAsset at a time. If multiple mods attempt to mod the same file (for example, `GOP_UnitMS.uasset`), major issues may occur.

To mitigate this, the Pre-Edited Assets folder has several assets that have been modded with changes that users may want. You can tune them as necessary for your own mods.

## Credits

- korgano for documentation and extracted assets
- trumank for retoc
- SD Gundam Battle Alliance dev team for their work on the game