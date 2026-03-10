# Traffic Sign Board Detection

> Real-time traffic sign recognition, powered by YOLOv5.

---

## Overview

Traffic Sign Board Detection is a computer vision project that performs real-time recognition of road signs using a YOLOv5 model trained on the German Traffic Sign Recognition Benchmark (GTSRB). It detects and classifies 43 types of traffic signs directly from a webcam feed or video file, drawing bounding boxes with class labels and confidence scores at inference time.

---

## Features

- **Real-Time Detection** - Live inference from webcam or video file with bounding boxes and confidence scores
- **43-Class Recognition** - Full GTSRB suite including speed limits, warnings, prohibitions, and mandatory signs
- **Priority Sign Highlighting** - Stop, No Entry, and Yield signs are automatically highlighted in red
- **FPS Overlay** - Live frames-per-second counter rendered directly on the detection feed
- **Video Export** - Save annotated output to `.mp4` with the `--save` flag
- **Screenshot on Demand** - Press `s` during live detection to capture a timestamped JPEG
- **GPU / CPU Auto-Detect** - Automatically uses CUDA if available, falls back to CPU
- **Configurable Thresholds** - Adjust confidence and IoU thresholds via CLI flags

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.8+ |
| Model | YOLOv5 (custom-trained) |
| Deep Learning | PyTorch |
| Computer Vision | OpenCV |
| Dataset | GTSRB (43 classes, 39k images) |
| Experiment Tracking | WandB |

---

## Getting Started (Local Setup)

### Prerequisites

- Python 3.8+
- [Anaconda](https://www.anaconda.com) or a virtual environment (recommended)
- The pre-trained model weights file (`best_93.pt`) - download link below
- Git

### 1. Clone the repository

```bash
git clone https://github.com/mahanthvamsi/Traffic-Sign-Board-Detection.git
cd Traffic-Sign-Board-Detection
```

### 2. Clone YOLOv5 into the project

```bash
git clone https://github.com/ultralytics/yolov5.git
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
# or install from the yolov5 requirements directly:
pip install -r yolov5/requirements.txt
```

### 4. Download the pre-trained model

Download [`best_93.pt`](https://mega.nz/file/rV4HDQ5b#UfgDAMlVHvfzSr7PquE8HWx_6jhRmDUGBS-qyfIn_oE) and place it in the project root:

```
Traffic-Sign-Board-Detection/
└── best_93.pt   ← here
```

### 5. Replace detect.py and run

```bash
cp src/detect.py yolov5/detect.py
cd yolov5
python detect.py --weights ../best_93.pt --source 0
```

---

## Usage

```bash
# Webcam (real-time)
python detect.py --weights ../best_93.pt --source 0

# Video file
python detect.py --weights ../best_93.pt --source /path/to/video.mp4

# Single image
python detect.py --weights ../best_93.pt --source /path/to/image.jpg

# Save annotated output to file
python detect.py --weights ../best_93.pt --source video.mp4 --save

# Headless mode (no window - useful for servers)
python detect.py --weights ../best_93.pt --source video.mp4 --save --no-view

# Custom thresholds
python detect.py --weights ../best_93.pt --source 0 --conf 0.5 --iou 0.4
```

### Keyboard shortcuts (live mode)

| Key | Action |
|-----|--------|
| `q` | Quit |
| `s` | Save screenshot |

---

## Model Performance

| Metric | Value |
|--------|-------|
| mAP@0.5 | **>93%** |
| Backbone | YOLOv5 |
| Input Size | 640×640 |
| Training Images | 39,209 |
| Classes | 43 |

Training runs and hyperparameter sweeps tracked via [WandB](https://wandb.ai/mdhamani/YOLOv5).

---

## Dataset

**GTSRB - German Traffic Sign Recognition Benchmark**

| Split | Images | Labels |
|-------|--------|--------|
| Training | 39,209 | Labeled |
| Test | 12,630 | Unlabeled |
| Classes | 43 | - |

Full dataset info at [benchmark.ini.rub.de](https://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset).

---

## Project Structure

```
Traffic-Sign-Board-Detection/
├── src/
│   └── detect.py          # Custom detection script (replaces yolov5/detect.py)
├── yolov5/                # Cloned YOLOv5 repo (not committed)
├── best_93.pt              # Pre-trained weights (downloaded separately)
├── requirements.txt
└── README.md
```

---

## License

This project is for academic and personal use.
