# Gesture Ink – Hand Gesture Writing & Drawing System

Gesture Ink is a real-time, no-touch writing and drawing system that lets users write or draw in mid-air using only natural hand gestures. The system combines computer vision, wearable sensing, and MQTT-based communication to create a seamless, hands-free interaction experience.

The project was built and demonstrated at **MakeUofT 2025**, Canada’s largest makeathon, where it received recognition for its innovation in gesture-based interfaces and IoT integration.

Gesture Ink is designed with both technical depth and human impact in mind. It explores how intuitive motion, tactile feedback, and real-time vision systems can replace traditional input devices in creative, assistive, and presentation-based environments.

---

## Demo

A full system demonstration, including live gesture drawing and glove-based color control, is available here:

**YouTube Demo:** [https://youtu.be/lAq6rWafrmU](https://youtu.be/lAq6rWafrmU)

### Live Gesture Drawing

![Gesture Drawing](https://github.com/user-attachments/assets/432637c5-4906-4aa1-b9c5-b3850cd591fe)

### Real-Time Color Control from Glove Sensors

![Color Change](https://github.com/user-attachments/assets/93cde095-60f9-4f15-bd4d-9df8ed427bb9)

### Team Presentation at MakeUofT 2025

![Team Presentation](https://github.com/user-attachments/assets/cd8db60f-47e6-4059-8a00-c65dbf8d277c)

---

## What Gesture Ink Does

Gesture Ink enables users to draw or write without touching a screen. A webcam tracks hand movements in real time, interprets gestures, and converts them into strokes on a digital canvas. A wearable glove communicates additional sensor data wirelessly, allowing dynamic color changes and tactile feedback.

The result is a natural interaction loop where the user sees, feels, and controls their drawing entirely through motion.

---

## Core Capabilities

### Gesture-Based Writing and Drawing

Hand gestures are mapped to drawing actions using real-time hand landmark detection.

Two fingers raised initiates drawing mode. A single finger continues the stroke, allowing precise control. A three-finger gesture triggers an undo operation, while a closed fist stops drawing entirely. These gestures were chosen to be intuitive and easy to remember during live use.

### Real-Time Color Control via Wearable Sensors

An Arduino-based glove streams RGB sensor values over MQTT. These values directly control the brush color on the drawing canvas, allowing users to change colors mid-stroke without interacting with any physical interface.

This enables expressive, uninterrupted drawing and was a key highlight during the live MakeUofT demo.

### Boundary Detection with Tactile Feedback

The system continuously monitors hand position relative to the drawing area. When the user moves out of bounds, a message is published over MQTT to trigger a buzzer on the glove. This provides immediate tactile feedback, helping users stay spatially aware without looking away from their work.

### Real-Time MQTT Communication

MQTT acts as the backbone of the system’s communication layer. The Python application subscribes to live glove sensor data while publishing control signals such as buzzer activation. This architecture keeps the vision system and wearable hardware loosely coupled, scalable, and responsive.

### Computer Vision and Hand Tracking

Gesture Ink uses OpenCV for video capture and image processing, combined with MediaPipe (via cvzone) for accurate hand landmark detection. This allows robust tracking of finger positions, gesture states, and movement trajectories in real time.

### Undo and Reset Interactions

Undo and canvas reset operations are handled entirely through gestures, maintaining the no-touch design philosophy. The system keeps a stroke history to support smooth and predictable undo behavior.

---

## Technical Architecture

The system is divided into three primary layers.

The vision layer handles webcam input, hand detection, gesture classification, and stroke rendering. This layer is implemented in Python using OpenCV, cvzone, MediaPipe, and NumPy.

The communication layer uses MQTT to exchange data between the vision system and the wearable glove. Sensor values, control signals, and feedback events are transmitted with low latency.

The hardware layer consists of an ESP32 or ESP8266-based glove equipped with flex sensors, RGB controls, and a buzzer. Firmware is written in C++ using the Arduino framework.

---

## Technology Stack

### Software

Python 3.12 or higher is used for the main application logic. OpenCV handles video input and drawing operations. cvzone and MediaPipe provide reliable hand tracking and landmark detection. NumPy supports efficient image and data manipulation. MQTT communication is implemented using the paho-mqtt library.

### Hardware

The wearable glove is built using an ESP32 or ESP8266 microcontroller. Flex sensors detect finger movement, while RGB inputs control brush color. A buzzer provides tactile feedback for boundary alerts and system events. A standard webcam is used for hand tracking.

### Languages and Protocols

Python is used for the vision and application layer. C++ is used for the Arduino firmware. MQTT enables real-time, wireless communication between components.

---

## Hardware Setup Overview

Upload the glove firmware to the ESP32 using the Arduino IDE. Connect the flex sensors, RGB inputs, and buzzer according to the firmware configuration. Set up an MQTT broker such as Mosquitto and configure the broker address in both the firmware and Python application.

Once connected, start the Python script and ensure the webcam feed and MQTT messages are active.

---

## Installation

Install the required Python dependencies using pip:

```
pip install opencv-python numpy cvzone paho-mqtt
```

Ensure your MQTT broker is running before launching the application.

---

## Future Directions

Gesture Ink is designed as a foundation rather than a finished product.

Future work includes integrating handwriting recognition to convert air-written strokes into editable text, potentially using machine learning models or external APIs. Pressure-sensitive or speed-based brush dynamics could enable more expressive drawing styles. VR and AR integration could transform Gesture Ink into a 3D whiteboard or immersive collaboration tool. Cloud synchronization would allow drawings and notes to persist across devices and sessions.

---

## Final Thoughts

Gesture Ink explores a future where interaction is defined by movement rather than hardware. By combining computer vision, wearable sensing, and real-time communication, the project demonstrates how natural gestures can become a powerful input modality.

Built at **MakeUofT 2025**, Gesture Ink reflects both technical rigor and a human-centered design mindset. It is a step toward more accessible, expressive, and intuitive ways of interacting with digital systems.
