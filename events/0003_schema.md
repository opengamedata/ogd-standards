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
| event_name              | Event           | simple    | string    | No[^2]   | Yes        | (inferred from `event_id`) |
| event_data              | Event           | compound  | JSON      | Yes      | Yes        | -              |
| private_metadata        | Private Context | compound  | JSON      | No       | No         | { }            |

[^1]: One of `game_time` and `session_sequence_index` is required. If `game_time` is given, both fields are guaranteed. If only `session_sequence_index` is given, `game_time` is not guaranteed.
[^2]: One of `event_id` and `event_name` is required. If only `event_name` is given, an `event_id` of 9999 will be used. This special code marks an event logged without an event id, such as one from a game that logs by name only. If only `event_id` is given, there are two cases: (1) if the `event_id` is reserved in the event standard catalog, the name of the event type will be used. (2) if the `event_id` is not reserved in the catalog, a name based on the base, thousands-level block will be used (e.g. "meta_event" for a non-reserved event in the 1000-level block).
