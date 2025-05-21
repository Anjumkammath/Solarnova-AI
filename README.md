# SolarNova AI: Automatic Dust Detection & Cleaning System for Solar Panels

SolarNova AI is an intelligent, AI-powered embedded system that automatically detects dust accumulation on solar panels and activates a cleaning mechanism—all without manual intervention. Leveraging a lightweight MobileNet CNN deployed on a Raspberry Pi, the system offers a cost-effective, sustainable solution to maintaining optimal solar energy efficiency.

## 🚀 Key Features

🔍 Real-Time Image Capture and Classification

🧠 MobileNet-Based Deep Learning for Dust Detection

⚙️ Automated Cleaning via Servo/Stepper Motors

🧩 Embedded Deployment on Raspberry Pi

💸 Low-Cost and Eco-Friendly Maintenance

♻️ Reduces Manual Labor and Increases Solar Output Efficiency


### 🧠 How It Works

Image Capture
A camera module (USB or Pi Camera) continuously monitors the solar panel surface.

Preprocessing
Captured images are resized to 224x224 and normalized for MobileNet input.

Classification
A fine-tuned MobileNet model classifies the panel state as "Clean" or "Dusty".

Action Trigger
If dust is detected confidently, the Raspberry Pi activates a cleaning mechanism using servo/stepper motors.

Continuous Monitoring
The system runs in real-time, ensuring consistent performance and maximum solar output.


#### 🛠️ Tech Stack

Technology	Purpose
Python	Scripting and Integration
TensorFlow/Keras	Deep learning model development
OpenCV	Image processing and camera integration
MobileNet	Lightweight CNN for classification
Raspberry Pi	Edge computing device
Servo/Stepper Motors	Hardware for the cleaning mechanism
Camera Module / USB Webcam	for image acquisition

##### ⚙️ Setup and Usage Instructions

1️⃣ Environment Setup
Use a virtual environment (recommended):

bash
Copy
Edit
python3 -m venv solarnova-env
source solarnova-env/bin/activate  # Linux/macOS
bash
Copy
Edit
solarnova-env\Scripts\activate  # Windows
Install the required dependencies:

bash
Copy
Edit
pip install -r requirements.txt

2️⃣ Prepare Dataset
📦 Download the dataset (~1GB):
👉 Download Detect_Solar_Dust (Insert Google Drive or relevant link)

Organize the dataset as follows:

bash
Copy
Edit
dataset/
├── clean/      # Images of clean solar panels
└── dirt/       # Images of dusty solar panels
📝 Ensure images have a resolution of at least 400x800 pixels.
The training script will automatically resize them.

3️⃣ Train the Model
Run the training script:

bash
Copy
Edit
python src/train_model.py
This will:

Load a pre-trained MobileNet model

Fine-tune it using your dataset

Save the trained model as FineTuned_MobileNet.h5

4️⃣ Convert to TensorFlow Lite
Convert the model for lightweight edge deployment:

bash
Copy
Edit
python src/convert_to_tflite.py
This will generate:

tflite_model.tflite → Optimized for Raspberry Pi

5️⃣ Run Live Dust Detection & Cleaning
Execute the live inference and control script:

bash
Copy
Edit
python src/predict_live.py
Features:
Captures live video frames

Performs inference every 2 seconds

If dust is detected with confidence > 0.90, it activates cleaning motors

Displays live feed with real-time classification

Stops when you press q

🔐 On Raspberry Pi, for GPIO access, you may need to use:

bash
Copy
Edit

🔧 Hardware & Configuration Notes
Ensure the camera is correctly connected and accessible (/dev/video0 for Linux/RPi or 0 for OpenCV).

GPIO pin configurations and motor logic should be updated in predict_live.py based on your hardware setup.

The cleaning mechanism uses stepper motors controlled through a motor driver (e.g., L298N or ULN2003).

###### 📚 Publication

📖 SolarNova AI: Dynamic Dust Detection, Cleaning, and Panel Orientation for Enhanced Solar Efficiency with AI Technologies
Advances in Intelligent Systems and Computing, Springer, 2024
🔗 Read the paper on Springer

🙋 Contact & Support
For queries, feature requests, or contributions, please open an issue or contact the maintainer.

🌱 Acknowledgments
Thanks for exploring SolarNova AI — promoting clean energy through smart automation.
Let’s make solar smarter, cleaner, and more efficient — together!p
Install Python and the required packages. It's recommended to use a virtual environment:

python3 -m venv solarnova-env source solarnova-env/bin/activate # On Linux/MacOS

OR
solarnova-env\Scripts\activate # On Windows

Install dependencies:

2. Prepare the Dataset
📦 Dataset Download
The full Solar Dust Detection dataset (~1 GB) is available via Google Drive:

👉 Download Detect_solar_dust

Organize your images into the following structure:

dataset/ ├── clean/ # Images of clean solar panels └── dirt/ # Images of dusty solar panels

Ensure images are of sufficient resolution (preferably ≥400x800 pixels). The training script handles resizing.

3. Training the Model
Train the MobileNet-based classifier on your dataset by running:

python src/train_model.py

This script will:

Load a pre-trained MobileNet model (MobileNet.h5)
Fine-tune it on your clean and dusty solar panel images
Save the fine-tuned model as FineTuned_Mobilenet.h5
4. Convert Fine-Tuned Model to TensorFlow Lite
For optimized inference on the Raspberry Pi, convert your .h5 model to TensorFlow Lite format:

python src/convert_to_tflite.py

This script will:

Load FineTuned_Mobilenet.h5
Convert it to tflite_model.tflite for lightweight deployment
5. Run Real-Time Dust Detection and Cleaning
Run the live inference and cleaning control script on the Raspberry Pi:

python src/predict_live.py

Features:

Captures live frames from the connected camera
Runs TensorFlow Lite model inference every 2 seconds
If dust is detected with confidence > 0.9, it activates the stepper motors to clean the panels
Displays live camera feed with real-time updates
Stops when you press q
Additional Notes
Make sure your camera device is accessible (/dev/video0 on Linux/RPi or 0 for OpenCV).

Adjust GPIO pin assignments and motor steps in predict_live.py to your hardware setup.

You may need to run scripts with sudo on the Raspberry Pi for GPIO access:

sudo python src/predict_live.py

📚 Publications
"SolarNova AI: Dynamic Dust Detection, Cleaning, and Panel Orientation for Enhanced Solar Efficiency with AI TechnologiesAdvances in Intelligent Systems and Computing, Springer, 2024.
https://link.springer.com/chapter/10.1007/978-981-96-0228-5_14
Contact & Support
For questions or issues, please open an issue or contact the maintainer.

Thank you for choosing SolarNova AI — automating clean solar energy!






