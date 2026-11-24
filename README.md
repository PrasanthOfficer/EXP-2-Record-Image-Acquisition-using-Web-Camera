# EXP-2-Record-Image-Acquisition-using-Web-Camera

---
### Developed By:
**Name:** Prasanth T

### Register No: 212224040243

## Aim

To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1. Write the frame as a JPG file  
2. Display the video  
3. Display the video by resizing the window  
4. Rotate and display the video  

---

## 🛠️ Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  

---

## ⚙️ Algorithm

### Step 1:
Import the required libraries and initialize the webcam using `cv2.VideoCapture()`.

### Step 2:
Capture frames continuously from the webcam.

### Step 3:
Save a frame as a JPG image using `cv2.imwrite()`.

### Step 4:
Display the live video stream using `cv2.imshow()`.

### Step 5:
Resize the frame and rotate it using OpenCV functions, then display the processed frames.

---

## 💻 Program

```py
import cv2
from IPython.display import display, Image

cap = cv2.VideoCapture(0, cv2.CAP_DSHOW)

ret, frame = cap.read()
cap.release()

if ret:
    cv2.imwrite("image.jpg", frame)

    resized = cv2.resize(frame, (400, 300))
    rotated = cv2.rotate(
        resized, cv2.ROTATE_90_CLOCKWISE
    )

    cv2.imwrite("resized.jpg", resized)
    cv2.imwrite("rotated.jpg", rotated)

    print("Original Image")
    _, buffer = cv2.imencode(".jpg", frame)
    display(Image(data=buffer.tobytes()))

    print("Resized Image")
    _, buffer = cv2.imencode(".jpg", resized)
    display(Image(data=buffer.tobytes()))

    print("Rotated Image")
    _, buffer = cv2.imencode(".jpg", rotated)
    display(Image(data=buffer.tobytes()))

    print("All images saved successfully!")
else:
    print("Image capture failed!")
## for video
import cv2
import os

# Load the three saved images
img1 = cv2.imread("image.jpg")
img2 = cv2.imread("resized.jpg")
img3 = cv2.imread("rotated.jpg")

if img1 is None or img2 is None or img3 is None:
    print("Image files not found! Check the file names.")
else:
    # Resize all images to the same size
    size = (400, 300)

    img1 = cv2.resize(img1, size)
    img2 = cv2.resize(img2, size)
    img3 = cv2.resize(img3, size)

    # Create video writer
    video = cv2.VideoWriter(
        "output.mp4",
        cv2.VideoWriter_fourcc(*"mp4v"),
        1,
        size
    )

    # Show each image for 2 seconds
    for img in [img1, img2, img3]:
        for i in range(2):
            video.write(img)

    video.release()

    print("Video created successfully: output.mp4")
    print("Duration: approximately 6 seconds")
from IPython.display import Video, display

display(Video("output.mp4", embed=True))
```
---

## Output

### i) Write the frame as JPG image
Captured image is saved as 

<img width="741" height="977" alt="image" src="https://github.com/user-attachments/assets/a5edea6c-d9b0-4592-abde-3022d7a8aeac" />



### ii) Display the video
Live webcam video is displayed

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/e9a042ca-de4b-426c-a970-9a19e67795e0" />



### iii) Display the video by resizing the window
Video is shown in resized resolution (640 × 480)

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/df7ab43b-628d-4cff-8ec6-8ad002494986" />


### iv) Rotate and display the video
Video is displayed after rotation (90° clockwise)

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/4c538f2c-7dba-4d6b-9868-af8e6cf3d93a" />


---

## Result

Thus, the image is successfully captured from the webcam and various video processing operations such as saving, displaying, resizing, and rotating are performed using OpenCV.
