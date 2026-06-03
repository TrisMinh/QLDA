# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 6: QUẢN LÝ NGUỒN NHÂN LỰC DỰ ÁN

## Mục tiêu trình bày

Trình bày cách nhóm phân công nhân lực, điều phối nguồn lực và theo dõi tải công việc.

## Kịch bản nói

Ở Chương 6, nhóm trình bày quản lý nguồn nhân lực.

Dự án có ba thành viên nên việc phân công phải rõ ràng để tránh chồng chéo. Thành viên A đảm nhiệm vai trò PM và mô hình ARX. Thành viên B phụ trách phần cứng, firmware ESP32, backend Django và Web Dashboard. Thành viên C phụ trách Kalman Filter, MPC Controller và tích hợp thuật toán điều khiển.

Trong quá trình điều phối, nhóm ưu tiên các công việc có thời gian dự trữ thấp và các công việc nằm trên đường găng. Điều này đặc biệt quan trọng với chuỗi AI, vì nếu Kalman hoặc MPC trễ thì tích hợp và kiểm thử cuối kỳ sẽ bị ảnh hưởng.

Sơ đồ phụ tải nguồn nhân lực cho thấy B có khối lượng lớn nhất vì kiêm cả phần cứng, firmware, backend và web. C tập trung mạnh hơn ở giai đoạn Kalman/MPC. A tham gia xuyên suốt với vai trò PM, ARX và hỗ trợ dữ liệu mô phỏng cho C khi MPC cần kiểm thử.

## Ý cần nhấn mạnh

- Vai trò ba thành viên được tách rõ.
- Điều phối dựa trên ưu tiên công việc quan trọng và ít dự trữ.
- Khi phát sinh trễ AI, nhóm tăng tải cho C và A/B hỗ trợ đúng phạm vi.

