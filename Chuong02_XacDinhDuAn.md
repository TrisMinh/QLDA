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

### 2.2.0 Tổng quan về SOW

**Statement of Work (SOW)** là văn bản thống nhất giữa **Lãnh đạo, Quản lý dự án, Khách hàng và Nhà tài trợ** về mục đích/mục tiêu rõ ràng của dự án. SOW có vai trò:
- Liệt kê chi phí, lịch trình và kết quả dự kiến.
- Xác định vai trò và trách nhiệm các bên.
- Có thể xét duyệt và cập nhật trong quá trình triển khai.

**Các thành phần chủ yếu của SOW:**
1. Giới thiệu dự án
2. Mục đích và mục tiêu
3. Phạm vi
4. Những người liên quan chính
5. Tài nguyên dự án
6. Các mốc thời gian
7. Kinh phí
8. Danh sách rủi ro
9. Điều chỉnh và cập nhật
10. Chữ ký các bên

**Quy trình thực hiện SOW:**

```
Viết dự thảo → Chuyển cho đơn vị tài trợ/khách hàng → Tổ chức họp, xét duyệt
    ↓                                                          ↓
Đã thống nhất → Các bên ký                          Không đạt → Sửa chữa → Quay lại xét duyệt
```

**Các sai lầm cần tránh khi lập SOW:**
- ❌ Nội dung không đầy đủ (đặc biệt là các ràng buộc).
- ❌ Nhượng bộ các yêu cầu không khả thi.
- ❌ Câu chữ mơ hồ, không rõ nghĩa.
- ❌ Không công bố rộng rãi bản phác thảo đã ký.
- ❌ Sau khi đã ký, những thay đổi (nếu có) mà không được cập nhật và thống nhất lại.

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

## 2.3 Xác định vai trò và trách nhiệm trong dự án

### 2.3.1 Ba đối tượng tham gia dự án (theo lý thuyết)

Theo lý thuyết quản lý dự án, mọi dự án đều có **3 nhóm đối tượng chính** tham gia:

**① Nhà tài trợ / Khách hàng:**

| Đối tượng | Trách nhiệm |
|-----------|-------------|
| **Nhà tài trợ** | Cung cấp, giải quyết tài chính và phê duyệt dự án; Đề ra và đảm bảo mục tiêu của dự án được đáp ứng; Xét duyệt và nghiệm thu kết quả |
| **Khách hàng** | Đưa ra yêu cầu dự án; Thụ hưởng kết quả và hỗ trợ cung cấp thông tin; Tham gia xét duyệt và nghiệm thu |

**② Ban giám đốc / Quản lý dự án:**

| Đối tượng | Trách nhiệm |
|-----------|-------------|
| **Ban giám đốc** | Bổ nhiệm nhân sự Ban quản lý dự án; Phụ trách giấy phép, thủ tục pháp lý và triển khai dự án |
| **Quản lý dự án (PM)** | Tổ chức đội ngũ, báo cáo hiện trạng; Đảm bảo phạm vi, chất lượng sản phẩm; Quản lý thay đổi, kiểm soát kế hoạch, tài nguyên và chi phí |

**③ Đội dự án:**
- Thực hiện các nhiệm vụ chuyên môn cụ thể.
- Cung cấp thông tin hỗ trợ quản lý (các công việc phải làm, ước lượng thời gian, các thay đổi nảy sinh).
- Báo cáo hiện trạng công việc định kỳ cho Quản lý dự án.

### 2.3.2 Áp dụng cho dự án Smart Greenhouse

| Vai trò lý thuyết | Áp dụng trong dự án | Người đảm nhiệm |
|-------------------|---------------------|:----------------:|
| Nhà tài trợ | Cung cấp kinh phí (tự túc) | Cả nhóm A, B, C |
| Khách hàng | Đặt yêu cầu, nghiệm thu, chấm điểm | Giảng viên hướng dẫn |
| Ban giám đốc / PM | Quản lý dự án, điều phối, kiểm soát | **Thành viên A** |
| Đội dự án | Thực hiện chuyên môn, báo cáo tiến độ | A, B, C |

> **Lưu ý:** Trong bối cảnh đồ án sinh viên, một số vai trò bị gộp — giảng viên vừa là khách hàng vừa là nhà tài trợ (cho điểm); thành viên A vừa là PM vừa là developer.

### 2.3.3 Quản lý dự án (PM) — Thành viên A

**Vai trò:** Project Manager kiêm AI Developer.

**Trách nhiệm:**
- Lập kế hoạch tổng thể, phân công công việc, theo dõi tiến độ.
- Điều phối họp nhóm, giải quyết xung đột, báo cáo cho giảng viên.
- Phát triển và huấn luyện mô hình AI: ARX, Kalman Filter, MPC.
- Tích hợp pipeline AI vào Backend.
- Viết báo cáo QLDA (Chương 1, 2, 3, 9, 10).

### 2.3.4 Nhóm phát triển — Vai trò & trách nhiệm từng thành viên

| Thành viên | Vai trò | Trách nhiệm chính |
|:----------:|---------|-------------------|
| **A** | PM + AI Developer | Quản lý dự án, mô hình ARX/Kalman/MPC, tích hợp AI, báo cáo QLDA (Ch1,2,3,9,10) |
| **B** | Firmware + Hardware Engineer | Thiết kế mạch, lập trình ESP32, cảm biến, relay, WebSocket client, báo cáo QLDA (Ch5,6,7) |
| **C** | Web + Backend Developer | Django Backend, ReactJS Dashboard, API, Database, báo cáo QLDA (Ch4,8) + Phụ lục |

### 2.3.5 Khách hàng / Giảng viên — Vai trò & trách nhiệm

**Vai trò:** Khách hàng (Customer) kiêm Nhà tài trợ (Sponsor).

**Trách nhiệm:**
- Đặt ra yêu cầu đề tài và phạm vi dự án.
- Cung cấp phản hồi trong các buổi báo cáo tiến độ.
- Đánh giá và chấm điểm sản phẩm cuối cùng.
- Hỗ trợ giải đáp thắc mắc kỹ thuật khi cần.

### 2.3.6 Ma trận RACI

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
