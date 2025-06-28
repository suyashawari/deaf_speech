# Deaf Speech - Real-Time Hand Gesture Recognition

**Recognize hand gestures instantly on your Android device using the live camera or gallery media.**

Deaf Speech leverages MediaPipe for on-device machine learning to identify hand gestures, overlaying visual landmarks for an interactive experience.

---

## ✨ Key Features

*   **Live Camera & Gallery Recognition:** Analyze gestures in real-time or from existing media.
*   **Visual Hand Landmarks:** See detected keypoints and connections overlaid on hands.
*   **Front/Back Camera Support:** Easily switch cameras in live mode.
*   **Confidence Scores:** View the recognized gesture and its accuracy.
*   **MediaPipe Powered:** Fast and efficient on-device ML.
*   **Customizable Model:** Includes resources for training your own gesture models.

---

## 🌊 Core Workflow

1.  **Launch & Select Mode:** Start the app, choose "Camera" or "Gallery".
2.  **Camera Mode:**
    *   App requests camera permission.
    *   Live feed starts; gestures are recognized with landmarks overlaid.
3.  **Gallery Mode:**
    *   Select an image/video.
    *   Media is analyzed; gestures and landmarks are shown.
4.  **Results:** Recognized gesture name and confidence score are displayed.

---

## 💻 Tech Stack

*   **Platform:** Android
*   **Language:** Kotlin
*   **ML:** MediaPipe (`tasks-vision`)
*   **Camera:** CameraX
*   **UI:** AndroidX (AppCompat, Material, Navigation), RecyclerView
*   **Model:** TensorFlow Lite (`.task`)
*   **Model Training (Optional):** Python, Jupyter, MediaPipe Model Maker, TensorFlow

---

## 🚀 Getting Started

### Project Requirements

| Category                     | Requirement                    | Notes                                                        |
| :--------------------------- | :----------------------------- | :----------------------------------------------------------- |
| **Android Application**      | Android Studio                 | Latest stable version (e.g., Hedgehog+)                      |
|                              | Android SDK                    | API 24+ (Nougat)                                             |
|                              | Android Device/Emulator        | API 24+                                                      |
| **Model Training (Optional)** | Python                         | 3.8+                                                         |
|                              | pip                            | Python package installer                                     |
|                              | Jupyter Notebook/Lab           | For `.ipynb` files                                           |
|                              | Python Libraries               | `tensorflow`, `mediapipe-model-maker`, `opencv-python`, `matplotlib` |

---

### ⚙️ Installation & Setup

#### 1. Android Application

1.  **Clone Repository:**
    ```bash
    git clone https://github.com/suyashawari/Deaf_speech.git
    cd Deaf_speech # Or your project's root directory
    ```
2.  **Open in Android Studio:** Open the cloned project directory.
3.  **Sync Gradle:** Allow Android Studio to download dependencies.
4.  **Ensure Model:** Verify `gesture_recognizer.task` is in `src/main/assets/`.
5.  **Build & Run:** Select a device/emulator and click "Run".

#### 2. Model Training & Customization (Simplified Steps)

Use the provided Jupyter Notebook (e.g., `gesture_recognizer.ipynb`) to train your own gesture model.

1.  **Prepare Dataset:**
    *   Create image folders for each gesture.
        *   **Example Structure:**
            ```
            project_root/
            ├── datasets/
            │   ├── thumbs_up/
            │   │   ├── img1.jpg
            │   │   └── img2.png
            │   ├── fist/
            │   │   ├── image_A.png
            │   │   └── image_B.jpg
            │   └── peace/
            │       ├── pic_01.jpeg
            ```
    *   *(Optional)* Resize images using `model/resize.py` (configure paths in the script first if needed).

2.  **Install Training Tools:**
    ```bash
    pip install tensorflow mediapipe-model-maker jupyter opencv-python matplotlib
    ```

3.  **Train the Model (using `.ipynb` file):**
    *   Start Jupyter: `jupyter notebook gesture_recognizer.ipynb`
    *   Inside the notebook:
        *   Update the dataset path variable to point to your `datasets` folder.
            *   **Example (in the notebook):**
                ```python
                dataset_path = "datasets" # if 'datasets' is in the same dir as the notebook
                # OR
                # dataset_path = "path/to/your/datasets_folder"
                ```
        *   Run the notebook cells to:
            1.  Load your image dataset.
            2.  Train the gesture recognizer model.
            3.  Evaluate its performance.
            4.  Export the trained model (typically as `gesture_recognizer.task` into an `exportedModel` folder).
            *   **Example output location after running notebook:** `project_root/exportedModel/gesture_recognizer.task`

4.  **Use Your Trained Model in the Android App:**
    *   Copy your newly exported `.task` file (e.g., from `exportedModel/gesture_recognizer.task`).
    *   Paste it into the Android app's `src/main/assets/` directory, replacing the existing model if there is one.
    *   Rebuild and run the Android application.

---

## ✅ Testing the App

1.  Launch "Deaf Speech".
2.  Grant camera permissions when prompted.
3.  **Camera Mode:** Perform various hand gestures in front of the camera. Observe the real-time landmark overlays and the recognized gesture name/score.
4.  **Gallery Mode:** Select an image or video containing hand gestures. Observe the landmark overlays and recognized gesture information on the selected media.

---

## 🖼️ Application Output (Brief Visual Description)

*   **Splash Screen:** App logo and "Deaf Speech" title.
*   **Main UI:** Bottom navigation tabs for "Camera" and "Gallery" modes.
*   **Recognition View (Camera/Gallery):**
    *   Displays the live camera feed or selected media.
    *   Overlays small colored dots (landmarks) on detected hands (knuckles, fingertips, palm).
    *   Draws lines connecting these landmarks, outlining the hand's shape.
    *   Shows a text area (e.g., at the top) with the recognized gesture (e.g., "Victory", "Open Palm") and a confidence percentage (e.g., "92%").

---

## 🤝 Contributing

Contributions are welcome!
1.  Fork the Project.
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

---

## 📜 License

Typically distributed under Apache License 2.0 (as this project is often based on MediaPipe examples). Please check the `LICENSE` file in the repository for specific details.

---

Happy Gesture Recognizing! ✨
