# Pilot (FiveM)

Pilot is a standalone FiveM self-driving / autopilot system with role profiles (civilian, police, EMS, taxi), adaptive speed, obstacle sensing, waypoint/route navigation, convoy following, and pull-over / park controls.

> Status: HEAVY BETA  
> Pilot is under active development. Behavior, commands, and tuning may change, and some edge cases may still be rough.  
> Planned upgrades include smarter intersection handling, real overtake logic, better pathing/repathing, optional NUI menu, and deeper role behaviors.

---

## Features

- Role profiles: civilian, police (patrol/response/pursuit), EMS, taxi
- Adaptive speed (curves, obstacles, follow distance)
- Basic forward “sensor” to reduce ramming
- Waypoint driving, coordinate driving, wandering
- Convoy / follow another player (server ID)
- Route recording + playback + save/load
- Pull-over + park behavior
- HUD + debug mode
- NPC traffic disable toggle (testing)

---

## Installation

1. Download / clone this repo into your FiveM `resources` folder:

   ```text
   resources/pilot

    Add to server.cfg:

    ensure pilot

    Restart your server (or refresh + ensure pilot).

Quick Start

    Set a waypoint on the map (recommended)

    Start: /ap

    Stop instantly: /apstop

No waypoint? Use /apdest wander.
Keybinds

    Toggle Pilot: J

    Stop Pilot: K

(You can rebind these in FiveM keybind settings.)
Commands
Core

    /ap — Toggle self driving ON/OFF

    /apstop — Hard stop (kills tasks, clears sirens/lights/indicators)

    /appause — Pause driving

    /apresume — Resume driving

UI / Debug

    /apui on | /apui off | /apui — HUD on/off

    /apdebug on | /apdebug off | /apdebug — Debug info on/off

Units / Speed

    /apunit mph | /apunit kph

    /apspeed <number> — Set target speed in current unit
    Examples: /apspeed 35, /apspeed 70

Roles / Police Modes

    /aprole civilian

    /aprole taxi

    /aprole ems

    /aprole police

Police mode (also sets role to police):

    /appolice patrol

    /appolice response

    /appolice pursuit

Lane Modes

    /aplane strict

    /aplane normal

    /aplane loose

    /aplane rightlane

    /aplane nopass

    /aplane pass_if_blocked

    /aplane shoulder

Destination / Navigation

    /apdest wp — Drive to map waypoint

    /apdest wander — Roam roads

    /apdest here — Set destination to current position

    /apdest clear — Reset destination back to waypoint mode

    /apgoto <x> <y> <z> — Drive to a coordinate
    Example: /apgoto 215.3 -810.2 30.7

Arrival Behavior

    /aparrive stop | /aparrive park | /aparrive none

    /aparrive <radiusMeters> — Example: /aparrive 12

Follow / Convoy

    /apfollow <server_id> [distMeters] — Examples: /apfollow 12, /apfollow 12 15

    /apfollowdist <meters> — Example: /apfollowdist 18

Siren / Lights / Hazards

    /apsiren auto | /apsiren on | /apsiren off

    /aplights auto | /aplights on | /aplights off

    /aphaz on | /aphaz off | /aphaz — Toggle hazards

Pull Over / Park

    /appark — Park immediately

    /appullover [right|left] [meters] — Examples: /appullover, /appullover left 10

Testing / Tuning

    /aptraffic on | /aptraffic off — Toggle NPC vehicles (testing)

    /aptrackwp on | /aptrackwp off — Repath when waypoint changes

    /apoverride stop | /apoverride ignore — Manual input cancels Pilot or not

Routes (Record + Replay)

    /aproute add

    /aproute clear

    /aproute play

    /aproute stop

    /aproute loop on | /aproute loop off

    /aproute save

    /aproute load

Help

    /aphelp — Quick list in-game
