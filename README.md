# 💡 Vanishing Point Detection in OpenCV **Canny + Hough Transform + RANSAC** (Python Tutorial)
---
[![main branch](https://img.shields.io/badge/branch-main-red?style=flat&logo=git&logoColor=white)](https://github.com/RH-NAYM/OpenCV-Vanishing-Point-Detection.ipynb/tree/main)
#
<p align="center">
  <a href="https://opencv.org/" target="_blank">
    <img src="https://img.shields.io/badge/OpenCV-Computer%20Vision-green?logo=opencv&logoColor=white">
  </a>
  <a href="https://www.python.org/" target="_blank">
    <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white">
  </a>
  <a href="https://jupyter.org/" target="_blank">
    <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white">
  </a>
  <a href="https://numpy.org/" target="_blank">
    <img src="https://img.shields.io/badge/Numpy-Numerical-lightblue?logo=numpy&logoColor=white">
  </a>
  <a href="https://matplotlib.org/" target="_blank">
    <img src="https://img_0.png">
  </a>
</p>



# 📌 Overview

This project demonstrates a `classical computer vision pipeline` for detecting `vanishing points` in images with strong perspective (`roads`, `corridors`, `railways`, `architecture` etc.).

**The method combines three fundamental techniques:**
1. `Canny` edge detection
2. `Probabilistic Hough Transform` for line segment detection
3. `RANSAC` for robust estimation of the vanishing point from noisy line intersections

**Despite being a non-deep-learning approach, this pipeline remains very useful in 2025 for:**
- interpretable results
- low computational requirements
- good initialization for SLAM / camera calibration / 3D reconstruction
- environments where deep models are too heavy or not desirable

---

# 📁 Project Structure

```bash
.
├── 📓 OpenCV-Vanishing-Point-Detection.ipynb       # Main notebook with full pipeline
├── 📘 README.md                                    # This file
├── 📦 requirements.txt                             # Python dependencies
├── 🖼️ testImage.jpg                                # Example test image (or download your own)
└── 🛠️ tools                                        # (optional) Utility functions
    └── tools.py                                    # Image loading & visualization helpers
```

# 📋 Table of Contents (Notebook Sections)
---
```bash
1. Introduction to Vanishing Points & Perspective Geometry
2. Loading and Preprocessing the Image
3. Edge Detection with Canny
4. Line Segment Detection using Probabilistic Hough Transform
5. Why naive line intersection fails
6. Robust Vanishing Point Estimation with RANSAC
7. Result Visualization & Inlier Highlighting
8. Parameter Tuning Guide
9. Common Failure Cases & Improvements
```

# 🧠 What You’ll Learn
---
- Geometric meaning of vanishing points in perspective projection
- Why edge quality dramatically affects the final result
- How to tune Canny thresholds for different scene types
- Most important Hough parameters and their impact
- How `RANSAC` handles noisy and outlier lines
- Practical strategies when the vanishing point is outside the image

# 🛠️ Technologies Used
---
- `Python 3.x`
- `OpenCV` for Vanishing Point Detection
- `NumPy` for array operations
- `Matplotlib` for visualization
- `Jupyter Notebook` for interactive experimentation


# 📦 Installation
---
## 1️⃣ Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate    # Linux / macOS
venv\Scripts\activate       # Windows
```
## 2️⃣ Install dependencies
```bash
pip install -r requirements.txt
```
# 🚀 How to Run
---
**Option 1: Jupyter Notebook (Local)**
- Install Jupyter if needed: `pip install notebook`.
- Launch Jupyter: `jupyter notebook`.
- Open `OpenCV-Vanishing-Point-Detection.ipynb` and run cells sequentially.
    - Notebook will automatically download a placeholder image if testImage.jpg is missing.


**Option 2: Google Colab**
- Upload `OpenCV-Vanishing-Point-Detection.ipynb` to Colab.
- Install dependencies: `!pip install -r requirements.txt`.
- Run all cells for interactive demonstrations.

Tip: The notebook works best with images containing strong perspective lines
(`roads`, `railways`, `long corridors`, `buildings` with parallel lines).
**Recommended test images:**
- Highway / road perspective
- Train tracks
- Building interiors with long hallways
- City streets with tall buildings


# ✅ Quick Parameter Tuning Reference
- `Stage`,`Parameter`,`Typical Range`                   ::  Advice / When to change
- `Canny`,`low/high threshold`,`50–120 / 120–250`       ::  Increase both in noisy images, decrease in low-contrast
- `Canny`,`apertureSize`,`3` / `5`                      ::  `5` for thicker, more continuous edges
- `HoughP`,`threshold`,`60–150`                         ::  Higher = fewer but more confident lines
- `HoughP`,`minLineLength`,`60–200`                     ::  Increase to remove short fragments
- `HoughP`,`maxLineGap`,`8–30`                          ::  Higher = connects broken lines better
- `RANSAC`,`inlier threshold (px)`,`3–10`               ::  Higher tolerance for noisy scenes
- `RANSAC`,`iterations`,`800–3000`                      ::  More iterations = higher chance to find good model

# 🍴 Real-World Applications (still relevant in 2025)
- `Lane detection` initialization in autonomous driving
- Camera `self-calibration` / `focal length` estimation
- `Augmented Reality` marker-less `tracking` initialization
- `Architectural analysis` & `rectification`
- `Robotics` — `corridor` / `hallway navigation`
- Low-compute fallback method when deep models are not available

# 📝 Possible Improvements & Next Steps
- Line clustering by angle → detect multiple vanishing points (_Manhattan world_)
- Use `LSD` (_Line Segment Detector_) instead of Hough
- Add weighted `RANSAC` (_longer lines = more important_)
- Filter lines by orientation before `RANSAC`
- Post-processing refine VP with least-squares on inliers

# 📌 Final Note
Even in the era of deep learning-based methods (_DeepVP, HorizonNet, etc._),
the `Canny` + `Hough` + `RANSAC` pipeline remains one of the most interpretable, fast and resource-efficient solutions for many real-world perspective geometry tasks.
