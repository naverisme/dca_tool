# DCA · Document Curation & Assurance

DCA là bộ công cụ và hướng dẫn quy chuẩn dành cho các Agent CLI (Codex, Antigravity,...) nhằm chuyển hóa toàn bộ dữ liệu thô, ghi chú hỗn độn hoặc tài liệu dự án chưa hoàn chỉnh thành một bộ thư mục `docs/` kỹ thuật chuẩn mực theo **8 Trụ Cột Kỹ Nghệ Hệ Thống**, có tính truy vết cao và sẵn sàng giao việc trực tiếp cho lập trình viên hoặc coding agent.

---

## 8 Trụ Cột Kỹ Nghệ Chuẩn (8 Engineering Pillars)

Bộ tài liệu do DCA sinh ra được tổ chức cố định thành 8 nhóm thư mục có đánh số thứ tự tuần tự:

| STT | Trụ Cột | Mục đích & Trả lời câu hỏi | Căn cứ & Giá trị đầu ra |
|:---:|---|---|---|
| **1** | **Định nghĩa sản phẩm** (`01-product/`) | Xây cho ai, giải quyết vấn đề gì, kết quả mong muốn là gì, phạm vi bản đầu đến đâu? | Danh sách mục tiêu đo lường được (`GOAL-xxx`) và giới hạn ranh giới để xét từng yêu cầu. |
| **2** | **Ngữ cảnh và kịch bản sử dụng** (`02-scenarios/`) | Ai hoặc hệ thống nào tương tác? Họ thực hiện việc gì từ đầu đến cuối? Các tình huống lỗi là gì? | Các luồng hành vi thực tế đầu-cuối (`UC-xxx`) để bóc tách yêu cầu cụ thể. |
| **3** | **Đặc tả yêu cầu** (`03-requirements/`) | Sản phẩm phải làm gì, theo quy tắc nào, đạt chỉ tiêu nào? | Mỗi yêu cầu có mã riêng (`REQ-xxx`), nguồn gốc từ mục tiêu và điều kiện kiểm tra sơ bộ. Căn cứ cốt lõi để thiết kế. |
| **4** | **Thiết kế trải nghiệm hoặc vận hành** (`04-experience/`) | Người dùng, thiết bị hoặc hệ thống khác tương tác qua điểm nào? Mỗi thao tác gây ra kết quả gì? | Màn hình giao diện (UI), tập lệnh tham số (CLI) hoặc tín hiệu/giao thức ngoài (IoT/phần cứng) cần triển khai. |
| **5** | **Thiết kế kiến trúc và hợp đồng giữa các phần** (`05-architecture/`) | Có những thành phần nào, phần nào sở hữu dữ liệu, chúng trao đổi thế nào, lỗi được xử lý ở đâu? | Ranh giới module (`MOD-xxx`), quyền sở hữu dữ liệu (Data Ownership), mô hình ERD, hợp đồng giao tiếp (`CTR-xxx`) và quyết định kỹ thuật (`ADR-xxx`) để chia việc. |
| **6** | **Kế hoạch kiểm chứng** (`06-verification/`) | Làm cách nào chứng minh từng yêu cầu đã đạt? Cần dữ liệu, thiết bị, phép đo hoặc ca thử nào? | Danh mục ca kiểm chứng chi tiết (`TC-xxx`) và tiêu chí hoàn thành cụ thể (Definition of Done) cho từng gói việc. |
| **7** | **Bảng truy vết** (`07-traceability/`) | Mục tiêu nào sinh ra yêu cầu nào? Thiết kế và ca kiểm tra nào đáp ứng yêu cầu đó? | Ma trận đối soát 2 chiều; phát hiện yêu cầu chưa có thiết kế hoặc chưa có cách kiểm tra (Gap Analysis). |
| **8** | **Kế hoạch triển khai và phiếu giao việc** (`08-delivery/`) | Việc nào làm trước, việc nào phụ thuộc việc khác, ai được sửa phần nào và bàn giao bằng chứng gì? | Các nhiệm vụ độc lập (`TASK-xxx`) đủ rõ ràng kèm whitelist file được sửa và bằng chứng nghiệm thu để giao trực tiếp cho kỹ sư hoặc coding agent bắt tay vào code ngay. |

---

## Cấu trúc thư mục tài liệu đầu ra

```text
<project-root>/
  docs/
    README.md
    01-product/
      overview.md
      scope.md
      glossary.md
    02-scenarios/
      context.md
      use-cases.md
      workflows.md
    03-requirements/
      srs.md
      business-rules.md
      permissions.md
    04-experience/
      screens.md
      navigation.md
      interaction-states.md
    05-architecture/
      system.md
      modules.md
      data-model.md
      contracts.md
      decisions.md
    06-verification/
      test-strategy.md
      acceptance-tests.md
      definition-of-done.md
    07-traceability/
      matrix.md
      gap-analysis.md
    08-delivery/
      plan.md
      task-packages.md
      readiness.md
  docs-clarifications.md   # Chỉ xuất hiện khi còn câu hỏi kỹ thuật cần chốt
```

---

## Cách sử dụng

Sau khi [cài DCA](INSTALL.md), bạn có thể gọi trực tiếp trong phiên làm việc của Agent CLI:

| Môi trường | Cú pháp ví dụ |
| --- | --- |
| **Codex** | `$dca build "./raw_data" --output ./docs` |
| **Antigravity** | `/dca build "./raw_data" --output ./docs` |
| **Agent CLI khác** | Đọc `dca/SKILL.md` trong repo `dca_tool`; thực hiện `dca build <folder-nguồn> --output ./docs` |

### Các lệnh chính:
- `dca help`: Xem cấu trúc 8 trụ cột và quy tắc vận hành.
- `dca build <folder-nguồn> [--output ./docs]`: Đọc toàn bộ tài liệu nguồn thô, bóc tách và tạo cấu trúc 8 trụ cột. Nếu có điểm mâu thuẫn hoặc thiếu thông tin, tự động tạo file `docs-clarifications.md`.
- `dca update <folder-nguồn> [--output ./docs]`: Đọc câu trả lời của người dùng (trong chat hoặc trong file câu hỏi), cập nhật đồng bộ toàn bộ các tài liệu liên quan trong `docs/` và dọn dẹp câu hỏi đã giải quyết.
- `dca trace [--output ./docs]`: Kiểm tra và đối soát tính toàn vẹn của ma trận truy vết và phát hiện các yêu cầu mồ côi hoặc ca thử thiếu.
- `dca diagram <chủ-đề> [--output ./docs]`: Sinh hoặc tối ưu sơ đồ trực quan (Mermaid/UML) vào đúng vị trí slot tài liệu.

---

## Quy tắc chất lượng đầu ra

1. **Tuyệt đối không rò rỉ rác thô:** Không đưa đường dẫn tuyệt đối máy tính cá nhân, tên file thô ngẫu nhiên, danh mục nguồn chưa xử lý hay đoạn trích thô vào thư mục `docs/`.
2. **Truy vết 2 chiều khép kín:** Mỗi mục tiêu sinh ra yêu cầu, mỗi yêu cầu dẫn đến thiết kế và bài test, mỗi bài test và module dẫn đến phiếu giao việc cụ thể.
3. **Sẵn sàng cho việc lập trình:** Thư mục `08-delivery/` cung cấp các phiếu giao việc (`TASK-xxx`) hoàn toàn độc lập, quy định rõ file được sửa, file cấm sửa và bằng chứng kiểm thử cần nộp để lập trình viên hoặc coding agent làm việc ngay lập tức mà không phải phỏng đoán.
