# DATA SCIENCE INTERNSHIP REPORT

## Intern Details

| Field | Details |
|-------|---------|
| **Name** | Vishal Kumar Sharma |
| **Internship Period** | 13/03/2026 to 13/05/2026 |
| **Organization** | Null Class |
| **Project Domain** | Data Science, Computer Vision & Machine Learning |

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Background](#2-background)
3. [Learning Objectives](#3-learning-objectives)
4. [Activities and Tasks](#4-activities-and-tasks)
5. [Skills and Competencies](#5-skills-and-competencies)
6. [Feedback and Evidence](#6-feedback-and-evidence)
7. [Challenges and Solutions](#7-challenges-and-solutions)
8. [Outcomes and Impact](#8-outcomes-and-impact)
9. [Conclusion](#9-conclusion)
10. [Appendices](#appendices)

---

## 1. Introduction

This report presents a comprehensive overview of my internship experience in the field of Data Science, Computer Vision & Machine Learning. During this internship period, I was assigned six distinct projects focused on real-world applications of deep learning, computer vision, and automated systems. These projects challenged me to apply theoretical knowledge to practical scenarios while developing production-ready machine learning models.

**The primary focus areas included:**

- Face recognition and emotion detection systems
- Object detection and classification using YOLO
- Real-time video processing and analysis
- GUI development for machine learning applications
- Time-based automated systems

This internship provided hands-on experience with industry-standard tools and frameworks including OpenCV, TensorFlow, PyTorch, YOLO, and various Python libraries for data processing and visualization.

---

## 2. Background

### 2.1 Domain Context

Data Science, Computer Vision and Machine Learning are rapidly evolving fields with applications across education, security, wildlife conservation, automotive safety, and demographic analysis. The projects undertaken during this internship address real-world challenges in these domains:

- **Educational Technology:** Automated attendance systems reduce administrative burden and improve accuracy
- **Wildlife Conservation:** Animal detection aids in monitoring endangered species
- **Road Safety:** Drowsiness detection prevents accidents
- **Accessibility:** Sign language recognition enables better communication
- **Traffic Management:** Vehicle analysis optimizes traffic flow

### 2.2 Technologies Used

**Programming Languages:**
- Python 3.8+

**Machine Learning Frameworks:**
- TensorFlow/Keras
- PyTorch
- Ultralytics YOLO (v8)
- OpenCV (cv2)

**Libraries and Tools:**
- face_recognition (dlib-based)
- FER (Facial Emotion Recognition)
- MediaPipe (for pose/hand tracking)
- pandas, numpy (data processing)
- tkinter/PyQt5 (GUI development)
- pickle (model serialization)

**Development Environment:**
- Jupyter Notebook for experimentation
- VS Code for production code
- Git for version control

---

## 3. Learning Objectives

### 3.1 Technical Objectives

**Master Computer Vision Fundamentals**
- Understand image preprocessing techniques
- Learn face detection and recognition algorithms
- Implement object detection using state-of-the-art models

**Develop Deep Learning Expertise**
- Train custom CNN models for emotion recognition
- Fine-tune pre-trained models (YOLO, VGG)
- Optimize model performance for real-time applications

**Build Production-Ready Systems**
- Create robust error handling mechanisms
- Implement time-based automated workflows
- Develop user-friendly interfaces

**Data Management Skills**
- Collect and annotate custom datasets
- Handle data augmentation and preprocessing
- Manage model versioning and serialization

### 3.2 Soft Skills Objectives

- Time management for multiple concurrent projects
- Problem-solving under technical constraints
- Documentation and reporting skills
- Self-directed learning and research

---

## 4. Activities and Tasks

### Project 1: Attendance System with Emotion Detection

**Duration:** 1 and half weeks

#### Activities

**Data Collection Phase**
- Collected 50+ facial images per student from multiple angles
- Ensured diverse lighting conditions and expressions
- Organized dataset into structured directories

**Model Development**
- Generated 128-dimensional face encodings using face_recognition library
- Integrated FER library for emotion detection
- Implemented real-time face matching algorithm with 0.6 tolerance threshold

**System Features Implementation**
- Time-based activation (9:30 AM - 10:00 AM configurable window)
- Real-time emotion detection (7 emotions: Happy, Sad, Angry, Neutral, etc.)
- Automatic attendance marking with duplicate prevention
- CSV export with timestamp and emotion data

#### Deliverables
- Working attendance system with >85% face recognition accuracy
- CSV attendance records with student name, status, emotion, and timestamp
- Complete source code with documentation

---

### Project 2: Animal Detection and Classification

**Duration:** 1.5 weeks

#### Activities

**Model Selection and Training**
- Evaluated YOLO v5/v8 for real-time detection
- Used custom trained weights (20 animal classes)

**Carnivore Detection Logic**
- Implemented classification of carnivores vs. herbivores
- Red bounding boxes for carnivorous animals
- Pop-up alert system for carnivore count

**GUI Development**
- Created tkinter-based interface with image/video upload
- Implemented side-by-side preview (original vs. detected)
- Added progress indicators and result display

#### Deliverables
- GUI application supporting both image and video input
- Carnivore detection with visual alerts
- Processed output videos with bounding boxes

---

### Project 3: Drowsiness Detection System

#### Activities
- Eye aspect ratio (EAR) calculation for drowsiness detection
- Multi-person detection in single frame
- Age prediction integration using deep learning models
- Red marking for sleeping individuals with age display

---

### Project 4: Nationality and Attribute Prediction

#### Activities
- Nationality classification using facial features
- Conditional attribute prediction (age, dress color, emotion)
- Multi-task learning model architecture
- GUI with result display section

---

### Project 5: Sign Language Recognition

**Duration:** 1.5 weeks

#### Overview

Built a real-time sign language detection system that recognizes 9 hand gestures using MediaPipe for hand landmark extraction and a Random Forest classifier for prediction. The system runs on live webcam feed and displays a live confidence chart alongside the detection window.

**Signs Supported:** Hello, Thank You, Yes, No, I Love You, Please, Sorry, Eat, Drink

#### Activities

**Data Collection Phase** (`collect_images.py`)
- Captured 50 images per sign using webcam — total 450 images across 9 classes
- Images saved in structured folders: `collected_images/<sign_name>/`
- Added a 3-second countdown before each sign to ensure clean captures
- Used OpenCV to display live frame count during collection

**Feature Extraction & Model Training** (`train_model.py`)
- Used MediaPipe Hand Landmarker (`hand_landmarker.task`) to detect 21 hand landmarks per image
- Each landmark gives x and y coordinates — total 42 features per image
- Landmarks are position-independent (normalized 0 to 1) so hand position on screen doesn't affect prediction
- Trained a Random Forest Classifier (100 estimators) on extracted features
- 80/20 train-test split using sklearn's `train_test_split`
- Model serialized using pickle → saved as `models/sign_model.pkl`

**Real-Time Detection** (`detect_realtime.py`)
- Live webcam feed processed at ~30 FPS using MediaPipe VIDEO running mode
- Hand landmarks drawn on screen with connections across all 5 fingers and palm
- Each frame: 42 features extracted → passed to Random Forest → prediction + confidence displayed
- Implemented a live matplotlib confidence chart (dark themed, horizontal bar chart)
  - Runs as a separate popup window alongside webcam
  - Updates every 300ms to avoid slowing down the webcam feed
  - Predicted sign bar highlighted in green, all others in grey
- Predicted sign and confidence % shown on top of webcam window

#### Pipeline Summary

```
collect_images.py → train_model.py → detect_realtime.py
     (capture)          (train)            (detect)
```

#### Deliverables
- `collect_images.py` — automated image collection script
- `train_model.py` — landmark extraction + model training
- `detect_realtime.py` — real-time detection with live confidence visualization
- `models/sign_model.pkl` — trained Random Forest model
- **Recognition Accuracy:** 84%
- **Processing Speed:** ~30 FPS real-time

#### Key Technical Decisions

> **Why Random Forest over CNN?**
> Images are not directly fed to the model — only 42 landmark coordinates are used as features. Since the input is structured tabular data (not raw pixels), Random Forest performs well and is much faster to train than a CNN. It also works with small datasets (50 images per sign).

> **Why MediaPipe Landmarks instead of raw images?**
> Raw image classifiers are sensitive to background, lighting, and skin tone. Landmark-based approach extracts only hand geometry, making it robust across different environments and users.

---

### Project 6: Car Color Detection and Counting

#### Activities
- Vehicle detection using YOLO
- Color classification using color space analysis
- People counting at traffic signals
- Color-coded bounding boxes (red for blue cars, blue for others)

---

## 5. Skills and Competencies

### 5.1 Technical Skills Acquired

**Computer Vision:**
-  Face detection using Haar Cascades and HOG
-  Face recognition using 128-d embeddings
-  Object detection with YOLO architecture
-  Image preprocessing (resizing, normalization, augmentation)
-  Real-time video stream processing

**Machine Learning:**
-  CNN architecture design and training
-  Transfer learning and fine-tuning
-  Model evaluation metrics (precision, recall, F1-score)
-  Hyperparameter tuning
-  Handling class imbalance

**Software Development:**
-  Python advanced programming
-  GUI development with tkinter
- File I/O and data serialization (pickle, CSV)
-  Exception handling and error management
-  Code organization and modularity

**Tools & Frameworks:**
-  OpenCV for image processing
-  YOLO for object detection
-  face_recognition library
-  TensorFlow/Keras for deep learning
-  pandas for data manipulation

### 5.2 Soft Skills Developed

- **Problem-Solving:** Debugged complex issues like poor lighting affecting face recognition
- **Research Skills:** Evaluated multiple approaches (YOLO vs. R-CNN vs. SSD)
- **Time Management:** Balanced six concurrent projects with daily reporting
- **Documentation:** Maintained clear code comments and user guides
- **Adaptability:** Switched approaches when initial solutions failed

---

## 6. Feedback and Evidence

### 6.1 Self-Assessment

**Strengths:**
- Successfully implemented all six required projects
- Achieved >85% accuracy in face recognition system
- Developed clean, modular, and reusable code
- Met all project deadlines

**Areas for Improvement:**
- Initial difficulty with GPU optimization for YOLO training
- GUI design could be more polished
- Model deployment knowledge needs enhancement

### 6.2 Evidence of Work

**Project Outputs:**
-  Attendance CSV files with 100% data accuracy
-  Processed videos with bounding box annotations
-  GUI applications with functional interfaces
-  Model files (.pkl, .h5, .pt formats)
-  Complete source code repositories

**Performance Metrics:**

| Metric | Value |
|--------|-------|
| Face Recognition Accuracy | 87% |
| Emotion Detection Accuracy | 68% |
| Animal Detection mAP | 0.78 |
| Average FPS | 15-20 (real-time processing) |

### 6.3 Daily Progress Tracking

Maintained consistent daily reports at https://dailyreport.nullclass.com/ documenting:

- Tasks completed each day
- Challenges encountered
- Solutions implemented
- Time spent on each activity
- Learning outcomes

---

## 7. Challenges and Solutions

### Challenge 1: Low Face Recognition Accuracy (Initial: 62%)

**Problem:**
Initial face recognition accuracy was only 62%, with frequent false negatives when students wore glasses or had different hairstyles.

**Root Cause Analysis:**
- Insufficient training data (only 20 images per student)
- Poor image quality (low resolution, motion blur)
- High tolerance threshold (0.8)

**Solution Implemented:**
- Increased dataset to 50+ images per student with variations
- Added data collection guidelines (good lighting, multiple angles)
- Reduced tolerance threshold from 0.8 to 0.6
- Implemented frame skipping (process every 3rd frame) to reduce motion blur

**Result:** Accuracy improved to 87%

---

### Challenge 2: YOLO Model Training - Out of Memory Error

**Problem:**
GPU memory overflow during YOLO training with batch size 16 on 6GB GPU.

```
RuntimeError: CUDA out of memory. Tried to allocate 2.5 GiB
```

**Solution Implemented:**
- Reduced batch size from 50 to 20
- Used custom trained model with GPU
- Enabled mixed precision training (FP16)
- Cleared GPU cache between epochs

**Code Fix:**
```python
model.train(
    data='dataset.yaml',
    epochs=100,
    batch=20,      # Reduced from 50
    imgsz=640,
    amp=True      # Mixed precision
)
```

**Result:** Successfully trained model with 78% mAP

---

### Challenge 3: Emotion Detection Poor Accuracy (45%)

**Problem:**
FER library showing only 45% accuracy, often misclassifying neutral as sad.

**Solution Implemented:**
- Switched from basic FER to FER with MTCNN face detection
- Preprocessed face images (histogram equalization for lighting)
- Set minimum confidence threshold (0.5)
- Used ensemble approach (take top 2 emotions and display dominant)

**Code Improvement:**
```python
# Before
detector = FER()

# After
detector = FER(mtcnn=True)  # Better face detection
```

**Result:** Accuracy improved to 68% (acceptable for emotion detection)

---

### Challenge 4: GUI Freezing During Video Processing

**Problem:**
GUI becomes unresponsive when processing long videos (>2 minutes).

**Solution Implemented:**
- Implemented threading to separate GUI and processing
- Added progress bar with frame count
- Processed video in background thread
- Used queue for thread-safe communication

**Code Implementation:**
```python
import threading
from queue import Queue

def process_video_thread(self, video_path):
    # Processing logic here
    pass

thread = threading.Thread(target=self.process_video_thread, args=(path,))
thread.start()
```

**Result:** GUI remains responsive during processing

---

### Challenge 5: Time-Based System Testing

**Problem:**
Difficult to test attendance system outside 9:30-10:00 AM window.

**Solution Implemented:**
- Added `debug_mode` flag for development
- Implemented mock time functionality for testing
- Created separate test configuration file

**Code Solution:**
```python
class AttendanceSystem:
    def __init__(self, debug_mode=True):
        self.debug_mode = debug_mode
    
    def is_attendance_time(self):
        if self.debug_mode:
            return True  # Always active in debug mode
        # Normal time check
```

**Result:** Enabled testing anytime while maintaining production time restrictions

---

### Challenge 6: Dataset Annotation for Custom Animals

**Problem:**
Manual annotation of 2000+ animal images taking excessive time (estimated 40+ hours).

**Solution Implemented:**
- Used Roboflow for semi-automated annotation
- Leveraged pre-trained COCO model for initial bounding boxes
- Manual correction only for mislabeled boxes
- Used data augmentation to expand dataset

**Tools Used:**
- Roboflow (web-based annotation)
- LabelImg (offline tool)

**Result:** Reduced annotation time to 12 hours

---

## 8. Outcomes and Impact

### 8.1 Technical Outcomes

**Six Functional ML Systems Delivered:**
- All projects meet specified requirements
- Code is modular, documented, and maintainable
- Systems achieve acceptable accuracy thresholds

**Model Performance:**

| Project | Metric | Value |
|---------|--------|-------|
| Face Recognition | Accuracy | 87% |
| Animal Detection | mAP | 78% |
| Emotion Detection | Accuracy | 68% |
| Real-time Processing | FPS | 15-20 |

**Code Quality:**
- 3000+ lines of well-documented Python code
- Proper error handling and logging
- Reusable components and functions

### 8.2 Learning Outcomes

**Knowledge Gained:**
- Deep understanding of CNN architectures
- Practical experience with YOLO object detection
- Face recognition algorithms and their limitations
- Real-time video processing optimization techniques
- GUI development for ML applications

**Skills Mastered:**
- End-to-end ML project development
- Dataset collection and preprocessing
- Model training, evaluation, and optimization
- Production deployment considerations

### 8.3 Professional Growth

**Portfolio Development:**
- Six complete projects demonstrating diverse ML skills
- GitHub repository with professional README files
- Documented code suitable for showcasing to employers

**Industry Readiness:**
- Experience with real-world project constraints
- Understanding of accuracy vs. speed tradeoffs
- Knowledge of deployment challenges

**Problem-Solving Capability:**
- Developed systematic debugging approach
- Learned to research and implement solutions independently
- Built resilience when facing technical challenges

### 8.4 Potential Real-World Impact

**Attendance System:**
- Can reduce manual attendance time by 80%
- Provides emotion analytics for student engagement
- Applicable in schools, colleges, and corporate training

**Animal Detection:**
- Supports wildlife conservation efforts
- Helps in monitoring endangered species
- Assists in human-wildlife conflict prevention

**Drowsiness Detection:**
- Potential to prevent road accidents
- Applicable in commercial transportation
- Saves lives through early warning systems

---

## 9. Conclusion

This internship provided invaluable hands-on experience in applying machine learning and computer vision to solve real-world problems. Over the course of the internship, I successfully completed six distinct projects, each presenting unique technical challenges and learning opportunities.

### Key Achievements

-  **Technical Mastery:** Gained proficiency in OpenCV, YOLO, face recognition, and deep learning frameworks
-  **Project Completion:** Delivered all six projects meeting specified requirements
-  **Problem-Solving:** Overcame significant challenges including accuracy optimization, memory management, and real-time processing
-  **Professional Development:** Enhanced coding standards, documentation skills, and project management abilities

### Skills Transformation

| | Before Internship | After Internship |
|--|------------------|-----------------|
| ML Knowledge | Theoretical knowledge of ML algorithms | Hands-on expertise in computer vision |
| Python | Basic Python programming | Advanced Python development skills |
| Projects | Limited practical project experience | End-to-end ML project development capability |
| Systems | — | Production-ready code development |
| Optimization | — | Real-time system optimization |

### Future Applications

The skills acquired during this internship will be directly applicable to:

- Advanced computer vision projects
- Real-time AI systems development
- ML model deployment and optimization
- Research in deep learning
- Career opportunities in AI/ML industry

### Acknowledgments

I would like to thank **Null Class** for providing this opportunity.

### Personal Reflection

This internship transformed my understanding of machine learning from theoretical concepts to practical implementations. The most valuable lesson learned was that building production-ready ML systems requires not just algorithmic knowledge, but also considerations for data quality, computational efficiency, user experience, and real-world constraints.

The challenges faced — from debugging memory errors to optimizing model accuracy — taught me persistence and systematic problem-solving. Each obstacle overcome built confidence in my ability to tackle complex technical problems independently.

Moving forward, I am well-equipped to pursue advanced projects in computer vision and deep learning, with a strong foundation in both theory and practice.

---

## Appendices

### Appendix A: Project File Structure

```
internship_projects/
├── project1_attendance/
│   ├── dataset/
│   ├── encodings/
│   ├── attendance_records/
│   ├── collect_student_data.py
│   ├── train_face_encodings.py
│   └── attendance_system.py
├── project2_animal_detection/
│   ├── datasets/
│   ├── models/
│   └── animal_detection.py
├── project3_drowsiness/
├── project4_nationality/
├── project5_sign_language/
├── project6_car_detection/
└── requirements.txt
```

### Appendix B: Technologies Version Information

| Technology | Version |
|------------|---------|
| Python | 3.8.10 |
| OpenCV | 4.8.0 |
| TensorFlow | 2.13.0 |
| PyTorch | 2.0.1 |
| Ultralytics | 8.0.196 |
| face_recognition | 1.3.0 |
| FER | 22.5.1 |

### Appendix C: Performance Metrics Summary

| Project | Metric | Value |
|---------|--------|-------|
| Attendance | Face Recognition Accuracy | 87% |
| Attendance | Emotion Detection Accuracy | 68% |
| Attendance | Processing Speed | 18 FPS |
| Animal Detection | mAP@0.5 | 78% |
| Animal Detection | Inference Time | 45ms |
| Drowsiness | Detection Accuracy | 92% |
| Nationality | Classification Accuracy | 71% |
| Sign Language | Recognition Accuracy | 84% |
| Car Detection | Detection mAP | 81% |

---

## Declaration

I hereby declare that this report is based on my original work completed during the internship period. All sources of information have been duly acknowledged. The code and models developed are my own work, with proper attribution given to open-source libraries and pre-trained models used.

**Name:** Vishal Kumar Sharma
