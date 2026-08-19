## Event Parameters/Elements


### Categories of Parameter

* Identification (game, user, session, instance) - Identify who/what game
* Sequencing (timestamp, sequence indices) - Ordering events
* Segmenting (used for level/quest, etc.)
* Versioning (app, branch, logging)
* Context (configuration, game state, player history)
* Optional private context, i.e. metadata that may not be sharable due to identifiability
* Event-specific data (name, source, content)
* Device identifiers - browser, device, etc.

### Table of Proposed Parameters

| Name                    | Category        | Col. type | Data Type | Required* | Default    |
| ---                     | ---             | ---       | ---       | ---       | ---        |
| game_id                 | Identification  | simple    | string    | Yes       |            |
| instance_id             | Identification  | simple    | string    | No        | session_id |
| player_id               | Identification  | simple    | string    | No        | session_id |
| session_id              | Identification  | simple    | string    | Yes       |            |
| timestamp               | Sequencing      | compound  | datetime  | “Time”    | authoritative_timestamp |
| authoritative_timestamp | Sequencing      | compound  | datetime  | “Time”    | null       |
| game_time               | Sequencing      | compound  | timedelta | “Time”    | null       |
| session_sequence_index  | Sequencing      | simple    | int       | No        | (inferred from gametime sort order) |
| game_segment            | Segmenting      | compound? | JSON?     | No        | null? { }? |
| event_source            | Provenance      | simple    | string    | No        | “Game”     |
| source_version          | Versioning      | simple    | SemVer    | Yes       |            |
| game_version            | Versioning      | simple    | SemVer    | No        | source_version |
| schema_version          | Versioning      | simple    | SemVer    | Yes       |            |
| log_version             | Versioning      | simple    | SemVer    | Yes       |            |
| condition               | Configuration   | compound? | JSON?     | No        | null       |
| game_configuration      | Configuration   | compound  | JSON      | No        | { }        |
| platform                | Configuration   | compound  | JSON      | No        | { }        |
| game_state              | Context         | compound  | JSON      | No        | { }        |
| player_history          | Context         | compound  | JSON      | No        | { }        |
| event_id                | Event           | simple    | int       | Yes       |            |
| event_name              | Event           | simple    | string    | No?       | null?      |
| event_data              | Event           | compound  | JSON      | Yes       |            |
| private_metadata        | Private Context | compound? | JSON? / string matching id? | No | { }? null? |
