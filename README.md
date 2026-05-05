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


---

## 🎯 Why this exists

Existing MQTT GUIs (MQTT.fx, MQTT Explorer) are great for browsing topics
but **don't log data the way engineers actually need it**. Specifically:

- They don't **auto-flatten JSON** (`{sensor: {temp: 25}}` should become a
  CSV column `sensor.temp`)
- They don't **subscribe to multiple wildcards simultaneously**
- They don't include a **publisher** for testing — you need a separate tool
- Their CSV exports are useless for downstream pandas analysis

This project fixes all four. Built for IoT engineers who actually need to
process the data, not just look at it.

---

## 📂 Open Source vs Pro

This repo contains the **Community Edition** — a basic MQTT logger that
saves messages to CSV.

The **[MQTT Logger Pro](https://pokhts.gumroad.com)** version on Gumroad
adds the production features I built for real IoT projects:

| Feature | Community (this repo) | **[Pro Edition ($39)](https://pokhts.gumroad.com)** |
|---|:---:|:---:|
| Subscribe to a single topic | ✅ | ✅ |
| **Multi-topic subscribe** with wildcards (`+`, `#`) | ❌ | ✅ |
| Save messages to CSV | ✅ Raw | ✅ Auto-flattened |
| **Auto-flatten JSON** to dotted-key columns (`sensor.temp`) | ❌ | ✅ |
| **Built-in publisher** (test without a separate tool) | ❌ | ✅ QoS 0/1/2 |
| **TLS support** (strict + insecure modes) | ⚠️ Basic | ✅ Full |
| **paho-mqtt v1 + v2 compatibility** | ⚠️ One version | ✅ Both |
| **Demo Mode** (simulated factory broker, no setup) | ❌ | ✅ |
| **Last Will & Testament** support | ❌ | ✅ |
| **Dark industrial UI theme** | ❌ | ✅ |
| **Commercial license** | ❌ | ✅ |
| **Email support** | ❌ | ✅ |

### 👉 [Get MQTT Logger Pro on Gumroad — $39](https://pokhts.gumroad.com)

Or save $47 with the **[Industrial Python Toolkit Bundle](https://pokhts.gumroad.com)**
($129) — includes MQTT + Modbus + J1939 + EtherNet/IP.

---

## 🚀 Quick Start (Community Edition)

```bash
# Clone
git clone https://github.com/PhilYeh1212/Python-MQTT-Data-Logger-GUI
cd Python-MQTT-Data-Logger-GUI

# Install
pip install paho-mqtt

# Run
python main.py
```

Default settings connect to the public **HiveMQ broker**
(`broker.hivemq.com:1883`) on topic `test/#` so you can verify it works
without setting up your own broker.

---

## 🔧 Broker Compatibility

Tested with:

- **Mosquitto** (self-hosted)
- **HiveMQ** (Cloud + on-prem)
- **EMQX** (Cloud + on-prem)
- **AWS IoT Core** (with TLS + certificate auth)
- **Azure IoT Hub** (with SAS token)
- **Home Assistant** built-in broker
- **ThingsBoard** open-source IoT platform

If it speaks MQTT 3.1.1 or MQTT 5.0, this tool talks to it.

---

## 📖 Why JSON auto-flatten matters

A typical IoT payload looks like:

```json
{"deviceId":"sensor-42","ts":1735689600,"data":{"temp":25.3,"humid":62}}
```

Most MQTT loggers save this as a single CSV column:

```
timestamp,topic,payload
2026-01-05 14:00:00,sensors/temp,"{""deviceId"":""sensor-42"",""ts"":1735689600,""data"":{""temp"":25.3,""humid"":62}}"
```

Useless for analysis. The Pro version flattens it:

```
timestamp,topic,deviceId,ts,data.temp,data.humid
2026-01-05 14:00:00,sensors/temp,sensor-42,1735689600,25.3,62
```

Now `pandas.read_csv()` gives you proper columns and `df.plot()` works.

---

## 📚 Related reading

- More tutorials at [dev.to/philyeh](https://dev.to/philyeh)

---

## 📥 Get the Pro version

The Community Edition is great for learning the MQTT basics. The
**[Pro version](https://pokhts.gumroad.com)** is what I use in actual
IoT projects — production-quality, all features, commercial license.

| Product | Price | Link |
|---|---:|---|
| 📡 **MQTT Logger Pro** (this tool, Pro edition) | $39 | [Buy](https://pokhts.gumroad.com) |
| 🚛 **J1939 Sniffer Pro** | $59 | [Buy](https://pokhts.gumroad.com) |
| ⚙️ **Modbus Logger Pro** | $49 | [Buy](https://pokhts.gumroad.com) |
| 🏭 **EtherNet/IP Study Kit** | $29 | [Buy](https://pokhts.gumroad.com) |
| 🔒 **Private ChatGPT Stack** | $59 | [Buy](https://pokhts.gumroad.com) |
| 📦 **Industrial Python Toolkit Bundle** (4 tools, save $47) | **$129** | [Buy](https://pokhts.gumroad.com) |
| 📊 **CSV Dashboard** (free companion to visualize your logs) | $0 | [Download](https://pokhts.gumroad.com) |

---

## 📫 About

**Phil Yeh** — Senior Automation Engineer based in Taiwan. I build Python
tools for industrial protocol work.

- 🛒 **Store:** [pokhts.gumroad.com](https://pokhts.gumroad.com)
- ✍️ **Blog:** [dev.to/philyeh](https://dev.to/philyeh)

---

## 📝 License

The Community Edition in this repository is free for personal and
educational use. For commercial use (client projects, internal company
tools, products you sell), please get the **[Pro Edition](https://pokhts.gumroad.com)**
which includes a proper commercial license.

If this tool helped you, **a ⭐ on the repo** means a lot to an indie
developer. Thanks!

---

<sub>**Keywords:** Python, MQTT, MQTT 5, paho-mqtt, IoT, IIoT, broker,
subscribe, publish, GUI, Tkinter, JSON flatten, CSV export, Mosquitto,
HiveMQ, EMQX, AWS IoT, Azure IoT Hub, Home Assistant</sub>
