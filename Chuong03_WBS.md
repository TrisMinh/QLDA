# CHƯƠNG 3: LIỆT KÊ CÔNG VIỆC DỰ ÁN (WBS)

---

## 3.1 Tổng quan về WBS

WBS (Work Breakdown Structure — Cấu trúc phân rã công việc) là công cụ phân rã phạm vi dự án thành các công việc nhỏ hơn có thể quản lý được, có dạng cây phân cấp từ tổng thể đến chi tiết. WBS được xây dựng bằng cách kết hợp hai thành phần:
- **PBS (Product Breakdown Structure):** Phân rã sản phẩm.
- **TBS (Task Breakdown Structure):** Phân rã công việc.

**WBS = PBS × TBS** — Kết hợp danh sách sản phẩm và công việc thành WBS hoàn chỉnh.

Các nguyên tắc cốt lõi: Quy tắc 100% (tổng công việc con phải bao phủ đầy đủ công việc cha), Mutually Exclusive (không chồng chéo), Quy tắc 8/80 (mỗi work package tốn 8–80 giờ), và mỗi phần tử được đánh mã duy nhất.

---

## 3.2 Danh sách sản phẩm (PBS — Product Breakdown Structure)

### 3.2.1 Sản phẩm tổng: Hệ thống nhà kính thông minh

Sản phẩm tổng của dự án là **"Hệ thống Nhà kính Thông minh (Smart Greenhouse)"** — bao gồm phần cứng, phần mềm nhúng, backend + AI, web dashboard và kiểm thử.

### 3.2.2 Sản phẩm con cấp 1

| Mã | Sản phẩm cấp 1            | Mô tả                                                         |
| :-: | ---------------------------- | --------------------------------------------------------------- |
| P1 | Phần cứng (Hardware)       | Mạch điện, cảm biến, relay, actuator, mô hình nhà kính, Solar Tracking |
| P2 | Phần mềm nhúng (Firmware) | Chương trình trên ESP32                                     |
| P3 | Backend + AI                 | Server Django, mô hình ARX, Kalman, MPC                       |
| P4 | Web Dashboard                | Giao diện ReactJS giám sát và điều khiển                 |
| P5 | Kiểm thử                   | Kiểm thử hệ thống, hiệu chỉnh, hoàn thành dự án             |

### 3.2.3 Sản phẩm con cấp 2

| Mã | Sản phẩm cấp 2                                          | Thuộc cấp 1 |
| :--: | ---------------------------------------------------------- | :-----------: |
| P1.1 | Module cảm biến (DHT22, Soil, LDR)                       |      P1      |
| P1.2 | Module relay + actuator (bơm, quạt, phun sương, đèn) |      P1      |
| P1.3 | Mô hình nhà kính (khung, bố trí)                     |      P1      |
| P1.4 | Module Solar Tracking (tấm pin, servo, LDR)              |      P1      |
| P2.1 | Module đọc cảm biến                                    |      P2      |
| P2.2 | Module WebSocket Client                                    |      P2      |
| P2.3 | Module điều khiển relay                                 |      P2      |
| P3.1 | Django Server + API + Database                             |      P3      |
| P3.2 | Django Channels (WebSocket Server)                         |      P3      |
| P3.3 | Mô hình ARX                                              |      P3      |
| P3.4 | Kalman Filter                                              |      P3      |
| P3.5 | MPC Controller                                             |      P3      |
| P4.1 | Giao diện giám sát (Dashboard, biểu đồ, cảnh báo)    |      P4      |
| P4.2 | Giao diện điều khiển (bật/tắt thiết bị, dự báo)    |      P4      |
| P5.1 | Kiểm thử hệ thống                                      |      P5      |
| P5.2 | Hiệu chỉnh                                              |      P5      |
| P5.3 | Hoàn thành dự án                                         |      P5      |

---

## 3.3 Danh sách công việc (TBS — Task Breakdown Structure)

### 3.3.1 Các công việc tổng

| Mã | Công việc tổng        | Mô tả                                                              |
| :-: | ------------------------ | -------------------------------------------------------------------- |
| T1 | Phân tích yêu cầu    | Khảo sát, xác định yêu cầu chức năng và phi chức năng    |
| T2 | Thiết kế               | Thiết kế kiến trúc, sơ đồ mạch, thiết kế DB, thiết kế UI |
| T3 | Phát triển             | Lập trình firmware, backend, web, AI                               |
| T4 | Kiểm thử               | Kiểm thử đơn vị, tích hợp, hệ thống                         |
| T5 | Hoàn thành              | Hiệu chỉnh, báo cáo, bảo vệ đồ án                          |

### 3.3.2 Các công việc con chi tiết

**T1 — Phân tích yêu cầu:**

- T1.1: Khảo sát các giải pháp nhà kính thông minh hiện có
- T1.2: Xác định yêu cầu chức năng
- T1.3: Xác định yêu cầu phi chức năng
- T1.4: Xác định phạm vi và ràng buộc

**T2 — Thiết kế:**

- T2.1: Thiết kế kiến trúc tổng thể (HW + SW)
- T2.2: Thiết kế sơ đồ mạch điện
- T2.3: Thiết kế giao thức truyền thông (WebSocket, JSON)
- T2.4: Thiết kế cơ sở dữ liệu
- T2.5: Thiết kế giao diện Web (wireframe/mockup)
- T2.6: Thiết kế pipeline AI (ARX → Kalman → MPC)

**T3 — Phát triển:**

- T3.1: Lắp ráp phần cứng (mạch, cảm biến, relay, Solar Tracking)
- T3.2: Lập trình firmware ESP32
- T3.3: Phát triển Backend Django + WebSocket Server
- T3.4: Phát triển Web Dashboard (ReactJS)
- T3.5: Huấn luyện mô hình ARX
- T3.6: Phát triển Kalman Filter
- T3.7: Phát triển MPC Controller
- T3.8: Tích hợp AI vào Backend

**T4 — Kiểm thử:**

- T4.1: Kiểm thử phần cứng và firmware
- T4.2: Kiểm thử Backend, Web và AI
- T4.3: Kiểm thử tích hợp end-to-end

**T5 — Hoàn thành:**

- T5.1: Hiệu chỉnh phần cứng và mô hình AI
- T5.2: Hoàn thành báo cáo và bảo vệ đồ án

### 3.3.3 Mã hóa WBS

WBS sử dụng mã phân cấp dạng số với quy tắc:

```
[Mã sản phẩm].[Mã công việc]
```

Ví dụ:

- `P3.T3.6` = Sản phẩm "Backend + AI" → Công việc "Phát triển Kalman Filter"
- `P1.T2.2` = Sản phẩm "Phần cứng" → Công việc "Thiết kế sơ đồ mạch"

Trong bảng WBS dưới đây, để đơn giản, mã WBS được đánh số tuần tự dạng `WBS-XXX`.

---

## 3.4 Bảng WBS hoàn chỉnh

**Sơ đồ WBS dạng cây phân cấp**

```
Hệ thống Nhà kính Thông minh
├── P1: Phần cứng
│   ├── P1.1: Module cảm biến
│   │   ├── T2: Thiết kế sơ đồ kết nối cảm biến
│   │   ├── T3: Lắp ráp & đấu nối DHT22, Soil, LDR
│   │   └── T4: Kiểm thử giá trị cảm biến
│   ├── P1.2: Module relay + actuator
│   │   └── T3: Lắp ráp relay, bơm ×2, quạt, phun sương, đèn LED
│   ├── P1.3: Mô hình nhà kính
│   │   └── T3: Xây dựng khung nhà kính, bố trí thiết bị
│   └── P1.4: Module Solar Tracking
│       ├── T3: Lắp ráp tấm pin, TP4056, Servo ×2, LDR ×4, relay ×3
│       └── T4: Kiểm thử Solar Tracking
├── P2: Firmware ESP32
│   ├── P2.1: Module đọc cảm biến
│   │   └── T3: Lập trình đọc DHT22, Soil, LDR
│   ├── P2.2: Module WebSocket Client
│   │   └── T3: Lập trình kết nối WiFi, gửi/nhận dữ liệu
│   └── P2.3: Module điều khiển relay
│       └── T3: Lập trình nhận lệnh → kích relay → ACK, Manual/Auto
├── P3: Backend + AI
│   ├── P3.1: Django Server + API + Database
│   │   └── T3: Phát triển REST API, MySQL schema, migrations
│   ├── P3.2: Django Channels (WebSocket Server)
│   │   └── T3: Phát triển consumer, routing, xử lý real-time
│   ├── P3.3: Mô hình ARX
│   │   ├── T1: Thu thập và xử lý dữ liệu 105.120 mẫu
│   │   └── T3: Huấn luyện ARX(5,1,2), đánh giá FIT/RMSE
│   ├── P3.4: Kalman Filter
│   │   └── T3: Phát triển Adaptive Kalman Filter với IAE
│   └── P3.5: MPC Controller
│       └── T3: Phát triển hàm chi phí Zone/Range, ràng buộc, tối ưu
├── P4: Web Dashboard
│   ├── P4.1: Giao diện giám sát
│   │   └── T3: Phát triển Dashboard, biểu đồ real-time, cảnh báo
│   └── P4.2: Giao diện điều khiển
│       └── T3: Phát triển nút bật/tắt thiết bị, trang dự báo
└── P5: Kiểm thử
    ├── P5.1: Kiểm thử hệ thống
    │   ├── T4: Kiểm thử phần cứng và firmware
    │   └── T4: Kiểm thử Backend, Web Dashboard và AI
    ├── P5.2: Hiệu chỉnh
    │   └── T4: Hiệu chỉnh cảm biến, tune tham số MPC, sửa lỗi
    └── P5.3: Hoàn thành dự án
        └── T5: Demo hoàn chỉnh, báo cáo PBL + QLDA, slide, bảo vệ
```

**Bảng WBS chi tiết**

| Mã WBS | Sản phẩm | Công việc | Mô tả | Người PT |
|:------:|----------|-----------|-------|:--------:|
| **P1** | **Phần cứng** | | | **B** |
| P1.1.T2 | Module cảm biến | Thiết kế sơ đồ kết nối | Thiết kế sơ đồ kết nối DHT22, Soil Moisture, LDR vào ESP32 | B |
| P1.1.T3 | Module cảm biến | Lắp ráp & đấu nối | Lắp ráp cảm biến trên breadboard, đấu nối vào ESP32 | B |
| P1.1.T4 | Module cảm biến | Kiểm thử cảm biến | Kiểm tra giá trị đọc được từ từng cảm biến | B |
| P1.2.T3 | Module relay + actuator | Lắp ráp relay & actuator | Kết nối relay 4 kênh, bơm ×2, quạt, phun sương, đèn LED | B |
| P1.3.T3 | Mô hình nhà kính | Xây dựng khung nhà kính | Dựng khung, bố trí cảm biến và thiết bị bên trong | B |
| P1.4.T3 | Module Solar Tracking | Lắp ráp Solar Tracking | Kết nối tấm pin NLMT, TP4056, Servo ×2, LDR ×4, relay ×3 | B |
| P1.4.T4 | Module Solar Tracking | Kiểm thử Solar Tracking | Kiểm tra servo xoay theo ánh sáng, sạc pin hoạt động | B |
| **P2** | **Firmware ESP32** | | | **B** |
| P2.1.T3 | Module đọc cảm biến | Lập trình đọc cảm biến | Code đọc DHT22, Soil, LDR với chu kỳ ≤ 5 giây | B |
| P2.2.T3 | Module WebSocket Client | Lập trình WebSocket | Kết nối WiFi, gửi telemetry, nhận lệnh, auto-reconnect | B |
| P2.3.T3 | Module điều khiển relay | Lập trình điều khiển | Nhận lệnh → kích relay → gửi ACK, chuyển Manual/Auto | B |
| **P3** | **Backend + AI** | | | **A, B, C** |
| P3.1.T3 | Django Server + API + DB | Phát triển API & Database | Django REST API, MySQL schema, migrations, endpoints | B |
| P3.2.T3 | Django Channels | Phát triển WebSocket Server | Consumer, routing, xử lý dữ liệu real-time | B |
| P3.3.T1 | Mô hình ARX | Thu thập dữ liệu | Dataset 105.120 mẫu, tiền xử lý, chia train/val/test | A |
| P3.3.T3 | Mô hình ARX | Huấn luyện ARX | ARX(5,1,2), Least Squares, đánh giá FIT/RMSE | A |
| P3.4.T3 | Kalman Filter | Phát triển Kalman | Adaptive Kalman Filter với IAE lọc nhiễu cảm biến | C |
| P3.5.T3 | MPC Controller | Phát triển MPC | Hàm chi phí Zone/Range, ràng buộc, tối ưu điều khiển | C |
| **P4** | **Web Dashboard** | | | **B** |
| P4.1.T3 | Giao diện giám sát | Phát triển giám sát | Dashboard tổng quan, biểu đồ real-time, cảnh báo ngưỡng | B |
| P4.2.T3 | Giao diện điều khiển | Phát triển điều khiển | Nút bật/tắt thiết bị, trang dự báo xu hướng | B |
| **P5** | **Kiểm thử** | | | **A, B, C** |
| P5.1.T4 | Kiểm thử hệ thống | Kiểm thử HW & FW | Test cảm biến, relay, WebSocket, LCD | B |
| P5.1.T4 | Kiểm thử hệ thống | Kiểm thử BE, Web & AI | Test API, Dashboard, mô hình ARX/Kalman/MPC | A, B, C |
| P5.2.T4 | Hiệu chỉnh | Hiệu chỉnh hệ thống | Calibrate cảm biến, tune tham số MPC, sửa lỗi tích hợp | A, B, C |
| P5.3.T5 | Hoàn thành dự án | Báo cáo & bảo vệ | Demo hoàn chỉnh, viết báo cáo PBL + QLDA, slide, bảo vệ | A, B, C |

---

## 3.5 Kiểm soát các phiên bản WBS

Trong quá trình thực hiện dự án, WBS có thể được cập nhật khi có thay đổi phạm vi. Nguyên tắc kiểm soát phiên bản:

- **Không được hủy các phiên bản trước** để quản lý được các vấn đề nảy sinh do sự thay đổi.
- Các phiên bản cần có **số hiệu và ngày tháng**.
- Mỗi lần thay đổi cần được **ghi nhận lý do** và **phê duyệt** bởi PM.

| Phiên bản |  Ngày  | Thay đổi                                  | Lý do                                         |
| :---------: | :-----: | ------------------------------------------- | ---------------------------------------------- |
|    v1.0    | Tuần 2 | WBS ban đầu                               | Phân rã lần đầu sau phân tích yêu cầu |
|    v1.1    | Tuần 5 | Thêm P3.4.T3 (Kalman Filter) chi tiết hơn | Quyết định dùng Adaptive Kalman            |
|    v1.2    | Tuần 7 | Thêm P4.2.T3 (Trang dự báo)               | Yêu cầu bổ sung từ giảng viên            |

---
