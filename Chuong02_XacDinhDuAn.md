# CHƯƠNG 2: XÁC ĐỊNH DỰ ÁN

---

## 2.1 Xác định mục đích và mục tiêu dự án

### 2.1.1 Mối quan hệ giữa mục đích và mục tiêu

Trong quản lý dự án, **Mục đích (Goal)** và **Mục tiêu (Objective)** có quan hệ phân cấp chặt chẽ:
* **Mục đích (Goal):** Định hướng tổng quát ở mức cao, mang tính **định tính** (xác định dự án hướng tới cái gì).
* **Mục tiêu (Objective):** Tập hợp con cụ thể của mục đích, mang tính **định lượng** (đo lường được qua tiêu chí SMART). Khi toàn bộ mục tiêu hoàn thành, mục đích của dự án coi như đạt được.

### 2.1.2 Bảng mục đích – mục tiêu dự án nhà kính thông minh

| Mục đích (Goal) | Mục tiêu cụ thể (Objective) | Chỉ tiêu đo lường |
|------------------|------------------------------|-------------------|
| **G1:** Xây dựng hệ thống giám sát môi trường nhà kính tự động | O1.1: Thu thập dữ liệu 4 thông số cảm biến (nhiệt độ, độ ẩm KK, ánh sáng, độ ẩm đất) theo thời gian thực | Chu kỳ lấy mẫu ≤ 5 giây |
| | O1.2: Hiển thị dữ liệu trên Web Dashboard | ≥ 6 màn hình chức năng |
| | O1.3: Cảnh báo khi thông số vượt ngưỡng | Cảnh báo trong ≤ 3 giây |
| **G2:** Xây dựng mô hình AI dự đoán và điều khiển tối ưu | O2.1: Huấn luyện mô hình ARX(5,1,2) dự đoán độ ẩm đất | FIT 1-step ≥ 80% |
| | O2.2: Tích hợp Kalman Filter lọc nhiễu cảm biến | Giảm biên dao động so với dữ liệu thô |
| | O2.3: Triển khai MPC giữ độ ẩm đất trong vùng mục tiêu | Độ ẩm duy trì 55–65% |
| **G3:** Đảm bảo truyền thông ổn định giữa các thành phần | O3.1: Giao tiếp WebSocket hai chiều ESP32 ↔ Backend | Reconnect tự động khi mất kết nối |
| | O3.2: Cơ chế ACK xác nhận lệnh điều khiển | 100% lệnh được xác nhận |
| **G4:** Hoàn thành dự án đúng tiến độ và chất lượng | O4.1: Hoàn thành trong 15 tuần | Đúng deadline |
| | O4.2: Viết báo cáo đầy đủ và bảo vệ thành công | Đạt điểm ≥ 7.0 |

---

## 2.2 Tài liệu phác thảo dự án (Statement of Work — SOW)

Statement of Work (SOW) là văn bản thống nhất giữa các bên liên quan về mục đích, mục tiêu, phạm vi, lịch trình, kinh phí và kết quả chuyển giao của dự án. SOW được xây dựng từ đầu dự án và có thể điều chỉnh khi có thay đổi được các bên thống nhất.

---

### 2.2.1 Mục đích và mục tiêu

Để làm căn cứ pháp lý và phạm vi trong tài liệu SOW này, các mục đích và mục tiêu cốt lõi của dự án được kế thừa hoàn toàn từ phần phân tích SMART tại **Mục 2.1 (Bảng 2.1)**. Mục tiêu trọng tâm của SOW là xây dựng hệ thống IoT thu thập dữ liệu realtime (ESP32) kết hợp với mô hình AI (ARX, Kalman, MPC) nhằm duy trì độ ẩm đất ổn định trong khoảng tối ưu (55% - 65%) và hiển thị trực quan qua Web Dashboard.

### 2.2.2 Phạm vi dự án

- **Bao gồm:** Phần cứng (ESP32, cảm biến, relay, actuator), Firmware, Backend (Django), AI (ARX, Kalman, MPC), Web Dashboard (ReactJS), Tài liệu báo cáo.
- **Không bao gồm:** App mobile, triển khai cloud, phân quyền chi tiết, mô hình phi tuyến, thiết kế PCB.

### 2.2.3 Kết quả chuyển giao (Deliverables)

| STT | Deliverable | Mô tả | Thời điểm chuyển giao |
|:---:|-------------|-------|:---------------------:|
| 1 | Hệ thống phần cứng | ESP32 + cảm biến + relay + actuator hoạt động | Tuần 6 |
| 2 | Firmware ESP32 | Chương trình nhúng thu thập + WebSocket + điều khiển | Tuần 7 |
| 3 | Backend Server | Django + Django Channels + API + Database | Tuần 9 |
| 4 | Mô hình AI | ARX + Kalman Filter + MPC đã huấn luyện và tích hợp | Tuần 11 |
| 5 | Web Dashboard | ReactJS giao diện giám sát + điều khiển + biểu đồ | Tuần 12 |
| 6 | Tài liệu | Báo cáo PBL + Báo cáo QLDA | Tuần 14 |
| 7 | Bảo vệ | Slide thuyết trình + Demo hệ thống | Tuần 15 |

### 2.2.4 Các mốc quan trọng (Milestones)

| STT | Milestone | Mô tả | Tuần |
|:---:|-----------|-------|:----:|
| M1 | Hoàn thành khảo sát và phân tích yêu cầu | Xác định đầy đủ yêu cầu chức năng và phi chức năng | Tuần 2 |
| M2 | Hoàn thành thiết kế hệ thống | Kiến trúc HW/SW, sơ đồ mạch, thiết kế DB | Tuần 4 |
| M3 | Phần cứng hoạt động | ESP32 đọc được cảm biến, điều khiển relay | Tuần 6 |
| M4 | Backend + WebSocket hoạt động | Nhận/gửi dữ liệu realtime | Tuần 8 |
| M5 | Mô hình AI hoàn thành | ARX huấn luyện xong, Kalman + MPC tích hợp | Tuần 11 |
| M6 | Web Dashboard hoàn thành | Toàn bộ giao diện hoạt động | Tuần 12 |
| M7 | Kiểm thử tích hợp | Toàn hệ thống chạy end-to-end | Tuần 13 |
| M8 | Hoàn thành báo cáo | Nộp báo cáo PBL + QLDA | Tuần 14 |
| M9 | Bảo vệ đồ án | Thuyết trình + Demo | Tuần 15 |

### 2.2.5 Ước lượng sơ bộ

- **Thời gian:** 15 tuần × 3 người × ~15 giờ/tuần = ~675 giờ công.
- **Chi phí thiết bị (BOM):** ~625.000 VNĐ.

| Hạng mục | Chi tiết linh kiện | Chi phí (VNĐ) |
|----------|-------------------|:-------------:|
| Bộ điều khiển & LCD | ESP32 DevKit, Màn hình LCD I2C | 165.000 |
| Module cảm biến | Nhiệt độ DHT22, Độ ẩm đất, Ánh sáng LDR | 70.000 |
| Cơ cấu chấp hành | Relay 4 kênh, Bơm nước, Quạt mini, Phun sương, Đèn LED | 150.000 |
| Khung mô hình & Phụ kiện | Mô hình nhà kính, Breadboard, dây nối, nguồn, cáp... | 240.000 |
| **Tổng cộng** | **Toàn bộ phần cứng hệ thống** | **625.000** |

### 2.2.6 Danh sách rủi ro sơ bộ

| STT | Rủi ro | Mức độ ban đầu | Biện pháp dự kiến |
|:---:|--------|:--------------:|-------------------|
| 1 | Thiếu kinh nghiệm AI/MPC | Cao | Nghiên cứu lý thuyết 2 tuần trước khi code |
| 2 | Cảm biến hỏng/sai số lớn | Trung bình | Mua linh kiện dự phòng, dùng Kalman lọc nhiễu |
| 3 | Trễ tiến độ module AI | Cao | Phát triển song song, dùng dữ liệu mô phỏng |
| 4 | Mất kết nối WiFi/WebSocket | Trung bình | Auto-reconnect, buffer dữ liệu cục bộ |
| 5 | Thay đổi yêu cầu giữa chừng | Trung bình | Ghi nhận vào nhật ký, đánh giá tác động |

> *Chi tiết phân tích rủi ro sẽ được trình bày ở Chương 9.*

---

## 2.3 Vai trò và trách nhiệm trong dự án

### 2.3.1 Phân công vai trò

| Vai trò | Người đảm nhiệm | Trách nhiệm chính |
|---------|:----------------:|-------------------|
| **Khách hàng / Nhà tài trợ** | Giảng viên hướng dẫn | Đặt yêu cầu, phản hồi tiến độ, đánh giá và chấm điểm |
| **PM + AI Developer (ARX)** | Hoàng Minh Trí (Thành viên A) | Quản lý tiến độ dự án, lập kế hoạch và phân công công việc; thiết kế kiến trúc tổng thể hệ thống; nghiên cứu và phát triển mô hình ARX; tích hợp hệ thống tổng thể |
| **FW + HW & Web/BE Fullstack** | Đinh Công Trung Sỹ (Thành viên B) | Thiết kế và lắp ráp phần cứng; lập trình ESP32; kết nối cảm biến nhiệt độ, độ ẩm, ánh sáng, độ ẩm đất; điều khiển relay; xây dựng WebSocket client/server; phát triển Django Backend & ReactJS Dashboard Full-stack; thiết kế REST API & MySQL Database |
| **AI & Control Engineer** | Ngô Quang Sinh (Thành viên C) | Nghiên cứu và phát triển pipeline AI gồm Kalman Filter và MPC; tích hợp mô hình dự đoán ARX vào bộ điều khiển MPC và hệ thống điều khiển tối ưu |

### 2.3.2 Ma trận RACI

Ma trận RACI xác định vai trò của từng thành viên đối với mỗi hoạt động:
- **R** (Responsible): Người thực hiện
- **A** (Accountable): Người chịu trách nhiệm cuối cùng
- **C** (Consulted): Người được tham vấn
- **I** (Informed): Người được thông báo

| STT | Hoạt động | A (PM + ARX) | B (HW/FW & Fullstack) | C (Kalman & MPC) | Giảng viên |
|:---:|-----------|:---:|:---:|:---:|:---:|
| 1 | Lập kế hoạch dự án | **A/R** | C | C | I |
| 2 | Phân tích yêu cầu | **A/R** | R | R | C |
| 3 | Thiết kế kiến trúc tổng thể | **A/R** | C | C | I |
| 4 | Thiết kế phần cứng | C | **A/R** | I | I |
| 5 | Phát triển Firmware ESP32 | I | **A/R** | C | I |
| 6 | Thiết kế Database | C | **A/R** | I | I |
| 7 | Phát triển Backend | C | **A/R** | I | I |
| 8 | Phát triển Web Dashboard | I | **A/R** | C | I |
| 9 | Huấn luyện mô hình ARX | **A/R** | I | C | I |
| 10 | Phát triển Kalman Filter | C | I | **A/R** | I |
| 11 | Phát triển MPC | C | C | **A/R** | I |
| 12 | Tích hợp ARX vào hệ thống MPC | C | I | **A/R** | I |
| 13 | Tích hợp hệ thống | **A** | R | R | I |
| 14 | Kiểm thử tích hợp | **A** | R | R | C |
| 15 | Viết báo cáo | **A** | R | R | I |
| 16 | Bảo vệ đồ án | R | R | R | **A** |

---

### 2.3.3 Bảng phân công công việc chi tiết

| Giai đoạn | Nội dung công việc | Người thực hiện | Thời lượng (h) | Kết quả bàn giao (Deliverable) |
|:---------:|---------------------|:---------------:|:--------------:|--------------------------------|
| **Tuần 1** | Khảo sát yêu cầu đề tài | A, B, C | 15h / người | Tài liệu yêu cầu ban đầu |
| **Tuần 2** | - Lập kế hoạch dự án (SOW, WBS, RACI)<br>- Khảo sát linh kiện và lựa chọn Tech Stack | A (PM)<br>B (Dev) | 20h<br>30h | SOW, WBS, RACI, BOM |
| **Tuần 3–4** | - Thiết kế kiến trúc hệ thống và AI pipeline<br>- Thiết kế mạch nguyên lý, DB schema, UI wireframe | A (PM)<br>B (Dev) | 18h<br>32h | Sơ đồ mạch, ERD, Mockup Figma |
| **Tuần 4–7** | - Lắp ráp phần cứng và phát triển Firmware ESP32<br>- Thiết lập Django Server, viết REST API | B (Dev) | 38h | Prototype HW, API endpoints |
| **Tuần 5–8** | Nghiên cứu và huấn luyện mô hình dự đoán ARX | A (PM) | 25h | Mô hình ARX (FIT ≥ 85%) |
| **Tuần 7–10**| - Phát triển WebSocket server & Web Dashboard (React)<br>- Nghiên cứu & lập trình Kalman Filter + MPC | B (Dev)<br>C (Dev) | 42h<br>28h | WS real-time, Web Dashboard, AI pipeline |
| **Tuần 11–12**| - Tích hợp hệ thống tổng thể, tinh chỉnh bộ MPC<br>- Kiểm thử đơn vị phần cứng & firmware | A, C<br>B | 25h / người<br>15h | Hệ thống hoạt động End-to-End |
| **Tuần 12–13**| Kiểm thử tích hợp toàn hệ thống và sửa lỗi | A, B, C | 15h / người | Hệ thống hoàn thiện, Báo cáo lỗi |
| **Tuần 13–14**| Viết báo cáo kỹ thuật PBL và báo cáo QLDA | A, B, C | 18h / người | Báo cáo PBL & QLDA hoàn chỉnh |
| **Tuần 15** | Chuẩn bị slide, chạy thử demo và bảo vệ đồ án | A, B, C | 10h / người | Slide thuyết trình, Demo hoàn chỉnh |

> **Tổng giờ công ước tính:** A = ~146h, B = ~245h, C = ~111h → Tổng = **502h** cho 15 tuần. (Do B đảm nhiệm cả phần cứng và phần mềm Web Full-stack nên khối lượng công việc kỹ thuật lớn nhất, A phụ trách quản lý dự án & mô hình hóa ARX, C chịu trách nhiệm phần lọc nhiễu Kalman & thuật toán điều khiển MPC và tích hợp ARX).

---
