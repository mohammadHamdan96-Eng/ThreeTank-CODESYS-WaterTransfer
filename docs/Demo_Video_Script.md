# Demo Video Script - Three-Tank Water Transfer System V1

Recommended video length: 1-2 minutes.

## Opening

"This is a CODESYS PLC/HMI V1 simulation of a three-tank water-transfer system. It was built using Ladder Diagram for the main logic and Structured Text for level simulation."

## Scene 1 - HMI overview

Show the CODESYS HMI and say:

"The HMI shows the three tank levels, valve and pump status, mode indicators, alarm indicators, and the main process states."

## Scene 2 - Automatic start

Press Start and show the sequence moving from idle/precheck to filling.

Say:

"The automatic mode starts with a delay/precheck and then opens XV101 to fill Tank 101."

## Scene 3 - T101 filling

Show T101 level increasing.

Say:

"The T101 analog level is simulated in Structured Text and limited between zero and one hundred percent."

## Scene 4 - Transfer T101 to T102

Show XV102/P101 active and T102 increasing.

Say:

"After T101 reaches the fill setpoint, the system opens XV102 and starts P101 to transfer water to Tank 102."

## Scene 5 - Transfer T102 to T103

Show XV103/P102 active and T103 increasing.

Say:

"The second transfer stage uses XV103 and P102 to move water from T102 to T103."

## Scene 6 - Fault/reset example

Trigger or explain one fault.

Say:

"The system includes feedback monitoring. If a valve or pump command is active but feedback is missing, a fault is generated and the sequence moves to S90. The reset command returns the system to idle after the fault cause is cleared."

## Closing

"This V1 project demonstrates PLC sequence logic, device interlocks, feedback simulation, alarms, manual operation, and HMI visualization in CODESYS. Future improvements include a Siemens TIA Portal / WinCC version, reusable function blocks, alarm history, and extended FAT documentation."
