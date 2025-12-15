```md
# Pilot (FiveM)

Pilot is a standalone FiveM self-driving / autopilot system with role profiles (civilian, police, EMS, taxi), adaptive speed, basic obstacle sensing, waypoint/route navigation, convoy following, and pull-over / park controls.

> **Status: HEAVY BETA**
>
> Pilot is under active development. Behavior, commands, and tuning may change, and some edge cases may still be rough.
>
> Planned upgrades include: smarter intersection handling, real overtake logic, better pathing/repathing, optional NUI menu, and more role-specific behaviors.

---

## Installation

1. Download / clone this repo into your FiveM `resources` folder:
```

resources/pilot

```
2. Add to `server.cfg`:
```

ensure pilot

```
3. Restart your server or `refresh` + `ensure pilot`.

---

## Quick Start

- Set a waypoint on the map (recommended)
- Run:
- `/ap` to start
- `/apstop` to stop instantly

Default destination is waypoint (`wp`). If you don’t have a waypoint, use `/apdest wander`.

---

## Commands

### Core
- `/ap`  
Toggle self driving ON/OFF.

- `/apstop`  
Hard stop (kills tasks, clears lights/sirens/indicators).

- `/appause`  
Pause (stops driving but keeps system enabled).

- `/apresume`  
Resume driving.

---

### UI / Debug
- `/apui on` | `/apui off` | `/apui`  
Toggle the on-screen HUD.

- `/apdebug on` | `/apdebug off` | `/apdebug`  
Toggle debug readouts.

---

### Units / Speed
- `/apunit mph` | `/apunit kph`  
Switch speed units.

- `/apspeed <number>`  
Set the target speed in the current unit.  
Examples: `/apspeed 35`, `/apspeed 70`

---

### Roles / Police Modes
- `/aprole civilian`
- `/aprole taxi`
- `/aprole ems`
- `/aprole police`  
Sets the main driving role.

Police mode shortcut (also sets role to police):
- `/appolice patrol`
- `/appolice response`
- `/appolice pursuit`

---

### Lane Modes
- `/aplane strict`
- `/aplane normal`
- `/aplane loose`
- `/aplane rightlane`
- `/aplane nopass`
- `/aplane pass_if_blocked`
- `/aplane shoulder`

---

### Destination / Navigation
- `/apdest wp`  
Drive to the map waypoint.

- `/apdest wander`  
Roam roads (no waypoint required).

- `/apdest here`  
Set destination to your current position.

- `/apdest clear`  
Reset destination back to waypoint mode.

- `/apgoto <x> <y> <z>`  
Drive to an exact coordinate.  
Example: `/apgoto 215.3 -810.2 30.7`

---

### Arrival Behavior
- `/aparrive stop` | `/aparrive park` | `/aparrive none`  
What to do when arriving at the destination.

- `/aparrive <radiusMeters>`  
Set how close you must get before “arrived” triggers.  
Examples: `/aparrive 8`, `/aparrive 20`

---

### Follow / Convoy
- `/apfollow <server_id> [distMeters]`  
Follow another player by server ID.  
Examples: `/apfollow 12`, `/apfollow 12 15`

- `/apfollowdist <meters>`  
Set follow distance.  
Example: `/apfollowdist 18`

---

### Siren / Lights / Hazards
- `/apsiren auto` | `/apsiren on` | `/apsiren off`
- `/aplights auto` | `/aplights on` | `/aplights off`
- `/aphaz on` | `/aphaz off` | `/aphaz`  
Toggle hazards.

---

### Pull Over / Park
- `/appark`  
Park immediately where you are.

- `/appullover [right|left] [meters]`  
Pull to the shoulder then park (hazards on).  
Examples: `/appullover`, `/appullover left 10`

---

### Testing / Tuning
- `/aptraffic on` | `/aptraffic off`  
Toggle NPC vehicle traffic (useful for testing).

- `/aptrackwp on` | `/aptrackwp off`  
If ON, autopilot updates when your waypoint changes.

- `/apoverride stop` | `/apoverride ignore`  
- `stop` = player throttle/steer cancels Pilot  
- `ignore` = Pilot keeps control even if you touch controls

---

### Routes (Record + Replay)
- `/aproute add`  
Add a route point at your current vehicle position.

- `/aproute clear`  
Remove all route points.

- `/aproute play`  
Start driving the saved points in order.

- `/aproute stop`  
Stop route playback.

- `/aproute loop on` | `/aproute loop off`  
Loop the route.

- `/aproute save`  
Save route to client KVP storage.

- `/aproute load`  
Load route from client KVP storage.

---

### Help
- `/aphelp`  
Prints a quick command list in-game.

---

## Notes / Known Limitations (Beta)

- GTA/FiveM AI driving has limits. It can still do dumb things in rare cases.
- “Traffic light behavior” is best-effort and not perfect.
- Some emergency features depend on the vehicle having siren/lights support.
- Tuning varies by server handling packs and vehicle mods.

---

## License

Choose a license before publishing (MIT is common). If you don’t add one, GitHub treats it as “all rights reserved.”
```
