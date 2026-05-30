# CHƯƠNG 2: XÁC ĐỊNH DỰ ÁN

---

## 2.1 Xác định mục đích và mục tiêu dự án

### 2.1.1 Mối quan hệ giữa mục đích và mục tiêu

Trong quản lý dự án, **mục đích (Goal)** và **mục tiêu (Objective)** có mối quan hệ phân cấp:

- **Mục đích** là định hướng tổng quát, mang tính **định tính**, mô tả "cái mà dự án muốn đạt tới" ở mức cao nhất.
- **Mục tiêu** là tập hợp con cụ thể của mục đích, mang tính **định lượng**, có thể đo lường được theo tiêu chí SMART (Specific, Measurable, Achievable, Relevant, Time-bound).

Mỗi mục đích có thể được phân rã thành **nhiều mục tiêu cụ thể**. Khi tất cả mục tiêu được hoàn thành, mục đích coi như đạt được.

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

**Mục đích:** Xây dựng hệ thống nhà kính thông minh tích hợp IoT và AI, cho phép giám sát, dự đoán và điều khiển tối ưu các thông số môi trường.

**Mục tiêu chính:**
1. Thu thập dữ liệu cảm biến realtime qua ESP32.
2. Dự đoán độ ẩm đất bằng mô hình ARX với FIT ≥ 80%.
3. Lọc nhiễu cảm biến bằng Adaptive Kalman Filter.
4. Điều khiển tối ưu bằng MPC, duy trì độ ẩm 55–65%.
5. Phát triển Web Dashboard giám sát và điều khiển.

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

**Thời gian:** 15 tuần × 3 người × ~15 giờ/tuần/người = ~675 giờ công.

**Chi phí ước tính:**

| Hạng mục | Chi phí (VNĐ) |
|----------|:-------------:|
| ESP32 DevKit | 120.000 |
| Cảm biến DHT22 | 35.000 |
| Cảm biến độ ẩm đất | 25.000 |
| Cảm biến ánh sáng LDR | 10.000 |
| Module relay 4 kênh | 45.000 |
| Bơm nước mini | 30.000 |
| Quạt mini | 25.000 |
| Phun sương mini | 35.000 |
| Đèn LED | 15.000 |
| Breadboard + dây nối | 40.000 |
| Mô hình nhà kính (khung) | 150.000 |
| LCD I2C | 45.000 |
| Linh kiện phụ (nguồn, cáp...) | 50.000 |
| **Tổng** | **~625.000** |

### 2.2.6 Danh sách rủi ro sơ bộ

| STT | Rủi ro | Mức độ ban đầu | Biện pháp dự kiến |
|:---:|--------|:--------------:|-------------------|
| 1 | Thiếu kinh nghiệm AI/MPC | Cao | Nghiên cứu lý thuyết 2 tuần trước khi code |
| 2 | Cảm biến hỏng/sai số lớn | Trung bình | Mua linh kiện dự phòng, dùng Kalman lọc nhiễu |
| 3 | Trễ tiến độ module AI | Cao | Phát triển song song, dùng dữ liệu mô phỏng |
| 4 | Mất kết nối WiFi/WebSocket | Trung bình | Auto-reconnect, buffer dữ liệu cục bộ |
| 5 | Thay đổi yêu cầu giữa chừng | Trung bình | Ghi nhận vào nhật ký, đánh giá tác động |

> *Chi tiết phân tích rủi ro sẽ được trình bày ở Chương 9.*

### 2.2.7 Điều chỉnh và cập nhật

SOW có thể được điều chỉnh khi có thay đổi phạm vi hoặc yêu cầu. Mọi điều chỉnh cần được:
- Ghi nhận bằng văn bản.
- Thảo luận và thống nhất giữa các bên.
- Ký xác nhận lại nếu thay đổi lớn.

### 2.2.8 Chữ ký các bên liên quan

| Vai trò | Họ tên | Chữ ký | Ngày |
|---------|--------|:------:|:----:|
| Giảng viên hướng dẫn | _________________ | _______ | ___/___/2026 |
| Quản lý dự án (PM) - A | _________________ | _______ | ___/___/2026 |
| Thành viên B | _________________ | _______ | ___/___/2026 |
| Thành viên C | _________________ | _______ | ___/___/2026 |

---

## 2.3 Vai trò và trách nhiệm trong dự án

### 2.3.1 Phân công vai trò

| Vai trò | Người đảm nhiệm | Trách nhiệm chính |
|---------|:----------------:|-------------------|
| **Khách hàng / Nhà tài trợ** | Giảng viên hướng dẫn | Đặt yêu cầu, phản hồi tiến độ, đánh giá và chấm điểm |
| **PM + AI Developer** | Thành viên A | Quản lý dự án, phân công, ARX/Kalman/MPC, tích hợp hệ thống |
| **FW + HW Engineer** | Thành viên B | Thiết kế mạch, lập trình ESP32, cảm biến, relay, WebSocket client |
| **Web + Backend Developer** | Thành viên C | Django Backend, ReactJS Dashboard, API, Database |

### 2.3.2 Ma trận RACI

Ma trận RACI xác định vai trò của từng thành viên đối với mỗi hoạt động:
- **R** (Responsible): Người thực hiện
- **A** (Accountable): Người chịu trách nhiệm cuối cùng
- **C** (Consulted): Người được tham vấn
- **I** (Informed): Người được thông báo

| STT | Hoạt động | A (PM + AI) | B (FW/HW) | C (Web/BE) | Giảng viên |
|:---:|-----------|:---:|:---:|:---:|:---:|
| 1 | Lập kế hoạch dự án | **A/R** | C | C | I |
| 2 | Phân tích yêu cầu | **A/R** | R | R | C |
| 3 | Thiết kế kiến trúc tổng thể | **A/R** | C | C | I |
| 4 | Thiết kế phần cứng | C | **A/R** | I | I |
| 5 | Phát triển Firmware ESP32 | I | **A/R** | C | I |
| 6 | Thiết kế Database | C | I | **A/R** | I |
| 7 | Phát triển Backend | C | I | **A/R** | I |
| 8 | Phát triển Web Dashboard | I | I | **A/R** | I |
| 9 | Huấn luyện mô hình ARX | **A/R** | I | C | I |
| 10 | Phát triển Kalman Filter | **A/R** | C | I | I |
| 11 | Phát triển MPC | **A/R** | C | C | I |
| 12 | Tích hợp hệ thống | **A** | R | R | I |
| 13 | Kiểm thử tích hợp | **A** | R | R | C |
| 14 | Viết báo cáo | **A** | R | R | I |
| 15 | Bảo vệ đồ án | R | R | R | **A** |

---

### 2.3.3 Bảng phân công công việc chi tiết

| Tuần | Công việc | Người thực hiện | Thời lượng (h) | Deliverable |
|:----:|-----------|:---------------:|:--------------:|-------------|
| 1 | Khảo sát yêu cầu đề tài | A, B, C | 15h/người | Tài liệu yêu cầu |
| 2 | Viết SOW, lập WBS, phân công RACI | A | 20h | SOW + WBS + RACI |
| 2 | Khảo sát linh kiện, báo giá | B | 15h | Danh sách BOM |
| 2 | Khảo sát tech stack (Django, React) | C | 15h | Tài liệu so sánh |
| 3 | Thiết kế kiến trúc tổng thể + AI pipeline | A | 18h | Sơ đồ kiến trúc |
| 3–4 | Thiết kế mạch, sơ đồ nguyên lý | B | 16h | Sơ đồ mạch |
| 3–4 | Thiết kế DB schema + UI wireframe | C | 16h | ER Diagram + Figma |
| 4–6 | Lắp ráp phần cứng, test cảm biến | B | 20h | Prototype HW |
| 5–7 | Lập trình Firmware ESP32 + WebSocket | B | 18h | FW hoàn chỉnh |
| 5–7 | Setup Django, viết REST API | C | 18h | API endpoints |
| 5–8 | Nghiên cứu + huấn luyện ARX | A | 25h | Mô hình ARX (FIT≥85%) |
| 7–8 | Phát triển WebSocket server | C | 20h | WS real-time |
| 8–10 | Phát triển Kalman Filter + MPC | A | 28h | Pipeline AI |
| 8–10 | Fix bug FW, cải thiện ổn định | B | 12h | FW v2 |
| 9–12 | Phát triển ReactJS Dashboard | C | 22h | Web Dashboard |
| 11–12 | Tích hợp hệ thống, MPC tuning | A | 25h | End-to-end system |
| 11–12 | Kiểm thử HW + FW | B | 15h | Test report HW |
| 12–13 | Kiểm thử tích hợp toàn hệ thống | A, B, C | 15h/người | Bug list + fix |
| 13–14 | Viết báo cáo PBL + QLDA | A, B, C | 18h/người | Báo cáo 10 chương |
| 15 | Làm slide, chuẩn bị demo, bảo vệ | A, B, C | 10h/người | Slide + Demo |

> **Tổng giờ công ước tính:** A = ~168h, B = ~119h, C = ~137h → Tổng = **424h** cho 15 tuần.

---
