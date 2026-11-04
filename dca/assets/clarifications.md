# Cần làm rõ kỹ thuật · <Tên dự án>

File này nằm **ngang hàng với thư mục docs** (ví dụ: `docs-clarifications.md`) và chỉ tồn tại khi còn câu hỏi kỹ thuật chưa thể xác định dứt khoát từ nguồn thô. DCA tuyệt đối không đưa đường dẫn cá nhân, tên file thô hoặc trích dẫn rác vào đây.

| ID | Trụ cột liên quan | Câu hỏi kỹ thuật cần quyết định | Các phương án khả thi hoặc dữ kiện cần bổ sung | Ảnh hưởng đến slot docs | Phản hồi của người dùng |
|:---:|:---:|---|---|---|---|
| **Q-001** | `03-requirements` | Người dùng thường có được quyền xuất file báo cáo không? | A: Có quyền xuất PDF nhưng không được xuất CSV.<br>B: Cần quyền Quản trị viên mới được xuất bất kỳ định dạng nào. | `03-requirements/permissions.md`<br>`05-architecture/contracts.md` | *(Điền lựa chọn hoặc nhập trực tiếp)* |
| **Q-002** | `05-architecture` | Giao thức truyền tin giữa cảm biến và gateway là UART hay SPI? | A: Sử dụng UART tốc độ 115200 bps.<br>B: Sử dụng SPI tốc độ cao với chân CS riêng biệt. | `04-experience/screens.md`<br>`05-architecture/contracts.md` | *(Điền lựa chọn hoặc nhập trực tiếp)* |

---

### Hướng dẫn phản hồi:
1. Bạn có thể điền trực tiếp vào cột **Phản hồi của người dùng** trong file này, hoặc trả lời trực tiếp trong khung chat với Agent CLI theo cú pháp:  
   `Q-001: chọn A` hoặc `Q-002: chọn B, tốc độ 10MHz`.
2. Sau khi trả lời, chạy lệnh:  
   `dca update <folder-nguồn> --output ./docs`
3. DCA sẽ tự động phân giải logic, cập nhật đồng bộ toàn bộ chuỗi tài liệu liên quan (từ yêu cầu, kiến trúc, kiểm thử tới phiếu giao việc) và xóa bỏ mục đã giải quyết. Khi giải quyết hết tất cả các câu hỏi, file này sẽ tự động được thu hồi.
