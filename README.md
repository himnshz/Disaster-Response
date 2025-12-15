# Disaster Response System

A sophisticated disaster management platform that leverages AI to analyze SOS messages, assess severity, and visualize critical data for emergency responders. This project consists of a Python/Flask backend and a React frontend dashboard.

## 🚀 Features

*   **AI-Powered Analysis**: Uses Google Gemini Pro to parse SOS messages, extract key details (location, urgency, needs), and detect spam/fake requests.
*   **Intelligent Severity Scoring**: Automatically prioritizes incidents based on urgency levels and resource requirements.
*   **Geolocation & Routing**: utilizing Google Maps API to convert vague location descriptions into precise coordinates and calculate optimal rescue routes.
*   **Real-time Dashboard**: A React-based interface displaying the most critical SOS messages, interactive maps, and statistical overviews.
*   **Route Planning**: Calculates estimated travel times and distances from Rescue HQ to incident locations.
*   **Nearby Services**: Automatically locates nearby hospitals, police stations, and fire stations relative to the incident.

## 🛠 Tech Stack

### Backend
*   **Python 3.x**
*   **Flask**: REST API framework.
*   **Google Gemini AI**: For natural language understanding and analysis.
*   **Google Maps API**: For geocoding, directions, and places search.

### Frontend
*   **React.js**: UI / Component library.
*   **Google Maps React**: Interactive map components.
*   **Chart.js**: For visualizing data and statistics.
*   **Lucide React**: For icons.

## 📋 Prerequisites

Before running the project, ensure you have the following installed:
*   [Python 3.8+](https://www.python.org/downloads/)
*   [Node.js](https://nodejs.org/en/) (v14 or higher) & npm

### API Keys
You will need API keys for the following services:
1.  **Google Gemini API Key**: [Get it here](https://aistudio.google.com/app/apikey)
2.  **Google Maps API Key**: [Get it here](https://console.cloud.google.com/google/maps-apis/credentials) (Enable Geocoding API, Directions API, and Places API)

## ⚙️ Installation & Setup

### 1. Backend Setup

Navigate to the backend directory:
```bash
cd backend
```

Install the required Python dependencies:
```bash
pip install -r requirements.txt
```

Create a `.env` file in the `backend` folder and add your API keys:
```env
GEMINI_API_KEY=your_gemini_api_key_here
GOOGLE_MAPS_API_KEY=your_google_maps_api_key_here
```

### 2. Frontend Setup

Navigate to the frontend directory:
```bash
cd ../disaster-response-dashboard
```

Install the Node.js dependencies:
```bash
npm install
```

## 🏃‍♂️ Running the Application

### Step 1: Pre-process Data (Backend)
Before starting the server, you need to process the raw SOS messages. This script uses the AI to analyze the text and save the results.

From the `backend` directory:
```bash
python preprocess_data.py
```
*Note: This generates a `processed_data.json` file which the API serves.*

### Step 2: Start the Backend Server
Keep the terminal open and run:
```bash
python app.py
```
The server will start at `http://localhost:5000`.

### Step 3: Start the Frontend Dashboard
Open a new terminal window, navigate to the frontend directory, and start the app:

```bash
cd disaster-response-dashboard
npm start
```
The application will open in your browser at `http://localhost:3000`.

## 📁 Project Structure

```
Disaster/
├── backend/
│   ├── app.py                # Main Flask application entry point
│   ├── ai_core.py            # AI logic (Gemini) and Geolocation functions
│   ├── preprocess_data.py    # Script to process raw CSV data into JSON
│   ├── sos_messages.csv      # Raw input data
│   ├── processed_data.json   # Output data (generated script)
│   └── requirements.txt      # Python dependencies
│
└── disaster-response-dashboard/
    ├── src/                  # React source code
    ├── public/               # Static assets
    └── package.json          # Node dependencies and scripts
```

## ⚠️ Troubleshooting

*   **Map Errors**: If the map doesn't load or verify, ensure your Google Maps API key has the "Maps JavaScript API", "Geocoding API", and "Directions API" enabled.
*   **AI Errors**: If you see "AI analysis failed", check your Gemini API key and quota limits.
*   **CORS Issues**: If the frontend cannot talk to the backend, ensure the Flask backend is running and `flask-cors` is installed and active (it is enabled by default in `app.py`).