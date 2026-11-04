# Chuyển tài liệu thành sơ đồ và kiểm định

## Trình tự

1. Xác định câu hỏi, đối tượng đọc, mức hình thức, ranh giới và mốc nguồn. Nếu không có nhu cầu rõ, nêu lựa chọn bảng/văn bản thay vì vẽ bắt buộc.
2. Dùng [bảng chọn ký pháp](diagram-selection.md). Nêu tên và phiên bản tiêu chuẩn nếu đã kiểm tra được; phân biệt chuẩn ký pháp với công cụ xuất ảnh/mã. Nếu chỉ có Mermaid cho một loại không được hỗ trợ trung thực, chọn sơ đồ khái niệm có nhãn hoặc báo cần công cụ tương ứng.
3. Lập bảng mệnh đề đầu vào có ID và vị trí nguồn. Chuyển thành phần tử: tác nhân, activity, sự kiện, trạng thái, thực thể, cổng, kết nối... Chỉ vẽ quan hệ/nhánh có căn cứ. Chỗ mơ hồ ảnh hưởng đường đi phải giữ mở và hỏi người có quyền; có thể chỉ vẽ phần độc lập.
4. Viết mô tả bằng chữ cho điều kiện, hướng mũi tên, ngoại lệ, bội số, chú giải, đơn vị và trạng thái. Nếu sơ đồ là đề xuất từ suy luận, ghi rõ `INFERRED` hoặc `PROPOSED`; không trộn vào hiện trạng `VERIFIED`.
5. Sinh sơ đồ trong định dạng được yêu cầu và công cụ hiện có hỗ trợ. Với Mermaid trong GitHub, kiểm tra [cách GitHub xác định phiên bản Mermaid](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams); không giả định mọi cú pháp mới đều render. Với chuẩn kỹ thuật cần ký hiệu chuyên ngành, dùng công cụ/vật liệu đủ khả năng; nếu không có, giao mô hình văn bản/bảng và nói chưa tạo bản vẽ chuẩn.
6. Kiểm hai lớp: **ngữ nghĩa** (mọi nút/cạnh/nhánh truy về nguồn, không bỏ ngoại lệ, không thêm điều kiện); **ký pháp** (đúng loại thành phần, quan hệ, chiều, nhãn và các ràng buộc của tiêu chuẩn/phiên bản thực sự dùng). Kiểm render trực quan khi có trình render, kiểm file/đường dẫn và đặt nhãn khi chưa render được. Không tuyên bố “tuân chuẩn” nếu mới chỉ so phần tóm tắt công khai của tiêu chuẩn.
7. Trả sơ đồ cùng [hồ sơ](../assets/diagram-record.md): mục đích, lựa chọn, căn cứ nguồn, mức tuân ký pháp, giả định, phát hiện còn mở và điểm chưa kiểm. `diagram-check` có kết quả `PASS`, `FAIL`, `UNVERIFIED` theo từng quy tắc có nguồn, không chỉ đánh giá đẹp/xấu.

## Những nhầm lẫn cần bắt

- UML Use Case có mũi tên theo thứ tự các bước: sai mục đích; thay bằng mô tả luồng/BPMN/Activity khi cần.
- Swimlane vẽ bằng Mermaid flowchart tự gắn nhãn BPMN: chỉ là diễn giải, thiếu ngữ nghĩa events/gateways/flows.
- Bảng quyết định thiếu trường hợp hoặc có hai luật cùng khớp nhưng không nêu hit policy: chưa đủ để gọi DMN đã kiểm định.
- State diagram không có sự kiện/guard hoặc có nhánh không thể tới: thiếu ngữ nghĩa vòng đời.
- ERD không rõ 0..1, 1..n hay bắt buộc: chưa đủ xác nhận bội số.
- Sơ đồ điện/khí nén hay bản vẽ cơ khí chỉ có các hộp và mũi tên: đó là sơ đồ nguyên lý khái niệm, không phải bản vẽ theo chuẩn kỹ thuật.

Không tự sinh thêm sơ đồ khác, kế hoạch triển khai hoặc task khi người dùng chỉ yêu cầu một sơ đồ.
