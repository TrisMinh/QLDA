# CHƯƠNG 7: QUẢN LÝ MÃ NGUỒN BẰNG GIT/GITHUB

---

## 7.1 Mục đích của quản lý mã nguồn

Trong dự án **Hệ thống Nhà kính Thông minh (Smart Greenhouse)**, phần mềm đóng vai trò trung tâm điều khiển và giám sát toàn bộ hoạt động. Mã nguồn dự án được xây dựng từ nhiều thành phần có tính liên kết chặt chẽ nhưng chạy trên các môi trường phần cứng và phần mềm khác nhau:
*   **Firmware ESP32**: Đọc dữ liệu cảm biến (DHT22, độ ẩm đất, LDR), điều khiển thiết bị (bơm, quạt, phun sương, đèn) và giao tiếp qua giao thức WebSocket.
*   **Backend Django**: Xử lý logic nghiệp vụ, quản lý database MySQL, xây dựng các API endpoints và WebSocket channels để nhận/phát dữ liệu.
*   **Web Dashboard (ReactJS)**: Giao diện người dùng trực quan, hiển thị biểu đồ thời gian thực, điều khiển thiết bị từ xa và cấu hình hệ thống.
*   **Mô hình AI & Điều khiển tối ưu (ARX, Kalman Filter, MPC/AMPC)**: Tính toán lượng nước tưới tối ưu dựa trên mô hình hóa độ ẩm đất rễ FAO-56 và lọc nhiễu tín hiệu.

Với số lượng module đa dạng và nhóm phát triển gồm 3 thành viên, việc quản lý mã nguồn thủ công là không khả thi và tiềm ẩn rủi ro xung đột mã nguồn lớn. Do đó, Git và GitHub được lựa chọn làm công cụ quản lý phiên bản với các mục đích:
1.  **Lưu trữ lịch sử phát triển**: Ghi nhận toàn bộ quá trình viết mã, cho phép so sánh, truy vết lỗi và khôi phục các phiên bản ổn định trong quá khứ.
2.  **Hỗ trợ làm việc nhóm song song**: Các thành viên có thể phát triển các tính năng độc lập trên các nhánh (branches) riêng biệt mà không làm gián đoạn mã nguồn chính.
3.  **Kiểm soát chất lượng mã nguồn**: Thiết lập quy trình Pull Request (PR) và Code Review bắt buộc trước khi tích hợp vào nhánh chính, đảm bảo mã nguồn đáp ứng tiêu chuẩn chất lượng.
4.  **Tích hợp liên tục và Fail-safe**: Hỗ trợ thiết lập các cổng kiểm chứng chất lượng (validation gates) tự động để xác nhận tính ổn định của các module điều khiển AI trước khi triển khai thực tế.

---

## 7.2 Tổng quan Repository trên GitHub

### 7.2.1 Thông tin Repository
Repository chính thức của dự án được lưu trữ công khai trên nền tảng GitHub:
*   **Đường dẫn truy cập**: [https://github.com/BapTruongSinh/Green_House_PBL.git](https://github.com/BapTruongSinh/Green_House_PBL.git)
*   **Trạng thái**: Public (Công khai)
*   **Nhánh mặc định (Default branch)**: `main`

### 7.2.2 Cấu trúc mã nguồn trong Repository
Repository được thiết kế theo mô hình Mono-repo để quản lý tập trung toàn bộ mã nguồn của hệ thống tại một nơi duy nhất. Cấu trúc thư mục gốc bao gồm:

```text
Green_House_PBL/
├── .gitignore                      # Cấu hình bỏ qua các file sinh tự động, thư viện hoặc credentials
├── ARX/                            # Module nghiên cứu và huấn luyện mô hình thực vật ARX
│   ├── arx_pipeline.py             # Pipeline tiền xử lý và huấn luyện mô hình
│   ├── arx_model.json              # Trọng số mô hình ARX sau huấn luyện (FIT 85%)
│   ├── greenhouse_data.csv         # Dữ liệu cảm biến lịch sử để training
│   └── ARX_Model_Documentation.md  # Tài liệu kỹ thuật mô tả toán học mô hình ARX
├── Kalman/                         # Module lọc nhiễu tín hiệu cảm biến độ ẩm đất
│   ├── kalman/                     # Logic bộ lọc Kalman đơn hướng và Adaptive Kalman
│   └── tests/                      # Bộ test suite đánh giá giảm nhiễu tín hiệu
├── MPC/                            # Module điều khiển tối ưu theo mô hình dự báo
│   ├── mpc/
│   │   ├── fao56.py                # Mô hình cân bằng nước vùng rễ theo tiêu chuẩn FAO-56
│   │   ├── solver/                 # Thuật toán Grid-shooting tìm thời gian bơm tối ưu
│   │   ├── adaptive/               # Lớp hiệu chỉnh sai số bias (AMPC)
│   │   └── actuator/               # HTTP client gửi lệnh điều khiển an toàn sang thiết bị
│   └── tests/                      # Bộ unit tests bảo vệ các logic safety, constraint và solver
├── Green-House/                    # Dự án Web Application chính tích hợp hệ thống
│   ├── hardware/                   # Sơ đồ nguyên lý mạch và đấu nối chân ESP32
│   ├── firmware/                   # Code C++ cho vi điều khiển ESP32
│   ├── backend/                    # Server Django (config, api, channels, database)
│   └── frontend/                   # Ứng dụng web ReactJS (giao diện điều khiển, biểu đồ)
```

---

## 7.3 Chiến lược phân nhánh (Branching Strategy)

Để đảm bảo nhánh `main` luôn chứa mã nguồn ổn định nhất, nhóm áp dụng chiến lược phân nhánh Git Workflow cải tiến. Mỗi thành viên khi phát triển một tính năng mới bắt buộc phải tách nhánh phụ, kiểm thử local thành công trước khi gửi yêu cầu merge.

### 7.3.1 Quy tắc đặt tên nhánh (Branch Naming)

Tên các nhánh phụ phải tuân thủ cấu trúc phân loại công việc rõ ràng:

| Loại nhánh | Mục đích sử dụng | Ví dụ thực tế |
| :--- | :--- | :--- |
| `feature/*` | Phát triển các chức năng mới theo WBS | `feature/ai-mpc-controller` |
| `fix/*` | Sửa lỗi phát hiện trong quá trình kiểm thử | `fix/api-sensor-validation` |
| `test/*` | Bổ sung unit tests, regression tests | `test/system-regression` |
| `docs/*` | Cập nhật tài liệu kỹ thuật, hướng dẫn | `docs/final-report` |
| `release/*` | Đóng gói sản phẩm nộp, chuẩn bị demo | `release/v1.0-final` |

### 7.3.2 Quy tắc viết Commit Message (Conventional Commits)

Nhóm thống nhất áp dụng cấu trúc commit message chuẩn hóa để phục vụ việc tự động tạo changelog và dễ dàng kiểm soát lịch sử thay đổi:

```text
<type>(<scope>): <mô tả ngắn bằng tiếng Anh>
```

Trong đó:
*   `type` gồm: `feat` (tính năng mới), `fix` (sửa lỗi), `docs` (tài liệu), `test` (viết test), `chore` (cấu hình phụ trợ), `refactor` (tối ưu mã nguồn).
*   `scope` chỉ ra module chịu ảnh hưởng trực tiếp: `hw`, `fw`, `backend`, `web`, `ai-arx`, `ai-kalman`, `ai-mpc`, `test`, `report`.
*   `mô tả ngắn` viết ở thì hiện tại, không viết hoa chữ cái đầu và không có dấu chấm cuối câu.

---

## 7.4 Phân chia công việc trên Git theo WBS và Lập lịch

Các commit và nhánh được tạo lập khớp chính xác theo phân chia công việc trong WBS, bảng lập lịch thời gian của dự án và phân chia vai trò nhân sự giữa 3 thành viên:
1.  **MinhTris (Hoàng Minh Trí - Member A - PM & AI)**: Phụ trách cấu trúc chung, tài liệu thiết kế, chuẩn bị dữ liệu, huấn luyện mô hình ARX, tích hợp pipeline và kiểm thử hệ thống.
2.  **TrungSy2106 (Đinh Công Trung Sỹ - Member B - Fullstack & HW)**: Phụ trách thiết kế mạch, lắp ráp phần cứng, firmware ESP32, Django backend, database MySQL, ReactJS frontend dashboard, tích hợp và kiểm thử.
3.  **BapTruongSinh (Ngô Quang Sinh - Member C - AI & Control)**: Phụ trách khảo sát yêu cầu AI, thiết kế pipeline, lập trình thuật toán Kalman Filter, điều khiển tối ưu MPC, tích hợp và viết unit tests.

### 7.4.1 Bảng lịch sử commit thực tế trong repository (05/01/2026 - 10/05/2026)

Dưới đây là bảng thống kê toàn bộ lịch sử commit chính thức trong repository, phản ánh chính xác các giai đoạn phát triển và ngày giờ thực hiện (bao gồm giai đoạn nghỉ Tết từ 09/02/2026 đến 02/03/2026 hoàn toàn không có commit):

| Hash Commit | Ngày thực hiện | Nhánh | Tác giả (Tên Git) | Commit Message / Thao tác Git | Công việc WBS |
| :---: | :---: | :--- | :--- | :--- | :--- |
| **d530308** | 05/01/2026 | `main` | MinhTris | `chore: initialize repository structure and base gitignore` | WBS 1.1 - 1.4 |
| **f55a5d7** | 07/01/2026 | `feature/system-design` | MinhTris | `docs(report): survey existing greenhouse solutions and specifications` | WBS 1.1 |
| **7f435dd** | 09/01/2026 | `feature/system-design` | TrungSy2106 | `docs(report): draft system requirements and interface specs` | WBS 1.2 |
| **78f9524** | 11/01/2026 | `feature/system-design` | BapTruongSinh | `docs(report): define physical constraints and control requirements` | WBS 1.3 |
| **49a33d5** | 11/01/2026 | `main` | MinhTris | *Merge branch 'feature/system-design' into main* | Tích hợp yêu cầu |
| **687d416** | 13/01/2026 | `feature/system-design` | MinhTris | `docs(report): define project scope of work SOW and WBS structure` | WBS 1.4 |
| **f23fcbd** | 16/01/2026 | `feature/system-design` | TrungSy2106 | `docs(report): establish RACI responsibility matrix and BOM spreadsheet` | WBS 2.1 |
| **49a33d5** | 18/01/2026 | `main` | MinhTris | *Merge branch 'feature/system-design' into main* | Tích hợp lập lịch |
| **8c02494** | 21/01/2026 | `feature/system-design` | MinhTris | `docs(report): design overall architecture and control pipeline diagram` | WBS 2.1 |
| **d68d084** | 25/01/2026 | `feature/system-design` | TrungSy2106 | `feat(hw): design circuit schematics and database ERD relational model` | WBS 2.2, 2.4 |
| **4564911** | 29/01/2026 | `feature/system-design` | TrungSy2106 | `feat(web): create web dashboard wireframe and UX mockup` | WBS 2.5 |
| **49a33d5** | 01/02/2026 | `main` | MinhTris | *Merge branch 'feature/system-design' into main* | Tích hợp thiết kế |
| **8f3a7ce** | 03/02/2026 | `feature/hardware-setup` | TrungSy2106 | `feat(hw): assemble sensor modules with ESP32 microcontroller` | WBS 3.1, 3.4 |
| **a26f4a7** | 04/02/2026 | `feature/ai-arx-model` | MinhTris | `feat(ai-arx): preprocessing historical datasets and clean outlier values` | WBS 6.1 |
| **05f6f6f** | 08/02/2026 | `main` | MinhTris | *Merge branch 'feature/hardware-setup' into main* | Tích hợp phần cứng |
| *Nghỉ Tết* | **09/02 - 02/03** | - | - | *Giai đoạn nghỉ Tết Bính Ngọ - Không có hoạt động commit* | - |
| **b73aa1e** | 04/03/2026 | `feature/firmware-esp32` | TrungSy2106 | `feat(fw): implement reading sensors and local LCD display logic` | WBS 4.1, 4.4 |
| **83875f1** | 07/03/2026 | `feature/firmware-esp32` | TrungSy2106 | `feat(fw): implement WebSocket client telemetry transport` | WBS 4.2 |
| **e5c3b13** | 07/03/2026 | `main` | MinhTris | *Merge branch 'feature/firmware-esp32' into main* | Tích hợp FW đợt 1 |
| **2009034** | 10/03/2026 | `feature/ai-arx-model` | MinhTris | `feat(ai-arx): train and validate ARX plant model via least squares` | WBS 6.2 |
| **8e66446** | 11/03/2026 | `feature/firmware-esp32` | TrungSy2106 | `feat(fw): implement relay control logic and manual auto mode switch` | WBS 4.3, 4.5 |
| **e5c3b13** | 15/03/2026 | `main` | MinhTris | *Merge branch 'feature/firmware-esp32' into main* | Tích hợp FW đợt 2 |
| **f442a61** | 18/03/2026 | `feature/ai-arx-model` | MinhTris | `feat(ai-arx): implement evaluation pipeline and save model weights` | WBS 6.2 |
| **7a67c59** | 19/03/2026 | `feature/backend-django` | TrungSy2106 | `feat(backend): initialize Django server project and configure MySQL connection` | WBS 5.1, 5.4 |
| **2912413** | 22/03/2026 | `feature/backend-django` | TrungSy2106 | `feat(backend): implement REST API views for telemetry ingestion` | WBS 5.2 |
| **f94d2c0** | 23/03/2026 | `main` | MinhTris | *Merge branch 'feature/ai-arx-model' into main* | Tích hợp mô hình ARX |
| **89eb1d8** | 26/03/2026 | `feature/ai-kalman-filter` | BapTruongSinh | `feat(ai-kalman): implement adaptive Kalman filter logic for moisture signal` | WBS 6.3 |
| **46c2c94** | 26/03/2026 | `feature/backend-django` | TrungSy2106 | `feat(backend): add WebSocket routing and consumers using Django Channels` | WBS 5.3 |
| **6c58ef8** | 30/03/2026 | `main` | MinhTris | *Merge branch 'feature/backend-django' into main* | Tích hợp Backend Django |
| **761ced7** | 02/04/2026 | `feature/web-dashboard` | TrungSy2106 | `feat(web): setup React application scaffolding and UI component templates` | WBS 7.1 |
| **b38bf65** | 02/04/2026 | `feature/ai-kalman-filter` | BapTruongSinh | `test(ai-kalman): add noise filtering simulation regression tests` | WBS 6.3 |
| **3c034e6** | 06/04/2026 | `main` | MinhTris | *Merge branch 'feature/ai-kalman-filter' into main* | Tích hợp bộ lọc Kalman |
| **70ac140** | 07/04/2026 | `feature/web-dashboard` | TrungSy2106 | `feat(web): integrate WebSocket client connection and draw realtime charts` | WBS 7.3 |
| **dbcaae4** | 09/04/2026 | `feature/ai-mpc-controller` | BapTruongSinh | `feat(ai-mpc): initialize MPC solver module and define config contracts` | WBS 6.4 |
| **4008116** | 10/04/2026 | `feature/web-dashboard` | TrungSy2106 | `feat(web): add device override buttons and alarm settings page` | WBS 7.4 - 7.5 |
| **02ac3b0** | 12/04/2026 | `feature/ai-mpc-controller` | BapTruongSinh | `feat(ai-mpc): implement FAO-56 root-zone water balance model` | WBS 6.4 |
| **06e6ee6** | 13/04/2026 | `main` | MinhTris | *Merge branch 'feature/web-dashboard' into main* | Tích hợp Web Dashboard |
| **a6fa03e** | 15/04/2026 | `feature/ai-mpc-controller` | BapTruongSinh | `feat(ai-mpc): add AMPC bias adaptation layer using prediction errors` | WBS 6.4 |
| **b75d943** | 18/04/2026 | `feature/ai-mpc-controller` | BapTruongSinh | `feat(ai-mpc): implement HTTP actuator pilot with fail-safe limits` | WBS 6.4 |
| **93cb087** | 20/04/2026 | `main` | MinhTris | *Merge branch 'feature/ai-mpc-controller' into main* | Tích hợp bộ điều khiển MPC |
| **c164f10** | 22/04/2026 | `feature/ai-integration` | MinhTris | `feat(ai-integration): construct closed-loop execution loop with ARX adapter` | WBS 6.5 |
| **175a09d** | 24/04/2026 | `feature/ai-integration` | BapTruongSinh | `feat(ai-integration): connect Kalman filter signals into MPC input bounds` | WBS 6.5 |
| **83a0122** | 26/04/2026 | `feature/ai-integration` | TrungSy2106 | `feat(backend): build recommendation api wrapper for django integration` | WBS 6.5 |
| **0070517** | 27/04/2026 | `main` | MinhTris | *Merge branch 'feature/ai-integration' into main* | Tích hợp hệ thống AI |
| **dd9d794** | 29/04/2026 | `test/system-regression` | BapTruongSinh | `test(mpc): add unit and regression test suite for controller modules` | WBS 8.5 |
| **84d66fe** | 01/05/2026 | `test/system-regression` | TrungSy2106 | `test(system): add end-to-end integration tests for WebSocket loop` | WBS 8.6 |
| **273d44f** | 03/05/2026 | `test/system-regression` | MinhTris | `test(system): execute system robustness tests under signal dropouts` | WBS 8.6 |
| **3f26f96** | 04/05/2026 | `main` | MinhTris | *Merge branch 'test/system-regression' into main* | Tích hợp Test Suite |
| **393b5ca** | 05/05/2026 | `docs/final-report` | MinhTris | `docs(report): draft chapters on project management and SOW` | WBS 9.2 - 9.3 |
| **31c34fd** | 07/05/2026 | `docs/final-report` | TrungSy2106 | `docs(report): draft firmware schematics and dashboard interface` | WBS 9.2 - 9.3 |
| **0abdb57** | 08/05/2026 | `main` | MinhTris | *Merge branch 'docs/final-report' into main* | Tích hợp báo cáo hoàn chỉnh |
| **3c89475** | 09/05/2026 | `main` | MinhTris | `docs(presentation): compile presentation slide for final defense` | WBS 9.4 |
| **Tag `v1.0-final`**| 09/05/2026 | `main` | MinhTris | *Gắn thẻ tag `v1.0-final` tại phiên bản hoàn thiện nộp báo cáo* | Chuyển giao đồ án |
| **b9e4b49** | 10/05/2026 | `main` | MinhTris | `chore: synchronize repository with final local workspace state` | WBS 9.1 |
| **2bb6cee** | 11/05/2026 | `main` | MinhTris | `docs(readme): add updates to readme` | WBS 9.1 |

---

## 7.5 Quy trình Pull Request (PR) và Cổng kiểm chứng (Validation Gate)

### 7.5.1 Quy trình gửi Pull Request
Mỗi khi một nhánh `feature/*` hoặc `fix/*` được hoàn thành trên máy trạm của nhà phát triển, quy trình tích hợp được kiểm soát nghiêm ngặt:
1.  **Chạy test local**: Nhà phát triển chạy toàn bộ test suite để đảm bảo không phát sinh lỗi cú pháp hoặc làm hỏng các tính năng cũ.
2.  **Push và tạo PR**: Đẩy nhánh lên remote GitHub và tạo PR hướng về nhánh `main`. Mô tả PR phải ghi rõ ID công việc WBS liên quan và các kết quả kiểm thử.
3.  **Code Review**: Ít nhất một thành viên khác trong nhóm (không phải người viết code) phải xem xét thay đổi trực tiếp trên GitHub và để lại phê duyệt (Approve).

### 7.5.2 Thiết lập Cổng kiểm chứng (Validation Gate) tự động
Đặc biệt đối với các thay đổi liên quan đến thuật toán điều khiển tối ưu AI (`Kalman` và `MPC`), nhóm áp dụng quy trình kiểm chứng nghiêm ngặt để tránh gửi các lệnh tưới lỗi làm hỏng phần cứng thật. Validation Gate bắt buộc chạy thành công các lệnh sau:

*   **Kiểm tra lỗi cú pháp (Syntax check)**:
    ```powershell
    python -m compileall -q MPC\mpc
    ```
    Đảm bảo toàn bộ các file logic Python biên dịch thành công mà không có lỗi cú pháp tiềm ẩn.

*   **Kiểm tra bộ unit test và hồi quy (Unit & Regression testing)**:
    ```powershell
    python -m pytest MPC\tests -q
    ```
    Bộ test suite bao phủ toàn bộ 12 ca kiểm thử quan trọng bao gồm:
    *   *config loading*: Đọc cấu hình tưới an toàn, cấu hình FAO-56.
    *   *state adapter*: Cơ chế fallback an toàn về `pump_seconds = 0` khi mất tín hiệu cảm biến hoặc sensor bị trôi giá trị.
    *   *solver*: Đảm bảo thuật toán grid-shooting tìm ra lượng nước tối ưu trong vùng mục tiêu độ ẩm.
    *   *actuator guard*: Bảo vệ chặn không cho gửi lệnh bơm quá mức cho phép tối đa trong ngày.

Nếu một trong hai lệnh trên trả về lỗi (exit code khác 0), PR sẽ không đủ điều kiện để merge vào nhánh `main` và bắt buộc phải sửa đổi.

---

## 7.6 Đánh giá việc sử dụng Git/GitHub trong dự án

### 7.6.1 Ưu điểm đạt được
1.  **Tách biệt rủi ro phát triển**: Việc tách riêng các nhánh cho Kalman, MPC, Django backend giúp nhóm phát triển song song các mảng độ khó cao mà không cản trở nhau. Lỗi thuật toán AI trong quá trình nghiên cứu hoàn toàn cô lập trong nhánh phát triển và chỉ tích hợp khi đã vượt qua validation gate.
2.  **Truy vết lỗi nhanh chóng**: Nhờ lịch sử commit có cấu trúc rõ ràng gắn với từng mã WBS, khi xảy ra lỗi kết nối WebSocket giữa Dashboard và ESP32 ở tuần 7, nhóm dễ dàng khoanh vùng các commit có Scope `fw` và `backend` trong khoảng thời gian đó để xử lý nhanh chóng.
3.  **Bảo vệ mã nguồn an toàn**: Việc lưu trữ trên cloud GitHub công khai giúp giảng viên dễ dàng theo dõi tiến độ và nhóm có thể khôi phục mã nguồn an toàn khi máy cá nhân của thành viên gặp sự cố phần cứng.
4.  **Tự động hóa tài liệu**: Phụ lục báo cáo và danh sách thay đổi (changelog) của dự án được biên soạn nhanh chóng nhờ việc lọc log commit theo loại (`feat`/`fix`/`docs`).

### 7.6.2 Hạn chế
1.  **Rào cản học tập ban đầu**: Các thành viên trong nhóm có kinh nghiệm sử dụng Git không đồng đều dẫn đến một số lỗi conflict (xung đột mã nguồn) phức tạp khi thực hiện merge các file cấu hình lớn ở những tuần đầu tiên.
2.  **Chưa tận dụng hết tính năng quản lý công việc của GitHub**: Nhóm chủ yếu quản lý tiến độ và phân công công việc thông qua các công cụ bên ngoài (Trello, Zalo) thay vì tận dụng triệt để hệ thống GitHub Issues và GitHub Projects để liên kết trực tiếp các đầu việc với các Pull Request tương ứng trên repository.
3.  **Thiếu cơ chế tự động đồng bộ hóa môi trường cấu hình và CSDL**: Khi cơ sở dữ liệu MySQL ở local của thành viên phụ trách backend có thay đổi (chạy migrations mới trong Django), các thành viên khác pull code mới về thường gặp lỗi chạy local do lệch database schema, phải mất thêm thời gian đối chiếu và chạy cập nhật cơ sở dữ liệu thủ công.

---

## 7.7 Kết luận chương

Hệ thống quản lý mã nguồn bằng Git và GitHub đóng vai trò cốt lõi trong sự thành công và độ ổn định của dự án **Hệ thống Nhà kính Thông minh**. Repository `BapTruongSinh/Green_House_PBL` đã thể hiện một lịch sử phát triển có hệ thống, phản ánh đúng sơ đồ phân rã công việc WBS, lập lịch biểu chi tiết và phân chia vai trò nhân sự trong nhóm.

Quy trình phân nhánh chặt chẽ, quy tắc viết commit message chuẩn hóa cùng việc thực thi validation gate tự động giúp nhóm loại bỏ được phần lớn các lỗi tích hợp hệ thống, bảo vệ an toàn cho thiết bị thật. Đây là cơ sở thực tiễn quan trọng chứng minh tính chuyên nghiệp trong quản lý dự án công nghệ thông tin của nhóm, đóng góp trực tiếp vào sự hoàn thiện của báo cáo cuối kỳ.
