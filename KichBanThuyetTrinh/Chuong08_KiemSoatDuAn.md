# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 8: KIỂM SOÁT DỰ ÁN

## Mục tiêu trình bày

Chương 8 cần trình bày rõ phần thực tế: dự án lệch ở đâu, vì sao lệch, nhóm phát hiện bằng cách nào, nhóm điều chỉnh ra sao, và vì sao cuối cùng vẫn đúng hạn.

## Mở đầu chương

Kính thưa thầy/cô và các bạn, Chương 8 là phần kiểm soát dự án. Nếu các chương trước nói về kế hoạch, thì chương này trả lời câu hỏi: khi làm thật, kế hoạch có chạy đúng không, nếu không đúng thì nhóm xử lý như thế nào?

Trong dự án này, nhóm không hoàn toàn đi đúng kế hoạch ở mọi công việc. Thực tế điểm trễ quan trọng nằm ở phát triển AI/control, đặc biệt là Kalman Filter, MPC Controller và tích hợp AI vào Web. Tuy nhiên, nhóm đã phát hiện sớm, điều chỉnh nhân lực và nén tiến độ ở giai đoạn cuối nên dự án vẫn hoàn thành đúng ngày 10/05/2026.

## 1. Nhóm kiểm soát dự án bằng những gì

Nhóm dùng bốn công cụ chính để kiểm soát:

- TimeSheet nhiệm vụ: so sánh kế hoạch và thực tế theo từng nhóm công việc.
- TimeSheet cá nhân: theo dõi giờ công của từng thành viên.
- Sai biệt lịch biểu và EVM: đo xem dự án đang nhanh hay chậm so với kế hoạch.
- Issue Log và Nhật ký thay đổi: ghi lại vấn đề thật sự xảy ra và cách xử lý.

Nhờ những công cụ này, nhóm không chỉ cảm nhận là "dự án đang chậm", mà có số liệu và bằng chứng cụ thể để ra quyết định.

## 2. Thực tế dự án bị lệch ở đâu

Trong TimeSheet nhiệm vụ, hầu hết các phần như phân tích yêu cầu, phần cứng, firmware, backend và web đều đúng tiến độ. Phần bị lệch chủ yếu nằm ở AI.

Sai lệch chính nằm ở **cụm L-M-N bị trễ/dời lịch**. Đây là phần ảnh hưởng trực tiếp đến cuối dự án:

- L - Kalman Filter kế hoạch kết thúc 06/04, thực tế kéo dài đến 09/04.
- M - MPC Controller kế hoạch 07/04-20/04, thực tế dời thành 10/04-27/04.
- N - Tích hợp AI vào Web kế hoạch 21/04-24/04, thực tế dời thành 28/04-01/05.

Vì N bị dời sát giai đoạn kiểm thử, nhóm buộc phải điều chỉnh các công việc cuối như O và P.

## 3. Vấn đề đường găng và thời gian dự trữ

Ở đây có một điểm rất quan trọng về lý thuyết đường găng.

Theo lý thuyết, công việc trên đường găng có Slack bằng 0, tức là không có thời gian dự trữ. Nếu một công việc trên đường găng bị trễ, ngày kết thúc dự án sẽ bị trễ theo nếu nhóm không điều chỉnh.

Vì vậy, nhóm không được hiểu là "lấy thời gian dự trữ của công việc khác bù cho công việc trên đường găng". Thời gian dự trữ không phải là quỹ thời gian chung để chuyển qua lại.

Cách hiểu đúng trong dự án này là:

- L-M-N bị trễ/dời sát giai đoạn cuối, nên tạo nguy cơ làm trễ toàn bộ dự án.
- Để giữ mốc cuối, nhóm phải dùng biện pháp nén tiến độ, không phải dùng float của công việc khác.

Nén tiến độ ở đây gồm hai cách:

- Crashing: tăng giờ làm, tăng nguồn lực cho phần đang chậm.
- Fast-tracking: sắp xếp một số hoạt động kiểm thử, tích hợp và hoàn thiện theo cách gọn hơn.

## 4. Nhóm đã điều chỉnh như thế nào

Khi phát hiện module MPC chậm, nhóm điều chỉnh theo vai trò thực tế của từng thành viên.

Thành viên C là người phụ trách Kalman Filter và MPC Controller, nên C tăng giờ làm trong tuần 9-10 để tập trung xử lý thuật toán.

Thành viên A phụ trách ARX và quản lý dự án, nên A hỗ trợ C bằng cách chuẩn bị dữ liệu mô phỏng từ mô hình ARX. Việc này giúp C kiểm thử MPC độc lập, không phải chờ dữ liệu thực từ phần cứng.

Thành viên B phụ trách phần cứng, firmware, backend và web, nên B hỗ trợ kiểm thử tích hợp giữa ESP32 và Backend/Web. Nhờ vậy C không phải chia thời gian quá nhiều cho phần tích hợp kỹ thuật.

Ở giai đoạn cuối, nhóm rút ngắn các hoạt động:

- O - kiểm thử tích hợp chức năng.
- P - hiệu chỉnh phần cứng và mô hình AI.

Việc rút ngắn này không có nghĩa là bỏ kiểm thử, mà là tập trung vào các chức năng chính, ưu tiên các ca kiểm thử quan trọng và giảm các phần phụ để giữ mốc bảo vệ.

## 5. Số liệu kiểm soát cho thấy điều gì

Trong bảng sai biệt lịch biểu:

- Phát triển AI có SV = -1, nghĩa là trễ 1 tuần.
- Kiểm thử có SV = +1, nghĩa là thực tế được rút ngắn hơn kế hoạch 1 tuần.
- Tổng dự án có SV = 0, nghĩa là dự án vẫn đúng thời gian tổng thể.

Trong EVM tại tuần 10, SPI = 0.93. Chỉ số này cho thấy dự án đang chậm khoảng 7% so với kế hoạch, chủ yếu do MPC. Đây là dấu hiệu để nhóm kích hoạt điều chỉnh, gồm tăng giờ C, A hỗ trợ dữ liệu ARX và B hỗ trợ kiểm thử tích hợp.

## 6. Issue Log và Nhật ký thay đổi

Issue Log ghi lại các vấn đề thật sự xảy ra. Vấn đề quan trọng nhất là VĐ02 - trễ tiến độ module MPC. Biện pháp xử lý là tăng giờ làm của C, A hỗ trợ dữ liệu mô phỏng ARX và B hỗ trợ kiểm thử tích hợp.

Nhật ký kiểm soát thay đổi ghi rõ các thay đổi trong lịch:

- L kéo dài đến 09/04.
- M dời sang 10/04-27/04.
- N dời sang 28/04-01/05.
- O và P được rút ngắn để bù tiến độ.
- Cảm biến DHT22 hỏng được thay bằng cảm biến dự phòng.

Điểm quan trọng là mỗi thay đổi đều có người chịu trách nhiệm và quyết định chấp nhận, chứ không phải thay đổi tùy tiện.

## 7. Kết quả cuối cùng

Sau khi điều chỉnh, dự án vẫn hoàn thành đúng 15 tuần, kết thúc ngày 10/05/2026.

Về chi phí, kế hoạch ban đầu là 1.200.000 VNĐ, thực tế là 1.371.000 VNĐ, vượt 14,25%. Tuy nhiên nhóm có quỹ dự phòng 255.000 VNĐ nên tổng chi phí vẫn nằm trong ngân sách dự trù.

Về chất lượng, mô hình ARX đạt FIT 85,85%, MPC giữ độ ẩm trong vùng mục tiêu 55-65%, Web Dashboard hoàn thành đủ các màn hình chính.

## Câu kết chương

Tóm lại, Chương 8 cho thấy dự án không phải lúc nào cũng chạy đúng kế hoạch. Nhóm đã có trễ thật, đặc biệt ở phần AI/MPC. Nhưng nhờ theo dõi bằng TimeSheet, EVM, Issue Log và Gantt thực tế, nhóm phát hiện sớm vấn đề, điều chỉnh nhân lực và nén tiến độ để giữ mốc cuối. Đây là phần thể hiện rõ nhất việc quản lý dự án trong thực tế.

## Gợi ý khi nói trên slide

- Đừng dùng mã hoạt động cũ như J/P/Q/R/T/U/V. Hãy nói theo bảng AC mới: L-M-N là cụm bị dời sát giai đoạn kiểm thử, còn O-P được rút ngắn để bù tiến độ.
- Nhấn mạnh: "Không lấy float của công việc khác để bù đường găng, mà nhóm dùng nén tiến độ."
- Khi nói giải pháp, trình bày đúng vai trò: C chính AI/MPC, A hỗ trợ dữ liệu ARX, B hỗ trợ tích hợp.
