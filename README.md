# Tasks Performed During the Internship using AIML Skills

---

# 📹 Video Processing & Object Detection Internship (Week 1, 2 & 3)

## 👨‍💻 Overview

This repository documents my progress and submissions for the internship tasks assigned. The tasks focus on **video processing using FFmpeg**, multimedia manipulation, and **AI-based computer vision techniques** such as object detection and semantic segmentation using **Ultralytics YOLO**.

---

# 📅 Week 1 Tasks

## 🔹 Task 1: Extract Images from Video using FFmpeg

### 🎯 Objective

* Download a short YouTube video
* Extract multiple frames (images) using FFmpeg

### 🛠️ Tools Used

* yt-dlp – for downloading YouTube videos
* ffmpeg – for frame extraction

### 📌 Steps Performed

Downloaded video:

```
yt-dlp <youtube_video_url>
```

Extracted frames:

```
ffmpeg -i input.mp4 -vf fps=1 output_%04d.png
```

### 📷 Output

* Extracted images stored in `/task1_frames/`
* Sample images uploaded

### 🔗 Video Link

https://www.youtube.com/watch?v=STzJdvt_8X0&list=PPSV

---

## 🔹 Task 2: Generate Video from Frames

### 🎯 Objective

* Extract 30 FPS frames from a 1-minute video (~1800 images)
* Reconstruct video using extracted frames

### 📌 Steps Performed

Extract frames at 30 FPS:

```
ffmpeg -i input.mp4 -vf fps=30 frames/frame_%04d.png
```

Recreate video:

```
ffmpeg -framerate 30 -i frames/frame_%04d.png -c:v libx264 -pix_fmt yuv420p output.mp4
```

### 📊 Output

* ~1800 frames generated
* Reconstructed 1-minute video

### 🔗 Video Link

https://www.youtube.com/watch?v=mbqCXpmo15A&t=1s

---

## 🔹 Task 3: Add Audio to Video

### 🎯 Objective

* Select a 1-minute audio track
* Merge audio with generated video

### 🛠️ Tools Used

* Audio source: Pixabay
* Audio editing: Audacity
* FFmpeg for merging

### 📌 Steps Performed

Trim audio to 1 minute using Audacity

Merge audio with video:

```
ffmpeg -i output.mp4 -i audio.mp3 -c:v copy -c:a aac final_output.mp4
```

### 🎧 Output

* Final video with audio track

### 🔗 Resources

Video: https://www.youtube.com/watch?v=mbqCXpmo15A&t=1s


Audio: https://cdn.pixabay.com/download/audio/2025/02/06/audio_9939140ee3.mp3

---

# 📅 Week 2 Tasks

## 🔹 Task 1: Create Python Virtual Environment

### 🎯 Objective

Set up isolated Python environment for project work

### 📌 Steps

```
python3 -m venv venv
source venv/bin/activate
```

---

## 🔹 Task 2: Install Ultralytics

### 🎯 Objective

Install YOLO package for object detection

### 📌 Command

```
pip install -U ultralytics
```

---

## 🔹 Task 3: Run YOLO Object Detection

### 🎯 Objective

Perform object detection using pretrained YOLO model

### 📌 Sample Code

```
from ultralytics import YOLO

model = YOLO("yolov8n.pt")
results = model("image.jpg", show=True)
```

### 📊 Output

* Detected objects with bounding boxes
* Outputs stored in `/runs/detect/`

---

## 🔹 Task 4: Advanced Video Annotation with YOLOv8 and Audio Integration

### 🎯 Objective

Process video frames using YOLOv8 and reconstruct annotated video

### 🛠️ Tools Used

* Python & Virtual Environment
* Ultralytics YOLOv8
* OpenCV, FFmpeg, Matplotlib

### 📌 Steps Performed

Run detection on frames using custom script

Create video from annotated frames:

```
ffmpeg -framerate 30 -i annotated/frame_%04d.jpg -c:v libx264 -pix_fmt yuv420p output_video_no_audio.mp4
```

Add audio:

```
ffmpeg -i output_video_no_audio.mp4 -i music_1min.mp3 -c:v copy -c:a aac -shortest output_video.mp4
```

### 📊 Output

* Annotated frames
* Video with detected objects and audio

---

# 📅 Week 3 Tasks

## 🔹 Task 1: Performance Metrics & Semantic Segmentation

### 🎯 Objective

* Analyze detection performance metrics
* Apply semantic segmentation on images
* Convert segmented images into video with audio

---

## 🧠 Part A: Performance Metrics

### 📌 Description

Metrics were obtained from YOLO validation results stored in:

```
runs/detect/val/
```

### 📊 Metrics Observed

* Precision
* Recall
* mAP50
* mAP50-95

### 📷 Files Generated

* `results.png`
* `confusion_matrix.png`
* `results.csv`

---

## 🧠 Part B: Semantic Segmentation

### 🎯 Objective

Perform pixel-level classification of objects

### 📌 Command Used

```
yolo segment predict model=yolov8n-seg.pt source=frames/
```

### 📊 Output

* Segmented images stored in:

```
runs/segment/predict/
```

* Objects highlighted with colored masks

---

## 🧠 Part C: Convert Segmented Images to Video

### 📌 Command

```
ffmpeg -framerate 30 -pattern_type glob -i "*.jpg" -c:v libx264 -pix_fmt yuv420p segmented_video.mp4
```

---

## 🧠 Part D: Add Audio

### 📌 Command

```
ffmpeg -i segmented_video.mp4 -i music_1min_trimmed.mp3 -c:v copy -c:a aac final_segmented_video.mp4
```

---

## 📊 Final Output

* Segmented images with pixel-wise classification
* Final 1-minute video with segmentation + audio

---

# 🚀 Key Learnings

* Learned video processing using FFmpeg
* Understood frame extraction and reconstruction
* Gained hands-on experience with object detection using YOLO
* Explored semantic segmentation for precise object boundaries
* Learned performance evaluation using precision, recall, and mAP
* Developed end-to-end AI video processing pipeline

---

# 📌 Notes

* Maintain sequential frame naming for video creation
* Always activate virtual environment before running code
* Ensure model files (`yolov8n.pt`, `yolov8n-seg.pt`) are present
* Segmentation provides more precise results than detection

---

# 🙏 Acknowledgement

Thanks to the internship mentors for structured tasks and continuous guidance throughout the program.

