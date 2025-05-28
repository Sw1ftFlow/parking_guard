#  NO MORE PARKING TICKETS

This is an end-to-end learning project using **Rasperry Pie 5**, **Logitech Brio 300**, and **YOLO11n model** to detect when a parking guard is spotted in frame and sends a sms message to the owner using **Twilio**. The live feed is accessible via a local webserver setup using **Flask**.

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

##  Model

**Yolo11n**

- The base model is a Yolo11n (nano) the smallest and fastest model, but also least accurate 
- FPS: The camera feed usually provides a video stream of around 6-7 FPS and a resolution of 1280x720
- Stream: The stream is accessiable via a flask app setup and can be viewed while inside the local network. The stream is protected using a login and password
- Guard detection: The model is pre-trained to recognize people and create bounding boxes. Once a bounding box consits of a certain amount of yellow pixels the model will flag this as a parking guard. Simple yet effective. 

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




