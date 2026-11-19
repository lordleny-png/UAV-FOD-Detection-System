# UAV-FOD-Detection-System
AI-powered Foreign Object Debris detection for airport runway inspection using YOLO11 and UAV technology.
# UAV-Based Foreign Object Debris (FOD) Detection System

**AI-Powered Airport Runway Inspection | Computer Vision | YOLO11 | UAV Technology**

## 1. Project Overview

This project aims to develop an artificial intelligence system capable of detecting and classifying Foreign Object Debris (FOD) on airport runways using computer vision.

Foreign Object Debris includes objects such as screws, bolts, stones, metal fragments, plastic materials, tools, and other objects that may create safety risks for aircraft.

The long-term objective is to integrate an AI-based detection model into an Unmanned Aerial Vehicle (UAV) to support automated runway inspection.

**Current development stage:** Dataset preparation, model training, and validation.

## 2. Project Objectives

- Detect foreign objects in images using deep learning.
- Classify objects into 31 FOD categories.
- Explore UAV-based runway inspection.
- Evaluate object detection performance.
- Prepare the model for future embedded deployment and real-time inference.

## 3. Dataset Description

The project uses the FODPascalVOCFormat V2.1 dataset.

| Characteristic | Description |
|---|---|
| Original images | 33,793 |
| Object categories | 31 |
| Total annotated objects (dataset summary) | 34,472 |
| Original annotation format | Pascal VOC (XML) |
| Converted annotation format | YOLO (TXT) |

### Dataset Split

| Subset | Images |
|---|---:|
| Training | 20,235 |
| Validation | 5,059 |
| Testing | 8,429 |
| **Total in splits** | **33,723** |

The dataset preparation process included:
- Duplicate detection and removal.
- Train, validation, and test separation.
- XML-to-YOLO annotation conversion.
- Bounding-box normalization and validation.
- Dataset configuration using `data.yaml`.

The complete dataset is not included in this repository.

## 4. Model Architecture and Training

The object detection model was developed using **YOLO11n**, a lightweight YOLO architecture suitable for exploring efficient object detection.

### Training Configuration

| Parameter | Value |
|---|---|
| Model | YOLO11n |
| Number of classes | 31 |
| Epochs | 50 |
| Image size | 640 × 640 |
| Batch size | 16 |
| Pretrained weights | YOLO11n |
| GPU | NVIDIA Tesla T4 |
| Framework | Ultralytics / PyTorch |
| Environment | Google Colab |

## 5. Validation Results

The trained model achieved the following results on the validation dataset:

| Metric | Result |
|---|---:|
| Precision | 99.7% |
| Recall | 99.3% |
| mAP@50 | 99.3% |
| mAP@50-95 | 91.6% |

**Important:** These are validation results, not final test results. Independent evaluation on the test dataset is still required to estimate generalization performance.

## 6. Repository Structure

```text
UAV-FOD-Detection-System/
│
├── README.md
├── README_FR.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── UAV_FOD_Detection_Training.ipynb
│
├── models/
│   ├── best.pt
│   └── README.md
│
├── results/
│   ├── training/
│   ├── evaluation/
│   └── predictions/
│
├── docs/
│   ├── project_overview.md
│   └── dataset_information.md
│
└── assets/
    ├── images/
    └── screenshots/
```

## 7. Technologies Used

- Python
- PyTorch
- Ultralytics YOLO11
- OpenCV
- NumPy
- Matplotlib
- Google Colab

## 8. Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/UAV-FOD-Detection-System.git
cd UAV-FOD-Detection-System
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

## 9. Run Inference

After installing the dependencies and making the model weights available:

```python
from ultralytics import YOLO

model = YOLO("models/best.pt")

results = model.predict(
    source="path/to/your/image.jpg",
    conf=0.25,
    imgsz=640,
    save=True
)
```

Replace the image path with your own test image.

## 10. Project Roadmap

- [x] Dataset exploration
- [x] Dataset cleaning and preparation
- [x] Pascal VOC to YOLO annotation conversion
- [x] YOLO11n model training
- [x] Validation evaluation
- [ ] Independent test evaluation
- [ ] Visual prediction analysis
- [ ] Evaluation on real UAV-acquired runway images
- [ ] Model optimization for embedded hardware
- [ ] UAV integration
- [ ] Real-time detection dashboard

## 11. Future Development

Future work will focus on:
- Testing the model on images captured from different drone altitudes.
- Improving the detection of small objects.
- Evaluating robustness under different lighting and environmental conditions.
- Exploring deployment on embedded platforms such as NVIDIA Jetson.
- Integrating detection results into a monitoring dashboard.

## 12. Safety and Limitations

This project is an experimental research and engineering prototype. High validation metrics do not establish operational reliability.

The model has not yet been validated under real airport operating conditions or approved for aviation safety decisions. Human inspection and established airport safety procedures remain essential.

## 13. Author

**NYMBUSSEDE LENY NAPALA**

Data Analytics | Machine Learning | Computer Vision

GitHub: https://github.com/lordleny-png

---

*This project explores the application of artificial intelligence and UAV technology to support airport runway inspection and aviation safety.*

