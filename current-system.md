# e-reg current system

Updated 22 November 2026. Decisions live in [decisions.md](decisions.md); this file states
what is true now. Nothing is designed, built or flown yet.

Owner: Kione. Helpers: Anav. Next milestone: James: do we build it?.

Seeded from the [Notion brief](https://app.notion.com/p/41ecc5f72fe28137bd9bf30438c0246f) and from Ogma2's decisions as they stood on
22 November. Where they disagree, Ogma2's decisions win, and the difference is
listed below.

## Purpose

The electronics for propulsion's electronic pressure regulator: its own board beside the valve bay, next to the valve and transducers it controls, running the pressure loop locally ([D-21Nov.10](https://github.com/ULAS-HiPR/Ogma2/blob/main/decisions.md)). **Whether avionics builds it at all is with James.** Nothing here is locked until he confirms.

## Must demonstrate

- Holds its set pressure through a cold-flow bench run.
- Goes to a safe state on a fault or on lost power.

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
