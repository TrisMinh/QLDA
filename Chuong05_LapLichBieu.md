# CHƯƠNG 5: LẬP LỊCH BIỂU CHO DỰ ÁN

## 5.1 Mục đích của việc lập lịch biểu

Lập lịch biểu là quá trình sắp xếp các công việc trong WBS theo trình tự thời gian, xác định mối quan hệ phụ thuộc, thời điểm bắt đầu và kết thúc dự kiến, cũng như những công việc đòi hỏi sự tuân thủ tiến độ nghiêm ngặt.

Đối với dự án Hệ thống Nhà kính Thông minh, lịch biểu phục vụ các mục đích quản lý chủ yếu sau: xác định thứ tự thực hiện và quan hệ phụ thuộc giữa các công việc; đánh giá mức độ phân bổ và khả năng quá tải nguồn lực theo từng giai đoạn. Từ đó, nhóm có cơ sở để đánh giá tính khả thi của mục tiêu hoàn thành dự án trong vòng 15 tuần và chủ động điều chỉnh khi cần thiết.

## 5.2 Lập bảng hoạt động

### 5.2.1 Bảng hoạt động

Bảng 15. Bảng hoạt động của dự án.

| AC | WBS | Hoạt động | Công việc trước đó | Thời gian | Thời lượng |
|:--:|:---:|-----------|--------------------|-----------|:----------:|
| A | T1.1 | Khảo sát các giải pháp nhà kính thông minh hiện có | - | 05/01/2026 - 08/01/2026 | 4 ngày |
| B | T1.2 | Xác định yêu cầu chức năng | A | 09/01/2026 - 12/01/2026 | 4 ngày |
| C | T1.3 | Xác định yêu cầu phi chức năng | B | 13/01/2026 - 16/01/2026 | 4 ngày |
| D | T1.4 | Xác định phạm vi và ràng buộc | C | 17/01/2026 - 20/01/2026 | 4 ngày |
| E | T2.1 - T2.5 | Thiết kế kiến trúc tổng thể HW + SW | D | 21/01/2026 - 24/01/2026 | 4 ngày |
| F | T2.6 | Thiết kế pipeline AI ARX - Kalman - MPC | E | 25/01/2026 - 05/02/2026 | 12 ngày |
| G | T3.1 | Lắp ráp phần cứng mạch, cảm biến, relay, Solar Tracking | E | 25/01/2026 - 05/02/2026 | 12 ngày |
| H | T3.2 | Lập trình firmware ESP32 | G | 03/03/2026 - 16/03/2026 | 14 ngày |
| I | T3.3 | Phát triển Backend Django + WebSocket Server | H | 17/03/2026 - 01/04/2026 | 16 ngày |
| J | T3.4 | Phát triển Web Dashboard ReactJS | I | 02/04/2026 - 15/04/2026 | 14 ngày |
| K | T3.5 | Huấn luyện mô hình ARX | F | 03/03/2026 - 23/03/2026 | 21 ngày |
| L | T3.6 | Phát triển Kalman Filter | K | 24/03/2026 - 06/04/2026 | 14 ngày |
| M | T3.7 | Phát triển MPC Controller | L | 07/04/2026 - 20/04/2026 | 14 ngày |
| N | T3.8 | Tích hợp AI vào Web | J, M | 21/04/2026 - 24/04/2026 | 4 ngày |
| O | T4.1 - T4.3 | Kiểm thử tích hợp chức năng | N | 25/04/2026 - 02/05/2026 | 8 ngày |
| P | T5.1 | Hiệu chỉnh phần cứng và mô hình AI | O | 03/05/2026 - 06/05/2026 | 4 ngày |
| Q | T5.2 | Hoàn thành báo cáo và bảo vệ đồ án | P | 07/05/2026 - 10/05/2026 | 4 ngày |

Ghi chú: Khoảng thời gian từ 06/02/2026 đến 02/03/2026 là giai đoạn nghỉ Tết/nghỉ giữa tiến độ nên nhóm không bố trí công việc phát triển chính. Các công việc sau kỳ nghỉ bắt đầu lại từ ngày 03/03/2026.

## 5.3 Sơ đồ ADM

ADM (Arrow Diagramming Method) biểu diễn công việc bằng mũi tên và thể hiện quan hệ trước - sau giữa các hoạt động.

Hình 6. Sơ đồ ADM

## 5.4 Sơ đồ Gantt

Bảng phân công thời gian

| ID | Hoạt động | Ngày bắt đầu | Ngày kết thúc | Thời lượng | Công việc trước đó |
|----|-----------|--------------|---------------|------------|--------------------|
| A | Khảo sát các giải pháp nhà kính thông minh hiện có | 05/01 | 08/01 | 4 | None |
| B | Xác định yêu cầu chức năng | 09/01 | 12/01 | 4 | A |
| C | Xác định yêu cầu phi chức năng | 13/01 | 16/01 | 4 | B |
| D | Xác định phạm vi và ràng buộc | 17/01 | 20/01 | 4 | C |
| E | Thiết kế kiến trúc tổng thể HW + SW | 21/01 | 24/01 | 4 | D |
| F | Thiết kế pipeline AI ARX - Kalman - MPC | 25/01 | 05/02 | 12 | E |
| G | Lắp ráp phần cứng mạch, cảm biến, relay, Solar Tracking | 25/01 | 05/02 | 12 | E |
| H | Lập trình firmware ESP32 | 03/03 | 16/03 | 14 | G |
| I | Phát triển Backend Django + WebSocket Server | 17/03 | 01/04 | 16 | H |
| J | Phát triển Web Dashboard ReactJS | 02/04 | 15/04 | 14 | I |
| K | Huấn luyện mô hình ARX | 03/03 | 23/03 | 21 | F |
| L | Phát triển Kalman Filter | 24/03 | 06/04 | 14 | K |
| M | Phát triển MPC Controller | 07/04 | 20/04 | 14 | L |
| N | Tích hợp AI vào Web | 21/04 | 24/04 | 4 | J, M |
| O | Kiểm thử tích hợp chức năng | 25/04 | 02/05 | 8 | N |
| P | Hiệu chỉnh phần cứng và mô hình AI | 03/05 | 06/05 | 4 | O |
| Q | Hoàn thành báo cáo và bảo vệ đồ án | 07/05 | 10/05 | 4 | P |

Từ bảng phân công thời gian, nhóm có thể xây dựng sơ đồ GANTT để trực quan hóa tiến độ thực hiện dự án. Sơ đồ GANTT giúp nhóm theo dõi thứ tự công việc, các quan hệ phụ thuộc và các mốc cần hoàn thành đúng tiến độ.

Trên sơ đồ Gantt, khoảng trống từ 06/02/2026 đến 02/03/2026 thể hiện giai đoạn nghỉ Tết/nghỉ giữa tiến độ, không phải thiếu công việc trong lịch biểu.

![Hình 7. Gantt tổng quan theo tuần làm việc](image/Chuong05_LapLichBieu/gantt_ly_thuyet.png)

Hình 7. Gantt tổng quan theo tuần làm việc

Gantt thực tế được lập dựa trên quá trình triển khai dự án. So với kế hoạch ban đầu, các hoạt động L, M và N bị trễ hoặc dời lịch do cần xử lý Kalman Filter, tuning MPC và tích hợp AI vào Web. Để bảo đảm dự án vẫn kết thúc đúng ngày 10/05/2026, nhóm rút ngắn các hoạt động O và P ở giai đoạn kiểm thử, hiệu chỉnh.

![Hình 8. Gantt thực tế của dự án](image/Chuong05_LapLichBieu/gantt_thuc_te.png)

Hình 8. Gantt thực tế của dự án

## 5.5 Sơ đồ PDM

### 5.5.1 Thời gian dự trữ

Thời gian dự trữ (Slack/Float) là khoảng thời gian một hoạt động có thể bị trì hoãn mà không làm thay đổi ngày kết thúc dự án. Trong sơ đồ PDM, thời gian dự trữ được tính theo công thức:

Slack = LS - ES = LF - EF

Trong đó:

- ES (Earliest Start): thời điểm bắt đầu sớm nhất.
- EF (Earliest Finish): thời điểm kết thúc sớm nhất.
- LS (Latest Start): thời điểm bắt đầu muộn nhất mà không làm trễ dự án.
- LF (Latest Finish): thời điểm kết thúc muộn nhất mà không làm trễ dự án.

Nếu Slack = 0, hoạt động không có thời gian dự trữ. Nếu Slack > 0, hoạt động có thể trễ trong giới hạn Slack mà chưa làm thay đổi ngày kết thúc dự án.

| Hoạt động | ES | EF | LS | LF | Thời lượng | Slack | Nhận xét |
|-----------|----|----|----|----|------------|-------|----------|
| A | 0 | 4 | 0 | 4 | 4 | 0 | Không có dự trữ. |
| B | 4 | 8 | 4 | 8 | 4 | 0 | Không có dự trữ. |
| C | 8 | 12 | 8 | 12 | 4 | 0 | Không có dự trữ. |
| D | 12 | 16 | 12 | 16 | 4 | 0 | Không có dự trữ. |
| E | 16 | 20 | 16 | 20 | 4 | 0 | Không có dự trữ. |
| F | 20 | 32 | 20 | 32 | 12 | 0 | Không có dự trữ. |
| G | 20 | 32 | 25 | 37 | 12 | 5 | Có thể trễ tối đa 5 ngày. |
| H | 32 | 46 | 37 | 51 | 14 | 5 | Có thể trễ tối đa 5 ngày. |
| I | 46 | 62 | 51 | 67 | 16 | 5 | Có thể trễ tối đa 5 ngày. |
| J | 62 | 76 | 67 | 81 | 14 | 5 | Có thể trễ tối đa 5 ngày. |
| K | 32 | 53 | 32 | 53 | 21 | 0 | Không có dự trữ. |
| L | 53 | 67 | 53 | 67 | 14 | 0 | Không có dự trữ. |
| M | 67 | 81 | 67 | 81 | 14 | 0 | Không có dự trữ. |
| N | 81 | 85 | 81 | 85 | 4 | 0 | Không có dự trữ. |
| O | 85 | 93 | 85 | 93 | 8 | 0 | Không có dự trữ. |
| P | 93 | 97 | 93 | 97 | 4 | 0 | Không có dự trữ. |
| Q | 97 | 101 | 97 | 101 | 4 | 0 | Hoạt động cuối dự án, không có dự trữ. |

### 5.5.2 Sơ đồ PDM của dự án

Hình 9. Sơ đồ PDM của dự án
