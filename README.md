# AquaIntelligence – AI Pool Risk Detection Platform

AquaIntelligence is an **AI-powered insurance intelligence platform** that detects swimming pools from aerial images and evaluates insurance risk automatically.

The system combines **computer vision, machine learning, IoT monitoring, drone simulation, and fraud detection** to assist insurance companies in underwriting and claims verification.

---

## Key Features

### 🛰️ AI Pool Detection

* Detect swimming pools from aerial/satellite images using **YOLO object detection**
* Classify pool **structure type** (Inground / Aboveground)
* Detect **pool cover status** (Covered / Uncovered)
* Generate **annotated images with bounding boxes**
* Automatic **risk scoring based on pool characteristics**

### 📊 Risk Assessment Engine

* Property-level risk scoring based on:

  * Pool presence
  * Pool size
  * Pool cover status
  * Pool structure type
  * Number of pools
* Generates **LOW / MEDIUM / HIGH risk levels**
* Provides **explanations for risk factors**

### 🕐 Time-Series Fraud Detection

* Compare **before and after satellite images**
* Detect:

  * Newly added pools
  * Removed pools
  * Unchanged pools
* Identify **possible insurance fraud cases**

### 🚁 3D Drone Surveillance Simulation

* Real-time **3D drone patrol simulation** built with Pygame
* Drone autonomously navigates a **neighbourhood of 9 properties**
* Performs **AI scan of each property** to detect pool presence, type, and disclosure status
* Pool types detected: **In-ground, Above-ground, Covered, Freeform**
* Raises live **fraud alerts** for undisclosed pools
* Interactive **perspective camera** — drag to rotate, scroll to zoom, `R` to reset
* **Side panel** shows per-property scan results, risk badges, and alert log in real time
* Visual indicators:
  * 🟢 **COMPLIANT** — pool declared and confirmed
  * 🔴 **FLAGGED** — undisclosed pool detected (pulsing red ring)
  * 🟡 **PENDING** — property not yet scanned
  * ⚪ **CLEAR** — no pool found

**Run the simulation:**

```bash
pip install pygame numpy
python drone_pool_detection.py
```

### 📡 IoT Inspection System

* Accepts **ESP8266 sensor readings**
* Automatically classifies **risk level from sensor data**
* Sends **SMS alerts using Twilio** when risk is high
* Stores IoT inspection history

### 🔎 Document Fraud Detection

* Upload property documents (PDF or image)
* Extract text using **Tesseract OCR**
* Detect suspicious documents using:

  * Rule-based validation
  * **Isolation Forest anomaly detection**
* Generates **fraud risk score and recommendations**

### ⚖️ Claims Management System

* Policyholders can **submit insurance claims**
* Insurers can:

  * View claims
  * Update claim status
  * Flag potential fraud
* Claim tracking system for policyholders

### 🏠 Policyholder Registration

* Register property and declare pool information
* Store policyholder profile and pool details
* Link claims to registered policyholders

### ✉️ Communication System

* Send **email notifications via SMTP**
* Send **SMS alerts via Twilio**
* Maintain communication logs

### 📄 Reporting & GeoJSON Export

* Generate **AI underwriting reports**
* Export detected pools as **GeoJSON spatial data**
* Structured JSON reports for insurance analytics

---

## Tech Stack

### Frontend

* React (Vite)
* JavaScript
* HTML / CSS

### Backend

* Python
* FastAPI
* SQLAlchemy
* SQLite Database

### Machine Learning

* YOLO (pool detection)
* MobileNetV2 (pool structure & cover classification)
* Isolation Forest (document fraud detection)

### Drone Simulation

* Pygame (3D rendering and real-time simulation)
* NumPy (3D perspective projection math)
* Custom software renderer (no game engine dependency)

### Other Technologies

* OpenCV
* Tesseract OCR
* Twilio SMS API
* SMTP Email
* ESP8266 IoT integration

---

## Project Structure

```
project/
│
├── frontend/                     # React dashboard
│   ├── src/
│   ├── public/
│   └── package.json
│
├── dataset/                      # Sample images for testing
├── api.py                        # FastAPI backend
├── backend.py                    # YOLO + MobileNetV2 detection pipeline
├── drone_pool_detection.py       # 3D drone surveillance simulation
├── cover_classifier.pth          # Cover detection model weights
├── structure_classifier.pth      # Structure classification model weights
├── requirements.txt              # Python dependencies
└── README.md
```

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/aquaintelligence.git
cd aquaintelligence
```

---

## Backend Setup

### Install Python Dependencies

```bash
pip install -r requirements.txt
```

### Run the Backend API

```bash
uvicorn api:app --reload --port 5000
```

API documentation available at:

```
http://localhost:5000/docs
```

---

## Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs at:

```
http://localhost:5173
```

---

## Drone Simulation Setup

Install simulation dependencies (lightweight — only Pygame and NumPy):

```bash
pip install pygame numpy
```

Run the simulation:

```bash
python drone_pool_detection.py
```

**Controls:**

| Input | Action |
|---|---|
| Drag mouse | Rotate camera |
| Scroll wheel | Zoom in / out |
| `R` key | Reset camera to default view |
| `Esc` key | Exit simulation |

The drone will automatically patrol all 9 properties, scan each one, and populate the alert panel with any undisclosed pools it finds.

---

## System Workflow

1. User uploads satellite image **or** runs the drone simulation.
2. AI detects swimming pools using YOLO.
3. Pools are classified by structure and cover type.
4. Risk scoring engine evaluates property risk.
5. Fraud detection compares historical images (time-series).
6. IoT sensor data provides additional on-site inspection data.
7. Document fraud engine validates property certificates via OCR.
8. Reports and alerts are generated for insurers.

---

## Sample Dataset

A small **sample dataset (25 images)** is included in the `dataset/` folder to test the detection system.

---

## Authors

Akshay A Agile
Monish S
Annapoorna Hiremath
Dhanyasree J
