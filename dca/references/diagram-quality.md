# Kiểm tra chất lượng sơ đồ trước khi đưa vào docs

Sơ đồ là cách diễn đạt trực quan lại các thông tin và quy tắc đã được xác định rõ ràng, không tự ý tạo thêm quy tắc ngoài văn bản. Chỉ dựng sơ đồ khi có luồng công việc nhiều nhánh, máy trạng thái phức tạp, quan hệ thực thể hoặc giao thức trao đổi tuần tự khiến văn bản khó diễn đạt trọn vẹn; chọn ký pháp theo [bảng chọn sơ đồ](diagram-selection.md).

Trong cấu trúc 8 Trụ Cột của DCA, đặt sơ đồ trực tiếp vào slot tài liệu tương ứng (ví dụ: Context Diagram trong `02-scenarios/context.md`, Screen Flow / State Machine trong `04-experience/navigation.md`, ERD trong `05-architecture/data-model.md`, Sequence Diagram trong `05-architecture/contracts.md`, DAG trong `08-delivery/plan.md`), không tự tạo thêm thư mục tùy tiện.

---

## Quy trình kiểm soát chất lượng sơ đồ

1. **Xác định mục tiêu & đối tượng:** Sơ đồ giải quyết câu hỏi kỹ thuật nào, phục vụ vai trò nào (kiến trúc sư, lập trình viên, kiểm thử viên hay chuyên gia vận hành). Nếu thiếu dữ kiện để vẽ trọn vẹn một nhánh logic, đưa câu hỏi vào file clarifications; tuyệt đối không tự vẽ phỏng đoán.
2. **Đối chiếu nội bộ:** Ánh xạ từng khối, mũi tên, nhãn và điều kiện rẽ nhánh về đúng mã yêu cầu (`REQ-xxx`) hoặc hợp đồng (`CTR-xxx`). Không đưa đường dẫn file thô hay dữ liệu tạm vào sơ đồ.
3. **Mô tả văn bản đi kèm:** Mọi sơ đồ phải có đoạn văn hoặc bảng đi kèm giải thích rõ điều kiện tiên quyết, ý nghĩa chiều mũi tên, các mã lỗi ngoại lệ, đơn vị đo lường hoặc chú giải ký hiệu.
4. **Kiểm tra cú pháp & tính tương thích:**
   - Đảm bảo cú pháp Mermaid hợp lệ, render tốt trên các nền tảng phổ biến (GitHub, GitLab, Obsidian, IDE preview).
   - Tránh nhầm lẫn ký pháp: Một `flowchart` Mermaid không tự động trở thành một quy trình BPMN chuẩn, một sơ đồ mạch điện IEC hay một bản vẽ cơ khí ISO. Ghi rõ mức độ chuẩn hóa (sơ đồ khái niệm vs tuân thủ đặc tả).
5. **Cập nhật đồng bộ:** Khi có thay đổi từ người dùng thông qua `dca update`, phải cập nhật đồng thời cả văn bản đặc tả và sơ đồ trực quan để bảo đảm tính nhất quán tuyệt đối.
