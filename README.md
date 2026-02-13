# ArcFace Identity & Face Locking System

**A lightweight, privacy-focused face recognition and locking solution.**
Powered by ArcFace ONNX embeddings and 5-point facial alignment. Designed for efficiency on standard CPUs.

---

## 📥 Installation

### 1. Setup Environment
Open your terminal and run:

```bash
# Clone the repository
git clone https://github.com/Gishman-creator/FaceLocking
cd FaceLocking

# Create virtual environment
python -m venv .venv

# Activate (Windows)
.venv\Scripts\Activate

# Activate (Linux/macOS)
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Install ArcFace Model

**Option A: Automatic (Windows/Linux/Mac)**
We have provided a script to handle the download and setup for you.
```bash
python download_model.py
```

**Option B: Manual Setup**
1.  Download `buffalo_l.zip` from [InsightFace Model Zoo](https://github.com/deepinsight/insightface/releases/download/v0.7/buffalo_l.zip).
2.  Extract the zip file.
3.  Rename the file `w600k_r50.onnx` to `embedder_arcface.onnx`.
4.  Create a folder named `models` in the project root.
5.  Move `embedder_arcface.onnx` into `models/`.

---

## 🚀 Usage Guide

### 1. Verification
Ensure your hardware and software are ready:
```bash
python -m src.camera      # Check webcam feed
python -m src.landmarks   # Check facial mapping
```

### 2. Enroll Faces (Build Database)
This step saves face embeddings to the `data/` folder.
```bash
python -m src.enroll
```
*   **Enter Name**: Type a person's name in the terminal.
*   **Space**: Capture a photo manually.
*   **'a'**: Toggle auto-capture mode (recommended).
*   **'s'**: Save and finish enrollment (aim for 15+ samples).
*   **'q'**: Quit without saving.

### 3. Start Recognition
Launch the live recognition system:
```bash
python -m src.recognize
```
The system will now identify enrolled faces in real-time.

### 4. Face Locking
Lock onto a specific identity and track their actions (movements, blinks, smiles).
```bash
python -m src.facelock
```
*   **Select Identity**: Choose an enrolled user from the list.
*   **Interaction**: The system tracks the locked face and ignores others.
*   **History**: Actions are recorded in the `history/` folder.
*   **'q'**: Quit.

---

## 🔧 Troubleshooting

**"No module named mediapipe"**
Reinstall the specific compatible version:
```bash
pip install -r requirements.txt --force-reinstall
```

**Camera not opening**
*   Check if another app is using the camera.
*   Try running `python -m src.camera` to debug.

**Low Accuracy?**
*   Ensure good lighting during enrollment.
*   Capture at least 15 photos per person at different angles (left, right, up, down).
