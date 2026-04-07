# Online-Internship-I-HUB-Data-IIITH
Tasks performed during the internship using AIML skills

📹 Video Processing & Object Detection Internship (Week 1 & 2)

👨‍💻 Overview

This repository documents my progress and submissions for the internship tasks assigned. The tasks focus on video processing using FFmpeg, basic multimedia manipulation, and introduction to object detection using YOLO.

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
