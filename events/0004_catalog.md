## Event Catalog: Categories & Specifications

The remainder of this document is dedicated to a catalog of basic event types.
We define a hierarchical, conceptual taxonomy of events types that serves to guide the identification of real-world game events with a conceptual type.
Each type is associated with a numeric code, which can be used to identify semantically-similar events across vastly different games.
This numeric tagging approach then enables standardized analyses to be applied across games.

The taxonomy is flexible by design, with ample numeric codes reserved for custom use in games with novel interactions or game mechanics.

### Numeric code approach

Each event type defined in our taxonomy is assigned a four-digit numeric code, identifying a telemetry event with its type.
Each of the four digits corresponds to one level of hierarchy in our taxonomy:

* The top level of the hierarchy is grouped primarily by the actor within the game that caused the event to be triggered, such as the "focal" player, an NPC, or the game system. There also exist top-level groups that relate to a particularly prevalent game mechanic or structure, such as dialog and segmentation.
  * We reserve one top-level category for fully-custom event space, i.e. events that don’t fit into other parts of standard
* The second level groups by a particular class of game mechanic within the top-level category. For example, "dialog" events are grouped at the second level into narration, "true" dialog with player choices, tutorialization, etc.
* The third level groups events by a particular "unit" of the interaction or game structure. For example, the Segmentation -> Exclusive Segmentation category uses grouping at the third level to represent hierarchies of segments within a game, such as rounds within a level.
  * In practice, the third level is not meaningfully utilized in most cases, but is reserved for future expansions of the event catalog.
* The fourth level represents the event "verb," such as "select", "deselect", "submit", or "cancel." The taxonomy generally follows a few conventions to make identification easier.
  * Lower-value digits (e.g. xxx0, xxx1) are used for most-broadly-applicable events, e.g. "start," with higher-value digits corresponding to more distinctive verbs.
  * Even digits are typically used for "start" or other "initiation" events, with the next consecutive odd digit for "end."
  * The mapping of verbs to digits typically repeats across groups in the 3rd level.

While this is the general convention, it’s important to note that the use and meaning of the lower-level groupings will always depend to a degree on the higher-level grouping(s), and so some exceptions will always exist.

### Using the Catalog

This catalog documents a hierarchical taxonomy of events. Within any game, for each event that is identified, implementers should use the taxonomy to help locate the corresponding event type within the catalog. Then that specific event within the game should be assigned the identified ID code, i.e. the `event_id` field in the telemetry log should contain that ID code.

The event name should be chosen to reflect the instantiation of that type of event within the game, though the event type can be used as a fallback.

### Top-Level Categories

Some general commitments:

* X900+ is intentionally left blank within each block for custom events
* 9000+ is intentionally left blank as a fully custom block

### Summary of Top-Level Categories

| Numeric Range | Range Name                | Description                                                                                |
| --------      | ------------------------- | ------------------------------------------------------------------------------------------ |
| 1000          | Meta-Events               | Events that occur within the application, but are not a part of gameplay, e.g. navigating a main menu |
| 2000          | Dialog                    | Events relating to dialog and other “spoken” portions of gameplay, including cutscenes and tutorials. |
| 3000          | Segmentation              | Events that indicate the player’s location within the game’s progression, world regions, or other discrete “segments” of the game |
| 4000          | Player Actions            | Direct player interactions with the game |
| 5000          | Other-Human-Actor Actions | Actions within the game taken by “other” players than the active player. Typically equivalent to player actions, but with a different actor. These are generally other players in a multiplayer session. |
| 6000          | System-Controlled Actor Actions | Actions within the game taken by system-controlled actors, such as NPCs. Typically equivalent to player actions, but with a different actor. |
| 7000          | System Actions            | Instances of system feedback or other changes in game system state, often in response to player actions. |
| 8000          | Replay/Clickstream        | State captures or direct I/O events useful for replay systems |
| 9000          | Open Block                | Reserved for events that do not cleanly fit within the spec |

#### 1. Meta-Events

Application and session context outside gameplay

* settings/setup/menu navigation
* pause/unpause
* focus loss / gain

#### 2: Dialog

Game-to-player communication

Events relating to dialog within a game. This might include cutscenes, narration, feedback pop-ups, as well as traditional dialog trees.

A few points of terminology:

* Block-printed text: Text that is displayed all at once, with no animation
* Progressive-printed text: Text that is displayed through an animation.

Within the category, we have the following 100-level blocks:

1. **Narration (non-interactive)** - dialog events such as cutscenes, in which the player has little to no agency except to observe and possibly skip the dialog presented to them.
2. **Dialog** - interactive dialog between the player and a non-player character, such as traditional dialog trees. This category should also include “implied” dialog in which the player character’s responses are pre-scripted, but is presented to the player in a similar way to traditional dialog, such as in point-and-click adventures, where the player clicks on an NPC, reads/listens through some pre-scripted dialog, and immediately resumes pointing and clicking.
3. **Prompting / Tutorialization** - Similar to dialog, except that the expected player response is some non-dialog interaction. For example, this category of dialog would include instructions given by a NPC to the player during a tutorial segment in which the player is expected to make moves based on the NPC’s directions.
4. **Feedback** - Dialog and dialog-like text or audio that provides some feedback on some task or interaction the player attempted. In general, feedback events indicate positive or negative feedback from the system to the player, such as success or failure messages.
5. **Hint** - Similar to Feedback, this is text that is displayed (or audio played) to give the user a suggestion for what to try next, or how to work their way out of a difficult spot. This includes games that give the player a “help” button or a guide character who the player can freely go to for help. Thus, this category is distinct from prompting dialog events.

We use the following general verbs, used within the various sub-blocks:

1. **Start** - When an individual “line” of dialog begins to display (text) or play (audio/video).
2. **Complete** - When an individual “line” of dialog completes its display or finishes playing. For block-printed text, the “start” event is also the time when the display finishes. Thus, this event is only used for animated text display.
3. **Clear** - When one or more textual lines of dialog are cleared from display. This is primarily recommended for games that only display one dialog line at a time - games that accumulate multiple lines are recommended to send a single clear when an entire text area is cleared, but it may also be the case that “clear” is irrelevant for such systems.
4. **Next** - A player action indicating the player has clicked, tapped, hot-keyed, or otherwise signalled to advance to the next line of dialog. For games that only display one line of dialog at a time, this event is expected to be followed by a clear event, and then a start event for the next line.
5. **Skip to End** - A player action indicating the player has signaled to skip the animation or playback of the current line of dialog. This is used, for example, by games that use progressive-printed text, but allow a user to click to skip the progressive-printing animation and display the whole text.

#### 3: Segmentation

Game structure and progression

The 3000 block is used for segmentation-related events, that indicate the player moving to another “part” of the game, whether in terms of progression or location in the game.

Within the block, we assign the following 100-level blocks:

1. **“Universal” segments** - sessions, game playthroughs, etc.
2. **“Exclusive” or “Singular” progression** - progression events that represent entry into a discrete, mutually-exclusive progression segment such as a “level” or “puzzle”
3. **“Non-exclusive” or “plural” progression** - events that represent entry into non-exclusive progression segment such as an “objective,” where multiple objectives may be active at one time

#### 4: Active-Player Actions

Intentional (focal) player actions

Within this category, there is no "click" verb, as every event represents an action taken within the game system, not related to the specific hardware interface.

1. **Universal non-diegetic actions** - UI actions, open / close
2. **Puzzle / Constructed Response Actions**
3. **Point-and-Click Actions**
4. **Combat Actions**
5. **Spatial Navigation**
6. **Resource Management Actions**
7. **Simulation Actions**
8. **Interface & Structural Navigation Actions**

#### 5: Non-Active-Player Actions

Actions within the game taken by “other” players than the active player. Equivalent to player actions, but executed by another (non-focal) human player

Actions by players other than the active user. Likely only includes events that are visible to the active player in some way

* meant for things like multiplayer

#### 6: System-Controlled Actor Actions

Gameplay actions performed by non-focal actors whose behavior is controlled by the game rather than by a human player

Actions by actors controlled directly by the game system, such as NPCs or in-game enemies.

#### 7: System Actions

System-performed actions within gameplay

The events generated by the game system, often as the end result of a player action. They typically affect all players equally, whether the active player, a 3rd-party player, or AI agent

* Spawning/destroying entities
* changes in underlying simulation values (health, currency, etc)
* All physics engine related stuff (collision, triggering)

#### 8: Replay/Clickstream Events

State captures or direct I/O events useful for replay systems

for replay via game state interpolation on “ticks”, or via buffer actions. More broadly, recording hardware-level interactions (clicks, mouse movements, vr controllers)

<!-- #### 8: Experiments

questionnaires, condition assignments -->

#### 9: “Open” Block

Reserved for events that do not cleanly fit within the spec

1000 free event codes with no attached conventions
