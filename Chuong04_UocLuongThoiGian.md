# CHƯƠNG 4: ƯỚC LƯỢNG THỜI GIAN DỰ ÁN

## 4.1 Mục đích của ước lượng thời gian

Ước lượng thời gian dự án là bước chuyển các công việc trong WBS thành các giá trị thời lượng cụ thể, làm cơ sở cho lập lịch biểu, phân bổ nhân lực, kiểm soát tiến độ và đánh giá khả năng hoàn thành dự án trong giới hạn thời gian của học phần.

Đối với dự án Hệ thống Nhà kính Thông minh, việc ước lượng thời gian có ý nghĩa quan trọng vì dự án gồm nhiều nhóm công việc phụ thuộc lẫn nhau: phần cứng, firmware ESP32, Server, mô hình ARX, Kalman Filter và MPC Controller. Nếu một nhóm công việc như AI hoặc Server bị trễ, quá trình kiểm thử tích hợp và demo cuối kỳ sẽ bị ảnh hưởng trực tiếp.

## 4.2 Phương pháp ước lượng

### 4.2.1 Ước lượng theo PERT

Công thức PERT dùng để ước lượng thời gian cho các nhóm công việc chính. PERT phù hợp với dự án vì nhiều công việc có độ bất định, đặc biệt là các phần ARX, Kalman Filter, MPC Controller và tích hợp AI vào Web.

Các tham số:

- MO (Most Optimistic): thời gian lạc quan nhất.
- ML (Most Likely): thời gian khả dĩ nhất.
- MP (Most Pessimistic): thời gian bi quan nhất.
- EST (Estimated Time): thời gian ước lượng theo PERT.

Công thức:

EST = (MO + 4 × ML + MP) / 6

### 4.2.2 Ước lượng theo giờ công

Ngoài ước lượng theo tuần, nhóm quy đổi công việc thành giờ công để đánh giá tải nhân lực. Giờ công được tính theo mức độ phức tạp, vai trò của từng thành viên và khối lượng thực hiện trong báo cáo PBL.

Quy ước: 1 man-month = 160 giờ công

Chi phí nhân lực không quy đổi thành tiền lương thực tế mà dùng để đánh giá effort, mức phân bổ công việc và khả năng quá tải của từng thành viên.

## 4.3 Bảng ước lượng thời gian dự án

### 4.3.1 Ước lượng PERT theo WBS

Ước lượng thời gian theo PERT.

| AC | WBS | Hoạt động | MO | ML | MP | EST (ngày) |
|:--:|:---:|-----------|:--:|:--:|:--:|:----------:|
| **T1** | | **Phân tích yêu cầu** | | | | |
| A | T1.1 | Khảo sát các giải pháp nhà kính thông minh hiện có | 2 | 4 | 6 | 4,00 |
| B | T1.2 | Xác định yêu cầu chức năng | 2 | 4 | 6 | 4,00 |
| C | T1.3 | Xác định yêu cầu phi chức năng | 2 | 4 | 6 | 4,00 |
| D | T1.4 | Xác định phạm vi và ràng buộc | 2 | 4 | 6 | 4,00 |
| | | **Tổng T1** | | | | **16,00** |
| **T2** | | **Thiết kế** | | | | |
| E | T2.1 - T2.5 | Thiết kế kiến trúc tổng thể HW + SW | 3 | 4 | 6 | 4,17 |
| F | T2.6 | Thiết kế pipeline AI ARX - Kalman - MPC | 8 | 12 | 16 | 12,00 |
| | | **Tổng T2** | | | | **16,17** |
| **T3** | | **Phát triển** | | | | |
| G | T3.1 | Lắp ráp phần cứng mạch, cảm biến, relay, Solar Tracking | 8 | 12 | 16 | 12,00 |
| H | T3.2 | Lập trình firmware ESP32 | 10 | 14 | 21 | 14,50 |
| I | T3.3 | Phát triển Backend Django + WebSocket Server | 12 | 16 | 22 | 16,33 |
| J | T3.4 | Phát triển Web Dashboard ReactJS | 10 | 14 | 21 | 14,50 |
| K | T3.5 | Huấn luyện mô hình ARX | 14 | 21 | 30 | 21,33 |
| L | T3.6 | Phát triển Kalman Filter | 10 | 14 | 21 | 14,50 |
| M | T3.7 | Phát triển MPC Controller | 10 | 14 | 22 | 14,67 |
| N | T3.8 | Tích hợp AI vào Web | 3 | 4 | 7 | 4,33 |
| | | **Tổng T3** | | | | **112,16** |
| **T4** | | **Kiểm thử** | | | | |
| O | T4.1 - T4.3 | Kiểm thử tích hợp chức năng | 5 | 8 | 11 | 8,00 |
| | | **Tổng T4** | | | | **8,00** |
| **T5** | | **Hoàn thành** | | | | |
| P | T5.1 | Hiệu chỉnh phần cứng và mô hình AI | 3 | 4 | 7 | 4,33 |
| Q | T5.2 | Hoàn thành báo cáo và bảo vệ đồ án | 3 | 4 | 7 | 4,33 |
| | | **Tổng T5** | | | | **8,66** |
| | | **Tổng cộng** | | | | **160,99** |

### 4.3.2 Cơ sở ước lượng cho từng nhóm công việc

Cơ sở ước lượng cho từng nhóm công việc

| WBS | Hoạt động | Cơ sở ước lượng | Rủi ro ảnh hưởng thời gian |
|-----|-----------|-----------------|----------------------------|
| T1 | Phân tích yêu cầu | Khảo sát yêu cầu nhà kính, xác định chức năng dashboard, cảm biến và điều khiển | Yêu cầu thay đổi khi demo thử |
| T2 | Thiết kế hệ thống | Thiết kế kiến trúc ESP32 - Django - React - AI, thiết kế mạch và pipeline dữ liệu | Phụ thuộc quyết định giao tiếp WebSocket/API |
| T3.1 | Phát triển phần cứng | Lắp cảm biến, relay, actuator, Solar Tracking và mô hình nhà kính | Linh kiện lỗi, sai số cảm biến |
| T3.2 | Phát triển Firmware | Đọc cảm biến, gửi dữ liệu, nhận lệnh, điều khiển relay | Kết nối WiFi/WebSocket không ổn định |
| T3.3 | Phát triển Backend | Xây dựng Django, REST API, WebSocket Server, MySQL | Thay đổi khi kết nối dữ liệu với frontend và AI |
| T3.4 | Phát triển Web Dashboard | Dashboard realtime, biểu đồ, điều khiển, cảnh báo, dự báo | UI phải đồng bộ với dữ liệu backend |
| T3.5 - T3.8 | Phát triển AI | Thu thập dữ liệu, ARX, Kalman, MPC và tích hợp AI vào Web | Độ khó thuật toán và tinh chỉnh tham số |
| T4 | Kiểm thử | Kiểm thử phần cứng, firmware, backend, web, AI và end-to-end | Lỗi tích hợp xuất hiện muộn |
| T5 | Hoàn thành | Hiệu chỉnh, báo cáo PBL, báo cáo QLDA, slide, bảo vệ | Dồn việc vào cuối kỳ |

## 4.4 Ước lượng giờ công theo WBS

Bảng ước lượng giờ công theo WBS

| Mã WBS | Nhóm công việc | Giờ công | Nhân sự chính | Cơ sở ước lượng |
|--------|----------------|----------|---------------|-----------------|
| T1 | Phân tích yêu cầu | 50h | A, B, C | Khảo sát yêu cầu đề tài, xác định yêu cầu chức năng/phi chức năng, phạm vi và ràng buộc. |
| T2 | Thiết kế hệ thống | 55h | A, B, C | Thiết kế kiến trúc tổng thể, sơ đồ mạch, giao thức truyền thông, database, UI và pipeline AI. |
| T3.1 | Phát triển phần cứng | 45h | B | Module cảm biến, relay/actuator, Solar Tracking và mô hình nhà kính. |
| T3.2 | Phát triển Firmware | 50h | B | Đọc cảm biến, WebSocket Client, điều khiển relay, Manual/Auto. |
| T3.3 | Phát triển Backend | 60h | B | Django Server, REST API, Django Channels, MySQL. |
| T3.4 | Phát triển Web Dashboard | 55h | B | Dashboard tổng quan, biểu đồ realtime, điều khiển, cảnh báo, trang dự báo. |
| T3.5 - T3.8 | Phát triển AI | 95h | A, C | Dữ liệu, ARX, Kalman Filter, MPC Controller và tích hợp AI vào Web. |
| T4 | Kiểm thử | 52h | A, B, C | Kiểm thử phần cứng, firmware, backend, web, AI và end-to-end. |
| T5 | Hoàn thành | 40h | A, B, C | Hiệu chỉnh, demo, báo cáo PBL, báo cáo QLDA, slide thuyết trình. |
| | Tổng | 502h | | |

## 4.5 Ước lượng chi phí nhân lực

Quy đổi man-month theo WBS

| WBS | Nhóm công việc | Giờ công | Man-month |
|-----|----------------|----------|-----------|
| T1 | Phân tích yêu cầu | 50h | 0,31 |
| T2 | Thiết kế hệ thống | 55h | 0,34 |
| T3.1 | Phát triển phần cứng | 45h | 0,28 |
| T3.2 | Phát triển Firmware | 50h | 0,31 |
| T3.3 | Phát triển Backend | 60h | 0,38 |
| T3.4 | Phát triển Web Dashboard | 55h | 0,34 |
| T3.5 - T3.8 | Phát triển AI | 95h | 0,59 |
| T4 | Kiểm thử | 52h | 0,33 |
| T5 | Hoàn thành | 40h | 0,25 |
| | Tổng | 502h | 3,14 |

Trong báo cáo này, quy ước 1 man-month = 160 giờ công được áp dụng nhằm quy đổi toàn bộ effort của dự án về cùng một đơn vị đo lường thống nhất. Cần lưu ý rằng con số 160 giờ không phản ánh thời lượng của một tuần làm việc, mà thể hiện khối lượng công việc tương đương một tháng làm việc tiêu chuẩn của một nhân sự.

Cơ sở quy đổi được xác định như sau: một tuần làm việc tiêu chuẩn gồm 5 ngày, mỗi ngày 8 giờ, tương đương 40 giờ/tuần. Một tháng làm việc được tính xấp xỉ bằng 4 tuần, do đó:

1 man-month = 4 tuần × 40 giờ/tuần = 160 giờ công

## 4.6 Ước lượng hiệu chỉnh theo GEF

Hệ số hiệu chỉnh môi trường (GEF) được sử dụng để phản ánh các yếu tố thực tế làm giảm năng suất làm việc của nhóm so với điều kiện lý tưởng. GEF được xác định theo công thức:

GEF = 100% - Tổng tỷ lệ suy giảm năng suất = 100% - 15% = 85%

Trên cơ sở đó, giờ công thực tế cần thiết được hiệu chỉnh bằng cách chia giờ công ước tính ban đầu cho GEF, nhằm bù đắp phần năng suất bị suy giảm:

Giờ công hiệu chỉnh = 502 / 0,85 = 590,6 giờ

Quy đổi sang đơn vị man-month theo quy ước 1 man-month = 160 giờ công:

Man-month hiệu chỉnh = 590,6 / 160 = 3,69 man-month

Ước lượng hiệu chỉnh theo GEF

| Yếu tố ảnh hưởng | Tỷ lệ suy giảm | Giải thích |
|------------------|----------------|------------|
| Khoảng nghỉ 06/02/2026 - 02/03/2026 | 5% | Làm gián đoạn mạch phát triển và kiểm thử. |
| Độ phức tạp IoT - Backend - Web - AI | 4% | Hệ thống gồm nhiều lớp kỹ thuật cần tích hợp với nhau. |
| Rủi ro phần cứng, cảm biến và WebSocket | 2% | Có thể phát sinh lỗi kết nối, sai số cảm biến, mất WiFi. |
| Rủi ro Kalman/MPC | 4% | MPC cần tuning và kiểm thử nhiều kịch bản điều khiển. |
| Tổng suy giảm | 15% | |

## 4.7 Nhận xét

Độ chính xác của các ước lượng trên chỉ mang tính tương đối và có thể có sự chênh lệch so với thực tế, do đây là kết quả ước lượng ban đầu dựa trên các giả định và còn phụ thuộc vào nhiều yếu tố khác phát sinh trong quá trình triển khai. Trong suốt vòng đời dự án, các con số ước lượng sẽ được xem xét và cập nhật định kỳ theo tiến độ thực tế, nhằm đảm bảo kế hoạch luôn phản ánh sát nhất tình trạng hiện tại của dự án.
