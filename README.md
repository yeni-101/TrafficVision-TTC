# TrafficVision-TTC
Pilot study on the impact of bounding-box localization errors on Time-to-Collision estimation in pre-collision traffic scenes.

## Overview

This pilot study investigates how bounding-box localization errors propagate to Time-to-Collision (TTC) estimation in a pre-collision traffic scene.

## Research Question

How do different magnitudes and directions of bounding-box localization errors affect trajectory-based TTC estimation?

## Dataset

Nexar Dashcam Collision Prediction Dataset and Challenge. This pilot study uses Clip 006 from the training set.

## Method

1. Detect vehicles using YOLO11.
2. Track the target vehicle using ByteTrack.
3. Extract the bounding-box trajectory.
4. Estimate image scale using:

   s(t) = sqrt(w(t) * h(t))

5. Estimate TTC from temporal scale change.
6. Inject controlled localization errors:
   - Under-boxing
   - Over-boxing
   - IoU = 0.9, 0.7, 0.5
   - Duration = 3 frames
7. Compare perturbed TTC with baseline TTC.

## Evaluation
- Median Absolute TTC Deviation
- TTC Estimation Failure

## Preliminary Results

Increasing localization error severity generally produced larger TTC deviations and more estimation failures.

In this pilot clip, over-boxing produced larger TTC deviations than under-boxing at the same IoU level.

### TTC Absolute Deviation

![TTC Absolute Deviation](results/ttc_absolute_deviation.png)

### TTC Estimation Failures

![TTC Estimation Failures](results/ttc_estimation_failures.png)

## Limitations

This is a pilot study based on a single collision clip.
The TTC values are image-based estimates rather than physical ground-truth TTC values.

## Tools

- Python
- Ultralytics YOLO11
- ByteTrack
- Pandas
- NumPy
