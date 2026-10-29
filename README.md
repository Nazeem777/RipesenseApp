# 🌴 RipenessSense: Smartphone-Based Palm Oil Ripeness and Ganoderma Detection

> **Final Year Project (2024/2025)**[cite: 55]  
> **Faculty of Computer Science and Information Technology, Universiti Malaya**  
> **Author:** Muhammad Nazeem Bin Mohamed Thakubig (23006494)  
> **Supervisor:** Dr. Zati Hakim Azizul Hasan[cite: 1]  
> **Collaborative Initiative:** CoE Food Security and Intelligent Farming, Universiti Malaya

---

## 📖 Overview
**RipenessSense** is a unified, cross-platform mobile application designed to empower oil palm smallholders and plantation owners with low-cost, real-time Artificial Intelligence[cite: 6]. Traditional agricultural monitoring relies on expensive hyperspectral, thermal, or laser-scanning sensors, or is limited to single-bunch classification. RipenessSense solves these barriers by integrating **Fresh Fruit Bunch (FFB) Ripeness Classification** and **Ganoderma Boninense Disease Detection** into a single mobile framework running lightweight computer vision models on standard smartphone RGB cameras[cite: 6].

---

## ✨ Key Features & System Architecture

* **Dual AI Model Framework:** Combines two distinct AI pipelines within a single application (FFB Ripeness and Ganoderma stem/bark detection)[cite: 58].
* **Real-Time Edge Inference:** Runs entirely offline locally on mobile hardware using TFLite FP16 quantization, achieving sub-500ms latency without requiring internet or server dependencies[cite: 58].
* **Multi-Bunch & Environmental Robustness:** Capable of scanning multiple fruit bunches in a single frame and handling challenging outdoor lighting, shadows, and wet weather conditions[cite: 6, 63, 64].
* **Plantation Analytics Dashboard:** Real-time summary views tracking total scans, ripeness distributions (Abnormal, Flower, Ripe, Underripe, Unripe), and disease detection rates[cite: 48, 54].
* **Audit Trail & History Log:** Automatically logs scan results with timestamps, unique scan IDs, confidence score breakdowns, and image metadata[cite: 8, 48, 56].

---

## 📊 Performance & Evaluation Metrics

Both models underwent rigorous sprint benchmarking across multiple YOLO variants before full training on Google Colab (NVIDIA L4/RTX GPUs)[cite: 12, 28, 37]:

| Model Module | Selected Architecture | Target Metric | Achieved Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Module 1: Ripeness Classification** | YOLOv8-Small[cite: 22] | mAP@50 $\ge$ 0.70[cite: 7] | **76.66%** (mAP@50)[cite: 50] | ✅ **Exceeded**[cite: 12] |
| **Module 2: Ganoderma Detection** | YOLOv11-Small[cite: 38] | F1-Score $\ge$ 0.80[cite: 7] | **84.80%** (F1-Score)[cite: 51] | ✅ **Exceeded**[cite: 12] |

---

## 🛠️ Tech Stack & Tools

* **Programming Languages:** Python (Model Training), Dart (Flutter Mobile App)[cite: 13]
* **Deep Learning & Frameworks:** PyTorch, Ultralytics YOLOv8 / YOLOv11, TensorFlow Lite[cite: 13]
* **Dataset Management & Annotation:** Roboflow, Science Data Bank[cite: 12, 15, 33]
* **Development Environments:** Google Colab, VS Code, Jupyter Notebook[cite: 13]

---

## 📱 Mobile App UI & Workflow

1. **Starting Page & Dashboard:** Clean splash screen leading to the central dashboard overview displaying total scans, active metrics, and quick action buttons[cite: 55].
2. **Dual-Path Selection:** Users select either *Ripeness Classification* or *Ganoderma Detection* upon launching the camera or selecting an image from the gallery[cite: 55].
3. **Inference & Results:** Displays bounding boxes with per-object class labels, confidence scores (e.g., *Ripe 79%*, *Ganoderma Detected 82.2%*), and actionable agronomist recommendations[cite: 48, 64, 71].
4. **Error Handling & Edge Cases:** Built-in safeguards prompt users to retake photos when encountering blurry frames, low-light/night conditions, zero-object detections, or missing camera permissions[cite: 59, 61, 63].

---

## 🚀 Minimum Mobile Requirements

* **OS:** Android 8.0+[cite: 49]
* **RAM:** 4 GB minimum[cite: 49]
* **GPU:** FP16 support[cite: 49]
* **Storage:** ~100 MB free space[cite: 49]
* **Performance:** Optimized for mid-range mobile hardware (~3–5 FPS local inference)[cite: 46, 49]

---

## 📂 Repository Structure

```text
RipenessSense/
├── datasets/                 # Training and validation dataset configurations (YAML)
├── models/                   # PyTorch checkpoints and exported TFLite weights (.tflite)
├── mobile_app/               # Flutter cross-platform source code (UI, Providers, Screens)
├── notebooks/                # Google Colab training & sprint benchmark notebooks
└── README.md
