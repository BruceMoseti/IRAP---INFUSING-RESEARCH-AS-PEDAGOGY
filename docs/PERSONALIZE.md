# Before you share this repo — checklist

Working note for the author. **Delete this file once you have worked through it**; it is not
meant for recruiters.

The program pages are taken straight from the NJIT Makerspace course description, so those are
accurate. The capstone write-up was reconstructed from the project photos and from what the
curriculum covers, which means the *structure* is right but a few specifics need your real
numbers and names. Fix these and the write-up becomes airtight:

## Must do

- [ ] Add the five project photos to `images/` with the filenames listed in
      [`images/README.md`](../images/README.md), then paste the gallery markdown from that same
      page back into the README and the project write-up. The write-ups currently describe the
      run in words only, so the photos are the single biggest improvement available.
- [ ] Confirm the cycle you completed and its dates, and put them at the top of
      [`docs/advanced-manufacturing-and-mechatronics-program.md`](advanced-manufacturing-and-mechatronics-program.md).
- [ ] State whether the capstone was individual or a team build, and if it was a team, say what
      *you* owned. Recruiters ask this first.
- [ ] Replace hardware descriptions with the actual parts in
      [`docs/projects/automated-plant-irrigation-system.md`](projects/automated-plant-irrigation-system.md):
      controller/PLC model, soil-moisture probe model, pump or valve type, reservoir, and tubing size.
- [ ] Check the control-logic sketch against what you actually programmed and correct any rung
      that differs. Do not leave logic in there that you cannot walk through in an interview.
- [ ] Fill in the real parameter values you used: dry setpoint, dose time, lockout interval, and
      the per-interval dose cap. Concrete numbers are far more convincing than "a fixed dose."
- [ ] Name the species you planted and the sowing date, and say how long the run lasted.
- [ ] Remove the author-note HTML comment at the top of the project write-up.

## Worth doing

- [ ] Any measured data you kept — moisture logs, watering counts, germination counts, heights.
      Even a small table beats photos alone.
- [ ] A photo of the controller, wiring, and reservoir, and one of the ladder-logic program.
- [ ] The certificate of completion, if you are comfortable posting it.
- [ ] Your instructors' names, if they agreed to be referenced.
- [ ] Cross-check the "what broke" table against the faults you actually chased, and swap in the
      real ones. Genuine failure stories are the strongest part of a portfolio.
