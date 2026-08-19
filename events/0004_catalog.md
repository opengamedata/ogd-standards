## Event Categories & Specifications

### A numeric code approach

Four-digit codes
First digit is a high-level category, e.g. 1000s for progression, 2000s for player actions, 3000 for system events, etc.
On inner digits, often used even numbers for “start”, odd numbers for “end”
Lower-value numbers (e.g. 4000, 40001) used for most-broadly-applicable events, e.g. “tick”
Reserve one top-level category for fully-custom event space, things that don’t fit into other parts of standard
Could benefit from separating different common mechanics, but need more than single digit there

### Summary of Proposed Ranges

| Numeric Range | Range Name                | Description                                                                                |
| --------      | ------------------------- | ------------------------------------------------------------------------------------------ |
| 1000          | Meta-Events               | Events that occur within the application, but are not a part of gameplay, e.g. navigating a main menu |
| 2000          | Dialog                    | Events relating to dialog and other “spoken” portions of gameplay, including cutscenes and tutorials. |
| 3000          | Segmentation              | Events that indicate the player’s location within the game’s progression, world regions, or other discrete “segments” of the game |
| 4000          | Player Actions            | Direct player interactions with the game |
| 5000          | Other-Human-Actor Actions | Actions within the game taken by “other” players than the active player. Typically equivalent to player actions, but with a different actor. These are generally other players in a multiplayer session, but includes NPCs with sufficient “agency.” |
| 6000          | System-Controlled Actor Actions | Actions within the game taken by system-controlled actors, such as NPCs. Typically equivalent to player actions, but with a different actor. These are generally other players in a multiplayer session, but includes NPCs with sufficient “agency.” |
| 7000          | System Actions            | Instances of system feedback or other changes in game system state, often in response to player actions. |
| 8000          | Replay/Clickstream        | State captures or direct I/O events useful for replay systems |
| 9000          | Open Block                | Reserved for events that do not cleanly fit within the spec |

### Proposed Ranges

Within each 1000s-level block, we attempt to develop useful 100s-level blocks, and typically use 10s-level digit to correspond to a particular “unit” of the interaction, with the 1s-place for the specific verb (which repeats across 10s-level units). While this is the general trend, it’s important to note that the use and meaning of the lower-level digits will always depend on the higher-level digit(s), and so exceptions will always exist for the general trends.

Some general commitments:
* X900+ is intentionally left blank in each block for custom events
* 9000+ is intentionally left blank to be a custom block


#### 1. Meta-Events

Application and session context outside gameplay

settings/setup/menu navigation
pause/unpause
focus loss / gain

#### 2: Dialog

Game-to-player communication

Events relating to dialog within a game. This might include cutscenes, narration, feedback pop-ups, as well as traditional dialog trees.

A few points of terminology:

* Block-printed text: Text that is displayed all at once, with no animation
* Progressive-printed text: Text that is displayed through an animation.

Within the block, we have the following 100-level blocks:

1. **Narration (non-interactive)** - dialog events such as cutscenes, in which the player has little to no agency except to observe and possibly skip the dialog presented to them.
2. **Dialog** - interactive dialog between the player and a non-player character, such as traditional dialog trees. This category should also include “implied” dialog in which the player character’s responses are pre-scripted, but is presented to the player in a similar way to traditional dialog, such as in point-and-click adventures, where the player clicks on an NPC, reads/listens through some pre-scripted dialog, and immediately resumes pointing and clicking.
3. **Prompting / Tutorialization** - Similar to dialog, except that the expected player response is some non-dialog interaction. For example, this category of dialog would include instructions given by a NPC to the player during a tutorial segment in which the player is expected to make moves based on the NPC’s directions.
4. **Feedback** - Dialog and dialog-like text or audio that provides some feedback on some task or interaction the player attempted. In general, feedback events indicate positive or negative feedback from the system to the player, such as success or failure messages.
5. **Hint** - Similar to Feedback, this is text that is displayed (or audio played) to give the user a suggestion for what to try next, or how to work their way out of a difficult spot. This includes games that give the player a “help” button or a guide character who the player can freely go to for help. Thus, this category is distinct from prompting dialog events.

We propose the following general verbs, used within the various sub-blocks:

1. **Start** - When an individual “line” of dialog begins to display (text) or play (audio/video).
2. **Complete** - When an individual “line” of dialog completes its display or finishes playing. For block-printed text, the “start” event is also the time when the display finishes. Thus, this event is only used for animated text display.
3. **Clear** - When one or more textual lines of dialog are cleared from display. This is primarily recommended for games that only display one dialog line at a time - games that accumulate multiple lines are recommended to send a single clear when an entire text area is cleared, but it may also be the case that “clear” is irrelevant for such systems.
4. **Next** - A player action indicating the player has clicked, tapped, hot-keyed, or otherwise signalled to advance to the next line of dialog. For games that only display one line of dialog at a time, this event is expected to be followed by a clear event, and then a start event for the next line.
5. **Skip to End** - A player action indicating the player has signaled to skip the animation or playback of the current line of dialog. This is used, for example, by games that use progressive-printed text, but allow a user to click to skip the progressive-printing animation and display the whole text.

#### 3: Segmentation

Game structure and progression

The 3000 block is use for segmentation-related events, that indicate the player moving to another “part” of the game, whether in terms of progression or location in the game.

Within the block, we assign the following 100-level blocks:

1. **“Universal” segments** - sessions, game playthroughs, etc.
2. **“Exclusive” or “Singular” progression** - progression events that represent entry into a discrete, mutually-exclusive progression segment such as a “level” or “puzzle”
3. **“Non-exclusive” or “plural” progression** - events that represent entry into non-exclusive progression segment such as an “objective,” where multiple objectives may be active at one time

#### 4: Active-Player Actions

Intentional (focal) player actions

Within this block we’ve had a philosophy that there is no “click”, everything is an action taken within the context of the game, not related to the hardware interface.

We’re currently thinking of a few "hundreds blocks” in this group:

1. **Universal non-diegetic actions** - UI actions, open / close
2. **Diegetic Actions**
3. **State Machine Actions**
4. **Game Specific “Interacts”**

#### 5: Non-Active-Player Actions

Actions within the game taken by “other” players than the active player. Equivalent to player actions, but executed by another (non-focal) human player

Actions by players other than the active user, whether these are from other players or AI agents. Likely only includes events that are visible to the active player in some way

* meant for things like multiplayer

#### 6: System-Controlled Actor Actions

Gameplay actions performed by non-focal actors whose behavior is controlled by the game rather than by a human player

Actions by actors controlled directly by the game system, such as NPCs or in-game enemies.

#### 7: System Actions

System-performed actions within gameplay

Actions within the game taken by “other” players than the active player. Equivalent to player actions, but executed by another (non-focal) human player

The events by the game system, often as the result of a player action. They typically affect all players equally, whether the active player, a 3rd-party player, or AI agent

* Spawing/destroying entities
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
