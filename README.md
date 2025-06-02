# ⚽ Football Match Analysis

> A complete computer vision pipeline to analyze football match videos — including player tracking, ball detection, team color assignment, speed/distance estimation, and match annotation.

---

## 🎯 Objective

This project automates the analysis of football videos by detecting and tracking players and the ball, estimating movement, assigning teams, and overlaying insights such as:

- Player speed and distances
- Ball possession and passes
- Team colors and roles
- Camera movement correction
- Tactical position visualization (bird-eye view)

---

## 📁 Project Structure

```
football_analysis/
├── input_videos/               # Raw input videos (.mp4)
├── output_videos/              # Annotated output videos (.avi/.mp4)
├── models/                     # YOLO models (best.pt)
├── stubs/                      # Precomputed data for fast testing
├── utils/                      # Utility functions (video, bbox, etc.)
├── trackers/                   # Tracking and annotations (YOLO + ByteTrack)
├── team_assigner/              # Team color classification
├── view_transformer/           # Homography and top-view transformation
├── speed_and_distance_estimator/  # Speed and distance estimation logic
├── player_ball_assigner/       # Ball ownership logic
├── camera_movement_estimator/  # Camera motion compensation
├── training/                   # Notebook for training YOLO
└── main.ipynb                  # Main Colab notebook to run the pipeline
```

---

## 🚀 How to Use (Google Colab)

1. **Mount your Drive**:
    ```python
    from google.colab import drive
    drive.mount('/content/drive')
    %cd /content/drive/MyDrive/football_analysis
    ```

2. **Install dependencies**:
    ```bash
    !pip install opencv-python tqdm numpy ultralytics
    ```

3. **Run the pipeline**:
    - Open `main.ipynb`
    - Set your input video path
    - Execute all cells

---

## 🧠 Features

| Feature                      | Description                                              |
|-----------------------------|----------------------------------------------------------|
| 🎯 Detection & Tracking     | YOLOv8 + ByteTrack for multi-object tracking             |
| 🎽 Team Assignment          | Color-based classification for player team labels        |
| ⚽ Ball Possession          | Nearest-player proximity-based control detection         |
| 📏 Speed & Distance         | Estimate motion and running distances for each player    |
| 🎥 Camera Stabilization     | Detects and compensates for camera movements             |
| 🧭 View Transformation      | Project player coordinates to a bird-eye tactical view   |
| 🖼️ Annotated Output        | Final annotated video saved with team labels, motion, etc |

---

## 📸 Example Output

<p align="center">
  <img src="output_videos/screenshot.png" width="600"/>
</p>

---

## 📃 Sample Usage

```python
from utils import read_video
from trackers import Tracker

video_frames = read_video("input_videos/match.mp4")
tracker = Tracker("models/best.pt")
tracks = tracker.get_object_tracks(video_frames)
```

---

## 🧠 Training

YOLO models were trained using custom football datasets. See:
```
training/football_training_yolo_v5.ipynb
```

---

## 🙌 Credits

- YOLOv8 by [Ultralytics](https://github.com/ultralytics/ultralytics)
- ByteTrack for MOT
- Community datasets from Roboflow
- Project developed and tested in Google Colab

---

## 📄 License

MIT License © 2025 — Your Name or Team Name
