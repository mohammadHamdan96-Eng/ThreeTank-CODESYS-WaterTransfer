# Project Report - Three-Tank Water Transfer System

## 1. Executive Summary

This project is a CODESYS PLC/HMI simulation of a three-tank industrial water-transfer process. It was developed to demonstrate practical PLC programming ability using Ladder Diagram, Structured Text, sequence logic, device permissives, alarms, fault handling, manual operation, and HMI visualization.

The V1 system contains a full automatic cycle, simulated analog tank levels, valve and pump command-feedback behavior, alarm indications, reset logic, and a basic manual operating mode for device testing.

## 2. Project Objective

The objective was to build a realistic automation portfolio project that proves the following skills:

- Building PLC sequence logic from zero
- Designing process steps and transitions
- Controlling valves and pumps with interlocks
- Simulating analog tank levels
- Detecting faults from missing feedback
- Creating an HMI overview screen
- Presenting a complete V1 automation project professionally

## 3. Tools Used

| Tool | Use |
|---|---|
| CODESYS | PLC programming and HMI visualization |
| Ladder Diagram (LD) | Main process logic, sequence steps, alarms, interlocks |
| Structured Text (ST) | Analog tank-level simulation and normal range logic |
| CODESYS Visualization | HMI overview and operator interface |

## 4. Process Description

The simulated process transfers water through three tanks:

1. Tank T101 is filled through inlet valve XV101.
2. When T101 reaches its setpoint, the system transfers water to T102 using valve XV102 and pump P101.
3. When T102 reaches its setpoint, the system transfers water to T103 using valve XV103 and pump P102.
4. The process ends when T103 reaches its final fill setpoint.
5. Any major fault sends the system to S90 Fault.

## 5. Sequence Logic

| Step | Name | Purpose |
|---:|---|---|
| 0 | Idle | Safe waiting state |
| 10 | Precheck | Start delay and permissive checking |
| 20 | Fill T101 | Inlet filling using XV101 |
| 30 | T101 Ready | T101 filled and ready for transfer |
| 40 | Transfer T101 to T102 | XV102 + P101 active |
| 50 | T102 Ready | T102 filled and ready for transfer |
| 60 | Transfer T102 to T103 | XV103 + P102 active |
| 70 | Complete | Process complete |
| 90 | Fault | Fault state requiring reset |

## 6. Device Logic Philosophy

The device logic follows this engineering pattern:

```text
Request / permissive -> Command -> Feedback -> Fault detection -> Alarm indication
```

For example, a valve is commanded open, then a feedback delay simulates open feedback. If the command remains active and feedback does not appear within a defined time, a fault is latched and the sequence can move to S90.

## 7. Alarm and Fault Handling

The V1 project includes:

- Tank high-high alarms
- Tank high warnings
- Tank low warnings
- Tank low-low alarms
- Valve feedback faults
- Pump running feedback faults
- Emergency and stop behavior
- Reset from S90 after clearing conditions

## 8. Manual Mode V1

Manual mode allows basic device-level testing. It is included as a V1 feature and demonstrates the concept of manual control. For a future professional version, manual mode should be further refined with separate AutoCmd, ManualCmd, and FinalCmd variables for every actuator.

## 9. HMI Overview

The CODESYS visualization screen provides a full process overview with:

- Tank level bars
- Start, stop, auto, and fault indication
- Valve and pump indicators
- Tank alarms and normal-level indicators
- Filling and transfer state indicators

## 10. Project File and Evidence

The CODESYS project file is included in the repository under:

```text
codesys/ThreeTank_WaterTransfer_CODESYS_V1.project
```

Screenshots and documentation are included. A short demo video should be recorded and linked in the README to show the automatic sequence, fault/reset behavior, and manual operation.

## 11. Future Work

- Siemens TIA Portal / WinCC version
- Reusable function blocks for pumps, valves, tanks, and alarms
- Formal alarm acknowledgement and alarm history
- HMI trend screen for tank levels
- Completed FAT results with screenshots/video evidence
- Electrical/EPLAN-style signal documentation
