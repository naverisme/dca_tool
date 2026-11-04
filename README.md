# DCA · Document Curation & Assurance

DCA là bộ hướng dẫn để agent CLI biến một folder dữ liệu thô thành folder `docs/` có nội dung được viết lại, thống nhất và xếp theo **quy ước cố định của người dùng**. Mô hình và quyền đọc/ghi đến từ Codex, Antigravity hoặc agent đang chạy; repo này không cài một lệnh shell độc lập.

## Cách dùng

Sau khi [cài DCA](INSTALL.md), mở agent CLI tại dự án và gọi:

| Agent | Ví dụ |
| --- | --- |
| Codex | `$dca build "/đường-dẫn/bất-kỳ/raw" --output ./docs` |
| Antigravity | `/dca build "/đường-dẫn/bất-kỳ/raw" --output ./docs` |
| Agent đọc file | `Đọc dca/SKILL.md trong dca_tool; thực hiện dca build cho <folder-nguồn> và xuất ./docs.` |

`--output` trỏ thẳng tới folder tài liệu. Nguồn có thể nằm ngoài repo nếu agent có quyền đọc. DCA không sửa nguồn.

## Quy trình

1. Đọc toàn bộ nguồn trong phạm vi được giao và làm rõ mục tiêu bộ tài liệu. Phân biệt dữ kiện, đề xuất, ví dụ và quyết định đã được người có quyền xác nhận.
2. Chọn **profile tài liệu cố định**. Profile `software-v1` dùng cùng tên nhóm và file cho mọi dự án phần mềm. Với lĩnh vực khác chưa có profile, DCA hỏi để xác lập một profile dùng lại, không tự tạo cấu trúc khác nhau theo từng dự án.
3. Đối chiếu nội dung, gộp phần trùng, viết lại theo vị trí đã quy định. Chỉ tạo file có nội dung đủ rõ. Không chép câu rời rạc hay chỉ tạo chỉ mục tới nguồn.
4. Nếu có điểm mâu thuẫn, thiếu hoặc cần quyết định, tạo **một file** `docs-clarifications.md` bên cạnh `docs/`, gồm câu hỏi cụ thể, các cách hiểu và chỗ sẽ cập nhật. Không tự điền giả định vào docs.
5. Khi bạn trả lời trong phiên hoặc điền vào file câu hỏi, gọi `dca update <folder-nguồn> --output ./docs`. DCA kiểm tra câu trả lời, sửa các file docs bị ảnh hưởng và giữ lại chỉ những câu hỏi chưa giải quyết.

```text
<project>/
  docs/
    README.md
    product/
    requirements/
    ux/
    architecture/
    contracts/
    verification/
    operations/
  docs-clarifications.md   # chỉ có khi còn câu hỏi
```

Chỉ tạo nhóm và file có nội dung. Danh mục, tên file và ranh giới của `software-v1` nằm trong [quy ước tài liệu](dca/references/document-standard.md). Các phần cần làm rõ không trở thành quy tắc đã chốt.

**Quy tắc đầu ra:** Không đưa trích dẫn, tên hoặc đường dẫn của file thô, danh mục nguồn, bảng truy vết, manifest hay hồ sơ kiểm định vào `docs/` hoặc file câu hỏi. DCA vẫn phải đối chiếu nguồn **trong quá trình xử lý**; việc đối chiếu này không tự chứng minh nội dung đúng ngoài thực tế. Liên kết **giữa các tài liệu đã tạo trong docs** vẫn được phép. Chỉ ghi trạng thái `Đã duyệt` khi có xác nhận của người có quyền.

DCA không tự lập roadmap, chia task hoặc suy ra bước coding. [Hướng dẫn vận hành](dca/SKILL.md) · [Quy tắc kiểm định](dca/references/curation.md).