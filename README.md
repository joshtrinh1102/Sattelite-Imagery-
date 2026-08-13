# Sattelite Imagery — Ship Detection

Detect ships (including berthed ships) in port satellite imagery. Fine-tunes a
pretrained YOLO oriented-bounding-box (OBB) model, since ships at a berth
sit at an angle relative to the image axes rather than axis-aligned.

## Data

`data/roboflow_dataset/` is a small annotated set (16 train / 5 valid / 5 test
tiles, 5 classes: `boats`, `containers`, `crane`, `personal ships`, `water`)
exported from Roboflow in YOLO-OBB format.

The full-resolution port scenes and ~39k unlabeled 1024px tiles they were cut
from live outside this repo (too large for git) at:

```
G:\My Drive\Me  Cho tôi\Career  Sự Nghiệp\Research\Supply Chain\i-jepa model\Sattelite Model\
```

Annotate more tiles from that pool and re-export to grow
`data/roboflow_dataset/` — 26 images is enough for a first baseline signal,
not enough for a reliable model.

## Usage

Open `ship_detection.ipynb` and run the cells top to bottom (Jupyter installs
its own dependencies in the first cell). It fine-tunes `yolo11n-obb.pt`
(pretrained on DOTA, an aerial/oriented-object dataset) on
`data/roboflow_dataset/`, reports metrics on the test split, and shows one
sample prediction. Runs and weights land in `runs/` (gitignored).
