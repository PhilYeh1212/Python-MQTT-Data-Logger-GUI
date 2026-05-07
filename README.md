# 📡 MQTT Logger Pro — Python MQTT Subscriber + Publisher with Auto-JSON Decoding

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![paho-mqtt](https://img.shields.io/badge/paho--mqtt-1.6%20%7C%202.0+-purple.svg)](https://github.com/eclipse/paho.mqtt.python)
[![Protocol](https://img.shields.io/badge/Protocol-MQTT%205.0-9266ff.svg)](https://mqtt.org/)
[![License](https://img.shields.io/badge/License-MIT--like-lightgrey.svg)](#-license)

> **Subscribe, publish, and auto-flatten JSON payloads to CSV** — for
> any MQTT broker. Mosquitto, HiveMQ, EMQX, AWS IoT, Azure IoT Hub. TLS
> support, multi-topic subscribe with wildcards, built-in test publisher.
> One clean Python GUI.

MQTT Logger Pro screenshot
<img width="1280" height="720" alt="mqtt_cover" src="https://github.com/user-attachments/assets/6ce5e08f-0b6d-4622-97a9-a82ce9366e94" />


# MQTT Logger Pro

> A Python MQTT client with subscribe, publish, JSON auto-flatten, TLS, and CSV export — built for IIoT engineers who need to debug MQTT brokers without spinning up a Node-RED instance.

**This is a commercial tool, sold on Gumroad.** Source code is included in your purchase.

---

## What it does

- **Subscribe + Publish** in the same GUI — no need to switch tools
- **Wildcard support** — `sensors/+/temperature`, `factory/#`, all standard MQTT patterns
- **JSON auto-flatten** — nested payloads displayed as flat key/value rows
- **TLS / mTLS** — connect to AWS IoT, Azure IoT Hub, HiveMQ Cloud
- **Username + password authentication**
- **QoS 0 / 1 / 2** with retained-message handling
- **CSV export** — pair with [CSV Dashboard](https://philyeh.gumroad.com/l/python-csv-dashboard) for free interactive plotting
- **Single-file Python** built on paho-mqtt v2

## Why this exists

MQTT debugging tools are either $0 (MQTT Explorer — fine, but no CSV / no scripting) or $500+ (HiveMQ MQTT CLI Pro tools). There's a gap in the middle for engineers who want a polished GUI that's also scriptable Python.

This is what I built for myself. It's the same tool I use at work to debug factory MQTT brokers.

## Tested with

| Broker | Notes |
|---|---|
| Eclipse Mosquitto | Local + cloud |
| HiveMQ Cloud | TLS + auth |
| AWS IoT Core | mTLS with X.509 certs |
| Azure IoT Hub | SAS tokens |
| EMQX | Both v4 and v5 |
| Home Assistant Mosquitto | Local discovery topics |

## Get it

→ **[MQTT Logger Pro on Gumroad — $39](https://philyeh.gumroad.com/l/mqtt-data-logger-pro)**

Or grab the **[Industrial Integration Bundle](https://philyeh.gumroad.com/l/industrial-integration-bundle)** ($119) — MQTT + Modbus + OPC UA Bridge together, saves $48.

## What's in the purchase

- `mqtt_logger.py` — Single-file Python application
- `requirements.txt` — Pinned dependencies
- `README.md` — Setup guide for each major broker
- Commercial use license per Gumroad EULA

## License

Commercial use license per Gumroad EULA. You may use this software at the company that purchased it for any commercial purpose. Redistribution, resale, or open-sourcing the code is not permitted.

## Support

- Reply to your Gumroad purchase email
- Bug reports / feature requests via [GitHub Issues](https://github.com/PhilYeh1212/Python-MQTT-Data-Logger-GUI/issues)

---

I write about industrial Python and protocol internals at **[dev.to/philyeh](https://dev.to/philyeh)**, and post Chinese versions on [iThelp](https://ithelp.ithome.com.tw/users/20171204).

— Phil Yeh · Senior Automation Engineer · Industrial Python · Developer Tools

