# CHƯƠNG 4 ƯỚC LƯỢNG THỜI GIAN DỰ ÁN

## 4.1 Mục đích của ước lượng thời gian

Ước lượng thời gian dự án là bước chuyển các công việc trong WBS thành các giá trị thời lượng cụ thể, làm cơ sở cho lập lịch biểu, phân bổ nhân lực, kiểm soát tiến độ và đánh giá khả năng hoàn thành dự án trong giới hạn thời gian của học phần.

Đối với dự án Hệ thống Nhà kính Thông minh, việc ước lượng thời gian có ý nghĩa quan trọng vì dự án gồm nhiều nhóm công việc phụ thuộc lẫn nhau: phần cứng, firmware ESP32, Server, mô hình ARX, Kalman Filter và MPC Controller. Nếu một nhóm công việc như AI hoặc Server bị trễ, quá trình kiểm thử tích hợp và demo cuối kỳ sẽ bị ảnh hưởng trực tiếp.

## 4.2 Phương pháp ước lượng

Công thức PERT dung để ước lượng thời gian cho các nhóm công việc chính. PERT phù hợp với dự án vì nhiều công việc có độ bất định, đặc biệt là các phần ARX, Kalman Filter, MPC Controller và tích hợp AI vào backend.

Các tham số:

MO (Most Optimistic): thời gian lạc quan nhất.

ML (Most Likely): thời gian khả dĩ nhất.

MP (Most Pessimistic): thời gian bi quan nhất.

EST (Estimated Time): thời gian ước lượng theo PERT.

Công thức:

EST=MO+4×ML+MP6

## 4.3 Ước lượng PERT theo WBS

Uớc lượng thời gian theo WBS.

| AC | WBS | Hoạt động | MO | ML | MP | EST (ngày) |
| --- | --- | --- | --- | --- | --- | --- |
| T1 | Phân tích yêu cầu | Phân tích yêu cầu | Phân tích yêu cầu | Phân tích yêu cầu | Phân tích yêu cầu | Phân tích yêu cầu |
| A | T1.1 | Khảo sát các giải pháp nhà kính thông minh hiện có | 2 | 4 | 6 | 4,00 |
| B | T1.2 | Xác định yêu cầu chức năng | 2 | 4 | 6 | 4,00 |
| C | T1.3 | Xác định yêu cầu phi chức năng | 2 | 4 | 6 | 4,00 |
| D | T1.4 | Xác định phạm vi và ràng buộc | 2 | 4 | 6 | 4,00 |
|  |  | Tổng T1 |  |  |  | 16,00 |
| T2 | Thiết kế | Thiết kế | Thiết kế | Thiết kế | Thiết kế | Thiết kế |
| E | T2.1 - T2.5 | Thiết kế kiến trúc tổng thể HW + SW | 3 | 4 | 6 | 4,17 |
| F | T2.6 | Thiết kế pipeline AI ARX - Kalman - MPC | 8 | 12 | 16 | 12,00 |
|  |  | Tổng T2 |  |  |  | 16,17 |
| T3 | Phát triển | Phát triển | Phát triển | Phát triển | Phát triển | Phát triển |
| G | T3.1 | Lắp ráp phần cứng mạch, cảm biến, relay, Solar Tracking | 8 | 12 | 16 | 12,00 |
| H | T3.2 | Lập trình firmware ESP32 | 10 | 14 | 20 | 14,33 |
| I | T3.3 | Phát triển Backend Django + WebSocket Server | 12 | 16 | 22 | 16,33 |
| J | T3.4 | Phát triển Web Dashboard ReactJS | 10 | 14 | 20 | 14,33 |
| K | T3.5 | Huấn luyện mô hình ARX | 14 | 21 | 30 | 21,33 |
| L | T3.6 | Phát triển Kalman Filter | 10 | 14 | 20 | 14,33 |
| M | T3.7 | Phát triển MPC Controller | 10 | 14 | 20 | 14,33 |
| N | T3.8 | Tích hợp AI vào Web | 3 | 4 | 7 | 4,33 |
|  |  | Tổng T3 |  |  |  | 111,31 |
| T4 | Kiểm thử | Kiểm thử | Kiểm thử | Kiểm thử | Kiểm thử | Kiểm thử |
| O | T4.1 - T4.3 | Kiểm thử tích hợp chức năng | 5 | 8 | 11 | 8,00 |
|  |  | Tổng T4 |  |  |  | 8,00 |
| T5 | Hoàn thành | Hoàn thành | Hoàn thành | Hoàn thành | Hoàn thành | Hoàn thành |
| P | T5.1 | Hiệu chỉnh phần cứng và mô hình AI | 3 | 4 | 7 | 4,33 |
| Q | T5.2 | Hoàn thành báo cáo và bảo vệ đồ án | 3 | 4 | 7 | 4,33 |
|  |  | Tổng T5 |  |  |  | 8,66 |
|  |  | Tổng cộng |  |  |  | 160,14 |
