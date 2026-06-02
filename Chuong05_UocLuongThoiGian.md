# CHƯƠNG 5: ƯỚC LƯỢNG THỜI GIAN DỰ ÁN

---

## 5.1 Mục đích của ước lượng thời gian

Ước lượng thời gian dự án là bước chuyển các công việc trong WBS thành các giá trị thời lượng cụ thể, làm cơ sở cho lập lịch biểu, phân bổ nhân lực, kiểm soát tiến độ và đánh giá khả năng hoàn thành dự án trong giới hạn thời gian của học phần.

Đối với dự án Hệ thống Nhà kính Thông minh, việc ước lượng thời gian có ý nghĩa quan trọng vì dự án gồm nhiều nhóm công việc phụ thuộc lẫn nhau: phần cứng, firmware ESP32, Server, mô hình ARX, Kalman Filter và MPC Controller. Nếu một nhóm công việc như AI hoặc Server bị trễ, quá trình kiểm thử tích hợp và demo cuối kỳ sẽ bị ảnh hưởng trực tiếp.

---

## 5.2 Phương pháp ước lượng

### 5.2.1 Ước lượng theo PERT

Công thức PERT được dùng để ước lượng thời gian cho các nhóm công việc chính. PERT phù hợp với dự án vì nhiều công việc có độ bất định, đặc biệt là các phần ARX, Kalman Filter, MPC Controller và tích hợp AI vào backend.

Các tham số:
* **MO (Most Optimistic):** thời gian lạc quan nhất.
* **ML (Most Likely):** thời gian khả dĩ nhất.
* **MP (Most Pessimistic):** thời gian bi quan nhất.
* **EST (Estimated Time):** thời gian ước lượng theo PERT.

Công thức:
$$EST = \frac{MO + 4 \times ML + MP}{6}$$

### 5.2.2 Ước lượng theo giờ công

Ngoài ước lượng theo tuần, nhóm quy đổi công việc thành giờ công để đánh giá tải nhân lực. Giờ công được tính theo mức độ phức tạp, vai trò của từng thành viên và khối lượng thực hiện trong báo cáo PBL.

Quy ước:
$$1\text{ man-month} = 160\text{ giờ công}$$

Chi phí nhân lực không quy đổi thành tiền lương thực tế mà dùng để đánh giá effort, mức phân bổ công việc và khả năng quá tải của từng thành viên.

---

## 5.3 Bảng ước lượng thời gian dự án

### 5.3.1 Ước lượng PERT theo WBS (TBS)

**Bảng 12. Bảng ước lượng thời gian theo PERT**

| Mã WBS | Nhóm công việc | Nhân sự chính | MO (ngày) | ML (ngày) | MP (ngày) | EST (ngày) |
|:---:|----------------|:-------------:|:---:|:---:|:---:|:---:|
| **T1** | Phân tích yêu cầu | Trí, Sỹ, Sinh | 7 | 10 | 14 | 10,2 |
| **T2** | Thiết kế hệ thống | Trí, Sỹ, Sinh | 12 | 18 | 24 | 18,0 |
| **T3.1** | Phát triển phần cứng | Sỹ | 14 | 20 | 28 | 20,3 |
| **T3.2** | Phát triển Firmware | Sỹ | 14 | 20 | 28 | 20,3 |
| **T3.3** | Phát triển Backend Django + WebSocket Server | Sỹ | 18 | 25 | 35 | 25,5 |
| **T3.5 - T3.8** | Phát triển & Tích hợp AI | Trí, Sinh | 35 | 49 | 63 | 49,0 |
| **T3.4** | Phát triển Web Dashboard | Sỹ | 24 | 35 | 49 | 35,5 |
| **T4** | Kiểm thử | Trí, Sỹ, Sinh | 14 | 21 | 30 | 21,3 |
| **T5** | Hoàn thành | Trí, Sỹ, Sinh | 14 | 20 | 28 | 20,3 |

### 5.3.2 Cơ sở ước lượng cho từng nhóm công việc

**Bảng 13. Cơ sở ước lượng cho từng nhóm công việc**

| Mã WBS | Hoạt động | Cơ sở ước lượng | Rủi ro ảnh hưởng thời gian |
|:---:|-----------|-----------------|----------------------------|
| **T1** | Phân tích yêu cầu | Khảo sát yêu cầu nhà kính, xác định chức năng dashboard, cảm biến và điều khiển | Yêu cầu thay đổi khi demo thử |
| **T2** | Thiết kế hệ thống | Thiết kế kiến trúc ESP32 - Django - React - AI, thiết kế mạch và pipeline dữ liệu | Phụ thuộc quyết định giao tiếp WebSocket/API |
| **T3.1** | Phát triển phần cứng | Lắp cảm biến, relay, actuator, LCD và mô hình nhà kính | Linh kiện lỗi, sai số cảm biến |
| **T3.2** | Phát triển Firmware | Đọc cảm biến, gửi dữ liệu, nhận lệnh, điều khiển relay | Kết nối WiFi/WebSocket không ổn định |
| **T3.3** | Phát triển Backend Django + WebSocket Server | Xây dựng Django, REST API, WebSocket Server, MySQL | Thay đổi khi kết nối dữ liệu với frontend và AI |
| **T3.5 - T3.8** | Phát triển & Tích hợp AI | Thu thập dữ liệu, ARX, Kalman, MPC, tích hợp quy trình tự động | Độ khó thuật toán và tinh chỉnh tham số |
| **T3.4** | Phát triển Web Dashboard | Login, dashboard realtime, chart, điều khiển, cảnh báo, dự báo | UI phải đồng bộ với dữ liệu backend |
| **T4** | Kiểm thử | Kiểm thử module, kiểm thử AI, kiểm thử end-to-end | Lỗi tích hợp xuất hiện muộn |
| **T5** | Hoàn thành | Demo, báo cáo PBL, báo cáo QLDA, slide, bảo vệ | Dồn việc vào cuối kỳ |

---

## 5.4 Ước lượng giờ công theo WBS

### Bảng ước lượng giờ công theo WBS

**Bảng 14. Bảng ước lượng giờ công theo WBS**

| Mã WBS | Nhóm công việc | Giờ công | Nhân sự chính | Cơ sở ước lượng |
|:------:|----------------|:--------:|:-------------:|-----------------|
| **T1** | Phân tích yêu cầu | 50h | Trí, Sỹ, Sinh | Khảo sát yêu cầu đề tài, xác định yêu cầu chức năng/phi chức năng, phạm vi và ràng buộc |
| **T2** | Thiết kế hệ thống | 55h | Trí, Sỹ, Sinh | Thiết kế kiến trúc tổng thể, sơ đồ mạch, giao thức truyền thông, database, UI và pipeline AI |
| **T3.1** | Phát triển phần cứng | 45h | Sỹ | Module cảm biến, relay/actuator, mô hình nhà kính, LCD I2C |
| **T3.2** | Phát triển Firmware | 50h | Sỹ | Đọc cảm biến, WebSocket Client, điều khiển relay, LCD, Manual/Auto |
| **T3.3** | Phát triển Backend Django + WebSocket Server | 60h | Sỹ | Django Server, REST API, Django Channels, MySQL |
| **T3.5 - T3.8** | Phát triển & Tích hợp AI | 95h | Trí, Sinh | Dữ liệu, ARX, Kalman Filter, MPC Controller và tích hợp pipeline điều khiển |
| **T3.4** | Phát triển Web Dashboard | 55h | Sỹ | Login, dashboard tổng quan, biểu đồ realtime, điều khiển, cảnh báo, trang dự báo |
| **T4** | Kiểm thử | 52h | Trí, Sỹ, Sinh | Kiểm thử phần cứng, firmware, backend, web, AI và end-to-end |
| **T5** | Hoàn thành | 40h | Trí, Sỹ, Sinh | Demo, báo cáo PBL, báo cáo QLDA, slide thuyết trình |
| | **Tổng** | **502h** | | |

---

## 5.5 Ước lượng chi phí nhân lực

### Quy đổi man-month theo WBS

**Bảng 15. Quy đổi man-month theo WBS**

| Mã WBS | Nhóm công việc | Giờ công | Man-month |
|:------:|----------------|:--------:|:---------:|
| **T1** | Phân tích yêu cầu | 50h | 0,31 |
| **T2** | Thiết kế hệ thống | 55h | 0,34 |
| **T3.1** | Phát triển phần cứng | 45h | 0,28 |
| **T3.2** | Phát triển Firmware | 50h | 0,31 |
| **T3.3** | Phát triển Backend Django + WebSocket Server | 60h | 0,38 |
| **T3.5 - T3.8** | Phát triển & Tích hợp AI | 95h | 0,59 |
| **T3.4** | Phát triển Web Dashboard | 55h | 0,34 |
| **T4** | Kiểm thử | 52h | 0,33 |
| **T5** | Hoàn thành | 40h | 0,25 |
| | **Tổng** | **502h** | **3,14** |

Trong báo cáo này, quy ước $1\text{ man-month} = 160\text{ giờ công}$ được áp dụng nhằm quy đổi toàn bộ effort của dự án về cùng một đơn vị đo lường thống nhất. Cần lưu ý rằng con số 160 giờ không phản ánh thời lượng của một tuần làm việc, mà thể hiện khối lượng công việc tương đương một tháng làm việc tiêu chuẩn của một nhân sự.

Cơ sở quy đổi được xác định như sau:
$$1\text{ man-month} = 4\text{ tuần} \times 40\text{ giờ/tuần} = 160\text{ giờ công}$$

---

## 5.6 Ước lượng hiệu chỉnh theo GEF

Hệ số hiệu chỉnh môi trường (GEF) được sử dụng để phản ánh các yếu tố thực tế làm giảm năng suất làm việc của nhóm so với điều kiện lý tưởng.

GEF được xác định theo công thức:
$$GEF = 100\% - 15\% = 85\%$$

Trên cơ sở đó, giờ công thực tế cần thiết được hiệu chỉnh bằng cách chia giờ công ước tính ban đầu cho GEF, nhằm bù đắp phần năng suất bị suy giảm:
$$\text{Giờ công hiệu chỉnh} = \frac{502}{0,85} = 590,6\text{ giờ}$$

Quy đổi sang đơn vị man-month theo quy ước $1\text{ man-month} = 160\text{ giờ công}$:
$$\text{Man-month hiệu chỉnh} = \frac{590,6}{160} = 3,69$$

### Ước lượng hiệu chỉnh theo GEF

| Yếu tố ảnh hưởng | Tỷ lệ suy giảm | Giải thích |
|-------------------|:--------------:|------------|
| Khoảng nghỉ Tết âm lịch 09/02/2026 - 02/03/2026 | 5% | Làm gián đoạn mạch phát triển và kiểm thử |
| Độ phức tạp IoT - Backend - Web - AI | 4% | Hệ thống gồm nhiều lớp kỹ thuật cần tích hợp với nhau |
| Rủi ro phần cứng, cảm biến và WebSocket | 2% | Có thể phát sinh lỗi kết nối, sai số cảm biến, mất WiFi |
| Rủi ro Kalman/MPC | 4% | MPC cần tuning và kiểm thử nhiều kịch bản điều khiển |
| **Tổng suy giảm** | **15%** | |

---

## 5.7 Nhận xét

Độ chính xác của các ước lượng trên chỉ mang tính tương đối và có thể có sự chênh lệch so với thực tế, do đây là kết quả ước lượng ban đầu dựa trên các giả định và còn phụ thuộc vào nhiều yếu tố khác phát sinh trong quá trình triển khai.

Trong suốt vòng đời dự án, các con số ước lượng sẽ được xem xét và cập nhật định kỳ theo tiến độ thực tế, nhằm đảm bảo kế hoạch luôn phản ánh sát nhất tình trạng hiện tại của dự án.
