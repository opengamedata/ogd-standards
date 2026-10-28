# ogd-standards

Official documentation of the OpenGameData logging standards and software reference platform.

## Event codes

`generated/OGDEvents.cs` and `generated/OGDEvents.js` hold the event codes from the tables in `events/`, as nested classes by category and family (e.g. `OGDEvents.PlayerAction.PointAndClick.SelectObject`). They're copied into the Unity and JavaScript logging libraries. `generated/ogd_events.gd` has the same codes for the Godot logger, as one enum per category (e.g. `OGDEvents.PlayerAction.POINT_AND_CLICK_SELECT_OBJECT`), since GDScript inner classes would clash with a game's own classes of the same name.

After changing a code table, run `python scripts/generate_event_codes.py` and commit the result. A check on pull requests fails if the committed files don't match the tables.

The Unity, JavaScript and Godot loggers each have a workflow that copies these files every day and opens a pull request when they change. Once a token that can write to those three repos' contents and actions is saved here as the `EVENT_CODE_SYNC_TOKEN` secret, each push to main that touches the event codes starts those workflows right away, and turns them back on if GitHub turned them off after 60 days without activity.
