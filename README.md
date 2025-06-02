#  NO MORE PARKING TICKETS

This is an end-to-end learning project using a Raspberry Pi 5, Logitech Brio 300 camera, and the YOLOv11n model to detect parking guards in real time. When a guard is spotted, the system sends an SMS alert to the owner via Twilio. The live video feed is accessible through a local web server powered by Flask, and is secured with login and password.

To further enhance the system, FastReID (torchreid) is integrated for advanced person re-identification. This allows the system to assign persistent IDs to each detected individual, enabling reliable tracking of guards even as they move, change pose, or temporarily leave the camera’s view. By combining YOLOv11n’s fast and accurate object detection with FastReID’s robust person recognition, the project delivers more accurate and actionable alerts, reducing false alarms and improving the overall user experience.

---

##  Project Goals

- Detect parking guards before they can give you a ticket
- Set up a live feed accessible within the local network
- Send a sms warning message when a parking guard is spotted
- Automatically purchase a parking ticket when a parking guard is spotted in frame
- Log data in a csv for analytics and insights 

---

## Example Images

Here’s what the detection looks like in action:

<p align="center">
  <img src="https://github.com/user-attachments/assets/2932ada3-0805-435b-a130-b503a15976d9" alt="Detection Example 1" width="400"/>
  <img src="https://github.com/user-attachments/assets/c3ce35b1-5c16-4d7b-ab53-6635c809e226" alt="Detection Example 2" width="400"/>
</p>

---

##  Hardware

| Tool | Purpose |
|------|---------|
| **Rasperry Pie 5 (8GB)** | Run the python code, processing & model training |
| **Logitech Brio 300** | Capture Video |
| **SD Card 32GB** | Harddrive |
| **Python** | Core language |

---

## Models

### YOLOv11n

- **Base Model:** YOLOv11n (nano) is the smallest and fastest YOLO model, making it ideal for edge devices and real-time applications where computational resources are limited. While it is less accurate than larger variants, it achieves a strong balance between speed and detection quality.
- **FPS:** On a Raspberry Pi 5, the camera feed typically provides 6–7 FPS at 1280x720 resolution. This ensures smooth real-time monitoring and alerting for parking guard detection.
- **Stream:** The video stream is served via a Flask web server and can be viewed on any device within the local network. Access is protected by login and password, ensuring security and privacy.
- **Guard Detection:** The model is pre-trained to detect people and draw bounding boxes around each individual. After detection, if a bounding box contains a certain threshold of yellow pixels (indicative of a parking guard’s uniform or vest), the system flags that person as a parking guard. This approach is simple yet effective for reliable identification in real-world environments.
- **Performance Metrics:**  
  - **mAP (COCO, 640x640):** 39.5  
  - **Parameters:** 2.6 million  
  - **FLOPs:** 6.5 billion  
  - **Speed:** ~56 ms per image on CPU (ONNX), but real-world edge device performance is 6–7 FPS at 1280x720.
- **Integration:** YOLOv11n is optimized for speed and efficiency, making it highly adaptable for deployment on edge devices like the Raspberry Pi 5. Its lightweight nature allows for continuous operation and easy integration with additional logic such as color analysis and persistent ID tracking.


### FastReID (or Torchreid)

- **Purpose:** FastReID is a state-of-the-art re-identification platform, designed for recognizing and tracking individuals across video frames.
- **Why Use It:**  
  - **Persistent Tracking:** YOLO assigns new IDs to people each time they leave and re-enter the frame or change their appearance. FastReID (or similar models like Torchreid) assigns a persistent ID to each person, allowing the system to recognize the same individual even if they move, change pose, or temporarily leave the frame.
  - **Event Logging:** With persistent IDs, analytics and event logging (e.g., dwell time, entry/exit) are more accurate and meaningful.
  - **Better Alerts:** By tracking individuals over time, the system can provide more reliable alerts and avoid redundant notifications for the same person.
- **How It Works:**  
  - **Feature Extraction:** For each detected person, FastReID extracts a unique feature vector (embedding) based on their appearance.
  - **Matching:** When a person is detected in subsequent frames, their new feature vector is compared to those stored in a database. If a match is found, the same persistent ID is assigned.
  - **Multi-Frame Averaging:** To improve robustness, feature vectors from several frames are averaged before matching, reducing false positives and ID switches.
- **Integration:** FastReID (or Torchreid) is integrated into the pipeline after YOLO detection, providing persistent IDs that are used for logging and analytics.

## Why Use Persistent IDs?

- **Accurate Analytics:** Logs and analytics are tied to individuals, not just detections.
- **Reduced False Alerts:** The system can avoid sending multiple alerts for the same person.
- **Better User Experience:** Users can track the same guard over time, even if they move or change appearance.

---

##  Project Structure

```text
parking_guard_detection/
├── Code/
├── Images/
│   └── 2 example images
├── README.md
├── requirements.txt
└── LICENSE
