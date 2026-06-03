# CHƯƠNG 2: XÁC ĐỊNH DỰ ÁN

## 2.1 Xác định mục đích và mục tiêu dự án

Bảng 3. Mục đích và mục tiêu dự án

| Mục đích (Goal) | Mục tiêu cụ thể (Objective) |
|-----------------|-----------------------------|
| G1: Xây dựng hệ thống giám sát môi trường nhà kính tự động | O1.1: Thu thập dữ liệu 4 thông số cảm biến theo thời gian thực<br>O1.2: Hiển thị dữ liệu trên Web Dashboard<br>O1.3: Cảnh báo khi thông số vượt ngưỡng |
| G2: Xây dựng mô hình AI dự đoán và điều khiển tối ưu | O2.1: Huấn luyện mô hình ARX(5,1,2) dự đoán độ ẩm đất<br>O2.2: Tích hợp Kalman Filter lọc nhiễu cảm biến<br>O2.3: Triển khai MPC giữ độ ẩm đất trong vùng mục tiêu |
| G3: Đảm bảo truyền thông ổn định giữa các thành phần | O3.1: Giao tiếp WebSocket hai chiều ESP32 ↔ Backend<br>O3.2: Cơ chế ACK xác nhận lệnh điều khiển |
| G4: Hoàn thành dự án đúng tiến độ và chất lượng | O4.1: Hoàn thành trong 15 tuần<br>O4.2: Viết báo cáo đầy đủ và bảo vệ thành công |

## 2.2 Phạm vi dự án

Dự án tập trung xây dựng hệ thống nhà kính thông minh ở quy mô mô hình nguyên mẫu trong phòng thí nghiệm. Hệ thống bao gồm phần cứng ESP32 kết nối cảm biến và relay, firmware nhúng giao tiếp WebSocket, Backend Django tích hợp pipeline AI (ARX, Kalman Filter, MPC), và giao diện Web Dashboard trên ReactJS hiển thị dữ liệu real-time. Ngoài ra, hệ thống tích hợp module Solar Tracking sử dụng tấm pin năng lượng mặt trời kết hợp Servo và cảm biến ánh sáng LDR.

- Bao gồm: Phần cứng (ESP32, cảm biến, relay, actuator, Solar Tracking), Firmware, Backend (Django), AI (ARX, Kalman, MPC), Web Dashboard (ReactJS).
- Không bao gồm: App mobile, triển khai cloud, phân quyền chi tiết, mô hình phi tuyến, thiết kế PCB.

## 2.3 Nguồn nhân lực

Bảng 4. Phân công vai trò

| Vai trò | Người đảm nhiệm | Trách nhiệm chính |
|---------|-----------------|-------------------|
| Khách hàng | Giảng viên | Đặt yêu cầu, phản hồi tiến độ, đánh giá và chấm điểm |
| PM + AI (ARX) | Hoàng Minh Trí<br>(Thành viên A) | Quản lý tiến độ dự án, lập kế hoạch và phân công công việc; thiết kế kiến trúc tổng thể hệ thống; nghiên cứu và phát triển mô hình ARX; tích hợp hệ thống tổng thể |
| FW + HW & Web/BE Fullstack | Đinh Công Trung Sỹ (Thành viên B) | Thiết kế và lắp ráp phần cứng; lập trình ESP32; kết nối cảm biến nhiệt độ, độ ẩm, ánh sáng, độ ẩm đất; điều khiển relay; xây dựng WebSocket client/server; phát triển Django Backend & ReactJS Dashboard Full-stack; thiết kế REST API & MySQL Database |
| AI & Control Engineer | Ngô Quang Sinh (Thành viên C) | Nghiên cứu và phát triển pipeline AI gồm Kalman Filter và MPC; tích hợp mô hình dự đoán ARX vào bộ điều khiển MPC và hệ thống điều khiển tối ưu |

## 2.4 Thời gian thực hiện dự án

- Tổng thời gian: 15 tuần.
- Ngày bắt đầu: 5/01/2026.
- Ngày kết thúc: 10/05/2026.

## 2.5 Các mốc thực hiện dự án

Bảng 5. Các mốc thực hiện dự án

| Mã | Kết thúc giai đoạn | Ngày báo cáo | Yêu cầu |
|----|---------------------|--------------|---------|
| 1 | Khởi động dự án | 05/01/2026 | Lựa chọn thành viên làm chung trong học phần |
| 2 | Nộp đề xuất, lựa chọn đề tài | 21/01/2026 | Bản đề xuất đề tài, giới thiệu đề tài và tài liệu tham khảo liên quan |
| 3 | Báo cáo tiến độ lần 1 | 04/02/2026 | Trình bày đề xuất đề tài, tài liệu đã đọc, mã nguồn tham khảo, thiết bị phần cứng và BOM linh kiện |
| 4 | Báo cáo tiến độ lần 2 | 25/02/2026 | Báo cáo tiến độ lắp ráp ESP32, kết nối cảm biến, thiết kế sơ đồ mạch và các vấn đề kỹ thuật |
| 5 | Báo cáo tiến độ lần 3 | 18/03/2026 | Báo cáo tiến độ firmware, Backend Django, huấn luyện ARX và phân chia công việc |
| 6 | Báo cáo tiến độ lần 4 | 12/04/2026 | Báo cáo tiến độ Web Dashboard, Kalman Filter, MPC và tích hợp hệ thống |
| 7 | Báo cáo tiến độ lần 5 | 28/04/2026 | Báo cáo kiểm thử tích hợp, sửa lỗi và demo hệ thống |
| 8 | Báo cáo tổng kết dự án | 10/05/2026 | Báo cáo tổng kết và bảo vệ đồ án |

## 2.6 Kinh phí

Kinh phí thực hiện dự án Smart Greenhouse được nhóm tự túc nhằm phục vụ cho việc xây dựng mô hình prototype và triển khai hệ thống thử nghiệm trong phòng thí nghiệm. Các linh kiện phần cứng được lựa chọn dựa trên tiêu chí tối ưu chi phí nhưng vẫn đảm bảo đáp ứng yêu cầu kỹ thuật của hệ thống.

| STT | Tên linh kiện | Giá tiền (VNĐ) |
|-----|---------------|----------------|
| 1 | ESP32 DevKit V1 | 95.000 |
| 2 | Màn hình LCD I2C 16×2 | 70.000 |
| 3 | Cảm biến DHT22 + Cảm biến độ ẩm đất + LDR | 70.000 |
| 4 | Relay 4 kênh + Bơm nước ×2 + Quạt mini + Phun sương + Đèn LED | 210.000 |
| 5 | Mô hình nhà kính + Breadboard + dây nối + nguồn + cáp | 240.000 |
| 6 | Tấm pin NLMT 6V 5–7W | 130.000 |
| 7 | Module sạc TP4056 + Boost 5V + Đốc pin 18650 đôi + Pin 18650 ×2 | 160.000 |
| 8 | Servo SG90 ×2 | 60.000 |
| 9 | Cảm biến LDR GL5528 ×4 + Điện trở 10kΩ ×4 + Relay 1 kênh ×3 | 100.000 |
| 10 | Công tắc nguồn ON/OFF + Dây USB Type C | 65.000 |
| | Tổng cộng | 1.200.000 |
