# Real-Time Multi-Camera Object Tracking and Re-Identification System  

This project was developed during my internship at **Havelsan Teknoloji Radar (HTR)**.  
The system enables **real-time multi-object tracking (MOT)**, **cross-camera person re-identification (ReID)**, and **alarm-based monitoring** using state-of-the-art computer vision methods and a modular backend–frontend integration.  

---

## 🔍 Project Overview  

- **Goal**: Provide an **integrated surveillance system** with real-time tracking, alarm generation, and dynamic user control.  
- **Core Idea**: Once a person enters a predefined alarm zone, the system automatically starts live tracking. If the tracked person is lost, a **general search** runs across all cameras to re-identify and continue following the person seamlessly.  
- **Additional Feature**: Background sabotage detection system alerts when cameras are blocked, redirected, or tampered with.  

---

## 🚀 Features  

- **Camera Management**  
  - Add / Remove cameras dynamically  
  - Adjust camera settings via frontend controls  
  - Real-time camera switching & monitoring  

- **Dynamic Alarm Zones & Crossing Lines**  
  - Create, edit, and delete alarm areas  
  - Define crossing lines for people-flow monitoring  
  - Automatic alarm triggering when a tracked person enters restricted zones  

- **Real-Time Tracking**  
  - Multi-object tracking across multiple cameras (MOT)  
  - Live tracking of selected IDs  
  - Auto re-identification when person is lost  
  - Background global search to continue tracking across cameras  

- **Sabotage Detection**  
  - Detect if camera is blocked with transparent/solid objects  
  - Detect laser/flashlight interference  
  - Detect camera rotation or tilt changes  
  - Automatic alarm triggering with live feed focus  

- **Frontend Panel**  
  - Camera monitoring dashboard  
  - Active IDs list (select any ID to follow live)  
  - User-friendly area/line configuration tools  
  - Real-time alerts and logs  

- **Extra Functionalities**  
  - Advanced line-crossing control  
  - ID mapping  
  - Snapshot capture  
  - ReID embedding extraction  
  - Logging system for events and alarms  

---

## 🏗️ System Architecture  

- **Backend**:  
  - **YOLOv11s** for object detection  
  - **TorchReID (OSNet)** for ReID embeddings  
  - **BoT-SORT (BoxMOT fork)** for multi-object tracking (Kalman filter + IoU tracking) with custom performance improvements  
  - **Flask API** for dynamic configuration (camera/area/line updates)  
  - **GStreamer** for camera pipelines and stream processing  

- **Frontend**:  
  - WebSocket communication for real-time video transfer and controls  
  - Dynamic monitoring and camera management interface  

---

## ⚙️ Technologies Used  

- **Object Detection**: [YOLOv11s](https://github.com/ultralytics/ultralytics)  
- **Re-Identification**: [TorchReID](https://kaiyangzhou.github.io/deep-person-reid/) with **OSNet** backbone  
- **Multi-Object Tracking**: [BoT-SORT / BoxMOT](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet) (with custom modifications)  
- **Backend Framework**: Flask, Torch  
- **Data Pipeline**: GStreamer  
- **Realtime Communication**: WebSocket  
- **Frontend**: Custom monitoring dashboard  

---

## 📊 Workflow  

1. **Cameras connected via GStreamer**  
2. **Video streams sent to backend for detection & tracking**  
3. **YOLO detects persons → ReID extracts embeddings → BoT-SORT handles tracking**  
4. **Results streamed via WebSocket to frontend**  
5. **Frontend allows user to manage areas, lines, and alarms dynamically**  
6. **If sabotage detected → automatic alarm & focus on affected camera**  

---

## 🙏 Acknowledgements  

Special thanks to **Havelsan Teknoloji Radar (HTR)** for the opportunity to work on a **full-stack computer vision project** and contribute to a real-world scalable system.  
