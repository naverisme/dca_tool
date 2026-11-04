# DCA · Document Curation & Assurance

DCA biến một tập tài liệu thô thành **bộ tài liệu theo chủ đề, có nội dung được biên soạn lại và dẫn nguồn**. Nó đối chiếu các phát biểu, tách phần mâu thuẫn hoặc thiếu căn cứ ra khu vực rà soát, rồi chỉ đưa phần đạt điều kiện kiểm định vào `docs/`. DCA cũng có thể tạo sơ đồ phù hợp với loại thông tin, khi sơ đồ giúp người đọc hiểu hơn.

Đây là gói quy trình cho agent dùng trong phiên làm việc, không phải chương trình dòng lệnh độc lập. Codex, Antigravity hoặc agent khác cung cấp mô hình và quyền truy cập file; `dca/SKILL.md` cùng các tài liệu kèm theo quy định cách DCA làm việc. Gói dùng được với nhiều lĩnh vực, không mặc định dự án phần mềm hay Snote.

## Bắt đầu

Clone repo và đọc [INSTALL.md](INSTALL.md) để cài ở cấp người dùng hoặc cấp dự án. Sau đó, trong phiên agent đang mở tại dự án hoặc thư mục làm việc bạn chọn, gọi theo giao diện của agent:

| Môi trường | Ví dụ gọi |
| --- | --- |
| Codex | `$dca help`, `$dca build /đường-dẫn/nguồn-thô --output ./docs` |
| Antigravity | `/dca help`, `/dca build /đường-dẫn/nguồn-thô --output ./docs` |
| Agent khác đọc file | `Đọc <đường-dẫn>/dca_tool/dca/SKILL.md rồi thực hiện dca build <folder-nguồn> --output ./docs.` |

Các từ `build`, `audit` hoặc `diagram` là thao tác được agent diễn giải theo gói hướng dẫn. Chúng không phải lệnh shell `dca` và repo này không cài một binary tên `dca`.

Ví dụ, nếu hai file nguồn bất đồng về quyền xem checklist, DCA ghi cả hai nguồn và điểm chưa phân xử trong `docs-review/unresolved.md`. Nó không viết một quy tắc quyền tùy chọn vào `docs/`. Các phần khác đủ căn cứ vẫn có thể được biên soạn thành tài liệu dùng trực tiếp.

## Đầu ra của `build`

`--output` trỏ **thẳng tới folder docs**. Nếu bỏ qua, DCA dùng `./docs`. Hồ sơ rà soát mặc định ở folder ngang hàng `./docs-review`, hoặc đường dẫn được chọn bằng `--review-output`.

```text
<parent>/
  docs/
    README.md               Mục tiêu, phạm vi, mốc nguồn và bản đồ chủ đề
    <danh-mục>/
      README.md             Phạm vi danh mục
      <chủ-đề>.md           Nội dung đã biên soạn và dẫn nguồn tại chỗ
      <sơ-đồ>.md            Chỉ tạo khi hữu ích và có đủ căn cứ
  docs-review/
    README.md               Độ phủ và giới hạn kiểm định
    provenance.md           Dấu vết nguồn → mệnh đề → tài liệu
    unresolved.md           Mâu thuẫn, mơ hồ, thiếu bằng chứng
    manifest.md             Mốc nguồn và danh sách file DCA sở hữu
    blocked/                Bản nháp bị chặn, nếu cần
```

Trước khi ghi, DCA xác định mục tiêu bộ dữ liệu tài liệu, lĩnh vực và người đọc; đề xuất cấu trúc và quy cách trình bày khi chưa có quy ước. Nó trao đổi với bạn nếu có nhiều phương án ảnh hưởng đáng kể tới ý nghĩa hoặc tổ chức tài liệu. Tên danh mục được chọn từ nội dung nguồn và quy ước đã chốt; không áp một cây thư mục cố định cho mọi lĩnh vực. `docs/` là tài liệu đã được biên soạn để đọc trực tiếp, không phải danh sách đường dẫn trở lại file thô. `DCA-checked` có nghĩa là đã đối chiếu trong phạm vi khảo sát; chỉ ghi `approved` khi có chứng cứ người có quyền đã phê duyệt. Tệp nguồn không bị di chuyển hoặc sửa bởi `build`.

## Các thao tác

| Thao tác | Công dụng | Ghi file mặc định |
| --- | --- | --- |
| `help` | Phiên bản, cách gọi | Không |
| `init [phạm vi]` | Xác định nguồn, mốc, giới hạn | Không |
| `inventory [phạm vi]` | Kiểm kê nguồn và độ phủ | Không |
| `audit [chủ đề]` | Phát hiện mâu thuẫn, mơ hồ, thiếu, lặp, cũ | Không |
| `organize [phạm vi]` | Đề xuất danh mục và nơi lưu chính | Không |
| `normalize [tệp/chủ đề]` | Xem trước chuẩn hóa thuật ngữ, cấu trúc | Không |
| `verify [mệnh đề/phạm vi]` | Kiểm chứng một phát biểu theo nguồn | Không |
| `explain [câu hỏi]` | Giải thích có dẫn chứng và giới hạn | Không |
| `sync [phạm vi]` | Đối chiếu nguồn mới với tài liệu chuẩn | Không |
| `diagram [chủ đề]` | Chọn loại sơ đồ và tạo bản có truy nguồn | Không |
| `diagram-check [sơ đồ]` | Rà sơ đồ so với nguồn và ký pháp | Không |
| `build <folder-nguồn> [--output <folder-docs>] [--review-output <folder-review>]` | Xuất trực tiếp folder docs và hồ sơ review bên cạnh | Có, tại hai đích đã chọn |
| `apply <draft-id>` | Ghi đúng bản nháp đã chọn sau khi kiểm lại đích | Có, tại tệp đích |

`organize`, `normalize` và `diagram` chỉ lưu bản nháp với `--draft` khi được yêu cầu. `apply` kiểm lại mốc và khác biệt trước khi ghi. DCA không tự quyết định ý nghĩa nghiệp vụ đang tranh chấp và không lập kế hoạch coding hay giai đoạn tiếp theo.

## Thành phần gói

| Đường dẫn | Vai trò |
| --- | --- |
| [INSTALL.md](INSTALL.md) | Cài, kiểm tra, cập nhật, gỡ |
| [dca/SKILL.md](dca/SKILL.md) | Điểm vào và hợp đồng thao tác |
| [dca/references/](dca/references/) | Bằng chứng, chuẩn hóa, xuất bản, đầu ra và sơ đồ |
| [dca/assets/](dca/assets/) | Mẫu tài liệu và sổ kiểm định |
| [dca/VERSION](dca/VERSION) | Phiên bản gói |

Cơ chế nạp skill: [Codex](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) và [Antigravity](https://antigravity.google/docs/skills/). Quyền truy cập file và dữ liệu do môi trường agent đang chạy kiểm soát.
