## Event Logging Approach

### Event Definition

An event is a timestamped record of a concrete occurrence representing a player action, system action, narrative interaction, structural transition, or application/session-level change.

Events are discrete and atomic; each event captures a single, well-defined occurrence.

Durational or ongoing states should be represented using state-transition events (e.g., start and end), rather than as continuous conditions.

Event codes defined in this codebook identify types of events, which are instantiated as individual event records during gameplay.

Events describe what happened in the game, not why it happened or what it means analytically.

### Governing Rule

Every event must be interpretable on its own as a concrete occurrence, free of analytic judgment or inferred intent.

Event records must not encode:

* analytic interpretation or judgment,
* inferred player intent beyond the logged action,
* inferred player skill, engagement, or learning,
* success or failure as an analytic conclusion.

Events may reflect game-level rule evaluation (e.g., valid vs. invalid actions) when that evaluation is part of the game’s mechanics, but must not represent analytic inference.

Derived measures and interpretive constructs are expected to be computed downstream using the raw event data defined by this codebook.

###	Focal Player Perspective

Events in this schema are recorded from the perspective of a focal player. The event stream represents what occurs in relation to that player’s interaction with the game system.

Actions performed by the focal player are recorded as Player Action events (4000s).

Actions performed by the game system are recorded as System Action events (5000s).

Actions performed by other actors with agency, such as other players or NPCs, are recorded as Other Actor Action events (6000s).

This perspective ensures that event records consistently capture the interaction between the focal player, the game system, and other actors within the game environment.

In multiplayer environments, each player’s event stream may be recorded separately from that player’s perspective.

### Units of Analysis

The following units describe different types of data that may appear in a gameplay telemetry system. Only events are defined and standardized by this codebook; the other units provide context for how event data may be organized or supplemented.

#### Primary Unit: Event

Each recorded event is an instance of an event type defined in this codebook.

#### Event Attributes

Attributes provide additional detail (e.g., identifiers, spatial data, replay context) without changing the semantic identity of the event.

The codebook defines event types, while payload structure is defined separately. Contextual detail (e.g., object type, target, outcome) should be captured as attributes and is not represented within the event code.

#### Contextual Metadata

Metadata applies at session, player, or device scope and provides contextual information associated with event streams. These records are not logged as gameplay events.

#### High-Frequency Data Streams

High-frequency data streams capture continuous telemetry used for replay or simulation reconstruction. These streams are separate from the discrete event log defined by this codebook.

Continuous data (e.g., positional tracking, physics simulation, or input polling) should not be represented as discrete events. Such data should be captured separately as high-frequency telemetry or replay data streams.

### Session

A session represents a continuous period of player activity within the application.

A session begins when the player performs an interaction after application launch or after a period of inactivity exceeding the session timeout threshold.

A session ends when the player exits the application or when player inactivity exceeds the configured timeout threshold.

Sessions provide a container for gameplay events but are not themselves gameplay actions.

### Schema Structure and Code Hierarchy

Event codes in this codebook are organized using a hierarchical numeric structure that encodes both the type of gameplay interaction and the role of the event type within that interaction. The structure is designed to support consistency, extensibility, and analysis across different game designs while preserving semantic meaning at multiple levels of aggregation.

Each event code is composed of four hierarchical components, where higher-order digits represent broader, more stable concepts and lower-order digits represent more specific actions or outcomes. Event codes identify types of events defined by this standard, not individual occurrences of those events during gameplay.

#### Top-level category (thousands place)

The thousands place identifies the interaction domain to which an event belongs. This level distinguishes broad categories of gameplay experience, such as narration and dialogue, player actions, and game progression, or other major interaction types. Top-level categories define families of events that are conceptually related and comparable at a high level.

Top-level categories are intended to be stable and change infrequently. New top-level categories should be introduced only when a genuinely new interaction domain is added to the schema.

#### Interaction family (hundreds place)

The hundreds place identifies the interaction family within a top-level category. Interaction families correspond to specific gameplay systems, structured interactions, or recurring patterns within the broader domain.

This level allows events to be grouped by the system or interaction they are associated with, while remaining flexible enough to accommodate variation across games. Interaction families provide a meaningful middle layer for analysis and comparison.

#### Phase or function (tens place)

The tens place identifies the phase or functional role of the event within the lifecycle of an interaction. This level captures where the event occurs in the progression of an interaction, such as entry, initiation, completion, skipping, abandonment, or other common stages.

Phase codes are reused consistently across interaction families and top-level categories to support cross-domain comparison.

Not all top-level categories use all hierarchical positions; some categories intentionally omit tens-level semantics. Only categories representing multi-step sequences (notably Narrative and Segmentation) use tens-place semantics to represent phases of an interaction. In other categories, the tens and ones places together identify the specific event type.

#### Specific event (ones place)

The ones place identifies the specific event type within the family. In categories that use tens-place semantics, it identifies the event within the current phase. This level distinguishes concrete player actions or system outcomes that occur at a particular phase of an interaction, such as selecting an option, completing a sequence, or exiting an interaction.

New codes are most commonly introduced at this level. Specific event codes must not redefine or contradict the meaning established by the higher-level components of the code.

Only categories representing multi-step sequences (notably Narrative and Segmentation) use tens-place semantics.
