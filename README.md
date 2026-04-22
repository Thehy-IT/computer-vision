# Computer Vision & Image Processing (CVIP) Portfolio

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.7+-green.svg)](https://opencv.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)](https://pytorch.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.12+-orange.svg)](https://wwww.tensorflow.org/)

A comprehensive collection of Computer Vision implementations ranging from fundamental image processing to state-of-the-art Deep Learning architectures. This project serves as a practical laboratory series covering classical algorithms, frequency-domain analysis, and modern facial recognition systems.

---

## Project Information

- **Lead Developer:** Huỳnh Thế Hy
- **Student ID:** 051205009083
- **Collaborators:** Nghiêm Đức Thuận, Đào Thiện Nhân, Tạ Nguyễn Quốc Triệu, Hoàng Phú, Thanh Tân.
- **Institution:** UTH (University of Transport and Communications)

---

## Key Technical Modules

### 1. Fundamental Image Engineering (`Lab1`, `Lab2.1`)

- **Color Space Dynamics:** Implementation of RGB, HSV, and Grayscale transformations and their mathematical foundations.
- **Spatial Domain Filtering:**
  - Point operators: Brightness, Contrast adjustment, Image Negation, and Thresholding.
  - Linear filters: Mean (Box), Gaussian Blur for noise reduction, and Laplacian/Sobel for sharpening.

### 2. Advanced Feature Extraction (`Lab2.2`, `photo_matching`)

- **Canny Edge Detection Pipeline:** Complete implementation including Gaussian smoothing, Gradient calculation (Sobel), Non-Maximum Suppression (NMS), and Hysteresis Thresholding.
- **Traditional Feature Matchers:**
  - **ORB (Oriented FAST and Rotated BRIEF):** Efficient and robust keypoint detection.
  - **SIFT (Scale-Invariant Feature Transform):** Scale and rotation invariant matching.
  - **RANSAC Optimization:** Improving match quality by eliminating outliers.

### 3. Frequency Domain & Similarity Analysis (`Lab3.1`)

- **Discrete Wavelet Transform (DWT):** Signal decomposition using PyWavelets.
- **Image Hashing (wHash):** Converting spatial information into compact bitstrings for rapid similarity lookup.
- **Metric Evaluation:** Performance analysis using **Hamming Distance**, **ROC Curves**, and **AUC** scores.

### 4. Deep Learning & Facial Recognition (`Lab3.2`, `photo_matching`)

- **Siamese Networks:** Built with **PyTorch** for learning similarity metrics via Contrastive Loss.
- **Modern Face Recognition Pipeline:**
  - **MTCNN:** Multi-task Cascaded Convolutional Networks for high-accuracy face detection and landmarking.
  - **FaceNet:** Deep learning model for generating 512-dimensional facial embeddings.
  - **Vector Similarity:** Using Cosine Similarity for identity verification.

---

## Project Structure

```text
computer-vision/
├── data/                 # Multi-modal datasets
│   ├── input/            # Raw source images
│   ├── processed/        # Algorithm outputs
│   ├── DWT/              # Data for Wavelet Analysis
│   ├── faceID/           # Samples for facial recognition
│   └── photo_matching/   # Benchmarks for ORB/SIFT/Siamese
├── docs/                 # Theoretical documentation & Lecture notes
├── notebooks/            # Core implementation (Jupyter)
│   ├── Lab1.ipynb        # Basics & Color Spaces
│   ├── Lab2.1.ipynb      # Spatial Filtering & Enhancement
│   ├── Lab2.2.ipynb      # Canny & Hough Transform
│   ├── Lab3.1.ipynb      # DWT & Similarity Evaluation
│   ├── Lab3.2.ipynb      # FaceNet & MTCNN Integration
│   └── photo_matching.ipynb # Traditional vs. DL Matching
├── requirements.txt      # Dependency manifest
└── README.md             # Project documentation
```

---

## Setup & Installation

### Prerequisites

- Python 3.9 or higher
- (Optional) CUDA-enabled GPU for PyTorch/TensorFlow acceleration

### 1. Environment Preparation

```bash
# Clone the repository
git clone https://github.com/your-repo/computer-vision.git
cd computer-vision

# Create a virtual environment
python -m venv venv

# Activate venv
# On Windows:
.\venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate
```

### 2. Dependency Installation

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 3. Launching the Workspace

```bash
jupyter notebook
```

Navigate to the `notebooks/` directory to begin exploration.

---

## Performance & Results

The project includes automated evaluation scripts to assess the robustness of algorithms:

- **Precision/Recall Analysis** for edge detectors.
- **ROC/AUC Curves** for wHash-based image similarity.
- **Confusion Matrices** for facial recognition benchmarks.

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.
