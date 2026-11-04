# Kiểm sơ đồ trước khi đưa vào docs

Sơ đồ là cách diễn đạt lại thông tin đã rõ, không tạo thêm quy tắc. Chỉ tạo khi có nhiều nhánh, trạng thái, quan hệ hoặc trao đổi khiến văn bản/bảng khó đọc; chọn ký pháp theo [bảng chọn](diagram-selection.md). Trong `software-v1`, đặt sơ đồ trong slot tài liệu đang mô tả nội dung đó, không tự tạo tên folder/file mới.

1. Xác định câu hỏi sơ đồ phải trả lời, đối tượng đọc, phạm vi và loại sơ đồ. Nếu không đủ thông tin để vẽ đúng một nhánh/quan hệ, đưa điều cần hỏi vào file clarifications; vẽ riêng phần độc lập nếu vẫn hữu ích.
2. Ánh xạ **nội bộ** từng thành phần và quan hệ về phát biểu đã được đối chiếu. Không chuyển dấu vết file thô, ID khảo sát, chú thích nguồn hoặc đường dẫn file thô vào sơ đồ hay tài liệu đầu ra.
3. Kèm mô tả bằng chữ về điều kiện, ngoại lệ, chiều mũi tên, bội số, đơn vị hoặc chú giải cần thiết. Kiểm sơ đồ không mâu thuẫn với tài liệu ở slot chính và không tự thêm chi tiết.
4. Kiểm cú pháp và render nếu có công cụ. Ghi rõ mức độ: minh họa khái niệm, dùng ký pháp thông dụng, hoặc bản tuân chuẩn **khi đã kiểm đủ yêu cầu và công cụ phù hợp**. Mermaid flowchart không tự thành BPMN, UML, bản vẽ điện/cơ khí đạt chuẩn.
5. Sau khi người dùng trả lời câu hỏi làm đổi logic, cập nhật cả sơ đồ và văn bản trong cùng lần `dca update`.

Không bắt buộc có sơ đồ; bảng và đoạn văn thường phù hợp hơn với định nghĩa hoặc ma trận quyền ngắn.