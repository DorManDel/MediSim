# MedSim Toolkit — Verification Matrix

A test record should include `pattern_id`, date/time, `SimDesigner` version, `LLEAP` version, patient monitor version, mannequin/simulator model, import location, setup, expected behavior, actual behavior, verdict, screenshots/log files, and responsible tester.

| ID | Pattern | Action | Pass condition | Status |
|---|---|---|---|---|
| T01 | NIBP | Trigger `Measure BP` once | Auto then Manual after configured 2 s, desired NIBP behavior | To verify on target |
| T02 | NIBP | Trigger rapidly twice | No overlapping or stuck mode | To verify |
| T03 | Core | Connect Monitoring | NIBP, ECG 3-lead, SpO₂ connected | To verify |
| T04 | Core | Detach all twice | All expected leads detached with no adverse side effects | To verify |
| T05 | Handler reuse | Save `.hnx`, load into another `.scx` | Same aliases, responses, delays and dependencies; no unexpected duplicate events | To verify |
| T06 | Two handlers | Both active, one stopped | No duplicate reaction or unintentionally stopped utilities | To verify |
| T07 | Soft reset | Detach + pause/silence | Clear station display; old alarms do not unexpectedly recur mid-intro | To verify |
| T08 | Soft reset | During active media | Audio is actually stopped using validated control, not only Hidden | To verify |
| T09 | PEA | Move PEA → No PEA explicitly | Intended pulse and vital signs visible and simulated | To verify |
| T10 | PEA | PEA → No change negative test | Detect/record undesired inheritance if present | To verify |
| T11 | Navigation | Change Phase | Correct state and event availability, old handlers/trends lifecycle checked | To verify |
| T12 | Restart | Restart twice | Correct patient baseline and timer/counter state | To verify |
| T13 | Timer | Run for two cycles | Milestones fire expected number of times without log flooding | To verify |
| T14 | Preset | Change BP relative to current | Parameterization and min/max verified or rejected as unsupported | To verify |
| T15 | Media | Play WAV once, then stop | Playback and stop behave as documented on target monitor | To verify |
| T16 | Instructor UX | Single operator completes scenario | Task completion, errors and workload recorded for comparison | To measure |

**Release rules:** Any PEA or physiologic transition needs explicit review; failure to restore the target state blocks release. Every native `.hnx/.phx/.scx` must be generated and saved in SimDesigner, not produced by renaming text files. The interactive website does not satisfy any native test above.