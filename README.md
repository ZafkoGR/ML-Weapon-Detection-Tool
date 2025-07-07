# 🔍 AI-Based Weapon Detection System (NASNetMobile)

This project presents a deep learning–based tool for real-time weapon detection in images. The system uses a multi-task learning model built on NASNetMobile to simultaneously classify the presence of weapons and localize them using bounding boxes—enabling fast, automated surveillance applications.

---

## 📘 Project Background

This weapon detection tool was developed as part of **Chapter 5: Practical AI in Cybersecurity** of my Master's thesis titled *Practical AI in Cyberwarfare and Cybersecurity*.

The project was implemented by **Konstantinos Zafeiropoulos** (Student ID: 20390293) at the  
**University of West Attica**  
**Faculty of Engineering, Department of Informatics and Computer Engineering**

> ⚠️ Although fully implemented and tested, this tool was **not included in the final thesis submission** due to time and scope constraints, and the decision to prioritize other tools with higher experimental impact and better alignment with the core thesis narrative.

---

## 1️⃣ Why AI is Needed

Manual video or image surveillance:
- Is slow and prone to human error  
- Cannot scale across thousands of frames or surveillance feeds  
- Lacks adaptability for different angles, lighting, and occlusions

✅ AI enables:
- Real-time detection and localization of weapons  
- Adaptive learning from diverse weapon types and scenes  
- Significantly faster response in critical situations like schools, airports, and public spaces

---

## 2️⃣ Can This Be Done Without AI?

Yes, but with serious limitations:

- Rule-based or classical image processing methods:
  - Fail under variable lighting, occlusion, or partial weapon visibility  
  - Cannot generalize across scenes or weapon types  
  - Lack real-time performance

✅ Conclusion: Only AI provides the flexibility, scalability, and accuracy needed for such a system.

---

## 3️⃣ AI Algorithm and Tool Architecture

### ✅ AI Algorithm Used
- **NASNetMobile** via **Transfer Learning**
  - Pretrained on ImageNet
  - Fine-tuned for dual-task: classification + bounding box regression

### 🧠 Tool Architecture

- **Input**: 300x300 pixel preprocessed images with normalized bounding boxes  
- **Model Backbone**: NASNetMobile (base frozen during training)  

#### Two Output Branches:
1. **Classification**  
   - Dense layers → Softmax → `Weapon` vs `No Weapon`

2. **Localization**  
   - Dense layers → Sigmoid → `xmin`, `ymin`, `xmax`, `ymax`

#### Loss Functions:
- `SparseCategoricalCrossentropy` for classification  
- `Mean Squared Error (MSE)` for bounding box coordinates

#### Training Strategy:
- Callbacks: `EarlyStopping`, `ReduceLROnPlateau`  
- Optimized for performance and training stability

---

## 4️⃣ AI Subcategory

✅ **Computer Vision**

Subdomains:
- Image Classification  
- Object Detection  
- Multi-task Learning (classification + regression)

---

## 5️⃣ Purpose & Social Impact

This tool aims to:
- Enhance **public safety** through fast, automated visual weapon detection  
- Minimize reliance on **manual surveillance** in real-time systems  
- Enable **rapid alerts** and prevent incidents in high-risk environments

✅ **Impact**: Faster detection → quicker response → saved lives and safer public spaces

---

## 6️⃣ Dataset Overview

The model was trained on a structured dataset containing both weapon and non-weapon images with bounding box labels:

| Field       | Description                                |
|-------------|--------------------------------------------|
| `file_name` | Image filename (e.g., `Defense123.jpg`)    |
| `width`     | Image width (300 px)                       |
| `height`    | Image height (300 px)                      |
| `class_num` | 1 = Weapon, 0 = No Weapon                  |
| `xmin`      | Left x-coordinate of bounding box          |
| `ymin`      | Top y-coordinate of bounding box           |
| `xmax`      | Right x-coordinate of bounding box         |
| `ymax`      | Bottom y-coordinate of bounding box        |

Dataset Stats:
- **603 weapon images** (`class_num = 1`)  
- **219 non-weapon images** (`class_num = 0`)  
- Combined from **XML-formatted annotations**

---
## 👤 Author

**Konstantinos Zafeiropoulos**  
Master's Thesis: *Practical AI in Cyberwarfare and Cybersecurity*  
University of West Attica – Department of Informatics and Computer Engineering
