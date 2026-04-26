# 🚀 Video Processing & AI-Based Object Detection Internship

*(AIML Internship Project – Weeks 1 to 4)*

---

## 👨‍💻 Overview

This repository documents a complete internship project focused on:

* 🎥 Video processing using FFmpeg
* 🧩 Frame extraction and reconstruction
* 🤖 Object detection using YOLOv8
* 🧠 Semantic segmentation using YOLOv8-seg
* 📊 Model evaluation and performance metrics
* 🎵 Audio-video merging and multimedia generation
* 📁 Dataset structure analysis (YOLO / COCO format)

The project demonstrates an end-to-end AI video pipeline from raw video input to structured AI-processed outputs.

---

## 🛠️ Tech Stack

* FFmpeg
* Python 3.x
* Ultralytics YOLOv8
* OpenCV
* yt-dlp
* Linux / WSL environment

---

# 📅 Week 1 – Video Processing Pipeline

## 🔹 Task 1: Extract Frames from Video

### 🎯 Objective

Extract frames from a YouTube video using FFmpeg.

```bash
yt-dlp -f mp4 -o input.mp4 "<youtube_url>"
ffmpeg -i input.mp4 -vf fps=1 frame_%04d.png
```

---

## 🔹 Task 2: Reconstruct Video

```bash
ffmpeg -framerate 30 -i frame_%04d.png -c:v libx264 output.mp4
```

---

## 🔹 Task 3: Add Audio

```bash
ffmpeg -i output.mp4 -i audio.mp3 -c:v copy -c:a aac final_video.mp4
```

---

# 📅 Week 2 – YOLO Object Detection Setup

## 🔹 Virtual Environment Setup

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 🔹 Install Ultralytics

```bash
pip install -U ultralytics
```

---

## 🔹 Object Detection (YOLOv8)

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")
results = model("image.jpg", show=True)
```

---

## 🔹 Output

* Detected objects with bounding boxes
* Results saved in `runs/detect/`

---

# 📅 Week 3 – Segmentation & Advanced Video Pipeline

## 🔹 Semantic Segmentation

```bash
yolo segment predict model=yolov8n-seg.pt source=frames/
```

---

## 🔹 Performance Metrics

Located in:

```
runs/detect/val/
```

### 📊 Metrics:

* Precision
* Recall
* mAP50
* mAP50-95

---

## 🔹 Video Reconstruction

```bash
ffmpeg -framerate 30 -i annotated/frame_%04d.jpg output.mp4
```

---

## 🔹 Add Audio

```bash
ffmpeg -i output.mp4 -i music.mp3 -c:v copy -c:a aac final_output.mp4
```

---

## 🔹 Final Pipeline (Stacked Output)

```bash
ffmpeg -i raw.mp4 -i detect.mp4 -i segment.mp4 -filter_complex "vstack=inputs=3" final_stacked.mp4
```

---

# 📅 Week 4 – Dataset Understanding (YOLO / COCO8 Analysis)

---

## 🔹 Task 1: Dataset Structure Analysis

### 🎯 Objective

Understand YOLO dataset configuration using COCO8 dataset.

### 📁 Dataset Structure

```
coco8/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
```

---

## ⚙️ YAML Configuration File

Example (`coco8.yaml`):

```yaml
path: coco8

train: images/train
val: images/val

names:
  0: person
  1: bicycle
  2: car
```

---

## 📌 Role of YAML

* Defines dataset structure
* Maps class IDs to names
* Links dataset to YOLO model in Ultralytics

---

## 🏷️ Label Format

```
<class_id> <x_center> <y_center> <width> <height>
```

### Example:

```
58 0.519219 0.451121 0.39825 0.75729
75 0.501188 0.592138 0.26 0.456192
```

---

## 📌 Interpretation

* Each line = one object
* Coordinates are normalized (0–1)
* Multiple objects per image supported

---

## 🔹 Task 2: YOLO Model Training & Inference

### 🎯 Objective

Train a YOLOv8 object detection model on a custom labeled dataset and run inference.

---

## 📌 Training Command

```bash
yolo detect train data=data.yaml model=yolov8n.pt epochs=10
```

---

## 📌 Output After Training

* Trained weights saved in:

```
runs/detect/train/weights/best.pt
```

* Training logs and metrics saved in:

```
runs/detect/train/
```

---

## 📌 Inference (Testing Model)

```bash
yolo detect predict model=best.pt source=image.jpg
```

or video:

```bash
yolo detect predict model=best.pt source=video.mp4
```

---

## 📊 Results

* Bounding box detection on custom dataset
* Successful model training using YOLOv8
* Outputs stored in `runs/detect/predict/`

---

## 📊 Key Learnings

* YOLO datasets require strict structure
* YAML connects dataset and model logic
* Labels store object-level spatial data
* COCO8 is used for testing/debugging pipelines
* Proper dataset formatting is essential for AI training

---

## 📚 References

* [https://docs.ultralytics.com](https://docs.ultralytics.com)
* [https://docs.ultralytics.com/datasets/detect/coco8/](https://docs.ultralytics.com/datasets/detect/coco8/)
* [https://github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)

---

## 🧠 Final Outcome

This internship project successfully demonstrates:

* End-to-end video AI pipeline
* Object detection and segmentation workflow
* Dataset configuration understanding
* Real-world application of YOLO models
* Media processing using FFmpeg

---

## ⭐ Repository Status

✔ Completed Weeks 1–4 Tasks

✔ Video Processing Pipeline

✔ YOLO Object Detection & Segmentation

✔ Dataset Analysis (COCO8)

✔ Model Training & Inference

✔ Documentation & Reporting

---



