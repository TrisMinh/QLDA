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

Sản phẩm tổng của dự án là **"Hệ thống Nhà kính Thông minh (Smart Greenhouse)"** — bao gồm phần cứng, phần mềm nhúng, backend + AI, web dashboard và tài liệu.

### 3.2.2 Sản phẩm con cấp 1

| Mã | Sản phẩm cấp 1            | Mô tả                                                         |
| :-: | ---------------------------- | --------------------------------------------------------------- |
| P1 | Phần cứng (Hardware)       | Mạch điện, cảm biến, relay, actuator, mô hình nhà kính |
| P2 | Phần mềm nhúng (Firmware) | Chương trình trên ESP32                                     |
| P3 | Backend + AI                 | Server Django, mô hình ARX, Kalman, MPC                       |
| P4 | Web Dashboard                | Giao diện ReactJS giám sát và điều khiển                 |
| P5 | Tài liệu                   | Báo cáo PBL, báo cáo QLDA, slide thuyết trình             |

### 3.2.3 Sản phẩm con cấp 2

| Mã | Sản phẩm cấp 2                                          | Thuộc cấp 1 |
| :--: | ---------------------------------------------------------- | :-----------: |
| P1.1 | Module cảm biến (DHT22, Soil, LDR)                       |      P1      |
| P1.2 | Module relay + actuator (bơm, quạt, phun sương, đèn) |      P1      |
| P1.3 | Mô hình nhà kính (khung, bố trí)                     |      P1      |
| P1.4 | LCD I2C hiển thị                                         |      P1      |
| P2.1 | Module đọc cảm biến                                    |      P2      |
| P2.2 | Module WebSocket Client                                    |      P2      |
| P2.3 | Module điều khiển relay                                 |      P2      |
| P2.4 | Module hiển thị LCD                                      |      P2      |
| P2.5 | Module chuyển chế độ Manual/Auto                       |      P2      |
| P3.1 | Django Server + API                                        |      P3      |
| P3.2 | Django Channels (WebSocket Server)                         |      P3      |
| P3.3 | Database MySQL                                             |      P3      |
| P3.4 | Mô hình ARX                                              |      P3      |
| P3.5 | Kalman Filter                                              |      P3      |
| P3.6 | MPC Controller                                             |      P3      |
| P4.1 | Trang đăng nhập                                         |      P4      |
| P4.2 | Dashboard tổng quan                                       |      P4      |
| P4.3 | Trang biểu đồ realtime                                  |      P4      |
| P4.4 | Trang điều khiển thiết bị                             |      P4      |
| P4.5 | Trang cảnh báo                                           |      P4      |
| P4.6 | Trang dự báo xu hướng                                  |      P4      |
| P5.1 | Báo cáo PBL                                              |      P5      |
| P5.2 | Báo cáo QLDA                                             |      P5      |
| P5.3 | Slide thuyết trình                                       |      P5      |

---

## 3.3 Danh sách công việc (TBS — Task Breakdown Structure)

### 3.3.1 Các công việc tổng

| Mã | Công việc tổng        | Mô tả                                                              |
| :-: | ------------------------ | -------------------------------------------------------------------- |
| T1 | Phân tích yêu cầu    | Khảo sát, xác định yêu cầu chức năng và phi chức năng    |
| T2 | Thiết kế               | Thiết kế kiến trúc, sơ đồ mạch, thiết kế DB, thiết kế UI |
| T3 | Phát triển             | Lập trình firmware, backend, web, AI                               |
| T4 | Kiểm thử               | Kiểm thử đơn vị, tích hợp, hệ thống                         |
| T5 | Triển khai & Tài liệu | Triển khai demo, viết báo cáo, chuẩn bị bảo vệ               |

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

- T3.1: Lắp ráp phần cứng (mạch, cảm biến, relay)
- T3.2: Lập trình firmware ESP32
- T3.3: Phát triển Backend Django
- T3.4: Phát triển WebSocket Server (Django Channels)
- T3.5: Phát triển Web Dashboard (ReactJS)
- T3.6: Huấn luyện mô hình ARX
- T3.7: Phát triển Kalman Filter
- T3.8: Phát triển MPC Controller
- T3.9: Tích hợp AI vào Backend

**T4 — Kiểm thử:**

- T4.1: Kiểm thử phần cứng (cảm biến, relay)
- T4.2: Kiểm thử firmware (WebSocket, điều khiển)
- T4.3: Kiểm thử Backend (API, Database)
- T4.4: Kiểm thử Web Dashboard
- T4.5: Kiểm thử mô hình AI (ARX accuracy, MPC performance)
- T4.6: Kiểm thử tích hợp end-to-end

**T5 — Triển khai & Tài liệu:**

- T5.1: Triển khai demo hoàn chỉnh
- T5.2: Viết báo cáo PBL
- T5.3: Viết báo cáo QLDA
- T5.4: Chuẩn bị slide thuyết trình
- T5.5: Bảo vệ đồ án

### 3.3.3 Mã hóa WBS

Hệ thống mã hóa WBS sử dụng **mã phân cấp dạng số** với quy tắc:

```
[Mã sản phẩm].[Mã công việc]
```

Ví dụ:

- `P3.T3.6` = Sản phẩm "Backend + AI" → Công việc "Huấn luyện mô hình ARX"
- `P1.T2.2` = Sản phẩm "Phần cứng" → Công việc "Thiết kế sơ đồ mạch"

Trong bảng WBS dưới đây, để đơn giản, mã WBS được đánh số tuần tự dạng `WBS-XXX`.

---

## 3.4 Bảng WBS hoàn chỉnh

**Sơ đồ WBS dạng cây phân cấp**

```
Hệ thống Nhà kính Thông minh
├── P1: Phần cứng
│   ├── P1.1: Module cảm biến
│   │   ├── T1: Khảo sát & chọn cảm biến
│   │   ├── T2: Thiết kế sơ đồ kết nối
│   │   ├── T3: Lắp ráp & đấu nối
│   │   └── T4: Kiểm thử cảm biến
│   ├── P1.2: Module relay + actuator
│   │   ├── T2: Thiết kế mạch relay
│   │   ├── T3: Lắp ráp bơm, quạt, phun sương, đèn
│   │   └── T4: Kiểm thử relay + actuator
│   ├── P1.3: Mô hình nhà kính
│   │   └── T3: Xây dựng khung nhà kính
│   └── P1.4: LCD I2C
│       ├── T3: Kết nối LCD
│       └── T4: Kiểm thử hiển thị
├── P2: Firmware ESP32
│   ├── P2.1: Module đọc cảm biến
│   │   ├── T2: Thiết kế giao tiếp SPI/I2C
│   │   ├── T3: Lập trình đọc DHT22, Soil, LDR
│   │   └── T4: Kiểm thử giá trị cảm biến
│   ├── P2.2: Module WebSocket Client
│   │   ├── T2: Thiết kế giao thức JSON
│   │   ├── T3: Lập trình kết nối, gửi/nhận dữ liệu
│   │   └── T4: Kiểm thử reconnect, độ trễ
│   ├── P2.3: Module điều khiển relay
│   │   ├── T3: Lập trình nhận lệnh → kích relay → gửi ACK
│   │   └── T4: Kiểm thử bật/tắt từng thiết bị
│   ├── P2.4: Module hiển thị LCD
│   │   └── T3: Lập trình hiển thị thông số
│   └── P2.5: Module chuyển chế độ
│       └── T3: Lập trình nút bấm Manual/Auto
├── P3: Backend + AI
│   ├── P3.1: Django Server + API
│   │   ├── T2: Thiết kế models, views, serializers
│   │   ├── T3: Phát triển REST API
│   │   └── T4: Kiểm thử endpoints
│   ├── P3.2: Django Channels (WebSocket)
│   │   ├── T2: Thiết kế consumer, routing
│   │   ├── T3: Phát triển WebSocket server
│   │   └── T4: Kiểm thử realtime
│   ├── P3.3: Database MySQL
│   │   ├── T2: Thiết kế schema time-series
│   │   └── T3: Migration, seed data
│   ├── P3.4: Mô hình ARX
│   │   ├── T1: Thu thập dữ liệu 105.120 mẫu
│   │   ├── T2: Thiết kế pipeline ARX(5,1,2)
│   │   ├── T3: Huấn luyện Least Squares
│   │   └── T4: Đánh giá FIT/RMSE
│   ├── P3.5: Kalman Filter
│   │   ├── T2: Thiết kế Adaptive Kalman + IAE
│   │   ├── T3: Phát triển bộ lọc
│   │   └── T4: Đánh giá giảm nhiễu
│   └── P3.6: MPC Controller
│       ├── T2: Thiết kế hàm chi phí Zone/Range
│       ├── T3: Phát triển tối ưu + ràng buộc
│       └── T4: Đánh giá điều khiển
├── P4: Web Dashboard
│   ├── P4.1: Trang đăng nhập
│   │   ├── T2: Thiết kế UI login
│   │   └── T3: Phát triển form + xác thực
│   ├── P4.2: Dashboard tổng quan
│   │   ├── T2: Thiết kế layout card
│   │   └── T3: Phát triển hiển thị thông số
│   ├── P4.3: Biểu đồ realtime
│   │   └── T3: Phát triển Chart.js time-series
│   ├── P4.4: Điều khiển thiết bị
│   │   └── T3: Phát triển nút bật/tắt
│   ├── P4.5: Cảnh báo
│   │   └── T3: Phát triển hiển thị cảnh báo ngưỡng
│   └── P4.6: Dự báo xu hướng
│       └── T3: Phát triển hiển thị dự đoán ARX
└── P5: Tài liệu
    ├── P5.1: Báo cáo PBL
    │   └── T5: Viết báo cáo kỹ thuật
    ├── P5.2: Báo cáo QLDA
    │   └── T5: Viết 10 chương QLDA
    └── P5.3: Slide thuyết trình
        └── T5: Chuẩn bị PowerPoint + Demo
```

**Bảng WBS chi tiết**

| Mã WBS | Tên công việc | Mô tả | Mức | Người phụ trách |
|:------:|---------------|-------|:---:|:---------------:|
| **1.0** | **Phân tích yêu cầu** | | **1** | **A, B, C** |
| 1.1 | Khảo sát giải pháp hiện có | Tìm hiểu Priva Connext, Ridder Drive, các giải pháp trong nước | 2 | A |
| 1.2 | Xác định yêu cầu chức năng | Liệt kê các chức năng: giám sát, điều khiển, dự đoán, cảnh báo | 2 | A, B, C |
| 1.3 | Xác định yêu cầu phi chức năng | Hiệu năng, độ tin cậy, bảo mật | 2 | A |
| 1.4 | Xác định phạm vi & ràng buộc | Trong/ngoài phạm vi, ràng buộc thời gian/chi phí/nhân lực | 2 | A |
| **2.0** | **Thiết kế hệ thống** | | **1** | **A, B, C** |
| 2.1 | Thiết kế kiến trúc tổng thể | Kiến trúc client-server + IoT, sơ đồ thành phần | 2 | A |
| 2.2 | Thiết kế sơ đồ mạch điện | Sơ đồ kết nối ESP32, cảm biến, relay | 2 | B |
| 2.3 | Thiết kế giao thức truyền thông | Định dạng JSON, WebSocket protocol, ACK mechanism | 2 | A, B |
| 2.4 | Thiết kế cơ sở dữ liệu | Schema MySQL cho time-series data | 2 | B |
| 2.5 | Thiết kế giao diện Web | Wireframe/mockup cho 6 màn hình | 2 | B |
| 2.6 | Thiết kế pipeline AI | Luồng: Sensor → Kalman → ARX → MPC → Actuator | 2 | A, C |
| **3.0** | **Phát triển phần cứng** | | **1** | **B** |
| 3.1 | Lắp ráp mạch cảm biến | Kết nối DHT22, Soil Moisture, LDR vào ESP32 | 2 | B |
| 3.2 | Lắp ráp mạch relay + actuator | Kết nối relay 4 kênh, bơm, quạt, phun sương, đèn | 2 | B |
| 3.3 | Xây dựng mô hình nhà kính | Dựng khung nhà kính, bố trí cảm biến và thiết bị | 2 | B |
| 3.4 | Kết nối LCD I2C | Lắp và hiển thị thông tin trên LCD | 2 | B |
| **4.0** | **Phát triển Firmware** | | **1** | **B** |
| 4.1 | Lập trình đọc cảm biến | Code đọc DHT22, Soil, LDR, lấy trung bình | 2 | B |
| 4.2 | Lập trình WebSocket Client | Kết nối, gửi telemetry, nhận pending_commands | 2 | B |
| 4.3 | Lập trình điều khiển relay | Nhận lệnh → kích relay → gửi ACK | 2 | B |
| 4.4 | Lập trình hiển thị LCD | Hiển thị thông số cảm biến lên LCD | 2 | B |
| 4.5 | Lập trình chuyển chế độ | Nút bấm hoặc lệnh chuyển Manual/Auto | 2 | B |
| **5.0** | **Phát triển Backend** | | **1** | **B** |
| 5.1 | Phát triển Django Server | Setup project, models, views, serializers | 2 | B |
| 5.2 | Phát triển REST API | API endpoints cho web dashboard | 2 | B |
| 5.3 | Phát triển WebSocket Server | Django Channels consumer, routing | 2 | B |
| 5.4 | Thiết lập Database MySQL | Migration, schema, seed data | 2 | B |
| **6.0** | **Phát triển AI** | | **1** | **A, C** |
| 6.1 | Thu thập và xử lý dữ liệu | Dataset 105.120 mẫu, tiền xử lý, chia train/val/test | 2 | A |
| 6.2 | Huấn luyện mô hình ARX | ARX(5,1,2), Least Squares, đánh giá FIT/RMSE | 2 | A |
| 6.3 | Phát triển Kalman Filter | Adaptive Kalman Filter với IAE | 2 | C |
| 6.4 | Phát triển MPC Controller | Hàm chi phí Zone/Range, ràng buộc, tối ưu | 2 | C |
| 6.5 | Tích hợp AI vào Backend | Kết nối pipeline AI với Django | 2 | B, C |
| **7.0** | **Phát triển Web Dashboard** | | **1** | **B** |
| 7.1 | Phát triển trang đăng nhập | Form login, xác thực | 2 | B |
| 7.2 | Phát triển dashboard tổng quan | Card hiển thị thông số, trạng thái thiết bị | 2 | B |
| 7.3 | Phát triển biểu đồ realtime | Chart.js/Recharts cho time-series | 2 | B |
| 7.4 | Phát triển trang điều khiển | Nút bật/tắt bơm, quạt, phun sương, đèn | 2 | B |
| 7.5 | Phát triển trang cảnh báo | Hiển thị cảnh báo khi vượt ngưỡng | 2 | B |
| 7.6 | Phát triển trang dự báo | Hiển thị dự đoán ARX + MPC | 2 | B |
| **8.0** | **Kiểm thử** | | **1** | **A, B, C** |
| 8.1 | Kiểm thử phần cứng | Test cảm biến đọc đúng, relay hoạt động | 2 | B |
| 8.2 | Kiểm thử firmware | Test WebSocket, điều khiển, chế độ | 2 | B |
| 8.3 | Kiểm thử Backend + API | Test endpoints, WebSocket server | 2 | B |
| 8.4 | Kiểm thử Web Dashboard | Test UI, chức năng, responsive | 2 | B |
| 8.5 | Kiểm thử mô hình AI | Đánh giá FIT, RMSE, MPC performance | 2 | A, C |
| 8.6 | Kiểm thử tích hợp | Test end-to-end: ESP32 → Backend → Web | 2 | A, B, C |
| **9.0** | **Triển khai & Tài liệu** | | **1** | **A, B, C** |
| 9.1 | Triển khai demo hoàn chỉnh | Setup và chạy toàn bộ hệ thống | 2 | A, B, C |
| 9.2 | Viết báo cáo PBL | Báo cáo kỹ thuật đồ án PBL | 2 | A, B, C |
| 9.3 | Viết báo cáo QLDA | Báo cáo quản lý dự án 10 chương | 2 | A, B, C |
| 9.4 | Chuẩn bị slide thuyết trình | Slide PowerPoint cho buổi bảo vệ | 2 | A |
| 9.5 | Bảo vệ đồ án | Thuyết trình + Demo trước hội đồng | 2 | A, B, C |


---

**Tiêu chuẩn WBS tốt**

Bảng WBS của dự án nhà kính thông minh được đánh giá theo các tiêu chuẩn:

| STT | Tiêu chuẩn                                                              | Đạt? | Giải thích                                                                                     |
| :-: | ------------------------------------------------------------------------- | :----: | ------------------------------------------------------------------------------------------------ |
|  1  | **Mọi nhánh chi tiết đến mức thấp nhất theo quy tắc 8/80** |   ✅   | Phân rã đến work package cấp 2, mỗi WP tốn 8–80 giờ, có thể phân công cho 1 người |
|  2  | **Mọi ô đánh mã duy nhất**                                    |   ✅   | Mỗi công việc có mã WBS riêng (1.0 → 9.5), không trùng lặp                             |
|  3  | **Mọi ô PBS mô tả bằng danh từ (tính từ nếu cần)**        |   ✅   | Ví dụ: "Module cảm biến", "Database MySQL"                                                   |
|  4  | **Mọi công việc xác định đầy đủ**                         |   ✅   | Mỗi work package có mô tả, người phụ trách, mức phân cấp                              |
|  5  | **Đã được phản hồi và chấp thuận**                        |   ✅   | WBS được cả nhóm thảo luận và thống nhất trước khi triển khai                       |

**100% Rule:** Tổng các work packages bao phủ toàn bộ phạm vi dự án đã xác định ở Chương 1 (mục 1.4). Mọi deliverable ở mục 2.2.3 đều có công việc tương ứng trong WBS.

---

## 3.5 Kiểm soát các phiên bản WBS

Trong quá trình thực hiện dự án, WBS có thể được cập nhật khi có thay đổi phạm vi. Nguyên tắc kiểm soát phiên bản:

- **Không được hủy các phiên bản trước** để quản lý được các vấn đề nảy sinh do sự thay đổi.
- Các phiên bản cần có **số hiệu và ngày tháng**.
- Mỗi lần thay đổi cần được **ghi nhận lý do** và **phê duyệt** bởi PM.

| Phiên bản |  Ngày  | Thay đổi                                  | Lý do                                         |
| :---------: | :-----: | ------------------------------------------- | ---------------------------------------------- |
|    v1.0    | Tuần 2 | WBS ban đầu                               | Phân rã lần đầu sau phân tích yêu cầu |
|    v1.1    | Tuần 5 | Thêm WP 6.3 (Kalman Filter) chi tiết hơn | Quyết định dùng Adaptive Kalman            |
|    v1.2    | Tuần 7 | Thêm WP 7.6 (Trang dự báo)               | Yêu cầu bổ sung từ giảng viên            |

---
