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

### Bảng 17. Bảng phân bố nguồn nhân lực

| Mã | Hoạt động | Công việc trước đó | Thời lượng | Nhân lực | Nhân sự chính |
| :---: | --------- | :----------------: | :--------: | :------: | ------------- |
| A | Khảo sát giải pháp nhà kính thông minh hiện có | - | 4 ngày | 3 | Cả nhóm |
| B | Xác định yêu cầu, phạm vi và ràng buộc | A | 3 ngày | 3 | Cả nhóm |
| C | Thiết kế kiến trúc tổng thể HW + SW | B | 7 ngày | 2 | Sỹ, Trí |
| D | Thiết kế sơ đồ mạch điện | C | 3 ngày | 1 | Sỹ |
| E | Thiết kế giao thức WebSocket/JSON | D | 4 ngày | 1 | Sỹ |
| F | Thiết kế cơ sở dữ liệu và giao diện Web | C | 7 ngày | 1 | Sỹ |
| G | Thiết kế pipeline ARX - Kalman - MPC | C | 7 ngày | 2 | Trí, Sinh |
| H | Lắp ráp phần cứng | D | 7 ngày | 1 | Sỹ |
| I | Lập trình firmware ESP32 | H, E | 14 ngày | 1 | Sỹ |
| J | Phát triển Backend Django | F | 7 ngày | 1 | Sỹ |
| K | Phát triển WebSocket Server | J, E | 7 ngày | 1 | Sỹ |
| L | Huấn luyện mô hình ARX | G | 21 ngày | 1 | Trí |
| M | Phát triển Kalman Filter | L | 14 ngày | 1 | Sinh |
| N | Phát triển MPC Controller | M | 14 ngày | 1 | Sinh |
| O | Phát triển Web Dashboard | F, J, K | 14 ngày | 1 | Sỹ |
| P | Tích hợp AI vào Backend | K, N, O | 4 ngày | 3 | Cả nhóm |
| Q | Kiểm thử phần cứng và firmware | H, I | 4 ngày | 1 | Sỹ |
| R | Kiểm thử Backend/API/Database | J, K | 3 ngày | 1 | Sỹ |
| S | Kiểm thử Web Dashboard | O | 3 ngày | 1 | Sỹ |
| T | Kiểm thử mô hình AI/control | L, M, N | 3 ngày | 2 | Trí, Sinh |
| U | Kiểm thử tích hợp end-to-end và sửa lỗi | P, Q, R, S, T | 7 ngày | 3 | Cả nhóm |
| V | Triển khai demo hoàn chỉnh | U | 2 ngày | 1 | Sỹ |
| W | Viết báo cáo PBL và QLDA | U | 4 ngày | 2 | Trí, Sinh |
| X | Chuẩn bị slide thuyết trình và tổng duyệt | V, W | 2 ngày | 3 | Cả nhóm |

**Hình 8.** Sơ đồ phụ tải nguồn nhân lực
