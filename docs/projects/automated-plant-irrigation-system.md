# Capstone project: sensor-driven automated irrigation testbed

**Built during:** Advanced Training Module, NJIT Makerspace Pre-Apprenticeship Skills Training
Program in Advanced Manufacturing and Mechatronics
([program record](../advanced-manufacturing-and-mechatronics-program.md))
**Type:** Course-long mechatronics build used as a research instrument
**Outcome:** Ran unattended for the length of a multi-week germination-to-seedling study and
watered every pot on sensor feedback alone

<!--
  AUTHOR NOTE (not rendered on GitHub): fill in the specifics only you know —
  cycle number and dates, teammates and your specific role, PLC/controller model,
  soil-moisture probe model, pump/valve type, the actual moisture setpoint and dose
  and lockout times, the species planted, and any measured growth data.
  Then delete this comment. See ../PERSONALIZE.md for the full checklist.
-->

---

## What it is

Four planted pots on a single tray by a south-facing window. Each pot has a soil-moisture
probe staked next to the seed line and its own water delivery line. A controller reads the
probes, decides when a pot is dry, and pulses water into just that pot — then waits for the
soil to equilibrate before it trusts the sensor again. No one waters anything by hand.

The taped sign in every photo reads *"please do not touch or move — research project."* That
sign is the whole point of the build: the rig lived in a shared space and had to keep running
correctly without supervision, because the plants were the measurement and any manual
intervention would have contaminated the data.

## Why it was worth building

The obvious version of this project is "pump turns on when soil is dry," and that version is
finished in an afternoon. It is also useless as an instrument, because it does not water the
replicates *the same way*.

Everything interesting in the build came from that requirement:

- **Identical treatment across pots.** Four sensors and four delivery lines that behave the
  same, so a difference in plant growth is a difference in the thing being studied and not a
  difference in the plumbing.
- **Unattended reliability.** A rig with water in it, standing in a public corridor next to
  live electronics, that has to survive weekends without flooding the tray or drying out.
- **Trustworthy readings.** A soil-moisture probe reads whatever is happening in the few
  cubic centimeters around it — placement, contact, and timing all matter more than the sensor
  spec sheet suggests.

This is the *Infusing Research as Pedagogy* framing in one sentence: the automation is not the
deliverable, it is the apparatus, and it has to be good enough that the data it produces means
something.

## System as built

| Subsystem | Implementation | Why it was done that way |
| --- | --- | --- |
| Sensing | One soil-moisture probe per pot, staked vertically at a consistent depth beside the seed line, with each cable dressed back to a common harness | Consistent depth and distance from the emitter is what makes the four channels comparable; anything else and each pot is running a different experiment |
| Water delivery | Flexible tubing from a shared reservoir, split into one line per pot, with the emitter end fixed over the soil surface rather than left loose | Fixed emitters keep the wetted spot in the same place every dose, so the sensor sees the same wetting front each time |
| Actuation | Pump/valve control through a relay output, energized only for a bounded dose | Bounded doses mean a stuck sensor reading cannot flood a pot; the worst case is one dose too many, not a drained reservoir |
| Control | PLC-based control loop in ladder logic: read moisture, compare to a low setpoint, dose for a fixed time, then hold off before re-reading | Timers and interlocks in the control code, not in someone's head |
| Power and wiring | Controller and pump supply wired per AC/DC practice from the Introductory module — sized conductors, terminated leads, grounding, and every rail verified with a meter before first power-up | Water and mains-derived power in the same enclosure area is exactly where sloppy wiring becomes a safety incident |
| Placement | Single tray, single window, pots grouped so light and temperature exposure is as close to equal as the location allows | Controls the largest environmental variable available to control indoors |

## Control logic

The watering rule is deliberately conservative and lives entirely in the PLC program:

```
For each pot channel:

  Rung 1   Moisture reading  <  dry setpoint
           AND  lockout timer  NOT  running
           AND  channel enabled
             -->  latch WATER_REQUEST for this channel

  Rung 2   WATER_REQUEST latched
           AND  no other channel dosing        (one dose at a time)
             -->  energize pump/valve output
             -->  start DOSE timer

  Rung 3   DOSE timer done
             -->  de-energize output
             -->  unlatch WATER_REQUEST
             -->  start LOCKOUT timer
             -->  increment DOSE_COUNT for this channel

  Rung 4   DOSE_COUNT  >  per-interval maximum
             -->  inhibit channel and flag for inspection
```

Three details in there are the difference between a demo and an instrument:

1. **The lockout timer.** Water needs time to spread through the soil before a moisture
   reading means anything. Without the hold-off the loop reads "still dry" immediately after
   dosing and doses again, and again — the classic way to drown a plant with a correct sensor.
2. **One channel at a time.** Sequencing the doses instead of opening everything at once keeps
   supply pressure — and therefore the delivered volume — the same for every pot.
3. **The dose counter and inhibit.** If a channel asks for water far more often than
   physically plausible, the sensor or the line is the problem, so the program stops trusting
   that channel and flags it rather than quietly ruining a replicate.

## Experiment design

- **Replicates:** four pots, sown and instrumented identically, run simultaneously on the same
  controller and the same reservoir.
- **Controlled variables:** light exposure and ambient temperature (single tray, single
  window), soil volume and type, sowing depth, sensor depth and position, dose volume and
  timing rules.
- **Observation:** scheduled photographs of the whole tray from a consistent angle, so
  germination timing, emergence, and seedling development are directly comparable frame to
  frame across the run.
- **Protection of the run:** the rig was signed and positioned so passers-by would not adjust
  the tubing or move pots between observations.

## Results

The observation series is the result: the same four pots, watered only by the control loop,
from bare soil to a full stand of seedlings.

<!--
  Photo gallery: the five frames below were photographed. Add the image files to images/
  using the filenames in images/README.md, which also holds the gallery markdown to paste
  back into this section.
-->

| Stage | What the rig looked like |
| --- | --- |
| **Germination** | Probes, emitters, and cabling in place in all four pots before anything sprouted, so no pot had to be disturbed once the run started. Only the first sprouts breaking the surface. |
| **Emergence** | Seedlings up in every pot, each still fed by its own delivery line off the shared reservoir. |
| **Cotyledon stage** | Open cotyledons across all four replicates — the loop was holding moisture in the germination band without waterlogging it. |
| **True leaves** | Stands thickened and leaf area grew. Watering demand climbed and the sensor-driven loop tracked it with no change to the program. |
| **End of run** | Healthy, dense seedling stands, grown start to finish on automated, sensor-triggered irrigation. |

What the sequence demonstrates:

- The control loop kept every pot inside a viable moisture band continuously, through
  germination — when the surface dries fastest and a mistake kills the whole cohort — and
  through the higher demand of leafed-out seedlings.
- No pot was lost to overwatering or to drying out, which is the practical test of whether the
  lockout timing and dose sizing were right.
- The rig ran unattended in a shared space for the full study without a flood, a spill, or an
  electrical fault.

## What broke, and what I did about it

The honest part of the write-up, and the part the Advanced module's troubleshooting sessions
were actually for:

| Symptom | Cause | Fix |
| --- | --- | --- |
| One channel reading much drier than its neighbors under obviously similar soil | Probe not fully in contact with soil — an air gap along one face of the stake | Re-seated the probe and standardized insertion depth and orientation across all four pots so the channels became comparable |
| Noisy, jumping moisture values | Long unshielded sensor runs picking up interference, plus connector movement | Dressed and strapped the harness, re-terminated the suspect connections, and filtered the reading in software before comparing to the setpoint |
| Uneven wetting between pots on the same dose | Flow split unequally between the delivery lines — tubing runs of different length and routing | Rerouted and equalized the lines and balanced flow so an identical dose command delivered a comparable volume to each pot |
| A pot re-triggering almost immediately after dosing | Moisture read before water had spread through the soil | Lengthened the lockout interval and added the per-interval dose cap so a bad reading cannot cascade into repeated watering |

## What I would do next

- **Log the data, not just photographs.** Timestamped moisture readings and dose events per
  channel would turn the study from a qualitative photo series into a dataset — and would make
  sensor drift visible while the run is happening instead of afterward.
- **Calibrate each probe** against gravimetric water content so the four channels share one
  setpoint in real units instead of raw counts.
- **Add reservoir level sensing** and a low-level alarm, so an empty reservoir announces itself
  rather than being discovered by a dead plant.
- **Introduce a real treatment variable** — different setpoints per pot, for example — now
  that the apparatus is trustworthy enough to attribute a difference in growth to the treatment
  rather than to the rig.

## Skills demonstrated

Mechanical assembly and fabrication from a bill of materials · dimensional measurement and
repeatable fixturing · AC/DC wiring, termination, and grounding · meter-based verification and
electrical troubleshooting · tubing, fittings, and flow balancing · PLC I/O wiring · ladder-logic
programming with timers, counters, latches, and interlocks · analog sensor conditioning and
calibration · relay-driven actuator control · fault isolation on live hardware · experiment
design, controlled replicates, and documentation

See the [skills matrix](../skills.md) for where each of these was learned and applied.
