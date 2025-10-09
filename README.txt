Visomni — Computer Vision Internship Challenge

Author: Adhini Nasarin P S
GitHub Repository: Visomni---Computer-Vision-Internship-Challenge

Tools Used: YOLOv8, OpenCV, Shapely, Pandas, Python 3.10+, Jupyter Notebook

🎯 Project Overview

This project implements an AI-based video analytics system that detects and tracks people in real-time and monitors their movement inside a restricted polygonal zone.
It is designed as part of the Visomni Computer Vision Internship Challenge, which focuses on developing intelligent vision systems to make industrial environments safer and more efficient.

🧩 Objectives

Detect people in each frame of a video.

Assign unique IDs to each detected person and track them across frames.

Define a polygonal zone (restricted area).

Log events when a person:

enters the zone

stays for more than 5 seconds

exits the zone

⚙️ Technologies & Libraries
Library	Purpose
Ultralytics YOLOv8	Person detection & tracking
OpenCV	Frame processing & video rendering
Shapely	Polygonal zone definition & point-in-polygon checks
Pandas	Event logging to CSV
TQDM	Progress visualization during frame processing
🧱 System Architecture

Input Video → YOLOv8 Detection

Detects all persons (class ID: 0).

YOLOv8 Tracking (persist=True)

Assigns unique, persistent track IDs.

Zone Detection

Uses Shapely to check if a tracked person’s center point lies within the polygonal restricted zone.

Event Logic

Logs “entered”, “stayed_5s”, and “exited” events based on frame timestamps.

Output

Annotated video (output.mp4)

Event log file (events.csv)

📂 Project Structure
Visomni---Computer-Vision-Internship-Challenge/
│
├── main.ipynb          # Main notebook with full implementation
├── events.csv          # Event log (timestamp, track_id, event)
├── output.mp4          # Processed output video with bounding boxes & zones
├── README.txt          # Short note for submission
├── README.md           # Detailed GitHub documentation
├── input.mp4           # Input test video (optional)
└── .git/               # Git commit history (required for submission)

🧪 How to Run Locally
# Clone the repository
git clone https://github.com/Adhini99/Visomni---Computer-Vision-Internship-Challenge.git
cd Visomni---Computer-Vision-Internship-Challenge

# (Optional) Create virtual environment
python -m venv venv
source venv/bin/activate   # or venv\\Scripts\\activate on Windows

# Install dependencies
pip install ultralytics opencv-python-headless pandas shapely tqdm

# Open and run the notebook
jupyter notebook main.ipynb

🧾 Sample Output

Output Video:
Annotated with:

Bounding boxes

Track IDs

Zone polygon

Events Logged (events.csv):

timestamp_seconds	track_id	event
0.0	3	entered
6.2	3	stayed_5s
8.5	3	exited
🚀 Key Features

✅ Real-time person detection and tracking
✅ Polygonal zone definition with dynamic coordinates
✅ Event logging for entry, exit, and stay duration
✅ Modular, extensible pipeline for industrial monitoring
✅ Clean and documented Jupyter notebook workflow

🧩 Improvements Implemented

Fixed exited_lost issue by merging with proper exited events.

Added configurable stay time threshold (STAY_THRESHOLD).

Enhanced visual output clarity and annotation consistency.

🧠 Challenges & Learnings

Maintaining tracking consistency for re-entering persons.

Balancing accuracy vs. performance when using different YOLOv8 variants.

Designing a clear event-based logging mechanism using timestamps.

Understanding how YOLO’s internal tracker manages lost detections.

🏁 Results

The system successfully detects and tracks multiple individuals simultaneously, logs all relevant events, and outputs both a visual and tabular summary of activities in the monitored zone.

🤝 Acknowledgment

This project was completed as part of the Visomni Computer Vision Internship Challenge, aiming to create vision-based systems for industrial safety and efficiency