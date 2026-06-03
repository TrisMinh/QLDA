# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 5: LẬP LỊCH BIỂU CHO DỰ ÁN

## Mục tiêu trình bày

Trình bày bảng hoạt động, quan hệ phụ thuộc, Gantt kế hoạch, Gantt thực tế và cách nhóm bù tiến độ.

## Kịch bản nói

Ở Chương 5, nhóm trình bày cách lập lịch biểu cho dự án dựa trên WBS và ước lượng thời gian.

Đầu tiên, nhóm xây dựng bảng hoạt động từ A đến Q. Mỗi hoạt động có mã, thời gian bắt đầu, thời gian kết thúc, thời lượng và công việc trước đó. Ví dụ, B phụ thuộc A, C phụ thuộc B, D phụ thuộc C; sau thiết kế tổng thể E, nhóm có F là thiết kế pipeline AI và G là lắp ráp phần cứng. Sau giai đoạn nghỉ Tết từ 06/02 đến 02/03, nhóm tiếp tục với firmware, backend, web và AI.

Trên Gantt kế hoạch, các công việc được bố trí từ 05/01 đến 10/05. Chuỗi AI là một chuỗi quan trọng vì gồm thiết kế pipeline AI, huấn luyện ARX, Kalman Filter, MPC Controller và tích hợp AI vào Web. Nếu chuỗi này trễ, các bước kiểm thử và hiệu chỉnh cuối dự án sẽ bị ảnh hưởng.

Khi thực hiện thực tế, phần lớn công việc như phân tích yêu cầu, phần cứng, firmware, backend và web hoàn thành đúng tiến độ. Điểm trễ chính nằm ở cụm AI/control: hoạt động L - Kalman Filter kéo dài đến 09/04, hoạt động M - MPC Controller dời sang 10/04-27/04 và hoạt động N - tích hợp AI vào Web dời sang 28/04-01/05.

Để bù tiến độ, nhóm tăng giờ làm của thành viên C phụ trách Kalman/MPC, thành viên A hỗ trợ dữ liệu mô phỏng từ ARX để C kiểm thử MPC độc lập, và thành viên B hỗ trợ kiểm thử tích hợp ESP32 với Backend/Web. Ở giai đoạn cuối, các hoạt động O và P được rút ngắn để dự án vẫn kết thúc đúng ngày 10/05.

## Ý cần nhấn mạnh

- Gantt kế hoạch dùng để xác định tiến độ ban đầu.
- Gantt thực tế cho thấy L, M, N bị trễ/dời.
- Nhóm bù tiến độ bằng tăng giờ C, A hỗ trợ dữ liệu ARX, B hỗ trợ tích hợp, rút ngắn kiểm thử cuối.
- Kết quả: dự án vẫn đúng hạn 10/05/2026.
