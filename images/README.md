# Project photos

The write-ups reference the five project photos below by exact filename. Drop the photos into
this folder using these names and every image in the repository renders.

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

## Where each one is used

- `README.md` — the "Results at a glance" table uses frames 01, 03, and 05.
- `docs/projects/automated-plant-irrigation-system.md` — frame 01 at the top, then all five in
  the Results gallery.

## Optional extras

If you have them, these would strengthen the write-up considerably. Add them here and link them
from the project page:

- The controller and wiring: PLC, terminal strip, relay, and the sensor harness.
- The reservoir and pump, and the tubing split into the four delivery lines.
- The ladder-logic program on screen.
- A wider shot showing the whole rig, controller included, in its location.
