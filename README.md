# 🌞 SolarNova AI: Automatic Dust Detection & Cleaning System for Solar Panels

**SolarNova AI** is an intelligent, AI-powered embedded system that detects dust accumulation on solar panels and autonomously triggers a cleaning mechanism—without manual intervention. Built using a fine-tuned MobileNet CNN and deployed on a Raspberry Pi, the system ensures optimal solar panel performance in a cost-effective, sustainable manner.

---

## 🚀 Key Features

- 🔍 **Real-Time Image Capture & Classification**
- 🧠 **MobileNet-Based Deep Learning for Dust Detection**
- ⚙️ **Automated Cleaning via Servo/Stepper Motors**
- 🧩 **Embedded Deployment on Raspberry Pi**
- 💸 **Low-Cost & Eco-Friendly Maintenance**
- ♻️ **Reduces Manual Labor, Improves Solar Efficiency**

---

## 🧠 How It Works

1. **Image Capture**  
   A USB or Pi Camera module continuously monitors the surface of the solar panel.

2. **Preprocessing**  
   Captured images are resized to 224x224 and normalized to match MobileNet’s input requirements.

3. **Classification**  
   The MobileNet model classifies the panel as either `Clean` or `Dusty`.

4. **Action Trigger**  
   If dust is detected with high confidence (> 0.90), the Raspberry Pi activates a cleaning mechanism using servo or stepper motors.

5. **Continuous Monitoring**  
   The system runs in real-time, ensuring uninterrupted efficiency and performance.

---

## 🛠️ Tech Stack

| Technology           | Purpose                                 |
|----------------------|------------------------------------------|
| **Python**           | Scripting and automation                 |
| **TensorFlow/Keras** | Deep learning model training             |
| **OpenCV**           | Image acquisition and preprocessing      |
| **MobileNet**        | Lightweight CNN model for classification |
| **Raspberry Pi**     | Embedded AI computing                    |
| **Servo/Stepper Motors** | Hardware for cleaning mechanism    |
| **USB Camera**       | Image capture and surveillance           |

---

## ⚙️ Setup & Usage Instructions

### 1️⃣ Environment Setup

Create a virtual environment (recommended):

```bash
python3 -m venv solarnova-env
source solarnova-env/bin/activate  # For Linux/macOS
```

Or, for Windows:

```bash
solarnova-env\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

### 2️⃣ Prepare Dataset

📦 Download the dataset (~1GB):  
👉 [Download Detect_Solar_Dust](#) *(Insert Google Drive or relevant link)*

Organize images into the following structure:

```
dataset/
├── clean/    # Images of clean solar panels
└── dirt/     # Images of dusty solar panels
```

> 📝 Ensure images have a minimum resolution of 400x800 pixels.  
The training script will automatically resize them to 224x224.

---

### 3️⃣ Train the Model

Train the MobileNet-based model with your dataset:

```bash
python src/train_model.py
```

This script will:

- Load a pre-trained MobileNet model
- Fine-tune it on the clean/dusty dataset
- Save the model as `FineTuned_MobileNet.h5`

---

### 4️⃣ Convert Model to TensorFlow Lite

Convert the fine-tuned `.h5` model to `.tflite` for optimized edge deployment:

```bash
python src/convert_to_tflite.py
```

This will generate:

```
tflite_model.tflite  → Optimized for Raspberry Pi
```

---

### 5️⃣ Run Real-Time Detection & Cleaning

Execute the live detection and cleaning control script:

```bash
python src/predict_live.py
```

**Features:**

- Captures live frames from the camera
- Runs TensorFlow Lite inference every 2 seconds
- Triggers cleaning motors when dust is detected (confidence > 0.90)
- Displays real-time video feed with classification results
- Press `q` to quit

> 🔐 For GPIO access on Raspberry Pi, run with sudo:

```bash
sudo python src/predict_live.py
```

---

## 🔧 Hardware & Configuration Notes

- Ensure the camera is accessible (`/dev/video0` for Linux/RPi or `0` in OpenCV).
- Update GPIO pin numbers and motor logic in `predict_live.py` according to your circuit.
- Use motor driver boards like **L298N** or **ULN2003** for motor control.
- Test motors and camera independently before integration.

---

## 📚 Publication

📄 **Title:** *SolarNova AI: Dynamic Dust Detection, Cleaning, and Panel Orientation for Enhanced Solar Efficiency with AI Technologies*  
📚 *Published in:* Advances in Intelligent Systems and Computing, Springer, 2024  
🔗 [Read the full paper on Springer](https://link.springer.com/chapter/10.1007/978-981-96-0228-5_14)

---

## 🙋 Contact & Support

For questions, contributions, or bug reports:  
🔧 Open an issue on the [GitHub repository](#) or contact the project maintainer.

---

## 🌱 Acknowledgments

Thank you for exploring **SolarNova AI** — helping shape a cleaner, more energy-efficient future through intelligent automation.

> 💡 *Let’s make solar energy smarter and cleaner — together!*
