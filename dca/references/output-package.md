# Từ nguồn thô thành bộ docs có kiểm định

`build [phạm vi] --output <thư mục>` đọc tập nguồn, tách/đối chiếu các phát biểu, rồi **biên soạn lại thành tài liệu theo chủ đề để người đọc dùng trực tiếp**. Không dùng một trang chỉ dẫn đọc file thô làm sản phẩm chính. Nếu không chỉ định đường dẫn, chọn `dca-output/` trong workspace. Thư mục đầu ra tách biệt với nguồn; không di chuyển hoặc sửa nguồn.

## Cổng lọc trước khi biên soạn

Chỉ đưa một phát biểu vào `docs/` khi đã kiểm tra:

1. **Nguồn và thẩm quyền:** vị trí, phiên bản, phạm vi và loại bằng chứng đủ cho điều được khẳng định; quyết định đã duyệt có chứng cứ riêng.
2. **Nghĩa:** chủ thể, hành động, đối tượng, điều kiện, ngoại lệ và thời điểm rõ để người đọc không phải mở file thô mới hiểu.
3. **Nhất quán:** đã đối chiếu mọi nguồn liên quan trong phạm vi; không còn mâu thuẫn trọng yếu chưa giải quyết về phát biểu đó.
4. **Truy vết:** có trích dẫn ngay trong tài liệu, dẫn đến bản gốc và vị trí; diễn giải không đổi nghĩa và không được nâng suy luận thành quy tắc.

Nội dung trượt cổng nằm ở `review/unresolved.md` hoặc một bản nháp trong `review/blocked/` khi cần giữ đủ ngữ cảnh; **không** đặt vào `docs/` như quy định đã xác minh. Có thể biên soạn những phần độc lập đã đạt cổng và nêu rõ phạm vi chưa bao gồm phần bị chặn. `DCA-checked` chỉ xác nhận DCA đã kiểm theo nguồn trong phạm vi; `approved` chỉ khi có bằng chứng người có quyền duyệt.

## Một thư mục, hai khu vực rõ nghĩa

```text
dca-output/
  README.md                     # Bộ này có gì, phạm vi và trạng thái kiểm định
  docs/                         # Tài liệu đã qua cổng lọc, tự đủ ngữ cảnh
    README.md                   # Bản đồ chủ đề và mục đích từng danh mục
    <danh-mục>/
      README.md                 # Phạm vi danh mục và liên kết tài liệu
      <chủ-đề>.md               # Nội dung đã biên soạn và trích dẫn
      <sơ-đồ>.md                # Chỉ khi sơ đồ có ích; đặt cạnh chủ đề liên quan
  review/                       # Hồ sơ kiểm định, không phải tài liệu chính thức
    provenance.md               # Mã nguồn, vị trí, phiên bản và ánh xạ nội dung
    unresolved.md               # Mâu thuẫn, mơ hồ, thiếu chứng cứ và phần bị chặn
    blocked/                    # Chỉ khi cần giữ bản nháp chưa qua cổng
```

Không tạo thư mục rỗng. Chọn danh mục theo **nội dung và mục đích tài liệu**, không theo tên file thô hay gán cứng cấu trúc web cho mọi lĩnh vực. Ví dụ, dự án phần mềm có thể cần sản phẩm/yêu cầu/kiến trúc; hồ sơ cơ khí có thể cần cơ cấu/điện/điều khiển. Nếu dự án có phân loại đã duyệt, tuân theo nó. Mỗi định nghĩa/quy tắc có một nơi lưu chính, nơi khác liên kết đến đó.

## Nội dung phải hữu ích khi không mở file thô

`docs/README.md` giải thích từng danh mục dùng để trả lời câu hỏi nào và đường đi đến tài liệu cần xem. Mỗi tài liệu chủ đề nêu mục đích, phạm vi, thuật ngữ, quy tắc/quan hệ đã được viết lại thành văn mạch lạc, điều kiện, ngoại lệ, trạng thái kiểm định và trích dẫn. Không xuất danh sách câu rời rạc từ các file theo thứ tự đọc. Dùng [mẫu chỉ mục](../assets/package-index.md) và [mẫu tài liệu](../assets/curated-document.md).

Trích dẫn đặt **ngay sau phát biểu quan trọng** trong docs, có thể là footnote: `[^SRC-01]` trỏ đến tên nguồn, phiên bản, mục/trang/dòng và đường dẫn gốc. Tài liệu được hiểu đầy đủ ngay cả khi người đọc không theo liên kết. `review/provenance.md` giữ vết chi tiết nguồn → mệnh đề → tài liệu, dùng để kiểm tra chứ không thay nội dung docs. Không ghi một nguồn thành hai nguồn độc lập. Với nguồn ngoài, ghi ngày kiểm tra và giới hạn trích dẫn. Dùng [mẫu hồ sơ kiểm định](../assets/package-registers.md).

`README.md` ở gốc tóm tắt bộ tài liệu đã sản xuất, phạm vi và mốc nguồn, số chủ đề đạt cổng, chủ đề bị chặn, trạng thái duyệt và giới hạn. Hướng dẫn cụ thể **dùng docs thế nào**, chỗ nào là tài liệu chuẩn và chỗ nào là hồ sơ rà soát. Không bắt người đọc đi qua `provenance.md` để tìm nội dung chính.

## Ghi và kiểm tra

- Nếu đích mới, tạo một thư mục duy nhất. Nếu đích đã có nội dung, nhận diện tệp DCA sở hữu và thay đổi thủ công; xem diff, không xóa/ghi đè âm thầm. Không theo symlink ngoài phạm vi.
- Kiểm từng tài liệu có nội dung đủ nghĩa, nguồn/cước chú hoạt động, danh mục đúng chức năng và không trùng nơi lưu chính. Kiểm `docs/README.md` liệt kê đúng các tài liệu. Kiểm `review/unresolved.md` có mọi vấn đề chặn tài liệu, không bị giấu trong chú thích nhỏ.
- Với sơ đồ, kiểm bảng/trình tự cạnh so với câu chữ và nguồn; không nhận Mermaid khái niệm là bản kỹ thuật đạt chuẩn. Kiểm render khi có công cụ, nếu không ghi chưa kiểm.
- Bàn giao đường dẫn thư mục, số tài liệu đã qua cổng, số nội dung bị chặn, độ phủ nguồn và giới hạn xác minh. Nếu không mệnh đề nào qua cổng, `docs/README.md` nói rõ chưa có tài liệu đủ điều kiện; không tạo tài liệu giả.
