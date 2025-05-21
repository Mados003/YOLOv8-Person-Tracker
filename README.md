# YOLOv8 Person Tracker

This project implements an advanced person tracking system using YOLOv8's pose estimation capabilities. It can track multiple people in video footage, maintain their identities through brief occlusions, and visualize their movement paths with color-coded trails.

## Features

- **Robust Person Detection**: Uses YOLOv8 pose estimation model to accurately detect people
- **Persistent Identity Tracking**: Maintains consistent IDs for individuals even when temporarily occluded
- **Motion Prediction**: Predicts positions of occluded individuals using velocity history
- **Visual Trails**: Displays color-coded movement paths for each tracked person
- **Status Overlay**: Shows tracking status (active/lost) with frame count information
- **Confidence Visualization**: Displays detection confidence scores for each person

## Requirements

- Python 3.7+
- OpenCV
- NumPy
- Ultralytics YOLOv8
- GPU recommended for real-time processing

## Installation

1. Clone this repository:
```
git clone https://github.com/yourusername/YOLOv8-Person-Tracker.git
cd YOLOv8-Person-Tracker
```

2. Install dependencies:
```
pip install ultralytics opencv-python numpy
```

3. Download the YOLOv8 pose model (this happens automatically on first run)

## Usage

Basic usage:
```python
from tracker import track_and_draw

# Process a video file
track_and_draw(
    input_path='path/to/video.mp4',
    output_path='output_video.mp4',
    track_multiple=True,
    conf_threshold=0.7
)
```

## How It Works

1. **Detection**: The system uses YOLOv8's pose estimation model to detect people in each video frame
2. **Tracking**: People are assigned unique IDs that persist across frames
3. **Path Visualization**: Movement paths are drawn as color-coded trails
4. **Occlusion Handling**: When a person is temporarily lost from view:
   - The system predicts their position based on previous velocity
   - Tracking is maintained for up to 45 frames of absence
   - Visual indicators show predicted positions

## Parameters

- `input_path`: Path to input video
- `output_path`: Path for processed output video
- `track_multiple`: Enable tracking multiple people (default: False)
- `conf_threshold`: Detection confidence threshold (default: 0.7)

## Limitations

- Works best with up to 3 people in frame
- Prediction accuracy decreases with longer occlusions
- Performance depends on video resolution and hardware

## Future Improvements

- Implementation of more sophisticated tracking algorithms
- Support for larger groups of people
- Behavior analysis based on movement patterns
