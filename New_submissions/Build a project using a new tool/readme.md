# Challenge: Build a Project Using a New Tool – Wokwi Space Telemetry Simulator ✅

## 🎉 Team Challenge Summary

**Challenge Completed:** Build a Project Using a New Tool ✅  
**Team:** Space Dogs  
**Event:** Global Hack Week: Agents (Agent Week)

We built a small embedded-systems simulation in Wokwi — a tool none of us on the team had ever used for a real project before. The project simulates a satellite subsystem that reads temperature and humidity from a sensor, streams real-time telemetry over Serial, and decides on a mission status (NOMINAL / WARNING) based on those readings. It was a natural fit with ARPIP’s interest in embedded and space systems.

## 📋 Challenge Overview

- **Challenge Name:** Build a Project Using a New Tool  
- **Event:** Global Hack Week: Agents | MLH  
- **Tool Used:** Wokwi (online embedded systems simulator)  
- **Difficulty:** Easy  
- **Status:** Successfully Completed ✅  
- **Date Completed:** August 10, 2026  
- **Project Link:** [add your Wokwi SHARE link here]

### Why This Matters

Wokwi lets you simulate microcontrollers and electronic components right in the browser — no physical hardware needed. For Space Dogs / ARPIP this is genuinely useful: it’s a quick way to prototype the embedded logic for future satellite, ground-station, or mission-telemetry ideas before we ever touch real boards.

## 🛠️ What We Built

**Project name:** Wokwi Space Telemetry Simulator  

**Concept:** A simulated satellite subsystem that reads environmental data from a sensor, packages it into telemetry, and reports a mission status derived from that data — basically the same flow a real spacecraft’s onboard computer would follow.

### Workflow

```
DHT22 Sensor (Temperature + Humidity)
        ↓
     ESP32 (microcontroller)
        ↓
   Telemetry (Serial output)
        ↓
 Mission Status Evaluation
   (NOMINAL / WARNING)
```

### Hardware (Simulated)

| Component       | Role                          |
|-----------------|-------------------------------|
| ESP32 DevKit-C  | Onboard “mission computer”    |
| DHT22           | Temperature & humidity sensor |

### Wiring

| DHT22 Pin | ESP32 Pin |
|-----------|-----------|
| VCC       | 3V3       |
| GND       | GND       |
| DATA      | GPIO 4    |

### Code (sketch.ino)

```cpp
#include <DHT.h>

#define DHTPIN 4
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
  Serial.println("================================");
  Serial.println(" WOKWI SPACE TELEMETRY SYSTEM");
  Serial.println("================================");
  Serial.println("System initialized");
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  if (isnan(temperature) || isnan(humidity)) {
    Serial.println("Sensor read failed");
    delay(2000);
    return;
  }

  String status = "NOMINAL";
  if (temperature > 60.0) {
    status = "WARNING";
  }

  Serial.println("--------------------------------");
  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.println(" C");
  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.println(" %");
  Serial.print("Mission Status: ");
  Serial.println(status);

  delay(2000);
}
```

## 📸 Proof of Completion

Four screenshots document the working simulation:

1. **Circuit** – ESP32 + DHT22 wired together in the Wokwi simulator.  
2. **Code** – The sketch.ino logic that reads the sensor and builds the telemetry output.  
3. **Status: NOMINAL** – Simulation running with temperature within the normal range.  
4. **Status: WARNING** – Simulation running with temperature above the 60 °C threshold, showing the system correctly detecting the anomaly.

```
Temperature: 24.00 C
Humidity: 40.00 %
Mission Status: NOMINAL
```

```
Temperature: 76.60 C
Humidity: 40.00 %
Mission Status: WARNING
```

✅ ESP32 + DHT22 circuit built and wired correctly  
✅ Custom telemetry program written and running  
✅ NOMINAL state verified  
✅ WARNING state verified (anomaly correctly detected)

## 🔗 Connection to the Broader Plan

This project ticks the “Build a Project Using a New Tool” challenge from our GHW: Agents action plan. It also shows the first stage of a bigger flow the team is exploring this week — simulated sensor → microcontroller → telemetry packet → agent analysis → mission status — which can later feed into ARPIP’s agent-based mission-analysis tools.

## 💡 Key Takeaways

- Wokwi is a fast way to validate embedded logic without physical hardware.  
- Keeping sensor state (diagram.json) separate from application logic (sketch.ino) makes it easy to reconfigure the simulation for different test scenarios.  
- Simple threshold-based status logic (NOMINAL / WARNING) is an effective way to demonstrate a telemetry-analysis pattern that will be useful for future ARPIP mission-operations tools.

**Completed by:** Space Dogs Team  
**Date:** August 10, 2026  

Sensor connected. Telemetry flowing. Mission status confirmed. 🛰️
