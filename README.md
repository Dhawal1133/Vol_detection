# 📦 Volume Detection Using Depth Estimation (MiDaS)

This project uses the [MiDaS](https://github.com/isl-org/MiDaS) deep learning model to estimate depth from images and determine whether a container (like a box) is **full** or **half-full** by comparing the depth statistics.

---

## 🔧 Features

- 🔍 Depth estimation from 2D images using PyTorch and the MiDaS model.
- 📈 Statistical analysis of depth values in a Region of Interest (ROI).
- 🖼️ Saves a colorized depth map with ROI overlay.
- ✅ Compares depth values to infer volume status (e.g., full vs half-full).

---

## 🖼️ Example Results

| Input Image       | Depth Map Output        |
|-------------------|--------------------------|
| `box_full.jpeg`   | `output/full_depth_roi.png` |
| `box_half.jpeg`   | `output/half_depth_roi.png` |

---

## 📁 Project Structure

```
project/
│
├── images/
│   ├── box_full.jpeg
│   └── box_half.jpeg
│
├── output/
│   └── full_depth_roi.png
│   └── half_depth_roi.png
│
├── main.py
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/volume-detection.git
cd volume-detection
```

### 2. Install Dependencies

Make sure you have Python 3.8+ and install the required libraries:

```bash
pip install torch torchvision opencv-python numpy
```

> Ensure your system supports CUDA if you want to run it on GPU.

---

## ▶️ Run the Script

Update the image paths in `main.py`:

```python
image_paths = {
    "full": "images/box_full.jpeg",
    "half": "images/box_half.jpeg"
}
```

Then run:

```bash
python main.py
```

---

## 📊 Output Sample

```bash
--- FULL ---
ROI mean depth:   0.456
ROI median depth: 0.462
ROI min-max:      0.322 - 0.623
ROI std dev:      0.049
ROI shape: (480, 640)

--- HALF ---
ROI mean depth:   0.613
ROI median depth: 0.620
ROI min-max:      0.499 - 0.745
ROI std dev:      0.043
ROI shape: (480, 640)

=== RESULT ===
 Container is NOT full (detected lower fill level).
Mean depth difference: 0.157
```

---

## 📌 Notes

- The depth values are **relative**, not in physical units.
- You can adjust `roi_ratio` to focus on a specific part of the image if needed.
- Ideal for tasks like container monitoring, inventory checking, etc.

---

## 🧠 Credit

- [MiDaS Model](https://github.com/isl-org/MiDaS) by Intel ISL
- Developed using PyTorch and OpenCV

---

## 📜 License

This project is open-source and free to use under the MIT License.
