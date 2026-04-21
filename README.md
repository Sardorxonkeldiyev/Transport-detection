
(![scale_1200 (3)](https://github.com/user-attachments/assets/3f0e0677-455c-47fc-8c49-e178798751b5))

# 🚗 Vehicle Detection using Haar Cascades

## 📝 Project Overview
This project demonstrates a real-time vehicle detection system using **OpenCV** and **Haar Cascade Classifiers**. Unlike deep learning approaches, this method relies on a pre-trained XML classifier (`cars.xml`) to identify object features (edges, lines) and detect vehicles in video streams or video files.

## 🛠️ Tools & Technologies
* **Language:** Python
* **Computer Vision Library:** OpenCV (`cv2`)
* **Algorithm:** Haar Cascade Classifier

## 🚀 How it Works
1. **Grayscale Conversion:** Each frame of the video is converted to grayscale to simplify calculations and speed up the detection process.
2. **Feature Matching:** The `cars.xml` classifier scans the image for specific Haar-like features that represent a car's structure.
3. **Multi-Scale Detection:** The `detectMultiScale` function allows the model to find cars of different sizes by scaling the detection window.
4. **Bounding Boxes:** Once a vehicle is identified, a red rectangle (bounding box) is drawn around it in real-time.

## 📂 Project Structure
* `cars.xml`: The pre-trained Haar Cascade XML file for vehicle detection.
* `vehicle_detection.py`: The main Python script that processes the video and applies detection.
* `video.avi`: The sample video file used for testing the detection system.

## 📌 Usage
To run the project, ensure you have OpenCV installed:
```bash
pip install opencv-python
