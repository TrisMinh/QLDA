# CHƯƠNG 2: XÁC ĐỊNH DỰ ÁN

---

## 2.1 Mục đích, mục tiêu của dự án

- **Mục đích:** Xây dựng hệ thống nhà kính thông minh Smart Greenhouse ứng dụng trí tuệ nhân tạo và IoT, góp phần tự động hóa quá trình giám sát, dự đoán và điều khiển tối ưu các thông số môi trường trong nhà kính, hướng tới mô hình canh tác nông nghiệp hiện đại.

- **Mục tiêu:**
  - Xây dựng phần cứng cho hệ thống bao gồm mạch ESP32 tích hợp cảm biến (nhiệt độ, độ ẩm không khí, ánh sáng, độ ẩm đất), relay điều khiển thiết bị chấp hành (bơm, quạt, phun sương, đèn LED) và module Solar Tracking.
  - Xây dựng firmware nhúng trên ESP32 thu thập dữ liệu cảm biến theo thời gian thực (chu kỳ ≤ 5 giây) và giao tiếp WebSocket hai chiều với Backend.
  - Huấn luyện mô hình dự đoán ARX(5,1,2) đạt độ chính xác FIT 1-step ≥ 80%, tích hợp bộ lọc Kalman thích nghi lọc nhiễu cảm biến và bộ điều khiển MPC duy trì độ ẩm đất trong vùng tối ưu 55–65%.
  - Xây dựng Backend Django tích hợp Django Channels xử lý dữ liệu real-time, REST API và cơ sở dữ liệu MySQL.
  - Xây dựng Web Dashboard trên ReactJS cho phép người dùng giám sát thông số môi trường, xem biểu đồ lịch sử, nhận cảnh báo ngưỡng và điều khiển thiết bị từ giao diện web.

---

## 2.2 Phạm vi của dự án

Dự án tập trung xây dựng hệ thống nhà kính thông minh ở quy mô mô hình prototype trong phòng thí nghiệm. Hệ thống bao gồm phần cứng ESP32 kết nối cảm biến và relay, firmware nhúng giao tiếp WebSocket, Backend Django tích hợp pipeline AI (ARX, Kalman Filter, MPC), và giao diện Web Dashboard trên ReactJS hiển thị dữ liệu real-time. Ngoài ra, hệ thống tích hợp module Solar Tracking sử dụng tấm pin năng lượng mặt trời kết hợp Servo và cảm biến ánh sáng LDR.

- **Bao gồm:** Phần cứng (ESP32, cảm biến, relay, actuator, Solar Tracking), Firmware, Backend (Django), AI (ARX, Kalman, MPC), Web Dashboard (ReactJS), Tài liệu báo cáo.
- **Không bao gồm:** App mobile, triển khai cloud, phân quyền chi tiết, mô hình phi tuyến, thiết kế PCB.

---

## 2.3 Nguồn nhân lực

- **Giảng viên hướng dẫn:** Giảng viên PBL phụ trách nhóm.
- **Nhóm trưởng:** Hoàng Minh Trí (Điều phối phân chia các hoạt động trong nhóm, thiết kế kiến trúc hệ thống, phát triển mô hình ARX).
- **Phần cứng + Firmware + Backend + Web:** Đinh Công Trung Sỹ (Thiết kế lắp ráp phần cứng, lập trình ESP32, phát triển Django Backend & ReactJS Dashboard Full-stack).
- **AI & Điều khiển:** Ngô Quang Sinh (Phát triển Kalman Filter & MPC, tích hợp mô hình ARX vào hệ thống điều khiển tối ưu).
- **Lắp đặt thiết bị phần cứng:** Nhóm làm chung.

---

## 2.4 Thời gian thực hiện dự án

- **Tổng thời gian:** 15 tuần.
- **Ngày bắt đầu:** 14/01/2026
- **Ngày kết thúc:** 10/05/2026

---

## 2.5 Các mốc thực hiện dự án

Bảng mốc các báo cáo, yêu cầu cần thực hiện:

| Mã | Kết thúc giai đoạn | Ngày báo cáo | Yêu cầu |
|:--:|---------------------|:------------:|----------|
| 1 | Khởi động dự án | 14/01/2026 | Lựa chọn thành viên làm chung trong học phần |
| 2 | Nộp đề xuất, lựa chọn đề tài | 21/01/2026 | Bản đề xuất đề tài, giới thiệu đề tài, các tài liệu tham khảo liên quan |
| 3 | Báo cáo tiến độ lần 1 | 04/02/2026 | Trình bày đề xuất đề tài, các tài liệu đã đọc, mã nguồn tham khảo, thiết bị phần cứng cần thiết và BOM linh kiện |
| 4 | Báo cáo tiến độ lần 2 | 25/02/2026 | Báo cáo tiến độ lắp ráp phần cứng ESP32, kết nối cảm biến, thiết kế sơ đồ mạch và các vấn đề kỹ thuật cần hướng dẫn |
| 5 | Báo cáo tiến độ lần 3 | 18/03/2026 | Báo cáo tiến độ firmware, Backend Django, huấn luyện mô hình ARX và phân chia công việc cho các thành viên |
| 6 | Báo cáo tiến độ lần 4 | 12/04/2026 | Báo cáo tiến độ hoàn thành Web Dashboard, Kalman Filter, MPC và tích hợp hệ thống |
| 7 | Báo cáo tiến độ lần 5 | 28/04/2026 | Báo cáo tiến độ kiểm thử tích hợp, sửa lỗi và các demo đã có được |
| 8 | Báo cáo tổng kết dự án | 10/05/2026 | Báo cáo tổng kết dự án, bảo vệ đồ án |

*Bảng 1: Các mốc thực hiện dự án*

---

## 2.6 Kinh phí

| STT | Tên linh kiện | Giá tiền (VNĐ) |
|:---:|---------------|:--------------:|
| 1 | ESP32 DevKit V1 | 95.000 |
| 2 | Màn hình LCD I2C 16×2 | 70.000 |
| 3 | Cảm biến DHT22 + Cảm biến độ ẩm đất + LDR | 70.000 |
| 4 | Relay 4 kênh + Bơm nước ×2 + Quạt mini + Phun sương + Đèn LED | 210.000 |
| 5 | Mô hình nhà kính + Breadboard + dây nối + nguồn + cáp | 240.000 |
| 6 | Tấm pin NLMT 6V 5-7W | 130.000 |
| 7 | Module sạc TP4056 + Boost 5V + Đốc pin 18650 đôi + Pin 18650 ×2 | 160.000 |
| 8 | Servo SG90 ×2 | 60.000 |
| 9 | Cảm biến LDR GL5528 ×4 + Điện trở 10kΩ ×4 + Relay 1 kênh ×3 | 100.000 |
| 10 | Công tắc nguồn ON/OFF + Dây USB Type C | 65.000 |
| | **Tổng cộng** | **1.200.000** |

---
