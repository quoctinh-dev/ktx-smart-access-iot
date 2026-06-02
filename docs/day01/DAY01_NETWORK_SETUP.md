# DAY 01 – Thiết kế và cấu hình mạng cơ bản trên Cisco Packet Tracer

## Mục tiêu

Xây dựng mô hình mạng cơ bản phục vụ hệ thống kiểm soát ra vào Ký túc xá thông minh.

---

## Topology

Thiết bị sử dụng:

* Router 2911 (R1_KTX)
* Switch 2960 (SW1_KTX)
* Server (KTX_SERVER)
* Admin PC (ADMIN_PC)
* Home Gateway
* Student Laptop

---

## Kết nối

Router → Switch

Switch → Server

Switch → Admin PC

Switch → Home Gateway

Laptop → WiFi → Home Gateway

---

## Cấu hình IP

| Thiết bị     | IP           |
| ------------ | ------------ |
| Router       | 192.168.1.1  |
| Server       | 192.168.1.10 |
| Admin PC     | 192.168.1.20 |
| Home Gateway | 192.168.1.30 |
| Laptop       | DHCP         |

---

## Kiến thức học được

* Router thực hiện định tuyến trong mạng.
* Switch kết nối các thiết bị trong LAN.
* Home Gateway cung cấp WiFi và NAT.
* DHCP cấp phát địa chỉ IP tự động.
* Ping được sử dụng để kiểm tra kết nối.

---

## Kết quả

* Laptop ping được Router.
* Laptop ping được Server.
* Admin PC ping được Server.
* Mô hình hoạt động ổn định.

---

## Hướng phát triển

DAY 02:

* VLAN
* Phân tách mạng Admin
* Phân tách mạng Student
* Phân tách mạng IoT
