# K26CNTT2_IT108_Session02_Ex03
# BÀI 3: THEO DÕI VÀ QUẢN LÝ TIẾN TRÌNH HỆ THỐNG

### 1. GIẢI THÍCH TÌNH HUỐNG QUA MÔ HÌNH "BAN QUẢN LÝ TÒA NHÀ"

- Cư dân là phần mềm và user <ex:> Chrome, VS Code gửi yêu cầu sử dụng tài nguyên.
- Lễ tân (Shell) nhận lệnh từ người dùng (click chuột, gõ phím) và chuyển giao cho ban quản lý.
- Ban quản lý tòa nhà (Kernel) trực tiếp phân phối tài nguyên phần cứng (CPU, RAM).
- Phòng làm việc (RAM) khi Chrome mở quá nhiều tab, dung lượng phòng bị chiếm tới 95%. Kernel buộc phải ép các ứng dụng xếp hàng chờ hoặc dùng không gian tạm ngoài sân Swap File, gây ra hiện tượng giật lag.



### 2. MÔ HÌNH IPO

- **Input (Đầu vào):** tín hiệu kích hoạt mở ứng dụng từ người dùng .
- **Process (Xử lý):**
  1. Shell chuyển lệnh đến Kernel.
  2. Kernel định vị file thực thi (.exe) trên storage (SSD/HDD).
  3. Kernel cấp phát không gian trong RAM và chép dữ liệu ứng dụng từ Storage vào RAM.
  4. CPU truy xuất mã lệnh từ RAM để khởi chạy tiến trình.
- **Output (Đầu ra):** giao diện ứng dụng hiển thị trên màn hình.



### 3. RÀNG BUỘC & BẪY DỮ LIỆU

### So sánh hiệu suất Swap File khi RAM đầy (SSD vs HDD):
- **SSD:** Tốc độ đọc/ghi ngẫu nhiên cao gấp nhiều lần HDD, giúp thao tác chuyển đổi dữ liệu (page swap) diễn ra nhanh hơn, máy ít bị đơ cứng.
- **HDD:** Tốc độ đọc/ghi chậm, đầu đọc cơ học bị quá tải khi truy xuất liên tục, dẫn đến lag nặng và treo hệ thống.


### 4. SƠ ĐỒ PHÂN TẦNG (ARCHITECTURE LAYERS) MỞ TRÌNH DUYỆT

```text
[ User ]
        │ (click icon Chrome)
        ▼
[ Trình duyệt Chrome ]
        │ (gửi sytem)
        ▼
[ User Interface ]
        │ (chuyển lệnh xuống hệ thống)
        ▼
[ Kernel ]
        │ (quản lý tiến trình & Cấp phát bộ nhớ RAM)
        ▼
[ CPU, RAM, Storage ]
