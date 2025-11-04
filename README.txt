AI Assignment: Footfall Counter using Computer Vision
=======================================================

Objective:
-----------
To develop a real-time **footfall counting system** that detects and tracks people in a video using
YOLOv8 and a Centroid Tracking algorithm. The system counts the number of people entering and exiting
a defined area, providing visual analytics via an annotated output video and event log.

Approach:
---------
1. **Detection:**
   - Model: YOLOv8 (weights: 'yolov8n.pt' by default)
   - Task: Person detection (COCO class 0)
   - Framework: Ultralytics YOLOv8 for efficient and accurate detection

2. **Tracking:**
   - Algorithm: Centroid Tracker (custom implementation)
   - Purpose: Maintains consistent IDs for detected persons across frames, even with brief occlusions

3. **Counting Logic:**
   - A virtual horizontal line is drawn across the frame (configurable position)
   - Direction-based counting:
        - When a tracked person crosses upward → **Exit Count**
        - When a tracked person crosses downward → **Entry Count**

4. **Visualization:**
   - Bounding boxes, IDs, and entry/exit counts are drawn on the video frames
   - Final output video is saved with all visual annotations

Usage:
------
1. Place your **input video** file (e.g., 'input_video.mp4') in the same folder as this script.
2. Update the path inside the code:
      SOURCE = "input_video.mp4"
3. Run the notebook or Python script:
      python footfall_counter_merged.py
4. The processed output video and event logs will be automatically generated.

Generated Files:
----------------
- **output_video.avi** : Video annotated with bounding boxes, track IDs, and counts
- **count_log.csv**    : CSV file containing timestamped entry and exit events

Dependencies:
-------------
- Python 3.8+
- ultralytics (YOLOv8)
- opencv-python
- numpy
- imutils

Install using:
    pip install ultralytics opencv-python imutils numpy

Notes & Challenges:
-------------------
- Re-identification: If a person leaves the frame and re-enters, the tracker may assign a new ID.
- Accuracy: Adjust confidence threshold and centroid distance parameters for best results.
- For higher performance, resize input frames or switch to 'yolov8s' for better detection in crowded scenes.
- System assumes a top-down or fixed camera angle for optimal counting accuracy.

