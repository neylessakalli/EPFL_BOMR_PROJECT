# Autonomous Thymio Navigation with Computer Vision

**EPFL, Basics of Mobile Robotics (MICRO-452), Group 08. Final grade: 6/6.**

A Thymio robot navigates autonomously to a goal on a map observed by an overhead camera. The system builds the map, plans the shortest collision-free path, and follows it. It also handles three disturbances: unexpected obstacles, being lifted and moved ("kidnapping"), and the camera being covered.

**Full technical report (design choices, results, figures):** [`report.ipynb`](report.ipynb)
**Demo videos:** [Google Drive](https://drive.google.com/drive/folders/1-yAhwDbuhh3VsZBCLwUvYRCsoxUqLP8g?usp=drive_link)

## Modules

| Module | Methods | Author |
|---|---|---|
| Vision (`classes/cv/`) | Camera calibration, ArUco detection, homography, obstacle contours (OpenCV) | Adrien Tarbouriech |
| Global navigation (`classes/gp/`) | Visibility graph, A* search, obstacle inflation | Jiri Blaha |
| Local navigation (`classes/local_avoidance.py`) | Reactive edge following with proximity sensors, proportional control | Neyl Essakalli |
| State estimation (`classes/ekf.py`) | Extended Kalman Filter fusing odometry and camera pose | Medina Colabrese |
| Motion control (`classes/motion_control.py`) | PID controller | Medina Colabrese |

Original team repository: [Medina-C/EPFL-BOMR-Project](https://github.com/Medina-C/EPFL-BOMR-Project)

## Running it

Requires Python 3.13, a Thymio II robot and a webcam above the map.

```bash
pip install -r requirements.txt
python main.py
```

If the camera does not open, change its index in `Vision()` in `main.py` (usually 1 or 2).

## Running the Demo

The demo can be ran by executing the `main.py` file. If camera isn't loading, change its index in `Vision()` (`main.py`, usually 1 or 2) or disable `cv.CAP_DSHOW` in `classes/cv/vision.py`. Make sure to go over `main.ipynb` first.
