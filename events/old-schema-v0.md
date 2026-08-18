## Existing v0.1 Event Schema

| Name                 | Data Type | Required | Brief Description |
| game_id              | string    | Yes      | A unique, human-readable ID for the game that generated the data. |
| session_id           | int       | Yes      | A unique string of digits to identify a gameplay session, from the time the game was opened to the time it was closed. |
| user_id              | string    | No       | A non-identifiable, randomly-assigned ID for keeping track of a single player across multiple gameplay sessions. |
| user_data            | JSON      | No       | Additional data associated with a user_id, possibly reflecting cross-game data, such as list of other games played on a common platform. |
| client_time          | datetime  | Yes      | The time, according to the game client system, at which an event was generated. |
| client_offset        | int       | Yes      | The offset between GMT and the local timezone set in the client system. |
| server_time          | datetime  | Yes      | The time, according to the telemetry server, at which the event was received and recorded. |
| event_name           | string    | Yes      | A human-readable name identifying the type of event recorded by this Event. |
| event_data           | JSON      | Yes      | Event-specific data, describing the changes in game state that resulted from the given event, such as an updated score. |
| event_source         | string    | Yes      | A string indicating whether the event was logged directly by the game, or generated post-hoc. |
| game_state           | JSON      | No       | Additional data about the game state at the moment the event occurred, such as current level. |
| app_version          | string    | Yes      | The version of the game that generated this Event. |
| app_branch           | string    | No       | The name of the branch of the game that generated this Event. This allows for data to be captured from multiple “parallel” versions of a game, as in a randomized experiment. |
| log_version          | int       | Yes      | The version of the game’s logging logic that generated this Event, independent of the version of the game experience itself. |
| event_sequence_index | int       | Yes      | A counter that indicates the absolute order of event occurrences within a session. |


