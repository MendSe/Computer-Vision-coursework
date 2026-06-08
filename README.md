# Computer Vision Course Projects

This repository contains my assignments and project work for the **Computer Vision** course (Spring 2026) taught by Prof. Ohad Fried at Reichman University.
The project documents my work across multiple assignments covering the core pipeline of classical computer vision: image filtering, feature detection, line detection, stereo matching, 3D reconstruction, camera geometry, epipolar geometry, and robust feature-based estimation.

The repository is organized as a sequence of Jupyter notebooks, with each homework building on the previous one. The work emphasizes implementing core algorithms from first principles, analyzing parameter sensitivity, and validating results on both synthetic data and real images.

## Why this repository is relevant

This project demonstrates practical experience with:

- **Image processing fundamentals** using NumPy, OpenCV, and SciPy
- **Classical feature extraction** including gradients, Harris corners, and patch descriptors
- **Geometric computer vision** including projection matrices, triangulation, stereo disparity, and epipolar geometry
- **Robust matching pipelines** using SSD, NCC, SIFT, and RANSAC/LMedS-style estimation
- **Experimental analysis** through controlled synthetic tests and real-world image evaluation
- **Notebook-based technical communication**, including visualizations, intermediate diagnostics, and result interpretation

## Repository structure

```text
Computer Vision Course/
|-- hw0/
|   |-- hw0.ipynb
|   `-- Yami.jpg
|-- hw1/
|   |-- hw1_ID_ID.ipynb
|   `-- image assets for convolution and corner-detection experiments
|-- hw2/
|   |-- hw2_ID_ID.ipynb
|   |-- synthetic_lines.png
|   `-- images/
|-- hw3/
|   |-- hw3.ipynb
|   |-- left.tif / right.tif
|   |-- epipolarLines1.png
|   `-- images/
|-- LICENSE
`-- README.md
```

## Project overview by assignment

### HW0: Python, NumPy, and image-processing foundations

`hw0/hw0.ipynb` is a foundation notebook used to establish the tools and programming patterns required for later assignments.

Topics covered:

- Python basics and control flow
- NumPy array creation, indexing, slicing, and vectorized operations
- Statistical and matrix operations
- Matplotlib plotting, including 2D and 3D visualization
- Basic image loading, display, thresholding, and connected-components analysis
- A custom `gaussian_2d` function for working with Gaussian surfaces

This notebook serves as the base layer for the more advanced work in the later homeworks.

### HW1: Convolutions and Harris corner detection

`hw1/hw1_ID_ID.ipynb` focuses on low-level image filtering and feature detection.

Main components:

- Manual convolution operations
- Gaussian smoothing and Gaussian derivative filters
- Gradient computation in the x/y directions
- Harris corner detector implementation from scratch
- Non-maximum style neighborhood reasoning using local filtering
- Comparative experiments across a range of synthetic and real images

Implemented functions include:

- `convolutionMask`
- `gaussian1D`
- `gaussian1D_partialdiff`
- `deriv_gauss_xy`
- `grad_xy`
- `gaussian2D`
- `harris_corner`

Evaluation in this notebook explores how detection quality changes as parameters are varied, including:

- smoothing sigma
- neighborhood sigma
- threshold
- corner density controls

The experiments use diverse images such as buildings, checkerboards, office scenes, flags, and textured surfaces to expose both strengths and failure modes of the detector.

### HW2: Hough-style line detection, patch matching, and stereo reconstruction

`hw2/hw2_ID_ID.ipynb` expands the project into mid-level vision tasks.

#### Section A: Straight-line detection

This part implements a straight-line detection pipeline, including:

- Hough-style accumulator construction
- line parameter voting
- synthetic line generation for controlled testing
- overlay and visualization of detected lines
- experiments on the effect of radius and angle resolution
- analysis of lines supported by large numbers of pixels

Relevant functions:

- `H_matrix`
- `list_lines`
- `display_lines`
- `straight_lines`
- `create_synthetic_line_image`
- `create_lines_overlay`

#### Section B: Patch matching and local descriptors

This section studies local matching between image points using multiple descriptors and similarity measures.

Implemented ideas include:

- patch extraction and normalization
- grayscale patch descriptors
- histogram-based patch descriptors
- gradient-based descriptors
- SSD and NCC similarity functions
- vectorized matching implementations
- corner-based interest point selection
- diagnostic visualization of good and bad matches

Relevant functions:

- `SSD`, `NCC`
- `patch_from_im`, `normalize_patch`
- `grey_descriptor`
- `hist_patch_im`
- `gradient`, `hist_gradient`
- `vectorized_SSD`, `vectorized_NCC`
- `compute_corners`
- `compute_descriptor`
- `build_descriptor_matrix`
- `match_points`
- `draw_matches`
- `run_matching_experiment`

#### Section C: Extracting 3D structure

The final section introduces stereo vision and 3D recovery:

- disparity map computation
- vectorized disparity estimation
- depth-map visualization
- 3D point-cloud generation from stereo correspondences

Relevant functions:

- `compute_disparity_map`
- `compute_disparity_map_vec`
- `compute_3d_structure`
- `display_disparity_map`
- `display_depth_map`
- `plot_3d_point_cloud`

This assignment connects local correspondence methods to full 3D scene interpretation.

### HW3: Camera projection, triangulation, epipolar geometry, and robust estimation

`hw3/hw3.ipynb` focuses on multi-view geometry and feature-based estimation.

#### Section A: Projection and triangulation

This section covers:

- camera projection with homogeneous coordinates
- projection matrix reasoning
- triangulation from multiple image views
- visualization of projected points in paired images

Relevant functions:

- `proj`
- `skew`

#### Section B: Epipolar geometry

This part works with:

- the fundamental matrix
- epipoles
- epipolar lines
- visualization of geometric relationships between corresponding points in stereo images

Relevant functions:

- `line_endpoints`
- `epipoles_from_F`

#### Section C: SIFT and robust estimation with LMedS/RANSAC-style logic

The final section applies feature-based matching on user-captured image pairs and estimates epipolar geometry robustly.

Highlights:

- SIFT-based keypoint matching
- robust estimation of the fundamental matrix
- outlier handling through robust model fitting
- application to real images captured independently rather than only course-provided examples

Relevant function:

- `compute_F_with_sift_lmeds`

This assignment demonstrates a transition from hand-built local methods to modern feature pipelines combined with geometric verification.

## Technical stack

The notebooks primarily use:

- **Python**
- **NumPy**
- **OpenCV (`cv2`)**
- **SciPy**
- **Matplotlib**
- **Pillow**
- **Jupyter Notebook**

## Skills demonstrated

From a software and research perspective, this repository shows:

- translating mathematical vision concepts into working code
- implementing algorithms without relying entirely on black-box library calls
- building reusable helper functions for visualization and analysis
- comparing algorithm behavior under different parameter choices
- using synthetic data to verify correctness before testing on real images
- presenting results clearly through plots, overlays, and notebook narratives

## How to run

### Option 1: Open the notebooks directly

If you already have a Python scientific environment installed:

1. Clone the repository
2. Launch Jupyter Notebook or JupyterLab
3. Open any notebook under `hw0/`, `hw1/`, `hw2/`, or `hw3/`
4. Run the cells in order

### Option 2: Create a fresh environment

```bash
pip install numpy opencv-python scipy matplotlib pillow jupyter
```

Then launch:

```bash
jupyter notebook
```

