# AeroGuard Orbit — AI-Powered Satellite Collision Avoidance Dashboard

**Smart India Hackathon 2024 — Prototype Dashboard**

---

## What Is This?

AeroGuard Orbit is an interactive mission-control dashboard prototype demonstrating an
AI-assisted satellite collision avoidance system built on a low-cost 3U CubeSat platform.

> **IMPORTANT:** This is a proof-of-concept prototype using simulated orbital data.
> It is NOT flight-certified and does NOT represent an operational spacecraft control system.

---

## How to Run

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox)
2. No server, no install, no internet required — fully self-contained
3. The boot sequence runs automatically (~3 seconds)

---

## Core Design Principle

```
SENSE → PROCESS → PREDICT → PLAN → VALIDATE → ACT → TELEMETRY

AI PROPOSES · PHYSICS VERIFIES · SAFETY DECIDES
```

---

## Dashboard Pages

| Page | Description |
|------|-------------|
| **Dashboard** | Main mission control — orbital map, risk, safety validation, operator control |
| **Orbital Map** | Full-screen animated orbital visualization with beam lines |
| **Risk Analysis** | 48h risk projection, decision pipeline, conjunction analysis |
| **Maneuver Planner** | ΔV optimizer, burn profile, simulation controls |
| **What-If Sim** | LeoLabs-style maneuver simulator with sliders |
| **Sensors** | 8 live hardware sensor cards (ESP32, GPS, IMU, Camera, etc.) |
| **Telemetry** | 6 live telemetry panels + velocity stream chart |
| **Event Log** | Scrolling mission event timeline |
| **Decision Advantage** | Honest capability comparison vs. current operational approach |

---

## Simulation Modes

Use the **SIM** dropdown in the top-right to switch between:

| Mode | Description |
|------|-------------|
| 🟢 NORMAL | Low risk (3.7%) — no maneuver required |
| 🟡 WARNING | Elevated risk (34.2%) — monitoring recommended |
| 🔴 CRITICAL | High risk (78.4%) — conjunction alert, human approval required |

Switching modes updates: orbital map, risk graph, AI recommendation, safety checks,
conjunction alert, ComLink feed, subsystem status, event log — everything.

---

## Hardware Prototype (Simulated)

| Component | Role |
|-----------|------|
| ESP32 | Edge AI processing — runs LSTM/GRU model |
| NEO-6M GPS | Position + time reference |
| MPU6050 IMU | Orientation + acceleration |
| OV2640 Camera | Visual input / star tracker |
| MicroSD | Data logging at 10 Hz |
| OLED Display | Local status output |
| Servo Motor | Maneuver simulation actuator |

Estimated hardware cost: ~₹6,500 (~$80 USD)

---

## AI Architecture

- **Model:** LSTM / Gated GRU v5.1
- **Input:** Orbital TLE data + GPS + IMU + Camera feed
- **Output:** Collision probability (Pc), Anomaly score, 24h prediction
- **Edge deployment:** ESP32 microcontroller
- **Inference time:** ~47 ms per cycle

---

## Safety Architecture

AeroGuard does NOT allow AI to autonomously execute maneuvers.
Every maneuver goes through:

1. **AI proposes** — GRU model generates ΔV recommendation
2. **Physics verifies** — 6 rule-based checks (keep-out zone, fuel, trajectory, etc.)
3. **Human decides** — operator must APPROVE or REJECT before any action

---

## Files

```
aerogaurd/
├── index.html          ← Complete dashboard (single file, ~128 KB)
└── README.md           ← This file
```

---

## Development Roadmap

- [x] COTS Hardware Prototype
- [x] Simulated Orbital Dataset
- [x] LSTM/GRU Concept Model
- [ ] Higher-Fidelity Orbital Simulation
- [ ] Train on Real TLE Data
- [ ] Lab Validation
- [ ] Flight Qualification

---

## Disclaimer

All orbital data, satellite positions, collision probabilities, and sensor readings
displayed in this dashboard are **simulated** for demonstration purposes.
This prototype is not affiliated with ESA, NASA, or any space agency.
