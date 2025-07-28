# Real-Time American Sign Language Recognition using MediaPipe and Random Forest on Raspberry Pi

This project implements a real-time American Sign Language (ASL) recognition system using **MediaPipe** for hand landmark detection and **Random Forest** for classification. Designed for hardware deployment, the system runs efficiently on a **Raspberry Pi**, enabling low-cost, portable assistive technology.

---

## 📌 Abstract

Hand sign recognition plays a critical role in gesture-based interfaces and accessibility tools. This project presents a lightweight and accurate ASL recognition pipeline that processes static hand gestures using **21 hand landmarks** extracted via MediaPipe. Each landmark's 2D coordinates (x, y) are normalized, forming a 42-dimensional feature vector.

We evaluated five machine learning models:
- Random Forest (🏆 best performance – 94.21%)
- Logistic Regression (94.5%)
- Naive Bayes (84.78%)
- Decision Tree (59.89%)
- Angle-based approach (discarded due to poor accuracy)

The final model runs in real time on a **Raspberry Pi**, enabling sign language recognition in portable, low-power scenarios.

---

## 🧠 Methodology

### 1. Dataset Collection
- Custom dataset of **9,000+ images**, ~300 per ASL alphabet class.
- Collected using webcam + OpenCV + MediaPipe in various lighting/backgrounds.
- Data organized into folders per letter (`data/A/`, `data/B/`, etc.)

### 2. Feature Extraction
- MediaPipe extracts **21 hand landmarks** per frame.
- Each image converted into a 42-feature vector (x, y coordinates).
- Features are **normalized** for position/scale invariance.

### 3. Model Training
- Models trained and evaluated using cross-validation.
- Final Random Forest model saved as `.p5` for deployment.

### 4. Hardware Deployment
- Optimized and tested on **Raspberry Pi** (4B recommended).
- Supports real-time prediction using onboard camera or USB webcam.

---

## 🗂️ Repository Structure

```
asl-sign-recognition-raspberrypi/
│
├── data/                       # Image dataset (organized by class)
│   └── A/, B/, ..., Z/
│
├── models/                    # Saved CSV features & trained model
│   ├── data.csv
│   └── model.p5
│
├── notebooks/                 # Jupyter Notebooks for each stage
│   ├── 01_collect_img.ipynb       # Image collection
│   ├── 02_create_ds.ipynb         # Feature extraction & dataset creation
│   ├── 03_detection.ipynb         # Live hand detection
│   └── 04_model.ipynb             # Model training & evaluation
│
└── README.md
```

---

## 🚀 Setup Instructions

### Prerequisites
- Python 3.7+
- Raspberry Pi (tested on Pi 4)
- Required libraries:
  ```bash
  pip install mediapipe opencv-python pandas scikit-learn
  ```

### Run the System
1. Collect images: Run `01_collect_img.ipynb`
2. Build dataset: Run `02_create_ds.ipynb`
3. Train model: Run `04_model.ipynb`
4. Deploy on Pi: Follow `raspberry_pi/deployment_guide.md`

---

## 🔬 Results

| Model               | Accuracy    |
|--------------------|-------------|
| **Random Forest**  | 94.21%      |
| Logistic Regression| 94.5%       |
| Naive Bayes        | 84.78%      |
| Decision Tree      | 59.89%      |

---

## 🧩 Applications

- Assistive technology for Deaf or hard-of-hearing users
- Smart interfaces for gesture-based control
- Real-time recognition on embedded devices

---

## 📚 Keywords

American Sign Language, MediaPipe, Raspberry Pi, Random Forest, Gesture Recognition, Human-Computer Interaction, Real-Time ASL

---

📜 License
This project is licensed under the MIT License.
You are free to use, modify, and distribute this software with proper attribution.

🙌 Acknowledgements
This project was developed as part of an internship at The LNM Institute of Information Technology (LNMIIT), Jaipur.

#### Special thanks to:
Dr. Sandeep Saini </br>
Dean of Academic Affairs, LNMIIT </br>
For his constant guidance and support throughout the project.

#### Team Members:
- Aman Kaushal
- Prakhar Agrawal
- Manan Rathi
- Lov Chaudary

#### Libraries and Tools:
- MediaPipe by Google for hand landmark detection
- OpenCV for image processing and visualization
- scikit-learn for model training (Random Forest)
- Raspberry Pi for real-time deployment and testing
