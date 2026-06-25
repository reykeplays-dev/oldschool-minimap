# Oldschool Minimap

**Oldschool Minimap** is a Foundry VTT module that adds a shared retro dungeon tracker for room-by-room exploration, party movement, fog-preview discovery, encounter markers, and random encounter spawning.

It is designed for tables that want a simple old-school dungeon map experience without needing to reveal a full tactical map to the players.

## Features

- Shared dungeon tracker visible to the GM and players
- GM-authored room layout
- Party marker for tracking exploration
- Persistent discovered rooms
- Persistent fog-preview rooms for nearby unexplored paths
- Player movement request markers
- GM-only monster and trap markers
- Player-visible treasure and boss markers
- Import and export dungeon layouts
- Random encounter spawning when the party reaches a Monster marker
- Encounter table support using Rollable Tables
- Compendium actor lookup, import, token spawning, and combat setup

## Compatibility

- Minimum Foundry version: **12**
- Verified Foundry version: **13**

## Installation

Install the module using the manifest URL from the latest GitHub release:

```text
https://github.com/reykeplays-dev/oldschool-minimap/releases/latest/download/module.json
```

Or manually install by placing the module folder in:

```text
Data/modules/oldschool-minimap/
```

The folder should contain:

```text
module.json
scripts/minimap.js
styles/minimap.css
```

Then enable **Oldschool Minimap** in your world’s Manage Modules menu.

## Basic Usage

The GM controls the tracker from the Foundry scene controls. The visibility button cycles through three states:

1. **Hidden** — tracker is hidden from everyone.
2. **GM Setup** — tracker is visible only to the GM.
3. **Live** — tracker is visible to the GM and players.

Use **GM Setup** to build the dungeon before play. Switch to **Live** when the party begins exploring.

## GM Controls

The GM toolbar is split into three groups.

### Map Tools

- **Room** — place a room on the tracker grid.
- **Erase** — remove a room and its associated tracker data.
- **Party** — place the party marker.
- **Move** — move the party marker to any fully revealed room.

### Marker Tools

- **Monster** — place a GM-only monster encounter marker.
- **Trap** — place a GM-only trap marker.
- **Treasure** — place a player-visible treasure marker.
- **Boss** — place a player-visible boss marker.
- **Clear Mark** — remove a marker from a room.

### Utility Tools

- **Clear Req** — clear all player movement request markers.
- **Export** — export the room layout and markers to a JSON file.
- **Import** — import a saved room layout and markers from a JSON file.
- **Reset** — clear the current tracker state.

## Exploration and Fog Preview

The tracker uses two visibility layers.

### Fully Revealed Rooms

Rooms at the party’s current position and one space away become fully revealed. Fully revealed rooms remain visible permanently.

Players can request movement to any fully revealed room, which makes backtracking quick and easy.

### Fog-Preview Rooms

Rooms two spaces away from the party appear as darkened fog-preview rooms. These rooms remain visible once seen, helping players remember possible unexplored paths.

Fog-preview rooms do not show markers, and players cannot move into them until they become fully revealed.

## Player Movement Requests

Players cannot directly move the party marker. Instead, they click a fully revealed room to place a movement request marker.

The GM resolves the request by moving the party marker to that room. When the party marker moves there, the request marker is cleared.

## Import and Export

The module can export and import dungeon layouts as JSON files.

Exported layouts include:

```text
rooms
markers
```

Exported layouts do not include:

```text
party position
discovered rooms
fog-preview rooms
movement requests
```

This keeps reusable dungeon prep separate from live session state.

## Random Encounter Spawning

When the GM moves the party marker onto a room with a **Monster** marker, the module opens a **Generate Encounter** dialog.

The GM chooses:

- Encounter table
- Number of table rolls

The module then:

1. Rolls the selected Rollable Table.
2. Parses the results.
3. Finds matching monsters in the configured compendium.
4. Imports or reuses world Actors.
5. Spawns tokens on the active scene.
6. Adds the spawned tokens to combat.
7. Optionally rolls NPC initiative.
8. Optionally clears the Monster marker after the encounter is spawned.

## Encounter Settings

The following settings can be configured in Foundry’s module settings:

| Setting | Purpose |
| --- | --- |
| Encounter Tables Folder Name | The Rollable Table folder used for encounter table selection. |
| Monster Compendium Pack | The compendium pack ID used to find monsters by name. |
| Reuse Existing World Actors | Reuse matching world Actors instead of importing duplicates. |
| Imported Monster Folder Name | Actor folder used for imported monsters. |
| Encounter Token Spacing | Distance between spawned tokens in grid squares. |
| Roll NPC Initiative | Automatically roll NPC initiative after adding tokens to combat. |
| Default Encounter Table Rolls | Default number of table rolls in the encounter dialog. |
| Clear Monster Marker After Encounter | Remove the Monster marker after a successful spawn. |

## Encounter Table Result Formats

Encounter tables should list **one Actor per table result**.

Each result should point to a single monster or enemy. The module rolls on the selected encounter table a number of times equal to the value entered by the GM in the **Generate Encounter** prompt.

Supported result formats:

```text
Goblin
@UUID[Compendium.world.shared-monsters.Actor.xxxxx]
```

## Spawn Location

Encounter tokens spawn around the currently selected token.

If no token is selected, tokens spawn near the center of the active scene.

## Recommended Workflow

1. Switch the tracker to **GM Setup**.
2. Build the dungeon layout using the Room tool.
3. Add Monster, Trap, Treasure, or Boss markers.
4. Export the layout if you want to reuse it later.
5. Place the party marker.
6. Switch the tracker to **Live**.
7. Let players request movement.
8. Move the party marker as GM.
9. Resolve Monster marker encounters when triggered.

## Notes

Oldschool Minimap is intentionally lightweight. It does not replace a tactical battle map. Instead, it gives the table a shared exploration tracker that preserves the feeling of mapping a dungeon room by room.
