# CHƯƠNG 7: QUẢN LÝ RỦI RO DỰ ÁN

## 7.1 Tổng quan về quản lý rủi ro

Rủi ro (Risk) trong quản lý dự án là sự kiện hoặc điều kiện không chắc chắn mà nếu xảy ra sẽ có tác động tiêu cực đến mục tiêu dự án (phạm vi, thời gian, chi phí, chất lượng). Rủi ro khác với vấn đề (Issue): rủi ro chưa xảy ra — cần dự phòng; vấn đề đã xảy ra — cần giải quyết ngay.

Tính chất: Mọi dự án đều có rủi ro, rủi ro khó loại trừ triệt để — chỉ có thể dự đoán, kiểm soát và giảm thiểu.

Bảng 21. Quy trình quản lý rủi ro

| Bước | Nội dung | Mô tả |
|------|----------|-------|
| 1 | Nhận diện rủi ro | Brainstorming, SWOT, rà soát tài liệu → lập Risk Register |
| 2 | Khử bỏ rủi ro | Loại bỏ hoàn toàn nguyên nhân nếu có thể (đào tạo, thay công cụ) |
| 3 | Giảm bớt nguyên nhân | Xác định gốc rễ → thiết kế biện pháp phòng ngừa |
| 4 | Giữ trong tầm kiểm soát | Giám sát liên tục, giao người phụ trách, đo KPI |
| 5 | Giảm bớt hậu quả | Né tránh (Avoid), Giảm thiểu (Mitigate), Chuyển giao (Transfer), Chấp nhận (Accept) |

Đánh giá rủi ro sử dụng thang 1–10 cho Khả năng xuất hiện (P) và Mức độ tác động (I):

Điểm rủi ro (Risk Score) = P × I

Bảng 22. Thang điểm đánh giá rủi ro

| Ngưỡng điểm | Mức độ | Hành động |
|-------------|--------|-----------|
| 1–20 | Thấp | Chấp nhận, theo dõi |
| 21–40 | Vừa | Cần kế hoạch giảm thiểu |
| 41–70 | Cao | Cần hành động ngay |
| 71–100 | Rất cao | Ưu tiên xử lý khẩn cấp |

## 7.2 Bảng quản lý rủi ro dự án nhà kính thông minh

### 7.2.1 Bảng nhận diện rủi ro

Phân loại ngưỡng điểm rủi ro (thang 1–10 × 1–10 = max 100):

- 1–20: Thấp — chấp nhận, theo dõi
- 21–40: Vừa — cần kế hoạch giảm thiểu
- 41–70: Cao — cần hành động ngay
- 71–100: Rất cao — ưu tiên xử lý khẩn cấp

Bảng 23. Nhận diện thứ tự ưu tiên cho rủi ro

| ID | Rủi ro | Nhóm | P (1-10) | I (1-10) | Điểm | Thứ tự ưu tiên |
|----|--------|------|----------|----------|------|----------------|
| R01 | Thiếu kinh nghiệm AI/MPC | Kỹ thuật | 6 | 7 | 42 | 1 |
| R02 | Trễ tiến độ module AI | Dự án | 6 | 7 | 42 | 1 |
| R03 | MPC điều khiển không ổn định | Kỹ thuật | 5 | 7 | 35 | 3 |
| R04 | Mô hình ARX không đạt FIT | Kỹ thuật | 5 | 6 | 30 | 4 |
| R05 | Cảm biến hỏng/sai số lớn | Kỹ thuật | 4 | 5 | 20 | 5 |
| R06 | Mất kết nối WiFi/WebSocket | Kỹ thuật | 4 | 5 | 20 | 5 |
| R07 | Thay đổi yêu cầu giữa chừng | Nghiệp vụ | 3 | 6 | 18 | 7 |
| R08 | Thành viên nghỉ đột xuất | Dự án | 3 | 6 | 18 | 7 |
| R09 | Xung đột nội bộ nhóm | Dự án | 3 | 4 | 12 | 9 |
| R10 | Thiết bị chấp hành hỏng | Kỹ thuật | 3 | 4 | 12 | 9 |

### 7.2.2 Kế hoạch ứng phó: Phòng ngừa và Khắc phục

Bảng 24. Kế hoạch ứng phó rủi ro

| ID | Rủi ro | Phương pháp phòng ngừa | Phương pháp khắc phục | Phụ trách |
|----|--------|------------------------|----------------------|-----------|
| R01 | Thiếu kinh nghiệm AI/MPC | Nghiên cứu lý thuyết 2 tuần trước khi code; tham khảo MathWorks, APMonitor; xây prototype nhỏ | Tham vấn giảng viên; sử dụng thư viện có sẵn thay vì tự viết từ đầu | A, C |
| R02 | Trễ tiến độ AI | Triển khai AI sớm theo kế hoạch; dùng dữ liệu mô phỏng; review tiến độ hàng tuần | Tăng giờ làm của C; A hỗ trợ dữ liệu mô phỏng ARX; B hỗ trợ kiểm thử tích hợp | A, B, C |
| R03 | MPC không ổn định | Tune tham số trên dữ liệu mô phỏng trước; thêm ràng buộc safety constraints | Chuyển sang điều khiển rule-based đơn giản; giới hạn biên độ actuator | C |
| R04 | ARX không đạt FIT | Thử nhiều cấu trúc (na, nb, nk); dùng Ridge regularization; đánh giá validation | Tăng dữ liệu huấn luyện; chuyển sang mô hình đơn giản hơn (AR) | A |
| R05 | Cảm biến hỏng | Mua 2 bộ cảm biến dự phòng; dùng Kalman lọc nhiễu; lấy trung bình nhiều lần đo | Thay cảm biến dự phòng ngay; hiệu chuẩn lại sau khi thay | B |
| R06 | Mất kết nối WiFi | Auto-reconnect trong firmware; buffer dữ liệu cục bộ khi mất mạng | Restart ESP32; kiểm tra router; chuyển sang hotspot điện thoại | B |
| R07 | Thay đổi yêu cầu | Ghi nhận thay đổi vào nhật ký; đánh giá tác động trước khi chấp nhận | Điều chỉnh WBS; đàm phán lại thời gian với giảng viên | A |
| R08 | Thành viên nghỉ | Tài liệu code rõ ràng; cross-training kiến thức giữa các thành viên | Phân bổ lại công việc cho 2 người còn lại; ưu tiên module quan trọng | A |
| R09 | Xung đột nhóm | Phân công RACI rõ ràng; họp định kỳ; PM giải quyết bất đồng kịp thời | Tổ chức họp khẩn; làm rõ lại vai trò và trách nhiệm | A |
| R10 | Thiết bị hỏng | Dùng relay bảo vệ; kiểm tra mạch kỹ trước khi cấp nguồn; mua dự phòng | Thay thiết bị dự phòng; kiểm tra lại toàn bộ mạch trước khi cấp nguồn lại | B |

### 7.2.3 Kinh phí dự phòng

Bảng 25. Kế hoạch kinh phí dự phòng

| STT | Hạng mục dự phòng | Mục đích | Chi phí (VNĐ) |
|-----|-------------------|----------|---------------|
| 1 | Cảm biến dự phòng (DHT22 + Soil × 2) | Thay thế khi hỏng | 60.000 |
| 2 | Relay dự phòng | Thay thế khi cháy | 30.000 |
| 3 | Bơm + quạt dự phòng | Thay thế khi hỏng | 55.000 |
| 4 | Dây nối + breadboard phụ | Đấu lại khi cần | 20.000 |
| 5 | Servo SG90 dự phòng | Thay thế cho Solar Tracking | 35.000 |
| 6 | Pin 18650 dự phòng (×1) | Thay thế khi chai pin | 55.000 |
| | Tổng kinh phí dự phòng | | 255.000 |

Tỷ lệ dự phòng: 255.000 / 1.200.000 ≈ 21% tổng chi phí — cao hơn mức thông thường (10–15%) do đặc thù phần cứng prototype dễ hỏng.

## 7.3 Tổng kết quản lý rủi ro

### 7.3.1 Thống kê kết quả

Bảng 26. Thống kê kết quả sau quản lý rủi ro

| Hạng mục | Giá trị |
|----------|---------|
| Tổng rủi ro nhận diện | 10 |
| Rủi ro mức Cao | 2 (R01, R02) |
| Rủi ro mức Vừa | 2 (R03, R04) |
| Rủi ro mức Thấp | 6 |
| Rủi ro thực sự xảy ra | 2 (R02: trễ AI, R05: cảm biến hỏng) |
| Rủi ro xử lý thành công | 2/2 (100%) |
| Kinh phí dự phòng đã sử dụng | 171.000/255.000 VNĐ (67%) |

### 7.3.2 Bài học rút ra từ quản lý rủi ro

Bảng 27. Bài học rút ra từ quản lý rủi ro

| STT | Bài học | Chi tiết |
|-----|---------|----------|
| 1 | Nhận diện sớm = xử lý rẻ | R01 (thiếu kinh nghiệm AI) được nhận diện từ tuần 1 → phòng ngừa bằng nghiên cứu 2 tuần → không phát sinh chi phí thêm |
| 2 | Dự phòng thiết bị là bắt buộc | R05 xảy ra thực tế (DHT22 hỏng) → thay nhanh nhờ mua sẵn dự phòng → không ảnh hưởng tiến độ |
| 3 | AI/ML cần buffer thời gian lớn | R02 xảy ra (trễ 1 tuần) dù đã phòng ngừa → nên dự trù +30% thời gian cho module AI trong các dự án sau |
| 4 | Cross-training giảm rủi ro nhân sự | A hỗ trợ C bằng dữ liệu mô phỏng ARX, B hỗ trợ kiểm thử tích hợp để C tập trung xử lý Kalman/MPC |

### 7.3.3 Thành quả của quản lý rủi ro hiệu quả

- Dự án hoàn thành đúng hạn (15 tuần) dù có 2 rủi ro xảy ra.
- Chi phí kiểm soát được — chỉ sử dụng 67% kinh phí dự phòng.
- Chất lượng đạt mục tiêu — FIT 85,85% > 80% yêu cầu.
- Không có rủi ro bất ngờ — tất cả sự cố xảy ra đều đã nằm trong danh sách nhận diện.
