# e-reg current system

Updated 22 November 2026. Decisions live in [decisions.md](decisions.md); this file states
what is true now. Nothing is designed, built or flown yet.

Owner: Kione. Helpers: Anav. Next milestone: Requiements 26/11/26.

Seeded from the [Notion brief](https://app.notion.com/p/41ecc5f72fe28137bd9bf30438c0246f) and from Ogma2's decisions as they stood on
22 November. Where they disagree, Ogma2's decisions win.

## Purpose

Pressure regulation system for the propulsion subsystem: It has a board beside the valve bay, next to the valve and transducers it controls, running the pressure loop locally ([D-21Nov.10](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md)).
**Whether avionics builds it at all is with James.** He confirmed that the e-reg will be built.


## Role
- Regulate COPV pressure into fuel and nitrous tanks
- Use closed-loop control system to automatically maintain a set amount of pressure
  for the tanks without interaction.
- Independent from main flight computer



## Functionality must include

- Holding its target pressure through a cold-flow bench run.
- Enters a safe state when a fault occurs
- Enters a safe state when power is lost


 
## Architecture
- 2 boards
- 1 To maintain fuel tank pressure
  2 To maintain nitrous tank pressure
- Built close to valve bay and to the systems it control
- Valve: Allows high pressure into the e-reg
- Vent: releases excess pressure
- Regulates tank pressure

## Connection to hardware
- Regulate COPV pressure into tanks
- Compare current pressure with the maximum pressure allowed-using a sensor
- Controls minimum,maximum and maintained pressure
- Each tank has valves
- Has 2 vents per board
- Too low? valve is opened
- Too high? vents open
- Neither ? Valves remain closed
- valve: Allows high presurised gas into the tank
- vent: used to release excess pressure when e-reg lets in too much
- Each e-reg has its own e-reg board
- Has a pressure sensor to read the pressure values

## Connection to Fajita
- Fajita is the main propulsion controller
- Both E-regs are connected through a CAN link
- Independent from main flight computer

### Fajita sends
-  state: safe,active,abort
-  maximum and target pressures

### E-REG sends
- Tank pressure
- valve state
- fault status
- health information on the tanks
- only regulates pressure when receives an ok /active command from fajita

#### State received
- Active command: E-REG regulates when it receives an active command from jajita
- Abort command: E-REG enters safe state using failure system within a specified response time( as quick as possible)
- Relies on Fajita for safety conditions

  
## CAN COMMUNICATION

## OPEN
- Connector type
- CAN bitrate
- Message rate
- frequency of sending health information to and from Fajita
- Should there be a "timeout" where nothing happens before it is put into a safe state


## Connection to Churro
 Fajita is the main propulsion controller
- Receives power
- Route : still to be decided
- Churro- fajita -e-reg servo/valve actuator

## Connection to Burrito 
- No direct connection
- Monitoring handled by fajita (main controller)


## Safety Systems
- 2 valves per e-reg
- Pressure exceeds threshold : vent oepns
- Fajita can handle venting(still open)
- Must be able to vent regardless of e-reg's state
- 

# Questions


## Firmware
- Can wait
- Uses STM32
- Knowledge in C++ important -can be learned


  
  

## Interfaces

Set by Ogma2's decisions unless marked proposed. Changing one needs the other
owner's agreement and a row in both repositories.

| With | What | Ogma2 decision |
| --- | --- | --- |
| Fajita | Its own CAN link to Fajita. Never on bus 1, which stays Burrito–Fajita. Fajita can vent whatever the e-reg does. | [D-21Nov.10](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md) |
| Churro | Its valve servo takes power from Churro's PROP branch, through Fajita (proposed in D-21Nov.10, not decided). | [D-21Nov.10](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md) |
| Burrito | None. It sits inside propulsion's boundary. | — |

## External rules

Appendix E1 if it powers a propellant valve; LV-0300–0320 if it carries its own pack; LV-0190 if it's part of the vent path.

## Parts one person can own

1. Valve driver and the servo's power
2. Pressure sensing and the loop
3. The link to Fajita and the safe state

## Timeline

| Milestone | Date |
| --- | --- |
| Requirements captured | 14 December 2026 |
| Schematics reviewed | 28 December 2026 |
| PCBs laid out and ordered | 11 January 2027 |
| Boards in hand | 1 February 2027 |
| Testing, firmware and integration | from 1 February 2027 |
| All electronics on one table | 3 weeks before the integrated vehicle |

From the [Electronics page](https://app.notion.com/p/3c8cc5f72fe28092aaf7dc3baacb4f67)'s avionics timeline.

## State

Repository created 22 November 2026. No requirements, schematic, layout or
firmware yet. Open questions are in [decisions.md](decisions.md#open).
