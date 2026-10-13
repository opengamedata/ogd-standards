## Event Schema

The event *schema* defines the elements of telemetry events.
These elements fall within some general categories, outlined below, which help to show conceptually what role each element is intended to play.

In the table of event elements, the "Required" column indicates whether the element is strictly required as an output from a data logging client or other event generator.
"Guaranteed" indicates whether the element is guaranteed to contain a meaningful value within any dataset output by the OpenGameData telemetry logging infrastructure.
All "required" elements are also "guaranteed," as any event data missing these elements is rejected.
Some "non-required" elements are "guaranteed"; these are elements which are automatically assigned a reasonable inferred value based on certain other "guaranteed" elements.
In addition, we list "default" values for all non-required elements.
For non-guaranteed elements, the default is an "empty" value such as `null` or an empty JSON object.

### Categories of Parameter

* Identification (game, user, session, instance) - Identify who/what game
* Sequencing (timestamp, sequence indices) - Ordering events
* Segmenting (used for level/quest, etc.)
* Versioning (app, branch, logging)
* Context (configuration, game state, player history)
* Optional private context, i.e. metadata that may not be sharable due to identifiability
* Event-specific data (name, source, content)
* Device identifiers - browser, device, etc.

### Table of Proposed Elements

| Name                    | Category        | Col. type | Data Type | Required | Guaranteed | Default        |
| ----------------------- | --------------- | --------- | --------- | -------- | ---------- | ---------------|
| game_id                 | Identification  | simple    | string    | Yes      | Yes        | -              |
| instance_id             | Identification  | simple    | string    | No       | Yes        | player_id      |
| player_id               | Identification  | simple    | string    | No       | Yes        | session_id     |
| session_id              | Identification  | simple    | string    | Yes      | Yes        | -              |
| timestamp               | Sequencing      | compound  | datetime  | Yes      | Yes        | -              |
| authoritative_timestamp | Sequencing      | compound  | datetime  | No       | No         | null           |
| game_time               | Sequencing      | compound  | timedelta | No[^1]   | No         | null           |
| session_sequence_index  | Sequencing      | simple    | int       | No[^1]   | Yes        | inferred from `game_time` sort order |
| game_segment            | Segmenting      | compound  | JSON      | No       | No         | { }            |
| event_source            | Provenance      | simple    | string    | No       | Yes        | "Game"         |
| source_version          | Versioning      | simple    | SemVer    | Yes      | Yes        | -              |
| game_version            | Versioning      | simple    | SemVer    | No       | Yes        | source_version |
| schema_version          | Versioning      | simple    | SemVer    | Yes      | Yes        | -              |
| log_version             | Versioning      | simple    | SemVer    | Yes      | Yes        | -              |
| condition               | Configuration   | simple    | string    | No       | No         | null           |
| game_configuration      | Configuration   | compound  | JSON      | No       | No         | { }            |
| platform                | Configuration   | compound  | JSON      | No       | No         | { }            |
| game_state              | Context         | compound  | JSON      | No       | No         | { }            |
| player_history          | Context         | compound  | JSON      | No       | No         | { }            |
| event_id                | Event           | simple    | int       | No[^2]   | Yes        | 9999           |
| event_name              | Event           | simple    | string    | No[^2]   | Yes        | inferred from `event_id` |
| event_data              | Event           | compound  | JSON      | Yes      | Yes        | -              |
| private_metadata        | Private Context | compound  | JSON      | No       | No         | { }            |

[^1]: One of `game_time` and `session_sequence_index` is required. If `game_time` is given, both fields are guaranteed. If only `session_sequence_index` is given, `game_time` is not guaranteed.
[^2]: One of `event_id` and `event_name` is required. If only `event_name` is given, an `event_id` of 9999 will be used. This special code marks an event logged without an event id, such as one from a game that logs by name only. If only `event_id` is given, there are two cases: (1) if the `event_id` is reserved in the event standard catalog, the name of the event type will be used. (2) if the `event_id` is not reserved in the catalog, a name based on the base, thousands-level block will be used (e.g. "meta_event" for a non-reserved event in the 1000-level block).

### Description of Each Element

#### game_id

An identifier uniquely identifying the fundamental game from which the data originated.
This should remain the same across different versions of the same game.

#### instance_id

An identifier for a unique "instance" of a game.
For multiplayer games, this could be an instance players individually join.
For singleplayer games that support saving and reloading game states, this could be an identifier of a "playthrough" or "save file."
If the game does not directly define a concept of "instance," this field will be filled with the `player_id` field's value.

#### player_id

An identifier for a unique player of a game.
For multiplayer games, multiple players with individual `player_id`s are expected to join into a single instance.
For singleplayer games, `player_id` is often assigned to distinguish between individual players on their own unique playthroughs.
If the game does not directly define a player ID, this field will be filled with the `session_id` field's value.

#### session_id

A unique identifier for a gameplay session.
A session is generally defined as the play that happens from the time the game executable starts to the time it stops.
Games that support saving and reloading game states may have multiple sessions for a single player/instance.

#### timestamp

A [UTC datetime string](https://www.w3.org/TR/NOTE-datetime) with timezone offset from GMT, indicating the local time read from the player's machine when the event occurred.

#### authoritative_timestamp

A UTC datetime string without timezone offset, read from an authoritative time server when the event occurred.
The accuracy of such a timestamp is necessarily capped by the latency of the time server, but may be useful as a secondary source of timing data if the client machine's date/time settings are unreliable.

#### game_time

A floating-point indicating the number of seconds elapsed since the beginning of the current gameplay session.
If a total play time across multiple sessions is desired, the game should include timing data from prior gameplay sessions in the `player_history` field, or this prior timing data should be calculated during post-processing.

#### session_sequence_index

An integer indicating where the given event falls in an absolute ordering of game-generated events.
A session sequence index is not currently defined for post-hoc generated events; these should typically use the session sequence index of the event that "triggers" the generation of the post-hoc event.

#### game_segment

A JSON object encoding details of the segment of the game in which the event occurred.

#### event_source

An all-caps string indicating the source of a given event. For events logged from a client library, this is always "GAME."
Post-hoc events have a source of "GENERATED."

#### source_version

A "semantic version"-style string indicating the version of the source that generated the event.
For game-generated events, this is identical to the `game_version`.
For post hoc events, this is the version of whatever post-hoc data processing tool was used to generate the event.

#### game_version

A "semantic version"-style string indicating the version of the game from which the data originated.
For post hoc events, this is the `game_version` of the event data that were used to generate the event.

#### schema_version

A "semantic version"-style string indicating the version of the OGD schema that the data conforms to.
This enables tools to reject incompatible data formats.

#### log_version

A "semantic version"-style string indicating the version of the game-specific *event specification* implemented in the game from which the data originated.
Where `game_version` captures the version of the game as the player experiences it, `log_version` indicates the version of the spec that defines the specific events that are logged from a game.
For example, a game may release with `game_version = "1.0"` and `log_version = "1.0"`.
If the implementation of telemetry logging is updated to add additional telemetry events, remove old events, or change the contents of existing events, then `log_version` will be independently incremented, e.g. to `log_version = "2.0"`.
If minor changes are made to adjust the game difficulty, the `game_version` will be independently incremented, e.g. to `game_version = 1.1`.
In other cases, both version indicators may change at the same time, such as when new features are implemented in the game, with corresponding additions to the event specification.

#### condition

A string indicating an experimental condition, A-B testing condition, or other form of "parallel version" of the game from which the data originated.
For example, during an experiment in which multiple different variations of a game are deployed in parallel, one variant may send `condition = "experimental_group"` and the other may send `condition = "control_group"` (of course, greater specificity is encouraged).
For games that utilize the `game_configuration` field, the `condition` may be thought of as a name corresponding to a specific value of `game_configuration`.

#### game_configuration

A JSON object encoding details of the game's fundamental configuration.
That is, this field is not intended to capture player-controlled configurations (such as audio volume or graphics quality), but developer-controlled configurations (such as a set of simulation parameters for a game playthrough).

#### platform

A JSON object encoding details about the platform on which the game was played.
This might include the name and version of the operating system or web browser.
Platform data should *not* include unique identifiers such as a hardware ID or IP/MAC address.

#### game_state

A JSON object encoding details about the state of the game at the moment *before* the event occurred, used as context for interpreting the event.
The set of elements within the object should be the same for all events within a single game, though the values change.
For example, a game that includes `"player_score"` as an element of the `game_state` should do so for every event.
The associated value should indicate the player's score in the instant before the event occurred.
If the event results in a change of score, the new score (or number of points scored) should be included in the `event_data`.

While `game_state` *could* encode full details of the entire game state, the *strongly-recommended* best practice is to avoid such comprehensive encodings, and instead log the smallest set of state details needed to provide a reasonable context for interpreting player interactions across all telemetry events logged by the game.
For example, `"player_score"` may be a reasonable element of `game_state`, since a player's score is (for many games) a core guiding variable that players are encouraged to maximize.

On the other hand, an element called `valid_placement_locations` is likely only relevant to interactions in which a player is attempting to place some object.
Thus, such an element is likely inappropriate for inclusion in `game_state`, and instead should be a part of the `event_data` for events related to object placement.

#### player_history  

A JSON object encoding details about the gameplay history for a given player.
This is not intended to give comprehensive running totals on a player's actions within a given session, but to provide a summary of prior history with the given game, or other related games on a common platform.
In particular, it should include data that is not otherwise readily-available to the player within the gameplay session.

For example, consider a player's "high score" within a game.
If the player can not see their high score from within the game itself, or can only see the high score through a "main menu" outside of active gameplay, then `player_history` might include a `"high_score"` element containing that value.
On the other hand, if the game displays a "high score" alongside a player's current score, it would be more appropriate to include `"high_score"` as an element of `game_state`.

#### event_id

A four-digit integer used to indicate the particular "type" of the event that occurred.
The remainder of this event specification document lays out a catalog of standardized event "types," with corresponding reserved ID codes.
A *strongly-encouraged* best practice is to match as many telemetry events as possible from a given game to the standardized types in the catalog, using the reserved ID codes to ensure that common event types can be aligned across games.
Each "block" in the catalog includes ranges of ID codes that are intentionally un-reserved within the catalog, which may be freely assigned within a game's event specification to any telemetry events that do not match well with any standard type.

#### event_name

A string indicating the name of the specific event type within the game.
By default, this is simply the name of the type in the standard event catalog corresponding to the event's `event_id`.
However, individual games are encouraged to override the standard name with game-specific names, in order to increase the readability of the data and enable any useful game-specific event filtering and analyses.

For example, a game may log telemetry events when a player places a house or a tree within a game map.
Each of these might be determined to fall within the "place_object" event type.
However, a reasonable choice of `event_name` might be `"place_house"` and `"place_tree"`, respectively.
Note that different events of the same standard type need not have the same `event_name`; the `event_name` element is intended to use identify events in terms of the language of the game itself.

#### event_data

A JSON object encoding the specific details of the event that occurred.
Whereas most other elements of the event schema tend to provide contextual information some kind, this element is wholly-specific to the type of event being logged.

#### private_metadata

For games which may need to collect some form of data not suitable for public release, this element is a JSON object encoding such data.
There are no specific recommended practices or constraints provided; however, this element *may* be blocked, ignored, cleared, or otherwise dropped at the system level by any data processing tool, particularly where such a tool is not authorized to handle private data.
In particular, OpenGameData's own standard infrastructure does not presently support the use of this element.
It is included in the standard for completeness, and to provide flexibility for future systems that may be designed to handle such non-public data.
