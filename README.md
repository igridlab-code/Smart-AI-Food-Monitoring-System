# 🍽️ Smart AI Food Monitoring System

### AI-Powered Food Recognition, Nutrition Analysis & Accessible Canteen Monitoring

An AI-powered food monitoring system designed for **college canteens**. The system uses a **Raspberry Pi 5 and camera** to capture a student's food tray, recognize food items, estimate portion size using a **college ID card as a reference object**, and calculate estimated calories and macronutrients.

The project also provides a modern web dashboard with nutrition charts, meal history, smart alerts, accessibility options, and text-to-speech support.

> **Academic Project – Assistive Technology for College Canteens**

---

## ✨ Key Features

- 📷 **Camera-Based Food Capture**
  - Captures food images using the Raspberry Pi camera.
  - Supports a development fallback camera mode.

- 🤖 **AI Food Recognition**
  - Designed to identify food items from the captured tray image.
  - Provides the foundation for automated meal analysis.

- 🪪 **Portion Size Estimation**
  - Uses a college ID card as a reference object.
  - Avoids the need for a load cell or weighing sensor.

- 🥗 **Nutrition Analysis**
  - Estimates:
    - Calories
    - Protein
    - Carbohydrates
    - Fat

- 📊 **Interactive Dashboard**
  - Current meal information
  - 7-day calorie trend
  - Macronutrient distribution
  - Calorie target gauge
  - Recent meal history

- 🚨 **Smart Alerts**
  - Over-calorie-target warnings
  - Low-protein notifications

- ♿ **Accessibility Support**
  - High-contrast mode
  - Large-font support
  - Speak-summary functionality using the Web Speech API

- 🗄️ **Meal History**
  - Stores analysed meals using SQLite.
  - Provides recent and daily nutrition statistics.

- 🔊 **Text-to-Speech**
  - Generates a TTS-friendly meal summary for accessible use.

---

## 🛠️ Technology Stack

| Component | Technology |
|---|---|
| Hardware | Raspberry Pi 5 |
| Camera | Raspberry Pi Camera |
| Backend | Python, FastAPI |
| Database | SQLite |
| Frontend | HTML, CSS, JavaScript |
| Charts | Chart.js |
| API Documentation | FastAPI / OpenAPI |
| Accessibility | Web Speech API |
| Nutrition Data | JSON |
| Development | Python Virtual Environment |

---

## 📁 Project Structure

```text
calories/
├── backend/
│   ├── main.py               # FastAPI application and API endpoints
│   ├── database.py           # SQLite setup and database helpers
│   ├── models.py             # Pydantic response models
│   ├── camera.py             # Raspberry Pi camera capture
│   └── dummy_data.py         # Sample data for demo mode
│
├── config/
│   └── settings.py           # Central project configuration
│
├── data/
│   ├── food_nutrition.json   # Nutrition data per 100 g
│   └── food_density.json     # Density and shape assumptions
│
├── frontend/
│   └── index.html            # Web dashboard
│
├── pipeline/                 # Computer-vision pipeline modules
├── captures/                 # Captured camera images
├── models/                   # AI model files
├── requirements.txt          # Python dependencies
├── run.sh                    # Quick-start script
└── README.md                 # Project documentation
```

---

## 🔄 System Workflow

```text
Student places food tray
          ↓
Raspberry Pi Camera
          ↓
Food Image Capture
          ↓
AI Food Recognition
          ↓
ID Card Reference Detection
          ↓
Portion Size Estimation
          ↓
Nutrition Calculation
          ↓
Calories + Protein + Carbohydrates + Fat
          ↓
SQLite Database
          ↓
Web Dashboard
          ↓
Charts + Alerts + Accessible Meal Summary
```

---

## ⚙️ Requirements

### Hardware

- Raspberry Pi 5
- Raspberry Pi Camera
- 4.3-inch display (if used in the prototype)
- College ID card for reference-based portion estimation
- Stable Wi-Fi/network connection

### Software

- Raspberry Pi OS
- Python 3
- pip
- Python virtual environment
- FastAPI
- SQLite
- Modern web browser

---

## 🚀 Installation & Quick Start

### 1. Update Raspberry Pi

```bash
sudo apt update
```

### 2. Install Python and Virtual Environment

```bash
sudo apt install -y python3 python3-pip python3-venv
```

### 3. Open the Project Directory

If the project is located on the Desktop:

```bash
cd ~/Desktop/calories
```

### 4. Run the Project

The included `run.sh` script can be used to start the system:

```bash
bash run.sh
```

The script is designed to:

1. Create a Python virtual environment.
2. Install the required dependencies.
3. Initialize the SQLite database.
4. Start the FastAPI server on port `8000`.

---

## 🌐 Open the Dashboard

After starting the server, open a browser on the Raspberry Pi or another device connected to the same Wi-Fi network.

```text
http://raspberrypi.local:8000
```

You can also use the Raspberry Pi's IP address:

```text
http://<PI_IP>:8000
```

### API Documentation

FastAPI provides interactive API documentation at:

```text
http://raspberrypi.local:8000/docs
```

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Checks whether the backend is running |
| GET | `/api/current_meal` | Returns the latest analysed meal |
| POST | `/api/capture` | Captures an image using the Pi Camera |
| POST | `/api/analyze_meal` | Runs the meal-analysis pipeline |
| POST | `/api/save_meal` | Saves the current meal |
| GET | `/api/daily_stats` | Returns daily calorie aggregates |
| GET | `/api/recent_meals` | Returns recent meal records |
| GET | `/api/today_stats` | Returns today's totals and calorie target |
| GET | `/api/summary_text` | Returns a TTS-friendly meal summary |

---

## 📊 Dashboard

The dashboard is designed to provide a simple view of the user's food and nutrition information.

### Current Meal

Displays:

- Captured food image
- Food information
- Estimated calories
- Macronutrient information

### Nutrition Charts

The dashboard includes:

- 7-day calorie trend
- Macronutrient doughnut chart
- Calorie target gauge

### Recent Meals

Displays previously analysed meals and their food information.

### Smart Alerts

The system can provide alerts for:

- Calories exceeding the configured target
- Low protein intake

---

## ♿ Accessibility

Accessibility is an important part of the system because it is designed as an assistive technology project.

The dashboard includes:

- **High-contrast mode**
- **Large-font support**
- **Speak Summary**
- **Web Speech API integration**

These features are intended to make nutrition information easier to read and listen to.

---

## 🗃️ Nutrition Data

Nutrition information is stored in JSON files inside the `data/` directory.

### `food_nutrition.json`

Contains nutrition information such as:

- Calories
- Protein
- Carbohydrates
- Fat

The nutrition table is represented on a per-100-gram basis.

### `food_density.json`

Contains density and shape assumptions used as part of portion-size estimation.

---

## 💾 Database

The project uses **SQLite** for local meal storage.

The database is used to support:

- Saving analysed meals
- Retrieving recent meals
- Calculating daily statistics
- Maintaining nutrition history

No separate database server is required for the basic project setup.

---

## 🧪 Development / Demo Mode

The project includes `backend/dummy_data.py` for sample/demo data.

This makes it possible to demonstrate the dashboard and backend functionality while individual hardware or AI pipeline components are being developed.

---

## 🏗️ Development Roadmap

| Step | Status | Description |
|---|---|---|
| 1 | ✅ Done | Project skeleton, backend, dashboard and dummy data |
| 2 | ⬜ Next | Raspberry Pi camera integration |
| 3 | ⬜ Planned | Food detection and ID-card-based scale estimation |
| 4 | ⬜ Planned | SQLite integration and real nutrition charts |
| 5 | ⬜ Planned | UI polishing, accessibility and TTS |

> The roadmap reflects the implementation status documented for this project. Features marked as planned should not be considered fully implemented until completed.

---

## 👥 Contributors

| Name | Role |
|---|---|
| **Indhumathi J** | Project Team Member |
| **Ajay K** | Project Team Member |
| **Sathya T** | Project Team Member |

## 🎯 Project Objective

The main objective of the Smart AI Food Monitoring System is to create an accessible and practical solution for monitoring food intake in college canteens.

The system aims to reduce the need for manual food measurement by combining:

**Computer Vision + AI Food Recognition + Reference-Based Portion Estimation + Nutrition Analysis + Accessible Dashboard**

This provides students with an easier way to understand the estimated nutritional value of their meals.

---

## 🌟 Advantages

- No load cell required for the proposed portion-estimation approach
- Raspberry Pi-based edge hardware
- Automated food image capture
- Nutrition information in an easy-to-understand dashboard
- Meal history and statistics
- Accessibility-focused interface
- Suitable for academic and prototype development

---

## 🔮 Future Enhancements

Possible future improvements include:

- More accurate food recognition models
- Support for a larger food dataset
- Improved portion-size estimation
- Better segmentation of multiple food items
- More accurate nutrition databases
- Personalized calorie and nutrition targets
- Cloud synchronization
- Mobile application support
- Improved multilingual accessibility
- Real-time model optimization for Raspberry Pi

---

## 👩‍💻 Project Type

**Academic / Assistive Technology Project**

**Application Area:**  
College Canteens • Food Monitoring • Nutrition Analysis • Computer Vision • AI • Accessibility

---

## 📜 License

This project is an academic project and is intended for educational and research purposes.

---

## ❤️ Acknowledgement

This project combines embedded computing, computer vision, artificial intelligence, nutrition analysis, web technologies, and accessibility concepts to develop a practical smart food monitoring solution for college environments.

**Smart AI Food Monitoring System**  
*Scan • Analyze • Eat Smart*
