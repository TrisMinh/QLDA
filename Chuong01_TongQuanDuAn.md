# CHƯƠNG 1: TỔNG QUAN DỰ ÁN

---

## 1.1 Giới thiệu đề tài

### 1.1.1 Tên dự án

**Hệ thống Nhà kính Thông minh — Smart Greenhouse**

### 1.1.2 Mô tả tổng quát dự án

Dự án xây dựng một hệ thống nhà kính thông minh tích hợp công nghệ IoT và trí tuệ nhân tạo (AI), cho phép **giám sát liên tục** các thông số môi trường (nhiệt độ, độ ẩm không khí, cường độ ánh sáng, độ ẩm đất) và **điều khiển tự động** các thiết bị chấp hành (bơm nước, quạt thông gió, phun sương, đèn LED) nhằm duy trì điều kiện tối ưu cho sự sinh trưởng của cây trồng.

Hệ thống bao gồm 4 thành phần chính:

- **Phần cứng (Hardware):** Vi điều khiển ESP32, cảm biến DHT22 (nhiệt độ & độ ẩm), cảm biến độ ẩm đất, cảm biến ánh sáng LDR, relay điều khiển thiết bị chấp hành.
- **Firmware:** Chương trình nhúng trên ESP32 thu thập dữ liệu cảm biến, giao tiếp WebSocket hai chiều với Backend, nhận và thực thi lệnh điều khiển.
- **Backend + AI:** Server Django xử lý dữ liệu, chạy mô hình dự đoán ARX (AutoRegressive with eXogenous inputs), bộ lọc Kalman thích nghi (Adaptive Kalman Filter) để lọc nhiễu cảm biến, và bộ điều khiển dự đoán mô hình MPC (Model Predictive Control) để tối ưu hóa điều khiển tưới tiêu.
- **Web Dashboard:** Giao diện ReactJS cho phép giám sát thời gian thực, điều khiển thủ công, xem biểu đồ lịch sử, cảnh báo ngưỡng và dự báo xu hướng.

### 1.1.3 Bối cảnh thực hiện

- **Môn học:** Đồ án PBL (Project-Based Learning) — Hệ thống nhúng, kết hợp báo cáo môn Quản lý dự án phần mềm.
- **Nhóm thực hiện:** 3 thành viên (A, B, C).
- **Thời gian thực hiện:** 1 học kỳ (khoảng 15 tuần).
- **Địa điểm:** Trường Đại học Bách khoa — Đại học Đà Nẵng.

### 1.1.4 Lý do chọn đề tài

Trong bối cảnh biến đổi khí hậu ngày càng phức tạp, tài nguyên nước và đất nông nghiệp ngày càng bị thu hẹp, việc ứng dụng công nghệ vào sản xuất nông nghiệp đã trở thành xu hướng tất yếu. Các hệ thống nhà kính thương mại hiện tại (như Priva Connext, Ridder Drive) có chi phí cao và chủ yếu điều khiển theo ngưỡng cứng (rule-based), chưa tích hợp mô hình dự đoán hay điều khiển tối ưu.

Nhóm chọn đề tài này vì:
- **Tính thực tiễn:** Kết hợp IoT, AI và điều khiển tự động — xu hướng nông nghiệp 4.0.
- **Tính học thuật:** Áp dụng kiến thức liên ngành: hệ thống nhúng, xử lý tín hiệu, mô hình hóa hệ thống, điều khiển tối ưu.
- **Tính khả thi:** Sử dụng ESP32 chi phí thấp, phù hợp quy mô sinh viên.
- **Tính sáng tạo:** Tích hợp mô hình ARX + Kalman + MPC — vượt xa mức rule-based thông thường.

---

## 1.2 Mục đích dự án (Goals)

### 1.2.1 Mục đích tổng quát

Xây dựng một hệ thống nhà kính thông minh có khả năng **giám sát**, **dự đoán** và **điều khiển tối ưu** các thông số môi trường, hướng tới mô hình canh tác nông nghiệp hiện đại, tiết kiệm tài nguyên và nâng cao năng suất cây trồng.

### 1.2.2 Ý nghĩa thực tiễn

| STT | Ý nghĩa | Mô tả |
|:---:|---------|-------|
| 1 | Tiết kiệm nước | MPC tối ưu lượng tưới, tránh tưới quá tay hoặc để đất khô |
| 2 | Nâng cao năng suất | Duy trì điều kiện tối ưu cho cây trồng tự động |
| 3 | Giảm sức lao động | Tự động hóa thay thế giám sát thủ công |
| 4 | Ứng dụng IoT | Giám sát và điều khiển từ xa qua Web Dashboard |
| 5 | Nền tảng nghiên cứu | Mô hình ARX + Kalman + MPC có thể mở rộng cho các bài toán khác |

---

## 1.3 Mục tiêu dự án (Objectives)

### 1.3.1 Các mục tiêu cụ thể (SMART)

| Mục tiêu | S (Specific) | M (Measurable) | A (Achievable) | R (Relevant) | T (Time-bound) |
|-----------|:---:|:---:|:---:|:---:|:---:|
| Thu thập dữ liệu cảm biến realtime | Thu thập nhiệt độ, độ ẩm, ánh sáng, độ ẩm đất | Chu kỳ lấy mẫu ≤ 5 giây | ESP32 + cảm biến sẵn có | Cần cho mô hình AI | Tuần 1–4 |
| Xây dựng mô hình dự đoán ARX | Mô hình ARX(5,1,2) dự đoán độ ẩm đất | FIT 1-step ≥ 80% | Least Squares + Python | Là nền tảng cho MPC | Tuần 5–8 |
| Tích hợp Kalman Filter | Lọc nhiễu cảm biến bằng Adaptive Kalman | Giảm biên dao động so với dữ liệu thô | Thuật toán IAE | Cải thiện chất lượng dữ liệu | Tuần 7–9 |
| Triển khai MPC | Điều khiển tối ưu giữ ẩm đất trong vùng mục tiêu | Độ ẩm duy trì 55–65% | Dựa trên ARX đã huấn luyện | Mục tiêu cuối cùng | Tuần 9–12 |
| Phát triển Web Dashboard | Giao diện giám sát + điều khiển | ≥ 6 màn hình chức năng | ReactJS + Django | Giao diện người dùng | Tuần 6–13 |

### 1.3.2 Các chức năng cần đạt

1. **Giám sát thời gian thực:** Hiển thị nhiệt độ, độ ẩm không khí, ánh sáng, độ ẩm đất trên Dashboard.
2. **Biểu đồ lịch sử:** Xem xu hướng dữ liệu cảm biến theo thời gian (time-series chart).
3. **Điều khiển thủ công (Manual Mode):** Bật/tắt bơm, quạt, phun sương, đèn từ Web.
4. **Điều khiển tự động (AI-based Mode):** Hệ thống tự quyết định tưới/quạt dựa trên ARX + MPC.
5. **Cảnh báo ngưỡng:** Thông báo khi thông số vượt ngưỡng an toàn.
6. **Dự báo xu hướng:** Hiển thị dự đoán độ ẩm đất trong tương lai.
7. **Đăng nhập hệ thống:** Xác thực người dùng trước khi truy cập.

### 1.3.3 Các chỉ tiêu đánh giá

| STT | Chỉ tiêu | Giá trị mục tiêu | Kết quả đạt được |
|:---:|----------|:-----------------:|:-----------------:|
| 1 | FIT 1-step (ARX) | ≥ 80% | 85,85% ✅ |
| 2 | FIT free-run (ARX) | ≥ 60% | 66,42% ✅ |
| 3 | RMSE free-run | ≤ 1.5 | 0,978 ✅ |
| 4 | Vùng mục tiêu MPC | 55–65% | Đạt ✅ |
| 5 | Kalman Filter | Giảm dao động so với raw | Đạt ✅ |
| 6 | Số màn hình Dashboard | ≥ 6 | 6 màn hình ✅ |
| 7 | Truyền thông WebSocket | Hai chiều realtime | Đạt ✅ |

---

## 1.4 Phạm vi dự án

### 1.4.1 Phạm vi chức năng

**Trong phạm vi:**
- Giám sát 4 thông số: nhiệt độ, độ ẩm không khí, ánh sáng, độ ẩm đất.
- Điều khiển 4 thiết bị: bơm nước, quạt, phun sương, đèn LED.
- 2 chế độ: Manual và AI-based (Auto).
- Mô hình dự đoán ARX cho độ ẩm đất.
- Bộ lọc Kalman thích nghi (Adaptive Kalman Filter).
- Bộ điều khiển MPC tối ưu tưới tiêu.
- Web Dashboard giám sát và điều khiển.

### 1.4.2 Phạm vi kỹ thuật

| Thành phần | Công nghệ |
|------------|-----------|
| Vi điều khiển | ESP32 (Dual-core 240MHz, WiFi) |
| Cảm biến | DHT22, Soil Moisture Sensor, LDR |
| Giao tiếp | WebSocket (JSON) |
| Backend | Django + Django Channels + DRF |
| Frontend | ReactJS + Vite + Tailwind CSS |
| Database | MySQL |
| AI/ML | Python (ARX, Kalman, MPC) |
| Firmware | PlatformIO + Arduino Framework |

### 1.4.3 Phạm vi người dùng

- **Người dùng chính:** Sinh viên, giảng viên trong phạm vi đồ án.
- **Người dùng mở rộng (tiềm năng):** Nông dân, kỹ sư nông nghiệp muốn áp dụng hệ thống thông minh.

### 1.4.4 Những gì ngoài phạm vi dự án

- ❌ Ứng dụng di động (mobile app).
- ❌ Triển khai trên cloud (AWS, GCP).
- ❌ Phân quyền người dùng chi tiết (admin/operator).
- ❌ Mô hình phi tuyến (LSTM, Transformer).
- ❌ Quản lý nhiều khu vực nhà kính (multi-zone).
- ❌ Cảm biến pH, EC, mực nước.
- ❌ Thiết kế mạch PCB hoàn chỉnh.

---

## 1.5 Các bên liên quan (Stakeholders)

| STT | Bên liên quan | Vai trò | Kỳ vọng |
|:---:|---------------|---------|---------|
| 1 | **Giảng viên hướng dẫn** | Khách hàng + Nhà tài trợ (đánh giá, cho điểm) | Hệ thống hoạt động đúng, báo cáo đầy đủ |
| 2 | **Thành viên A** | Quản lý dự án (PM) + Phát triển AI (ARX, Kalman, MPC) | Hoàn thành đúng tiến độ, chất lượng tốt |
| 3 | **Thành viên B** | Phát triển Firmware + Phần cứng | Hệ thống HW/FW hoạt động ổn định |
| 4 | **Thành viên C** | Phát triển Web Dashboard + Backend | Giao diện đẹp, chức năng đầy đủ |
| 5 | **Người dùng cuối** | Sử dụng hệ thống giám sát/điều khiển | Giao diện trực quan, dễ sử dụng |

---

## 1.6 Ràng buộc dự án

### 1.6.1 Ràng buộc về thời gian
- Thời gian thực hiện: **15 tuần** (1 học kỳ).
- Bao gồm: nghiên cứu, thiết kế, phát triển, kiểm thử, viết báo cáo và bảo vệ.

### 1.6.2 Ràng buộc về chi phí
- Ngân sách **tự túc** bởi các thành viên.
- Chi phí ước tính chủ yếu cho linh kiện phần cứng: ESP32, cảm biến, relay, bơm, quạt, vật tư nhà kính.
- Phần mềm sử dụng mã nguồn mở (miễn phí).

### 1.6.3 Ràng buộc về nhân lực
- **3 thành viên** — tất cả đều là sinh viên, chưa có kinh nghiệm dự án thực tế lớn.
- Thời gian làm việc hạn chế do phải song song với các môn học khác.

### 1.6.4 Ràng buộc về công nghệ
- ESP32 giới hạn về bộ nhớ và tốc độ xử lý.
- Cảm biến giá rẻ có sai số (±3–5%).
- WebSocket yêu cầu kết nối WiFi ổn định.

### 1.6.5 Ràng buộc về thiết bị
- Mô hình nhà kính ở mức **thử nghiệm** (prototype), không phải nhà kính thực tế.
- Sử dụng breadboard đấu nối, chưa có mạch PCB.

---

## 1.7 Rủi ro tổng quát ban đầu

| STT | Rủi ro | Mô tả | Mức độ ban đầu |
|:---:|--------|-------|:--------------:|
| 1 | Thiếu nhân lực / thiếu kinh nghiệm | 3 thành viên đều là sinh viên, chưa quen dự án lớn | Cao |
| 2 | Thay đổi yêu cầu | Giảng viên hoặc nhóm thay đổi yêu cầu giữa chừng | Trung bình |
| 3 | Trễ tiến độ | Khối lượng công việc lớn, thời gian hạn chế | Cao |
| 4 | Lỗi kỹ thuật phần cứng | Cảm biến hỏng, mạch chập, ESP32 lỗi kết nối | Trung bình |
| 5 | Lỗi kỹ thuật phần mềm | Bug trong mô hình ARX/MPC, lỗi WebSocket | Trung bình |

> *Chi tiết phân tích rủi ro sẽ được trình bày ở Chương 9.*

---

## 1.8 Phương pháp phát triển phần mềm

### 1.8.1 Giới thiệu Waterfall

Mô hình Waterfall (thác nước) là phương pháp phát triển phần mềm tuần tự, trong đó mỗi giai đoạn phải hoàn thành trước khi chuyển sang giai đoạn tiếp theo.

**Các giai đoạn:** Phân tích yêu cầu → Thiết kế → Phát triển → Kiểm thử → Triển khai → Bảo trì.

**Ưu điểm:**
- Rõ ràng, có cấu trúc, dễ quản lý.
- Tài liệu đầy đủ ở mỗi giai đoạn.
- Phù hợp khi yêu cầu ổn định, ít thay đổi.

**Nhược điểm:**
- Khó quay lại giai đoạn trước khi phát hiện lỗi.
- Không linh hoạt với thay đổi yêu cầu.
- Sản phẩm chỉ thấy ở cuối quá trình.

### 1.8.2 Giới thiệu Agile/Scrum

Agile là phương pháp phát triển phần mềm linh hoạt, chia dự án thành các sprint ngắn (2–4 tuần), mỗi sprint tạo ra sản phẩm hoạt động được.

**Scrum** là framework phổ biến nhất trong Agile, bao gồm:
- **Sprint Planning:** Lập kế hoạch cho sprint.
- **Daily Standup:** Họp ngắn hàng ngày.
- **Sprint Review:** Đánh giá kết quả sprint.
- **Sprint Retrospective:** Rút kinh nghiệm.

**Ưu điểm:**
- Linh hoạt, thích ứng nhanh với thay đổi.
- Phản hồi sớm từ khách hàng.
- Sản phẩm tăng trưởng dần (incremental).

**Nhược điểm:**
- Cần kinh nghiệm và kỷ luật cao.
- Khó quản lý tài liệu.
- Không phù hợp nếu yêu cầu rất rõ ràng từ đầu.

### 1.8.3 Lý do lựa chọn mô hình cho dự án

Nhóm lựa chọn **mô hình Waterfall** cho dự án Smart Greenhouse.

| Tiêu chí | Waterfall ✅ | Agile/Scrum ❌ | Lý do chọn Waterfall |
|-----------|:-----------:|:-------------:|---------------------|
| Yêu cầu | Ổn định, xác định rõ từ đầu | Thay đổi liên tục | Yêu cầu đề tài PBL **ổn định**, được giảng viên duyệt từ đầu |
| Quy mô nhóm | Phù hợp mọi quy mô | Phù hợp nhóm lớn | Nhóm chỉ **3 người** — Scrum quá phức tạp (cần Scrum Master, Daily Standup, Sprint Review...) |
| Tài liệu | Đầy đủ mỗi giai đoạn | Ít tài liệu | Báo cáo đồ án **yêu cầu tài liệu đầy đủ** ở mỗi giai đoạn |
| Kiểm soát | Rõ ràng, tuần tự | Linh hoạt | PM dễ kiểm soát tiến độ khi **mỗi giai đoạn có đầu ra rõ ràng** |
| Thời gian | Dễ lập kế hoạch tổng thể | Khó dự đoán tổng thể | 15 tuần cố định → cần **lịch biểu tổng thể ngay từ đầu** |

**Các giai đoạn Waterfall áp dụng:**

```
Tuần 1-2         Tuần 3-4           Tuần 4-12              Tuần 11-13         Tuần 13-15
┌──────────┐   ┌──────────┐   ┌────────────────────┐   ┌──────────────┐   ┌──────────────┐
│ Phân tích │──▶│ Thiết kế │──▶│    Phát triển       │──▶│  Kiểm thử    │──▶│ Triển khai   │
│ yêu cầu  │   │ hệ thống │   │ (HW, FW, BE, AI,   │   │ (đơn vị,     │   │ & Tài liệu   │
│           │   │          │   │  Web Dashboard)     │   │  tích hợp)   │   │ & Bảo vệ     │
└──────────┘   └──────────┘   └────────────────────┘   └──────────────┘   └──────────────┘
```

**Lý do cụ thể:**
1. **Yêu cầu xác định rõ từ đầu:** Hệ thống cảm biến, giao thức WebSocket, mô hình ARX/MPC — tất cả cần được thiết kế trước khi code.
2. **Nhóm 3 người, không cần Scrum:** Agile yêu cầu Daily Standup, Sprint Planning, Sprint Review — quá nặng nề cho 3 sinh viên song song với các môn học khác.
3. **Tài liệu đầy đủ:** Mỗi giai đoạn Waterfall tạo ra deliverable rõ ràng → thuận lợi cho viết báo cáo 10 chương.
4. **Sử dụng Trello** để theo dõi công việc trong từng giai đoạn (không phải Sprint Backlog), giúp minh bạch tiến độ.

---
