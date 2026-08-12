# Skills matrix

Every skill below was taught in a lab session of the NJIT Makerspace Advanced Manufacturing and
Mechatronics program and then used on the
[capstone irrigation testbed](projects/automated-plant-irrigation-system.md). The right-hand
column says where it was actually applied, not just covered.

## Mechanical

| Skill | Where it came from | Where I applied it |
| --- | --- | --- |
| Hand tools: screwdrivers, wrenches, hammers, saws, shears | Introductory, week 1 | Frame and mount fabrication, sensor stakes, fastening the rig so nothing shifted mid-run |
| Fastener and material selection | Introductory, week 1 | Choosing hardware that survives a wet environment without loosening or corroding |
| Dimensional measurement: calipers, squares, scales, tape, thread gauges | Introductory, week 2 | Repeatable sensor insertion depth and emitter height across all four pots — the basis of comparable channels |
| Power tools: drills, drivers, power saws | Introductory, week 3 | Drilling and cutting mounts and tubing pass-throughs |
| Hand and power finishing: files, abrasives, grinding, sanding, buffing, painting | Introductory, week 3 | Deburring cut edges so tubing and wiring were not chafed, and protecting bare surfaces near water |
| Mechanical assembly from documentation and a BOM | Advanced, week 9 | Building the rig from a parts list and verifying dimensions after assembly |
| Mechanical troubleshooting: alignment, balance, correct hardware, damage and corrosion | Advanced, week 11 | Diagnosing uneven flow and shifted sensor placement between pots |
| Maintenance and repair: hardware removal, cleaning, lubrication, refinishing | Advanced, week 11 | Keeping a rig that lives in standing water serviceable for the full run |

## Electrical

| Skill | Where it came from | Where I applied it |
| --- | --- | --- |
| AC and DC wiring fundamentals: gauge, plugs, batteries, junction boxes, breakers, grounding | Introductory, week 4 | Powering controller and pump safely with water present, and grounding the rig properly |
| Electrical hand tools: strippers, lineman's pliers | Introductory, week 5 | Every sensor and actuator termination in the harness |
| Electrical measurement and testers | Introductory, week 5 | Continuity and rail verification before first power-up, and fault isolation during the run |
| Electrical assembly from documentation and a BOM | Advanced, week 10 | Building, labeling, and measuring the harness before energizing it |
| Electrical troubleshooting: breakers, fuses, batteries, switches and plugs | Advanced, week 12 | Isolating intermittent connections and confirming supply integrity |
| Maintenance and repair: resetting breakers, replacing fuses | Advanced, week 12 | Safe recovery from a tripped supply without guessing |

## Controls and mechatronics

| Skill | Where it came from | Where I applied it |
| --- | --- | --- |
| PLC anatomy, digital and analog I/O, memory access | Introductory, week 7 | Wiring four analog moisture inputs and a relay output for the pump/valve |
| Ladder-logic programming, including AND/OR logic and analog measures | Introductory, week 7 | Expressing the watering rule as rungs instead of as a script |
| Event sequencing and continuous operation | Advanced, week 13 | One-channel-at-a-time dosing and an unattended loop that ran for the whole study |
| Timers, counters, and logic/math functions | Advanced, week 13 | Dose timing, post-dose lockout, and the per-interval dose cap that inhibits a suspect channel |
| Sensors: proximity (ultrasonic, magnetic, optical) and analog measurement | Advanced, week 14 | Soil-moisture probe conditioning, placement, filtering, and setpoint comparison |
| Actuators: motors, pneumatic devices, grippers, relays | Advanced, week 14 | Relay-driven pump/valve control with bounded energize time |
| Stepper and servo motor control | Advanced, week 14 | Lab exercises; the pattern carries directly to metered dosing and conveyor-style sequencing |
| Testing and troubleshooting procedures | Advanced, weeks 11, 12, 14 | Every fault in the [what broke](projects/automated-plant-irrigation-system.md#what-broke-and-what-i-did-about-it) table |

## Fluid and pneumatic systems

| Skill | Where it came from | Where I applied it |
| --- | --- | --- |
| Regulators, filters, flow control valves | Introductory, week 6 | Understanding and balancing delivered flow per channel |
| Tubing, fittings, and leak-free routing | Introductory, week 6 | Reservoir-to-pot delivery lines routed so they neither kink nor drip where they should not |
| Cylinders and actuator control | Introductory, week 6 | Lab exercises in bounded, controlled actuation |

## Engineering practice

| Skill | Evidence |
| --- | --- |
| Working safely by default | Safety was taught in every session of both modules; the capstone combined water, mains-derived power, and a shared public space, and ran the full study without incident |
| Reading and following documentation | Assembly instructions and BOM organization in both the mechanical and electrical assembly sessions |
| Experiment design with controlled replicates | Four identically instrumented pots, controlled light, soil, sowing, and dose parameters |
| Systematic fault isolation | Diagnosing sensor-contact, interference, and flow-split faults by measurement instead of by swapping parts |
| Technical documentation | This repository — a build that someone else could reproduce from the write-up |
| Unattended reliability engineering | Interlocks, bounded doses, and self-inhibit logic so a single bad reading cannot ruin the run |
