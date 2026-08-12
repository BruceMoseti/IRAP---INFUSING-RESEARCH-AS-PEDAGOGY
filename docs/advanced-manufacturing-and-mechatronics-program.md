# Advanced Manufacturing and Mechatronics Training Program — NJIT Makerspace

A record of the Pre-Apprenticeship Skills Training Program in Advanced Manufacturing and
Mechatronics that I completed at the NJIT Makerspace, including the full curriculum and the
capability each block builds.

- **Provider:** NJIT Makerspace, New Jersey Institute of Technology, Newark, NJ ([program page](https://www.njitmakerspace.com/advanced-manufacturing-and-mechatronics-training-program))
- **Program:** Pre-Apprenticeship Skills Training Program in Advanced Manufacturing and Mechatronics
- **Format:** In person, one cycle of roughly four months across 14+ weeks, two sequential modules (Introductory, then Advanced), lecture integrated with lab
- **Program contact:** Dr. Ashish Borgaonkar
- **Credential:** Official NJIT Certificate of Completion for participants who attend the sessions and complete a course successfully
- **Requirements:** Minimum 85% session attendance and all assignments completed; training is free to admitted participants, and eligible students may receive a stipend of up to $500 on successful completion
- **Capstone:** [Sensor-driven automated irrigation testbed](projects/automated-plant-irrigation-system.md)

Trainees are recruited for a full cycle rather than for individual modules, so the two
modules below are a single continuous body of work: the Advanced module deliberately reuses
every tool, wiring practice, and PLC technique from the Introductory module inside one
course-long project.

## Who the program is for

- Individuals seeking or already working as technical/engineering staff in manufacturing-related fields
- Individuals working in technical areas, especially electrical and mechanical engineering, who want to branch into manufacturing careers
- Current or prospective Engineering or Engineering Technology students at community colleges or universities

## Module 1 — Introductory Training

Foundational lectures and laboratories on each topic. Safety instruction is part of every
session, not a separate unit.

| Week | Topic | Session content | Capability it builds |
| --- | --- | --- | --- |
| 1 | Introduction and overview of the session | Enrollment and paperwork confirmation, session locations, learning-management-system access and parking, introductions to the instructional team, session coordinators, and support staff, topic breakdown, plus career development and safety | Orientation to the shop, the safety expectations, and the arc of the cycle |
| 1 | Mechanical hand tools, hardware, and materials | Screwdrivers, shears, hammers, saws, and wrenches, each demonstrated against the hardware and materials it is meant for, with safety instruction | Selecting the right tool and fastener for a material instead of forcing the one in hand |
| 2 | Mechanical measurement tools | Tape measures, scales and rulers, squares, thread gauges, and calipers, with safety instruction | Dimensional measurement, squareness checks, and thread identification to a usable tolerance |
| 3 | Mechanical power tools | Drills, drivers, and power saws, with the hardware and materials appropriate to each, with safety instruction | Confident, controlled power-tool work: speed, feed, clamping, and bit/blade selection |
| 3 | Mechanical hand finishing tools | Files, sandpaper, steel wool, nylon mesh, abrasive pads, and painting, with safety instruction | Deburring, surface prep, and protective finishing by hand |
| 3 | Mechanical power finishing tools | Power grinding, sanding, and buffing, using both attachment-driven tools (drill, Dremel) and dedicated units, with safety instruction | Faster material removal and finishing without overheating or gouging the workpiece |
| 4 | Fundamentals of AC and DC wiring, hardware, and materials | Typical wire gauge, plugs, batteries, junction boxes, breakers, and grounding, focused on identifying components and knowing when each is used, with safety instruction | Reading a power path end to end and choosing conductors, protection, and grounding correctly |
| 5 | Electrical hand and measurement tools | Strippers, lineman's pliers, and electrical testers, with safety instruction | Clean strips and terminations, and verifying a circuit with a meter/tester rather than assuming |
| 6 | Pneumatic systems | Regulators, filters, flow control valves, tubing and fittings, and cylinders, with safety instruction | Plumbing and tuning a pneumatic circuit, and controlling actuator speed and force |
| 7 | Basic mechatronics: PLC anatomy and programming basics | PLC anatomy, analog and digital I/O ports, and memory access, plus the basics of ladder-logic programming | Wiring field devices to a PLC and reading/writing a first ladder program |
| 7 | Basic mechatronics: programming basics | Further ladder-logic technique including AND/OR logic and analog measures, and how ladder logic maps to real-world scenarios | Translating a written sequence of operations into working rungs |
| 7 | Basic mechatronics: ladder logic applications | Additional ladder-logic technique applied to real-world scenarios | Solving an actual machine-control problem rather than a textbook exercise |
| 8 | Introductory module review and catch-up | Mandatory session for anyone needing to make up a missed session; opportunity to revisit any topic | Consolidation before the Advanced module raises the stakes |

## Module 2 — Advanced Training: fundamentals of mechanical and electrical assembly, maintenance, and repair

The Advanced module builds directly on the Introductory module by integrating its topics
into hands-on sessions and a course-long project that trainees fabricate and assemble.
Completion of the Introductory course is a prerequisite.

| Week | Topic | Session content | Capability it builds |
| --- | --- | --- | --- |
| 9 | Mechanical assembly | Reading assembly instructions, organizing a bill of materials, preparing tools and hardware, mechanical assembly, and post-assembly measurement, with safety instruction | Working from documentation to a correctly built, verified assembly |
| 10 | Electrical assembly | Reading assembly instructions, organizing a bill of materials, preparing tools and hardware, electrical assembly, and post-assembly measurement, with safety instruction | Building a wiring harness or panel that is documented, labeled, and measured before power-up |
| 11 | Basic mechanical equipment troubleshooting | Checking whether an assembly is aligned and balanced, whether the correct hardware was used, and identifying damaged material and corrosion, with safety instruction | Diagnosing a mechanical fault by inspection and measurement instead of by replacement |
| 11 | Basic mechanical equipment maintenance and repair | Removing damaged hardware, cleaning, lubrication, and sanding and painting, with safety instruction | Returning equipment to service and preventing the next failure |
| 12 | Basic electrical equipment troubleshooting, maintenance, and repair | Assessing breaker, fuse, battery, and power switch/plug condition, then resetting a breaker and replacing a fuse, with safety instruction | Safely isolating and clearing common electrical faults |
| 13 | Advanced mechatronics: PLC programming | Event sequencing and continuous operation, plus basic mathematical functions, logic expressions, counters, and timers | Writing control code that runs indefinitely and sequences real events on a clock |
| 14 | Advanced mechatronics: sensors and actuators, testing and troubleshooting | Hands-on work with industrial actuators (electrical motors, pneumatic devices, grippers, relays) and proximity sensors (ultrasonic, magnetic, optical), plus testing and troubleshooting procedures | Choosing, wiring, and verifying the sensor/actuator pair a job actually needs |
| 14 | Advanced mechatronics: real-world industrial applications | Hands-on stepper and servo motor control, and real-world mechatronics applications including conveyors, robotics, and automated production lines | Seeing the same control patterns scale from a bench rig to a production line |

## How the capstone used the curriculum

The course-long project I built — a closed-loop irrigation testbed that waters four planted
pots from soil-moisture feedback — pulled the modules together as follows:

| From the curriculum | How it showed up in the build |
| --- | --- |
| Hand, power, measurement, and finishing tools | Fabricating and fitting the frame, sensor stakes, and tubing routing; measuring for repeatable sensor placement across pots |
| AC/DC wiring fundamentals | Powering the controller and pump safely, sizing conductors, and grounding a rig that sits in standing water |
| Electrical hand and measurement tools | Stripping and terminating every sensor and actuator lead, then verifying continuity and supply rails with a meter before power-up |
| Pneumatics and fluid handling | Tubing, fittings, and flow control transferred directly to routing the water delivery lines and balancing flow between pots |
| PLC anatomy, I/O, and ladder logic | Reading the moisture sensors on input, driving the pump/valve on output, and expressing the watering rules as rungs |
| Advanced PLC: timers, counters, sequencing, continuous operation | Watering pulses with fixed dose time, lockout intervals so soil can equilibrate before re-reading, and unattended continuous operation for the length of the study |
| Sensors and actuators | Soil-moisture probe conditioning and calibration, and pump/valve control through relay outputs |
| Troubleshooting, maintenance, and repair | Chasing real faults during the run: drift and noisy readings, uneven flow between delivery lines, and connections that had to be re-terminated |

Details, decisions, and photographed results are in the
[project write-up](projects/automated-plant-irrigation-system.md).
