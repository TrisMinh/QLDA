# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 7: QUẢN LÝ RỦI RO DỰ ÁN

## Mục tiêu trình bày

Chương này không chỉ nói "rủi ro là gì", mà cần làm rõ nhóm đã dự đoán rủi ro như thế nào, rủi ro nào thật sự xảy ra, và nhóm xử lý ra sao để dự án không bị vỡ tiến độ.

## Mở đầu chương

Kính thưa thầy/cô và các bạn, ở Chương 7 nhóm trình bày phần quản lý rủi ro của dự án Nhà kính thông minh.

Với nhóm, quản lý rủi ro không phải là lập một bảng cho đủ nội dung báo cáo. Mục đích chính là nhìn trước những vấn đề có khả năng xảy ra, chuẩn bị phương án xử lý, và khi sự cố thật sự xuất hiện thì nhóm không bị động.

Trong dự án này, nhóm có nhiều thành phần kỹ thuật liên kết với nhau: phần cứng ESP32, firmware, backend Django, web ReactJS và AI gồm ARX, Kalman Filter, MPC. Vì vậy chỉ cần một module trễ hoặc lỗi, các bước tích hợp và kiểm thử cuối kỳ sẽ bị ảnh hưởng.

## 1. Nhóm nhận diện rủi ro như thế nào

Đầu tiên, nhóm nhận diện rủi ro bằng ba cách:

- Brainstorming: cả nhóm cùng liệt kê các vấn đề có thể xảy ra.
- SWOT: nhìn vào điểm mạnh, điểm yếu, cơ hội và thách thức của dự án.
- Rà soát tài liệu: xem lại WBS, bảng hoạt động, Gantt, danh sách linh kiện, yêu cầu kỹ thuật và phân công nhân sự.

Sau đó, nhóm ghi các rủi ro vào Risk Register. Risk Register là bảng theo dõi rủi ro, trong đó có tên rủi ro, nhóm rủi ro, xác suất xảy ra, mức tác động, điểm ưu tiên và phương án xử lý.

Nhóm đánh giá rủi ro theo công thức:

`Risk Score = P x I`

Trong đó `P` là khả năng xảy ra, còn `I` là mức độ tác động. Điểm càng cao thì rủi ro càng cần được ưu tiên xử lý sớm.

## 2. Rủi ro quan trọng nhất của dự án

Trong bảng nhận diện, nhóm xác định hai rủi ro có độ ưu tiên cao nhất:

Rủi ro thứ nhất là **R01 - thiếu kinh nghiệm AI/MPC**. Đây là rủi ro kỹ thuật, vì MPC không phải là phần điều khiển đơn giản theo ngưỡng. MPC cần mô hình dự đoán, cần dữ liệu đầu vào ổn định và cần tinh chỉnh tham số để không tưới quá nhiều hoặc quá ít.

Rủi ro thứ hai là **R02 - trễ tiến độ module AI**. Đây là rủi ro về tiến độ. Nếu ARX, Kalman hoặc MPC trễ thì hoạt động tích hợp AI vào Web và kiểm thử end-to-end cũng có nguy cơ bị dời theo.

Hai rủi ro này được ưu tiên cao vì chúng liên quan trực tiếp đến đường găng và mốc hoàn thành cuối dự án.

## 3. Rủi ro nào đã xảy ra trong thực tế

Trong quá trình thực hiện, có hai rủi ro thật sự xảy ra.

Rủi ro thứ nhất là **R02 - trễ tiến độ AI**. Cụ thể, nhóm gặp khó khăn ở Kalman Filter và MPC Controller. Dữ liệu cảm biến có nhiễu, làm cho dự báo ARX khi chạy free-run dễ tích lũy sai số. Khi dữ liệu đầu vào chưa ổn định, MPC cũng khó tuning hơn vì bộ điều khiển có thể ra quyết định tưới chưa phù hợp.

Nói dễ hiểu, MPC cần dự đoán trạng thái độ ẩm đất trong tương lai để quyết định có tưới hay không. Nếu dữ liệu đầu vào bị nhiễu hoặc mô hình dự đoán sai lệch, MPC phải được tinh chỉnh lại. Quá trình tinh chỉnh này chính là tuning MPC, và nó làm nhóm mất thêm thời gian.

Rủi ro thứ hai là **R05 - cảm biến hỏng hoặc sai số lớn**. Đây là rủi ro phần cứng. Trong thực tế, cảm biến DHT22 gặp vấn đề nên nhóm phải thay cảm biến dự phòng và hiệu chuẩn lại dữ liệu.

## 4. Cách nhóm xử lý rủi ro trễ AI

Khi module AI có dấu hiệu trễ, nhóm không xử lý bằng cách "lấy thời gian dự trữ của công việc khác bù vào". Thời gian dự trữ không phải là quỹ thời gian chung. Nếu một công việc trên đường găng bị trễ, về lý thuyết nó sẽ làm trễ toàn bộ dự án nếu không có điều chỉnh.

Vì vậy, cách xử lý thực tế của nhóm là **nén tiến độ**.

Nhóm thực hiện ba việc:

- Thành viên C tăng giờ làm để tập trung vào Kalman Filter và MPC Controller.
- Thành viên A hỗ trợ C bằng cách chuẩn bị dữ liệu mô phỏng từ mô hình ARX, giúp C kiểm thử MPC độc lập mà không phải chờ dữ liệu thực từ phần cứng.
- Thành viên B hỗ trợ kiểm thử tích hợp ESP32 với backend, để C không bị phân tán khỏi phần thuật toán.

Cách làm này giúp nhóm giảm áp lực cho C ở phần tích hợp, đồng thời cho phép phần MPC được kiểm thử sớm hơn trên dữ liệu mô phỏng.

## 5. Cách nhóm xử lý rủi ro cảm biến hỏng

Đối với rủi ro cảm biến, nhóm đã chuẩn bị trước trong kế hoạch dự phòng. Khi cảm biến gặp lỗi, nhóm dùng cảm biến dự phòng và hiệu chuẩn lại thay vì phải chờ mua linh kiện mới.

Điểm quan trọng là rủi ro này có phát sinh chi phí, nhưng không làm trễ mốc cuối. Chi phí thay cảm biến và phát sinh vận chuyển được lấy từ kinh phí dự phòng. Vì vậy, dù chi phí thực tế tăng, nó vẫn nằm trong ngân sách tổng có dự phòng.

## 6. Kết quả quản lý rủi ro

Kết quả cuối cùng là nhóm nhận diện được 10 rủi ro, trong đó có 2 rủi ro thật sự xảy ra: trễ AI và cảm biến hỏng.

Cả hai rủi ro đều được xử lý thành công:

- R02 được xử lý bằng tăng giờ C, A hỗ trợ dữ liệu ARX, B hỗ trợ tích hợp và rút ngắn kiểm thử cuối.
- R05 được xử lý bằng cảm biến dự phòng và kinh phí dự phòng.

Dự án vẫn hoàn thành đúng 15 tuần. Kinh phí dự phòng sử dụng 171.000/255.000 VNĐ, tức là vẫn nằm trong mức dự trù.

## Câu kết chương

Tóm lại, Chương 7 cho thấy nhóm đã không chỉ liệt kê rủi ro trên giấy. Những rủi ro quan trọng như trễ AI và lỗi cảm biến đã thật sự xảy ra, nhưng vì được nhận diện trước và có phương án ứng phó, nhóm vẫn giữ được tiến độ và chất lượng của dự án.

## Gợi ý khi nói trên slide

- Đừng đọc hết bảng rủi ro.
- Tập trung nói 2 rủi ro thật sự xảy ra: R02 và R05.
- Nhấn mạnh câu: "Rủi ro đã xảy ra, nhưng không làm dự án thất bại vì nhóm có phương án xử lý trước."
