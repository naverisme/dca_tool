# Từ nguồn thô thành bộ docs có kiểm định

`build <folder-nguồn> [--output <folder-docs>] [--review-output <folder-review>]` đọc tập nguồn ở bất kỳ đường dẫn nào agent được phép đọc, tách và đối chiếu phát biểu, rồi **biên soạn lại thành tài liệu theo chủ đề để người đọc dùng trực tiếp**. `--output` trỏ thẳng đến folder docs, mặc định `./docs` trong thư mục làm việc. Folder review mặc định là folder ngang hàng mang tên `<tên-folder-docs>-review` (ví dụ `./docs-review`); `--review-output` cho phép chọn đường dẫn khác. Không di chuyển hoặc sửa nguồn. Không quét lại folder đầu ra như nguồn.

## Cổng lọc trước khi biên soạn

Chỉ đưa một phát biểu vào `docs/` khi đã kiểm tra:

1. **Nguồn và thẩm quyền:** vị trí, phiên bản, phạm vi và loại bằng chứng đủ cho điều được khẳng định; quyết định đã duyệt có chứng cứ riêng.
2. **Nghĩa:** chủ thể, hành động, đối tượng, điều kiện, ngoại lệ và thời điểm rõ để người đọc không phải mở file thô mới hiểu.
3. **Nhất quán:** đã đối chiếu mọi nguồn liên quan trong phạm vi; không còn mâu thuẫn trọng yếu chưa giải quyết về phát biểu đó.
4. **Truy vết:** có trích dẫn ngay trong tài liệu, dẫn đến bản gốc và vị trí; diễn giải không đổi nghĩa và không được nâng suy luận thành quy tắc.

Nội dung trượt cổng nằm ở `<folder-review>/unresolved.md` hoặc một bản nháp trong `<folder-review>/blocked/` khi cần giữ đủ ngữ cảnh; **không** đặt vào `docs/` như quy định đã xác minh. Có thể biên soạn những phần độc lập đã đạt cổng và nêu rõ phạm vi chưa bao gồm phần bị chặn. `DCA-checked` chỉ xác nhận DCA đã kiểm theo nguồn trong phạm vi; `approved` chỉ khi có bằng chứng người có quyền duyệt.

## Đầu ra chính và hồ sơ kiểm định riêng

```text
<parent>/
  docs/                         # --output ./docs; tài liệu đã biên soạn
    README.md                   # Mục tiêu, phạm vi, mốc nguồn, bản đồ chủ đề
    <danh-mục>/
      README.md                 # Phạm vi danh mục
      <chủ-đề>.md               # Nội dung có trích dẫn tại chỗ
      <sơ-đồ>.md                # Chỉ khi hữu ích và có đủ căn cứ
  docs-review/                  # Mặc định; có thể đổi bằng --review-output
    README.md                   # Độ phủ, trạng thái, giới hạn và số vấn đề mở
    provenance.md               # Nguồn → mệnh đề → tài liệu
    unresolved.md               # Mâu thuẫn, mơ hồ, thiếu căn cứ
    manifest.md                 # Mốc nguồn và file DCA sở hữu
    blocked/                    # Chỉ khi cần giữ bản nháp chưa qua cổng
```

Không tạo thư mục rỗng. Trước khi ghi, xác định mục tiêu bộ dữ liệu tài liệu, người đọc và lĩnh vực từ yêu cầu và nguồn. Chọn danh mục theo **nội dung và mục đích tài liệu**, không theo tên file thô hay gán cứng cấu trúc web cho mọi lĩnh vực. Nếu có nhiều cách phân loại hoặc chuẩn trình bày tác động đáng kể tới ý nghĩa và khả năng dùng tài liệu, trình bày phương án ngắn gọn để người dùng chốt; vẫn xử lý phần không phụ thuộc. Nếu chưa có quy chuẩn lĩnh vực, dùng cấu trúc Markdown rõ ràng và nêu rằng đây là quy ước trình bày của bộ tài liệu, không tự nhận tuân chuẩn chuyên ngành. Ví dụ, dự án phần mềm có thể cần sản phẩm/yêu cầu/kiến trúc; hồ sơ cơ khí có thể cần cơ cấu/điện/điều khiển. Nếu dự án có phân loại đã duyệt, tuân theo nó. Mỗi định nghĩa/quy tắc có một nơi lưu chính, nơi khác liên kết đến đó.

## Nội dung phải hữu ích khi không mở file thô

`docs/README.md` giải thích từng danh mục dùng để trả lời câu hỏi nào và đường đi đến tài liệu cần xem. Mỗi tài liệu chủ đề nêu mục đích, phạm vi, thuật ngữ, quy tắc/quan hệ đã được viết lại thành văn mạch lạc, điều kiện, ngoại lệ, trạng thái kiểm định và trích dẫn. Không xuất danh sách câu rời rạc từ các file theo thứ tự đọc. Dùng [mẫu chỉ mục](../assets/package-index.md) và [mẫu tài liệu](../assets/curated-document.md).

Trích dẫn đặt **ngay sau phát biểu quan trọng** trong docs, có thể là footnote: `[^SRC-01]` trỏ đến tên nguồn, phiên bản, mục/trang/dòng và đường dẫn gốc. Tài liệu được hiểu đầy đủ ngay cả khi người đọc không theo liên kết. `<folder-review>/provenance.md` giữ vết chi tiết nguồn → mệnh đề → tài liệu, dùng để kiểm tra chứ không thay nội dung docs. Không ghi một nguồn thành hai nguồn độc lập. Với nguồn ngoài, ghi ngày kiểm tra và giới hạn trích dẫn. Dùng [mẫu hồ sơ kiểm định](../assets/package-registers.md).

`docs/README.md` là điểm vào chính: tóm tắt mục tiêu, phạm vi và mốc nguồn, chủ đề đã biên soạn, trạng thái kiểm định/phê duyệt và giới hạn; chỉ tới từng danh mục. `<folder-review>/README.md` tóm tắt độ phủ và các vấn đề mở. Nội dung docs phải tự hiểu được mà không cần mở review hoặc file thô.

## Ghi và kiểm tra

- Xác định riêng hai đích docs và review; không để review nằm trong docs hoặc đầu ra bị quét như nguồn. Nếu đích đã có nội dung, đối chiếu manifest và file hiện hữu, xem diff và chỉ sửa file DCA sở hữu; không xóa hoặc ghi đè âm thầm. Không theo symlink ngoài phạm vi.
- Kiểm từng tài liệu có nội dung đủ nghĩa, nguồn/cước chú hoạt động, danh mục đúng chức năng và không trùng nơi lưu chính. Kiểm `docs/README.md` liệt kê đúng các tài liệu. Kiểm `<folder-review>/unresolved.md` có mọi vấn đề chặn tài liệu, không bị giấu trong chú thích nhỏ.
- Với sơ đồ, kiểm bảng/trình tự cạnh so với câu chữ và nguồn; không nhận Mermaid khái niệm là bản kỹ thuật đạt chuẩn. Kiểm render khi có công cụ, nếu không ghi chưa kiểm.
- Bàn giao đường dẫn folder docs và folder review, số tài liệu đã qua cổng, số nội dung bị chặn, độ phủ nguồn và giới hạn xác minh. Nếu không mệnh đề nào qua cổng, `docs/README.md` nói rõ chưa có tài liệu đủ điều kiện; không tạo tài liệu giả.
