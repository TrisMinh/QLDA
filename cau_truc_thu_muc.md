# CẤU TRÚC THƯ MỤC DỰ ÁN HỆ THỐNG NHÀ KÍNH THÔNG MINH (SMART GREENHOUSE)

Tài liệu này mô tả chi tiết cấu trúc thư mục và chức năng của các tệp tin quan trọng trong toàn bộ dự án, bao gồm mã nguồn phát triển và tài liệu báo cáo quản lý dự án.

---

## I. CẤU TRÚC MÃ NGUỒN (Repository `Green_House_PBL` - nằm trong thư mục `MPC/`)

Đây là kho chứa mã nguồn chính của dự án, được thiết kế theo mô hình Mono-repo để quản lý tập trung toàn bộ các module phần cứng, firmware, web server và các thuật toán AI.

```text
Green_House_PBL/
├── .gitignore                      # Cấu hình bỏ qua tệp tự sinh, thư viện
├── README.md                       # Hướng dẫn & cấu trúc repo
├── ARX/                            # Mô hình thực vật ARX
│   ├── arx_pipeline.py             # Code train mô hình ARX
│   ├── arx_model.json              # Trọng số mô hình sau train
│   └── greenhouse_data.csv         # Dữ liệu cảm biến training
├── Kalman/                         # Lọc nhiễu cảm biến độ ẩm
│   └── kalman/
│       ├── filter/cycle.py         # Lọc Kalman & Adaptive Kalman
│       └── prediction/arx_adapter.py # Adapter Kalman sang ARX
├── MPC/                            # Bộ điều khiển tối ưu MPC
│   └── mpc/
│       ├── fao56.py                # Cân bằng nước rễ (FAO-56)
│       ├── solver/grid.py          # Thuật toán tìm thời gian tưới
│       ├── adaptive/bias.py        # Hiệu chỉnh sai số AMPC
│       └── plant/arx.py            # Mô phỏng nhà kính theo ARX
└── Green-House/                    # Web App & phần cứng
    ├── hardware/                   # Sơ đồ mạch ESP32
    ├── firmware/                   # Code ESP32 đọc cảm biến, relay
    ├── backend/                    # Server backend Django
    │   ├── manage.py               # Quản lý Django dự án
    │   ├── config/                 # Cấu hình Django chính
    │   └── api/
    │       ├── views.py            # REST APIs nhận/gửi dữ liệu
    │       ├── consumer.py         # WebSocket truyền thời gian thực
    │       ├── ampc_scheduler.py   # Lập lịch chu kỳ Kalman-ARX-MPC
    │       └── models.py           # Bảng CSDL MySQL
    └── frontend/                   # Web Dashboard ReactJS
        ├── src/App.jsx             # Giao diện Dashboard React
        └── src/main.tsx            # Khởi chạy React App
```

---

## II. CẤU TRÚC TÀI LIỆU QUẢN LÝ DỰ ÁN (Nằm trong thư mục `QLDA/`)

Thư mục này chứa toàn bộ các chương báo cáo môn học Quản lý dự án CNTT của nhóm:

*   **`Chuong01_TongQuanDuAn.md`**: Giới thiệu đề tài, bối cảnh dự án, mục đích, mục tiêu cụ thể và phạm vi dự án (phần cứng, phần mềm, người dùng).
*   **`Chuong02_XacDinhDuAn.md`**: Định nghĩa vai trò của 3 thành viên, ma trận trách nhiệm RACI và bảng tính tổng giờ công chi tiết của từng người (PM Trí, Fullstack Sỹ, AI Sinh).
*   **`Chuong03_WBS.md`**: Sơ đồ phân rã công việc chi tiết (Work Breakdown Structure) từ cấp dự án đến các gói công việc nhỏ nhất.
*   **`Chuong05_UocLuongThoiGian.md` & `.docx`**: Tài liệu ước lượng thời gian dự án theo giờ công và man-month dựa trên phương pháp ước lượng 3 điểm (PERT).
*   **`Chuong06_LapLichBieu.md` & `.docx`**: Tài liệu lập lịch biểu dự án, sơ đồ PDM/AON, ADM/AOA và xác định đường găng (Critical Path) của dự án.
*   **`Chuong07_Git.md` & `.docx`**: Báo cáo quản lý mã nguồn, sơ đồ phân nhánh Git, commit message rules, validation gate và bảng log chi tiết 55 commit thực tế.
*   **`Chuong09_QuanLyRuiRo.md`**: Bảng ma trận quản lý rủi ro dự án, các biện pháp ứng phó và bài học kinh nghiệm rút ra.
*   **`Chuong10_KiemSoatDuAn.md`**: Tài liệu theo dõi tiến độ họp nhóm, cá nhân time sheet thực tế hàng tuần và nhật ký xử lý các tình huống phát sinh.
*   **`nhat_ky_chinh_sua_vai_tro.md`**: Nhật ký lưu trữ chi tiết các nội dung đã thay đổi trong các chương báo cáo để đảm bảo đồng bộ thông tin vai trò nhân sự mới.
*   **`phan_chia_cong_viec.md`**: Tài liệu đối chiếu nhanh tóm tắt vai trò kỹ thuật cụ thể của 3 thành viên (Hoàng Minh Trí, Đinh Công Trung Sỹ, Ngô Quang Sinh).
*   **`cau_truc_thu_muc.md`**: Tệp tin này (mô tả cấu trúc thư mục hiện tại của dự án).
