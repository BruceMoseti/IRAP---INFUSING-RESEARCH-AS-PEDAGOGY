# Project photos

This folder is where the five photos of the irrigation testbed go. The write-ups currently
describe the run in text only, because the image files are not in the repository yet — add them
here and then paste the gallery markdown at the bottom of this page back into the write-ups.

Use JPEG (`.jpg`). If a photo comes off an iPhone as `.HEIC`, convert it first — GitHub will
not render HEIC inline:

```bash
# macOS, built in
sips -s format jpeg IMG_1234.HEIC --out images/irrigation-rig-01-germination.jpg

# or with ImageMagick
magick IMG_1234.HEIC images/irrigation-rig-01-germination.jpg
```

## Expected files, in chronological order

| Filename | The photo to use |
| --- | --- |
| `irrigation-rig-01-germination.jpg` | Earliest frame. Mostly bare soil, only the first tiny sprouts visible; probes and delivery lines already installed in all four pots; the "research project" sign taped to the window behind the tray. |
| `irrigation-rig-02-emergence.jpg` | Sprouts visible in every pot, still small. Closer view showing the probes and the emitter ends of the delivery lines fixed above the soil. |
| `irrigation-rig-03-cotyledon-stage.jpg` | Several seedlings per pot with open cotyledons — the first frame where the stands read clearly as plants. |
| `irrigation-rig-04-true-leaves.jpg` | Denser, larger seedlings across the tray; noticeably more leaf area than the previous frame. |
| `irrigation-rig-05-final-results.jpg` | Final frame. Fullest green stands of the sequence — this is the "results" photo. |

Keep the frames in this order even if the intervals between them were uneven; the sequence is
presented as a progression, not as dated observations.

## Gallery markdown to paste in once the files are here

In `README.md`, under **Results at a glance**:

```markdown
| Start of run | Mid-run | End of run |
| --- | --- | --- |
| ![Testbed at germination, probes and delivery lines installed in four pots](images/irrigation-rig-01-germination.jpg) | ![Seedlings at cotyledon stage under automated watering](images/irrigation-rig-03-cotyledon-stage.jpg) | ![Full stand of seedlings at the end of the run](images/irrigation-rig-05-final-results.jpg) |
```

In `docs/projects/automated-plant-irrigation-system.md`, replacing the stage table in the
**Results** section (note the `../../` prefix — that page is two directories down):

```markdown
| | |
| --- | --- |
| ![Germination: bare soil with the first sprouts breaking the surface, probes and delivery lines already installed in all four pots](../../images/irrigation-rig-01-germination.jpg) | ![Emergence: sprouts visible in every pot, delivery-line emitters fixed above the soil surface](../../images/irrigation-rig-02-emergence.jpg) |
| **Germination.** Probes, emitters, and cabling in place before anything sprouts, so no pot is disturbed once the run starts. | **Emergence.** Seedlings up in all four pots, each fed by its own line from the shared reservoir. |
| ![Cotyledon stage: multiple seedlings per pot with open cotyledons](../../images/irrigation-rig-03-cotyledon-stage.jpg) | ![True leaves: denser stands of larger seedlings across the tray](../../images/irrigation-rig-04-true-leaves.jpg) |
| **Cotyledon stage.** Open cotyledons across all replicates — the loop is holding moisture in the germination band without waterlogging it. | **True leaves.** Stands thicken and leaf area grows; watering demand climbs and the loop tracks it without any change to the program. |
| ![Final results: full green stands of seedlings at the end of the run](../../images/irrigation-rig-05-final-results.jpg) | |
| **End of run.** Healthy, dense seedling stands grown start to finish on automated, sensor-triggered irrigation. | |
```

Also drop one frame in at the top of the project page, under "What it is":

```markdown
![The testbed early in the run: four pots on a tray, each with a soil-moisture probe and its own delivery line, cabling routed back to the controller](../../images/irrigation-rig-01-germination.jpg)
```

## Optional extras

If you have them, these would strengthen the write-up considerably. Add them here and link them
from the project page:

- The controller and wiring: PLC, terminal strip, relay, and the sensor harness.
- The reservoir and pump, and the tubing split into the four delivery lines.
- The ladder-logic program on screen.
- A wider shot showing the whole rig, controller included, in its location.
