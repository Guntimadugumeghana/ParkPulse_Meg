# ParkPulse: Smart Parking Prediction App

*Plan. Predict. Park.*

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Demo](#demo)
- [Appwrite Setup](#appwrite-setup)
- [Local Setup](#local-setup)
- [Flask Prediction Server](#flask-prediction-server)
- [Future Improvements](#future-improvements)

## Overview

ParkPulse is a **real-time smart parking solution**. It provides:

- **Live parking availability**
- **Wait-time predictions** using machine learning
- **Future planning** for parking slots (Cars, Bikes, Physically Abled)

Designed for both **users** and **admins**, ParkPulse simplifies parking during peak hours and events.

## Key Features

| Feature | Description |
|---------|-------------|
| OTP Login | Secure authentication for users |
| Live Tracking | Real-time vacancy updates for 3 slot types |
| Wait Predictions | ML-powered estimates when slots are full |
| Trip Planner | Check future availability probabilities |
| Admin Panel | Manage slots, events, and view analytics |

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React Native + Expo |
| Backend | Appwrite Cloud DB |
| ML Server | Flask (Python) |
| Styling | Tailwind CSS (NativeWind) |

## Demo

Watch the [Demo Video](https://drive.google.com/file/d/1TblDwl9gicRjzqaBoa8vXxgzsFtwGBh7/view?usp=sharing).

## Appwrite Setup

### Collections Structure

#### 1. `parking` Collection

| Key | Type | Required |
|-----|------|----------|
| Slotid | String | Yes |
| Vacancy | Boolean | Yes |
| check_in | String | No |
| check_out | String | No |
| slot_type | Enum | Yes |

#### 2. `waiting` Collection

| Key | Type | Required |
|-----|------|----------|
| slotid | String | Yes |
| wait_time | Double | No |
| check_in | String | Yes |
| check_out | String | No |
| category | Enum | Yes |

#### 3. `event` Collection

| Key | Type | Required |
|-----|------|----------|
| event_name | String | Yes |
| event_type | Enum | Yes |
| event_date | DateTime | Yes |

## Local Setup

### 1. Clone the Repository and Install Dependencies

```bash
git clone https://github.com/Pudi-Sravan/ParkPulse.git
cd ParkPulse
npm install
```

### 2. Configure Environment

Create a `.env` file with the following:

```env
EXPO_PUBLIC_APPWRITE_PROJECT_ID=your_project_id
EXPO_PUBLIC_APPWRITE_DATABASE_ID=
EXPO_PUBLIC_APPWRITE_PARKING_COLLECTION_ID=
EXPO_PUBLIC_APPWRITE_WAITLOG_COLLECTION_ID=
EXPO_PUBLIC_APPWRITE_EVENT_COLLECTION_ID=
EXPO_PUBLIC_FLASK_SERVER=http://localhost:5000
```

### 3. Start Expo

```bash
npx expo start
```

## Flask Prediction Server

For the ML prediction server setup, refer to the dedicated repository:
[Parking Availability Predictor](https://github.com/Pudi-Sravan/Parking_avl_predictor)

To connect with the Flask server locally:

1. Visit the repository linked above.
2. Follow the setup instructions in that repository.
3. Run the Flask server.
4. Ensure port 5000 is open on your system to connect locally.

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/predict_wait` | Returns wait-time estimates |
| POST | `/predict_availability` | Returns future slot availability probability |

## Future Improvements

- Camera-based slot detection
- Google Maps integration

---

**Plan. Predict. Park.** Powered by ParkPulse.
