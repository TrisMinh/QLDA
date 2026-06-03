# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 3: LIỆT KÊ CÔNG VIỆC DỰ ÁN (WBS)

## Mục tiêu trình bày

Giải thích cách nhóm phân rã dự án thành sản phẩm, công việc và các work package để quản lý tiến độ, nhân lực và rủi ro.

## Kịch bản nói

Ở Chương 3, nhóm trình bày WBS, tức là cấu trúc phân rã công việc của dự án.

WBS được dùng để biến một dự án lớn thành các phần nhỏ hơn, rõ ràng hơn và có thể quản lý được. Với đề tài nhà kính thông minh, nếu chỉ nói chung là "làm hệ thống IoT + AI" thì rất khó phân công và theo dõi. Vì vậy nhóm chia dự án theo hai hướng: PBS là phân rã sản phẩm, và TBS là phân rã công việc.

Về PBS, nhóm xác định sản phẩm tổng là Hệ thống Nhà kính Thông minh. Sản phẩm này được chia thành năm nhóm: phần cứng, firmware, backend + AI, web dashboard và kiểm thử/hoàn thành. Trong đó phần cứng gồm cảm biến, relay, actuator, mô hình nhà kính và Solar Tracking; backend + AI gồm Django Server, WebSocket, ARX, Kalman Filter và MPC Controller; Web Dashboard gồm màn hình giám sát và điều khiển.

Về TBS, nhóm chia công việc thành năm nhóm lớn: phân tích yêu cầu, thiết kế, phát triển, kiểm thử và hoàn thành. Từ đó nhóm tiếp tục phân rã thành các công việc cụ thể như khảo sát giải pháp, xác định yêu cầu, thiết kế mạch, thiết kế WebSocket/JSON, thiết kế database, lập trình firmware ESP32, phát triển backend, web, huấn luyện ARX, phát triển Kalman Filter, MPC Controller và kiểm thử end-to-end.

Điểm quan trọng của WBS trong thực tế là nó trở thành nền để lập bảng hoạt động, ước lượng thời gian, lập Gantt, phân công nhân lực và nhận diện rủi ro. Ví dụ, trong WBS có nhóm T3.5 đến T3.8 là phát triển AI. Sau này khi module AI bị trễ, nhóm có thể xác định rõ phần bị ảnh hưởng là Kalman/MPC và tích hợp AI vào backend, thay vì nói chung chung là "dự án bị trễ".

Trong quá trình làm, WBS cũng được cập nhật theo thay đổi thực tế. Ví dụ nhóm bổ sung Kalman Filter khi phát hiện dữ liệu cảm biến có nhiễu, và điều này được ghi nhận trong phần kiểm soát phiên bản WBS. Nhờ vậy, WBS không chỉ là bảng lý thuyết mà còn là công cụ giúp nhóm theo dõi phạm vi và kiểm soát thay đổi.

## Điểm cần trình bày trên slide

- WBS = PBS + TBS.
- PBS: phần cứng, firmware, backend + AI, web dashboard, kiểm thử.
- TBS: phân tích, thiết kế, phát triển, kiểm thử, hoàn thành.
- Work package quan trọng: ARX, Kalman Filter, MPC Controller, tích hợp AI.
- WBS là cơ sở cho Gantt, phân công nhân lực, kiểm soát rủi ro và kiểm soát thay đổi.

## Câu kết chương

Tóm lại, WBS giúp nhóm chuyển một đề tài phức tạp thành các phần việc cụ thể, có mã rõ ràng, có thể ước lượng, phân công và theo dõi trong suốt dự án.

