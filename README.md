# Online-Internship-I-HUB-Data-IIITH
Tasks performed during the internship using AIML skills

📹 Video Processing & Object Detection Internship (Week 1 & 2)

👨‍💻 Overview

This repository documents my progress and submissions for the internship tasks assigned.
The tasks focus on video processing using FFmpeg, basic multimedia manipulation, and introduction to object detection using YOLO.

📅 Week 1 Tasks

🔹 Task 1: Extract Images from Video using FFmpeg

🎯 Objective

Download a short YouTube video
Extract multiple frames (images) using FFmpeg

🛠️ Tools Used

yt-dlp – for downloading YouTube videos
ffmpeg – for frame extraction

📌 Steps Performed

Downloaded video:

yt-dlp <youtube_video_url>

Extracted frames:

ffmpeg -i input.mp4 -vf fps=1 output_%04d.png

📷 Output

Extracted images are stored in /task1_frames/
Sample images will be uploaded separately

🔗 Video Link

 https://www.youtube.com/watch?v=STzJdvt_8X0&list=PPSV



🔹 Task 2: Generate Video from Frames

🎯 Objective

Extract 30 FPS frames from a 1-minute video (~1800 images)
Reconstruct video using extracted frames

Video -  https://www.youtube.com/watch?v=mbqCXpmo15A&t=1s


📌 Steps Performed

Extract frames at 30 FPS:

ffmpeg -i input.mp4 -vf fps=30 frames/frame_%04d.png

Recreate video:

ffmpeg -framerate 30 -i frames/frame_%04d.png -c:v libx264 -pix_fmt yuv420p output.mp4

📊 Output

~1800 frames generated
Reconstructed 1-minute video


🔹 Task 3: Add Audio to Video

🎯 Objective

Select a 1-minute audio track
Merge audio with generated video

🛠️ Tools Used

Audio source: Pixabay
Audio editing: Audacity
FFmpeg for merging

📌 Steps Performed

Trim audio to 1 minute (using Audacity)

Video -  https://www.youtube.com/watch?v=mbqCXpmo15A&t=1s

Audio - https://cdn.pixabay.com/download/audio/2025/02/06/audio_9939140ee3.mp3?filename=rolzim-peacable-milieu-297513.mp3

Merge audio with video:

ffmpeg -i output.mp4 -i audio.mp3 -c:v copy -c:a aac final_output.mp4

🎧 Output

Final video with audio track

📅 Week 2 Tasks


🔹 Task 1: Create Python Virtual Environment

🎯 Objective

Set up isolated Python environment for project work

📌 Steps

python3 -m venv myenv
source myenv/bin/activate


🔹 Task 2: Install Ultralytics

🎯 Objective

Install YOLO package for object detection

📌 Command

pip install -U ultralytics


🔹 Task 3: Run YOLO Object Detection

🎯 Objective

Perform object detection using pretrained YOLO model

📌 Sample Code

from ultralytics import YOLO

model = YOLO("yolov8n.pt")
results = model("image.jpg", show=True)

📊 Output

Detected objects with bounding boxes
Output images/videos stored in /runs/detect/


## **Task 4: Advanced Video Annotation with YOLOv8 and Audio Integration**

This task demonstrates an end-to-end pipeline where raw frames from a video are processed using **YOLOv8** for object detection, then combined back into a video with an optional audio track.


### **Step 1: Set up Virtual Environment**

Create a fresh virtual environment and activate it:

```bash
python3 -m venv venv
source venv/bin/activate
```

Install all required packages:

```bash
pip install ultralytics torch torchvision opencv-python matplotlib ffmpeg-python
```

Verify installation:

```bash
pip list | grep -E "ultralytics|torch|opencv-python|matplotlib|ffmpeg-python"
```

---

### **Step 2: Run YOLOv8 Detection on Frames**

Create a `detect.py` script:

```python
from ultralytics import YOLO
import os

input_folder = "./frames"
output_folder = "./annotated"
os.makedirs(output_folder, exist_ok=True)

model = YOLO("yolov8n.pt")  # Pre-trained YOLOv8 model

images = sorted(os.listdir(input_folder))
for img_name in images:
    img_path = os.path.join(input_folder, img_name)
    model.predict(source=img_path, save=True, save_dir=output_folder)
```

Run detection:

```bash
python detect.py
```

✅ Annotated images will appear in the `annotated/` folder.

---

### **Step 3: Create Video from Annotated Frames**

Use `FFmpeg` to combine frames into a video at 30 FPS:

```bash
ffmpeg -framerate 30 -i annotated/frame_%04d.jpg -c:v libx264 -pix_fmt yuv420p output_video_no_audio.mp4
```

> Note: `%04d` assumes filenames like `frame_0001.jpg`. Adjust if your numbering differs.

---

### **Step 4: Add Audio to Video**

If you have background audio (`music_1min.mp3`), merge it with the video:

```bash
ffmpeg -i output_video_no_audio.mp4 -i music_1min.mp3 -c:v copy -c:a aac -shortest output_video.mp4
```

✅ The final video `output_video.mp4` will have both annotated frames and audio.

---

### **Step 5: Key Notes**

* Make sure the **frames folder** contains all images in sequential order.
* YOLOv8 must be properly installed and the model file `yolov8n.pt` present in the working folder.
* Using `venv` keeps dependencies isolated and avoids conflicts with other projects.
* All paths are **WSL and Windows compatible** (e.g., `/mnt/c/...`).

---

### **Outcome**

* Annotated frames with detected objects.
* Video compilation with optional background music.
* Ready-to-use workflow for video analysis using YOLOv8.

Video -  https://www.youtube.com/watch?v=mbqCXpmo15A&t=1s

Audio - https://cdn.pixabay.com/download/audio/2026/03/31/audio_4c1ff76e9f.mp3?filename=kaazoom-thoughtful-1-minute-edit-relaxing-guitar-music-511743.mp3


🚀 Key Learnings

Learned video processing using FFmpeg
Understood frame extraction and reconstruction
Worked with audio-video merging
Set up Python virtual environments
Gained hands-on experience with YOLO object detection

📌 Notes

All outputs (images, videos) are uploaded separately
Commands tested in Linux environment
GitHub commits reflect progress timeline

🙌 Acknowledgment


Thanks to the internship mentors for structured tasks and continuous guidance.
