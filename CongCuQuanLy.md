# CÁC CÔNG CỤ QUẢN LÝ

## 1. Mục đích sử dụng công cụ quản lý

Trong dự án Hệ thống Nhà kính Thông minh, nhóm sử dụng các công cụ quản lý nhằm tổ chức công việc, theo dõi tiến độ, quản lý mã nguồn và đảm bảo quá trình phối hợp giữa các thành viên được thống nhất. Do dự án gồm nhiều thành phần như phần cứng ESP32, firmware, backend Django, giao diện ReactJS và mô hình AI, việc sử dụng công cụ hỗ trợ giúp nhóm hạn chế bỏ sót nhiệm vụ, giảm xung đột mã nguồn và kiểm soát chất lượng trước khi tích hợp hệ thống.

Hai công cụ chính được sử dụng trong dự án là Trello để quản lý công việc và Git/GitHub để quản lý mã nguồn.

## 2. Quản lý công việc bằng Trello

### 2.1 Giới thiệu Trello

Trello là công cụ được nhóm sử dụng để quản lý công việc và theo dõi tiến độ trong quá trình thực hiện dự án. Thông qua Trello, các nhiệm vụ được tổ chức dưới dạng thẻ công việc và sắp xếp theo từng trạng thái khác nhau. Cách quản lý này giúp các thành viên dễ dàng theo dõi công việc cần làm, công việc đang thực hiện, công việc cần kiểm tra và công việc đã hoàn thành.

Việc sử dụng Trello giúp nhóm phân công nhiệm vụ rõ ràng, hạn chế bỏ sót công việc và thuận tiện trong quá trình cập nhật tiến độ. Mỗi thành viên có thể theo dõi nhiệm vụ của mình, đồng thời nhóm trưởng có thể kiểm soát tình hình thực hiện chung của dự án.

### 2.2 Cấu trúc Board Trello

Board Trello của dự án được tổ chức theo các danh sách công việc chính:

- To-do: Chứa các công việc sắp làm hoặc cần được thực hiện trong các giai đoạn tiếp theo của dự án.
- Doing: Chứa các công việc đang được thực hiện bởi các thành viên trong nhóm.
- Review: Chứa các công việc đã hoàn thành bước đầu và cần được nhóm kiểm tra, góp ý hoặc xác nhận lại.
- Done: Chứa các công việc đã hoàn thành, đã được kiểm tra và đạt yêu cầu.

### 2.3 Quy trình làm việc trên Trello

Quy trình làm việc của nhóm trên Trello được thực hiện theo từng trạng thái công việc. Ban đầu, các nhiệm vụ cần thực hiện được đưa vào To-do. Khi thành viên bắt đầu làm nhiệm vụ, thẻ công việc được chuyển sang Doing. Sau khi hoàn thành bước đầu, công việc được chuyển sang Review để nhóm kiểm tra lại nội dung, đánh giá kết quả và góp ý chỉnh sửa nếu cần. Nếu công việc đã đạt yêu cầu, thẻ được chuyển sang Done.

Nhờ quy trình này, nhóm có thể theo dõi trạng thái của từng nhiệm vụ, kiểm soát tiến độ thực hiện và đảm bảo các công việc được hoàn thành đúng kế hoạch.

Các mốc minh họa Trello Board trong dự án:

- Hình 2. Trello 13/01/2026
- Hình 3. Trello 18/03/2026
- Hình 4. Trello 22/04/2026
- Hình 5. Trello 10/05/2026

## 3. Quản lý mã nguồn bằng Git/GitHub

### 3.1 Mục đích quản lý mã nguồn

Git và GitHub được sử dụng để quản lý mã nguồn dự án nhằm lưu trữ lịch sử phát triển, hỗ trợ làm việc nhóm song song, hạn chế xung đột mã nguồn và kiểm soát chất lượng thông qua Pull Request, Code Review cũng như các bước kiểm thử tự động trước khi triển khai.

### 3.2 Tổng quan Repository trên GitHub

Repository chính thức của dự án được lưu trữ công khai trên nền tảng GitHub:

- Đường dẫn truy cập: https://github.com/BapTruongSinh/Green_House_PBL.git
- Trạng thái: Public
- Nhánh mặc định: main

Repository được thiết kế theo mô hình mono-repo để quản lý tập trung toàn bộ mã nguồn của hệ thống tại một nơi duy nhất, bao gồm firmware ESP32, backend Django, giao diện ReactJS, module AI và tài liệu liên quan.

Hình 9. Cấu trúc mã nguồn dự án

### 3.3 Chiến lược phân nhánh

Nhóm sử dụng cơ chế phân nhánh để phát triển song song các module mà không ảnh hưởng trực tiếp đến nhánh chính.

| Loại nhánh | Mục đích sử dụng | Ví dụ |
|------------|------------------|-------|
| feature/* | Phát triển chức năng mới theo WBS | feature/ai-mpc-controller |
| fix/* | Sửa lỗi phát hiện trong quá trình kiểm thử | fix/api-sensor-validation |
| test/* | Bổ sung unit test hoặc regression test | test/system-regression |
| docs/* | Cập nhật tài liệu kỹ thuật, báo cáo | docs/final-report |
| release/* | Chuẩn bị phiên bản nộp hoặc demo | release/v1.0-final |

Hình 10. Các nhánh của dự án

### 3.4 Quy tắc viết Commit Message

Nhóm thống nhất áp dụng cấu trúc commit message theo định dạng:

`<type>(<scope>): <mô tả ngắn bằng tiếng Anh>`

Trong đó, `type` phản ánh bản chất thay đổi như `feat`, `fix`, `docs`, `test`, `chore`, `refactor`; `scope` xác định module chịu ảnh hưởng như `hw`, `fw`, `backend`, `web`, `ai-arx`, `ai-kalman`, `ai-mpc`, `test`, `report`; phần mô tả được viết ngắn gọn, rõ nghĩa và ở thì hiện tại.

Hình 11. Một số commit tiêu biểu

### 3.5 Đánh giá việc sử dụng Git/GitHub

Việc sử dụng Git/GitHub giúp nhóm tách branch theo module, phát triển song song, truy vết thay đổi và sao lưu mã nguồn an toàn. Tuy nhiên, ở giai đoạn đầu nhóm gặp một số khó khăn do chênh lệch kỹ năng sử dụng Git, dẫn đến xung đột khi merge. Sau khi thống nhất quy trình làm việc và quy tắc commit, việc quản lý mã nguồn trở nên ổn định hơn.
