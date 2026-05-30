# CHƯƠNG 1: TỔNG QUAN DỰ ÁN

---

## 1.1 Giới thiệu đề tài — Hệ thống Nhà kính Thông minh (Smart Greenhouse)

### 1.1.1 Giới thiệu đề tài

Trong bối cảnh nông nghiệp hiện đại, việc giám sát và điều khiển môi trường canh tác ngày càng đòi hỏi tính tự động hóa cao. Các hệ thống nhà kính thương mại hiện tại chủ yếu hoạt động theo ngưỡng cứng (rule-based), chưa tích hợp mô hình dự đoán hay điều khiển tối ưu. Từ đó, nhóm đề xuất đề tài **"Hệ thống Nhà kính Thông minh — Smart Greenhouse"** nhằm xây dựng giải pháp giám sát và điều khiển môi trường nhà kính dựa trên IoT kết hợp trí tuệ nhân tạo.

Hệ thống giám sát các thông số môi trường (nhiệt độ, độ ẩm, ánh sáng, độ ẩm đất) và điều khiển tự động các thiết bị chấp hành (bơm, quạt, phun sương, đèn LED). Kiến trúc gồm bốn thành phần: phần cứng ESP32 với cảm biến và relay; firmware nhúng giao tiếp WebSocket; backend Django tích hợp mô hình dự đoán ARX, bộ lọc Kalman thích nghi và bộ điều khiển MPC; và giao diện Web Dashboard trên ReactJS.

Nhóm lựa chọn đề tài vì tính thực tiễn cao theo xu hướng nông nghiệp 4.0, tính học thuật liên ngành (hệ thống nhúng, xử lý tín hiệu, điều khiển tối ưu), tính khả thi nhờ ESP32 chi phí thấp, và tính sáng tạo khi tích hợp pipeline ARX–Kalman–MPC vượt xa điều khiển rule-based thông thường.

### 1.1.2 Bảng mô tả tổng quan dự án

| Hạng mục | Chi tiết |
|----------|---------|
| **Project Name** | Hệ thống Nhà kính Thông minh (Smart Greenhouse) |
| **Development** | Nhóm 3 thành viên (A, B, C) |
| **Customer** | Giảng viên hướng dẫn PBL |
| **Industry / Service** | Nông nghiệp thông minh (Smart Agriculture) |
| **Technology** | ESP32, Django, ReactJS, WebSocket, ARX, Kalman, MPC |
| **Project Manager** | Thành viên A |
| **Thời gian thực hiện** | 15 tuần (Tuần 1 → Tuần 15) |
| **Số lượng thành viên** | 3 người |
| **Kinh phí dự án** | ~625.000 VNĐ (tự túc) |
| **Phương pháp phát triển** | Waterfall |

### 1.1.3 Nguồn nhân lực dự án

| STT | Họ và tên | Lớp | Vai trò | Mô tả công việc |
|:---:|-----------|:---:|---------|-----------------|
| 1 | Thành viên A | 23T_DTx | **Project Manager** kiêm AI Developer | Quản lý dự án, thiết kế kiến trúc, phát triển pipeline AI (ARX, Kalman, MPC), tích hợp hệ thống |
| 2 | Thành viên B | 23T_DTx | Firmware & Hardware Engineer | Thiết kế mạch, lắp ráp phần cứng, lập trình ESP32, cảm biến, relay, WebSocket client |
| 3 | Thành viên C | 23T_DTx | Web & Backend Developer | Phát triển Django Backend, ReactJS Dashboard, REST API, Database MySQL |

### 1.1.4 Các mốc thời gian dự án (Milestones)

| Mốc thời gian | Công việc | Deliverable |
|:--------------:|-----------|-------------|
| Tuần 1 – 2 | Khảo sát yêu cầu, phân tích bài toán | Tài liệu yêu cầu, SOW, WBS |
| Tuần 3 – 4 | Thiết kế kiến trúc, sơ đồ mạch, DB schema | Tài liệu thiết kế hệ thống |
| Tuần 4 – 6 | Phát triển phần cứng + Firmware | Prototype HW hoạt động |
| Tuần 5 – 9 | Phát triển Backend + Web Dashboard | API + Dashboard cơ bản |
| Tuần 5 – 12 | Phát triển AI (ARX, Kalman, MPC) | Mô hình AI hoàn chỉnh |
| Tuần 11 – 13 | Kiểm thử tích hợp, fix bug | Test report, hệ thống ổn định |
| Tuần 13 – 15 | Hoàn thiện tài liệu, báo cáo, demo | Báo cáo PBL + QLDA + Slide |
| Tuần 15 | Bảo vệ đồ án, bàn giao sản phẩm | Demo hoàn chỉnh |

## 1.2 Mục đích và mục tiêu dự án

Mục đích tổng quát của dự án là xây dựng một hệ thống nhà kính thông minh có khả năng giám sát, dự đoán và điều khiển tối ưu các thông số môi trường, hướng tới mô hình canh tác nông nghiệp hiện đại.

> *Chi tiết phân rã mục đích – mục tiêu SMART, phạm vi, deliverables, ràng buộc, vai trò và trách nhiệm được trình bày trong Chương 2: Xác định dự án.*

---

## 1.3 Phương pháp phát triển phần mềm

### 1.3.1 Giới thiệu Waterfall

Mô hình Waterfall (thác nước) là phương pháp phát triển phần mềm tuần tự, trong đó mỗi giai đoạn phải hoàn thành trước khi chuyển sang giai đoạn tiếp theo.

**Các giai đoạn:** Phân tích yêu cầu → Thiết kế → Phát triển → Kiểm thử → Triển khai → Bảo trì.

**Ưu điểm:**
- Rõ ràng, có cấu trúc, dễ quản lý.
- Tài liệu đầy đủ ở mỗi giai đoạn.
- Phù hợp khi yêu cầu ổn định, ít thay đổi.

**Nhược điểm:**
- Khó quay lại giai đoạn trước khi phát hiện lỗi.
- Không linh hoạt với thay đổi yêu cầu.

### 1.3.2 Lý do lựa chọn Waterfall

Nhóm lựa chọn **mô hình Waterfall** cho dự án Smart Greenhouse vì:

| Tiêu chí | Lý do chọn Waterfall |
|-----------|---------------------|
| **Yêu cầu** | Ổn định, xác định rõ từ đầu, được giảng viên duyệt |
| **Quy mô nhóm** | Chỉ 3 người — Scrum quá phức tạp |
| **Tài liệu** | Mỗi giai đoạn tạo deliverable rõ ràng, thuận lợi cho báo cáo |
| **Kiểm soát** | PM dễ kiểm soát tiến độ tuần tự |
| **Thời gian** | 15 tuần cố định → cần lịch biểu tổng thể ngay từ đầu |

### 1.3.3 Các giai đoạn Waterfall áp dụng

```
Tuần 1-2         Tuần 3-4           Tuần 4-12              Tuần 11-13         Tuần 13-15
┌──────────┐   ┌──────────┐   ┌────────────────────┐   ┌──────────────┐   ┌──────────────┐
│ Phân tích │──▶│ Thiết kế │──▶│    Phát triển       │──▶│  Kiểm thử    │──▶│ Triển khai   │
│ yêu cầu  │   │ hệ thống │   │ (HW, FW, BE, AI,   │   │ (đơn vị,     │   │ & Tài liệu   │
│           │   │          │   │  Web Dashboard)     │   │  tích hợp)   │   │ & Bảo vệ     │
└──────────┘   └──────────┘   └────────────────────┘   └──────────────┘   └──────────────┘
```

---
