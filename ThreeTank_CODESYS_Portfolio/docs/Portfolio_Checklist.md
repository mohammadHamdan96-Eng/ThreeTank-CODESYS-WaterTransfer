# Portfolio Checklist and Harsh Review

## Current Rating

| Evaluation Area | Rating |
|---|---:|
| CODESYS learning project | 8.5 / 10 |
| GitHub junior automation portfolio project | 8.0 / 10 |
| Job-application supporting project | 8.2 / 10 |
| Industrial/professional automation package | 5.0 / 10 |

## Why the Portfolio Rating Improved

The actual CODESYS project file is now included in the repository. This removes the biggest credibility gap from the first version.

## Strong Points

- Real CODESYS project file included
- Step sequence from S0 to S70 plus S90 fault state
- LD and ST used appropriately
- Valve command, feedback, fault, and alarm logic
- Pump command, run feedback, fault, and alarm logic
- ST tank level simulation
- HMI overview screen
- Manual operation concept included
- FAT test plan and I/O tag list included

## Remaining Weaknesses

- Demo video still missing
- FAT results are prepared but not yet proven with screenshots/video
- Manual mode is acceptable for V1 but not fully standardized
- HMI is functional, not yet industrial-looking
- No reusable valve/pump/tank function blocks yet
- Not yet rebuilt in Siemens TIA Portal / WinCC

## Highest-Impact Next Steps

1. Record a 1-2 minute demo video and add the link to README.md.
2. Run the FAT checklist and change important tests from PENDING EVIDENCE to PASS.
3. Add screenshots or video timestamps for fault/reset tests.
4. Later: rebuild in TIA Portal / WinCC for Siemens-focused applications.

## Public Presentation Recommendation

Present this project as:

```text
Three-Tank Water Transfer System - CODESYS PLC/HMI V1 Simulation
```

Do not present it as a final industrial commissioning project. Present it as a functional V1 automation portfolio project that demonstrates PLC logic, sequence control, HMI visualization, alarms, fault handling, and simulation.
