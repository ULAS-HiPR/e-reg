# e-reg

HiPR's electronics for propulsion's electronic pressure regulator. Owner: Kione. Helpers: Anav.
Nothing is designed, built or flown yet.

**Start here:** [current system](current-system.md) → [decisions](decisions.md) → [Notion brief](https://app.notion.com/p/41ecc5f72fe28137bd9bf30438c0246f).

## Read in this order

1. [Current system](current-system.md): what is true now.
2. [Decisions](decisions.md): what is settled, what is proposed, what is open.
3. [Requirements](docs/requirements/README.md): captured by 14 December.
4. [Interfaces](interfaces/README.md): where e-reg meets the rest of the vehicle.
5. [Hardware](hardware/README.md) for CAD.

Don't start at the project log.

## Where things live

| Where | What |
| --- | --- |
| This repository | Decisions, requirements, interfaces, design files: the truth |
| [Notion brief](https://app.notion.com/p/41ecc5f72fe28137bd9bf30438c0246f) | The brief, for newcomers |
| Discord, avionics-projects → e-reg | Questions and chat |
| [Ogma2](https://github.com/ULAS-HiPR/Ogma2) | Burrito and Churro, the core e-reg connects to, and the template this repository copies |

## Repository

| Path | Contents |
| --- | --- |
| `docs/requirements/` | Requirements with their source, mechanism and verification |
| `interfaces/` | Contracts with neighbouring boards |
| `hardware/` | Native KiCad and drawings, tracked directly |
| `sources/` | Only evidence a current decision needs |
| `project-log.md` | Append-only history |

CAD, measurements and datasheets outrank prose. No raw transcripts, private
correspondence or generated dumps. This repository is public.
