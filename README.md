# Augmented Reality Engine

A Python-based Augmented Reality engine that detects ArUco markers and renders 3D objects onto a live webcam feed using OpenCV.

<p align="center">
  <img src="https://user-images.githubusercontent.com/31953115/121981314-0b712c00-cdab-11eb-98d4-decf737824ea.gif" alt="AR Demo" />
</p>

## Overview
This project implements an AR pipeline from scratch without relying on the built-in `cv2.aruco` detection module. It demonstrates the core algorithms of Computer Vision:
1.  **Marker Detection:** Uses adaptive thresholding and bit-signature matching to identify custom ArUco markers.
2.  **Pose Estimation:** Calculates the Homography and Projection matrices to map 3D coordinates to the 2D camera plane.
3.  **Rendering:** Parses `.obj` files (3D models) and renders them frame-by-frame on the detected marker.

## Dependencies

* **Python 3.10+** (Tested on Python 3.13)
* **OpenCV** (opencv-contrib-python)
* **NumPy**

### Installation
You can install the required libraries directly using pip:

```bash
pip install opencv-contrib-python numpy
```

How to Run
1. Setup the Marker
The project uses the marker located in data/m1.png.

Print this image on white paper for the best results.

Tip: Leaving a white margin around the black border helps the detection algorithm.

2. Run the Main Engine
To start the standard AR application:
```bash
python ar.py
```

3. Run with Tracking (Smoother)
To run the version that uses Optical Flow (Lucas-Kanade method) for more stable tracking:
```bash
python ar_with_tracking.py
```
4. Camera Calibration (Optional)
If the 3D object looks distorted, you can recalibrate your specific webcam lens:
```bash
python camera_calib.py
```

Project Structure
ar.py: Main entry point. Handles webcam feed, detection, and rendering.

aruco_module.py: Custom implementation of the ArUco marker detection algorithm.

object_module.py: 3D renderer that parses and draws .obj models.

utils.py: Math utilities for calculating the rotation and translation vectors.

data/: Contains the reference marker and 3D assets.'
