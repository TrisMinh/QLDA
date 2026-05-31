# CHƯƠNG 3: LIỆT KÊ CÔNG VIỆC DỰ ÁN (WBS)

---

## 3.1 Tổng quan về WBS

WBS (Work Breakdown Structure — Cấu trúc phân rã công việc) là công cụ **phân rã phạm vi dự án thành các công việc nhỏ hơn** có thể quản lý được, có dạng cây phân cấp từ tổng thể đến chi tiết. WBS được xây dựng bằng cách kết hợp hai thành phần:

- **PBS (Product Breakdown Structure):** Phân rã sản phẩm — liệt kê "cái gì cần tạo ra" (dùng **danh từ**).
- **TBS (Task Breakdown Structure):** Phân rã công việc — liệt kê "cần làm gì cho từng sản phẩm" (dùng **động từ + bổ ngữ**).

> **WBS = PBS × TBS** — Kết hợp danh sách sản phẩm và danh sách công việc thành WBS hoàn chỉnh.

**Các nguyên tắc cốt lõi:** Quy tắc 100% (tổng công việc con phải bao phủ đầy đủ công việc cha), Mutually Exclusive (không chồng chéo), Quy tắc 8/80 (mỗi work package tốn 8–80 giờ), và mỗi phần tử được đánh **mã duy nhất**.

WBS là cơ sở cho việc ước lượng thời gian (Chương 5), lập lịch biểu (Chương 6) và phân công nhân lực (Chương 8).

---

## 3.2 Bảng WBS hoàn chỉnh

Sản phẩm tổng của dự án là **"Hệ thống Nhà kính Thông minh (Smart Greenhouse)"** — bao gồm phần cứng, phần mềm nhúng, backend + AI, web dashboard và tài liệu. Bảng WBS dưới đây phân rã toàn bộ công việc dự án:

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

**100% Rule:** Tổng các work packages bao phủ toàn bộ phạm vi dự án đã xác định ở Chương 1 (mục 1.4). Mọi deliverable ở mục 2.2.3 đều có công việc tương ứng trong WBS.

---

## 3.3 Kiểm soát các phiên bản WBS

Trong quá trình thực hiện dự án, WBS có thể được cập nhật khi có thay đổi phạm vi. Nguyên tắc kiểm soát phiên bản:

- **Không được hủy các phiên bản trước** để quản lý được các vấn đề nảy sinh do sự thay đổi.
- Các phiên bản cần có **số hiệu và ngày tháng**.
- Mỗi lần thay đổi cần được **ghi nhận lý do** và **phê duyệt** bởi PM.

| Phiên bản | Ngày | Thay đổi | Lý do |
|:---------:|:----:|----------|-------|
| v1.0 | Tuần 2 | WBS ban đầu | Phân rã lần đầu sau phân tích yêu cầu |
| v1.1 | Tuần 5 | Thêm WP 6.3 (Kalman Filter) chi tiết hơn | Quyết định dùng Adaptive Kalman |
| v1.2 | Tuần 7 | Thêm WP 7.6 (Trang dự báo) | Yêu cầu bổ sung từ giảng viên |

---

## 3.4 Ước lượng thời gian (PERT)

Ước lượng thời gian theo công thức **PERT (Program Evaluation and Review Technique):**

```
EST = (MO + 4×ML + MP) / 6
```

Trong đó:
- **MO** (Most Optimistic): Thời gian lạc quan nhất — điều kiện lý tưởng.
- **ML** (Most Likely): Thời gian khả dĩ nhất — điều kiện bình thường.
- **MP** (Most Pessimistic): Thời gian bi quan nhất — điều kiện tồi nhất.

**Bảng ước lượng thời gian các work package chính:**

| ID | Work Package | MO (ngày) | ML (ngày) | MP (ngày) | EST (ngày) |
|:--:|-------------|:---------:|:---------:|:---------:|:----------:|
| 1.0 | Phân tích yêu cầu | 5 | 7 | 10 | **7.2** |
| 2.0 | Thiết kế hệ thống | 5 | 7 | 14 | **8.2** |
| 3.0 | Thiết kế + lắp ráp phần cứng | 7 | 10 | 14 | **10.2** |
| 4.0 | Phát triển Firmware ESP32 | 10 | 14 | 21 | **14.5** |
| 5.0 | Phát triển Backend Django | 14 | 21 | 28 | **21** |
| 6.0 | Nghiên cứu + huấn luyện ARX | 10 | 14 | 21 | **14.5** |
| 6.1 | Phát triển Kalman Filter | 5 | 7 | 14 | **8.2** |
| 6.2 | Phát triển MPC Controller | 7 | 14 | 21 | **14** |
| 7.0 | Phát triển Web Dashboard | 14 | 21 | 28 | **21** |
| 8.0 | Kiểm thử tích hợp | 5 | 7 | 14 | **8.2** |
| 9.0 | Triển khai + Tài liệu | 7 | 10 | 14 | **10.2** |
| | **Tổng** | **89** | **132** | **199** | **137.2** |

> **Nhận xét:** Đường găng đi qua chuỗi: Phân tích → Thiết kế → ARX → Kalman → MPC → Tích hợp → Triển khai. Tổng EST ≈ 137 ngày ≈ **19.6 tuần**, nhưng do song song hóa (HW//Backend//Web//AI), thực tế chỉ cần **15 tuần**.

---
