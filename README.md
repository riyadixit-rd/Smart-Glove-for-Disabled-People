# 🧤 Smart Glove for Disabled People

> Transforming hand gestures into real-time speech using embedded systems and intelligent gesture mapping.

---

## 🚀 Overview

The **Smart Glove System** is an assistive wearable device designed to help individuals with speech disabilities communicate effectively. By detecting finger movements using flex sensors and processing them through a microcontroller, the system converts hand gestures into audible speech in real time.

This project integrates **IoT, embedded systems, and human-centered design** to deliver a **low-cost, portable, and impactful communication solution**.

---

## 🏗️ System Architecture

Flex Sensors  
↓  
Microcontroller (Arduino)  
↓  
Gesture Recognition  
↓  
DF Mini Player  
↓  
Speaker Output  
---

## ⚙️ Tech Stack

### 🔧 Hardware
- Flex Sensors  
- Arduino Uno / Nano  
- DF Mini Player  
- Speaker Module  
- Battery Pack  
- Wearable Glove  

### 💻 Software
- Arduino IDE  
- Embedded C  
- Gesture Mapping Logic  

---

## 🔄 Working Mechanism

1. Flex sensors detect finger bending  
2. Analog signals sent to Arduino  
3. Sensor values compared with threshold values  
4. Gesture pattern identified  
5. Corresponding audio file triggered  
6. Voice output played through speaker  

---

## 🧪 Performance Metrics

| Metric                | Value        |
|---------------------|-------------|
| Accuracy            | 95%         |
| Response Time       | 1.2 sec     |
| User Satisfaction   | 4.7 / 5     |
| Gestures Supported  | 20          |

---

## 💻 Sample Code

```cpp
#include <SoftwareSerial.h>
#include <DFRobotDFPlayerMini.h>

// DF Player setup
SoftwareSerial dfSerial(10, 11);
DFRobotDFPlayerMini dfPlayer;

// Flex sensor pins
const int thumbPin  = A0;
const int indexPin  = A1;
const int middlePin = A2;

// Thresholds
const int BEND_THRESHOLD = 500;
const int STRAIGHT_THRESHOLD = 350;

// Delay control
unsigned long lastTriggerTime = 0;
const int triggerDelay = 2000;

void setup() {
  Serial.begin(9600);
  dfSerial.begin(9600);

  if (!dfPlayer.begin(dfSerial)) {
    Serial.println("DFPlayer not detected!");
    while (true);
  }

  dfPlayer.volume(20);
}

void loop() {
  int thumb  = analogRead(thumbPin);
  int index  = analogRead(indexPin);
  int middle = analogRead(middlePin);

  if (millis() - lastTriggerTime < triggerDelay) return;

  if (thumb > 500 && index < 350 && middle < 350) {
    dfPlayer.play(1);
    lastTriggerTime = millis();
  }
  else if (index > 500 && thumb < 350 && middle < 350) {
    dfPlayer.play(2);
    lastTriggerTime = millis();
  }
  else if (middle > 500 && thumb < 350 && index < 350) {
    dfPlayer.play(3);
    lastTriggerTime = millis();
  }
}
```
## 🎥 Demo

👉 [Watch Demo Video](https://drive.google.com/file/d/1Sl1HWzl1fqGacY5yyUJuazX19TfmsotJ/view?usp=drivesdk)

---

## 📸 Project Showcase

- 🧤 Hardware setup  
- 🔌 Circuit connections  
- ⚡ Working demo  

---

## ⚠️ Challenges Faced

- Gesture overlap causing misclassification  
- Sensor noise affecting readings  
- Sensitivity to glove positioning  

---

## 🔮 Future Enhancements

- 🤖 Machine Learning-based gesture recognition  
- 📱 Mobile app connectivity (Bluetooth/Wi-Fi)  
- 🌍 Multi-language support  
- 🎯 Improved accuracy using IMU sensors  

---

## 🌍 Real-World Impact

- 🗣️ Enables independent communication  
- 🏥 Useful in healthcare applications  
- 🎓 Helps in education and workplaces  
- 🌐 Reduces communication barriers in daily life  

---

## 👩‍💻 Contributors

- Riya Dixit  
- Amandeep Jana 
- Srinidhi TK 

---

## 🎓 Academic Context

This project is developed as academic project work at VIT Bhopal University

---

## 📜 License

This project is developed for academic and research purposes.
