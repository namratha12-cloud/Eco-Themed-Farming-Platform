
# 🌿 Eco-Themed Farming Platform — KrishiSarthi AI

> **An intelligent, full-stack farming assistant powered by YOLOv8 computer vision, real-time weather APIs, and a multilingual AI chatbot — built to empower Indian farmers with smart, eco-friendly tools.**

---

## 📋 Table of Contents

1. [Project Overview](#-project-overview)
2. [Live Features](#-live-features)
3. [Tech Stack](#-tech-stack)
4. [Project Structure](#-project-structure)
5. [AI & ML Models](#-ai--ml-models)
6. [Backend API Reference](#-backend-api-reference)
7. [Frontend Pages](#-frontend-pages)
8. [Database Schema](#-database-schema)
9. [Setup & Installation](#-setup--installation)
10. [Environment Variables](#-environment-variables)
11. [Running Locally](#-running-locally)
12. [Screenshots](#-screenshots)
13. [Credits & Attributions](#-credits--attributions)

---

## 🌾 Project Overview

**KrishiSarthi AI** (KrishiSarthi = "Farmer's Guide" in Sanskrit) is an eco-themed smart farming web platform designed for Indian farmers. It combines modern AI/ML models with real government data APIs to help farmers:

- **Detect crop diseases** via image scanning
- **Identify wildlife threats** near their farmland
- **Get smart irrigation advice** based on crop type and soil moisture
- **View live market prices** from official Mandi records
- **Receive weather forecasts** with farming-specific climate alerts
- **Consult an AI chatbot** in English, Kannada (ಕನ್ನಡ), and Hindi (हिंदी)
- **Analyze soil health** with structured recommendations
- **Get daily farming advisories**

---

## ✨ Live Features

| Feature | Description | Status |
|---|---|---|
| 🔐 Auth (Register/Login) | Farmer authentication with hashed passwords | ✅ Active |
| 🌿 Crop Disease Scanner | YOLOv8-based image analysis for plant disease | ✅ Active |
| 🦌 Wildlife Detection | Dual YOLOv8 model (Detection + Classification) | ✅ Active |
| 💧 Irrigation Advisor | Physics-based irrigation calculator | ✅ Active |
| ☁️ Weather Forecast | OpenWeatherMap 5-day forecast + climate alerts | ✅ Active |
| 📈 Market Prices | Live data from data.gov.in Mandi API | ✅ Active |
| 🤖 AI Chatbot (KrishiSarthi) | Multilingual chatbot (EN / KN / HI) | ✅ Active |
| 🌱 Soil Analysis | Soil health scoring and recommendations | ✅ Active |
| 📅 Daily Advisory | Context-aware daily farming tips | ✅ Active |
| 👤 Farmer Profile | View and update profile details | ✅ Active |

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| **React 18** + **TypeScript** | Core UI framework |
| **Vite 6** | Build tool & dev server |
| **React Router DOM** | Client-side routing |
| **Recharts** | Data visualization / charts |
| **Radix UI** | Accessible UI primitives |
| **Lucide React** | Icon library |
| **Motion** (Framer Motion) | Animations |
| **Tailwind CSS** | Utility-first styling |
| **React Hook Form** | Form handling |
| **next-themes** | Dark/Light mode support |
| **Sonner** | Toast notifications |

### Backend
| Technology | Purpose |
|---|---|
| **Python 3.x** | Server-side language |
| **Flask** | Lightweight web framework |
| **Flask-CORS** | Cross-Origin Resource Sharing |
| **Ultralytics YOLOv8** | Object detection & classification |
| **Pillow (PIL)** | Image processing |
| **NumPy** | Numerical computations |
| **Werkzeug** | File handling & security |
| **SQLite** | Local relational database |
| **Requests** | External HTTP API calls |

### External APIs
| API | Used For |
|---|---|
| **OpenWeatherMap** (`/data/2.5/forecast`) | 5-day weather forecast |
| **data.gov.in** (`/resource/9ef84268...`) | Live Mandi/Market prices |

---

## 📁 Project Structure

```
Eco-Themed Farming Platform/
├── backend/
│   ├── app.py                         # Flask application entry point
│   ├── db/
│   │   ├── config.py                  # SQLite DB connection & schema init
│   │   └── farmer.db                  # SQLite database file
│   ├── models/
│   │   ├── crop_disease/
│   │   │   ├── predict.py             # YOLOv8 disease detection inference
│   │   │   └── best.pt                # Custom-trained YOLOv8 weights
│   │   ├── crops_classification/
│   │   │   ├── train.py               # Training script (YOLOv8s-cls)
│   │   │   ├── data.yml               # Dataset configuration
│   │   │   └── best.pt                # Trained classification weights
│   │   ├── irrigation/                # Irrigation model logic
│   │   ├── market/                    # Market model logic
│   │   └── soil/                      # Soil analysis logic
│   ├── routes/
│   │   ├── auth.py                    # Register, Login, Profile CRUD
│   │   ├── chatbot_routes.py          # Multilingual AI chatbot
│   │   ├── crop_classification.py     # Crop type classification route
│   │   ├── crop_routes.py             # Disease scan upload & DB save
│   │   ├── market_routes.py           # Market price with fuzzy search
│   │   ├── weather_routes.py          # Weather + Irrigation calculator
│   │   └── wildlife_routes.py         # Wildlife detection route
│   ├── uploads/                       # Temporary image upload directory
│   └── yolov8n.pt                     # YOLOv8 Nano detection weights
├── frontend/
│   └── src/
│       ├── App.tsx                    # Application router & auth guard
│       ├── main.tsx                   # React entry point
│       ├── index.css                  # Global styles
│       ├── components/
│       │   ├── CropScanner.tsx        # Crop disease scan UI
│       │   ├── Dashboard.tsx          # Main farmer dashboard
│       │   ├── DailyAdvisory.tsx      # Daily farming tips
│       │   ├── FloatingChatbot.tsx    # AI chatbot widget
│       │   ├── IrrigationAdvisor.tsx  # Water needs calculator UI
│       │   ├── Layout.tsx             # App layout shell
│       │   ├── LoginPage.tsx          # Login form
│       │   ├── RegisterPage.tsx       # Registration form
│       │   ├── MarketPrediction.tsx   # Market price lookup UI
│       │   ├── MarketPrice.tsx        # Market price display
│       │   ├── Profile.tsx            # Farmer profile page
│       │   ├── SoilAnalysis.tsx       # Soil analysis UI
│       │   ├── WeatherForecast.tsx    # Weather display UI
│       │   ├── WildlifeDetection.tsx  # Wildlife detection UI
│       │   └── ui/                    # Reusable Radix UI components
│       └── utils/
│           └── LanguageContext.tsx    # Multilingual context provider
├── yolov8n.pt                         # Root YOLOv8 Nano (detection)
├── yolov8n-cls.pt                     # YOLOv8 Nano classification weights
├── yolov8s-cls.pt                     # YOLOv8 Small classification weights
├── package.json                       # Frontend dependencies
├── vite.config.ts                     # Vite configuration
└── README.md                          # This file
```

---

## 🤖 AI & ML Models

### 1. 🌿 Crop Disease Detection — YOLOv8

| Property | Value |
|---|---|
| **Framework** | Ultralytics YOLOv8 |
| **Model File** | `backend/models/crop_disease/best.pt` |
| **Fallback** | `yolov8n.pt` (Nano) if custom weights missing |
| **Input** | Image (PNG/JPG/JPEG/BMP/WEBP) |
| **Confidence Threshold** | 0.30 (30%) |
| **Input Size** | 640×640 px |
| **Output** | List of `{class_id, label, confidence, box[x1,y1,x2,y2]}` |
| **Task** | Object Detection |

**Inference Pipeline:**
```python
# Load model
model = YOLO("best.pt")

# Predict
results = model.predict(source=image_path, conf=0.30, imgsz=640)

# Extract detections
for box in results[0].boxes:
    label      = model.names[int(box.cls)]
    confidence = float(box.conf)
    bbox       = box.xyxy.tolist()  # [x1, y1, x2, y2]
```

---

### 2. 🦌 Wildlife Detection — Dual YOLOv8 Pipeline

The wildlife detection module uses a **two-model ensemble strategy** for higher accuracy:

| Model | File | Task | Purpose |
|---|---|---|---|
| **Detection (YOLOv8n)** | `yolov8n.pt` | Object Detection | Count animals, locate Elephants |
| **Classification (YOLOv8n-cls)** | `yolov8n-cls.pt` | Image Classification | Identify specific animal species |

**Decision Logic:**
```
IF detection model finds specific animal (e.g., Elephant) with high confidence
    → Use detection result
ELSE IF classification model identifies a known animal
    → Use classification result (Monkey, Deer, Wild Boar, etc.)
ELSE
    → Return "Unknown" with low threat level
```

**Threat Level Mapping:**

| Animal | Threat Level |
|---|---|
| Wild Boar | 🔴 High |
| Elephant | 🔴 High |
| Monkey | 🟡 Medium |
| Deer | 🟢 Low |
| Unknown | 🟢 Low |

**Supported Classes:**
- Wild Boar / Boar / Hog
- Elephant / Tusker
- Monkey / Baboon / Macaque / Chimpanzee / Gorilla
- Deer / Fallow Deer / Impala / Gazelle / Elk / Moose
- Tiger / Lion / Leopard / Bear / Wolf / Fox / Bird

---

### 3. 🌱 Crop Classification — YOLOv8s-cls (Custom Training)

A custom-trained image classification model for identifying crop types.

| Property | Value |
|---|---|
| **Base Model** | `yolov8s-cls.pt` (YOLOv8 Small, Classification) |
| **Training Script** | `backend/models/crops_classification/train.py` |
| **Epochs** | 50 |
| **Image Size** | 224×224 px |
| **Batch Size** | 16 |
| **Config File** | `data.yml` (user-configured) |

**Training Command:**
```bash
cd backend/models/crops_classification
python train.py
```

---

### 4. 💧 Irrigation Calculator — Physics-Based Model

Not a neural network — this is a **mathematical model** based on agronomy constants.

**Formula:**
```
raw_need_mm = (base_water_need × stage_multiplier) + (temp_excess × temp_factor)
final_mm    = raw_need_mm × (100 - soil_moisture) / 50
```

**Supported Crops & Base Water Needs:**

| Crop | Base (mm/day) | Temp Factor |
|---|---|---|
| Rice | 12.0 | 0.5 |
| Sugarcane | 8.0 | 0.4 |
| Cotton | 6.0 | 0.3 |
| Tomato | 5.5 | 0.35 |
| Wheat | 5.0 | 0.2 |
| Potato | 4.5 | 0.25 |

**Growth Stage Multipliers (Rice example):**
| Stage | Multiplier |
|---|---|
| Germination | 1.2× |
| Vegetative | 1.5× |
| Flowering | 2.0× |
| Fruiting | 1.8× |

---

### 5. 🤖 KrishiSarthi AI Chatbot — Rule-Based NLU

A multilingual, intent-based chatbot supporting **English**, **Kannada**, and **Hindi**.

**Intent Categories:**
| Intent | Trigger Keywords |
|---|---|
| Market/Price | `price`, `market`, `mandi`, `rate`, `ಬೆಲೆ`, `ಮಾರುಕಟ್ಟೆ`, `कीमत`, `मंडी` |
| Weather | `weather`, `forecast`, `rain`, `ಹವಾಮಾನ`, `मौसम` |
| Crop/Season | `crop`, `plant`, `season`, `ಬೆಳೆ`, `ಕೃಷಿ`, `फसल`, `खेती` |
| Greeting | `hi`, `hello`, `ನಮಸ್ಕಾರ`, `नमस्ते` |

**Seasonal Crop Knowledge Base:**

| Season | English Crops | Kannada Crops |
|---|---|---|
| Rabi (Oct–Mar) | Wheat, Barley, Gram, Peas, Mustard, Lentil | ಗೋಧಿ, ಬಾರ್ಲಿ, ಕಡಲೆ |
| Kharif (Jun–Sep) | Rice, Maize, Cotton, Soybean, Bajra, Jowar | ಅಕ್ಕಿ, ಮೆಕ್ಕೆಜೋಳ, ಹತ್ತಿ |

---

## 📡 Backend API Reference

**Base URL:** `http://localhost:5000`

---

### 🔐 Authentication

#### `POST /register`
Register a new farmer account.

**Request Body:**
```json
{
  "name": "Ramesh Kumar",
  "email": "ramesh@example.com",
  "password": "securepassword",
  "phone": "9876543210",
  "location": "Mysore, Karnataka"
}
```

**Response:** `201 Created`
```json
{ "message": "Farmer registered successfully!" }
```

---

#### `POST /login`
Authenticate a farmer.

**Request Body:**
```json
{
  "email": "ramesh@example.com",
  "password": "securepassword"
}
```

**Response:** `200 OK`
```json
{ "authenticated": true, "farmer_id": 1 }
```

---

#### `GET /profile?farmer_id=1`
Get farmer profile details.

**Response:** `200 OK`
```json
{
  "id": 1,
  "name": "Ramesh Kumar",
  "email": "ramesh@example.com",
  "phone": "9876543210",
  "location": "Mysore, Karnataka"
}
```

---

#### `POST /update-profile`
Update farmer profile.

**Request Body:**
```json
{
  "farmer_id": 1,
  "name": "Ramesh K",
  "email": "ramesh@example.com",
  "phone": "9876543210",
  "location": "Bangalore, Karnataka"
}
```

---

### 🌿 Crop Disease Detection

#### `POST /scan-crop`
Upload an image to detect crop diseases.

**Request:** `multipart/form-data`
| Field | Type | Required | Description |
|---|---|---|---|
| `image` | File | ✅ | Crop image (PNG/JPG/JPEG/BMP/WEBP) |
| `farmer_id` | String | ❌ | Links scan record to farmer in DB |

**Response:** `200 OK`
```json
{
  "image": "/path/to/saved/image.jpg",
  "detections": [
    {
      "class_id": 2,
      "label": "Leaf Rust",
      "confidence": 0.87,
      "box": [120.5, 45.2, 380.1, 290.8]
    }
  ]
}
```

---

#### `GET /my-scans?farmer_id=1`
Retrieve all previous scans for a farmer.

**Response:** `200 OK`
```json
[
  {
    "id": 1,
    "farmer_id": 1,
    "image_path": "...",
    "crop_type": null,
    "disease": "Leaf Rust",
    "confidence": 0.87,
    "scan_date": "2025-03-05 10:30:00"
  }
]
```

---

### 🦌 Wildlife Detection

#### `POST /detect-wildlife`
Upload an image to detect wildlife and assess threat level.

**Request:** `multipart/form-data`
| Field | Type | Required |
|---|---|---|
| `image` | File | ✅ |

**Response:** `200 OK`
```json
{
  "animal": "Wild Boar",
  "raw_label": "",
  "confidence": 84,
  "threatLevel": "high",
  "count": 2
}
```

---

### ☁️ Weather & Irrigation

#### `GET /weather?city=Mysore`
Get 5-day weather forecast with farming-specific climate alerts.

**Response:** `200 OK`
```json
{
  "forecast": [
    {
      "day": "2025-03-05",
      "temp": 35.2,
      "humidity": 72,
      "rain": 12.4,
      "wind": 15.3,
      "condition": "clouds"
    }
  ],
  "alerts": [
    {
      "type": "heat",
      "severity": "medium",
      "title": "Heatwave Warning",
      "description": "Temperature may reach 38°C",
      "icon": "sun"
    }
  ],
  "recommendations": [
    "Irrigate during early morning or late evening.",
    "Use shade nets for vegetables during peak afternoon."
  ]
}
```

**Climate Alert Types:**
| Type | Trigger Condition |
|---|---|
| 🌊 `flood` | Rain ≥ 80 mm |
| 🔥 `heat` | Temp ≥ 38°C |
| 🌵 `drought` | Rain < 5 mm AND Humidity < 40% |
| 🌪️ `storm` | Wind > 40 km/h |

---

#### `POST /irrigation`
Calculate irrigation water requirement.

**Request Body:**
```json
{
  "crop": "rice",
  "stage": "flowering",
  "temperature": 30.5,
  "soilMoisture": 35.0
}
```

**Response:** `200 OK`
```json
{
  "waterLevel": 76.4,
  "amount": 19.1,
  "frequency": "daily",
  "status": "high",
  "tips": [
    "The flowering stage for Rice requires precise watering.",
    "Current moisture is 35%, adjusted need is 19.1 mm.",
    "Consider drip irrigation to maximize absorption."
  ]
}
```

---

### 📈 Market Prices

#### `GET /market?commodity=wheat&state=Karnataka&district=Mysore`

Get live Mandi market prices with fuzzy matching on commodity and district names.

| Parameter | Required | Description |
|---|---|---|
| `commodity` | ✅ | Crop name (fuzzy matched) |
| `state` | ✅ | Indian state name |
| `district` | ❌ | District for narrowed results |

**Response:** `200 OK`
```json
{
  "commodity_used": "Wheat",
  "count": 5,
  "results": [
    {
      "state": "Karnataka",
      "district": "Mysore",
      "market": "Mysore",
      "commodity": "Wheat",
      "variety": "Dara",
      "arrival_date": "05/03/2025",
      "min_price": "2100",
      "max_price": "2300",
      "modal_price": "2200"
    }
  ]
}
```

> ℹ️ Data sourced from **Government of India Open Data Platform** (data.gov.in). Cache refreshes every **6 hours**.

---

### 🤖 Chatbot

#### `POST /chatbot`
Query the KrishiSarthi AI assistant.

**Request Body:**
```json
{
  "message": "what should I plant this season?",
  "lang": "en"
}
```

**Supported Languages:** `"en"` (English), `"kn"` (ಕನ್ನಡ), `"hi"` (हिंदी)

**Response:** `200 OK`
```json
{
  "message": "We are currently in the Rabi window. I recommend planting Wheat, Barley, Gram, Peas, Mustard, Lentil for the best yield based on current climate trends."
}
```

---

## 🖥 Frontend Pages

| Route | Component | Description |
|---|---|---|
| `/login` | `LoginPage.tsx` | Farmer login with auth guard |
| `/register` | `RegisterPage.tsx` | New farmer registration |
| `/home` | `Dashboard.tsx` | Main dashboard overview |
| `/scan` | `CropScanner.tsx` | Upload image for disease scan |
| `/soil` | `SoilAnalysis.tsx` | Soil health analysis & tips |
| `/water` | `IrrigationAdvisor.tsx` | Smart irrigation calculator |
| `/weather` | `WeatherForecast.tsx` | 5-day forecast with alerts |
| `/wildlife` | `WildlifeDetection.tsx` | Upload image for wildlife ID |
| `/market` | `MarketPrediction.tsx` | Live market price lookup |
| `/advisory` | `DailyAdvisory.tsx` | Daily farming tips |
| `/profile` | `Profile.tsx` | Farmer profile management |

All routes except `/login` and `/register` are **protected** — unauthenticated users are automatically redirected to `/login`.

The floating `FloatingChatbot.tsx` widget is accessible on all authenticated pages.

---

## 🗄 Database Schema

**Database:** SQLite (`backend/db/farmer.db`)

### `farmers` Table
```sql
CREATE TABLE IF NOT EXISTS farmers (
    id            INTEGER  PRIMARY KEY AUTOINCREMENT,
    name          TEXT     NOT NULL,
    email         TEXT     UNIQUE NOT NULL,
    password_hash TEXT     NOT NULL,
    phone         TEXT,
    location      TEXT
);
```

### `crop_scans` Table
```sql
CREATE TABLE IF NOT EXISTS crop_scans (
    id          INTEGER   PRIMARY KEY AUTOINCREMENT,
    farmer_id   INTEGER   NOT NULL,
    image_path  TEXT      NOT NULL,
    crop_type   TEXT,
    disease     TEXT,
    confidence  REAL,
    scan_date   DATETIME  DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (farmer_id) REFERENCES farmers(id)
);
```

---

## ⚙️ Setup & Installation

### Prerequisites

| Tool | Version |
|---|---|
| Python | 3.9+ |
| Node.js | 18+ |
| npm | 9+ |

---

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/eco-farming-platform.git
cd "Eco-Themed Farming Platform"
```

---

### 2. Backend Setup

```bash
# Navigate to backend
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install Python dependencies
pip install flask flask-cors ultralytics pillow numpy werkzeug requests
```

**Initialize the Database:**
```bash
python db/config.py
# Output: Database initialized at .../farmer.db
```

---

### 3. Frontend Setup

```bash
# From project root
npm install
```

---

## 🔑 Environment Variables

### Backend (`backend/routes/weather_routes.py`)
Replace the placeholder with your actual API key:
```python
API_KEY = "YOUR_OPENWEATHERMAP_API_KEY"
```

Get a free key at: [openweathermap.org/api](https://openweathermap.org/api)

### Market API (`backend/routes/market_routes.py`)
The Government of India Mandi API key is already included:
```python
API_KEY = "579b464db66ec23bdd00000133b7171dbff644fc56fcaf9edfb59f18"
```

---

## 🚀 Running Locally

### Start the Backend (Flask)

```bash
cd backend
# Activate venv first
python app.py
# Server starts at: http://localhost:5000
```

### Start the Frontend (Vite)

```bash
# From project root
npm run dev
# App available at: http://localhost:5173
```

Open your browser and go to: **http://localhost:5173**

---

## 📸 Screenshots

> *The platform features a modern eco-themed dark UI with green gradients, animated components, and a fully responsive layout.*

| Page | Description |
|---|---|
| Dashboard | KPI cards, quick navigation, ecological theme |
| Crop Scanner | Drag-and-drop image upload with bounding box results |
| Wildlife Detection | Threat level display (High/Medium/Low) with count |
| Market Prices | Fuzzy-search across 500+ records with state/district filter |
| Weather Forecast | 5-day cards with climate alert badges |
| Irrigation Advisor | Visual water gauge with crop-stage details |
| KrishiSarthi Chatbot | Floating chat widget with language switcher |

---

## 📦 Model Files Summary

| File | Size | Purpose |
|---|---|---|
| `yolov8n.pt` | ~6.5 MB | Wildlife detection (COCO classes) |
| `yolov8n-cls.pt` | ~5.5 MB | Wildlife classification (species ID) |
| `yolov8s-cls.pt` | ~12.8 MB | Crop classification (base for training) |
| `backend/models/crop_disease/best.pt` | Custom | Crop disease detection (trained) |
| `backend/models/crops_classification/best.pt` | ~20 MB | Crop type classification (trained) |

---

## 📜 Credits & Attributions

- **YOLOv8** — [Ultralytics](https://github.com/ultralytics/ultralytics) — AGPL-3.0 License
- **Market Data** — [data.gov.in](https://data.gov.in) — Government of India Open Data Platform
- **Weather Data** — [OpenWeatherMap](https://openweathermap.org/) — Free Tier API
- **UI Components** — [Radix UI](https://www.radix-ui.com/) — MIT License
- **Icons** — [Lucide React](https://lucide.dev/) — ISC License
- **Charts** — [Recharts](https://recharts.org/) — MIT License

---

## 👩‍💻 Author

**Namratha K N**
Eco-Themed Farming Platform | KrishiSarthi AI
*Building smart tools for sustainable Indian agriculture* 🌾

---

> ⭐ If you found this project helpful, please consider starring the repository!
