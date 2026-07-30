# Filters

It is an augmented reality project that generates an interactive portal in the camera video using real-time hand tracking. Through a natural gesture, the user can al[...]

---

## Features

- Real-time hand tracking using MediaPipe Hands.
- Perspective portal dynamically built from the index and thumb tips of both hands.
- Eight visual filters applied exclusively inside the portal area.
- Filter change by gesture: bringing the hands closer triggers the transition to the next filter in the sequence.
- Hysteresis system to avoid accidental changes due to shakes or tracking inaccuracy.

## Included filters

| Filter | Description |
|--------|-------------|
| `filtro_grid` | Grid overlay on the original image |
| `filtro_1` | Duotone segmented by brightness thresholds |
| `filtro_2` | Black-and-white halftone dot pattern |
| `filtro_3` | Chromatic aberration with RGB channel separation |
| `filtro_5` | Thermal camera simulation using a colormap |
| `filtro_6` | Vintage sepia style with vignetting and grain |
| `filtro_blanco` | Frosted glass effect on the image |
| `filtro_rosa` | Pink-magenta duotone halftone |

## Installation

Clone the repository:

```bash
git clone https://github.com/mishu006/Filters.git
cd Filters
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate      # Windows
source venv/bin/activate   # macOS / Linux
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

```bash
python main.py
```

With the camera active, raise both hands with the index finger and thumb extended: the portal is generated automatically between them. Bring them closer to "close" and advance to the next filter in the [...]

## Project structure

```
Filters/
├── main.py            Entry point: capture loop and filter cycle
├── hand_tracking.py    Detection of extended fingers from landmarks
├── geometry.py          Portal geometry and close-gesture detection
├── filters.py            Definition of the eight available filters
├── requirements.txt
└── README.md
```

## Extending the project

To add a new filter, just define a function in `filters.py` that receives a BGR crop (`numpy.ndarray`) and returns a crop of the same size:

```python
def filtro_nuevo(roi: np.ndarray) -> np.ndarray:
    return roi
```

Then add it to the `FILTROS` list at the end of the file. The filter cycle automatically adapts to the number of elements in that list.

## Tech stack

- Python 3.10
- OpenCV
- MediaPipe
- NumPy

## License

This project is distributed under the MIT license.
