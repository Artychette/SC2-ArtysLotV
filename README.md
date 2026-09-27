# Arty's Legacy of the Void - SC2 mod basis

This is a base for modded LotV campaign (in the vein of Kit's WoL) that make the War Council and the Top bar easier a lot easier to customize (and possibly other things to come), mostly via a replacement for the voidstory dep. <br/>
If played as is, there should be no differences with the vanilla campaign with the exception of the achievements that are disabled on map init (and possibly i made the holo models a tiny bit smaller in the war council...). 
If you find something is off, by all mean, yell at me.

## Notes on Copyright License

Blizzard stance on mod's intellectual property is very vague, hence it is not clear if mods are Blizzard's or the modder's property. For this reason, no copyright license are provided but for all intent and purposes consider this under a copyleft license

## Dependencies

Requires [**Arty's Misc. Tool**](https://github.com/Artychette/SC2-AMT) mod.

## Manual hook 
If need be (say you already have several mission finished) you can hook the mod to your campaign without much trouble :
- If your LotV maps still use `void(story)` dependency, then add said dep in your main mod (or any mod shared by all maps), then remove it from the maps  
- Save the maps in component folder, if not already done.
- For the story maps (pstory01 and epiloguestory01), before saving go into the data editor, `gameplay data` tab (in the `Edit Advanced Game Data` submenu) , `Default SC2 Gameplay Settings` entry, open the `Trigger Libraries` field and clear blank the `Include Path` field for any the `VoiC`, `VCMI`, `VCST` or `VCUI` entry (there should be only 2 of them)
- Go into the map folder (story maps included), open the `MapScript.galaxy` file in notepad (or whatever soft you like to use). There should be a handful of include statements at the top of the file : <br/><br/>
Change `include TriggerLibs/VoidCampaignLib` into `include LibVoiC` <br/>
Change `include TriggerLibs/VoidCampaignStoryLib` into `include LibVCST` <br/>
Change `include TriggerLibs/VoidCampaignMissionLib` into `include LibVCMI` <br/>
Change `include TriggerLibs/VoidCampaignUILib` into `include LibVCUI` <br/><br/>
They are never all present (only 2 or 3, depending of the map), do not add the missing ones (should not cause any bug, but "if you don't need it, don't use it").
 
- Open whatever mod that directly use the voidstory dep : open the dependancy menu, remove `void(story)` and put the ArtyLotV dep in its place (you need to keep the order intact, e.g. if void(story) was first, then put this in first).

## Changes

### War council changes
- Units are shown (per category) in order of the Army Units list of the corresponding Army Category data entry (as in vanilla). You can have from 1 to 16 units per category (there is an auto-pagination system so evertything fit on the screen) ; it is not required that all categories hold the exact same number of unit.
- Details of each specific variant are defined in the `Campaign Tech Unit` user-type (as in vanilla). "Holo-model" for the variant is picked from the `UIUnit` field (the input unit must have a linked unitactor and a model). When displayed, the ready sound and the glossary anim set in the unitactor are launched, then the baseline anim (stand-index) is looped. Camera and auto-rotation setting are defined respectively in the `Tech Purchase Camera` and `Tech Purchase Speed` field of the model (a 0 speed let you manually rotate the model, as in vanilla, if the unit has the `turnable` flag on). All macro (i repeat, ***macro***, not *event macro*) in the `macro` field of the unitactor are also run upon display.
- A `Add Holo Glaze` macro can be added to the macro of a unit ('s unitactor) if you want to give it a "hologram" look. It's a band-aid, don't expect miracle out of it.
- Added a bunch of `UI_ArmyRoom_FactionButton` models (the "colored glowing fumes" around the faction icons) for the faction. You can change them in the `GlowModel` field of the `Army Factions` user-type
- As a side bonus of my script, you can add your own custom factions as you wish and assign any unit to those (because, no, this wasn't possible)

### Top Bar Changes
Use the top bar system of my tool mod instead of the vanilla trigger. You can change what top bar setting is loaded on mission start in the TopBarTemplate field of the Maps user-type. "[Default]" or empty entry means no top bar is loaded (if you don't want top bar at all, or if you need to handle it manually during the mission)
The link to the tools mod have the instruction on how to customize it
 
