# CHƯƠNG 1: TỔNG QUAN ĐỀ TÀI DỰ ÁN

---

## 1.1 Giới thiệu chung về đồ án

Trong bối cảnh nông nghiệp hiện đại, việc giám sát và điều khiển môi trường canh tác ngày càng đòi hỏi tính tự động hóa cao. Các hệ thống nhà kính thương mại hiện tại chủ yếu hoạt động theo ngưỡng cứng (rule-based), chưa tích hợp mô hình dự đoán hay điều khiển tối ưu. Từ đó, nhóm đề xuất đề tài **"Hệ thống Nhà kính Thông minh — Smart Greenhouse"** nhằm xây dựng giải pháp giám sát và điều khiển môi trường nhà kính dựa trên IoT kết hợp trí tuệ nhân tạo.

Hệ thống giám sát các thông số môi trường (nhiệt độ, độ ẩm, ánh sáng, độ ẩm đất) và điều khiển tự động các thiết bị chấp hành (bơm, quạt, phun sương, đèn LED). Kiến trúc gồm bốn thành phần: phần cứng ESP32 với cảm biến và relay; firmware nhúng giao tiếp WebSocket; backend Django tích hợp mô hình dự đoán ARX, bộ lọc Kalman thích nghi và bộ điều khiển MPC; và giao diện Web Dashboard trên ReactJS.

| Hạng mục | Chi tiết |
|----------|----------|
| **Tên dự án** | Hệ thống Nhà kính Thông minh (Smart Greenhouse) |
| **Nhóm phát triển** | 3 thành viên |
| **Khách hàng** | Giảng viên hướng dẫn PBL |
| **Lĩnh vực** | Nông nghiệp thông minh (Smart Agriculture) |
| **Công nghệ sử dụng** | ESP32, Django, ReactJS, WebSocket, ARX, Kalman, MPC |
| **Quản lý dự án** | Hoàng Minh Trí |
| **Thời gian thực hiện** | 15 tuần |
| **Kinh phí dự án** | ~1.200.000 VNĐ (tự túc) |

**Nguồn nhân lực dự án:**

| STT | Họ và tên | Lớp | Vai trò | Mô tả công việc |
|:---:|-----------|:---:|---------|-----------------|
| 1 | Hoàng Minh Trí | 23T_DT1 | **Project Manager** kiêm AI Developer (ARX) | Quản lý tiến độ dự án, lập kế hoạch và phân công công việc; thiết kế kiến trúc tổng thể hệ thống; nghiên cứu và phát triển mô hình ARX; tích hợp hệ thống tổng thể |
| 2 | Đinh Công Trung Sỹ | 23T_DT1 | **Firmware & Hardware** kiêm **Web & Backend Developer** | Thiết kế và lắp ráp phần cứng; lập trình ESP32; kết nối cảm biến; điều khiển relay; xây dựng WebSocket client/server; phát triển Django Backend & ReactJS Dashboard Full-stack; thiết kế REST API & MySQL Database |
| 3 | Ngô Quang Sinh | 23T_DT1 | **AI & Control Engineer** (Kalman & MPC) | Nghiên cứu và phát triển pipeline AI gồm Kalman Filter và MPC; tích hợp mô hình dự đoán ARX vào hệ thống điều khiển tối ưu MPC |

---

## 1.2 Kế hoạch triển khai

Dự án triển khai từ ngày 31/12/2025 đến ngày 10/05/2026, cụ thể như sau:

- **Từ ngày 31/12/2025 đến ngày 14/01/2026:** các sinh viên tổ chức thành nhóm để làm đồ án, giảng viên đề xuất các hướng nghiên cứu quan tâm và giới thiệu với sinh viên, sau đó giảng viên chia sẻ các bài báo, các tài liệu tham khảo liên quan.
- **Từ ngày 14/01/2026 đến ngày 21/01/2026:** GV hướng dẫn gặp nhóm SV để thống nhất đề tài cụ thể sẽ triển khai.
- **Từ ngày 21/01/2026 đến ngày 12/04/2026:** GV hướng dẫn gặp nhóm SV để hướng dẫn thực hiện và kiểm tra tiến độ đề tài.
- **Từ ngày 12/04/2026 đến ngày 10/05/2026:** Nhóm SV làm dự án liên tục để hoàn thành dưới sự giám sát của giảng viên hướng dẫn.

**Các mốc quan trọng của dự án Smart Greenhouse:**

| Mốc thời gian | Công việc | Kết quả bàn giao |
|:-------------:|-----------|-------------------|
| Tuần 1 – 2 | Khảo sát yêu cầu, phân tích bài toán | Tài liệu yêu cầu, SOW, WBS |
| Tuần 3 – 4 | Thiết kế kiến trúc, sơ đồ mạch, DB schema | Tài liệu thiết kế hệ thống |
| Tuần 4 – 6 | Phát triển phần cứng + Firmware | Prototype HW hoạt động |
| Tuần 5 – 9 | Phát triển Backend + Web Dashboard | API + Dashboard cơ bản |
| Tuần 5 – 12 | Phát triển AI (ARX, Kalman, MPC) | Mô hình AI hoàn chỉnh |
| Tuần 11 – 13 | Kiểm thử tích hợp, fix bug | Test report, hệ thống ổn định |
| Tuần 13 – 15 | Hoàn thiện tài liệu, báo cáo, demo | Báo cáo PBL + QLDA + Slide |
| Tuần 15 | Bảo vệ đồ án, bàn giao sản phẩm | Demo hoàn chỉnh |

---

## 1.3 Cách triển khai đồ án

- Các sinh viên tổ chức thành 3 – 4 sinh viên/nhóm cho mỗi đề tài.
- Đề tài do giảng viên gợi ý. Sinh viên có thể đề xuất, lựa chọn.
- Bộ môn phân công từng giảng viên phụ trách từng nhóm sinh viên.
- Giảng viên được phân công để giám sát và chỉ đạo các sinh viên thực hiện đồ án.

Nhóm triển khai dự án Smart Greenhouse bằng cách phân chia hệ thống thành các module độc lập và phát triển song song để tối ưu thời gian:

| Module | Người phụ trách | Nội dung |
|--------|:---------------:|----------|
| Quản lý dự án + Mô hình ARX | Hoàng Minh Trí (A) | Lập kế hoạch, giám sát tiến độ, huấn luyện mô hình dự đoán ARX |
| Phần cứng + Firmware + Backend + Web | Đinh Công Trung Sỹ (B) | Lắp ráp mạch, lập trình ESP32, phát triển Django Backend & ReactJS Dashboard |
| Kalman Filter + MPC | Ngô Quang Sinh (C) | Phát triển bộ lọc nhiễu Kalman và bộ điều khiển tối ưu MPC |

**Công cụ sử dụng:** Trello (quản lý task), GitHub (quản lý mã nguồn), Zalo/Discord (giao tiếp), Arduino IDE (firmware), Django + ReactJS (web), Python (AI).

---

## 1.4 Đánh giá kết quả thực hiện đồ án

- **Sản phẩm dự án** gồm: quyển báo cáo, hệ thống gồm các thiết bị phần cứng và chương trình máy tính chạy đúng theo yêu cầu đặt ra.
- **Điểm quá trình:** chuyên cần và thái độ làm việc nhóm, do giảng viên hướng dẫn chấm điểm (trọng số: 30%).
- **Điểm bảo vệ:** nhóm sinh viên thuyết trình slide và demo sản phẩm trước hội đồng chấm gồm giảng viên và cán bộ doanh nghiệp (trọng số: 70%).
- **Lịch bảo vệ đồ án:** theo lịch thi của Trường.

**Kết quả thực tế của dự án Smart Greenhouse:**

| Tiêu chí | Mục tiêu | Kết quả | Đánh giá |
|----------|:--------:|:-------:|:--------:|
| Thời gian | 15 tuần | 15 tuần | ✅ Đúng hạn |
| Chi phí | 1.200.000 VNĐ | 1.371.000 VNĐ | ⚠️ Vượt 14.25% |
| FIT 1-step ARX | ≥ 80% | 85,85% | ✅ Vượt mục tiêu |
| MPC vùng mục tiêu | 55–65% | Đạt | ✅ |
| Màn hình Web | ≥ 6 | 6 | ✅ |

---
