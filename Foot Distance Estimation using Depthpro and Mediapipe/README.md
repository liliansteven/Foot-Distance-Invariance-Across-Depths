# Foot Distance Estimation using DepthPro and MediaPipe 

## Overview

This project estimates foot distance in videos using depth estimation models and Mediapipe Pose. It implements multiple methods to measure foot distance based on different 3D coordinate extraction techniques and estimated focal length.

## Features

- Uses `DepthPro-hf` for depth estimation.
- Utilizes `Mediapipe Pose` for pose landmark detection.
- Computes foot distance using multiple methods:
  1. **Pinhole Camera Model**
  2. **Avoiding Camera Calibration**
  3. **Estimated Focal Length from Model**
  4. **Focal Length from Shoulder Proportions**
- Processes video frames and overlays distance calculations on the output video.

## Installation

### Install Required Dependencies

```bash
pip install git+https://github.com/huggingface/transformers.git
pip install mediapipe opencv-python numpy torch pillow
```

## Usage

### Running the Script

```python
video_path = '/content/Kirolos_video.mp4'  # Replace with your video path
output_path = '/content/output.mp4'  # Define output file path
process_video(video_path, output_path)
```

### Functions

- `estimate_depth_and_focal_length(frame)`: Estimates the depth map and focal length from the input frame.
- `convert_2d_to_3d_pinhole(landmarks_2d, depth_map, focal_length)`: Converts 2D pose landmarks into 3D coordinates using the pinhole camera model.
- `extract_3d_coordinates_without_calibration(landmarks_2d, depth_map)`: Extracts 3D coordinates without using camera calibration.
- `compute_3d_with_estimated_focal(landmarks_2d, depth_map, estimated_focal)`: Uses estimated focal length to compute 3D coordinates.
- `estimate_focal_length_from_shoulder(shoulder_width, depth)`: Estimates the focal length using shoulder width and depth.
- `compute_3d_euclidean_distance(feet_3d)`: Computes 3D Euclidean distance between feet.
- `compute_foot_distance_with_focal(feet_2d, depth_map, focal_length)`: Computes foot distance using estimated focal length.
- `process_video(video_path, output_path)`: Processes a video, extracts depth and pose landmarks, calculates distances, and generates an annotated output video.


## Output

- The script generates a processed video where distances calculated using different methods are displayed on each frame.
- please check the final output [here](https://drive.google.com/file/d/1QfNv_e-6B-iNn_6mpOa57fl5pVIMpXTO/view?usp=sharing)

## Notes

- Ensure that the input video is well-lit and contains a clear view of the subject's feet for accurate results.
- Depth estimation quality depends on the performance of `DepthPro-hf`.

## References

- [Hugging Face Transformers](https://github.com/huggingface/transformers)
- [Mediapipe Pose](https://developers.google.com/mediapipe/solutions/vision/pose)
- [DepthPro-hf](https://huggingface.co/apple/DepthPro-hf)
