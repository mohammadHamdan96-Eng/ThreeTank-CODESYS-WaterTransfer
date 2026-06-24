[README.md](https://github.com/user-attachments/files/29299175/README.md)
# Three-Tank Water Transfer System - CODESYS PLC/HMI V1 Simulation

**Status:** Functional V1 portfolio project  
**Platform:** CODESYS  
**Programming:** Ladder Diagram (LD), Structured Text (ST)  
**HMI:** CODESYS Visualization  
**Project type:** PLC/HMI process automation simulation

This repository contains a CODESYS-based PLC/HMI simulation of a three-tank water-transfer process. The project demonstrates step-based sequence control, pump and valve permissives, simulated device feedback, alarm/fault handling, reset behavior, manual device control, and an HMI overview.

!\[CODESYS HMI Overview](assets/screenshots/01\_hmi\_overview.png)

## Project Objective

The goal of this V1 project is to demonstrate practical PLC engineering thinking in a simulated industrial process, not to claim a commissioned industrial installation. The logic is structured around a realistic automation pattern:

```text
Permissive -> Command -> Feedback -> Fault -> Alarm / Reset
```

## Tools Used

|Tool|Use|
|-|-|
|CODESYS|PLC programming and visualization platform|
|Ladder Diagram (LD)|Main sequence, interlocks, alarms, device logic|
|Structured Text (ST)|Tank-level simulation and range calculations|
|CODESYS Visualization|HMI overview for monitoring and operation|

## Process Description

The simulated system transfers water through three tanks:

1. T101 is filled through inlet valve XV101.
2. Water is transferred from T101 to T102 through XV102 using pump P101.
3. Water is transferred from T102 to T103 through XV103 using pump P102.
4. The process finishes when T103 reaches its fill setpoint.
5. Critical faults move the system to S90 Fault and require reset after the cause is cleared.

```mermaid
flowchart LR
    INLET\[Inlet Supply] --> XV101\[XV101 Inlet Valve]
    XV101 --> T101\[T101]
    T101 --> XV102\[XV102 Transfer Valve]
    XV102 --> P101\[P101 Transfer Pump]
    P101 --> T102\[T102]
    T102 --> XV103\[XV103 Transfer Valve]
    XV103 --> P102\[P102 Transfer Pump]
    P102 --> T103\[T103]
```

## Automatic Sequence

|Step|State|Description|
|-:|-|-|
|S0|Idle|Safe waiting state|
|S10|Precheck|Initial checks before filling|
|S20|Fill T101|Open XV101 and fill Tank 101|
|S30|T101 Ready|Tank 101 reached filling setpoint|
|S40|Transfer T101 to T102|Open XV102 and run P101|
|S50|T102 Ready|Tank 102 reached filling setpoint|
|S60|Transfer T102 to T103|Open XV103 and run P102|
|S70|Complete|Process completed successfully|
|S90|Fault|Fault state, reset required|

## Main Features

* Full automatic sequence from S0 to S70
* Fault state S90 with reset behavior
* Valve command, simulated open feedback, and missing-feedback fault logic
* Pump start command, simulated run feedback, and missing-run fault logic
* Tank high-high, high, low, and low-low indications
* Manual device-control concept for V1 testing
* ST-based analog tank-level simulation
* CODESYS Visualization HMI overview

## CODESYS Project File

The CODESYS project file is included here:

```text
codesys/ThreeTank\_WaterTransfer\_CODESYS\_V1.project
```

An additional copy with the original uploaded filename is also kept in the same folder.

## HMI / Visualization

The HMI provides a one-screen overview of the process:

* Start / Stop / Auto Mode / Fault indication
* T101, T102, T103 level bars
* Pump and valve status indications
* Filling and transfer indicators
* Tank level alarm indicators
* Basic manual operation indicators

## Structured Text Simulation

Structured Text is used to simulate the tank levels. The logic increases or decreases tank levels based on valve and pump feedback states, then clamps all levels between 0% and 100%.

!\[Structured Text Simulation](assets/screenshots/08\_structured\_text\_simulation.png)

## Screenshots

|Area|Screenshot|
|-|-|
|HMI overview|!\[HMI overview](assets/screenshots/01\_hmi\_overview.png)|
|Tank 1 sequence logic|!\[Tank 1 sequence logic](assets/screenshots/02\_tank1\_sequence\_logic.png)|
|Tank 1 valve/feedback/fault logic|!\[Tank 1 valve logic](assets/screenshots/03\_tank1\_valve\_feedback\_alarm\_logic.png)|
|Tank 2 transfer permissive logic|!\[Tank 2 transfer logic](assets/screenshots/04\_tank2\_transfer\_permissive\_logic.png)|
|Tank 2 valve/pump feedback logic|!\[Tank 2 feedback logic](assets/screenshots/05\_tank2\_valve\_pump\_feedback\_logic.png)|
|Tank 3 transfer permissive logic|!\[Tank 3 transfer logic](assets/screenshots/06\_tank3\_transfer\_permissive\_logic.png)|
|Tank 3 pump/fault logic|!\[Tank 3 pump fault logic](assets/screenshots/07\_tank3\_pump\_fault\_logic.png)|

## Demo Video

is in the Fotos / Video File
```

Recommended demo structure:

1. Start the system from the HMI.
2. Show T101 filling.
3. Show transfer from T101 to T102.
4. Show transfer from T102 to T103.
5. Show the final complete state.
6. Trigger one fault and show reset behavior.
7. Show one manual operation example.

## Repository Structure

```text
ThreeTank\_CODESYS\_Portfolio/
├── README.md
├── codesys/
│   ├── ThreeTank\_WaterTransfer\_CODESYS\_V1.project
│   └── WaterTank\_V1\_Maneul\_original\_filename.project
├── assets/
│   ├── screenshots/
│   └── video/
├── docs/
│   ├── Project\_Report.md
│   ├── FAT\_Test\_Plan.md
│   ├── IO\_and\_Tag\_List.md
│   ├── Demo\_Video\_Script.md
│   ├── Portfolio\_Checklist.md
│   └── CV\_LinkedIn\_Text.md
└── LICENSE
```

## Documentation

* [Project Report](docs/Project_Report.md)
* [FAT Test Plan](docs/FAT_Test_Plan.md)
* [I/O and Tag List](docs/IO_and_Tag_List.md)
* [Demo Video Script](docs/Demo_Video_Script.md)
* [Portfolio Checklist](docs/Portfolio_Checklist.md)
* [CV / LinkedIn Text](docs/CV_LinkedIn_Text.md)

## Limitations and Future Improvements

This is a V1 simulation project. Planned improvements:

* Record and add demo video evidence
* Add completed FAT results with screenshots
* Standardize manual mode further using AutoCmd / ManualCmd / FinalCmd variables
* Improve HMI with a clearer process diagram, alarm banner, and current step text
* Add reusable function blocks for pumps, valves, tanks, and alarms
* Rebuild/polish the project in Siemens TIA Portal / WinCC using the trial version
* Add EPLAN-style electrical documentation and formal I/O mapping

## What This Project Demonstrates

* PLC sequence design
* Ladder Diagram programming
* Structured Text simulation
* Process permissives and interlocks
* Pump/valve command-feedback logic
* Fault detection and reset handling
* HMI visualization
* Practical automation-system thinking

\---

**Project by:** Mohammad Hamdan  
**Focus:** PLC programming, CODESYS, automation engineering, industrial control logic

