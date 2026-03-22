# Thermistor Beta Calculator for Klipper

A simple offline tool to calculate a corrected **beta value** for your thermistor — for more accurate temperature readings in Klipper.

**[Try it online](https://xyz-sign.github.io/thermistor-beta-calculator/)** <!-- replace with your GitHub Pages link -->

---

## The problem

Thermistors use a beta value to convert resistance → temperature. The issue is that beta isn't constant — it changes with temperature, and cheap sensors often have manufacturing tolerances of ±5%. This means your printer can be reading 220°C when the actual temperature is 215°C or 225°C.

## How it works

You measure the actual hotend temperature at 3 points using an external thermometer (thermocouple probe, IR thermometer, or thermal camera). The tool fits a quadratic curve through those 3 points and interpolates the correct beta for your target print temperature.

## Usage

1. Heat your hotend to 3 temperatures in your working range (e.g. 190°C, 220°C, 250°C)
2. Wait ~2–3 min for it to stabilize, then read your external thermometer
3. Enter the actual measured temps + corresponding beta reference values
4. Enter your target print temperature → click Calculate

For better accuracy: measure the actual resistance of your thermistor with a multimeter at room temperature and note the ambient temp at the time of measurement.

## Applying to printer.cfg

```ini
[thermistor MyThermistor]
temperature1: 24       # ambient temp (°C) when resistance was measured
resistance1: 98450     # actual measured resistance (Ω) at temperature1
beta: 4128             # your calculated value from the tool

[extruder]
sensor_type: MyThermistor
```

## Features

- Single HTML file — download and open in any browser
- Runs 100% offline, no install needed
- No frameworks, no dependencies, no tracking
- Built-in step-by-step guide

## License

MIT
