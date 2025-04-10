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

## Retoc GUI

Retoc GUI is a Tuw implementation based on Unreal modder Narknon's earlier JSON code.

![Retoc TUW GUI set to pack mod files with Container Override, version set to UE4_27, folder path to assets, and filename set.](/Documentation/Images/retoc-gui-tutorials-01.png)

To pack a mod, do the following:
- Set `Container Override` to `PreInitial`.
- Click browse and find the folder containing your modded files.
- Copy the folder path from the modded files path, paste it in the `Output .utoc File` box.
- Tack on your mod's file name to the end of the path.
- Set engine version to `UE4_27`.
- Optional: Set a file name in a `Batch file name` to create a script for redoing the command.

To switch to extracting content, click `Menu` in the top left corner, then pick `Unpack GUI`:
![Retoc TUW GUI with selector for repacking and unpacking IOstore assets open in the top left corner.](/Documentation/Images/retoc-gui-tutorials-02.png)

To extract files from the game, do the following:
![Retoc TUW GUI with selector for repacking and unpacking IOstore assets open in the top left corner.](/Documentation/Images/retoc-gui-tutorials-03.png)

- Set `Container Override` to `PreInitial`.
- Click browse for `Input path` and find the folder containing the game's `Content/Pak`.
- Click browse for `Output directory` and set your output folder.
- Optional: check the boxes for skipping conversion/compression of shader libraries.
- Optional: Use a filter like `-f GOP_` to select specific files to extract.

## Where to Find Stats

To find stats, check out the [Stat Locations page](./Documentation/sdgba_stats.md).

## Mod Warning

Only **ONE** mod can change values in a uAsset at a time. If multiple mods attempt to mod the same file (for example, `GOP_UnitMS.uasset`), major issues may occur.

To mitigate this, the Pre-Edited Assets folder has several assets that have been modded with changes that users may want. You can tune them as necessary for your own mods.

## Credits

- korgano for documentation and extracted assets
- trumank for retoc
- Narknon for the original Tuw GUI for retoc
- matyalatte for Tuw
- SD Gundam Battle Alliance dev team for their work on the game