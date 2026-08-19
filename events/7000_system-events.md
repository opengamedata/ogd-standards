## System Action Events (7000–7999)

System Action events capture actions performed by the game system during gameplay that alter the state of the game world, entities, or information available to the player.

These events represent system agency within gameplay. They describe observable changes initiated by the system rather than by direct player input.

System Action events do not represent player intentions, analytic calculations, or telemetry outcomes. Instead, they record the system’s operational effects on the game environment, entities, resources, or gameplay information.

| Code Range | Family | Family Description |
| 7100–7199 | Entity & Resource Changes | Creation, removal, or transformation of entities and quantitative resources |
| 7200–7299 | Movement & Spatial Change | System-driven spatial movement of entities or environmental elements |
| 7300–7399 | Simulation Execution | Operational control of simulation execution states |
| 7400–7499 | Information & Visibility | Changes to player-visible information |
| 7500–7599 | In-Game Interface State | System-driven presentation or interactivity of gameplay interface elements |
| 7600-7699 | System Signaling | System-generated cues that signal gameplay-relevant states or conditions to the player |
| 7700–7999 | Reserved | Reserved for future system action families |

### Entity & Resource Changes (7100–7199)

**Family intent**: Capture system actions that modify the material state of gameplay. These include the creation, removal, or transformation of discrete entities as well as system-driven changes to quantitative gameplay resources.

Event Code
Event Name
Description
7110
create entity
The system introduces a new entity into active gameplay.
7111
remove entity
The system removes an entity from active gameplay.
7112
transform entity
The system changes an entity’s form, type, or role while preserving continuity within gameplay.
7120
increment resource
The system increases the value of a gameplay resource.
7121
decrement resource
The system decreases the value of a gameplay resource.
7122
update counter
The system advances or updates a counter or timer variable.

### Movement & Spatial Change (7200–7299)

**Family intent**: Capture system-driven changes to the spatial position of entities or environmental elements independent of direct player input.

Event Code
Event Name
Description
7200
start entity movement
The system initiates continuous movement of an entity.
7201
end entity movement
The system ends continuous movement of an entity.
7202
reposition entity
The system instantly relocates an entity to a new position.
7203
start environment movement
The system initiates movement of an environmental gameplay element.
7204
end environment movement
The system ends movement of an environmental gameplay element.
7205
reposition environment element
The system instantly relocates an environmental gameplay element.

### Simulation Execution (7300–7399)

**Family intent**: Capture system control of simulation execution states such as initialization, starting, pausing, or resetting simulation processes.

Event Code
Event Name
Description
7300
initialize simulation
The system initializes a simulation process.
7301
start simulation
The system begins executing a simulation.
7302
pause simulation
The system pauses simulation execution.
7303
resume simulation
The system resumes a paused simulation.
7304
advance simulation
The system advances the simulation by a discrete step or interval.
7305
reset simulation
The system resets the simulation to a baseline state.
7306
terminate simulation
The system terminates simulation execution.

### Information & Visibility (7400–7499)

**Family intent**: Capture system actions that change what gameplay-relevant information is visible or discoverable to the player.

Event Code
Event Name
Description
7400
reveal information
The system makes gameplay-relevant information visible or discoverable to the player.
7401
conceal information
The system hides gameplay-relevant information from the player.

### In-Game Interface State (7500–7599)

**Family intent**: Capture system-driven changes to the visibility or interactivity of in-game interface elements during gameplay.

Event Code
Event Name
Description
7500
display interface element
The system displays an in-game interface element.
7501
hide interface element
The system hides an in-game interface element.
7502
update interface element
The system updates the content or state of an interface element.
7503
enable interface element
The system enables interaction with an interface element.
7504
disable interface element
The system disables interaction with an interface element.

### System Signaling (7600–7699)

**Family intent**: Capture system-generated audiovisual cues that signal gameplay-relevant system states or conditions to the player.

These events represent system communication through ambient sensory channels such as sound, music, or visual effects. System signaling events indicate that a gameplay-relevant condition exists or is changing but do not themselves modify entities, resources, or simulation state.
Event Code
Event Name
Description
7600
start system signal
The system begins emitting a gameplay-relevant audiovisual signal.
7601
end system signal
The system stops emitting a gameplay-relevant audiovisual signal.
7602
change system signal
The system changes the type or state of an active signal.
