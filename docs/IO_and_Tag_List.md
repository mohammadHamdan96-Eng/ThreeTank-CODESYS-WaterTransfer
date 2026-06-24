# I/O and Tag List - Three-Tank Water Transfer System V1

This signal list describes the main CODESYS V1 simulation tags. The project is a simulation, so many signals represent simulated digital inputs, feedbacks, and internal control bits rather than physical wired I/O.

## Main Control Tags

| Tag | Type | Direction | Description |
|---|---|---|---|
| Start | BOOL | HMI/Input | Operator start command |
| Stop | BOOL | HMI/Input | Operator stop command |
| Emergency | BOOL | HMI/Input | Emergency input / emergency simulation |
| Reset | BOOL | HMI/Input | Fault reset command |
| System_enable | BOOL | Internal | Main system enable bit |
| Auto_mode | BOOL | Internal/HMI | Automatic mode active |
| SequenceStep | INT | Internal/HMI | Main sequence state number |
| Fault_Led | BOOL | HMI Output | Fault indicator |

## Tank Level Tags

| Tag | Type | Direction | Description |
|---|---|---|---|
| T101_lvl | REAL | Internal/HMI | Simulated Tank 101 level in percent |
| T102_lvl | REAL | Internal/HMI | Simulated Tank 102 level in percent |
| T103_lvl | REAL | Internal/HMI | Simulated Tank 103 level in percent |
| Fillstop | REAL | Internal | T101 fill stop setpoint |
| T102_Fillstop | REAL | Internal | T102 fill stop setpoint |
| T103_Fillstop | REAL | Internal | T103 fill stop setpoint |

## Tank 101 / Inlet Filling

| Tag | Type | Direction | Description |
|---|---|---|---|
| XV101_opencmd | BOOL | Output/Internal | Command to open inlet valve XV101 |
| XV101_openFB | BOOL | Simulated DI | Simulated open feedback for XV101 |
| XV101_CloseFB | BOOL | Simulated DI | Simulated closed feedback for XV101 |
| XV101_Fault | BOOL | Internal/HMI | Fault if XV101 command active but feedback missing |
| T101_InitialFillReq | BOOL | Internal | Automatic fill request during S20 |
| T101_RefillReq | BOOL | Internal | Refill request during transfer stage |
| LSHH_101 | BOOL | Simulated DI | Tank 101 high-high level |
| LSH_101 | BOOL | Simulated DI | Tank 101 high level |
| LSL_101 | BOOL | Simulated DI | Tank 101 low level |
| LSLL_101 | BOOL | Simulated DI | Tank 101 low-low level |
| ALM_T101_HH | BOOL | HMI/Internal | Tank 101 high-high alarm |
| ALM_T101_H | BOOL | HMI/Internal | Tank 101 high alarm |
| ALM_T101_L | BOOL | HMI/Internal | Tank 101 low alarm |
| ALM_T101_LL | BOOL | HMI/Internal | Tank 101 low-low alarm |

## Tank 102 / Transfer T101 to T102

| Tag | Type | Direction | Description |
|---|---|---|---|
| XV102_opencmd | BOOL | Output/Internal | Command to open transfer valve XV102 |
| XV102_OpenFB | BOOL | Simulated DI | Simulated open feedback for XV102 |
| XV102_Fault | BOOL | Internal/HMI | Fault if XV102 command active but feedback missing |
| XV102_StartPermissive | BOOL | Internal | Auto permissive for starting transfer to T102 |
| XV102_RefillPermissive | BOOL | Internal | Auto permissive for refill/continued transfer logic |
| P101_StartCmd | BOOL | Output/Internal | Command to start pump P101 |
| P101_Run | BOOL | Simulated DI | Simulated run feedback for P101 |
| P101_Ready | BOOL | Internal/HMI | P101 available/ready condition |
| P101_Overload | BOOL | Simulated DI | Pump P101 overload input / simulation |
| P101_Fault | BOOL | Internal/HMI | Fault if P101 command active but run feedback missing |
| LSHH_102 | BOOL | Simulated DI | Tank 102 high-high level |
| LSH_102 | BOOL | Simulated DI | Tank 102 high level |
| LSL_102 | BOOL | Simulated DI | Tank 102 low level |
| LSLL_102 | BOOL | Simulated DI | Tank 102 low-low level |
| ALM_T102_HH | BOOL | HMI/Internal | Tank 102 high-high alarm |
| ALM_T102_H | BOOL | HMI/Internal | Tank 102 high alarm |
| ALM_T102_L | BOOL | HMI/Internal | Tank 102 low alarm |
| ALM_T102_LL | BOOL | HMI/Internal | Tank 102 low-low alarm |

## Tank 103 / Transfer T102 to T103

| Tag | Type | Direction | Description |
|---|---|---|---|
| XV103_opencmd | BOOL | Output/Internal | Command to open transfer valve XV103 |
| XV103_OpenFB | BOOL | Simulated DI | Simulated open feedback for XV103 |
| XV103_Fault | BOOL | Internal/HMI | Fault if XV103 command active but feedback missing |
| XV103_StartPermissive | BOOL | Internal | Auto permissive for starting transfer to T103 |
| P102_StartCmd | BOOL | Output/Internal | Command to start pump P102 |
| P102_Run | BOOL | Simulated DI | Simulated run feedback for P102 |
| P102_Ready | BOOL | Internal/HMI | P102 available/ready condition |
| P102_Overload | BOOL | Simulated DI | Pump P102 overload input / simulation |
| P102_Fault | BOOL | Internal/HMI | Fault if P102 command active but run feedback missing |
| LSHH_103 | BOOL | Simulated DI | Tank 103 high-high level |
| LSH_103 | BOOL | Simulated DI | Tank 103 high level |
| LSL_103 | BOOL | Simulated DI | Tank 103 low level |
| LSLL_103 | BOOL | Simulated DI | Tank 103 low-low level |
| ALM_T103_HH | BOOL | HMI/Internal | Tank 103 high-high alarm |
| ALM_T103_H | BOOL | HMI/Internal | Tank 103 high alarm |
| ALM_T103_L | BOOL | HMI/Internal | Tank 103 low alarm |
| ALM_T103_LL | BOOL | HMI/Internal | Tank 103 low-low alarm |

## Manual Mode Tags

| Tag | Type | Direction | Description |
|---|---|---|---|
| MAN_T1_Fillstop | BOOL | HMI/Input | Manual / idle setpoint preparation for T1 |
| MAN_T2 | BOOL | HMI/Input | Manual / idle setpoint preparation for T2 |
| MAN_T3 | BOOL | HMI/Input | Manual / idle setpoint preparation for T3 |
| MAN_XV101_OpenCmd | BOOL | HMI/Input | Manual command request for XV101 |
| MAN_XV102_FILL | BOOL | Internal/HMI | Manual command/permissive for XV102 |
| MAN_P101_READY | BOOL | Internal/HMI | Manual P101 ready permissive |
| MAN_P102_Ready | BOOL | Internal/HMI | Manual P102 ready permissive |
| MAN_P102_Run | BOOL | HMI/Input | Manual P102 start request |

## Sequence Step Reference

| Step | Meaning |
|---:|---|
| 0 | Idle |
| 10 | Precheck |
| 20 | Fill T101 |
| 30 | T101 Ready |
| 40 | Transfer T101 to T102 |
| 50 | T102 Ready |
| 60 | Transfer T102 to T103 |
| 70 | Complete |
| 90 | Fault |
