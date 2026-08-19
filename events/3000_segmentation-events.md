## Segmentation Events (3000–3999)

Segmentation events capture where the player is within the game’s structural progression. These events represent entry into, progression through, and exit from defined gameplay segments such as levels, quests, rounds, modes, or spatial regions. Spatial region events describe structural location within the game world and may occur as a consequence of player navigation actions.

Segmentation events describe structural boundaries and location in the game, not player intent, not system feedback, and not narrative presentation.

| Code Range | Family | Family Description |
| ------     | --------------           | ---------------------- |
| 3000–3099 | Global Gameplay Segments | Game-wide phases not tied to specific mechanics (e.g., mode, run, chapter) |
| 3100–3199 | Exclusive Topological Segments | Ordered, mutually exclusive segments (e.g., levels) |
| 3200–3299 | Non-Exclusive Segments | Overlapping segments (e.g., quests, objectives) |
| 3300–3399 | Spatial Regions | Location-based regions/areas in the game world |
| 3400–3999 | Reserved | Reserved for future segmentation families |

Verb mapping (ones place) used consistently across segmentation families:

| Ones | Verb | Meaning |
| ------     | --------------           | ---------------------- |
| 0 | start / enter / begin | Segment begins or player enters the segment |
| 1 | end / complete / exit | Segment ends or player exits the segment |
| 2 | abandon / quit | Segment exits without completion |
| 3 | resume / restore / restart | Segment resumes or is restored |
| 4 | Pause | Segment is temporarily paused and may be resumed/restored |

### Global Gameplay Segments (3000–3099)

**Family intent**: Capture game-wide segments/phases (e.g., run start/end) when needed for analysis beyond session lifecycle.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 3000       | start global segment | A global gameplay segment begins. |
| 3001       | end global segment | A global gameplay segment ends. |
| 3002       | abandon global segment | Global gameplay segment exits without completion. |
| 3003       | resume global segment | Global gameplay segment resumes/restores. |

### Exclusive Topological Segments (3100–3199)

**Family intent**: Capture ordered, mutually exclusive segments such as levels. Use tens place for subsegments (e.g., rounds within a level).

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 3100       | start segment (level) | The current exclusive segment begins (e.g., level start). |
| 3101       | end segment (level) | The current exclusive segment ends (e.g., level complete/exit). |
| 3102       | abandon segment (level) | Exclusive segment exits without completion. |
| 3103       | resume segment (level) | Exclusive segment resumes/restores. |
| 3110       | start subsegment (round) | A subsegment within the exclusive segment begins (e.g., round start). |
| 3111       | end subsegment (round) | A subsegment within the exclusive segment ends. |
| 3112       | abandon subsegment (round) | Subsegment exits without completion. |
| 3113       | resume subsegment (round) | Subsegment resumes/restores. |

### Non-Exclusive Segments (3200–3299)

**Family intent**: Capture overlapping segments such as quests, objectives, or parallel progress tracks.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 3200       | start segment (quest/objective) | A non-exclusive segment begins. |
| 3201       | end segment (quest/objective) | A non-exclusive segment ends/completes. |
| 3202       | abandon segment (quest/objective) | A non-exclusive segment is abandoned. |
| 3203       | resume segment (quest/objective) | A non-exclusive segment resumes/restores. |

### Spatial Regions (3300–3399)

**Family intent**: Capture entering/exiting spatial regions such as map areas or rooms.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 3300       | enter region | Player enters a spatial region/area. |
| 3301       | exit region | Player exits a spatial region/area. |
| 3302       | abandon region | Region is exited via interruption/quit (without normal exit). |
| 3303       | resume region | Player returns to a region via restore/resume. |
