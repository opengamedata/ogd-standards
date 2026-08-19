## System-Controlled Actor Action Events (6000–6999)

System-Controlled Actor Action events capture gameplay actions performed by non-focal actors whose behavior is controlled by the game rather than by a human player. These actors may include NPCs, enemies, companions, creatures, bots, scripted agents, or other autonomous in-game entities with action-selection capability.

System-Controlled Actor Actions represent intentional actions performed by non-focal game-controlled actors, analogous to Player Action events in the 4000 range.

These events mirror the structure of Player Actions but indicate that the acting entity is a non-focal computer-controlled actor rather than the focal player or another human player.

System-Controlled Actor Action events should be used when an in-game actor performs an action. They should not be used for non-agentic world changes, environmental updates, or broader system state changes; those remain System Action events (6000s).

| Event Code | Event Name               | Description |
| ------     | --------------           | ---------------------- |
| 6100–6199  | Puzzle / Constructed Response | Object manipulation actions performed by computer-controlled actors |
| 6200–6299  | Point-and-Click          | Selection and activation actions performed by computer-controlled actors |
| 6300–6399  | Combat                   | Combat actions performed by computer-controlled actors |
| 6400–6499  | Navigation               | Movement actions performed by computer-controlled actors |
| 6500–6599  | Resource Management      | Resource acquisition or consumption by computer-controlled actors |
| 6600–6699  | Simulation               | Simulation configuration actions by computer-controlled actors |
| 6700–6799  | Interface / Structural Navigation | Navigation through game structure by computer-controlled actors |
| 6800–6999  | Reserved                 | Reserved for future computer-controlled actor action families |
