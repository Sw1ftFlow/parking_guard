# 🪙 NO MORE PARKING TICKETS

This is an end-to-end learning project using **Rasperry Pie 5**, **Logitech Brio 300**, and **YOLO11n model** to detect when a parking guard is spotted in frame and sends a sms message to the owner using **Twilio**. The live feed is accessible via a local webserver setup using **Flask**.

---

## 📌 Project Goals

- Detect parking guards before they can give you a ticket
- Set up a live feed accessible within the local network
- Send a sms warning message when a parking guard is spotted
- Automatically purchase a parking ticket when a parking guard is spotted in frame
- Log data in a csv for analytics and insights 

---

## 🛠️ Hardware

| Tool | Purpose |
|------|---------|
| **Rasperry Pie 5 (8GB)** | Run the python code, processing & model training |
| **Logitech Brio 300** | Capture Video |
| **SD Card 32GB** | Harddrive |
| **Python** | Core language |

---

## 📈 Model

**Yolo11n**

- The base model is a Yolo11n (nano) the smallest and fastest model, but also least accurate 
- FPS: The camera feed usually provides a video stream of around 6-7 FPS and a resolution of 1280x720
- Stream: The stream is accessiable via a flask app setup and can be viewed while inside the local network. The stream is protected using a login and password
- Guard detection: The model is pre-trained to recognize people and create bounding boxes. Once a bounding box consits of a certain amount of yellow pixels the model will flag this as a parking guard. Simple yet effective. 

---

## 📂 Project Structure

```text
parking_guard_detection/
├── notebooks/
│   ├── 01_ingest_data_coingecko.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_training.ipynb
├── workflows/
│   └── btc_price_predictions
├── data/
│   └── (optional sample data files)
├── README.md
├── requirements.txt
└── LICENSE
```




