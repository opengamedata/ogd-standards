## Player Action Events (4000–4999)

Player Action events capture intentional, atomic actions performed by the player during gameplay. These events represent what the player attempts to do, independent of whether the attempt succeeds or what outcomes result.

Player Action events describe player intent, not system response, not narrative presentation, and not analytic or evaluative outcomes.

| Code Range | Family | Family Description |
| 4000–4099 | Universal Player Actions | Commit or cancel a gameplay response |
| 4100–4199 | Puzzle / Constructed Response | Manipulate objects to construct or modify a solution |
| 4200–4299 | Point-and-Click | Select, inspect, or activate objects via direct interaction |
| 4300–4399 | Combat | Target, attack, defend, or perform combat actions |
| 4400–4499 | Navigation | Move through space or time |
| 4500–4599 | Resource Management | Acquire, allocate, consume, or convert resources |
| 4600–4699 | Simulation | Configure or query simulation parameters |
| 4700–4799 | Interface / Structural Navigation | Navigate in-game structure or in-game interfaces |
| 4800–4999 | Reserved | Reserved for future player action families |

### Universal Player Actions (4000–4099)

**Family intent**: Capture explicit commitment or cancellation of a response/action.

| Event Code | Event Name | Description |
| 4000 | submit response | The player submits or commits a response or action. |
| 4001 | cancel submission | The player cancels or withdraws a previously initiated response. |

### Puzzle / Constructed Response (4100–4199)

**Family intent**: Capture object manipulation actions used to construct, test, or modify puzzle solutions.

Event Code
Event Name
Description
4100
pick up object
The player picks up or grabs an object.
4101
place object (valid)
The player places an object in a valid location/configuration.
4102
place object (invalid)
The player attempts to place an object in an invalid location/configuration.
4103
remove object
The player removes an object from its current placement.
4104
start rotate object
The player begins rotating an object.
4105
end rotate object
The player finishes rotating an object.
4106
preview placement
The player previews a potential object placement.
4107
modify object
The player modifies an object’s state or configuration.

### Point-and-Click (4200–4299)

**Family intent**: Capture direct click-based interaction with objects through selection, inspection, activation, or panning.

Event Code
Event Name
Description
4200
select object
The player selects an object.
4201
deselect object
The player deselects an object.
4202
activate object
The player activates or triggers an object.
4203
change object state
The player changes an object’s state through interaction.
4204
inspect object
The player inspects or examines an object.
4205
use object
The player applies or uses an object.
4206
start pan view
The player begins panning the view.
4207
end pan view
The player ends panning the view.

### Combat (4300–4399)

**Family intent**: Capture player intent to engage in combat-related actions.

Event Code
Event Name
Description
4300
select target
The player selects a combat target.
4301
initiate attack
The player initiates an attack.
4302
defend
The player performs a defensive action.
4303
evade
The player attempts to evade an attack.
4304
use ability
The player uses a combat ability.
4305
start aim
The player begins aiming.
4306
end aim
The player finishes aiming.

### Navigation (4400–4499)

**Family intent**: Capture movement through space or time within the game world.

Event Code
Event Name
Description
4400
start movement
The player begins moving.
4401
end movement
The player stops moving.
4402
enter area
The player enters a defined area.
4403
exit area
The player exits a defined area.
4404
set destination
The player sets a movement destination.
4405
snap to location
The player snaps to a specific location.
4406
advance time
The player advances time.

### Resource Management (4500–4599)

**Family intent**: Capture intent to acquire, allocate, consume, lose, discard, or convert resources.

Event Code
Event Name
Description
4500
buy
The player purchases a resource or item.
4501
sell
The player sells a resource or item.
4502
store
The player stores a resource or item.
4503
collect
The player collects or acquires a resource.
4504
use resource
The player uses or consumes a resource.
4505
lose resource
The player loses a resource.
4506
discard resource
The player discards a resource.
4507
allocate resource
The player allocates a resource.
4508
convert resource
The player converts one resource into another.

### Simulation (4600–4699)

**Family intent**: Capture player configuration or interrogation of simulation parameters (not simulation execution).

Event Code
Event Name
Description
4600
assign
The player assigns an entity or resource.
4601
unassign
The player removes an assignment.
4602
set priority
The player sets a priority value.
4603
adjust parameter
The player adjusts a simulation parameter.
4604
schedule action
The player schedules a simulation action.
4605
pause simulation
The player pauses the simulation.
4606
resume simulation
The player resumes the simulation.
4607
request current state
The player requests the current simulation state.

### Interface / Structural Navigation (4700–4799)

**Family intent**: Capture player intent to navigate the game’s structure or in-game interfaces (not application-level menus).

Event Code
Event Name
Description
4700
select segment
The player selects a segment or subsegment.
4701
open interface
The player opens an in-game interface element.
4702
close interface
The player closes an in-game interface element.
4703
navigate to screen
The player navigates to a different in-game screen.
4704
return to previous screen
The player returns to the previous in-game screen.
4705
select item
The player selects an interface item.
4706
confirm selection
The player confirms a selection.
4707
cancel selection
The player cancels a selection.
4708
switch view
The player switches views.
4709
toggle overlay
The player toggles an overlay.

