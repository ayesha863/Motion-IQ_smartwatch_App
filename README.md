# ⌚ MotionIQ – Data Fetcher Smartwatch

MotionIQ Smartwatch is a lightweight and efficient Android WearOS app for collecting **sensor data (accelerometer, gyroscope, magnetometer, heart rate, etc.)** directly from your smartwatch and transmitting it to a **RabbitMQ server** for real-time **human activity recognition (HAR)**.

---

## 🚀 Features

* ⌚ **Real-time smartwatch sensor data streaming**
* 🧠 **Integration with activity recognition pipelines**
* 🐇 **RabbitMQ-based message brokering**
* 💻 **Java-based backend consumer**

---

## 📦 How to Use

1. Set the **RabbitMQ server's IP address and port** in the app.
2. Select the **desired sensors** (accelerometer, gyroscope, magnetometer, heart rate, etc.) via the smartwatch UI.
3. Tap **Start** to begin transmission.
   ⚠️ **Important:** Ensure your smartwatch is paired with your smartphone (via **Bluetooth or WearOS app**) for network access.

---

## 🛠 Platform Setup Guide

### 1. RabbitMQ Installation

Download from [RabbitMQ Downloads](https://www.rabbitmq.com/download.html).

Enable management UI:

```bash
cd "C:\Program Files\RabbitMQ Server\rabbitmq_server-{version}\sbin"
rabbitmq-plugins enable rabbitmq_management
```

Access UI at: [http://localhost:15672](http://localhost:15672)

---

### 2. Create User

* **Username:** `test`
* **Password:** `test`
* **Tags:** administrator

> ⚠️ Note: Guest users can’t connect remotely.

---

### 3. Java Consumer Setup

Required files:

* `SensorDataConsumer.java`
* `amqp-client-5.21.0.jar`
* `slf4j-api-2.0.13.jar`
* `slf4j-simple-2.0.13.jar`

Run steps:

```bash
javac SensorDataConsumer.java
java SensorDataConsumer
```

---

### 4. Firewall

Ensure **ports 15672 and 5672** are open in Windows Firewall.

---

## 📱 Smartwatch App Setup

1. Install the **MotionIQ Smartwatch app** via **Android Studio (WearOS target) or APK sideloading**.
2. Pair your smartwatch with your smartphone via **Bluetooth / WearOS app**.
3. Set the following in the smartwatch app:

   * **RabbitMQ Server IP**
   * **Port:** `5672`
   * **Username:** `test`
4. Select which **sensors** you want to stream.
5. Check `sendDataService.java` for **credential configs**.

---

## ✅ Testing

1. Start **RabbitMQ** and the **Java consumer**.
2. Launch the **smartwatch app** and start data transmission.
3. Monitor **logs and RabbitMQ UI** (`Queues`, `Connections` tabs).

---

## 🤝 Contributing

Contributions are welcome! 🎉 Fork, submit PRs, or report issues to improve the system.

