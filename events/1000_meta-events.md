## Meta-Events (1000–1999)

**Meta-Events capture application- and session-level context that frames gameplay but is not part of gameplay itself.** These events represent how the player enters, exits, configures, and navigates the application and how gameplay sessions are started, paused, or ended.

Meta-Events describe the container around gameplay, not actions within the game world, narrative communication, or system behavior during gameplay.

| Code Range | Family                            | Family Description |
| ---------- | --------------                    | ------------------ |
| 1000–1099  | Application Lifecycle             | Existence and focus of the application |
| 1100–1199  | Session Lifecycle                 | Lifecycle of a player activity session |
| 1200–1299  | Menu & Application Navigation     | Navigation through non-gameplay menus |
| 1300–1399  | Settings & Configuration          | Application or session configuration |
| 1400–1499  | Profile & Identity                | Player identity management |
| 1500–1599  | Loading & Application Transitions | Application readiness and transitions |
| 1600–1699  | Matchmaking                       | Player participation in matchmaking processes used to form gameplay sessions. |

### Application Lifecycle (1000–1099)

**Family intent**: Capture application start/stop and focus transitions.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 1000       | application launched     | The application is launched or started. |
| 1001       | application terminated   | The application is closed or terminated. |
| 1002       | application foregrounded | The application becomes the active foreground application. |
| 1003       | application backgrounded | The application leaves the foreground. |

### Session Lifecycle (1100–1199)

*Family intent*: Capture the start and end of player activity sessions within the application.

Sessions represent continuous periods of player activity within the application. A new session begins when a player interacts with the application after launch or after a period of inactivity exceeding the session timeout threshold. Sessions may end when the player exits the application or when inactivity exceeds the timeout threshold.

Session lifecycle events describe this activity boundary and do not represent gameplay actions themselves.

| Event Code | Event Name      | Description                |
| ------     | -------------   | -------------------------- |
| 1100       | session started | A gameplay session begins. |
| 1101       | session paused  | The gameplay session is paused. |
| 1102       | session resumed | A paused gameplay session resumes. |
| 1103       | session ended   | The gameplay session ends. |
| 1104       | session reset   | The gameplay session is reset. |

### Menu & Application Navigation (1200–1299)

**Family intent**: Capture player navigation through application-level menus and non-gameplay screens.

| Event Code | Event Name              | Description                                 |
| ------     | ----------------        | -------------------------                   |
| 1200       | open main menu          | The player opens the main application menu. |
| 1201       | close main menu         | The player closes the main application menu. |
| 1202       | navigate menu screen    | The player moves between application-level menu screens without selecting an option. |
| 1203       | return to previous menu | The player returns to the previous menu screen. |
| 1204       | select menu option      | The player selects an application-level menu option. |

### Settings & Configuration (1300–1399)

**Family intent**: Capture changes to application/session configuration outside gameplay.

| Event Code | Event Name              | Description                                 |
| ------     | ----------------        | -------------------------                   |
| 1300 | open settings | The player opens the settings screen. |
| 1301 | change setting | The player changes a setting value. |
| 1302 | reset settings | Settings are reset to defaults. |
| 1303 | close settings | The settings screen is closed. |

### Profile & Identity (1400–1499)

**Family intent**: Capture profile selection and identity/authentication actions outside gameplay.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 1400 | select profile | A player profile is selected. |
| 1401 | login | A player logs in. |
| 1402 | logout | A player logs out. |
| 1403 | create profile | A new player profile is created. |
| 1404 | delete profile | A player profile is deleted. |

### Loading & Application Transitions (1500–1599)

**Family intent**: Capture application readiness states and transitions that occur outside gameplay. Loading and transition events describe internal application states that occur while the application is already running, such as loading assets, preparing gameplay environments, or transitioning between major modes of the application.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 1500 | start loading | Application-level loading begins. |
| 1501 | loading complete | Application-level loading completes. |
| 1502 | start application transition | A non-gameplay application transition begins. |
| 1503 | complete application transition | A non-gameplay application transition completes. |

### Matchmaking (1600–1699)

**Family intent**: Capture player participation in matchmaking processes used to assemble gameplay sessions.

Matchmaking events describe system processes that place players into multiplayer sessions. These events represent entry into matchmaking, waiting or queue states, assignment to matches or lobbies, and exit from matchmaking before gameplay begins.
Matchmaking events capture how multiplayer sessions are formed but do not represent gameplay actions themselves.

| Event Code | Event Name               | Description            |
| ------     | --------------           | ---------------------- |
| 1600 | enter matchmaking | The player enters a matchmaking process to be placed into a gameplay session. |
| 1601 | exit matchmaking | The player leaves a matchmaking process before being placed into a session. |
| 1602 | matchmaking match found | The system identifies a compatible match for the player. |
| 1603 | matchmaking assignment | The player is assigned to a gameplay session or pre-game lobby. |
| 1604 | matchmaking timeout | The matchmaking process ends without forming a match. |

