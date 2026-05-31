# 📝 NHẬT KÝ CHI TIẾT CÁC PHẦN ĐÃ CHỈNH SỬA (Lịch sử cập nhật vai trò)

Tài liệu này ghi lại chi tiết các tệp tin và các mục cụ thể đã được chỉnh sửa để đồng bộ hóa vai trò mới của nhóm:
*   **Thành viên A (Hoàng Minh Trí - PM):** Quản lý dự án, thiết kế kiến trúc hệ thống, nghiên cứu & phát triển mô hình ARX.
*   **Thành viên B (Đinh Công Trung Sỹ - HW/FW & Fullstack):** Thiết kế phần cứng, Firmware ESP32, Django Backend và ReactJS Web Dashboard.
*   **Thành viên C (Ngô Quang Sinh - AI & Control):** Bộ lọc Kalman Filter, thuật toán điều khiển tối ưu MPC và tích hợp ARX.

---

## 1. Tệp: `Chuong02_XacDinhDuAn.md`

### 🔹 Phần 1: Chữ ký các bên liên quan (Mục 2.2.8)
*   **Trước khi sửa:** Dùng placeholder "Quản lý dự án (PM) - A", "Thành viên B", "Thành viên C".
*   **Sau khi sửa:** Thay bằng tên thật của 3 thành viên:
    ```markdown
    | Quản lý dự án (PM) - Hoàng Minh Trí | _________________ | _______ | ___/___/2026 |
    | Thành viên - Đinh Công Trung Sỹ     | _________________ | _______ | ___/___/2026 |
    | Thành viên - Ngô Quang Sinh        | _________________ | _______ | ___/___/2026 |
    ```

### 🔹 Phần 2: Phân công vai trò (Mục 2.3.1)
*   **Trước khi sửa:** A làm tất cả AI bao gồm ARX/Kalman/MPC; B làm FW/HW; C làm Web/Backend.
*   **Sau khi sửa:** Cập nhật mô tả trách nhiệm chính theo phân công mới:
    *   **Thành viên A:** PM + AI Developer (ARX).
    *   **Thành viên B:** FW + HW & Web/BE Fullstack.
    *   **Thành viên C:** AI & Control Engineer (Kalman & MPC).

### 🔹 Phần 3: Ma trận RACI (Mục 2.3.2)
*   **Trước khi sửa:** Cột của C giữ vai trò **A/R** cho Database, Backend, Web Dashboard; A giữ vai trò **A/R** cho Kalman và MPC.
*   **Sau khi sửa:** 
    *   Chuyển giao quyền thực hiện và chịu trách nhiệm (**A/R**) của các công việc Database, Backend, Web Dashboard sang cho **B**.
    *   Chuyển giao quyền thực hiện và chịu trách nhiệm (**A/R**) của các công việc Kalman Filter, MPC, tích hợp ARX vào MPC sang cho **C**.

### 🔹 Phần 4: Bảng phân công công việc chi tiết & Giờ công (Mục 2.3.3)
*   **Trước khi sửa:** Người thực hiện các nhiệm vụ phần mềm là C, thuật toán là A. Tổng giờ: A = ~168h, B = ~119h, C = ~137h.
*   **Sau khi sửa:**
    *   Đổi người thực hiện các nhiệm vụ Web/BE sang cho B, các nhiệm vụ Kalman/MPC sang cho C.
    *   Cập nhật tổng giờ công hợp lý: **A = ~146h**, **B = ~245h**, **C = ~111h** (Tổng **502h**). Thêm chú thích giải thích lý do số giờ của B lớn nhất vì kiêm cả phần cứng lẫn phần mềm Web Dashboard Full-stack.

---

## 2. Tệp: `Chuong03_WBS.md` & `Chuong03_WBS copy.md`

### 🔹 Phần 1: Thiết kế hệ thống (Mục 2.0)
*   **Trước khi sửa:** 2.4 (Cơ sở dữ liệu) và 2.5 (Giao diện Web) do **C** phụ trách; 2.6 (Pipeline AI) do **A** phụ trách.
*   **Sau khi sửa:** 2.4 và 2.5 chuyển sang **B** phụ trách; 2.6 chuyển sang phối hợp **A, C** phụ trách.

### 🔹 Phần 2: Phát triển Backend (Mục 5.0)
*   **Trước khi sửa:** Toàn bộ công việc từ 5.1 đến 5.4 phụ trách bởi **C**.
*   **Sau khi sửa:** Chuyển toàn bộ sang **B** phụ trách.

### 🔹 Phần 3: Phát triển AI (Mục 6.0)
*   **Trước khi sửa:** Toàn bộ từ 6.1 đến 6.5 phụ trách bởi **A**.
*   **Sau khi sửa:** 6.1 và 6.2 (ARX) do **A** phụ trách; 6.3 và 6.4 (Kalman & MPC) do **C** phụ trách; 6.5 (Tích hợp AI) do **B, C** phối hợp phụ trách.

### 🔹 Phần 4: Phát triển Web Dashboard (Mục 7.0)
*   **Trước khi sửa:** Toàn bộ từ 7.1 đến 7.6 phụ trách bởi **C**.
*   **Sau khi sửa:** Chuyển toàn bộ sang **B** phụ trách.

---

## 3. Tệp: `Chuong09_QuanLyRuiRo.md`

### 🔹 Phần 1: Bảng ứng phó rủi ro (Mục 9.2.2)
*   **Trước khi sửa:** Rủi ro R01 (Thiếu kinh nghiệm AI/MPC) và R03 (MPC không ổn định) do **A** phụ trách chính.
*   **Sau khi sửa:** 
    *   R01 do **A, C** cùng phối hợp phụ trách.
    *   R03 do **C** phụ trách chính.

### 🔹 Phần 2: Bài học kinh nghiệm (Mục 9.4.2)
*   **Trước khi sửa:** Bài học số 4 ghi: "B có thể hỗ trợ kiểm thử AI khi A cần tập trung MPC".
*   **Sau khi sửa:** Đổi thành "B có thể hỗ trợ kiểm thử AI khi **C** cần tập trung MPC".

---

## 4. Tệp: `Chuong10_KiemSoatDuAn.md`

### 🔹 Phần 1: Time sheet cá nhân (Mục 10.2.2.b)
*   **Trước khi sửa:** Chia giờ theo phân công cũ (A = 168h, B = 119h, C = 137h).
*   **Sau khi sửa:** Lập lại bảng phân bổ giờ chi tiết cho từng tuần khớp hoàn toàn với tổng giờ công mới:
    *   **Thành viên A (PM & ARX):** Tổng **146h** (Tập trung tuần 1-8 và tuần 11-15).
    *   **Thành viên B (HW/FW & Web Fullstack):** Tổng **245h** (Hoạt động liên tục cả phần cứng, firmware và web dashboard).
    *   **Thành viên C (Kalman & MPC):** Tổng **111h** (Tập trung cao độ từ tuần 9 đến tuần 15 cho thuật toán).

### 🔹 Phần 2: Phần điều chỉnh & Xử lý tình huống (Mục 10.5.1 & 10.9.3)
*   **Trước khi sửa:** Ghi nhận "Tăng giờ làm việc của thành viên A" và "A tăng giờ làm" khi xảy ra trễ tiến độ MPC tuning.
*   **Sau khi sửa:** Đổi thành "Tăng giờ làm việc của thành viên **C** (từ 20h → 28h/tuần)" và "**C** tăng giờ làm" để phản ánh đúng việc Sinh là người chịu trách nhiệm thuật toán MPC.

---

## 5. Tệp: `phan_chia_cong_viec.md`

### 🔹 Phần: Đầu trang tệp tin
*   **Sửa đổi:** Bổ sung bảng định nghĩa vai trò kỹ thuật chi tiết của Thành viên A, B, C tương ứng với Hoàng Minh Trí, Đinh Công Trung Sỹ, và Ngô Quang Sinh để làm tài liệu đối chiếu nhanh cho toàn bộ báo cáo.
