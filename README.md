# 🚀 [IoT Subsystem] Hệ Kiểm Soát Ra Vào Ký Túc Xá Thông Minh

## 📌 Giới thiệu

Đây là Repository chuyên biệt dành cho khối **IoT Subsystem** của đồ án:

> **Hệ thống kiểm soát ra vào Ký túc xá thông minh (Smart Dormitory Access Control System)**

Repository này được tách riêng khỏi hệ thống Backend nhằm phục vụ việc phát triển độc lập các thành phần:

* Firmware ESP32
* Thiết kế phần cứng
* Kết nối cảm biến
* Điều khiển khóa điện tử
* Giao tiếp MQTT
* Cơ chế Offline Cache
* Device Monitoring

---

# 🎯 Mục tiêu của Repository

Repository này đóng vai trò là khu vực nghiên cứu, phát triển và kiểm thử độc lập cho toàn bộ hệ thống IoT tại các cửa ra vào của Ký túc xá.

Các chức năng chính:

* Xử lý xác thực người dùng tại cửa
* Điều khiển Relay mở khóa
* Giao tiếp MQTT với Backend
* Lưu cache cục bộ khi mất kết nối mạng
* Gửi trạng thái thiết bị định kỳ
* Ghi nhận sự kiện ra vào

---

# 🧩 Các thiết bị phần cứng sẽ phát triển

## 🖥️ Vi điều khiển chính

* ESP32

ESP32 đóng vai trò:

* Thu thập dữ liệu cảm biến
* Giao tiếp MQTT Broker
* Điều khiển Relay
* Lưu Offline Cache
* Gửi Heartbeat

---

## 🚪 Cổng KTX

### RFID Authentication

Thiết bị:

* RFID Reader MFRC522
* RFID Card / RFID Tag

Chức năng:

* Nhận diện sinh viên bằng thẻ từ
* Gửi UID thẻ lên hệ thống xử lý

---

## 🏢 Cửa chính KTX

### Face Recognition

Thiết bị:

* Camera
* Face Recognition Service

Chức năng:

* Nhận diện khuôn mặt sinh viên
* Gửi kết quả xác thực về hệ thống

---

## 🛏️ Cửa phòng

### Fingerprint Authentication

Thiết bị:

* Fingerprint Sensor

Chức năng:

* Xác thực dấu vân tay
* Kiểm soát quyền truy cập phòng

---

## 🔒 Cơ cấu chấp hành

### Relay Module

Thiết bị:

* Relay Module
* Khóa chốt điện từ

Chức năng:

* Điều khiển đóng/mở khóa
* Nhận lệnh từ ESP32

---

# ⭐ Tính năng nâng cao

## 📴 Offline Cache

Trong trường hợp mất kết nối mạng hoặc MQTT Broker không khả dụng:

ESP32 sẽ:

* Lưu danh sách RFID hợp lệ trong bộ nhớ
* Thực hiện xác thực cục bộ
* Cho phép mở cửa trong chế độ Offline
* Lưu lại Access Log tạm thời

Khi kết nối được khôi phục:

* Đồng bộ toàn bộ Log về Backend
* Cập nhật lại danh sách RFID hợp lệ

---

## 📡 Device Monitoring

ESP32 sẽ gửi tín hiệu Heartbeat định kỳ tới MQTT Broker.

Ví dụ:

```json
{
  "deviceId": "ESP32_GATE_01",
  "status": "ONLINE",
  "timestamp": "2026-01-01T10:00:00"
}
```

Mục tiêu:

* Theo dõi Online / Offline
* Phát hiện thiết bị lỗi
* Hiển thị trạng thái trên Dashboard

---

# 🔄 Luồng tín hiệu IoT

## 📤 Chiều gửi dữ liệu

```text
RFID / Face / Fingerprint
            ↓
          ESP32
            ↓
      MQTT Broker
            ↓
 Backend (Spring Boot)
```

---

## 📥 Chiều nhận lệnh

```text
Admin Web / Mobile App
            ↓
      Spring Boot
            ↓
      MQTT Broker
            ↓
          ESP32
            ↓
        Relay
            ↓
     Electronic Lock
```

---

# 📂 Cấu trúc thư mục đề xuất

```text
ktx-smart-access-iot
│
├── firmware_esp32/
│   ├── rfid/
│   ├── fingerprint/
│   ├── relay/
│   ├── mqtt/
│   └── offline_cache/
│
├── hardware_design/
│   ├── wiring_diagram/
│   ├── schematic/
│   └── pin_mapping/
│
├── docs/
│   ├── setup_guide/
│   ├── flashing_firmware/
│   └── libraries/
│
└── README.md
```

---

# 🛠️ Công nghệ sử dụng

* ESP32
* MQTT
* MFRC522 RFID
* Fingerprint Sensor
* Relay Module
* Electronic Lock
* WiFi
* Arduino Framework / ESP-IDF
* Spring Boot Integration

---

# 🚀 Roadmap

## Phase 1

* RFID Authentication
* MQTT Communication
* Relay Control

## Phase 2

* Fingerprint Authentication
* Access Logging

## Phase 3

* Face Recognition Integration

## Phase 4

* Offline Cache

## Phase 5

* Device Monitoring
* Heartbeat System

---

# 🎓 Đồ án tốt nghiệp

Smart Dormitory Access Control System

Repository này chỉ quản lý phần IoT Subsystem.

Backend, Mobile App, Web Admin và Database sẽ được quản lý tại Repository riêng.
