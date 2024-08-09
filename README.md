# Transport-detection with OpenCV


https://cdn.iportal.ru/news/2020/99/preview/a936c6dc139187fc292c4c039af7a2a30b2f8c8a_3000_1688_c.JPG

# Vehicle Detection Using Haar Cascade Classifier
### Overview
This project demonstrates a basic vehicle detection system using OpenCV's Haar Cascade Classifier. The system detects vehicles in a video feed and highlights them with bounding boxes.

### Project Structure
cars.xml: The Haar Cascade XML file used for vehicle detection.
video.avi: A sample video file used to test the vehicle detection system.
vehicle_detection.py: The main Python script that processes the video feed and detects vehicles.
README.md: Documentation for understanding and using the project.
### How It Works
* Video Capture: The system reads frames from a video file (video.avi) or a live camera feed.

* Grayscale Conversion: Each frame is converted to grayscale to simplify the image and make it easier for the classifier to process.

* Vehicle Detection: The Haar Cascade classifier (cars.xml) is used to detect vehicles in the grayscale frame. Detected vehicles are highlighted with red rectangles.

* Display: The processed frames with highlighted vehicles are displayed in a window.

* Exit Condition: The system runs in a loop, processing each frame until the user presses the 'q' key to exit.

Code Explanation
`vehicle_detection.py`

```python
import cv2

# Video faylni ochish
cap = cv2.VideoCapture('video.avi')  # 0 - bu default kamera

# Haar kaskadni yuklash
carcascade = cv2.CascadeClassifier('cars.xml')

while True:
    # Video oqimidan kadrni olish
    ret, frame = cap.read()
    if not ret:
        break  # Agar video tugasa, loopdan chiqish

    # Rangli kadrni kulrangga o'tkazish
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    # Avtomobillarni aniqlash
    cars = carcascade.detectMultiScale(gray, 1.1, 1)

    # Aniqlangan avtomobillarni tasvirga chizish
    for (x, y, w, h) in cars:
        cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 0, 255), 2)

    # Natijani ko'rsatish
    cv2.imshow('Output', frame)

    # 'q' tugmasini bosganda chiqish
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# Video oqimini to'xtatish va barcha oynalarni yopish
cap.release()
cv2.destroyAllWindows()
```

# How the Code Works
* Video Capture: The script opens the video.avi file for processing. If you want to use a live camera feed, replace 'video.avi' with 0 (which represents the default camera).

* Haar Cascade Loading: The cars.xml file is loaded to detect vehicles in the frames.

* Frame Processing:

* The frames are converted to grayscale using cv2.cvtColor to simplify processing.
* The detectMultiScale function is used to identify vehicles in the grayscale frames.
* Each detected vehicle is highlighted with a red rectangle.
* Display and Exit:

The processed frame is displayed in a window titled 'Output.'
Pressing the 'q' key will exit the loop, close the video stream, and shut down the display window.
# Usage
### Prerequisites
Ensure you have the following dependencies installed:
```
pip install opencv-python
```
### Running the Script
1. Clone the repository or download the project files.

2. Place your video file in the project directory or ensure your camera is connected.

3. Run the script:
```
python vehicle_detection.py
```
4. A window will appear showing the video feed with detected vehicles highlighted.
## Exiting the Program
To exit the program, simply press the 'q' key.

### Example Output
Below is an example of how the detected vehicles appear in the video feed:

 Add an image or GIF showing the detection process.

# Potential Improvements
* Real-time Vehicle Tracking: Implement vehicle tracking across frames.
* Multi-Class Detection: Extend the system to detect different types of vehicles (e.g., cars, trucks, buses).
* Deep Learning Integration: Replace Haar Cascade with a deep learning model (e.g., YOLO) for more accurate detection.

# License
This project is licensed under the MIT License - see the LICENSE file for details.

# Acknowledgments
* OpenCV for providing the tools to implement the detection system.
* The contributors of the Haar Cascade XML file for vehicle detection.
