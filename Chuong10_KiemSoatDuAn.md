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
|  **T1**  | Phân tích yêu cầu    |    Tuần 1    |    Tuần 2    |    Tuần 1    |    Tuần 2    |      100%      | Đúng tiến độ                       |
|  **T2**  | Thiết kế hệ thống    |    Tuần 3    |    Tuần 4    |    Tuần 3    |    Tuần 5    |      100%      | Trễ 1 tuần (thiết kế AI phức tạp) |
| **T3.1** | Phát triển phần cứng |    Tuần 4    |    Tuần 6    |    Tuần 4    |    Tuần 6    |      100%      | Đúng tiến độ                       |
| **T3.2** | Phát triển Firmware    |    Tuần 5    |    Tuần 7    |    Tuần 5    |    Tuần 7    |      100%      | Đúng tiến độ                       |
| **T3.3** | Phát triển Backend     |    Tuần 5    |    Tuần 9    |    Tuần 5    |    Tuần 9    |      100%      | Đúng tiến độ                       |
| **T3.5-T3.8** | Phát triển AI          |    Tuần 5    |   Tuần 11   |    Tuần 5    |   Tuần 12   |      100%      | Trễ 1 tuần (MPC tuning)               |
| **T3.4** | Phát triển Web         |    Tuần 6    |   Tuần 12   |    Tuần 6    |   Tuần 12   |      100%      | Đúng tiến độ                       |
|  **T4**  | Kiểm thử               |   Tuần 11   |   Tuần 13   |   Tuần 12   |   Tuần 14   |      100%      | Trễ 1 tuần do tích hợp AI trễ      |
|  **T5**  | Triển khai & Tài liệu |   Tuần 13   |   Tuần 15   |   Tuần 13   |   Tuần 15   |      100%      | Đúng tiến độ                       |

**b) Time sheet cá nhân**

|      Tuần      |         Thành viên A (PM + ARX)         |     Thành viên B (HW/FW & Fullstack)     |        Thành viên C (Kalman & MPC)        |
| :-------------: | :---------------------------------------: | :-----------------------------: | :------------------------------------: |
|      1–2      |       35h (phân tích, SOW, WBS, RACI)       |       30h (khảo sát HW & Web, BOM)       |      10h (khảo sát yêu cầu AI)      |
|      3–4      | 18h (thiết kế kiến trúc hệ thống) |     32h (thiết kế mạch & DB, Figma)     |        5h (tham vấn thiết kế pipeline AI)        |
|      5–6      |  12h (tiền xử lý dữ liệu cho ARX)  |   38h (lắp ráp HW, code FW & Django BE)   |        8h (mô phỏng thuật toán Kalman)        |
|      7–8      |      13h (huấn luyện & đánh giá ARX)      |      38h (hoàn thiện FW, WebSocket server)      |    8h (mô phỏng bộ điều khiển MPC)    |
|      9–10      |         8h (PM giám sát & kiểm soát)         |        23h (fix bug FW, ReactJS Dashboard)        |    28h (phát triển Kalman Filter & MPC)    |
|     11–12     |      25h (tích hợp hệ thống, MPC tuning)      | 26h (kiểm thử HW/FW, hoàn thiện Web) |   20h (tích hợp hệ thống, MPC tuning)   |
|     13–14     |  25h (kiểm thử tích hợp, viết báo cáo)  |   25h (kiểm thử tích hợp, viết báo cáo)   | 22h (kiểm thử tích hợp, viết báo cáo) |
|       15       |           10h (slide, bảo vệ)           |       10h (demo, bảo vệ)       |          10h (demo, bảo vệ)          |
| **Tổng** |              **146h**              |         **245h**         |             **111h**             |

### 10.2.3 Phân tích sai biệt

**a) Sai biệt lịch biểu (Schedule Variance — SV)**

| Mã WBS | Giai đoạn           | KH (tuần) | TT (tuần) | SV |     Đánh giá     |
| :-----: | --------------------- | :--------: | :--------: | :-: | :------------------: |
|  **T1**  | Phân tích yêu cầu |     2     |     2     |  0  |      ✅ Đúng      |
|  **T2**  | Thiết kế hệ thống    |     2     |     3     | -1  |      ⚠️ Trễ      |
| **T3.1 + T3.2** | Phát triển HW + FW  |     3     |     3     |  0  |      ✅ Đúng      |
| **T3.3** | Phát triển Backend  |     5     |     5     |  0  |      ✅ Đúng      |
| **T3.5-T3.8** | Phát triển AI       |     7     |     8     | -1  |      ⚠️ Trễ      |
| **T3.4** | Phát triển Web      |     7     |     7     |  0  |      ✅ Đúng      |
|  **T4**  | Kiểm thử            |     3     |     2     | +1  |    ✅ Nhanh hơn    |
| **Tổng** | Tổng dự án         |     15     |     15     |  0  | ✅ Đúng tổng thể |

**Nhận xét:** Dự án có 2 giai đoạn trễ (thiết kế và AI), nhưng bù lại bằng việc kiểm thử nhanh hơn. Tổng thời gian dự án vẫn đúng 15 tuần.

**b) Sai biệt chi phí (Cost Variance — CV)**

Để quản lý kinh phí chặt chẽ theo yêu cầu, dưới đây là bảng đối chiếu chi tiết giữa kinh phí dự tính ban đầu (kế hoạch - KH) và kinh phí mua sắm thực tế (thực tế - TT) của từng hạng mục thiết bị:

| STT | Danh mục linh kiện / Hạng mục | KH (VNĐ) | TT (VNĐ) | Sai lệch (CV) | Lý do chênh lệch |
|:---:|-------------------------------|:--------:|:--------:|:-------------:|------------------|
| 1 | ESP32 DevKit V1 | 95.000 | 105.000 | -10.000 | Biến động giá thị trường & phí ship |
| 2 | Màn hình LCD I2C 16×2 | 70.000 | 70.000 | 0 | Đúng dự toán |
| 3 | Cảm biến (DHT22 + Soil + LDR) | 70.000 | 86.000 | -16.000 | Biến động giá thị trường & phí ship |
| 4 | Relay + Bơm ×2 + Quạt + Phun sương + LED | 210.000 | 210.000 | 0 | Đúng dự toán |
| 5 | Mô hình + Breadboard + Dây + Nguồn | 240.000 | 265.000 | -25.000 | Mua thêm dây cắm test và phụ kiện phát sinh |
| 6 | Tấm pin NLMT 6V 5-7W | 130.000 | 130.000 | 0 | Đúng dự toán |
| 7 | Pin 18650 ×2 + Sạc TP4056 + Đốc pin | 160.000 | 160.000 | 0 | Đúng dự toán |
| 8 | Servo SG90 ×2 | 60.000 | 60.000 | 0 | Đúng dự toán |
| 9 | LDR ×4 + Trở 10kΩ ×4 + Relay 1 kênh ×3 | 100.000 | 100.000 | 0 | Đúng dự toán |
| 10 | Công tắc nguồn ON/OFF + Cáp USB | 65.000 | 65.000 | 0 | Đúng dự toán |
| 11 | Cảm biến DHT22 (Thay thế linh kiện hỏng) | 0 | 60.000 | -60.000 | Dùng quỹ dự phòng thay cảm biến hỏng ở tuần 5 |
| 12 | Chi phí vận chuyển phát sinh hỏa tốc | 0 | 60.000 | -60.000 | Ship hỏa tốc cảm biến và thiết bị dự phòng |
| | **Tổng kinh phí** | **1.200.000** | **1.371.000** | **-171.000** | **Vượt 14.25% so với dự toán** |

**Nhận xét:** Chi phí thực tế vượt 171.000 VNĐ (14.25%) so với kế hoạch ban đầu do biến động giá thị trường, mua thêm phụ kiện test (25.000 VNĐ), mua lại cảm biến DHT22 mới (60.000 VNĐ) khi cảm biến cũ gặp sự cố hỏng hóc trong tuần 5, và chi phí vận chuyển hỏa tốc phát sinh (60.000 VNĐ). Tuy nhiên, phần chi phí phát sinh này đã được bù đắp hoàn toàn bởi **quỹ dự phòng rủi ro** của dự án (255.000 VNĐ - quy định tại Chương 9), giúp tổng chi phí thực tế (1.371.000 VNĐ) vẫn nằm an toàn dưới giới hạn ngân sách tối đa cho phép (1.455.000 VNĐ bao gồm dự phòng).

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

Giả sử tổng ngân sách BAC = 1.200.000 VNĐ, tổng giờ công KH = 502h.

| Chỉ số |          Giá trị          | Diễn giải                                |
| :------: | :-------------------------: | ------------------------------------------ |
|    PV    |     ~70% × 502h = 351h     | Theo KH, tuần 10 phải hoàn thành 70%   |
|    EV    |     ~65% × 502h = 326h     | Thực tế hoàn thành 65% (AI đang trễ) |
|    AC    |            343h            | Công sức thực tế đã bỏ ra           |
|    SV    | 326 − 351 =**−25h** | ⚠️ Chậm tiến độ                      |
|    CV    | 326 − 343 =**−17h** | ⚠️ Vượt chi phí nhân công           |
|   SPI   |   326/351 =**0.93**   | Chậm 7% so với KH                        |
|   CPI   |   326/343 =**0.95**   | Chi phí vượt 5%                         |

**Nhận xét:** SPI = 0.93 cho thấy dự án chậm 7% tại tuần 10, chủ yếu do module MPC. Sau can thiệp (tăng giờ C và sự hỗ trợ của A, B), dự án đã hoàn thành đúng hạn tuần 15.

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
|   EAC   |        1.200.000 ÷ 0.95 =**1.263.158 VNĐ**        | Dự kiến chi phí tổng khi hoàn thành |
|   ETC   | 1.263.158 − 1.371.000 × (10/15) =**349.158 VNĐ** | Chi phí cần thêm cho phần còn lại   |
|   VAC   |      1.200.000 − 1.263.158 =**−63.158 VNĐ**      | Dự kiến vượt ngân sách ~5.3%        |

**Các công thức EAC khác (tùy tình huống):**

- `EAC = AC + (BAC − EV)` → Giả định: công việc còn lại sẽ đúng ngân sách.
- `EAC = AC + [(BAC − EV) ÷ (CPI × SPI)]` → Giả định: cả chi phí và tiến độ đều ảnh hưởng.

---

## 10.3 Phát hiện và giải quyết vấn đề

### 10.3.1 Phân tích nguyên nhân gốc (Phương pháp 5 Whys)

Phương pháp tìm nguyên nhân gốc bằng cách hỏi "Tại sao?" nhiều lần:

**Ví dụ áp dụng cho dự án Smart Greenhouse (Giải quyết trễ hạn bộ MPC):**

| Lần | Câu hỏi | Trả lời |
| :--: | ---------------------------- | -------------------------------------------------------------------------------------------------------- |
|  1  | Tại sao module AI & điều khiển bị trễ? | Vì thành viên C gặp khó khăn khi lập trình bộ điều khiển MPC |
|  2  | Vì sao C gặp khó khăn khi lập trình MPC? | Vì mô hình dự báo ARX free-run bị tích lũy sai số lớn (chỉ đạt FIT 66,42%) khiến MPC hoạt động không ổn định |
|  3  | Vì sao mô hình ARX bị sai số tích lũy? | Vì dữ liệu cảm biến đầu vào bị dính nhiễu thô mạnh và cấu hình dự báo free-run quá dài |
|  4  | Vì sao không xử lý lọc nhiễu ngay từ đầu? | Vì chưa xây dựng bộ lọc Kalman Filter cho cảm biến và chưa áp dụng chiến lược Receding Horizon |
|  5  | **Nguyên nhân gốc** | **Thiếu giải pháp lọc nhiễu cảm biến và chưa tối ưu luồng dự báo ngắn hạn** ➔ Đề xuất: C tập trung triển khai Adaptive Kalman Filter; A đổi luồng ARX sang Receding Horizon hỗ trợ MPC. |

> **Ý nghĩa:** Giải quyết tận gốc nguyên nhân, tránh lặp lại vấn đề trong tương lai.

### 10.3.2 Bảng theo dõi và giải quyết vấn đề thực tế (Issue Log)

Để áp dụng thực hành kiểm soát trực quan, mọi vấn đề phát sinh thực tế trong quá trình phát triển hệ thống nhà kính thông minh đều được ghi nhận, phân tích và xử lý triệt để theo bảng dưới đây:

| ID | Vấn đề phát sinh thực tế | Giai đoạn / Tuần | Cách phát hiện | Biện pháp giải quyết thực tế | Người phụ trách | Trạng thái |
| :--: | ---------------------------------- | :--------------: | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | :-------------: | :--------: |
| **VĐ01** | Lọc nhiễu cảm biến thô bị sai số và mô hình ARX free-run bị tích lũy sai số lớn. | Tuần 5–8 | Đồ thị giám sát nhiệt độ bị gai nhiễu mạnh; FIT free-run của ARX sụt giảm xuống còn 66,42%. | - **C** triển khai thuật toán lọc Adaptive Kalman Filter.<br>- **A** chuyển sang cấu trúc Receding Horizon (dự báo ngắn hạn) cung cấp cho MPC. | **A, C** | ✅ Đã xử lý |
| **VĐ02** | Trễ tiến độ module điều khiển tối ưu MPC (chậm 1 tuần). | Tuần 9–10 | Báo cáo EVM tuần 10 hiển thị chỉ số SPI = 0,93 (chậm 7%), SV = -33h. | - **C** tăng cường giờ làm việc (20h ➔ 28h/tuần).<br>- **B** hỗ trợ kiểm thử tích hợp.<br>- **A** dùng dữ liệu mô phỏng chạy song song. | **C** (chính)<br>**A, B** (hỗ trợ) | ✅ Đã xử lý |
| **VĐ03** | Cảm biến nhiệt độ/độ ẩm DHT22 đột ngột bị hỏng không phản hồi dữ liệu. | Tuần 11 | Màn hình LCD I2C hiển thị giá trị lỗi `NaN`; Web Dashboard không hiển thị được thông số. | - **B** sử dụng cảm biến DHT22 dự phòng sẵn có trong BOM để thay thế thiết bị hỏng.<br>- Thực hiện hiệu chuẩn lại thông số trong 1 ngày. | **B** | ✅ Đã xử lý |
| **VĐ04** | Mất kết nối WebSocket ngắt quãng giữa ESP32 và Django Channels server. | Tuần 12 | Giao diện Web Dashboard ngừng cập nhật thời gian thực, console log báo lỗi kết nối. | - **B** bổ sung thư viện tự động kết nối lại (Auto-reconnect) trong ESP32 firmware.<br>- Thiết lập buffer dữ liệu tạm thời để tránh mất mát. | **B** | ✅ Đã xử lý |


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

### 10.4.4 Biên bản họp nhóm mẫu

Dưới đây là biên bản họp kiểm soát và giải quyết các vấn đề phát sinh thực tế của dự án nhà kính thông minh:

| Mục | Nội dung |
| :--- | :--- |
| **Tên cuộc họp** | Họp kiểm soát tiến độ giữa kỳ & Giải quyết vướng mắc kỹ thuật |
| **Thời gian** | 09:00 - 10:00, Thứ Bảy, Tuần 8 của dự án |
| **Địa điểm** | Trực tuyến qua Discord và Google Meet |
| **Thành viên tham dự** | - **Hoàng Minh Trí** (Chủ trì - PM & ARX)<br>- **Đinh Công Trung Sỹ** (Thành viên - HW/FW & Fullstack Web)<br>- **Ngô Quang Sinh** (Thành viên - Kalman & MPC) |
| **Nội dung cuộc họp** | 1. Đánh giá hiện trạng hoàn thành các module so với tiến độ kế hoạch (Baseline schedule).<br>2. Phân tích nguyên nhân bộ lọc Kalman và MPC chưa chạy ổn định.<br>3. Thống nhất kế hoạch tăng tốc lập trình Web Dashboard và hoàn thiện firmware điều khiển hồi tiếp. |
| **Kết quả đánh giá** | - Phần cứng & Firmware ESP32: Đã hoàn thành 100% việc lắp ráp mô hình và kết nối truyền thông.<br>- Backend Django: Đã hoàn thành 80% luồng cơ sở dữ liệu và API.<br>- Mô hình ARX: Đã được **Hoàng Minh Trí** huấn luyện xong, độ chính xác đạt FIT = 85,85%.<br>- Giao diện Web Dashboard: Mới đạt 60% do phát sinh thêm thiết kế WebSockets truyền dữ liệu thời gian thực.<br>- Bộ điều khiển MPC & Kalman Filter: Đang bị chậm tiến độ (chưa bắt đầu tích hợp thử nghiệm) do **Ngô Quang Sinh** gặp khó khăn trong việc lọc nhiễu cảm biến thô đầu vào. |
| **Vấn đề & Rủi ro phát hiện** | - Thuật toán lọc nhiễu thô của cảm biến nhiệt độ/độ ẩm DHT22 có sai số lớn, gây dao động ngõ ra điều khiển của MPC.<br>- Tiến độ module điều khiển MPC bị trễ 1 tuần so với kế hoạch ban đầu, có nguy cơ làm ảnh hưởng đến thời gian kiểm thử tích hợp toàn hệ thống. |
| **Hành động & Phân công xử lý** | 1. **Ngô Quang Sinh**: Tập trung nghiên cứu và lập trình Adaptive Kalman Filter để lọc nhiễu cảm biến thô, sẵn sàng tích hợp trước Tuần 9.<br>2. **Đinh Công Trung Sỹ**: Tập trung đẩy nhanh tiến độ lập trình giao diện Web Dashboard (ReactJS) và tối ưu hóa luồng WebSockets (Tuần 9-10).<br>3. **Hoàng Minh Trí**: Hỗ trợ chuẩn bị dữ liệu mô phỏng nhà kính từ mô hình ARX để Sinh chạy mô phỏng kiểm thử độc lập cho bộ MPC mà không cần đợi phần cứng hoàn thiện.<br>4. Thống nhất tăng giờ làm việc của nhóm (đặc biệt là Sinh và Sỹ) để bù đắp phần tiến độ bị chậm. |


---

## 10.5 Điều chỉnh

### 10.5.1 Khi dự án không đúng lịch biểu

Trong dự án Smart Greenhouse, giai đoạn **Phát triển AI bị trễ 1 tuần** (Kalman Filter và MPC tuning phức tạp hơn dự kiến).

**Biện pháp đã áp dụng:**

- Tăng giờ làm việc của thành viên C (từ 20h → 28h/tuần trong tuần 9–10).
- Sử dụng dữ liệu mô phỏng để huấn luyện song song, không chờ dữ liệu thực.
- B hỗ trợ kiểm thử phần tích hợp ESP32 ↔ Backend trong khi C tập trung tối ưu Kalman Filter và MPC.

### 10.5.2 Khi chi phí có nguy cơ tăng

Chi phí vượt 171.000 VNĐ (14.25%) do biến động giá thị trường, mua thêm dây cắm, thay cảm biến hỏng và phí ship hỏa tốc.

**Biện pháp:**

- Sử dụng kinh phí dự phòng đã dự trù (255.000 VNĐ).
- Tổng chi phí thực tế (1.371.000 VNĐ) vẫn nằm trong ngân sách tổng (1.200.000 + 255.000 = 1.455.000 VNĐ).

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

## 10.7 Kết thúc dự án

### 10.7.1 Các lý do kết thúc

Dự án kết thúc vì **hoàn thành mục tiêu đề ra** trong thời gian quy định (15 tuần). Tất cả deliverables đã được chuyển giao:

- ✅ Hệ thống phần cứng hoạt động.
- ✅ Firmware ESP32 ổn định.
- ✅ Backend + AI tích hợp thành công.
- ✅ Web Dashboard đầy đủ 6 màn hình.
- ✅ Báo cáo PBL + QLDA hoàn thành.

### 10.7.2 Thống kê số liệu

| Hạng mục          |                Giá trị                |
| ------------------- | :-------------------------------------: |
| Tổng thời gian    |                15 tuần                |
| Tổng giờ công    |  502 giờ (A: 146h, B: 245h, C: 111h)  |
| Tổng chi phí      |            1.371.000 VNĐ              |
| Số work packages   |                   22                   |
| Số milestone       |                    9                    |
| Số thay đổi      |                    5                    |
| Số rủi ro xảy ra | 2 (R02: cảm biến hỏng, R03: trễ AI) |

### 10.7.3 So sánh kế hoạch vs thực tế

| Tiêu chí           |  Kế hoạch  |     Thực tế     |  Sai lệch  |
| -------------------- | :----------: | :----------------: | :----------: |
| Thời gian tổng     |   15 tuần   |      15 tuần      |      0      |
| Chi phí             | 1.200.000 VNĐ |    1.371.000 VNĐ    |   +14.25%    |
| FIT 1-step ARX       |    ≥ 80%    |       85,85%       |  +5,85% ✅  |
| FIT free-run         |    ≥ 60%    |       66,42%       |  +6,42% ✅  |
| RMSE free-run        |    ≤ 1.5    |       0,978       | Tốt hơn ✅ |
| MPC vùng mục tiêu |   55–65%   |       Đạt       |      ✅      |
| Số màn hình Web   |     ≥ 6     |         6         |      ✅      |
| Giai đoạn trễ     |      0      | 2 (thiết kế, AI) |     ⚠️     |

### 10.7.4 Bài học kinh nghiệm (Lessons Learned)

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
|  4  | WebSocket nên chọn từ đầu thay vị refactor giữa chừng | Tiết kiệm 3 ngày refactor firmware      |
|  5  | Tổ chức buổi sharing kiến thức nội bộ 2 tuần/lần     | Giảm rủi ro phụ thuộc 1 người        |

### 10.7.5 Lưu trữ hồ sơ dự án

Toàn bộ hồ sơ dự án được lưu trữ tại:

- **GitHub Repository:** Mã nguồn (firmware, backend, web, AI).
- **Google Drive/OneDrive:** Báo cáo, slide, biên bản họp, nhật ký thay đổi.
- **Trello Board:** Lịch sử quản lý công việc.

---

## 10.8 Kết quả dự án

### 10.8.1 Phần cứng

- Mạch hoàn chỉnh trên breadboard: ESP32 + DHT22 + cảm biến độ ẩm đất + LDR + 4 relay + buzzer.
- Hoạt động ổn định 24/7, truyền dữ liệu WebSocket real-time.
- Chi phí linh kiện: ~1.200.000 VNĐ.

### 10.8.2 Firmware

- ESP32 thu thập dữ liệu cảm biến mỗi 2 giây.
- Giao tiếp WebSocket hai chiều với Backend Django.
- State machine không blocking, xử lý mất kết nối tự động.

### 10.8.3 Backend + AI

| Thành phần             | Kết quả                                                    |
| ------------------------ | ------------------------------------------------------------ |
| **Django Backend** | REST API + WebSocket server, xử lý dữ liệu real-time     |
| **Mô hình ARX**  | Dự đoán nhiệt độ/độ ẩm, FIT ≥ 85%                  |
| **Kalman Filter**  | Lọc nhiễu cảm biến, giảm sai số ~30%                   |
| **MPC Controller** | Điều khiển tối ưu tưới tiêu, tiết kiệm nước ~25% |

### 10.8.4 Web Dashboard

- ReactJS Dashboard: giám sát real-time, biểu đồ lịch sử, cảnh báo ngưỡng.
- Điều khiển thủ công bơm/quạt/đèn từ giao diện web.
- Responsive trên desktop và mobile.

### 10.8.5 Tài liệu

- Báo cáo PBL: 10 chương đầy đủ.
- Báo cáo QLDA: 5 chương (Ch1, Ch2, Ch3, Ch9, Ch10).
- Slide thuyết trình + demo trực tiếp.

---

## 10.9 Kết luận và hướng phát triển

### 10.9.1 Kết luận

Dự án Smart Greenhouse đã **hoàn thành đúng mục tiêu** đặt ra ban đầu, tạo ra một hệ thống nhà kính thông minh tích hợp IoT và AI có khả năng giám sát, dự đoán và điều khiển tối ưu các thông số môi trường.

**Kết quả đạt được:**

- ✅ Hệ thống hoạt động ổn định, truyền dữ liệu real-time.
- ✅ Mô hình AI (ARX + Kalman + MPC) hoạt động đúng chức năng.
- ✅ Web Dashboard trực quan, dễ sử dụng.
- ✅ Dự án hoàn thành đúng hạn 15 tuần, chi phí vượt 14.25% nhưng trong phạm vi chấp nhận.
- ✅ Tất cả thành viên hoàn thành nhiệm vụ, không có xung đột nhân sự.

**Bài học từ dự án:**

- Quản lý dự án theo Waterfall phù hợp với nhóm nhỏ, yêu cầu ổn định.
- Phân công RACI ngay từ đầu giúp tránh chồng chéo.
- Dự trù thời gian nghiên cứu trước khi code (đặc biệt với MPC) là cần thiết.

### 10.9.2 Hướng phát triển

1. **Mở rộng phạm vi:** Thêm cảm biến CO₂, pH đất; mở rộng quy mô nhà kính thực tế.
2. **Nâng cao AI:** Chuyển từ ARX sang mô hình Deep Learning (LSTM, Transformer) cho dự đoán chính xác hơn.
3. **Mobile App:** Phát triển ứng dụng mobile (React Native) để giám sát và điều khiển từ xa.
4. **Bảo mật:** Thêm xác thực JWT, mã hóa WebSocket (WSS), phân quyền người dùng.
5. **Triển khai thực tế:** Deploy hệ thống tại nhà kính nông nghiệp, thu thập dữ liệu dài hạn.
