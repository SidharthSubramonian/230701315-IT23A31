🛡️ IoT-Based Smart Helmet

🚀 Overview

The **Smart Helmet** is an IoT-based safety system designed to enhance rider safety using real-time crash detection, helmet wear detection, and instant SOS alerting. Built using **Raspberry Pi 4**, this helmet integrates sensor data and cloud communication to provide proactive safety features for bikers.

---

📦 Features

* **Crash Detection**
  Detects falls or crashes using the **MPU6050** accelerometer and gyroscope module.

* **Helmet Wear Detection**
  Uses an **Ultrasonic Sensor** to detect whether the helmet is being worn.

* **Emergency SOS Alert**
  Sends an SOS alert with GPS location via a **Telegram Bot** if a crash is detected and the user remains inactive for more than 10 seconds.

* **Offline Voice Assistant Integration (Optional)**
  Can be extended to support voice commands via an offline assistant like **Jarvis**.

---

🧰 Hardware Requirements

* Raspberry Pi 4 (4GB recommended)
* MPU6050 (Accelerometer + Gyroscope)
* Ultrasonic Sensor (HC-SR04)
* GPS Module (e.g., NEO-6M) *(optional but recommended for location in SOS)*
* Buzzer or Vibration Motor (for alerts)
* Battery Pack / Power Source
* Helmet (for mounting components)
* Optional: Microphone, Speaker (for offline assistant)

---

🛠️ Software Requirements

* Raspbian / Kali Linux on Raspberry Pi
* Python 3.x
* Required Python Libraries:

  ```bash
  pip install RPi.GPIO smbus2 mpu6050-raspberrypi telepot
  ```

---

🔧 Setup Instructions

1. **Connect Sensors**

* MPU6050 to Raspberry Pi (I2C: SDA to GPIO2, SCL to GPIO3)
* Ultrasonic Sensor (Trigger to GPIO23, Echo to GPIO24)
* Buzzer/Vibration Motor to GPIO18 (or any GPIO with PWM)

2. **Telegram Bot Setup**

* Create a Telegram bot via [BotFather](https://core.telegram.org/bots#6-botfather)
* Get your `BOT_TOKEN`
* Use `telepot` to send messages in Python

3. **Run the Script**

```bash
python3 smart_helmet.py
```

---

⚙️ Working Logic

1. When the helmet is worn (ultrasonic sensor reads distance > 1000 cm), the system activates.
2. If a sudden impact or unusual orientation is detected (based on MPU6050 data), a 10-second countdown starts.
3. If no motion is detected in those 10 seconds, an SOS message is sent via Telegram, optionally with GPS coordinates.
4. Alerts may also be provided via buzzer or vibration.

---

📈 Future Enhancements

* GPS location tracking
* Cloud logging (Firebase, Supabase, etc.)
* Voice assistant for hands-free controls
* Fall pattern recognition using ML
* Integration with emergency services

---

📸 Sample Output

```text
[INFO] Helmet detected on head
[INFO] Monitoring crash detection...
[ALERT] Possible crash detected!
[WAIT] Checking for movement...
[ALERT] No motion detected. Sending SOS to Telegram...
[SUCCESS] SOS sent to @yourusername
```

---

📄 License

This project is open-source under the MIT License. Feel free to modify and use for educational or development purposes.

---

🙋‍♂️ Contributors

* Project Lead: Sidharth Subramonian
* Hardware Integration: Sivaramakrishnan R
* Telegram Bot: Sidharth Subramonian
* Documentation: Sivaramakrishnan R

---

