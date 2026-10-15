# ogd-standards

Official documentation of the OpenGameData logging standards and software reference platform.

## Event codes

`generated/OGDEvents.cs` and `generated/OGDEvents.js` hold the event codes from the tables in `events/`, as nested classes by category and family (e.g. `OGDEvents.PlayerAction.PointAndClick.SelectObject`). They're copied into the Unity and JavaScript logging libraries.

After changing a code table, run `python scripts/generate_event_codes.py` and commit the result. A check on pull requests fails if the committed files don't match the tables.
