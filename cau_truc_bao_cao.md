# 📋 CẤU TRÚC BÁO CÁO CUỐI KỲ - QUẢN LÝ DỰ ÁN PHẦN MỀM

## Đề tài: HỆ THỐNG NHÀ KÍNH THÔNG MINH (Smart Greenhouse)

---

> [!NOTE]
> Báo cáo gồm **10 chương** tương ứng với 10 nội dung môn học. Mỗi chương áp dụng lý thuyết vào đề tài PBL Nhà kính thông minh.

---

## 📖 MỤC LỤC TỔNG QUAN

| STT | Chương | Nội dung chính |
|:---:|--------|----------------|
| 01 | Tổng quan dự án | Giới thiệu, mục đích, mục tiêu, phạm vi, ràng buộc |
| 02 | Xác định dự án | Phác thảo dự án, vai trò & trách nhiệm, các bên liên quan |
| 03 | Liệt kê công việc dự án (WBS) | PBS, TBS, bảng WBS chi tiết |
| 04 | Trello | Quản lý công việc bằng Trello, cấu trúc board, quy trình |
| 05 | Ước lượng thời gian dự án | PERT, GEF, man-month, bảng ước lượng |
| 06 | Lập lịch biểu cho dự án | Sơ đồ PDM/AON, đường găng, sơ đồ Gantt |
| 07 | Git | Quản lý mã nguồn, branching, quy trình làm việc nhóm |
| 08 | Quản lý nguồn nhân lực | Phân công, biểu đồ phụ tải, điều phối nhân lực |
| 09 | Quản lý rủi ro dự án | Nhận diện, phân loại, bảng quản lý rủi ro |
| 10 | Kiểm soát dự án | Giám sát tiến độ, kiểm soát thay đổi, kết thúc dự án |

---

## CHƯƠNG 1: TỔNG QUAN DỰ ÁN

### 1.1 Giới thiệu đề tài
- 1.1.1 Tên dự án
- 1.1.2 Mô tả tổng quát dự án
- 1.1.3 Bối cảnh thực hiện *(môn học, nhóm PBL, thời gian thực hiện)*
- 1.1.4 Lý do chọn đề tài *(tại sao chọn nhà kính thông minh)*

### 1.2 Mục đích dự án (Goals)
- 1.2.1 Mục đích tổng quát *(mô tả cái dự án sẽ đạt tới — mang tính định tính)*
- 1.2.2 Ý nghĩa thực tiễn *(giá trị mang lại cho nông nghiệp, người dùng)*

### 1.3 Mục tiêu dự án (Objectives)
- 1.3.1 Các mục tiêu cụ thể *(tập hợp con có thể đo được của mục đích)*
- 1.3.2 Các chức năng cần đạt *(giám sát nhiệt độ, độ ẩm, điều khiển quạt/bơm...)*
- 1.3.3 Các chỉ tiêu đánh giá *(tiêu chí đo lường mức hoàn thành)*

### 1.4 Phạm vi dự án
- 1.4.1 Phạm vi chức năng *(các tính năng nằm trong phạm vi)*
- 1.4.2 Phạm vi kỹ thuật *(công nghệ sử dụng: Arduino, cảm biến, WebSocket, Web dashboard...)*
- 1.4.3 Phạm vi người dùng *(đối tượng sử dụng hệ thống)*
- 1.4.4 Những gì ngoài phạm vi dự án *(các tính năng KHÔNG làm)*

### 1.5 Các bên liên quan (Stakeholders)
- Khách hàng
- Nhà tài trợ
- Nhóm phát triển
- Quản lý dự án (PM)
- Người dùng cuối

### 1.6 Ràng buộc dự án
- 1.6.1 Ràng buộc về thời gian
- 1.6.2 Ràng buộc về chi phí
- 1.6.3 Ràng buộc về nhân lực
- 1.6.4 Ràng buộc về công nghệ
- 1.6.5 Ràng buộc về thiết bị

### 1.7 Rủi ro tổng quát ban đầu
- Thiếu nhân lực / thiếu kinh nghiệm
- Thay đổi yêu cầu
- Trễ tiến độ
- Lỗi kỹ thuật (phần cứng, phần mềm)

### 1.8 Phương pháp phát triển phần mềm
- 1.8.1 Giới thiệu Waterfall
- 1.8.2 Giới thiệu Agile/Scrum
- 1.8.3 Lý do lựa chọn mô hình cho dự án

---

## CHƯƠNG 2: XÁC ĐỊNH DỰ ÁN

### 2.1 Xác định mục đích và mục tiêu dự án
- 2.1.1 Mối quan hệ giữa mục đích và mục tiêu *(mục tiêu là chi tiết cụ thể, đo được của mục đích)*
- 2.1.2 Bảng mục đích – mục tiêu dự án nhà kính thông minh

### 2.2 Tài liệu phác thảo dự án (Statement of Work)
- 2.2.1 Mục đích và mục tiêu
- 2.2.2 Phạm vi dự án
- 2.2.3 Kết quả chuyển giao (Deliverables)
- 2.2.4 Các mốc quan trọng (Milestones)
- 2.2.5 Ước lượng sơ bộ (thời gian, chi phí)
- 2.2.6 Chữ ký các bên liên quan

### 2.3 Xác định vai trò và trách nhiệm trong dự án
- 2.3.1 Quản lý dự án (PM) — vai trò & trách nhiệm
- 2.3.2 Nhóm phát triển — vai trò & trách nhiệm từng thành viên
- 2.3.3 Khách hàng / Giảng viên — vai trò & trách nhiệm
- 2.3.4 Ma trận RACI *(Responsible, Accountable, Consulted, Informed)*

---

## CHƯƠNG 3: LIỆT KÊ CÔNG VIỆC DỰ ÁN (WBS)

### 3.1 Tổng quan về WBS
- 3.1.1 Khái niệm WBS (Work Breakdown Structure)
- 3.1.2 Các tính chất của WBS *(phân cấp, mô tả "cái gì" chứ không phải "như thế nào")*
- 3.1.3 Cấu trúc WBS: PBS + TBS

### 3.2 Danh sách sản phẩm (PBS - Product Breakdown Structure)
- 3.2.1 Sản phẩm tổng: Hệ thống nhà kính thông minh
- 3.2.2 Sản phẩm con cấp 1 *(Phần cứng, Phần mềm nhúng, Web Dashboard, Tài liệu)*
- 3.2.3 Sản phẩm con cấp 2 *(Chi tiết từng module)*

### 3.3 Danh sách công việc (TBS - Task Breakdown Structure)
- 3.3.1 Các công việc tổng
- 3.3.2 Các công việc con chi tiết *(phân tích, thiết kế, lập trình, kiểm thử...)*
- 3.3.3 Mã hóa WBS *(đánh số duy nhất cho từng ô)*

### 3.4 Bảng WBS hoàn chỉnh
- 3.4.1 Sơ đồ WBS dạng cây
- 3.4.2 Bảng WBS dạng bảng *(STT, Mã, Tên công việc, Mô tả, Mức)*

### 3.5 Tiêu chuẩn WBS tốt
- Mọi nhánh chi tiết đến mức thấp nhất
- Mọi ô đánh mã duy nhất
- Đã được phản hồi và chấp thuận

---

## CHƯƠNG 4: TRELLO

### 4.1 Giới thiệu Trello
- 4.1.1 Trello là gì?
- 4.1.2 Lý do sử dụng Trello trong dự án

### 4.2 Cấu trúc Trello Board của dự án
- 4.2.1 Các danh sách (Lists) *(Backlog, To Do, In Progress, Review, Done)*
- 4.2.2 Các thẻ công việc (Cards) *(mô tả, checklist, deadline, thành viên)*
- 4.2.3 Labels & Tags *(phân loại: Hardware, Software, Testing, Documentation)*

### 4.3 Quy trình làm việc trên Trello
- 4.3.1 Quy trình di chuyển card qua các cột
- 4.3.2 Phân công thành viên cho từng card
- 4.3.3 Theo dõi tiến độ và deadline

### 4.4 Minh họa Trello Board
- *(Ảnh chụp Trello Board thực tế của nhóm)*

---

## CHƯƠNG 5: ƯỚC LƯỢNG THỜI GIAN DỰ ÁN

### 5.1 Tổng quan về ước lượng
- 5.1.1 Khái niệm ước lượng
- 5.1.2 Các tính chất của ước lượng *(quá trình lặp, cần hiệu chỉnh dần)*
- 5.1.3 Những trở ngại khi ước lượng
- 5.1.4 Những lưu ý khi ước lượng

### 5.2 Các kỹ thuật ước lượng
- 5.2.1 Ước lượng theo kinh nghiệm
- 5.2.2 Ước lượng theo lịch sử
- 5.2.3 Ước lượng theo công thức PERT *(MO, ML, MP → TE = (MO + 4×ML + MP) / 6)*
- 5.2.4 Ước lượng theo năng suất toàn cục GEF *(GEF = 100% - tổng% khiếm khuyết)*
- 5.2.5 Ước lượng chi phí nhân lực (man-month)

### 5.3 Bảng ước lượng thời gian dự án nhà kính thông minh
- 5.3.1 Bảng ước lượng PERT cho từng công việc *(MO, ML, MP, TE)*
- 5.3.2 Tính GEF cho dự án
- 5.3.3 Bảng tổng hợp thời gian ước lượng

### 5.4 Các bước thực hiện ước lượng
- Dựa trên WBS → Lập ước lượng → Họp chung → Hiệu chỉnh

---

## CHƯƠNG 6: LẬP LỊCH BIỂU CHO DỰ ÁN

### 6.1 Tổng quan về lập lịch biểu
- 6.1.1 Tại sao cần lập lịch biểu *(WBS + ước lượng chưa đủ, cần lịch biểu)*
- 6.1.2 Các quan hệ phụ thuộc giữa công việc (Predecessor)
- 6.1.3 Các loại sơ đồ: ADM (AOA), PDM (AON), Gantt

### 6.2 Sơ đồ mạng PDM (Precedence Diagramming Method)
- 6.2.1 Giới thiệu sơ đồ PDM / AON
- 6.2.2 Các thông tin trong mỗi nút *(ES, EF, LS, LF, Duration)*
- 6.2.3 Tính toán tiến (Forward Pass): ES, EF
- 6.2.4 Tính toán lùi (Backward Pass): LS, LF
- 6.2.5 Sơ đồ PDM của dự án nhà kính thông minh

### 6.3 Đường găng (Critical Path)
- 6.3.1 Khái niệm đường găng
- 6.3.2 Xác định đường găng cho dự án
- 6.3.3 Ý nghĩa: công việc trên đường găng bị trễ → toàn dự án trễ

### 6.4 Độ thả nổi (Float / Slack)
- 6.4.1 Độ thả nổi tự do (Free Float): FF = ES(kế) - EF - 1
- 6.4.2 Độ thả nổi toàn bộ (Total Float): TF = LS - ES
- 6.4.3 Bảng tính float cho từng công việc

### 6.5 Sơ đồ Gantt
- 6.5.1 Giới thiệu sơ đồ Gantt
- 6.5.2 Đặc điểm sơ đồ Gantt *(trực quan, dễ theo dõi, dễ báo cáo)*
- 6.5.3 Sơ đồ Gantt của dự án nhà kính thông minh
- 6.5.4 Sơ đồ Gantt sau khi rút ngắn / điều chỉnh *(nếu có)*

---

## CHƯƠNG 7: GIT

### 7.1 Giới thiệu Git & GitHub
- 7.1.1 Git là gì?
- 7.1.2 GitHub là gì?
- 7.1.3 Lý do sử dụng Git trong dự án

### 7.2 Cấu trúc Repository của dự án
- 7.2.1 Cấu trúc thư mục *(firmware/, web-dashboard/, docs/...)*
- 7.2.2 File README.md
- 7.2.3 File .gitignore

### 7.3 Quy trình làm việc với Git (Git Workflow)
- 7.3.1 Branching strategy *(main, develop, feature branches)*
- 7.3.2 Quy trình commit & push
- 7.3.3 Pull Request & Code Review
- 7.3.4 Merge & Conflict Resolution

### 7.4 Minh họa Git
- *(Ảnh chụp lịch sử commit, network graph, pull requests)*

---

## CHƯƠNG 8: QUẢN LÝ NGUỒN NHÂN LỰC

### 8.1 Tổng quan về quản lý nguồn nhân lực
- 8.1.1 Tầm quan trọng của quản lý nhân lực
- 8.1.2 Các quy tắc điều phối nguồn lực *(ưu tiên công việc ít dự trữ, nhiều nhân lực, đường găng)*

### 8.2 Phân công công việc
- 8.2.1 Nguyên tắc phân công *(phù hợp kiến thức, kỹ năng, kinh nghiệm)*
- 8.2.2 Bảng phân công công việc chi tiết cho 3 thành viên
- 8.2.3 Ma trận trách nhiệm (Responsibility Matrix)

### 8.3 Biểu đồ phụ tải nhân lực
- 8.3.1 Khái niệm biểu đồ phụ tải *(nhu cầu nhân lực theo thời gian)*
- 8.3.2 Biểu đồ phụ tải cho từng thành viên / từng vị trí
- 8.3.3 Đánh giá: biểu đồ có tương đối bằng phẳng không?

### 8.4 Điều phối nhân lực
- 8.4.1 Các phương pháp điều phối *(tăng lag, chuyển nối tiếp, tận dụng thả nổi)*
- 8.4.2 Kết quả điều phối nhân lực cho dự án
- 8.4.3 Cân nhắc chi phí – chất lượng – thời gian

---

## CHƯƠNG 9: QUẢN LÝ RỦI RO DỰ ÁN

### 9.1 Tổng quan về quản lý rủi ro
- 9.1.1 Khái niệm rủi ro *(sự kiện cản trở mục tiêu dự án)*
- 9.1.2 Tính chất của rủi ro *(mọi dự án đều có rủi ro)*
- 9.1.3 Mục tiêu quản lý rủi ro *(ngăn chặn, giảm thiểu tổn thất)*

### 9.2 Các bước quản lý rủi ro
- 9.2.1 Bước 1: Dự đoán / nhận diện rủi ro *(dựa lịch sử, brainstorm)*
- 9.2.2 Bước 2: Khử bỏ rủi ro nếu được
- 9.2.3 Bước 3: Giảm bớt nguyên nhân rủi ro
- 9.2.4 Bước 4: Lập kế hoạch dự phòng

### 9.3 Phân loại rủi ro
- 9.3.1 Các tình huống rủi ro thường gặp *(nhân viên không làm được việc, yêu cầu không tốt, giải pháp sai...)*
- 9.3.2 Bảng phân loại độ rủi ro *(Xác suất × Tác động → Mức độ: Thấp/Vừa/Cao/Rất cao)*

### 9.4 Bảng quản lý rủi ro dự án nhà kính thông minh
- 9.4.1 Bảng nhận diện rủi ro *(Khoản mục, Mô tả, Xác suất, Tác động, Độ rủi ro)*
- 9.4.2 Kế hoạch ứng phó cho từng rủi ro
- 9.4.3 Kinh phí dự phòng

### 9.5 Lưu ý trong quản lý rủi ro
- Dự báo phụ thuộc kinh nghiệm PM
- Thiệt hại phải được lưu thành tài liệu

---

## CHƯƠNG 10: KIỂM SOÁT DỰ ÁN

### 10.1 Thu thập và đánh giá hiện trạng
- 10.1.1 Mục đích thu thập hiện trạng *(xác định mức độ tiến triển)*
- 10.1.2 Time sheet nhiệm vụ & Time sheet cá nhân
- 10.1.3 Phân tích sai biệt *(sai biệt lịch biểu, sai biệt chi phí)*

### 10.2 Họp
- 10.2.1 Họp định kỳ *(tần suất, nội dung)*
- 10.2.2 Họp đột xuất
- 10.2.3 Nguyên tắc họp hiệu quả *(thông báo trước, có chương trình, không quá dài)*
- 10.2.4 Biên bản họp nhóm *(minh họa các buổi họp thực tế)*

### 10.3 Điều chỉnh
- 10.3.1 Khi dự án không đúng lịch biểu *(thêm người, mua thiết bị tốt hơn, cải tiến cách làm việc)*
- 10.3.2 Khi chi phí có nguy cơ tăng *(cắt giảm, dùng thiết bị giá thấp)*
- 10.3.3 Khi chất lượng có nguy cơ giảm *(tăng kiểm tra, kiểm tra chéo, đào tạo)*

### 10.4 Kiểm soát thay đổi
- 10.4.1 Nguồn gốc thay đổi *(khách hàng, nhà tài trợ, nhóm phát triển)*
- 10.4.2 Phân loại thay đổi *(quan trọng, ít quan trọng, bổ sung)*
- 10.4.3 Thủ tục kiểm soát thay đổi *(ghi nhận → phân tích → phê duyệt → thực hiện)*
- 10.4.4 Nhật ký kiểm soát thay đổi

### 10.5 Lập kế hoạch lại (nếu có)
- 10.5.1 Khi nào cần lập kế hoạch lại
- 10.5.2 Quy trình tái cấu trúc kế hoạch

### 10.6 Kết thúc dự án
- 10.6.1 Các lý do kết thúc *(hoàn thành mục tiêu, hết kinh phí, hết thời gian)*
- 10.6.2 Thống kê số liệu *(chi phí, thời gian, chất lượng)*
- 10.6.3 So sánh kế hoạch vs thực tế
- 10.6.4 Bài học kinh nghiệm (Lessons Learned)
- 10.6.5 Lưu trữ hồ sơ dự án

### 10.7 Kỹ năng mềm trong quản lý dự án
- 10.7.1 Giao tiếp
- 10.7.2 Tổ chức
- 10.7.3 Xử lý tình huống

---

## PHỤ LỤC

### Phụ lục A: Các biểu mẫu sử dụng trong dự án
- Biểu mẫu phác thảo dự án
- Biểu mẫu báo cáo tiến độ
- Biểu mẫu kiểm soát thay đổi
- Biểu mẫu quản lý rủi ro

### Phụ lục B: Ảnh chụp minh họa
- Ảnh Trello Board
- Ảnh GitHub Repository
- Ảnh hệ thống phần cứng nhà kính
- Ảnh Web Dashboard

### Phụ lục C: Tài liệu tham khảo

---

> [!IMPORTANT]
> **Lưu ý quan trọng:**
> - Mỗi chương phải **áp dụng cụ thể** vào đề tài Nhà kính thông minh, không chỉ copy lý thuyết
> - Cần có **bảng biểu, sơ đồ, hình minh họa** ở mỗi chương
> - Chương 4 (Trello) và Chương 7 (Git) là công cụ thực tế → cần **ảnh chụp màn hình** thực tế của nhóm
> - Chương 6 (Lập lịch biểu) là chương nặng nhất → cần vẽ đầy đủ PDM, đường găng, Gantt
