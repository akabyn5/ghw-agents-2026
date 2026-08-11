# Project Description — Wokwi Space Telemetry Simulator

**Challenge:** Build a Project Using a New Tool
**Team:** Space Dogs
**Event:** Global Hack Week: Agents

Wokwi Space Telemetry Simulator is a small embedded-systems simulation built in **Wokwi**, an online circuit and microcontroller simulator our team had never used before. The project models a simplified satellite subsystem: an ESP32 microcontroller reads live temperature and humidity data from a simulated DHT22 sensor, formats it into a telemetry stream over Serial, and evaluates a mission status — `NOMINAL` or `WARNING` — based on whether the temperature exceeds a defined safety threshold.

The goal was to demonstrate a complete, working sensor-to-decision pipeline (sensor → microcontroller → telemetry → status evaluation) using a tool completely new to the team, while keeping the project directly relevant to ARPIP's interest in embedded and space systems. The simulation was verified in both states: normal operating conditions (`NOMINAL`) and a simulated thermal anomaly (`WARNING`), confirming that the logic correctly reacts to changing sensor data rather than displaying static text.

This lightweight project also lays conceptual groundwork for later challenges in the week, which extend the same sensor → telemetry → agent-analysis → mission-status flow into full AI agent pipelines.
