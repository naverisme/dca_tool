# Chọn loại sơ đồ và ký pháp trong 8 Trụ Cột DCA

## 1. Quy tắc chọn sơ đồ

1. **Xác định mục tiêu & đối tượng:** Sơ đồ phải trả lời câu hỏi gì: phạm vi chức năng, quy trình, quyết định, thứ tự trao đổi, vòng đời trạng thái, cấu trúc dữ liệu hay phân rã hệ thống?
2. **Xác định mức độ chuẩn hóa:** Minh họa khái niệm (conceptual illustration), dùng ký pháp thông dụng (informal notations), hay phải tuân thủ nghiêm ngặt một tiêu chuẩn kỹ nghệ (OMG UML, BPMN, DMN, SysML, ISO/IEC/IEEE). Ghi rõ cơ sở chọn; không tùy tiện tuyên bố tuân chuẩn nếu chỉ dùng Mermaid đơn giản.
3. **Độ đầy đủ của dữ kiện:** Đầu vào phải có đầy đủ thực thể, quan hệ, điều kiện rẽ nhánh, hướng mũi tên, mã lỗi ngoại lệ trước khi vẽ. Nếu thiếu dữ kiện cốt lõi, ghi câu hỏi vào file clarifications; chỉ vẽ phần đã đủ căn cứ xác thực.
4. **Vị trí lưu trữ chuẩn:** Sơ đồ phải được nhúng trực tiếp vào đúng slot tài liệu trong **8 Trụ cột**, không tạo thư mục hình ảnh phân mảnh rời rạc ngoài quy ước.

---

## 2. Bảng ánh xạ sơ đồ vào 8 Trụ Cột

| Cần làm rõ | Loại sơ đồ / Ký pháp khuyến nghị | Slot đặt sơ đồ trong 8 Trụ cột | Dữ kiện bắt buộc và điều cần kiểm | Tránh nhầm lẫn với |
| --- | --- | --- | --- | --- |
| Ranh giới hệ thống & tác nhân bên ngoài | Context Diagram (C4 Context hoặc SysML Context) | `02-scenarios/context.md` | Ranh giới hệ thống, danh sách tác nhân (người, hệ thống ngoài, thiết bị), kênh kết nối | Sơ đồ kiến trúc module chi tiết bên trong |
| Ai dùng hệ thống để đạt mục tiêu gì | UML Use Case 2.5.1 | `02-scenarios/use-cases.md` | Tác nhân bên ngoài, ranh giới, mục tiêu; `include`/`extend` chỉ khi đúng nghĩa UML | Luồng thao tác tuần tự theo thời gian |
| Công việc diễn ra qua các vai trò ra sao | BPMN 2.0.2 hoặc Flowchart có Swimlane | `02-scenarios/workflows.md` | Sự kiện bắt đầu/kết thúc, hoạt động, gateway điều kiện, pool/lane rõ ràng | Luồng tuần tự API giữa các service |
| Điều kiện logic dẫn đến quyết định nào | DMN 1.5 Decision Table hoặc Decision Requirements Diagram | `03-requirements/business-rules.md` | Bảng điều kiện đầu vào, đầu ra, hit policy, kiểm tra tính đầy đủ và không chồng chéo | Quy trình công việc BPMN |
| Điều hướng giữa các màn hình / trạng thái | Screen Navigation Flow / Wireflow | `04-experience/navigation.md` | Danh sách màn hình, hành động kích hoạt (click, swipe), hướng chuyển trang | Sơ đồ kiến trúc phần mềm |
| Vòng đời & chuyển tiếp trạng thái | UML State Machine 2.5.1 hoặc Mermaid State | `04-experience/interaction-states.md` | Trạng thái (idle, loading, error...), sự kiện kích hoạt, điều kiện guard, chuyển tiếp cấm | Quy trình công việc nhiều đối tượng |
| Kiến trúc tổng thể & phân rã module | C4 Container/Component hoặc ISO/IEC/IEEE 42010 Viewpoint | `05-architecture/system.md`, `05-architecture/modules.md` | Ranh giới module, trách nhiệm, hướng phụ thuộc (cấm vòng), quyền sở hữu dữ liệu (Data Ownership) | Tự gọi flowchart tùy ý là chuẩn 42010 |
| Cấu trúc thực thể và quan hệ dữ liệu | ERD (Chen / Crow's Foot) hoặc UML Class 2.5.1 | `05-architecture/data-model.md` | Thực thể logic/vật lý, thuộc tính, khóa chính/ngoại, lực lượng quan hệ (1-1, 1-N, N-N) | Bảng luồng dữ liệu (DFD) |
| Thứ tự trao đổi thông điệp / API giữa các phần | UML Sequence 2.5.1 hoặc Mermaid Sequence | `05-architecture/contracts.md` | Đối tượng tham gia (lifelines), thông điệp đồng bộ/bất đồng bộ, mã lỗi, nhánh phản hồi | Sơ đồ use-case tổng quát |
| Luồng kiểm thử & ma trận nghiệm thu | Verification Flowchart / Test Harness Diagram | `06-verification/test-strategy.md` | Các bước thiết lập fixture, kích hoạt test case, điểm đo lường và assertions | Luồng nghiệp vụ của người dùng cuối |
| Đồ thị phụ thuộc triển khai công việc | DAG (Directed Acyclic Graph) / Pert Chart | `08-delivery/plan.md` | Các mã task (`TASK-xxx`), hướng mũi tên phụ thuộc (A làm xong mới đến B), đường găng (critical path) | Roadmap thời gian không có quan hệ phụ thuộc |

---

## 3. Tiêu chuẩn tham chiếu

- **OMG UML 2.5.1:** [https://www.omg.org/spec/UML/2.5.1](https://www.omg.org/spec/UML/2.5.1)
- **OMG BPMN 2.0.2:** [https://www.omg.org/spec/BPMN/2.0.2](https://www.omg.org/spec/BPMN/2.0.2)
- **OMG DMN 1.5:** [https://www.omg.org/spec/DMN/1.5/](https://www.omg.org/spec/DMN/1.5/)
- **ISO/IEC/IEEE 42010:2022 (Architecture Description):** [https://www.iso.org/standard/74393.html](https://www.iso.org/standard/74393.html)
