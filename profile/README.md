# Auto-Intern skAInet  
**Industrial Edge-Compute Platform – Bridging the Physical and Digital World**

skAInet is the professional, German-engineered edge computing ecosystem developed by **Auto-Intern GmbH**.  
It is specifically designed for continuous, high-precision monitoring of physical processes in harsh industrial environments and forms the foundational infrastructure for next-generation process automation, predictive maintenance, process insight, and true Industry 4.0 / Industrial IoT applications.

The platform turns machines into entities that can “see”, “feel”, and “understand” their own condition — in real time, directly at the point of measurement.

### Core Components

| Component              | Description                                                                                                      | Key Features                                                                 |
|------------------------|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| **skAInet Edge-Compute** | Rugged (IP67), compact edge node with integrated managed PoE+ switch and powerful single-board computer          | 48 V DC (M12), –25 °C to +70 °C, 7× PoE+ downstream, 1× Gigabit upstream, RPi CM4/CM5 or NVIDIA Jetson series |
| **Peripheral Access Daemon (PAD)** | Proprietary daemon running on every Edge-Compute node – auto-detects, configures and manages all connected peripherals | Zero-touch provisioning, hot-plug support, firmware management             |
| **Sensors & Actuators** | Fully PoE-powered (up to ~10 W) or externally powered for higher loads                                           | Plug-and-play, no auxiliary power supplies required for most devices       |
| **Data Backbone**      | Central Redis instance (in-memory + optional persistence)                                                       | Unified topic-based data access, microsecond-level timestamps              |

### Supported Sensor Types (November 2025)

| Sensor Type                  | Resolution / Range                              | Typical Use Case                                      |
|------------------------------|-------------------------------------------------|-------------------------------------------------------|
| Vibration (IEPE/ICP)         | 24 bit, up to 51.2 kHz sampling                 | Condition monitoring, bearing fault detection         |
| Temperature                  | 1–36 channels per module (PT100, PT1000, thermocouples) | Oven zones, motor windings, process temperature       |
| Impedance Spectroscopy (EIS) | Full-spectrum AC impedance, 10 µHz – 100 kHz   | Battery state-of-health, corrosion monitoring         |
| Infrared Camera              | 384×288 or 640×480 px, radiometric             | Hot-spot detection, thermal process control           |
| Machine Vision Camera        | Up to 4K, global shutter, GigE Vision compliant | Quality inspection, object detection, positioning     |
| Structure-borne Sound        | High-sensitivity microphones + accelerometers   | Anomaly detection, acoustic signature analysis        |
| Humidity & Air Quality       | Combined temperature/humidity, optional VOC    | Climate control, environmental monitoring             |
| Digital Inputs               | 24 V opto-isolated                              | Machine status, safety circuits                       |
| Analog Inputs                | 4–20 mA, 0–10 V, 24 bit                         | Pressure, flow, level transmitters                    |

Custom sensors and measurement principles are available on request via Auto-Intern.

### Getting Started – Measurement in Under 2 Minutes

1. Mount the Edge-Compute node and supply 48 V DC via M12 connector  
2. Plug sensors/actuators into any of the seven PoE downstream ports  
3. Open a WebSocket connection to `ws://<edge-ip>:8001` – live data starts flowing immediately  
4. Open the built-in web interface and documentation at `http://<edge-ip>` (port 80)

No internet connection required. Fully air-gapped operation supported.

### Frequently Asked Questions

| Question                                                    | Answer |
|-------------------------------------------------------------|--------|
| **Do I need internet access?**                              | No. skAInet is designed for 100 % offline / air-gapped operation – perfect for critical infrastructure and confidential manufacturing environments. |
| **How many sensors can one Edge-Compute handle?**           | Practically unlimited. Real-world deployments already exceed 250 concurrent channels. The limit is determined only by desired sampling rates and on-edge analytics workload. |
| **Where do measurement data appear?**                       | All raw and processed data are published in real time to the unified Redis topic **`measurement`** (JSON payloads with nanosecond-resolution timestamps). |
| **Is an SDK required?**                                     | No. Direct Redis and WebSocket access is intentionally simple and language-agnostic. Full working examples in Python and C++ are provided in this organization. |
| **Best-case end-to-end latency?**                           | < 3 ms from ADC (RPi Pico-based sensor) → TCP → PAD → Redis → WebSocket client in the same LAN (measured with 10 kHz vibration data). |
| **Where can I find CAD files, schematics, and datasheets?** | All mechanical, electrical and 3D data are publicly available in this GitHub organization under the `hardware/` directory of the respective repositories. |
| **How are software updates performed?**                     | Over-the-air (encrypted) via the upstream port or fully offline via USB image (details in the documentation repository). |

### Open-Source Resources in This Organization

All example code and utilities are released under the **Apache License 2.0** with clear attribution requirements (see individual `NOTICE` files).

- High-performance C++ mappers (redis++, Boost.Beast WebSocket server examples)  
- Python minimal mappers (CPK, FFT, anomaly detection, data export)  
- Ready-to-deploy dashboards (React + WebSocket)  
- Docker images, systemd units, Yocto layers, and deployment scripts  
- Hardware design files (STEP, schematics, bill of materials)

You are explicitly encouraged to use these examples as the foundation for proprietary, closed-source applications.

### Partners & Extensions

| Partner         | Expertise                                                                 |
|-----------------|---------------------------------------------------------------------------|
| **Auto-Intern** | Custom sensor development, special Edge-Compute variants, project integration |
| **nerd_force1** | On-premise storage (Ceph), Kubernetes orchestration, high-availability clusters |
| **NexuFed AI**  | On-device and federated AI models tailored for skAInet hardware           |

### Contact & Custom Development

Need a sensor that doesn’t exist yet? A Jetson Orin NX 64 GB version? A special form factor?  
→ **stephan.boekelmann@gruppe.ai**

We build exactly what your process requires.

**skAInet – Because machines should finally understand themselves.**

Engineered and manufactured in Germany  
© 2025 Auto-Intern GmbH – All rights reserved