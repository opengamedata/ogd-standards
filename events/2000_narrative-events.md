## Narrative & Communication Events (2000–2999)

N**arrative & Communication events capture how the game presents information, story, instruction, and feedback to the player.** These events represent player-visible communication such as narration, dialog, tutorials, feedback, and hints, regardless of whether the interaction is interactive or non-interactive.

Narrative & Communication events describe what is communicated and how it progresses, not the gameplay consequences of that communication and not analytic interpretation of player understanding.

| Code Range | Family            | Family Description |
| ---------- | ---------------   | ------------------ |
| 2000–2099  | Narration         | Non-interactive or minimally interactive narrative presentation |
| 2100–2199  | Dialog            | Interactive dialog with characters (with/without choices) |
| 2200–2299  | Tutorialization   | Instructional guidance during gameplay |
| 2300–2399  | Positive Feedback | Affirmative feedback in response to correct action |
| 2400–2499  | Negative Feedback | Corrective feedback in response to incorrect action |
| 2500–2599  | Hinting           | System- or player-initiated hints/help |
| 2600–2999  | Reserved          | Reserved for future narrative/communication families |

### Narration (2000–2099)

**Family intent**: Capture presentation and progression of non-interactive or minimally interactive narration (at most allow skip).

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 2001       | enter narration | Narration sequence becomes available/active. |
| 2002       | exit narration | Narration sequence is exited and no longer active. |
| 2003       | abandon narration | Narration ends before completion due to interruption or quit. |
| 2010       | start narration | Narration begins advancing/playing. |
| 2011       | complete narration | Narration reaches its intended end without skipping/abandoning. |
| 2012       | clear narration | Narration display is cleared or no longer available. |
| 2013       | advance narration | Narration advances to the next unit (player or system driven). |
| 2014       | skip narration | Narration is skipped to the end (or past remaining content). |

### Dialog (2100–2199)

**Family intent**: Capture interactive dialog sequences between the player character and other characters, with or without choices/free response.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 2101       | enter dialog | Dialog sequence becomes available/active. |
| 2102       | exit dialog | Dialog sequence is exited and no longer active. |
| 2103       | abandon dialog | Dialog ends before completion due to interruption or quit. |
| 2110       | start dialog | Dialog begins advancing/playing. |
| 2111       | complete dialog | Dialog reaches its intended end (animation/playback finished). |
| 2112       | clear dialog | Dialog display is cleared or no longer available. |
| 2113       | advance dialog | Dialog advances to the next unit (typically player action). |
| 2114       | skip dialog | Dialog is skipped to the end (typically player action). |
| 2115       | choices displayed | Dialog choice options are displayed to the player. |
| 2116       | choice selected | A dialog choice is selected. |
| 2117       | free response initiated | Player begins a free-text or open response input. |
| 2118       | submit response | Player submits a dialog response (choice or free response). |

### Tutorialization (2200–2299)

**Family intent**: Capture presentation and progression of tutorial/instructional sequences.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 2201       | enter tutorial | Tutorial sequence becomes available/active. |
| 2202       | exit tutorial | Tutorial sequence is exited and no longer active. |
| 2203       | abandon tutorial | Tutorial ends before completion due to interruption or quit. |
| 2210       | start tutorial | Tutorial begins advancing/playing. |
| 2211       | complete tutorial | Tutorial reaches its intended end. |
| 2212       | clear tutorial | Tutorial display is cleared or no longer available. |
| 2213       | advance tutorial | Tutorial advances to the next unit. |
| 2214       | skip tutorial | Tutorial is skipped to the end. |

### Positive Feedback (2300–2399)

**Family intent**: Capture affirmative feedback sequences presented in response to correct player actions.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 2310       | start positive feedback | Positive feedback sequence begins. |
| 2311       | complete positive feedback | Positive feedback sequence completes naturally. |
| 2312       | clear positive feedback | Positive feedback display is cleared or no longer available. |
| 2313       | advance positive feedback | Positive feedback advances to the next unit (if multi-part). |
| 2314       | skip positive feedback | Positive feedback is skipped to the end. |

### Negative Feedback (2400–2499)

**Family intent**: Capture corrective/negative feedback sequences presented in response to incorrect player actions.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 2410       | start negative feedback | Negative feedback sequence begins. |
| 2411       | complete negative feedback | Negative feedback sequence completes naturally. |
| 2412       | clear negative feedback | Negative feedback display is cleared or no longer available. |
| 2413       | advance negative feedback | Negative feedback advances to the next unit (if multi-part). |
| 2414       | skip negative feedback | Negative feedback is skipped to the end. |

### Hinting (2500–2599)

**Family intent**: Capture hint/help sequences. Includes player-initiated requests for hints.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 2510       | start hint | Hint/help sequence begins. |
| 2511       | complete hint | Hint/help sequence completes naturally. |
| 2512       | clear hint | Hint/help display is cleared or no longer available. |
| 2513       | advance hint | Hint/help advances to the next unit. |
| 2514       | skip hint | Hint/help is skipped to the end. |
| 2515       | request hint | Player requests a hint/help (player-initiated request). |
