# KỊCH BẢN THUYẾT TRÌNH - CHƯƠNG 1: TỔNG QUAN DỰ ÁN

## Mục tiêu khi trình bày chương này

Chương 1 là phần mở đầu, cần nói nhanh nhưng đủ ý để cô nắm được:

- Tên đề tài là gì.
- Nhóm có những ai, ai là nhóm trưởng.
- Dự án làm trong bao lâu.
- Mục tiêu chính của dự án là gì.
- Sản phẩm cuối cùng nhóm làm ra gồm những gì.
- Có minh chứng thực tế như ảnh họp, ảnh phần cứng, ảnh web/demo.

## Kịch bản nói chính

Kính thưa cô và các bạn, nhóm em xin trình bày đề tài **Hệ thống Nhà kính Thông minh - Smart Greenhouse**.

Dự án của nhóm được thực hiện trong thời gian **15 tuần**, từ ngày **05/01/2026 đến ngày 10/05/2026**. Nhóm gồm 3 thành viên:

- **Hoàng Minh Trí**: nhóm trưởng, phụ trách quản lý tiến độ dự án, thiết kế kiến trúc tổng thể và mô hình ARX.
- **Đinh Công Trung Sỹ**: phụ trách phần cứng, firmware ESP32, backend Django và giao diện Web Dashboard.
- **Ngô Quang Sinh**: phụ trách Kalman Filter, MPC Controller và phần điều khiển tối ưu.

Mục tiêu của dự án là xây dựng một mô hình nhà kính thông minh có khả năng **giám sát môi trường**, **điều khiển thiết bị** và **hỗ trợ tưới tiêu bằng AI**. Cụ thể, hệ thống đọc các thông số như nhiệt độ, độ ẩm không khí, ánh sáng và độ ẩm đất; sau đó hiển thị dữ liệu lên giao diện web theo thời gian thực. Người dùng có thể theo dõi trạng thái nhà kính và điều khiển các thiết bị như bơm, quạt, phun sương hoặc đèn.

Điểm khác biệt của đề tài là nhóm không chỉ làm hệ thống bật/tắt theo ngưỡng đơn giản, mà có tích hợp mô hình AI và điều khiển tối ưu. Trong đó, mô hình **ARX** dùng để dự đoán độ ẩm đất, **Kalman Filter** dùng để lọc nhiễu dữ liệu cảm biến, còn **MPC Controller** dùng để đưa ra quyết định tưới nhằm giữ độ ẩm đất trong vùng mục tiêu.

Về kiến trúc, hệ thống gồm bốn phần chính:

- Phần cứng ESP32 kết nối cảm biến và relay.
- Firmware ESP32 đọc dữ liệu cảm biến và điều khiển thiết bị.
- Backend Django xử lý dữ liệu, lưu database và giao tiếp WebSocket.
- Web Dashboard ReactJS hiển thị dữ liệu, trạng thái thiết bị và kết quả điều khiển.

Trong quá trình làm dự án, nhóm có lưu các minh chứng như ảnh họp nhóm, ảnh tiến độ, ảnh phần cứng, ảnh giao diện web và ảnh demo kết quả. Những minh chứng này dùng để chứng minh dự án không chỉ được lập kế hoạch trên giấy mà có quá trình thực hiện thực tế.

Kết quả cuối cùng, nhóm hoàn thành được mô hình phần cứng, firmware ESP32, backend, web dashboard và module AI/control. Hệ thống có thể đọc dữ liệu cảm biến, hiển thị trên web, điều khiển thiết bị và chuyển kết quả dự đoán/điều khiển thành quyết định tưới cây. Mô hình ARX đạt FIT 85,85%, MPC giữ độ ẩm đất trong vùng mục tiêu 55-65%, và dự án hoàn thành đúng thời gian 15 tuần.

## Cách nói ngắn nếu bị giới hạn thời gian

Nếu chỉ có ít thời gian, có thể nói gọn như sau:

> Nhóm em thực hiện đề tài Hệ thống Nhà kính Thông minh trong 15 tuần, từ 05/01/2026 đến 10/05/2026. Nhóm có 3 thành viên, trong đó Hoàng Minh Trí là nhóm trưởng, phụ trách quản lý dự án và ARX; Đinh Công Trung Sỹ phụ trách phần cứng, firmware, backend và web; Ngô Quang Sinh phụ trách Kalman Filter và MPC. Mục tiêu dự án là xây dựng mô hình nhà kính có thể giám sát môi trường, điều khiển thiết bị và hỗ trợ tưới tiêu bằng AI. Sản phẩm cuối cùng gồm phần cứng ESP32, backend Django, web ReactJS và module AI/control. Nhóm có minh chứng thực tế như ảnh họp, ảnh phần cứng, ảnh web và ảnh demo kết quả.

## Các ý cô có thể hỏi và cách trả lời nhanh

### 1. Đề tài của nhóm là gì?

Đề tài của nhóm là **Hệ thống Nhà kính Thông minh - Smart Greenhouse**, kết hợp IoT và AI để giám sát, điều khiển và hỗ trợ tưới tiêu trong mô hình nhà kính.

### 2. Nhóm có bao nhiêu thành viên? Ai là nhóm trưởng?

Nhóm có 3 thành viên. **Hoàng Minh Trí là nhóm trưởng**, phụ trách quản lý tiến độ, thiết kế tổng thể và mô hình ARX.

### 3. Dự án thực hiện trong bao lâu?

Dự án thực hiện trong **15 tuần**, từ **05/01/2026 đến 10/05/2026**.

### 4. Mục tiêu chính của dự án là gì?

Mục tiêu chính là xây dựng hệ thống nhà kính thông minh có thể:

- Thu thập dữ liệu cảm biến.
- Hiển thị dữ liệu realtime trên web.
- Điều khiển thiết bị từ xa.
- Dùng AI để hỗ trợ quyết định tưới cây.

### 5. Sản phẩm cuối cùng gồm những gì?

Sản phẩm cuối cùng gồm:

- Mô hình phần cứng nhà kính.
- Firmware ESP32.
- Backend Django.
- Web Dashboard ReactJS.
- Module AI gồm ARX, Kalman Filter và MPC.

### 6. Có minh chứng thực tế không?

Có. Nhóm chuẩn bị ảnh họp nhóm, ảnh phần cứng, ảnh web dashboard và ảnh demo kết quả điều khiển/tưới cây.

## Lưu ý khi trình bày slide chương 1

- Nói rõ **tên đề tài, thành viên, nhóm trưởng, thời gian thực hiện** ngay từ đầu.
- Không sa vào giải thích thuật toán quá sâu ở Chương 1.
- Nhấn mạnh sản phẩm cuối cùng có cả **phần cứng + phần mềm + AI**.
- Khi nói đến minh chứng, chỉ cần nói nhóm có ảnh họp, ảnh phần cứng, ảnh web và ảnh demo; không cần giải thích dài.

