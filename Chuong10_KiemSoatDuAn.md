# CHƯƠNG 10: KIỂM SOÁT DỰ ÁN

---

## 10.1 Thu thập và đánh giá hiện trạng

### 10.1.1 Mục đích thu thập hiện trạng

Thu thập hiện trạng là quá trình **đo lường mức độ tiến triển** của dự án so với kế hoạch ban đầu, nhằm:
- Xác định công việc nào đã hoàn thành, đang thực hiện, chưa bắt đầu.
- Phát hiện sớm các sai lệch về thời gian, chi phí, chất lượng.
- Cung cấp cơ sở để ra quyết định điều chỉnh kịp thời.

### 10.1.2 Time sheet nhiệm vụ & Time sheet cá nhân

**a) Time sheet nhiệm vụ (Task Time Sheet)**

| Mã WBS | Công việc | KH bắt đầu | KH kết thúc | TT bắt đầu | TT kết thúc | % Hoàn thành | Ghi chú |
|:------:|-----------|:----------:|:----------:|:----------:|:----------:|:------------:|---------|
| 1.0 | Phân tích yêu cầu | Tuần 1 | Tuần 2 | Tuần 1 | Tuần 2 | 100% | Đúng tiến độ |
| 2.0 | Thiết kế hệ thống | Tuần 3 | Tuần 4 | Tuần 3 | Tuần 5 | 100% | Trễ 1 tuần (thiết kế AI phức tạp) |
| 3.0 | Phát triển phần cứng | Tuần 4 | Tuần 6 | Tuần 4 | Tuần 6 | 100% | Đúng tiến độ |
| 4.0 | Phát triển Firmware | Tuần 5 | Tuần 7 | Tuần 5 | Tuần 7 | 100% | Đúng tiến độ |
| 5.0 | Phát triển Backend | Tuần 5 | Tuần 9 | Tuần 5 | Tuần 9 | 100% | Đúng tiến độ |
| 6.0 | Phát triển AI | Tuần 5 | Tuần 11 | Tuần 5 | Tuần 12 | 100% | Trễ 1 tuần (MPC tuning) |
| 7.0 | Phát triển Web | Tuần 6 | Tuần 12 | Tuần 6 | Tuần 12 | 100% | Đúng tiến độ |
| 8.0 | Kiểm thử | Tuần 11 | Tuần 13 | Tuần 12 | Tuần 13 | 100% | Bắt đầu trễ do AI trễ |
| 9.0 | Triển khai & Tài liệu | Tuần 13 | Tuần 15 | Tuần 13 | Tuần 15 | 100% | Đúng tiến độ |

**b) Time sheet cá nhân**

| Tuần | Thành viên A (PM + AI) | Thành viên B (FW/HW) | Thành viên C (Web/BE) |
|:----:|:-----:|:-----:|:-----:|
| 1–2 | 20h (phân tích, khảo sát) | 15h (khảo sát HW) | 15h (khảo sát tech stack) |
| 3–4 | 18h (thiết kế kiến trúc, AI pipeline) | 16h (thiết kế mạch) | 16h (thiết kế DB, UI) |
| 5–6 | 22h (nghiên cứu ARX, bắt đầu code) | 20h (lắp ráp HW, code FW) | 18h (setup Django, API) |
| 7–8 | 25h (huấn luyện ARX, Kalman) | 18h (hoàn thiện FW) | 20h (WebSocket, tiếp tục API) |
| 9–10 | 28h (MPC, tích hợp AI) | 12h (fix bug FW) | 22h (phát triển Web Dashboard) |
| 11–12 | 25h (MPC tuning, kiểm thử AI) | 15h (kiểm thử HW, tích hợp) | 20h (hoàn thiện Web, kiểm thử) |
| 13–14 | 20h (kiểm thử tích hợp, báo cáo) | 15h (kiểm thử, báo cáo) | 18h (kiểm thử, báo cáo, phụ lục) |
| 15 | 10h (slide, bảo vệ) | 8h (demo, bảo vệ) | 8h (demo, bảo vệ) |
| **Tổng** | **168h** | **119h** | **137h** |

### 10.1.3 Phân tích sai biệt

**a) Sai biệt lịch biểu (Schedule Variance — SV)**

| Giai đoạn | KH (tuần) | TT (tuần) | SV | Đánh giá |
|-----------|:---------:|:---------:|:--:|:--------:|
| Phân tích yêu cầu | 2 | 2 | 0 | ✅ Đúng |
| Thiết kế | 2 | 3 | -1 | ⚠️ Trễ |
| Phát triển HW + FW | 3 | 3 | 0 | ✅ Đúng |
| Phát triển Backend | 5 | 5 | 0 | ✅ Đúng |
| Phát triển AI | 7 | 8 | -1 | ⚠️ Trễ |
| Phát triển Web | 7 | 7 | 0 | ✅ Đúng |
| Kiểm thử | 3 | 2 | +1 | ✅ Nhanh hơn |
| Tổng dự án | 15 | 15 | 0 | ✅ Đúng tổng thể |

**Nhận xét:** Dự án có 2 giai đoạn trễ (thiết kế và AI), nhưng bù lại bằng việc kiểm thử nhanh hơn. Tổng thời gian dự án vẫn đúng 15 tuần.

**b) Sai biệt chi phí (Cost Variance — CV)**

| Hạng mục | KH (VNĐ) | TT (VNĐ) | CV | Ghi chú |
|----------|:--------:|:--------:|:--:|---------|
| Linh kiện chính | 575.000 | 575.000 | 0 | Đúng dự toán |
| Linh kiện phụ | 50.000 | 65.000 | -15.000 | Mua thêm dây nối |
| Dự phòng sử dụng | 0 | 60.000 | -60.000 | Thay 1 cảm biến DHT22 hỏng |
| **Tổng** | **625.000** | **700.000** | **-75.000** | Vượt 12% |

### 10.1.4 Quản lý giá trị thu được (EVM — Earned Value Management)

EVM là phương pháp đo lường hiệu suất dự án bằng cách kết hợp phạm vi, thời gian và chi phí.

**Các chỉ số cơ bản:**

| Chỉ số | Tên đầy đủ | Ý nghĩa |
|:------:|------------|---------|
| **PV** | Planned Value | Giá trị công việc theo kế hoạch tại thời điểm đánh giá |
| **EV** | Earned Value | Giá trị công việc **đã hoàn thành** thực tế |
| **AC** | Actual Cost | Chi phí **thực tế** đã bỏ ra |

**Các chỉ số phân tích:**

| Chỉ số | Công thức | Ý nghĩa | Đánh giá |
|:------:|:---------:|---------|----------|
| **SV** | EV − PV | Sai biệt tiến độ | SV > 0: nhanh hơn KH; SV < 0: chậm hơn KH |
| **CV** | EV − AC | Sai biệt chi phí | CV > 0: tiết kiệm; CV < 0: vượt chi phí |
| **SPI** | EV / PV | Chỉ số hiệu suất tiến độ | SPI > 1: nhanh; SPI < 1: chậm |
| **CPI** | EV / AC | Chỉ số hiệu suất chi phí | CPI > 1: tiết kiệm; CPI < 1: lãng phí |

**Áp dụng EVM cho dự án Smart Greenhouse (tại tuần 10):**

Giả sử tổng ngân sách BAC = 625.000 VNĐ, tổng giờ công KH = 675h.

| Chỉ số | Giá trị | Diễn giải |
|:------:|:-------:|-----------|
| PV | ~70% × 675h = 472h | Theo KH, tuần 10 phải hoàn thành 70% |
| EV | ~65% × 675h = 439h | Thực tế hoàn thành 65% (AI đang trễ) |
| AC | 460h | Công sức thực tế đã bỏ ra |
| SV | 439 − 472 = **−33h** | ⚠️ Chậm tiến độ |
| CV | 439 − 460 = **−21h** | ⚠️ Vượt chi phí nhân công |
| SPI | 439/472 = **0.93** | Chậm 7% so với KH |
| CPI | 439/460 = **0.95** | Chi phí vượt 5% |

**Nhận xét:** SPI = 0.93 cho thấy dự án chậm 7% tại tuần 10, chủ yếu do module MPC. Sau can thiệp (tăng giờ A, B hỗ trợ), dự án đã hoàn thành đúng hạn tuần 15.

---

## 10.2 Họp

### 10.2.1 Họp định kỳ

- **Tần suất:** 1 lần/tuần (thứ 7 hoặc Chủ nhật).
- **Thời lượng:** 30–60 phút.
- **Hình thức:** Trực tiếp hoặc online (Discord/Zalo).
- **Nội dung:**
  - Báo cáo tiến độ tuần qua (mỗi người 5 phút).
  - Thảo luận vấn đề gặp phải.
  - Lập kế hoạch tuần tới.
  - Review rủi ro (nếu cần).

### 10.2.2 Họp đột xuất

Họp đột xuất được triệu tập khi:
- Phát hiện bug nghiêm trọng ảnh hưởng nhiều module.
- Cần thay đổi thiết kế/yêu cầu gấp.
- Chuẩn bị demo cho giảng viên.

### 10.2.3 Nguyên tắc họp hiệu quả

1. **Thông báo trước ≥ 1 ngày** (trừ đột xuất).
2. **Có chương trình họp** (agenda) rõ ràng.
3. **Không quá 60 phút** cho họp định kỳ.
4. **Ghi biên bản** mọi quyết định.
5. **Phân công rõ** ai làm gì sau họp.

### 10.2.4 Biên bản họp nhóm (minh họa)

**Biên bản họp #1:**

| Mục | Nội dung |
|-----|----------|
| Ngày | Tuần 3, Thứ 7 |
| Tham dự | A, B, C |
| Nội dung | Phân công công việc chi tiết cho giai đoạn thiết kế |
| Kết quả | B: thiết kế mạch (tuần 3–4); C: thiết kế DB + UI (tuần 3–4); A: thiết kế kiến trúc + AI pipeline |
| Vấn đề | Chưa rõ cấu trúc ARX nào phù hợp → A nghiên cứu thêm |
| Hành động | A: Đọc tài liệu MathWorks về ARX trước tuần 4 |

**Biên bản họp #2:**

| Mục | Nội dung |
|-----|----------|
| Ngày | Tuần 8, Thứ 7 |
| Tham dự | A, B, C |
| Nội dung | Review tiến độ giữa kỳ |
| Kết quả | HW + FW: hoàn thành 100%; Backend: 80%; AI (ARX): đang huấn luyện, FIT = 85,85%; Web: 60% |
| Vấn đề | Kalman Filter chưa bắt đầu → có nguy cơ trễ |
| Hành động | A: Ưu tiên Kalman tuần 9; C: Đẩy nhanh Web tuần 9–10 |

**Biên bản họp #3:**

| Mục | Nội dung |
|-----|----------|
| Ngày | Tuần 12, Thứ 7 |
| Tham dự | A, B, C |
| Nội dung | Chuẩn bị kiểm thử tích hợp |
| Kết quả | Tất cả module hoàn thành; MPC đã tune xong; Web đã tích hợp biểu đồ dự báo |
| Vấn đề | Cảm biến DHT22 hỏng 1 chiếc → thay dự phòng |
| Hành động | B: Thay cảm biến; Cả nhóm: kiểm thử end-to-end tuần 13 |

---

## 10.3 Điều chỉnh

### 10.3.1 Khi dự án không đúng lịch biểu

Trong dự án Smart Greenhouse, giai đoạn **Phát triển AI bị trễ 1 tuần** (MPC tuning phức tạp hơn dự kiến).

**Biện pháp đã áp dụng:**
- Tăng giờ làm việc của thành viên A (từ 20h → 28h/tuần trong tuần 9–10).
- Sử dụng dữ liệu mô phỏng để huấn luyện song song, không chờ dữ liệu thực.
- B hỗ trợ kiểm thử phần tích hợp ESP32 ↔ Backend trong khi A tập trung MPC.

### 10.3.2 Khi chi phí có nguy cơ tăng

Chi phí vượt 75.000 VNĐ (12%) do thay cảm biến hỏng và mua thêm dây nối.

**Biện pháp:**
- Sử dụng kinh phí dự phòng đã dự trù (165.000 VNĐ).
- Tổng chi phí thực tế (700.000 VNĐ) vẫn nằm trong ngân sách tổng (625.000 + 165.000 = 790.000 VNĐ).

### 10.3.3 Khi chất lượng có nguy cơ giảm

**Tình huống:** FIT free-run của ARX chỉ đạt 66,42% (thấp hơn FIT 1-step 85,85%), sai số tích lũy khi dự báo dài hạn.

**Biện pháp:**
- Tích hợp Kalman Filter để lọc nhiễu trước khi đưa vào MPC → tín hiệu ổn định hơn.
- MPC sử dụng dự báo ngắn hạn (receding horizon) thay vì free-run → tận dụng FIT 1-step cao.
- Thêm ràng buộc an toàn (safety constraints) trong MPC để tránh overshoot/undershoot.

---

## 10.4 Kiểm soát thay đổi

### 10.4.1 Nguồn gốc thay đổi

| Nguồn | Ví dụ |
|-------|-------|
| Giảng viên (khách hàng) | Yêu cầu thêm chức năng cảnh báo ngưỡng |
| Nhóm phát triển | Phát hiện cần thêm Adaptive Kalman thay Kalman cơ bản |
| Môi trường kỹ thuật | Cảm biến hỏng → thay đổi cách đọc dữ liệu |

### 10.4.2 Phân loại thay đổi

| Loại | Mô tả | Ví dụ |
|:----:|-------|-------|
| Quan trọng | Ảnh hưởng đến kiến trúc/tiến độ tổng thể | Thêm MPC vào hệ thống |
| Ít quan trọng | Thay đổi nhỏ, không ảnh hưởng tiến độ | Đổi màu giao diện |
| Bổ sung | Tính năng mới ngoài phạm vi ban đầu | Thêm trang dự báo xu hướng |

### 10.4.3 Thủ tục kiểm soát thay đổi

```
Ghi nhận yêu cầu → Phân tích tác động → Phê duyệt (PM + nhóm) → Thực hiện → Kiểm tra
```

1. **Ghi nhận:** Người đề xuất mô tả thay đổi cần thiết.
2. **Phân tích:** PM đánh giá tác động đến thời gian, chi phí, chất lượng.
3. **Phê duyệt:** PM quyết định (thay đổi nhỏ) hoặc cả nhóm biểu quyết (thay đổi lớn).
4. **Thực hiện:** Cập nhật WBS, phân công, thực hiện.
5. **Kiểm tra:** Xác nhận thay đổi đã được thực hiện đúng.

### 10.4.4 Nhật ký kiểm soát thay đổi

| STT | Ngày | Mô tả thay đổi | Nguồn | Loại | Tác động | Quyết định |
|:---:|:----:|-----------------|:-----:|:----:|----------|:----------:|
| 1 | Tuần 3 | Thêm Adaptive Kalman Filter (IAE) thay Kalman cơ bản | Nhóm dev | Quan trọng | +1 tuần phát triển AI | ✅ Chấp nhận |
| 2 | Tuần 5 | Giảng viên yêu cầu thêm chức năng cảnh báo ngưỡng trên Web | Giảng viên | Bổ sung | +3 ngày phát triển Web | ✅ Chấp nhận |
| 3 | Tuần 7 | Đổi giao thức HTTP polling sang WebSocket | Nhóm dev | Quan trọng | Thiết kế lại truyền thông, nhưng cải thiện realtime | ✅ Chấp nhận |
| 4 | Tuần 9 | Thêm trang dự báo xu hướng trên Dashboard | Nhóm dev | Bổ sung | +2 ngày phát triển Web | ✅ Chấp nhận |
| 5 | Tuần 11 | Thay cảm biến DHT22 hỏng bằng cảm biến dự phòng | Kỹ thuật | Ít quan trọng | +60.000 VNĐ chi phí | ✅ Chấp nhận |

---

## 10.5 Lập kế hoạch lại (nếu có)

### 10.5.1 Khi nào cần lập kế hoạch lại

Trong dự án, **không cần lập kế hoạch lại toàn bộ**. Tuy nhiên, có 2 điều chỉnh cục bộ:

1. **Tuần 5:** Khi quyết định thêm Adaptive Kalman → kéo dài giai đoạn AI thêm 1 tuần, bù bằng rút ngắn kiểm thử.
2. **Tuần 7:** Khi chuyển từ HTTP polling sang WebSocket → B cần refactor firmware 3 ngày, nhưng không ảnh hưởng tổng tiến độ vì B có thời gian dư.

### 10.5.2 Quy trình tái cấu trúc kế hoạch

1. Xác định phạm vi thay đổi.
2. Đánh giá tác động lên đường găng (Critical Path).
3. Điều chỉnh WBS, ước lượng thời gian, lịch biểu.
4. Thông báo cho tất cả thành viên.
5. Cập nhật Trello Board.

---

## 10.6 Kết thúc dự án

### 10.6.1 Các lý do kết thúc

Dự án kết thúc vì **hoàn thành mục tiêu đề ra** trong thời gian quy định (15 tuần). Tất cả deliverables đã được chuyển giao:
- ✅ Hệ thống phần cứng hoạt động.
- ✅ Firmware ESP32 ổn định.
- ✅ Backend + AI tích hợp thành công.
- ✅ Web Dashboard đầy đủ 6 màn hình.
- ✅ Báo cáo PBL + QLDA hoàn thành.

### 10.6.2 Thống kê số liệu

| Hạng mục | Giá trị |
|----------|:-------:|
| Tổng thời gian | 15 tuần |
| Tổng giờ công | 424 giờ (A: 168h, B: 119h, C: 137h) |
| Tổng chi phí | 700.000 VNĐ |
| Số work packages | 45 |
| Số milestone | 9 |
| Số thay đổi | 5 |
| Số rủi ro xảy ra | 2 (R02: cảm biến hỏng, R03: trễ AI) |

### 10.6.3 So sánh kế hoạch vs thực tế

| Tiêu chí | Kế hoạch | Thực tế | Sai lệch |
|----------|:--------:|:------:|:--------:|
| Thời gian tổng | 15 tuần | 15 tuần | 0 |
| Chi phí | 625.000 VNĐ | 700.000 VNĐ | +12% |
| FIT 1-step ARX | ≥ 80% | 85,85% | +5,85% ✅ |
| FIT free-run | ≥ 60% | 66,42% | +6,42% ✅ |
| RMSE free-run | ≤ 1.5 | 0,978 | Tốt hơn ✅ |
| MPC vùng mục tiêu | 55–65% | Đạt | ✅ |
| Số màn hình Web | ≥ 6 | 6 | ✅ |
| Giai đoạn trễ | 0 | 2 (thiết kế, AI) | ⚠️ |

### 10.6.4 Bài học kinh nghiệm (Lessons Learned)

Rút kinh nghiệm theo **4 bước** theo phương pháp luận quản lý dự án:

**Bước 1 — Ghi nhận thành công:**
- ✅ Mô hình Waterfall phù hợp: yêu cầu ổn định, tài liệu đầy đủ, dễ kiểm soát tiến độ cho nhóm 3 người.
- ✅ Phân công RACI ngay từ tuần 1 → không chồng chéo suốt 15 tuần.
- ✅ Dùng dữ liệu mô phỏng huấn luyện AI song song → tiết kiệm 2+ tuần.
- ✅ Mua thiết bị dự phòng → xử lý sự cố cảm biến hỏng trong 30 phút.

**Bước 2 — Xác định sai sót & vấn đề:**
- ⚠️ Ước lượng thời gian MPC quá lạc quan → trễ 1 tuần.
- ⚠️ Thiết kế AI pipeline muộn (tuần 5) → áp lực cuối dự án.
- ⚠️ Chưa có quy trình code review chính thức → phát hiện bug muộn.

**Bước 3 — Phân tích nguyên nhân:**
- MPC trễ do: (1) thiếu kinh nghiệm → tune tham số mất thời gian, (2) dữ liệu thực khác mô phỏng → cần calibrate lại.
- Thiếu code review do nhóm nhỏ (3 người), mỗi người phụ trách module riêng.

**Bước 4 — Đề xuất cải thiện cho dự án tương lai:**

| STT | Đề xuất | Lý do |
|:---:|---------|-------|
| 1 | Dự trù +30% thời gian cho module AI/ML | MPC tuning phức tạp hơn dự kiến |
| 2 | Bắt đầu nghiên cứu AI từ tuần 1 (không chờ tuần 5) | Giảm áp lực cuối dự án |
| 3 | Áp dụng code review bắt buộc qua Pull Request | Phát hiện bug sớm, chia sẻ kiến thức |
| 4 | WebSocket nên chọn từ đầu thay vì refactor giữa chừng | Tiết kiệm 3 ngày refactor firmware |
| 5 | Tổ chức buổi sharing kiến thức nội bộ 2 tuần/lần | Giảm rủi ro phụ thuộc 1 người |

### 10.6.5 Lưu trữ hồ sơ dự án

Toàn bộ hồ sơ dự án được lưu trữ tại:
- **GitHub Repository:** Mã nguồn (firmware, backend, web, AI).
- **Google Drive/OneDrive:** Báo cáo, slide, biên bản họp, nhật ký thay đổi.
- **Trello Board:** Lịch sử quản lý công việc.

---

## 10.7 Kỹ năng mềm trong quản lý dự án

### 10.7.1 Giao tiếp

- **Giao tiếp nội bộ:** Nhóm sử dụng Zalo/Discord cho trao đổi hàng ngày, họp online khi không gặp trực tiếp.
- **Giao tiếp với giảng viên:** Báo cáo tiến độ định kỳ, gửi email khi cần hỗ trợ.
- **Nguyên tắc:** Thông tin rõ ràng, kịp thời, không giấu vấn đề.

### 10.7.2 Tổ chức

- PM (thành viên A) duy trì **Trello Board** cập nhật, đảm bảo mọi công việc có người phụ trách và deadline.
- **WBS + RACI** giúp phân công rõ ràng, tránh chồng chéo.
- **Git workflow** (branching, pull request) giúp quản lý mã nguồn có tổ chức.

### 10.7.3 Xử lý tình huống

| Tình huống | Cách xử lý |
|------------|------------|
| Cảm biến DHT22 hỏng đột ngột | Thay nhanh bằng cảm biến dự phòng, không ảnh hưởng tiến độ |
| MPC tuning mất nhiều thời gian hơn dự kiến | A tăng giờ làm, B hỗ trợ kiểm thử tích hợp |
| Thành viên không hiểu module của người khác | Tổ chức buổi sharing kiến thức nội bộ |

---

## 10.8 Các lỗi thường gặp trong kiểm soát dự án

### 10.8.1 Phân loại lỗi theo quy trình kiểm soát (Control Flow)

| Giai đoạn | Mục tiêu | Lỗi thường gặp | Hậu quả |
|-----------|----------|-----------------|---------|
| **Monitoring** (Giám sát) | Thu thập và theo dõi dữ liệu | Dữ liệu sai/thiếu; không theo dõi thường xuyên; đánh giá cảm tính | Không biết tình trạng thực tế |
| **Measurement** (Đo lường) | So sánh KH và thực tế | Không dùng EVM; không tính CPI, SPI | Không đánh giá được hiệu suất |
| **Analysis** (Phân tích) | Phân tích sai lệch | Không phân tích CV, SV; không tìm nguyên nhân gốc | Không hiểu vấn đề; không thấy rủi ro tương lai |
| **Action** (Điều chỉnh) | Đưa ra giải pháp | Không xử lý khi có sai lệch; xử lý sai hướng | Dự án lệch ngày càng lớn |

### 10.8.2 Phân loại lỗi theo chuẩn PMBOK

| Nhóm kiểm soát | Lỗi điển hình | Hậu quả |
|:---------------:|---------------|---------|
| Scope (Phạm vi) | Scope creep (phình phạm vi) | Trễ tiến độ, vượt chi phí |
| Schedule (Tiến độ) | Theo dõi tiến độ sai | Delay dây chuyền |
| Cost (Chi phí) | Không theo dõi chi phí | Vỡ ngân sách |
| Quality (Chất lượng) | Không kiểm tra chất lượng | Khách hàng không hài lòng |
| Risk (Rủi ro) | Không theo dõi rủi ro | Bị động khi xảy ra sự cố |
| Change (Thay đổi) | Không có quy trình change | Dự án mất kiểm soát |
| Communication (Giao tiếp) | Báo cáo không minh bạch | Quyết định sai |

---

## 10.9 Best Practices trong kiểm soát dự án

| Nhóm | Best Practice |
|:----:|---------------|
| **Giám sát & Đo lường** | Duy trì nhịp độ giám sát thường xuyên; Báo cáo định kỳ; Dashboard trực quan; Áp dụng EVM; Đo outcome, không chỉ output |
| **Quy trình & Kiểm soát** | Chuẩn hóa mẫu báo cáo; Ghi nhận và quản lý thay đổi; Theo dõi rủi ro; Kiểm soát chất lượng liên tục |
| **Giao tiếp & Nhân sự** | Đào tạo kỹ năng cứng + mềm; Giao tiếp có mục tiêu rõ ràng; Phân công trách nhiệm cụ thể |
| **Lập KH & Quản trị** | Thiết lập kế hoạch dự phòng; Sử dụng công cụ QLDA phù hợp; Rút kinh nghiệm và cải tiến sau dự án |

> **Thành công = Kiểm soát tốt + Phản ứng nhanh + Cải tiến liên tục**

### 10.9.1 Công cụ kiểm soát dự án phổ biến

| Công cụ | Mục đích | Nhóm có sử dụng? |
|---------|----------|:-----------------:|
| **Trello** | Quản lý backlog, theo dõi task | ✅ Có — công cụ chính |
| **Excel/Google Sheets** | Time sheet, bảng rủi ro, EVM | ✅ Có — hỗ trợ |
| **GitHub** | Quản lý mã nguồn, issue tracking | ✅ Có — version control |
| **Zalo/Discord** | Giao tiếp nhóm, họp online | ✅ Có — giao tiếp |
| MS Project | Lập lịch biểu Gantt chuyên nghiệp | ❌ Không (dùng Excel thay) |
| Jira | Issue tracking phức tạp | ❌ Không (Trello đủ cho nhóm nhỏ) |
| Monday.com | Dashboard quản lý dự án | ❌ Không |
| Primavera P6 | Dự án xây dựng lớn | ❌ Không phù hợp |

**Lý do chọn Trello + Excel + GitHub:** Nhóm 3 người, dự án 15 tuần → ưu tiên công cụ miễn phí, dễ sử dụng, đủ chức năng. Không cần công cụ enterprise phức tạp.

---

## 10.10 Kiểm soát theo mô hình Waterfall

Dự án Smart Greenhouse áp dụng mô hình **Waterfall tuần tự** với 5 giai đoạn rõ ràng. Việc kiểm soát được thực hiện tại **điểm chuyển giao giữa các giai đoạn** (Phase Gate Review):

| Giai đoạn | Thời gian | Đầu ra (Deliverable) | Điểm kiểm soát |
|-----------|:--------:|----------------------|------------------|
| Phân tích yêu cầu | Tuần 1–2 | Tài liệu yêu cầu, SOW, WBS | **Gate 1:** Giảng viên duyệt phạm vi |
| Thiết kế | Tuần 3–4 | Kiến trúc, sơ đồ mạch, DB schema | **Gate 2:** Review thiết kế nhóm |
| Phát triển | Tuần 4–12 | HW, FW, Backend, AI, Web | **Gate 3:** Demo từng module |
| Kiểm thử | Tuần 11–13 | Test report, bug fix | **Gate 4:** Hệ thống chạy end-to-end |
| Triển khai | Tuần 13–15 | Báo cáo, slide, demo | **Gate 5:** Bảo vệ đồ án |

**Ưu điểm của Waterfall cho dự án này:**
- Mỗi giai đoạn có **đầu ra rõ ràng** → dễ viết báo cáo.
- PM kiểm soát bằng **Time sheet + EVM** tại từng mốc Gate.
- **Không cần Sprint/Daily Standup** — họp 1 lần/tuần là đủ cho nhóm 3 người.
- Trường hợp cần quay lại giai đoạn trước (như tuần 7 chuyển sang WebSocket): ghi nhận vào nhật ký thay đổi, đánh giá tác động, PM phê duyệt.

---
