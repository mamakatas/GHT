# Generalized Hough Transform with Scale and Rotation

This repository contains a Python implementation of the **Generalized Hough Transform (GHT)**. The algorithm is used to detect a specific template object within a target scene and it is robust to both scaling and rotation.

## Overview

The standard Hough Transform is typically used to find simple geometric shapes like lines and circles. The **Generalized Hough Transform** extends this to detect arbitrary, complex shapes. 

This notebook implements a GHT that actively handles discrete scales and rotations by voting in a 4-dimensional Hough space `(x, y, scale, rotation)`:
* **Scales handled:** `1.0`, `1.5`, `2.0`, `3.0`
* **Rotations handled:** Multiples of `15°` in the range `[0°, 15°, 30°, ..., 345°]`

### How it works:
1. **Edge Detection:** Applies the Canny Edge Detector to extract edges from both the template and scene images.
2. **R-Table Construction:** Maps the edge gradient directions of the template to displacement vectors pointing towards a chosen reference point (the center of the template).
3. **Voting:** For every edge point in the scene, the algorithm uses the R-table to cast votes for possible object centers across the discretized 4D space.
4. **Peak Detection:** The peaks in the Hough accumulator array indicate the most likely locations, scales, and rotations of the detected object.

## Requirements

To run the notebook, you will need Python 3.x and the following libraries:
* `numpy`
* `opencv-python` (cv2)
* `matplotlib`

You can install the dependencies via pip:
```bash
pip install numpy opencv-python matplotlib
