# CHƯƠNG 8: QUẢN LÝ NGUỒN NHÂN LỰC DỰ ÁN

---

## 8.1. Nguồn nhân lực

Nguồn nhân lực là yếu tố quan trọng quyết định sự thành công của dự án. Đối với dự án Nhà kính thông minh, nguồn nhân lực bao gồm các thành viên tham gia vào quá trình phân tích, thiết kế, phát triển phần cứng, phần mềm, kiểm thử và triển khai hệ thống.

Việc phân công nhiệm vụ dựa trên năng lực chuyên môn giúp tối ưu hiệu quả làm việc, hạn chế chồng chéo trách nhiệm và hỗ trợ theo dõi tiến độ dự án.

### Bảng 16. Bảng phân công

| ID | Họ và tên          | Nhiệm vụ                                                                                                                  |
| -- | ------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| 1  | Hoàng Minh Trí     | - Tìm hiểu mô hình dự đoán<br>- Xây dựng dữ liệu mô phỏng<br>- Tiền xử lý dữ liệu<br>- Huấn luyện và đánh giá mô hình ARX |
| 2  | Đinh Công Trung Sỹ | - Phụ trách phần cứng và ESP32<br>- Lập trình firmware ESP32<br>- Điều khiển relay và WebSocket<br>- Xây dựng website     |
| 3  | Ngô Quang Sinh     | - Cài đặt Kalman Filter<br>- Xây dựng MPC Controller<br>- Tích hợp pipeline AI điều khiển thiết bị                        |

---

## 8.2. Một số quy tắc điều phối nguồn lực

* Ưu tiên công việc có thời gian dự trữ thấp nhất.
* Nếu thời gian dự trữ bằng nhau, ưu tiên công việc đang thực hiện.
* Nếu tiếp tục bằng nhau, ưu tiên công việc cần nhiều nguồn lực hơn.
* Nếu vẫn bằng nhau, ưu tiên công việc có mức sử dụng nguồn lực lớn hơn trong một đơn vị thời gian.

---

## 8.3. Sơ đồ phụ tải nguồn nhân lực

### Bảng 17. Bảng phân bố nguồn nhân lực (22 hoạt động)

| Mã | Hoạt động | Công việc trước đó | Thời lượng | Nhân lực | Nhân sự chính |
| :---: | --------- | :----------------: | :--------: | :------: | ------------- |
| **A** | Thiết kế sơ đồ kết nối cảm biến | - | 19 ngày | 1 | Sỹ |
| **B** | Lắp ráp & đấu nối cảm biến | A | 7 ngày | 1 | Sỹ |
| **C** | Kiểm thử cảm biến | H | 4 ngày | 1 | Sỹ |
| **D** | Lắp ráp relay & actuator | A | 7 ngày | 1 | Sỹ |
| **E** | Xây dựng khung nhà kính | A | 7 ngày | 2 | Trí, Sỹ |
| **F** | Lắp ráp Solar Tracking | A | 7 ngày | 1 | Sỹ |
| **G** | Kiểm thử Solar Tracking | F | 3 ngày | 1 | Sỹ |
| **H** | Lập trình đọc cảm biến | B | 7 ngày | 1 | Sỹ |
| **I** | Lập trình WebSocket Client | H | 7 ngày | 1 | Sỹ |
| **J** | Lập trình điều khiển relay | D, H | 7 ngày | 1 | Sỹ |
| **K** | Phát triển API & Database | A | 14 ngày | 1 | Sỹ |
| **L** | Phát triển WebSocket Server | K | 7 ngày | 1 | Sỹ |
| **M** | Thu thập dữ liệu ARX | A | 7 ngày | 1 | Trí |
| **N** | Huấn luyện ARX | M | 21 ngày | 1 | Trí |
| **O** | Phát triển Kalman Filter | N | 14 ngày | 1 | Sinh |
| **P** | Phát triển MPC Controller | O | 14 ngày | 1 | Sinh |
| **Q** | Giao diện giám sát | K | 7 ngày | 1 | Sỹ |
| **R** | Giao diện điều khiển | Q | 7 ngày | 1 | Sỹ |
| **S** | Kiểm thử HW & FW | C, G, I, J | 7 ngày | 1 | Sỹ |
| **T** | Kiểm thử BE, Web & AI | L, R, P | 7 ngày | 3 | Trí, Sỹ, Sinh |
| **U** | Hiệu chỉnh hệ thống | S, T | 7 ngày | 3 | Trí, Sỹ, Sinh |
| **V** | Báo cáo & bảo vệ | U | 6 ngày | 3 | Trí, Sỹ, Sinh |

**Hình 8.** Sơ đồ phụ tải nguồn nhân lực
