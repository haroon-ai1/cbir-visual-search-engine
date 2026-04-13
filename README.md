# 🔍 Visual Search Engine — Content-Based Image Retrieval (CBIR) System

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?logo=opencv)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-In%20Progress%20(50%25)-orange)

> A university digital library visual search engine — search by image, not by keywords.

---

## 📌 Project Overview

This project is a **Content-Based Image Retrieval (CBIR)** system developed for the SZABIST University Computer Vision coursework. The system allows users to search an image archive by uploading a **query image** instead of relying on manual text keywords. It analyzes the raw visual content of the query and returns the most visually similar images from the **Wang Corel-1000 (Corel-1K)** benchmark dataset.

---

## ✅ Implemented Features (Midterm — ~50% Complete)

| # | Feature | Description |
|---|---------|-------------|
| 1 | **Image Loading & Preprocessing** | Loads images, resizes to `128×128`, applies CLAHE contrast enhancement |
| 2 | **Color Histogram Extraction** | Extracts a 96-dimensional HSV color histogram per image |
| 3 | **Edge-Based Feature Extraction** | Canny edge detection + Sobel gradients → edge density & orientation stats |
| 4 | **Feature Fusion** | Weighted concatenation: **70% Color + 30% Edge** |
| 5 | **Feature Index Building** | Pre-computes & saves all feature vectors as a NumPy matrix (`.npy`) |
| 6 | **Similarity Computation** | Ranks images using **Cosine Similarity** AND **Euclidean Distance** |
| 7 | **Top-5 Result Display** | Side-by-side Matplotlib visualization with similarity scores |
| 8 | **Performance Evaluation** | Measures retrieval accuracy using **Precision@5** across all 10 categories |

---

## 🗂️ Project Structure

```
cbir-visual-search-engine/
│
├── cbir_notebook.ipynb       # Main Jupyter Notebook (full pipeline)
├── feature_index.npy         # Pre-computed feature index (generated on first run)
├── labels.npy                # Corresponding image labels
├── cbir_output.png           # Sample output visualization (generated on run)
├── README.md                 # This file
│
└── dataset/                  # Wang Corel-1K dataset (not included — see below)
    ├── 0/                    # Africans
    ├── 1/                    # Beach
    ├── 2/                    # Buildings
    ├── 3/                    # Buses
    ├── 4/                    # Dinosaurs
    ├── 5/                    # Elephants
    ├── 6/                    # Flowers
    ├── 7/                    # Horses
    ├── 8/                    # Mountains
    └── 9/                    # Food
```

---

## ▶️ How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/cbir-visual-search-engine.git
cd cbir-visual-search-engine
```

### 2. Install Dependencies
```bash
pip install opencv-python numpy matplotlib scikit-learn scikit-image scipy
```

### 3. Download the Dataset
Download the **Wang Corel-1K** dataset and organize it into numbered folders (`0/` through `9/`) as shown in the project structure above.

### 4. Open the Notebook
```bash
jupyter notebook cbir_notebook.ipynb
```

### 5. Update the Dataset Path
In **Cell 2**, update the path variable to point to your local dataset folder:
```python
dataset_path = "C:/your/path/to/dataset"   # Windows
# dataset_path = "/home/user/dataset"      # Linux / Mac
```

### 6. Run All Cells (Top to Bottom)
The notebook will:
- Load and preprocess all images
- Extract color and edge features
- Build and save the feature index matrix
- Run a sample query image
- Display the **Top-5 results** as a visual grid (Cosine vs Euclidean)
- Calculate and print the **Precision@5** evaluation table

---

## 📊 Sample Output

```
Evaluating Precision@5 — 5 queries per category

Category        Cosine P@5    Euclidean P@5
--------------------------------------------
Africans              0.xx             0.xx
Beach                 0.xx             0.xx
Buildings             0.xx             0.xx
...
--------------------------------------------
OVERALL MEAN          0.xx             0.xx
```

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `opencv-python` | Image loading, resizing, CLAHE, Canny, Sobel |
| `numpy` | Feature vectors, matrix operations |
| `scikit-learn` | Cosine similarity computation |
| `scipy` | Euclidean distance computation |
| `matplotlib` | Result visualization |

---

## 👥 Collaborators

| Name | GitHub | Contributions |
|------|--------|---------------|
| **Muhammad Haroon** | [@haroon-ai1](https://github.com/haroon-ai1) | Preprocessing, Feature Fusion, Documentation |
| **Muneeb Ahmad** | [@MuneebAhmadOfficial](https://github.com/MuneebAhmadOfficial) | Color Histograms, Edge Extraction, Fusion Fixes |
| **[Third Member Name]** | [@Mibiol](https://github.com/Mibiol) | Query/Retrieval Logic, Visualizations, Precision Evaluation |

---

## 📋 Pending Features (Post-Midterm)

- [ ] Gabor texture feature extraction
- [ ] Interactive query UI (file upload widget)
- [ ] Support for custom user images outside the dataset
- [ ] Expanded dataset support

---

> 📚 *SZABIST University — Department of Robotics & AI | Computer Vision Lab | Spring 2026*
