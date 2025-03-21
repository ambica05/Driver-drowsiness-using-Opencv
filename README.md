# Drowsiness Detection System

This project implements a real-time driver drowsiness detection system using computer vision and machine learning techniques in Python.  The goal is to enhance road safety by identifying and alerting drivers who are showing signs of fatigue.

## Overview

Driver drowsiness is a significant factor in road accidents. This system analyzes a driver's facial features and behaviors to detect signs of drowsiness, providing timely alerts to prevent potential accidents.  The system utilizes:

*   **Real-time video capture:** Captures the driver's face using a webcam or in-vehicle camera.
*   **Facial landmark detection:** Identifies key facial features (eyes, mouth) using the dlib library.
*   **Eye Aspect Ratio (EAR) calculation:**  Calculates the EAR to determine eye closure, a key indicator of drowsiness.
*   **Drowsiness detection logic:**  Triggers alerts when the EAR falls below a certain thresh old for a specified duration.
*   **Alerting mechanism:** Provides audible or visual alerts to the driver.

## Features

*   Real-time drowsiness detection
*   Eye Aspect Ratio (EAR) calculation for eye closure detection
*   Configurable drowsiness thresholds
*   Audible alerts using `pygame`
*   [Possible:  Visual alerts/GUI using Tkinter or PyQt (based on report)]

## Requirements

*   Python 3.6+
*   OpenCV (`cv2`)
*   dlib
*   imutils
*   scipy
*   pygame
*   [Possible: TensorFlow/Keras, scikit-learn (based on report, if more sophisticated ML is implemented)]
*   [If CMake is used in the project build instructions would be here]

## Installation

1.  **Install Python dependencies:**

    ```bash
    pip install opencv-python dlib imutils scipy pygame
    # If using TensorFlow/Keras:
    # pip install tensorflow scikit-learn
    ```

2.  **Download the dlib shape predictor:**

    Download the `shape_predictor_68_face_landmarks.dat` file from a trusted source (e.g., [dlib's website](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2)) and place it in the project directory.  *This is a crucial file.*

## Usage

1.  **Run the drowsiness detection script:**

    ```bash
    python drowsiness_detection.py
    ```

    (or whatever the main script's name is)

2.  **The system will capture video from your webcam and display alerts if drowsiness is detected.**

## Code Structure

*   `drowsiness_detection.py`:  Main script for running the drowsiness detection system.
*   `shape_predictor_68_face_landmarks.dat`:  dlib's facial landmark predictor.
*   `[Possibly a file]utils.py`:  Helper functions for image processing.
*   `[Possible: A folder]models/`: Contains any pre-trained machine learning models.

## Algorithm Details

1.  **Face Detection:**  The system uses `dlib's frontal_face_detector` to find faces in the video frame.
2.  **Landmark Prediction:**  For each detected face, the `shape_predictor` is used to locate 68 facial landmarks.
3.  **Eye Aspect Ratio (EAR):** The EAR is calculated for each eye using the formula:

    ```
    EAR = (||p2 - p6|| + ||p3 - p5||) / (2 * ||p1 - p4||)
    ```

    where p1, p2, ..., p6 are the 2D landmark locations around the eye.
4.  **Drowsiness Detection:** The system monitors the EAR over time. If the EAR falls below a predefined `THRESH` value for more than `FRAME_CHECK` consecutive frames, the driver is considered drowsy, and an alert is triggered.

## Configuration

*   `THRESH`:  Threshold for the EAR value (default: 0.25).
*   `FRAME_CHECK`:  Number of consecutive frames below the threshold to trigger an alert (default: 20).
*   These parameters can be adjusted in the `drowsiness_detection.py` script to fine-tune the system's sensitivity.

## Future Work

*   Improve accuracy using deep learning models (CNNs).
*   Implement more sophisticated alerting mechanisms (e.g., haptic feedback).
*   Integrate with vehicle systems for automated responses.
*   Add environmental adaptation (IR cameras, lighting compensation).
*   Incorporate head pose and yawning detection.

## References

*   This project is inspired by the work described in the following research papers (from the project report's bibliography):

    *   [List of relevant papers from the bibliography, formatted for readability]

## License

[Specify the license, e.g., MIT License]


Important Considerations and Improvements

Download shape_predictor_68_face_landmarks.dat: This is the most critical step. The code will not work without this file and its location properly specified. The dlib documentation will have the most up-to-date information on where to obtain the file.

GitHub Link in the Report: Check if the GitHub link is correct and leads to the repository.

TensorFlow/Keras: The presence of TensorFlow/Keras indicates the possibility of a more complex drowsiness detection model (like a CNN) being used. If so, the README should describe how the model was trained and how to use it.

GUI: If the project uses Tkinter or PyQt for a GUI, the README should include instructions on how to run the GUI.

Clearer Code Structure Description: If the project is well-organized, the README should provide a clear description of the purpose of each Python file and directory.

Contributing: If you want others to contribute, add a contributing section with guidelines.

Example Images/Videos: Include a screenshot or a short video demo of the system in action.

Look for the README.md file: The README file is usually displayed on the repository's main page. If you don't see it, click on "Code" and look for a file named README.md in the file list.

Copy the content: Copy the contents of the README.md file.
