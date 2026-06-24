# oldschool-minimap
An oldschool dungeon minimap builder/exploration tool for foundry vtt


manifest: https://github.com/reykeplays-dev/oldschool-minimap/releases/latest/download/module.json


What it is: The Oldschool Minimap acts as a dungeon floor planner for any game that wants to do a dungeon crawl.
On the GM side of things, you will be able to hide the map for all players, bring it up for just you, or bring it up for everyone. It cycles through those states so you dont have to worry about it.

How it works: Once you have the map pulled up you can begin placing rooms on the map using the Rooms toggle. Once you have the rooms placed, the module reads any two rooms that are touching as being connected. So if you wanted a wrap around corner, you will need to add a space in the turn. But once the rooms are laid out, you can use the other toggles for markers to add the Monster Encounters (M), the Trap rooms (!), the Boss room (B), and the treasure rooms ($). Once everything is placed the last thing you place is the party marker (P). 

Once the dungeon has been laid out and the map is visible to the players they will be able to see what is in the immediate next connected rooms and then also a dimmed out room if it is just beyond. So players will have a good idea of the next one space, but would have a fog of war view for the room that is 2 out. In order to move, the party can agree on which move they want to do by having the players place a move request marker onto the map (?). The marker can be placed on any fully visible room. Once the group decides thats where they are going, the GM can move them there and it can continue like that until the floor is cleared.

An important thing to note is that the Treasure ($) and the Boss (B) markers will be visible to your players once they are discovered. But the Trap (!) and Monster (M) will remain hidden from the players so only the GM will know where they are and when to resolve those encounters. 

<img src="https://i.imgur.com/Xm08HUZ.png" width="33%"> The map planned out. </br>
<img src="https://i.imgur.com/XnR6rAU.png" width="45%"> The party encounters a monster fight. </br>
<img src="https://i.imgur.com/zTT7EJ0.png" width="45%"> The encounter is rolled out and the monsters appear on screen.</br>
<img src="https://i.imgur.com/vu0V9Kl.png" width="33%"> The exploration continues. </br>
