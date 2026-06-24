[README_FLAT.md](https://github.com/user-attachments/files/29299727/README_FLAT.md)
# Three-Tank Water Transfer System — CODESYS PLC/HMI V1 Simulation

**Status:** Functional V1 portfolio project
**Platform:** CODESYS
**Programming:** Ladder Diagram (LD), Structured Text (ST)
**HMI:** CODESYS Visualization
**Project type:** PLC/HMI process automation simulation

This repository contains a CODESYS-based PLC/HMI simulation of a three-tank
water-transfer process. The project demonstrates step-based sequence control,
pump and valve permissives, simulated device feedback, alarm/fault handling,
reset behavior, manual device control, and an HMI overview.

![CODESYS HMI Overview](assets/screenshots/01_hmi_overview.png)

## Project Objective

The goal of this V1 project is to demonstrate practical PLC engineering thinking
in a simulated industrial process — not to claim a commissioned industrial
installation. The logic is structured around a realistic automation pattern:

```
Permissive -> Command -> Feedback -> Fault -> Alarm / Reset
```

## Tools Used

| Tool | Use |
|---|---|
| CODESYS | PLC programming and visualization platform |
| Ladder Diagram (LD) | Main sequence, interlocks, alarms, device logic |
| Structured Text (ST) | Tank-level simulation and range calculations |
| CODESYS Visualization | HMI overview for monitoring and operation |

## Process Description

The simulated system transfers water through three tanks:

1. T101 is filled through inlet valve XV101.
2. Water is transferred from T101 to T102 through XV102 using pump P101.
3. Water is transferred from T102 to T103 through XV103 using pump P102.
4. The process finishes when T103 reaches its fill setpoint.
5. Critical faults move the system to S90 Fault and require reset after the cause is cleared.

```mermaid
flowchart TD
    INLET[Inlet Supply] --> XV101[XV101 Inlet Valve] --> T101[T101]
    T101 --> XV102[XV102 Transfer Valve] --> P101[P101 Transfer Pump] --> T102[T102]
    T102 --> XV103[XV103 Transfer Valve] --> P102[P102 Transfer Pump] --> T103[T103]
```

## Automatic Sequence

| Step | State | Description |
|---|---|---|
| S0  | Idle | Safe waiting state |
| S10 | Precheck | Initial checks before filling |
| S20 | Fill T101 | Open XV101 and fill Tank 101 |
| S30 | T101 Ready | Tank 101 reached filling setpoint |
| S40 | Transfer T101 to T102 | Open XV102 and run P101 |
| S50 | T102 Ready | Tank 102 reached filling setpoint |
| S60 | Transfer T102 to T103 | Open XV103 and run P102 |
| S70 | Complete | Process completed successfully |
| S90 | Fault | Fault state, reset required |

## Main Features

- Full automatic sequence from S0 to S70
- Fault state S90 with reset behavior
- Valve command, simulated open feedback, and missing-feedback fault logic
- Pump start command, simulated run feedback, and missing-run fault logic
- Tank high-high, high, low, and low-low indications
- Manual device-control concept for V1 testing
- ST-based analog tank-level simulation
- CODESYS Visualization HMI overview

## CODESYS Project File

The CODESYS project file is included at:

```
codesys/ThreeTank_WaterTransfer_CODESYS_V1.project
```

## HMI / Visualization

The HMI provides a one-screen overview of the process:

- Start / Stop / Auto Mode / Fault indication
- T101, T102, T103 level bars
- Pump and valve status indications
- Filling and transfer indicators
- Tank level alarm indicators
- Basic manual operation indicators

## Structured Text Simulation

Structured Text simulates the tank levels. The logic increases or decreases tank
levels based on valve and pump feedback states, then clamps all levels between
0% and 100%.

![Structured Text Simulation](assets/screenshots/08_structured_text_simulation.png)

## Screenshots

**Tank 1 — sequence logic**
![Tank 1 sequence logic](assets/screenshots/02_tank1_sequence_logic.png)

**Tank 1 — valve, feedback, and alarm logic**
![Tank 1 valve logic](assets/screenshots/03_tank1_valve_feedback_alarm_logic.png)

**Tank 2 — transfer permissive logic**
![Tank 2 transfer logic](assets/screenshots/04_tank2_transfer_permissive_logic.png)

**Tank 2 — valve/pump feedback logic**
![Tank 2 feedback logic](assets/screenshots/05_tank2_valve_pump_feedback_logic.png)

**Tank 3 — transfer permissive logic**
![Tank 3 transfer logic](assets/screenshots/06_tank3_transfer_permissive_logic.png)

**Tank 3 — pump/fault logic**
![Tank 3 pump fault logic](assets/screenshots/07_tank3_pump_fault_logic.png)

## Demo Video

A short demo of the running simulation (auto start → filling → transfers → fault/reset):

**Demo video:** 

https://github.com/user-attachments/assets/1f342805-5170-41db-9a4f-bd6626171fb8



## Note

This is a V1 **simulation** project for portfolio purposes — it demonstrates
practical PLC development and industrial automation thinking, and is not a final
commissioning package.

---

**Project by:** Mohammad Hamdan — PLC programming, automation engineering, CODESYS, industrial control logic
