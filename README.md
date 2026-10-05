# ogd-standards

Official documentation of the OpenGameData logging standards and software reference platform.

## Event codes

`generated/OGDEvents.cs` and `generated/OGDEvents.js` hold the event codes from the tables in `events/`, as nested classes by category and family (e.g. `OGDEvents.PlayerAction.PointAndClick.SelectObject`). They're copied into the Unity and JavaScript logging libraries. `generated/ogd_events.gd` has the same codes for the Godot logger, as one enum per category (e.g. `OGDEvents.PlayerAction.POINT_AND_CLICK_SELECT_OBJECT`), since GDScript inner classes would clash with a game's own classes of the same name.

After changing a code table, run `python scripts/generate_event_codes.py` and commit the result. A check on pull requests fails if the committed files don't match the tables.
