---
name: dca
description: Biến folder dữ liệu thô thành bộ tài liệu kỹ thuật chuẩn gồm 8 trụ cột khép kín (Định nghĩa sản phẩm, Ngữ cảnh, Yêu cầu, Trải nghiệm/Vận hành, Kiến trúc & Hợp đồng, Kiểm chứng, Bảng truy vết, Kế hoạch & Phiếu giao việc); hỗ trợ quản lý câu hỏi làm rõ và cập nhật đồng bộ.
---

# DCA · Document Curation & Assurance Agent

DCA là quy trình chuẩn hóa tài liệu kỹ thuật chạy **bên trong agent CLI**. Agent chủ (Codex, Antigravity,...) cung cấp mô hình trí tuệ, công cụ thao tác file và môi trường thực thi; DCA cung cấp bộ quy tắc phân loại, tiêu chuẩn cấu trúc 8 trụ cột kỹ nghệ và thuật toán đối chiếu logic chặt chẽ.

| Lệnh gọi | Kết quả thực thi |
| --- | --- |
| `dca help` | Hiển thị hướng dẫn cú pháp, cấu trúc 8 trụ cột và phiên bản hiện tại |
| `dca build <folder-nguồn> [--output <folder-docs>]` | Đọc dữ liệu thô, biên soạn thành bộ tài liệu chuẩn 8 trụ cột và sinh file câu hỏi nếu còn thiếu dữ kiện |
| `dca update <folder-nguồn> [--output <folder-docs>]` | Đọc phản hồi của người dùng, phân giải câu hỏi, cập nhật đồng bộ toàn bộ các slot docs bị ảnh hưởng |
| `dca diagram <chủ-đề> [--output <folder-docs>]` | Thêm hoặc tối ưu hóa sơ đồ kỹ thuật vào đúng slot tài liệu tương ứng |
| `dca trace [--output <folder-docs>]` | Rà soát toàn bộ ma trận truy vết và phân tích khoảng trống (`gap-analysis.md`) giữa yêu cầu, thiết kế, bài test và phiếu giao việc |

> Hỗ trợ các cú pháp gọi tương thích: `dca ...`, `/dca ...`, `$dca ...`.  
> Tham số `--output` mặc định là `./docs` từ thư mục làm việc hiện tại.

---

## Chuẩn cấu trúc 8 Trụ Cột (8 Engineering Pillars)

Mọi bộ tài liệu sinh ra bởi DCA đều tuân thủ nghiêm ngặt 8 nhóm thư mục có đánh số thứ tự logic:

```text
<project-root>/
  docs/
    README.md
    01-product/         # 1. Định nghĩa sản phẩm (Bài toán, người dùng, phạm vi MVP, mục tiêu & giới hạn)
    02-scenarios/       # 2. Ngữ cảnh & Kịch bản sử dụng (Tác nhân, luồng đầu-cuối, xử lý sự cố)
    03-requirements/    # 3. Đặc tả yêu cầu (Mã FR/NFR, quy tắc nghiệp vụ, ma trận quyền)
    04-experience/      # 4. Thiết kế trải nghiệm hoặc vận hành (Điểm chạm giao diện/lệnh/tín hiệu, luồng, trạng thái)
    05-architecture/    # 5. Kiến trúc & Hợp đồng (Ranh giới module, dữ liệu, API/giao thức, quyết định ADR)
    06-verification/    # 6. Kế hoạch kiểm chứng (Chiến lược đo kiểm, ca thử nghiệm TC-xxx, tiêu chí DoD)
    07-traceability/    # 7. Bảng truy vết (Ma trận truy vết 2 chiều, báo cáo phát hiện lỗ hổng/yêu cầu mồ côi)
    08-delivery/        # 8. Kế hoạch triển khai & Phiếu giao việc (DAG tiến độ, phiếu giao việc TASK-xxx cho người/agent)
  docs-clarifications.md  # Chỉ xuất hiện khi còn câu hỏi kỹ thuật cần người dùng chốt
```

---

## Hợp đồng thực thi của DCA

1. **Tuân thủ Slot tài liệu cố định:** Trước khi tạo file, đối chiếu với [Quy ước tài liệu chuẩn](references/document-standard.md). Không tự sáng tác tên thư mục hoặc tên file tùy tiện. Chỉ tạo những file có thông tin đủ căn cứ; tạo `docs/README.md` làm chỉ mục tổng quan.
2. **Quy trình lọc & biên soạn:** Đọc [Quy trình lọc và biên soạn](references/curation.md). Bóc tách phát biểu thô, chuẩn hóa định dạng, gắn mã định danh chuẩn (`GOAL-xxx`, `UC-xxx`, `REQ-FR-xxx`, `REQ-NFR-xxx`, `CTR-xxx`, `TC-xxx`, `TASK-xxx`). Giữ đúng bản chất logic kỹ thuật, không tự ý suy diễn hoặc bịa đặt dữ liệu.
3. **Tuyệt đối không rò rỉ rác thô:** Không đưa đường dẫn thư mục cá nhân, tên file thô ngẫu nhiên, trích dẫn văn bản chưa xử lý vào `docs/` hay file câu hỏi. Mọi liên kết phải là liên kết Markdown nội bộ tương đối giữa các file trong `docs/`.
4. **Quản trị câu hỏi kỹ thuật (`clarifications.md`):** Khi gặp mâu thuẫn hoặc thiếu tham số cốt tử, ghi ngay vào `<tên-folder-docs>-clarifications.md` theo [mẫu câu hỏi](assets/clarifications.md). Mỗi câu hỏi có ID ổn định (`Q-001`, `Q-002`,...). Các phần độc lập khác vẫn phải được hoàn thiện bình thường.
5. **Cơ chế cập nhật (`dca update`):** Khi người dùng cung cấp câu trả lời, DCA rà soát và cập nhật đồng bộ chuỗi liên kết (từ yêu cầu → kiến trúc/hợp đồng → ca kiểm thử → phiếu giao việc). Xóa câu hỏi đã giải quyết; khi không còn câu hỏi nào mở, tự động dọn dẹp file câu hỏi.
6. **Bảo đảm tính truy vết & khả năng thực thi:**
   - Lập ma trận tại `07-traceability/matrix.md` từ các mã đã có căn cứ; giữ ô thiếu và ghi khoảng trống trong `gap-analysis.md`. Không tạo thiết kế hay ca kiểm chứng giả để làm ma trận trông khép kín.
   - Chỉ viết kế hoạch và phiếu giao việc tại `08-delivery/` khi mục tiêu, yêu cầu, thiết kế, phụ thuộc và tiêu chí bàn giao đã đủ căn cứ. Chỉ định ranh giới file khi đã biết cấu trúc dự án; không tự bịa đường dẫn, công sức, người phụ trách hay lịch. Thiếu điều kiện nào thì ghi câu hỏi cần làm rõ và trạng thái chưa sẵn sàng. DCA chỉ chuẩn bị tài liệu, không thực thi nhiệm vụ hay viết mã.
7. **Tiêu chuẩn sơ đồ:** Áp dụng [Bảng chọn sơ đồ](references/diagram-selection.md) và [Quy tắc kiểm sơ đồ](references/diagram-quality.md). Sơ đồ phải gắn chặt với ngữ cảnh trong slot tài liệu, cú pháp chuẩn xác và có chú giải bằng lời đi kèm.
