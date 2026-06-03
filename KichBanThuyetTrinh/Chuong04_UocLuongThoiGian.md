# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 4: ƯỚC LƯỢNG THỜI GIAN DỰ ÁN

## Mục tiêu trình bày

Giải thích cách nhóm ước lượng thời gian, giờ công và chi phí nhân lực dựa trên WBS.

## Kịch bản nói

Ở Chương 4, nhóm trình bày phần ước lượng thời gian dự án.

Sau khi có WBS, nhóm dùng các nhóm công việc đó để ước lượng thời lượng thực hiện. Phương pháp chính là PERT, trong đó mỗi nhóm công việc được đánh giá theo ba giá trị: thời gian lạc quan, thời gian khả dĩ nhất và thời gian bi quan. Công thức PERT giúp nhóm có một giá trị ước lượng cân bằng hơn, đặc biệt phù hợp với các phần có độ bất định cao như AI, Kalman Filter và MPC.

Ngoài thời gian theo ngày hoặc tuần, nhóm còn quy đổi công việc thành giờ công. Ở đây, giờ công không dùng để tính tiền lương thực tế, mà dùng để đánh giá khối lượng công sức, mức phân bổ công việc và khả năng quá tải của từng thành viên.

Trong thực tế, phần AI được đánh giá là nhóm có rủi ro thời gian cao nhất vì phụ thuộc vào dữ liệu, độ chính xác mô hình ARX, khả năng lọc nhiễu của Kalman và việc tuning MPC. Đây cũng là lý do trong các chương sau, khi AI bị trễ, nhóm có cơ sở giải thích vì sao phần này cần được theo dõi kỹ hơn.

## Ý cần nhấn mạnh

- Ước lượng dựa trên WBS.
- PERT phù hợp vì có nhiều phần chưa chắc chắn.
- Giờ công dùng để đánh giá effort, không phải lương thực tế.
- AI là nhóm có độ bất định cao nhất.

