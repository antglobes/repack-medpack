# Repackable Medpacks
Conversion of vanilla medpacks to reusable ones that allow for additional storage/inventory optimisation.

## Features
1. Instant Random Unpack/Repack of Availalble Medical items
2. Out of the box compatiblity with BHS/BHSRO
3. Inventory Similar UI for item selection
4. Purchasable at any Medic
5. Ability to Add any item to the medpacks contents (Requires some script and ltx tweaks)
   
### Unpack/Repack
- As a right click menu option (rcmo) you can unpack all the contents of the medpack or repack all the available medical items from your inventory, into the medpack until it's max weight, this is done at random. 
- (For greater control see feature 3).

### BHS/BHSRO Compatibility
- BHS/BHSRO is a soft requirement of this addon, it's not needed for it to function but alot of anomaly players do use BHS/BHSRO in their runs, support for this has been included i.e no patch required.

### Medpack GUI
- Whilst being able to fill up or unload our medpack with ease, having greater control for organisation or sorting reasons might be ideal for you.
- A Simple GUI is implemented for you to move items between the medpack and your inventory, both will update themselves and shouldn't have conflicts with most UI related addons. (let me know otherwise)

### Medic Trading
- Repackable Medpacks will only be found at Medics, so if you are going for a traditional loner start with this mod, don't expect to see any until you get to Rostok.

### Modifiable Medpack Contents
- There will be a file with greater explanation in to how to add any item to the medpack but the short version is:
- You will need to add it to the dedicated "config_list" table in the "rpmk_medpack.script" file and ensure that it has a standard item ltx section.

## Installation
### M02
- Download the mod, M02, DLTX/Modded Exes, MCM
- Place the zip file in M02 downloads folder
- Right click on the zip from within M02, it should be underneath the downloads tab next to the data tab
- Click Install
- Select Main
- Done

### Manual
- Copy across the gamedata folder
- DONT COPY ACROSS THE FOMOD FOLDER
- Done
  
### Requirements
- [MO2](https://github.com/ModOrganizer2/modorganizer) (optional but preferred)
- [DLTX](https://github.com/themrdemonized/STALKER-Anomaly-modded-exes)
- [BHS](https://www.moddb.com/mods/stalker-anomaly/addons/100-groks-body-health-system-redux-for-151) (optional)
- [BHSRO](https://www.moddb.com/mods/stalker-anomaly/addons/bhs-realistic-overhaul) (optional, BHS required if using see their requirements)
  
## Future Implementations
- Drop item after certain condition
- Redesign GUI Textures
- Russian/Ukrainian Translation

## License
[GNU GPL 3](https://www.gnu.org/licenses/gpl-3.0.en.html)

## Conflicts
- Ravenascendent, nltp_ashes, xcvb, mrdemonized: helping me out with my dumb qs.
  
## Known Issues
- None as of v1.0
  
## Changelog
- v1.0 Base Version