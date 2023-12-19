# Medpack Filter System

## Contents
- Overview
- Filter item Functionality
- Setting up the items to be included in the filter
- Text based GUI
- Icon based GUI
- Drag and Drop

## Overview
There's 2 Filter Items: Marker and Plastic wallet. The plastic wallet (PW) acts as a filter for the medpack, The player drags and drops the PW onto the medpack then
is applied to the medpack, For each of the 3 repacking system (drag n drop, repack all functor, medpack gui) before moving the item to the medpack, it should check if
the item is included in the filter, if so it can be moved, if not then it's not accepted and a message displays saying so. 

## Filter Item Functionality
### Plastic Wallet
The Plastic Wallet just like any medpack is stored in a cache table which is saved and loaded through callbacks. The id of each plastic wallet is saved in the medpack table
whenever D&D'd on to a medpack for accessing PW variables. It can then be removed from the medpack via a custom functor injection belonging to the medpack which removes the 
most recent PW D&D'd into the medpack. 

Each PW should have the following variables: 
|Variable      |Type  |
|--------------|------|
|medpack_id    |number|
|filter_id     |number|
|filter_section|string|
|filter_items  |table |

Each Medpack should have the following variables in addtion to the existing ones: 
|Variable   |Type     |
|-----------|---------|
|filters    |table    | 
|max_filters|number   |

### Effects on Repacking System
#### General
"filter_items" table is called before performing the repacking. As filter_precond function that gets said table from FILTERS table and does a key check against an items section/name
 
#### Drag n Drop
Checks if current item is in the "filter_items" table if so add to medpack, if not display message and return nothing

#### Repack All Functor
Before adding to contents and removing existing item from inventory, perform the same check as D&D

#### Medpack GUI
Before transfering items to the medpack menu, check if the item/section is in the "filter_items" table if so allow transfer, if not display screen message

#### Side Effects
The Unpacking system in all applicable cases should be able to perform as orginially intended before the filter system is inplace.

## Setting up the items to be included in the filter
To allow for a wide range of customisation and organisation, there's 3 different ways that have a broad scope of applicability: 
- Adding item to the filter via typing out the names of said items (Text based GUI), 
- Selecting from a range of icons which has items belonging to a catergory (like the indicators on medical items) which any item inside that catergory are applied to the
  filter (Icon based GUI), 
- Dragging and dropping an item onto the PW in which an icon reprenting that item will be combined with the PW. 
Determining which GUI to use will be available via MCM but activated by the same right click menu functor.

### Text based GUI
#### Elements: 
- Medium sized window, 
- A title stating how many medical items can be accepted to the filter, 
- An list of medical items to choose from, 
- Input text box that displays the selected medical items, 
- 2 buttons: one to set the filter and another to close the GUI.

#### Functionality: 
Intitated by the right click menu functor, the player reads the title displaying the max items to select, then scrolls through the list and clicks on the
items to be choosen, when choosen it's highlighted and added to the text box. 

Once finished setting the filter items the player then clicked the set filter button and the choosen filter items are added to the list of filter items using that PW's id into the "filter_items" table var, then exits. 

If there are no choosen filter items then the "filter_items" table var is left alone and exits without touching anything. From the table "filter_items" a series of icons are made then combined on the bottom of the PW.

### Icon based GUI
#### Elements: 
- Medium-Large sized window, 
- 5 Tabs with each Catergory grouping as the text, 
- Series of icons displaying a catergoy with the catergory name above, 
- 3 Buttons: One to set the catergory, one to display a help window, one to close the window, 
- Display box for any messages and also which catergories have been selected, 
- Display box showing the max catergory number.

#### Functionality: 
The player selects an icon in any catergory group then that icon is highlighted and in the display box updates a message saying which icon is selected, if the player selects the same icon it highlights red for a second then unhighlights and is removed from the display box. 

If an icon is selected and the selected catergories are a max it unselected and unhighlights then displays a message saying max catergories has been reached for PW. 

The set catergory button works the same as the one in the TBG, so does the close, execept for "set catergory" instead of item icons, it's icons respective of the selected catergory. 

The Help button displays a item descrption window which displays a string explaining how to use the GUI.
 
### Drag and Drop
The player D&Ds an item onto a PW and then it's added to the "filter_items" table for the most recently inserted PW. If the PW is at the Max items per filter, no more items can be D&D'd, a message displays stating such.