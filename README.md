# 🌊 DeepNav AI — AI-Based Deep-Sea Navigation System

DeepNav AI is an AI-powered maritime navigation prototype developed using Python and Flask. The system simulates GPS-based vessel navigation, obstacle detection, dynamic speed adjustment, route planning, and AI-assisted pathfinding in a marine environment.

The project combines a Python Flask backend with an interactive web interface to demonstrate how intelligent navigation systems can assist vessels in making safer and more efficient navigation decisions.

> ⚠️ **Note:** DeepNav AI is a simulation and educational prototype. It does not connect to real GPS, radar, sonar, LiDAR, or vessel-control hardware.

---

## 🚀 Features

### 🛰️ GPS-Based Navigation
- Accepts starting and destination GPS coordinates.
- Calculates distance between GPS points using the Haversine formula.
- Calculates the bearing and heading between coordinates.
- Generates marine routes using SeaRoute.

### 🤖 AI Navigation & Pathfinding
- Uses the **A\* pathfinding algorithm** on a 20×20 navigation grid.
- Detects and avoids simulated obstacles.
- Generates alternative paths when obstacles are detected.
- Provides AI-assisted navigation decisions based on obstacle conditions.

### ⚠️ Surface Obstacle Detection
The system classifies obstacles into three threat levels:

| Distance | Threat Level | Navigation Response |
|----------|--------------|---------------------|
| > 100 m | 🟢 Safe | Maintain normal speed |
| 50–100 m | 🟡 Caution | Reduce speed and monitor |
| < 50 m | 🔴 Danger | Emergency course correction |

### ⚓ Dynamic Speed Control

The vessel speed is adjusted according to the detected obstacle distance:

- **Safe:** 12.0 knots
- **Caution:** 7.2 knots
- **Danger:** 3.5 knots

The updated speed is used to calculate the estimated time of arrival (ETA).

### 🌊 Underwater Obstacle Simulation
The system also simulates underwater obstacle information and depth values for demonstration purposes.

### 🗺️ Interactive Web Dashboard
The web interface provides:

- GPS coordinates
- Vessel heading
- Bearing
- Distance to destination
- Vessel speed
- SOG / STW
- Obstacle threat level
- Underwater depth
- AI navigation output
- Route waypoints
- Navigation grid
- Interactive map visualization

---

## 🏗️ System Architecture

```text
                    GPS Coordinates
                           │
                           ▼
                  ┌─────────────────┐
                  │  Flask Backend  │
                  └────────┬────────┘
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
        GPS Handler   Obstacle      Navigation
                      Detection        Engine
                                        │
                              ┌─────────┴─────────┐
                              ▼                   ▼
                       Haversine &          A* Pathfinding
                       Bearing              + SeaRoute
                              │                   │
                              └─────────┬─────────┘
                                        ▼
                              Navigation Decision
                                        │
                                        ▼
                              Interactive Web UI
