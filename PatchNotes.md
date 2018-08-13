## LSC Patch Notes

### Full Release! Version 1.0 Notes
*(August 12th, 2018)*

- The user guide has been brought up to date.
- Added Trade Skill and Transport Path to the first-run setup tool.
- Added a section to the inspector which allows users to input the desired profit for an item, and outputs the required list price of the base (non-crit) item to get that profit. This may later be expanded to allow users to weight the list prices between the base item and crit results, but that will be a much more complicated thing to implement.
- The inspector can now set and use the override value of the item being inspected.
- Reworked the search favorites tooltip. It should be easier to read, and correctly display all relevant information.
- Fixed a crash that occurred when using the interaction menu to remove an item from the watchlist.
- Fixed a potential bug if a search tool was opened or already open when reloading or rebuilding the database.
- Fixed more wiggly text.
- When loading the item database, high/low values are supposed to be verified and updated, if necessary (such as if an item's current value was manually changed in the csv). This wasn't working, and should be fixed.


### Public Beta v1.5 Notes  
*(July 16th, 2018)*

**Database Changes**
- A few dozen miscellaneous trade items have been added to the database, including pirate coins.
- Fish crates have been added to the database.

**Features**
- Right-clicking a trade item will instead show "Open in Trade Calc" instead of "Open in Inspector".
- Default trade skill and route for the trade tool can now be set in the settings menu.
- Trade items in the search tool will now show values based on user settings for trade skill and transport path. Note that the Desert Buff will always be included if the user settings make this a possibility (IE, if the user set skill level is over artisan 2, and the default path ends in Valencia).
- Merged the search tool and the price tool. A button to the left of the search box allows you to toggle between each mode.
- In the past, when updating any item's value, the change in value wouldn't be reflected when sorting the search tool, and users would have to restart LSC for these changes to happen. This is due to how LSC indexes items when LSC is first run, so they can be sorted and displayed quickly. To remedy this, these indexes can now be recompiled while LSC is running. While this is happening, the search tool will be inaccessible for a short period of time (~15 seconds). This reindex can be done manually from the main menu's database control, but will also be triggered automatically (if necessary) when a new search tool is opened. Automatic reindexing can be disabled from the settings menu.
- Reworked the beck-end of the search tool a bit. It should now populate faster and more smoothly, not causing LSC to stutter quite as much. There should also be zero delay for the list to start populating when using certain filters and sort methods. However, the "Profit"-mode values displayed are static, and won't change unless the database is reindexed. "Price"-mode will update dynamically, but is always sorted by last-updated date, oldest to newest
- Search filters have been cleaned up a bit. They've been re-sorted, and their effects should be more clear. Additionally, the "Hide Crit Elixirs" filter will now also hide critical food results, and has been renamed appropriately. This filter is now enabled by default.
- Search favorites will now preserve sort mode.
- Search favorites will show their full settings in a tooltip when moused over.
- Search "Value" has been changed from base item value to estimated craft value, with the exception of items that can't be crafted directly, which will just show their item value.

**Bug Fixes**
- Lots of miscellaneous polish - mostly cleaning up input fields so they're more consistent, and don't cause the UI to wiggle.
- Fixed a bug which could cause the trade tool to show incorrect values when the "Number of Crafts" multiplier was too high.
- Fixed an aesthetic bug which caused the settings menu to not set toggle button colors correctly when initially loading the menu.
- The "Hide trade items" search filter will now correctly show its setting when the filter window is brought up.
- The "Hide base materials" filter will no longer hide critical cooking results.


### Public Beta v1.4.1 Notes  
*(July 1st, 2018)*

- Added the "Scratch" category to the Search Tool, which shows an estimated scratch profit for a given item.
- Two items had themselves listed as ingredients. As you can probably guess, this does bad things. The items are "Purple Pink Flower Crate" and "Corn Flour".
- Fixed a bug that caused LSC to not finish loading when selecting "Skip Version" when prompted to update the database.


### Public Beta v1.4 Notes  
*(June 27th, 2018)*

**Database Changes**
- Added Dinosaur Meat to the item database
- Added two new databases - MatGroupDatabase.csv and AltRecipeDatabase.csv.
- The "Tag" category in the ItemDatabase.csv has been replaced with the "Material Group" category, and the "Tag2" category is now simply "Tag". Items that are a part of a material group can have the material group's name added to this category. Multiple groups can be assigned by separating them with two forward slashes " // ".
- All items previously tagged as "Trade Crates" are now tagged more appropriately as "Trade Items". These tags have been moved to the right one column, to align with the new placement of the "Tag" category.

**Features**
- Initial support for alternative recipes (such as using green/blue ingredients) has been added to the inspector tool. Alternate recipe items can be added by creating an entry for them in the AltRecipeDatabase.csv.
- A basic database validator has been added. It scans for typos across LSC's three databases, and outputs any errors to a text file. This validator will automatically run when LSC is launched, and when databases are reloaded/rebuilt. This functionality will soon be expanded to look for duplicate entries and other errors.
- A new database loader has been added. When initially launching LSC, the loader will appear if there is an issue loading one of LSC's databases, giving the user an easy method of loading or rebuilding them on an individual basis.
- The trade calculator now has a special dropdown menu for selecting a trade item, which includes a search box.
- Tool costs for alchemy and cooking have been implemented as part of the inspector's "Additional Info" panel. This feature may be moved to the main inspector later.
- Material groups are now editable - both what items they contain, and the group's market values - outside of LSC. To make a new material group, simply add an entry to the MatGroupDatabase.csv, with a unique group ID and name. Then, add that name to the "Material Group" category of items in the ItemDatabase.csv.
- Material group item values can now be edited from their material group list.
- Added a "Hide Trade Items" filter to the search tool.

**Fixes**
- "Save and Quit" will now abort quitting if a save fails.
- The use tree will now correctly show the number of the main item are used for sub items, based on their scratch materials. Additionally, the use tree will now correctly show use counts and profit per item for non-base material trees.
- The "Trade Crates" tool has been renamed to "Trade Calculator".


### Public Beta v1.3.1 Notes  
*(June 16th, 2018)*

**Database Changes**
- Fixed the Good Feed recipe (called for 1 dried fish instead of 2).
- Added recipes for producing black stones from refineries.
- Added the recipe for Sealed Old Moon Camping Anvil.

**Features**
- Trade crate tool has received a much needed rework. Now the material list and profit calculations work identically to the item inspector's adaptive mode.
- Added total sale per hour to the inspector additional info panel.
- The material group list now has a section for editing the current and override values for the group.

**Fixes**
- Removed a bunch of erroneous UE4 Plugins. Still more to trim...
- When sorting by profit in the search tool, certain items with no profit value wouldn't be sorted correctly. This has been fixed.
- Clicking a use tree when it's not at the forefront wasn't bringing it forward if an item was being clicked. This has been fixed by making only the arrow clickable to expand/collapse an item, similar to other tools. *(This is a band-aid of sorts, but may be better overall. Will be reworked in the future if people particularly don't like it.)*
- Really high "Number of Crafts" multipliers in the inspector causes weird results. This has been temporarily fixed by capping the maximum multiplier. See the in-app tooltip for more details. *(For the tech savvy, int32 sucks)*
- When changing a set value (like updating a price), the text box should now correctly show the current value as hint text.


### Public Beta v1.3 Notes  
*Final beta phase! Get your suggestions in now before the full release! :)*
*(June 10th, 2018)*

**Warning:** This version requires one last mandatory database wipe. I apologize again for all these wipes, but this *will* (I hope...) be the last time, as LSC and the database have been set up to patch future versions of the database.

**Features**
- Updated to Unreal 4.19.2 (Probably won't change anything, but it does make my life a bit easier)
- Added a setup tool to help with basic configuration and getting started with LSC.
- Added a quick-start guide at the beginning of the written guide to help new users get up and running as quickly as possible.
- Added a database updater. It still probably needs some work, but it is functional.
- Moved search filters to a new window (similar to favorites). Filters to hide party and crit elixirs have been added.
- Inspector tool now has an additional info panel, which shows useful, but non-essential data, such as crafting time estimates and profit per hour.
- Crafting time estimates, as well as profit per hour, have been implemented.
- Tools and notes can now be renamed.
- Notes can now be saved and loaded between sessions using the Note List.
- Items can be added to a Watchlist for easy access between sessions.
- Added a setting for selecting how dates are formatted.
- Made dozens of aesthetic, QOL, and error-proofing changes.

**Fixes**
- Added more missing items to the database - specifically high-quality and special plants, as well as all produce/herb/mushroom crates.
- Fixed the search favorites panel. It can now be toggled open and closed correctly.
- Search filter "Hide items with a free material" wasn't properly being saved when saved as a search favorite parameter. It should now work correctly.
- Last-seen dates should now correctly update the first time a price is changed.
- Updating the price of a material within the inspector in one mode will now correctly update it in the other modes.
- Items in material groups couldn't be right-clicked to bring up the interaction menu. This has been fixed.
- Items that are a part of a material group will now correctly show values in the Use Tree.
- Fixed an error triggered when right-clicking the Price Tool's handle.
- Notifications and errors should no longer appear behind certain menus.
- Fixed some misleading error messages.


### Public Beta v1.2 Notes  
*(May 20th, 2018)*

**Warning:** This version requires another mandatory database wipe. This should be the last time, as I have an updater tool in the works that should be ready by v1.3.

- Fixed more broken and missing entries in the database.
- Added a price configurator, which is essentially a simplified version of the item database. It allows the user to easily find and update the prices of any item in the database. This tool will eventually be merged into the search tool, but for now it's a separate thing.
- Dramatically increased search speed at a slight cost to performance. This performance impact only occurs while the tool is actively searching, and only really noticeable when trying to scroll or move the window.
- The search tool was causing some screen tearing within the app when it was populated with a lot of items. This should be fixed.
- The search tool will now show non-crafted items by default.
- The search favorites panel wasn't properly closing when the button was pressed again, and there was no easy way to fix this. Now the button will be disabled while the menu is open. To close it, simply click anywhere that isn't within the favorites window.
- The search favorites panel should now use panel and text color settings.
- Fixed a bug causing buttons in the right-click menu to not show up for items that were part of a material group.
- The right-click menu should now use panel and text color settings.
- When viewing the use tree of a base material, the tree will show estimated profit per material for the item based on scratch profit margins.
- Fixed a bug that caused the use tree to double up the list whenever a price was changed in another tool.


### Public Beta v1.1 Notes  
*(May 10th, 2018)*  

**Warning:** Ordinarily, users can keep their item database across versions, maintaining any customization and price changes they have made. **However, due to the large number of errors in the previous version of the database, I highly recommend NOT copying over an old database this time.** I will try to implement a database patching tool as soon as possible, so hopefully this will be the last time this needs to happen. Sorry for the inconvenience.  

- Added the ability to sort searches by material cost, item value, profit, and return.
- Slightly increased initial load time (to about 2 seconds) in exchange for better search performance and sorting.
- Search tool now has a toggleable filter to hide items with a zero-value material.
- Item search will now show the complete database when no text is entered into the search box.
- Mousing over the net profit value in the inspector will show the return on investment for the item.
- Improved the accuracy of trade distances in the crate tool, as well as fixing a few typos.
- Crate tool was missing skill levels Skilled 1 to 10, and this was affecting profit calculations at ranks above this. This has been fixed.
- Users can no longer select the Desert Buff in the trade crate tool when a skill level below Artisan 2 is selected.
- Fixed a large number of broken and missing entries in the item database, including adding recipes to blue elixirs (3 green + blue reagent), and adding entries for all party elixirs.
- LSC randomly adding an extra blank line to the end of the database (and ultimately causing errors) when loading or saving should be fixed.


### Public Beta v1.0.2 Notes  
*(May 7th, 2018)*  

- Database auto saving should now be working. Additionally, it will only trigger when something in the database has been changed.
- Material group values (both current and override) are now saved between sessions. However, note that this information isn't (presently) stored in a spreadsheet, so it's not editable outside of LSC.
- Material groups (meat, coral, etc) can now be correctly tagged as bottleneck items.
- Removed the profit per craft display from the recipe mode (for real this time).
- Broken in-app Discord link has been replaced with a link to the GitHub. Note that the Discord link in the README should always be up to date.
- User guide has been updated to reflect that deleting the settings save will also clear search favorites.
- Added a section to the user guide about the ItemDatabase.csv and how to (somewhat) safely edit it.


### Public Beta v1.0.1 Notes  
*(May 6th, 2018)*  

- Overall filesize should be significantly smaller. Removed a lot of the erroneous Unreal Engine plugins. Still more to do, though.
- Removed the profit per craft tooltip from recipe mode in the inspector.
- Moved the craft multiplier (for batch crafting) out of the additional settings section in the inspector.


### Public Beta v1.0 Notes  
*(May 5th, 2018)*  

- Added a simple in-app guide, explaining every feature of LSC :)
- Fixed multiple bugs involving the Use Tree, including a CTD. It should also be much snappier when loaded.
- Setting: Auto-save converted to a dropdown.
- Settings menu no longer uses checkboxes. Toggles are now used instead.
- Fixed Setting: Record High/Low Tolerance. It should update correctly now.
- Trade Crate tool no longer allows users to use the desert buff when a route to Valencia isn't selected.
- Added the ability to tag items as bottlenecks, highlighting them as red in the item inspector.
- Mousing over the total material cost of a material in the inspector will show the profit per item (IE profit per meat, milk, egg, etc). Additionally, it will show how much the material would sell for on the market after tax.
- Fixed various instances of overlapping text.


### Closed Beta v2.3 Notes  
*(May 4th, 2018)*  

- Double clicking an item name in the search tool and the inspector will now automatically bring up the appropriate tool (use tree for materials, inspector for crafted items).
- Add the ability to search by item name or by item source (alchemy, processing, gathering, etc)
- Added search favorites.
- Temporarily disabled the sorting buttons for the search panel. I will re-enable them when I can fix up their functionality, as well as the search tool as a whole.
- Added a "Force disable tax" toggle to the inspector.
- The value of critical products (IE, blue elixirs) can now be edited in the inspector.
- Added a "Total Sell Value" to the inspector.
- Adjusted the layout of the inspector.
- Added a three mode switch to the inspector instead of a "Base/Scratch" toggle. Introducing the "Adaptive" material list :)
- Fixed a typo in the coral material group.
- Fixed trade crates throwing an error every time a crate is selected.
- Made the alignment of items in the use/recipe trees consistent.
- Added partial implementation for customizing the appearance of the background, panels, and text. More work to do, but mostly functional.
- It should no longer be possible to move windows outside of the viewport. Note that a window can still be "lost" if placed near the edge before shrinking the viewport. However, simply enlarging it again will make it possible to retrieve the window.


### Closed Beta v2.0 Notes  
*(April 20th, 2018)*  

- Settings menu added. Allows users to enable/disable tooltips, auto-saving, value packs, and adjust the record high/low tolerance.
- Panels have been given a border.
- Updated the old check box in the Search tool.
- New panels will no longer be placed behind old ones.
- All buttons should have visual feedback when clicked.
- Clicking within any part of a window will now properly reorder it.
- Panels no longer twitch down and to the right when initially moved.
- Exposed production and crit multipliers in the database.
- Profit for imperial crates now accounts for crit/double crafts via Production Multiplier.
- Interaction menu size should be consistent.
- Interaction menu should now show appropriate options based on the item being interacted with.
- Interaction menus have been added to the items in the Recipe and Use Trees.
- Pulling up the interaction menu should always be brought up using right-click across all menus.
- Search tool will auto-focus the search bar when created or un-minimized.
- Searches with a large number of results should no longer cause lag when the window is moved around.
- Fixed the Item Inspector throwing an error when "confirming" an empty material value entry box.
- Material lists in the Item Inspector will now update quantities and costs to account for the craft multiplier.
- Value pack overrides have been added to the Inspector, independently for both normal and crit results.
- Added the ability to set production and crit multipliers for an item in the inspector, and whether to include critical crafts in the calculation.
- The material tree will no longer break down by production multiplier. It will instead show basic recipes.
- Use trees for items that are a part of material groups now function correctly.
- Use tree now shows how many of the item in question are used in the recipe.
- Use and material trees now have an arrow indicating which items have uses/materials.