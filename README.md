# Face-Detection_Eye_Blinking
Developing the system for detecting the area of interest(face) in real-time and keep tracking it. Also, 
this system detects movement of the eye i.e. blinking of the eyes.

The provided code is a Python script that uses the OpenCV library to perform real-time face and eye detection from a webcam feed. It also counts the number of blinks detected by monitoring eye activity. Here's a summary of the code:

1. **Importing Libraries**:
   - The code starts by importing the OpenCV library (`cv2`) for computer vision tasks.
   - It also imports the `time` library, although it's not used in the code.

2. **Cascade Classifiers**:
   - Two cascade classifiers are loaded using the `cv2.CascadeClassifier` class: one for face detection and one for eye detection.
   - The paths to the XML files containing the classifier data are specified.

3. **Variables**:
   - `eye_flag`: A Boolean variable to track if eyes are detected in the frame.
   - `show_count`: A Boolean variable to control whether the blink count is displayed.
   - `blink_count`: A counter to keep track of the number of blinks detected.

4. **Video Capture**:
   - The code initializes a video capture object (`cap`) to access the webcam (camera index 0).
   - It enters a continuous loop for capturing frames from the webcam.

5. **Frame Processing**:
   - Within the loop, the code reads a frame (`img`) from the webcam feed.
   - Converts the frame to grayscale (`gray`) for better processing efficiency.
   - Uses the face cascade classifier to detect faces in the grayscale frame.

6. **Face Detection**:
   - If a face is detected, the code draws a rectangle around the detected face and sets `eye_flag` to `False`.

7. **Eye Detection**:
   - If a face is detected, the code uses the eye cascade classifier to detect eyes within the region of interest (ROI), which is the area around the detected face.
   - If eyes are detected, the code draws rectangles around the eyes and sets `eye_flag` to `True`.

8. **Blink Counting**:
   - If `eye_flag` is `True`, indicating that eyes are currently detected, `show_count` is set to `True`.
   - If `show_count` is `True` and `eye_flag` becomes `False`, it means a blink has occurred, and the `blink_count` is incremented.

9. **Displaying Blink Count**:
   - The code uses OpenCV to display the current frame with any detected rectangles and the blink count at the top-left corner.

10. **Exiting the Loop**:
    - The loop continues until the 'Esc' key (key code 27) is pressed.
    - When the 'Esc' key is detected, the loop breaks.

11. **Release and Cleanup**:
    - After the loop exits, the video capture object is released to release the webcam.
    - All OpenCV windows are destroyed to clean up resources.

This code is a simple demonstration of how to perform basic real-time face and eye detection using OpenCV and count blinks based on eye activity. It can serve as a starting point for more advanced computer vision applications, such as driver drowsiness detection or gaze tracking.
