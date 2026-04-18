
# 📹 Video Processing & AI-Based Object Detection Internship  
## (Weeks 1, 2 & 3 – AIML Internship Project)

---

# 👨‍💻 Overview
This repository contains all tasks completed during the internship focused on:

- Video processing using FFmpeg  
- Frame extraction and reconstruction  
- Object detection using YOLOv8  
- Semantic segmentation using YOLOv8-seg  
- Performance evaluation of models  
- Audio-video merging and final multimedia generation  

---

# 📅 Week 1 Tasks

---

## 🔹 Task 1: Extract Frames from Video

### 🎯 Objective
Extract images from a YouTube video using FFmpeg.

### 🛠 Tools Used
- yt-dlp  
- ffmpeg  

### 📌 Commands
```bash
yt-dlp -f mp4 -o input.mp4 "<youtube_url>"

ffmpeg -i input.mp4 -vf fps=1 frame_%04d.png
````

### 📊 Output

* Extracted image frames stored in `/task1_frames/`

---

## 🔹 Task 2: Reconstruct Video from Frames

### 🎯 Objective

Convert extracted frames back into a video.

### 📌 Command

```bash
ffmpeg -framerate 30 -i frame_%04d.png -c:v libx264 output.mp4
```

### 📊 Output

* Reconstructed 1-minute video from frames

---

## 🔹 Task 3: Add Audio to Video

### 🎯 Objective

Merge audio with generated video.

### 📌 Command

```bash
ffmpeg -i output.mp4 -i audio.mp3 -c:v copy -c:a aac final_video.mp4
```

### 📊 Output

* Final video with audio track

---

# 📅 Week 2 Tasks

---

## 🔹 Task 1: Create Python Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 🔹 Task 2: Install Ultralytics (YOLO)

```bash
pip install -U ultralytics
```

---

## 🔹 Task 3: YOLO Object Detection

### 📌 Python Code

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")
results = model("image.jpg", show=True)
```

### 📊 Output

* Bounding boxes around detected objects
* Results stored in `/runs/detect/`

---

## 🔹 Task 4: Video Annotation + Audio Integration

### 📌 Convert frames to video

```bash
ffmpeg -framerate 30 -i annotated/frame_%04d.jpg output.mp4
```

### 📌 Add audio

```bash
ffmpeg -i output.mp4 -i music.mp3 -c:v copy -c:a aac final_output.mp4
```

---

# 📅 Week 3 Tasks

---

## 🔹 Task 1: Performance Metrics & Semantic Segmentation

### 📊 Metrics Used

* Precision
* Recall
* mAP50
* mAP50-95

### 📁 Metrics Location

```
runs/detect/val/
```

### 📌 Semantic Segmentation Command

```bash
yolo segment predict model=yolov8n-seg.pt source=frames/
```

### 📊 Output

```
runs/segment/predict/
```

---

## 🔹 Convert Segmented Images to Video

```bash
ffmpeg -framerate 30 -i segmented/frame_%04d.jpg segmented_video.mp4
```

---

## 🔹 Add Audio

```bash
ffmpeg -i segmented_video.mp4 -i music.mp3 -c:v copy -c:a aac final_segmented_video.mp4
```

---

# 📅 Week 3 Task 2 (Final Pipeline)

---

## 🔹 Steps Performed

* Trimmed video (13s → 60s)
* Object detection using YOLOv8
* Semantic segmentation using YOLOv8-seg
* Stacked videos vertically
* Added background music

---

## 📌 Final Command (Video Stacking)

```bash
ffmpeg -i raw.mp4 -i detect.mp4 -i segment.mp4 \
-filter_complex "vstack=inputs=3" final_stacked.mp4
```

---

## 📌 Add Audio to Final Video

```bash
ffmpeg -i final_stacked.mp4 -i music.mp3 -c:v copy -c:a aac final_output.mp4
```

---

# 📊 Final Output

* Raw video
* Object detection video
* Semantic segmentation video
* Final merged video with audio

---

# 🚀 Key Learnings

* FFmpeg video processing
* Frame extraction and reconstruction
* YOLO object detection
* Semantic segmentation
* AI-based video pipeline development
* Performance evaluation metrics

---

# 🙏 Acknowledgement

Thanks to the internship mentors for structured guidance and hands-on learning experience throughout the program.

```

---

