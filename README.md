# Face Detection Using Python, OpenCV & MediaPipe

A real-time face detection project built using **Python, OpenCV, and MediaPipe**. This project detects human faces through a webcam, draws custom bounding boxes around detected faces, and displays face detection confidence scores and real-time FPS.

## Features

- **Real-Time Face Detection:** Detects faces using a live webcam feed.
- **Custom Bounding Boxes:** Draws rectangular boxes around detected faces.
- **Corner-Style Bounding Boxes:** Uses custom OpenCV lines to create a more visually appealing detection box.
- **Confidence Score:** Displays the detection confidence percentage above each detected face.
- **FPS Counter:** Displays real-time frames per second.
- **Multiple Face Detection:** Supports detecting multiple faces in the same frame.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| OpenCV | Webcam access and image processing |
| MediaPipe | Face detection |
| NumPy | Image and numerical processing |

## Project Structure

```text
Face-Detection-Project/
│
├── FaceDetectionModule.py
├── pyproject.toml
├── uv.lock
├── .gitignore
└── README.md
```

## How It Works

### 1. MediaPipe Face Detection

The project initializes MediaPipe's face detection solution:

```python
mpFaceDetection = mp.solutions.face_detection

faceDetection = mpFaceDetection.FaceDetection()
```

### 2. Image Processing

The webcam frame is converted from BGR to RGB before being processed by MediaPipe.

```python
imgRGB = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
results = self.faceDetection.process(imgRGB)
```

### 3. Bounding Box Calculation

MediaPipe provides normalized bounding box coordinates. These are converted into pixel coordinates using the image dimensions.

```python
bboxC = detection.location_data.relative_bounding_box

ih, iw, ic = img.shape

bbox = (
    int(bboxC.xmin * iw),
    int(bboxC.ymin * ih),
    int(bboxC.width * iw),
    int(bboxC.height * ih)
)
```

### 4. Custom Bounding Box Drawing

OpenCV is used to draw rectangular bounding boxes and decorative corner lines around detected faces.

### 5. Confidence Score

The detection confidence is extracted and displayed as a percentage.

```python
int(detection.score[0] * 100)
```

### 6. FPS Calculation

The project calculates the frames per second using the time difference between consecutive frames.

```python
fps = 1 / (cTime - pTime)
```

## Learning Outcomes

Through this project, I explored:

- Real-time computer vision.
- MediaPipe face detection.
- OpenCV image processing.
- Normalized coordinates and bounding box calculations.
- Object-oriented programming using Python classes.
- Real-time FPS calculation.
- Custom visualization using OpenCV.

## Future Improvements

- Face landmark detection using MediaPipe Face Mesh.
- Face blurring for privacy protection.
- Face counting and tracking.
- Face detection from recorded videos and images.
- Improved detection performance and UI.
