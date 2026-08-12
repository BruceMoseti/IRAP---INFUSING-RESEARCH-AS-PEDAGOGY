# IRAP — Infusing Research as Pedagogy

Portfolio and documentation for my work in NJIT's *Infusing Research as Pedagogy* (IRAP)
effort, centered on the **Advanced Manufacturing and Mechatronics Pre-Apprenticeship Skills
Training Program** run by the [NJIT Makerspace](https://www.njitmakerspace.com/) and the
hands-on research project I built as part of it.

If you are a recruiter or hiring manager, the pages below are the fastest way to see what I
can do:

| Page | What it shows |
| --- | --- |
| [Capstone project: sensor-driven automated irrigation testbed](docs/projects/automated-plant-irrigation-system.md) | A working mechatronic system I wired, programmed, and ran as a multi-week experiment — with photos of the results |
| [Training program record](docs/advanced-manufacturing-and-mechatronics-program.md) | The full 14-week curriculum I completed, week by week, and what I actually did in each block |
| [Skills matrix](docs/skills.md) | Every skill mapped to where I demonstrated it |

---

## Summary

Over a ~4-month cycle of the NJIT Makerspace Pre-Apprenticeship program in Advanced
Manufacturing and Mechatronics, I moved from shop fundamentals (hand, power, measurement,
and finishing tools; AC/DC wiring; electrical test instruments) through industrial controls
(PLC anatomy, I/O, ladder-logic programming, sensors, actuators, pneumatics) and finished
with a course-long build: a **closed-loop, PLC-controlled irrigation testbed** that keeps
four planted pots watered from soil-moisture feedback while a growth study runs on top of it.

That project is where the IRAP idea shows up in practice — the automation is not the end
goal, it is the instrument. The rig had to be reliable enough that the plant-growth data it
produced meant something, which is a very different engineering bar than "the pump turns on."

**What I bring out of it**

- Reading a build to completion: bill of materials, assembly, wiring, bring-up, and
  troubleshooting on hardware I had to keep running unattended for weeks.
- Industrial controls literacy: ladder logic with timers, counters, and logic/math blocks;
  digital and analog I/O; sensor conditioning; actuator and relay control.
- Electromechanical assembly and repair: correct hardware selection, alignment and balance
  checks, wire termination, fault isolation on both mechanical and electrical failures.
- Experiment discipline: controlled conditions, identical treatment across replicates,
  scheduled observation, and documentation good enough for someone else to reproduce.
- Safety as a default, not an afterthought — every module in the program was taught with it
  and the rig ran water and mains-derived power next to live electronics.

## Results at a glance

Same rig, same four pots, observed across the run: bare instrumented soil at sowing, then
sprouts up in every pot, then open cotyledons across all four replicates, and finally dense
stands of leafed-out seedlings — every drop of it delivered by the control loop, with no pot
lost to overwatering or to drying out and no manual watering at any point.

<!--
  Photo gallery: the five project photos go in images/ with the filenames listed in
  images/README.md, which also has the markdown to paste back in here and in the project
  write-up once the files exist.
-->

The run in detail, stage by stage, is in the
[project write-up](docs/projects/automated-plant-irrigation-system.md#results).

## Repository map

```
README.md                                              this page
docs/
  advanced-manufacturing-and-mechatronics-program.md   the curriculum I completed, week by week
  skills.md                                            skills matrix with evidence
  projects/
    automated-plant-irrigation-system.md               capstone project write-up
images/                                                where the project photos go (see images/README.md)
```

## About the program

The NJIT Makerspace Pre-Apprenticeship Skills Training Program in Advanced Manufacturing and
Mechatronics runs in cycles of roughly four months, in two modules that must be taken in
order:

- **Introductory Training Module** — integrated lectures and labs on power, hand,
  measurement, and finishing tools; AC and DC wiring; electrical measurement tools;
  pneumatics; and PLC basics (anatomy, wiring, I/O, and ladder-logic programming).
- **Advanced Training Module** — the introductory topics folded into a course-long project
  that trainees fabricate and assemble, plus mechanical and electrical assembly,
  maintenance, repair, troubleshooting, sensors, actuators, and advanced testing.

Trainees are enrolled for a full cycle rather than individual modules, are expected to
attend at least 85% of sessions and complete all assignments, and receive an official NJIT
Certificate of Completion. Program contact: Dr. Ashish Borgaonkar. Cycles 4 and 5 (roughly
mid-August through mid-December 2026) were accepting applications on a rolling basis at the
time of writing — see the
[program page](https://www.njitmakerspace.com/advanced-manufacturing-and-mechatronics-training-program)
for current details.

A full week-by-week breakdown of both modules is in
[docs/advanced-manufacturing-and-mechatronics-program.md](docs/advanced-manufacturing-and-mechatronics-program.md).
