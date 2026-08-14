# 🍽️ Smart AI Food Monitoring System

**Assistive Technology for College Canteens** – Powered by Raspberry Pi 5

An AI-powered system that uses a camera to recognise food on a student's tray,
estimate portion sizes using a college ID card as a reference object (no load cell),
and calculate calories & macros. Includes a modern web dashboard with charts,
accessibility features, and text-to-speech support.

---

## Project Structure

```
calories/
├── backend/                  # FastAPI backend
│   ├── main.py               # App entry point + all API endpoints
│   ├── database.py           # SQLite setup, save/query helpers
│   ├── models.py             # Pydantic response models
│   ├── camera.py             # Pi Camera capture (w/ dev fallback)
│   └── dummy_data.py         # Sample data for demo mode
├── config/
│   └── settings.py           # Central constants (ID card size, targets…)
├── data/
│   ├── food_nutrition.json   # Nutrition table (kcal, macros per 100g)
│   └── food_density.json     # Density + shape assumptions for estimation
├── frontend/
│   └── index.html            # Single-page dashboard (HTML/CSS/JS + Chart.js)
├── pipeline/                 # CV pipeline modules (Steps 2–3)
├── captures/                 # Saved camera images (auto-created)
├── models/                   # AI model files (Step 3)
├── requirements.txt          # Python dependencies
├── run.sh                    # Quick-start script
└── README.md                 # This file
```

---

## Quick Start (Raspberry Pi 5)

### 1. Prerequisites

```bash
sudo apt update
sudo apt install -y python3 python3-pip python3-venv
```

### 2. Clone / Copy project

Copy the `calories/` folder to your Pi (e.g. `~/Desktop/calories`).

### 3. Run with one command

```bash
cd ~/Desktop/calories
bash run.sh
```

This will:
- Create a Python virtualenv.
- Install all dependencies.
- Initialise the SQLite database.
- Start the FastAPI server on port 8000.

### 4. Open the Dashboard

On any device on the same Wi-Fi network, open:

```
http://raspberrypi.local:8000
```

Or use the Pi's IP address: `http://<PI_IP>:8000`.

---

## API Endpoints

| Method | Path                 | Description                          |
|--------|----------------------|--------------------------------------|
| GET    | `/health`            | Health check                         |
| GET    | `/api/current_meal`  | Latest analysed meal                 |
| POST   | `/api/capture`       | Capture image from Pi Camera         |
| POST   | `/api/analyze_meal`  | Run full AI pipeline                 |
| POST   | `/api/save_meal`     | Save current meal to database        |
| GET    | `/api/daily_stats`   | Daily calorie aggregates (7 days)    |
| GET    | `/api/recent_meals`  | Recent meals list                    |
| GET    | `/api/today_stats`   | Today's totals + calorie target      |
| GET    | `/api/summary_text`  | TTS-friendly meal summary            |

Interactive API docs: `http://raspberrypi.local:8000/docs`

---

## Dashboard Features

- **Current Meal**: camera image with food overlays, calorie & macro cards
- **Charts**: 7-day calorie trend (line), macro split (doughnut), calorie gauge
- **Recent Meals**: history table with food pills
- **Smart Alerts**: over-target warnings, low-protein notices
- **Accessibility**: high-contrast mode, large fonts, speak summary (Web Speech API)

---

## Step-by-Step Build Plan

| Step | Status | Description |
|------|--------|-------------|
| 1    | ✅ Done  | Project skeleton, backend, dashboard with dummy data |
| 2    | ⬜ Next | Camera integration |
| 3    | ⬜      | Food detection + ID card scale estimation |
| 4    | ⬜      | SQLite integration + real charts |
| 5    | ⬜      | Polish, accessibility, TTS |

---

## License

Academic project – open source for educational use.
