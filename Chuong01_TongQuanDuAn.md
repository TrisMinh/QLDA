# CHƯƠNG 1: TỔNG QUAN DỰ ÁN

## Giới thiệu đề tài

Trong bối cảnh nông nghiệp hiện đại, việc giám sát và điều khiển môi trường canh tác ngày càng đòi hỏi tính tự động hóa cao. Các hệ thống nhà kính thương mại hiện tại chủ yếu hoạt động theo ngưỡng cứng, chưa tích hợp mô hình dự đoán hay điều khiển tối ưu. Từ đó, nhóm đề xuất đề tài “Hệ thống Nhà kính Thông minh — Smart Greenhouse” nhằm xây dựng giải pháp giám sát và điều khiển môi trường nhà kính dựa trên IoT kết hợp trí tuệ nhân tạo.

Hệ thống giám sát các thông số môi trường (nhiệt độ, độ ẩm, ánh sáng, độ ẩm đất) và điều khiển tự động các thiết bị chấp hành (bơm, quạt, phun sương, đèn LED). Kiến trúc gồm bốn thành phần: phần cứng ESP32 với cảm biến và relay; firmware nhúng giao tiếp WebSocket; backend Django tích hợp mô hình dự đoán ARX, bộ lọc Kalman thích nghi và bộ điều khiển MPC; và giao diện Web Dashboard trên ReactJS.

Mô tả tổng quan dự án

| Hạng mục | Chi tiết |
| --- | --- |
| Tên dự án | Hệ thống Nhà kính Thông minh (Smart Greenhouse) |
| Nhóm phát triển | 3 thành viên |
| Khách hàng | Thầy Huỳnh Hữu Hưng |
| Lĩnh vực | Nông nghiệp thông minh |
| Công nghệ sử dụng | ESP32, Django, ReactJS, WebSocket, ARX, Kalman, MPC |
| Quản lý dự án | Hoàng Minh Trí |
| Thời gian thực hiện | 15 tuần |
| Kinh phí dự án | ~1.200.000 VNĐ |

## Kế hoạch triển khai

Dự án triển khai từ ngày 31/12/2025 đến ngày 10/05/2026, cụ thể như sau:

Từ ngày 31/12/2025 đến ngày 05/01/2026: các sinh viên tổ chức thành nhóm để làm đồ án, giảng viên đề xuất các hướng nghiên cứu quan tâm và giới thiệu với sinh viên.

Từ ngày 05/01/2026 đến ngày 21/01/2026: Thống nhất đề tài triển khai, lý thuyết

Từ ngày 21/01/2026 đến ngày 12/04/2026: Thực hiện đề tài.

Từ ngày 12/04/2026 đến ngày 10/05/2026: Nhóm SV làm dự án liên tục để hoàn thành dưới sự giám sát của giảng viên hướng dẫn, xét duyệt và kiểm tra thành quả.

## Cách triển khai đồ án

Nhóm triển khai dự án Smart Greenhouse theo trình tự từ phân tích đề tài, xác định công việc, phân chia nhiệm vụ đến lập lịch thực hiện. Cách triển khai cụ thể như sau:

Phân tích đề tài, xác định mục tiêu, phạm vi và các yêu cầu chính của hệ thống.

Xác định các nhóm công việc cần thực hiện trong đồ án, bao gồm phần cứng, phần mềm, thuật toán, kiểm thử và báo cáo.

Phân chia công việc cho từng thành viên dựa trên vai trò, năng lực và khối lượng công việc.

Lập kế hoạch thời gian, xác định thứ tự thực hiện, các mốc kiểm tra tiến độ và thời hạn hoàn thành.

Theo dõi quá trình thực hiện, điều chỉnh kế hoạch khi cần thiết và tổng hợp kết quả để hoàn thiện đồ án.

## 1.4 Đánh giá kết quả thực hiện đồ án

Kết quả thực tế của dự án Smart Greenhouse

Đánh giá kết quả thực hiện

| Tiêu chí | Mục tiêu | Kết quả | Đánh giá |
| --- | --- | --- | --- |
| Thời gian | 15 tuần | 15 tuần | Đúng hạn |
| Chi phí | 1.200.000 VNĐ | 1.371.000 VNĐ | Vượt 14.25% |
| FIT 1-step ARX | ≥ 80% | 85,85% | Vượt mục tiêu |
| MPC vùng mục tiêu | 55–65% | Đạt | Đạt |
| Web | Đầy đủ chức năng theo dõi chỉ số | Đầy đủ | Đạt |
