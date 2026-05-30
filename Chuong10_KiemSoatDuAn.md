# CHƯƠNG 10: KIỂM SOÁT DỰ ÁN

---

## 10.1 Tổng quan về kiểm soát dự án

Kiểm soát dự án là quá trình **theo dõi tình hình thực tế, so sánh với kế hoạch, phát hiện sai biệt** và có biện pháp điều chỉnh phù hợp để dự án đi đúng hướng. Kiểm soát giúp phát hiện dấu hiệu từ sớm và can thiệp kịp thời, tránh tình trạng sai biệt nhỏ tích tụ thành chậm tiến độ, vượt chi phí, giảm chất lượng.

**Quy trình kiểm soát gồm 5 bước:**

| Bước | Nội dung | Mô tả |
|:----:|----------|-------|
| 1 | **Giám sát** | Thu thập thông tin về tiến độ, chi phí, chất lượng, phạm vi |
| 2 | **Phân tích vấn đề** | So sánh KH vs thực tế, tính SV, CV, SPI, CPI |
| 3 | **Kiểm soát thay đổi** | Ghi nhận → phân tích tác động → phê duyệt |
| 4 | **Thực hiện điều chỉnh** | Sửa lịch biểu, bổ sung nhân lực, cắt giảm phạm vi |
| 5 | **Kết thúc dự án** | Nghiệm thu, thống kê, rút kinh nghiệm |

---

## 10.2 Thu thập và đánh giá hiện trạng

### 10.2.1 Mục đích thu thập hiện trạng

Thu thập hiện trạng là quá trình **đo lường mức độ tiến triển** của dự án so với kế hoạch ban đầu, nhằm:

- Xác định công việc nào đã hoàn thành, đang thực hiện, chưa bắt đầu.
- Phát hiện sớm các sai lệch về thời gian, chi phí, chất lượng.
- Cung cấp cơ sở để ra quyết định điều chỉnh kịp thời.

### 10.2.2 Time sheet nhiệm vụ & Time sheet cá nhân

**a) Time sheet nhiệm vụ (Task Time Sheet)**

| Mã WBS | Công việc              | KH bắt đầu | KH kết thúc | TT bắt đầu | TT kết thúc | % Hoàn thành | Ghi chú                                |
| :-----: | ------------------------ | :-----------: | :-----------: | :-----------: | :-----------: | :------------: | --------------------------------------- |
|   1.0   | Phân tích yêu cầu    |    Tuần 1    |    Tuần 2    |    Tuần 1    |    Tuần 2    |      100%      | Đúng tiến độ                       |
|   2.0   | Thiết kế hệ thống    |    Tuần 3    |    Tuần 4    |    Tuần 3    |    Tuần 5    |      100%      | Trễ 1 tuần (thiết kế AI phức tạp) |
|   3.0   | Phát triển phần cứng |    Tuần 4    |    Tuần 6    |    Tuần 4    |    Tuần 6    |      100%      | Đúng tiến độ                       |
|   4.0   | Phát triển Firmware    |    Tuần 5    |    Tuần 7    |    Tuần 5    |    Tuần 7    |      100%      | Đúng tiến độ                       |
|   5.0   | Phát triển Backend     |    Tuần 5    |    Tuần 9    |    Tuần 5    |    Tuần 9    |      100%      | Đúng tiến độ                       |
|   6.0   | Phát triển AI          |    Tuần 5    |   Tuần 11   |    Tuần 5    |   Tuần 12   |      100%      | Trễ 1 tuần (MPC tuning)               |
|   7.0   | Phát triển Web         |    Tuần 6    |   Tuần 12   |    Tuần 6    |   Tuần 12   |      100%      | Đúng tiến độ                       |
|   8.0   | Kiểm thử               |   Tuần 11   |   Tuần 13   |   Tuần 12   |   Tuần 13   |      100%      | Bắt đầu trễ do AI trễ              |
|   9.0   | Triển khai & Tài liệu |   Tuần 13   |   Tuần 15   |   Tuần 13   |   Tuần 15   |      100%      | Đúng tiến độ                       |

**b) Time sheet cá nhân**

|      Tuần      |         Thành viên A (PM + AI)         |     Thành viên B (FW/HW)     |        Thành viên C (Web/BE)        |
| :-------------: | :---------------------------------------: | :-----------------------------: | :------------------------------------: |
|      1–2      |       20h (phân tích, khảo sát)       |       15h (khảo sát HW)       |      15h (khảo sát tech stack)      |
|      3–4      | 18h (thiết kế kiến trúc, AI pipeline) |     16h (thiết kế mạch)     |        16h (thiết kế DB, UI)        |
|      5–6      |  22h (nghiên cứu ARX, bắt đầu code)  |   20h (lắp ráp HW, code FW)   |        18h (setup Django, API)        |
|      7–8      |      25h (huấn luyện ARX, Kalman)      |      18h (hoàn thiện FW)      |    20h (WebSocket, tiếp tục API)    |
|      9–10      |         28h (MPC, tích hợp AI)         |        12h (fix bug FW)        |    22h (phát triển Web Dashboard)    |
|     11–12     |      25h (MPC tuning, kiểm thử AI)      | 15h (kiểm thử HW, tích hợp) |   20h (hoàn thiện Web, kiểm thử)   |
|     13–14     |  20h (kiểm thử tích hợp, báo cáo)  |   15h (kiểm thử, báo cáo)   | 18h (kiểm thử, báo cáo, phụ lục) |
|       15       |           10h (slide, bảo vệ)           |       8h (demo, bảo vệ)       |          8h (demo, bảo vệ)          |
| **Tổng** |              **168h**              |         **119h**         |             **137h**             |

### 10.2.3 Phân tích sai biệt

**a) Sai biệt lịch biểu (Schedule Variance — SV)**

| Giai đoạn           | KH (tuần) | TT (tuần) | SV |     Đánh giá     |
| --------------------- | :--------: | :--------: | :-: | :------------------: |
| Phân tích yêu cầu |     2     |     2     | 0 |      ✅ Đúng      |
| Thiết kế            |     2     |     3     | -1 |      ⚠️ Trễ      |
| Phát triển HW + FW  |     3     |     3     | 0 |      ✅ Đúng      |
| Phát triển Backend  |     5     |     5     | 0 |      ✅ Đúng      |
| Phát triển AI       |     7     |     8     | -1 |      ⚠️ Trễ      |
| Phát triển Web      |     7     |     7     | 0 |      ✅ Đúng      |
| Kiểm thử            |     3     |     2     | +1 |    ✅ Nhanh hơn    |
| Tổng dự án         |     15     |     15     | 0 | ✅ Đúng tổng thể |

**Nhận xét:** Dự án có 2 giai đoạn trễ (thiết kế và AI), nhưng bù lại bằng việc kiểm thử nhanh hơn. Tổng thời gian dự án vẫn đúng 15 tuần.

**b) Sai biệt chi phí (Cost Variance — CV)**

| Hạng mục           |     KH (VNĐ)     |     TT (VNĐ)     |        CV        | Ghi chú                      |
| -------------------- | :---------------: | :---------------: | :---------------: | ----------------------------- |
| Linh kiện chính    |      575.000      |      575.000      |         0         | Đúng dự toán              |
| Linh kiện phụ      |      50.000      |      65.000      |      -15.000      | Mua thêm dây nối           |
| Dự phòng sử dụng |         0         |      60.000      |      -60.000      | Thay 1 cảm biến DHT22 hỏng |
| **Tổng**      | **625.000** | **700.000** | **-75.000** | Vượt 12%                    |

### 10.2.4 Quản lý giá trị thu được (EVM — Earned Value Management)

EVM là phương pháp đo lường hiệu suất dự án bằng cách kết hợp phạm vi, thời gian và chi phí.

**Các chỉ số cơ bản:**

|   Chỉ số   | Tên đầy đủ | Ý nghĩa                                                           |
| :----------: | --------------- | ------------------------------------------------------------------- |
| **PV** | Planned Value   | Giá trị công việc theo kế hoạch tại thời điểm đánh giá |
| **EV** | Earned Value    | Giá trị công việc**đã hoàn thành** thực tế          |
| **AC** | Actual Cost     | Chi phí**thực tế** đã bỏ ra                             |

**Các chỉ số phân tích:**

|   Chỉ số   | Công thức | Ý nghĩa                       | Đánh giá                                  |
| :-----------: | :---------: | ------------------------------- | -------------------------------------------- |
| **SV** |  EV − PV  | Sai biệt tiến độ            | SV > 0: nhanh hơn KH; SV < 0: chậm hơn KH |
| **CV** |  EV − AC  | Sai biệt chi phí              | CV > 0: tiết kiệm; CV < 0: vượt chi phí |
| **SPI** |   EV / PV   | Chỉ số hiệu suất tiến độ | SPI > 1: nhanh; SPI < 1: chậm               |
| **CPI** |   EV / AC   | Chỉ số hiệu suất chi phí   | CPI > 1: tiết kiệm; CPI < 1: lãng phí    |

**Áp dụng EVM cho dự án Smart Greenhouse (tại tuần 10):**

Giả sử tổng ngân sách BAC = 625.000 VNĐ, tổng giờ công KH = 675h.

| Chỉ số |          Giá trị          | Diễn giải                                |
| :------: | :-------------------------: | ------------------------------------------ |
|    PV    |     ~70% × 675h = 472h     | Theo KH, tuần 10 phải hoàn thành 70%   |
|    EV    |     ~65% × 675h = 439h     | Thực tế hoàn thành 65% (AI đang trễ) |
|    AC    |            460h            | Công sức thực tế đã bỏ ra           |
|    SV    | 439 − 472 =**−33h** | ⚠️ Chậm tiến độ                      |
|    CV    | 439 − 460 =**−21h** | ⚠️ Vượt chi phí nhân công           |
|   SPI   |   439/472 =**0.93**   | Chậm 7% so với KH                        |
|   CPI   |   439/460 =**0.95**   | Chi phí vượt 5%                         |

**Nhận xét:** SPI = 0.93 cho thấy dự án chậm 7% tại tuần 10, chủ yếu do module MPC. Sau can thiệp (tăng giờ A, B hỗ trợ), dự án đã hoàn thành đúng hạn tuần 15.

**Ngưỡng cảnh báo:** Hầu hết tổ chức đặt ngưỡng khi CPI hoặc SPI nằm **ngoài khoảng 0.90–1.10**. Khi vượt ngưỡng → yêu cầu phân tích nguyên nhân và báo cáo giải trình.

### 10.2.5 Dự báo EVM (EAC, ETC, VAC)

|   Chỉ số   | Công thức | Ý nghĩa                                                                     |
| :-----------: | :---------: | ----------------------------------------------------------------------------- |
| **EAC** | BAC ÷ CPI | Tổng chi phí dự kiến khi hoàn thành (dựa trên hiệu suất hiện tại) |
| **ETC** |  EAC − AC  | Chi phí cần thêm để hoàn thành phần việc còn lại                   |
| **VAC** | BAC − EAC | Chênh lệch dự kiến giữa ngân sách và tổng chi phí cuối cùng       |

**Áp dụng cho dự án (tại tuần 10):**

| Chỉ số |                      Tính toán                      | Diễn giải                               |
| :------: | :---------------------------------------------------: | ----------------------------------------- |
|   EAC   |        625.000 ÷ 0.95 =**657.895 VNĐ**        | Dự kiến chi phí tổng khi hoàn thành |
|   ETC   | 657.895 − 700.000 × (10/15) =**191.228 VNĐ** | Chi phí cần thêm cho phần còn lại   |
|   VAC   |      625.000 − 657.895 =**−32.895 VNĐ**      | Dự kiến vượt ngân sách ~5.3%        |

**Các công thức EAC khác (tùy tình huống):**

- `EAC = AC + (BAC − EV)` → Giả định: công việc còn lại sẽ đúng ngân sách.
- `EAC = AC + [(BAC − EV) ÷ (CPI × SPI)]` → Giả định: cả chi phí và tiến độ đều ảnh hưởng.

---

## 10.3 Phát hiện và giải quyết vấn đề

### 10.3.1 Dấu hiệu báo động sớm

| # | Dấu hiệu                                        | Cảnh báo                                 |
| :-: | ------------------------------------------------- | ------------------------------------------ |
| 1 | Làm việc**không có kế hoạch**         | "Dự án nhỏ nên không cần kế hoạch" |
| 2 | **Yêu cầu không rõ ràng**              | "Người dùng không biết muốn gì"     |
| 3 | **Ước lượng đại khái**               | Bị áp đặt hoặc tùy tiện             |
| 4 | **Báo cáo ra muộn**                      | Không có gì mới so với kỳ trước    |
| 5 | Người chịu trách nhiệm**"mất tích"** | Không trả lời, né tránh               |

> **Nguyên tắc vàng:** Phòng bệnh hơn chữa bệnh. Phát hiện sớm và can thiệp ngay khi thấy dấu hiệu bất thường.

### 10.3.2 Quy trình xử lý vấn đề (5 bước)

```
1. Xác định vấn đề → 2. Phân tích nguyên nhân → 3. Đề xuất giải pháp → 4. Thực hiện xử lý → 5. Theo dõi & đánh giá
```

### 10.3.3 Root Cause Analysis: Phương pháp 5 Whys

Phương pháp tìm nguyên nhân gốc bằng cách hỏi "Tại sao?" nhiều lần:

**Ví dụ áp dụng cho dự án Smart Greenhouse:**

| Lần | Câu hỏi                    | Trả lời                                                                                                |
| :--: | ---------------------------- | -------------------------------------------------------------------------------------------------------- |
|  1  | Tại sao module AI trễ?     | Vì A làm chậm                                                                                         |
|  2  | Vì sao A làm chậm?        | Vì thiếu kinh nghiệm MPC                                                                              |
|  3  | Vì sao thiếu kinh nghiệm? | Vì chưa được training MPC                                                                           |
|  4  | Vì sao chưa training?      | Vì không có kế hoạch đào tạo từ đầu                                                           |
|  5  | **Nguyên nhân gốc** | **Thiếu kế hoạch đào tạo** → Đề xuất: dự trù 2 tuần tự nghiên cứu trước khi code |

> **Ý nghĩa:** Giải quyết tận gốc nguyên nhân, tránh lặp lại vấn đề trong tương lai.

## 10.4 Họp

### 10.4.1 Họp định kỳ

- **Tần suất:** 1 lần/tuần (thứ 7 hoặc Chủ nhật).
- **Thời lượng:** 30–60 phút.
- **Hình thức:** Trực tiếp hoặc online (Discord/Zalo).
- **Nội dung:**
  - Báo cáo tiến độ tuần qua (mỗi người 5 phút).
  - Thảo luận vấn đề gặp phải.
  - Lập kế hoạch tuần tới.
  - Review rủi ro (nếu cần).

### 10.4.2 Họp đột xuất

Họp đột xuất được triệu tập khi:

- Phát hiện bug nghiêm trọng ảnh hưởng nhiều module.
- Cần thay đổi thiết kế/yêu cầu gấp.
- Chuẩn bị demo cho giảng viên.

### 10.4.3 Nguyên tắc họp hiệu quả

1. **Thông báo trước ≥ 1 ngày** (trừ đột xuất).
2. **Có chương trình họp** (agenda) rõ ràng.
3. **Không quá 60 phút** cho họp định kỳ.
4. **Ghi biên bản** mọi quyết định.
5. **Phân công rõ** ai làm gì sau họp.

### 10.4.4 Biên bản họp nhóm (minh họa)

**Biên bản họp #1:**

| Mục         | Nội dung                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------- |
| Ngày        | Tuần 3, Thứ 7                                                                                               |
| Tham dự     | A, B, C                                                                                                       |
| Nội dung    | Phân công công việc chi tiết cho giai đoạn thiết kế                                                  |
| Kết quả    | B: thiết kế mạch (tuần 3–4); C: thiết kế DB + UI (tuần 3–4); A: thiết kế kiến trúc + AI pipeline |
| Vấn đề    | Chưa rõ cấu trúc ARX nào phù hợp → A nghiên cứu thêm                                               |
| Hành động | A: Đọc tài liệu MathWorks về ARX trước tuần 4                                                         |

**Biên bản họp #2:**

| Mục         | Nội dung                                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------- |
| Ngày        | Tuần 8, Thứ 7                                                                                |
| Tham dự     | A, B, C                                                                                        |
| Nội dung    | Review tiến độ giữa kỳ                                                                    |
| Kết quả    | HW + FW: hoàn thành 100%; Backend: 80%; AI (ARX): đang huấn luyện, FIT = 85,85%; Web: 60% |
| Vấn đề    | Kalman Filter chưa bắt đầu → có nguy cơ trễ                                            |
| Hành động | A: Ưu tiên Kalman tuần 9; C: Đẩy nhanh Web tuần 9–10                                    |

**Biên bản họp #3:**

| Mục         | Nội dung                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------- |
| Ngày        | Tuần 12, Thứ 7                                                                          |
| Tham dự     | A, B, C                                                                                   |
| Nội dung    | Chuẩn bị kiểm thử tích hợp                                                          |
| Kết quả    | Tất cả module hoàn thành; MPC đã tune xong; Web đã tích hợp biểu đồ dự báo |
| Vấn đề    | Cảm biến DHT22 hỏng 1 chiếc → thay dự phòng                                        |
| Hành động | B: Thay cảm biến; Cả nhóm: kiểm thử end-to-end tuần 13                             |

---

## 10.5 Điều chỉnh

### 10.5.1 Khi dự án không đúng lịch biểu

Trong dự án Smart Greenhouse, giai đoạn **Phát triển AI bị trễ 1 tuần** (MPC tuning phức tạp hơn dự kiến).

**Biện pháp đã áp dụng:**

- Tăng giờ làm việc của thành viên A (từ 20h → 28h/tuần trong tuần 9–10).
- Sử dụng dữ liệu mô phỏng để huấn luyện song song, không chờ dữ liệu thực.
- B hỗ trợ kiểm thử phần tích hợp ESP32 ↔ Backend trong khi A tập trung MPC.

### 10.5.2 Khi chi phí có nguy cơ tăng

Chi phí vượt 75.000 VNĐ (12%) do thay cảm biến hỏng và mua thêm dây nối.

**Biện pháp:**

- Sử dụng kinh phí dự phòng đã dự trù (165.000 VNĐ).
- Tổng chi phí thực tế (700.000 VNĐ) vẫn nằm trong ngân sách tổng (625.000 + 165.000 = 790.000 VNĐ).

### 10.5.3 Khi chất lượng có nguy cơ giảm

**Tình huống:** FIT free-run của ARX chỉ đạt 66,42% (thấp hơn FIT 1-step 85,85%), sai số tích lũy khi dự báo dài hạn.

**Biện pháp:**

- Tích hợp Kalman Filter để lọc nhiễu trước khi đưa vào MPC → tín hiệu ổn định hơn.
- MPC sử dụng dự báo ngắn hạn (receding horizon) thay vì free-run → tận dụng FIT 1-step cao.
- Thêm ràng buộc an toàn (safety constraints) trong MPC để tránh overshoot/undershoot.

---

## 10.6 Kiểm soát thay đổi

### 10.6.1 Nguồn gốc thay đổi

| Nguồn                      | Ví dụ                                                     |
| --------------------------- | ----------------------------------------------------------- |
| Giảng viên (khách hàng) | Yêu cầu thêm chức năng cảnh báo ngưỡng             |
| Nhóm phát triển          | Phát hiện cần thêm Adaptive Kalman thay Kalman cơ bản |
| Môi trường kỹ thuật    | Cảm biến hỏng → thay đổi cách đọc dữ liệu        |

### 10.6.2 Phân loại thay đổi

|      Loại      | Mô tả                                              | Ví dụ                         |
| :-------------: | ---------------------------------------------------- | ------------------------------- |
|   Quan trọng   | Ảnh hưởng đến kiến trúc/tiến độ tổng thể | Thêm MPC vào hệ thống       |
| Ít quan trọng | Thay đổi nhỏ, không ảnh hưởng tiến độ      | Đổi màu giao diện           |
|    Bổ sung    | Tính năng mới ngoài phạm vi ban đầu           | Thêm trang dự báo xu hướng |

### 10.6.3 Thủ tục kiểm soát thay đổi

```
Ghi nhận yêu cầu → Phân tích tác động → Phê duyệt (PM + nhóm) → Thực hiện → Kiểm tra
```

1. **Ghi nhận:** Người đề xuất mô tả thay đổi cần thiết.
2. **Phân tích:** PM đánh giá tác động đến thời gian, chi phí, chất lượng.
3. **Phê duyệt:** PM quyết định (thay đổi nhỏ) hoặc cả nhóm biểu quyết (thay đổi lớn).
4. **Thực hiện:** Cập nhật WBS, phân công, thực hiện.
5. **Kiểm tra:** Xác nhận thay đổi đã được thực hiện đúng.

### 10.6.4 Nhật ký kiểm soát thay đổi

| STT |  Ngày  | Mô tả thay đổi                                                     |    Nguồn    |      Loại      | Tác động                                                 | Quyết định |
| :-: | :------: | ---------------------------------------------------------------------- | :----------: | :-------------: | ----------------------------------------------------------- | :------------: |
|  1  | Tuần 3 | Thêm Adaptive Kalman Filter (IAE) thay Kalman cơ bản                |  Nhóm dev  |   Quan trọng   | +1 tuần phát triển AI                                    | ✅ Chấp nhận |
|  2  | Tuần 5 | Giảng viên yêu cầu thêm chức năng cảnh báo ngưỡng trên Web | Giảng viên |    Bổ sung    | +3 ngày phát triển Web                                   | ✅ Chấp nhận |
|  3  | Tuần 7 | Đổi giao thức HTTP polling sang WebSocket                           |  Nhóm dev  |   Quan trọng   | Thiết kế lại truyền thông, nhưng cải thiện realtime | ✅ Chấp nhận |
|  4  | Tuần 9 | Thêm trang dự báo xu hướng trên Dashboard                        |  Nhóm dev  |    Bổ sung    | +2 ngày phát triển Web                                   | ✅ Chấp nhận |
|  5  | Tuần 11 | Thay cảm biến DHT22 hỏng bằng cảm biến dự phòng                |  Kỹ thuật  | Ít quan trọng | +60.000 VNĐ chi phí                                       | ✅ Chấp nhận |

---

## 10.7 Lập kế hoạch lại (nếu có)

### 10.7.1 Khi nào cần lập kế hoạch lại

Trong dự án, **không cần lập kế hoạch lại toàn bộ**. Tuy nhiên, có 2 điều chỉnh cục bộ:

1. **Tuần 5:** Khi quyết định thêm Adaptive Kalman → kéo dài giai đoạn AI thêm 1 tuần, bù bằng rút ngắn kiểm thử.
2. **Tuần 7:** Khi chuyển từ HTTP polling sang WebSocket → B cần refactor firmware 3 ngày, nhưng không ảnh hưởng tổng tiến độ vì B có thời gian dư.

### 10.7.2 Các biện pháp điều chỉnh theo tình huống

**① Khi dự án diễn ra không đúng lịch biểu:**

- Điều chỉnh lại lịch biểu.
- Nhờ người hỗ trợ (B hỗ trợ A kiểm thử AI).
- Cải tiến cách làm việc (dùng dữ liệu mô phỏng song song).
- Tập trung vào các công việc trên đường găng.

**② Khi chi phí dự án có nguy cơ tăng:**

- Dùng linh kiện thay thế giá thấp hơn nếu có thể.
- Ưu tiên mua linh kiện cần thiết, trì hoãn mua dự phòng.
- Áp dụng "Design to Cost" — chỉ làm trong đúng ngân sách.

**③ Khi chất lượng có nguy cơ giảm:**

- Tăng cường kiểm tra chất lượng (test tích hợp sớm hơn).
- Tìm kiếm sự hỗ trợ từ giảng viên hướng dẫn.
- Kiểm tra chéo giữa các thành viên.
- Tập trung vào các khâu trọng yếu (MPC tuning, WebSocket).

### 10.7.3 Quy trình tái cấu trúc kế hoạch

1. Xác định phạm vi thay đổi.
2. Đánh giá tác động lên đường găng (Critical Path).
3. Điều chỉnh WBS, ước lượng thời gian, lịch biểu.
4. Thông báo cho tất cả thành viên.
5. Cập nhật Trello Board.

---

## 10.8 Kết thúc dự án

### 10.8.1 Các lý do kết thúc

Dự án kết thúc vì **hoàn thành mục tiêu đề ra** trong thời gian quy định (15 tuần). Tất cả deliverables đã được chuyển giao:

- ✅ Hệ thống phần cứng hoạt động.
- ✅ Firmware ESP32 ổn định.
- ✅ Backend + AI tích hợp thành công.
- ✅ Web Dashboard đầy đủ 6 màn hình.
- ✅ Báo cáo PBL + QLDA hoàn thành.

### 10.8.2 Thống kê số liệu

| Hạng mục          |                Giá trị                |
| ------------------- | :-------------------------------------: |
| Tổng thời gian    |                15 tuần                |
| Tổng giờ công    |  424 giờ (A: 168h, B: 119h, C: 137h)  |
| Tổng chi phí      |              700.000 VNĐ              |
| Số work packages   |                   45                   |
| Số milestone       |                    9                    |
| Số thay đổi      |                    5                    |
| Số rủi ro xảy ra | 2 (R02: cảm biến hỏng, R03: trễ AI) |

### 10.8.3 So sánh kế hoạch vs thực tế

| Tiêu chí           |  Kế hoạch  |     Thực tế     |  Sai lệch  |
| -------------------- | :----------: | :----------------: | :----------: |
| Thời gian tổng     |   15 tuần   |      15 tuần      |      0      |
| Chi phí             | 625.000 VNĐ |    700.000 VNĐ    |     +12%     |
| FIT 1-step ARX       |    ≥ 80%    |       85,85%       |  +5,85% ✅  |
| FIT free-run         |    ≥ 60%    |       66,42%       |  +6,42% ✅  |
| RMSE free-run        |    ≤ 1.5    |       0,978       | Tốt hơn ✅ |
| MPC vùng mục tiêu |   55–65%   |       Đạt       |      ✅      |
| Số màn hình Web   |     ≥ 6     |         6         |      ✅      |
| Giai đoạn trễ     |      0      | 2 (thiết kế, AI) |     ⚠️     |

### 10.8.4 Bài học kinh nghiệm (Lessons Learned)

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

| STT | Đề xuất                                                    | Lý do                                     |
| :-: | ------------------------------------------------------------- | ------------------------------------------ |
|  1  | Dự trù +30% thời gian cho module AI/ML                     | MPC tuning phức tạp hơn dự kiến       |
|  2  | Bắt đầu nghiên cứu AI từ tuần 1 (không chờ tuần 5)  | Giảm áp lực cuối dự án               |
|  3  | Áp dụng code review bắt buộc qua Pull Request             | Phát hiện bug sớm, chia sẻ kiến thức |
|  4  | WebSocket nên chọn từ đầu thay vì refactor giữa chừng | Tiết kiệm 3 ngày refactor firmware      |
|  5  | Tổ chức buổi sharing kiến thức nội bộ 2 tuần/lần     | Giảm rủi ro phụ thuộc 1 người        |

### 10.8.5 Lưu trữ hồ sơ dự án

Toàn bộ hồ sơ dự án được lưu trữ tại:

- **GitHub Repository:** Mã nguồn (firmware, backend, web, AI).
- **Google Drive/OneDrive:** Báo cáo, slide, biên bản họp, nhật ký thay đổi.
- **Trello Board:** Lịch sử quản lý công việc.

---

## 10.9 Kỹ năng mềm trong quản lý dự án

### 10.9.1 Giao tiếp

- **Giao tiếp nội bộ:** Nhóm sử dụng Zalo/Discord cho trao đổi hàng ngày, họp online khi không gặp trực tiếp.
- **Giao tiếp với giảng viên:** Báo cáo tiến độ định kỳ, gửi email khi cần hỗ trợ.
- **Nguyên tắc:** Thông tin rõ ràng, kịp thời, không giấu vấn đề.

### 10.9.2 Tổ chức

- PM (thành viên A) duy trì **Trello Board** cập nhật, đảm bảo mọi công việc có người phụ trách và deadline.
- **WBS + RACI** giúp phân công rõ ràng, tránh chồng chéo.
- **Git workflow** (branching, pull request) giúp quản lý mã nguồn có tổ chức.

### 10.9.3 Xử lý tình huống

| Tình huống                                        | Cách xử lý                                                          |
| --------------------------------------------------- | ---------------------------------------------------------------------- |
| Cảm biến DHT22 hỏng đột ngột                  | Thay nhanh bằng cảm biến dự phòng, không ảnh hưởng tiến độ |
| MPC tuning mất nhiều thời gian hơn dự kiến    | A tăng giờ làm, B hỗ trợ kiểm thử tích hợp                    |
| Thành viên không hiểu module của người khác | Tổ chức buổi sharing kiến thức nội bộ                           |

---

## 10.10 Kiểm soát theo mô hình Waterfall và công cụ sử dụng

Dự án Smart Greenhouse áp dụng mô hình **Waterfall tuần tự**, kiểm soát tại **điểm chuyển giao giữa các giai đoạn** (Phase Gate Review):

| Giai đoạn | Thời gian | Đầu ra | Điểm kiểm soát |
|-----------|:---------:|--------|----------------|
| Phân tích yêu cầu | Tuần 1–2 | Tài liệu yêu cầu, SOW, WBS | **Gate 1:** Giảng viên duyệt phạm vi |
| Thiết kế | Tuần 3–4 | Kiến trúc, sơ đồ mạch, DB schema | **Gate 2:** Review thiết kế nhóm |
| Phát triển | Tuần 4–12 | HW, FW, Backend, AI, Web | **Gate 3:** Demo từng module |
| Kiểm thử | Tuần 11–13 | Test report, bug fix | **Gate 4:** Hệ thống chạy end-to-end |
| Triển khai | Tuần 13–15 | Báo cáo, slide, demo | **Gate 5:** Bảo vệ đồ án |

**Công cụ kiểm soát nhóm đã sử dụng:** Trello (quản lý task), Excel/Google Sheets (time sheet, EVM, rủi ro), GitHub (version control, issue tracking), Zalo/Discord (giao tiếp, họp online).

## 10.11 Kết quả dự án

### 10.11.1 Phần cứng

- Mạch hoàn chỉnh trên breadboard: ESP32 + DHT22 + cảm biến độ ẩm đất + LDR + 4 relay + buzzer.
- Hoạt động ổn định 24/7, truyền dữ liệu WebSocket real-time.
- Chi phí linh kiện: ~625.000 VNĐ.

### 10.11.2 Firmware

- ESP32 thu thập dữ liệu cảm biến mỗi 2 giây.
- Giao tiếp WebSocket hai chiều với Backend Django.
- State machine không blocking, xử lý mất kết nối tự động.

### 10.11.3 Backend + AI

| Thành phần             | Kết quả                                                    |
| ------------------------ | ------------------------------------------------------------ |
| **Django Backend** | REST API + WebSocket server, xử lý dữ liệu real-time     |
| **Mô hình ARX**  | Dự đoán nhiệt độ/độ ẩm, FIT ≥ 85%                  |
| **Kalman Filter**  | Lọc nhiễu cảm biến, giảm sai số ~30%                   |
| **MPC Controller** | Điều khiển tối ưu tưới tiêu, tiết kiệm nước ~25% |

### 10.11.4 Web Dashboard

- ReactJS Dashboard: giám sát real-time, biểu đồ lịch sử, cảnh báo ngưỡng.
- Điều khiển thủ công bơm/quạt/đèn từ giao diện web.
- Responsive trên desktop và mobile.

### 10.11.5 Tài liệu

- Báo cáo PBL: 10 chương đầy đủ.
- Báo cáo QLDA: 5 chương (Ch1, Ch2, Ch3, Ch9, Ch10).
- Slide thuyết trình + demo trực tiếp.

---

## 10.12 Kết luận và hướng phát triển

### 10.12.1 Kết luận

Dự án Smart Greenhouse đã **hoàn thành đúng mục tiêu** đặt ra ban đầu, tạo ra một hệ thống nhà kính thông minh tích hợp IoT và AI có khả năng giám sát, dự đoán và điều khiển tối ưu các thông số môi trường.

**Kết quả đạt được:**

- ✅ Hệ thống hoạt động ổn định, truyền dữ liệu real-time.
- ✅ Mô hình AI (ARX + Kalman + MPC) hoạt động đúng chức năng.
- ✅ Web Dashboard trực quan, dễ sử dụng.
- ✅ Dự án hoàn thành đúng hạn 15 tuần, chi phí vượt 12% nhưng trong phạm vi chấp nhận.
- ✅ Tất cả thành viên hoàn thành nhiệm vụ, không có xung đột nhân sự.

**Bài học từ dự án:**

- Quản lý dự án theo Waterfall phù hợp với nhóm nhỏ, yêu cầu ổn định.
- Phân công RACI ngay từ đầu giúp tránh chồng chéo.
- Dự trù thời gian nghiên cứu trước khi code (đặc biệt với MPC) là cần thiết.

### 10.12.2 Hướng phát triển

1. **Mở rộng phạm vi:** Thêm cảm biến CO₂, pH đất; mở rộng quy mô nhà kính thực tế.
2. **Nâng cao AI:** Chuyển từ ARX sang mô hình Deep Learning (LSTM, Transformer) cho dự đoán chính xác hơn.
3. **Mobile App:** Phát triển ứng dụng mobile (React Native) để giám sát và điều khiển từ xa.
4. **Bảo mật:** Thêm xác thực JWT, mã hóa WebSocket (WSS), phân quyền người dùng.
5. **Triển khai thực tế:** Deploy hệ thống tại nhà kính nông nghiệp, thu thập dữ liệu dài hạn.
